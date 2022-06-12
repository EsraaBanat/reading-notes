# Sequelize-Normalization:

Sequelize supports the standard associations: 

One-To-One, One-To-Many and Many-To-Many.
To do this, Sequelize provides four types of associations that should be combined to create them:

1. The HasOne association
2. The BelongsTo association
3. The HasMany association
4. The BelongsToMany association


## Defining the Sequelize associations :
The four association types are defined in a very similar way. Let's say we have two models, `A` and `B`. Telling Sequelize that you want an association between the two needs just a function call:

````
const A = sequelize.define('A', /*...*/);
const B = sequelize.define('B', /*...*/);

A.hasOne(B); // A HasOne B
A.belongsTo(B); // A BelongsTo B
A.hasMany(B); // A HasMany B
A.belongsToMany(B, { through: 'C' }); // A BelongsToMany B through the junction table C
````
They all accept an options object as a second parameter (optional for the first three, mandatory for belongsToMany containing at least the through property):

````
A.hasOne(B, { /*options*/ });
A.belongsTo(B, { /*options*/ });
A.hasMany(B, { /*options*/ });
A.belongsToMany(B, { through: 'C', /*options*/ });

````
`A` is called the source model and `B` is called the target mode

- The `A.hasOne(B)` association means that a One-To-One relationship exists between A and B, with the foreign key being defined in the target model (B).

- The `A.belongsTo(B)` association means that a One-To-One relationship exists between A and B, with the foreign key being defined in the source model (A).

- The `A.hasMany(B)` association means that a One-To-Many relationship exists between A and B, with the foreign key being defined in the target model (B).

- The `A.belongsToMany(B, { through: 'C' })` association means that a Many-To-Many relationship exists between `A` and `B`, using table `C` as junction table, which will have the foreign keys (aId and bId, for example). Sequelize will automatically create this model `C` (unless it already exists) and define the appropriate foreign keys on

## One-To-One relationships:

### Implementation:

For the rest of this example, let's assume that we have two models, Foo and Bar. We want to setup a One-To-One relationship between them such that Bar gets a fooId column.

```
Foo.hasOne(Bar);
Bar.belongsTo(Foo);
```
Since no option was passed, Sequelize will infer what to do from the names of the models. In this case, Sequelize knows that a fooId column must be added to Bar.

This way, calling Bar.sync() after the above will yield the following SQL (on PostgreSQL, for example):

``` 
CREATE TABLE IF NOT EXISTS "foos" (
  /* ... */
);
CREATE TABLE IF NOT EXISTS "bars" (
  /* ... */
  "fooId" INTEGER REFERENCES "foos" ("id") ON DELETE SET NULL ON UPDATE CASCADE
  /* ... */
);
```

### Options :
Various options can be passed as a second parameter of the association call.

`onDelete` and `onUpdate`

The possible choices are `RESTRICT`, `CASCADE`,` NO ACTION`,` SET DEFAULT` and `SET NULL`.

The defaults for the One-To-One associations is `SET NULL` for ON DELETE and `CASCADE` for ON UPDATE.

### Customizing the foreign key :

Both the `hasOne` and `belongsTo` calls shown above will infer that the foreign key to be created should be called fooId. To use a different name, such as myFooId:
```
// Option 1
Foo.hasOne(Bar, {
  foreignKey: 'myFooId'
});
Bar.belongsTo(Foo);

// Option 2
Foo.hasOne(Bar, {
  foreignKey: {
    name: 'myFooId'
  }
});
Bar.belongsTo(Foo);

// Option 3
Foo.hasOne(Bar);
Bar.belongsTo(Foo, {
  foreignKey: 'myFooId'
});

// Option 4
Foo.hasOne(Bar);
Bar.belongsTo(Foo, {
  foreignKey: {
    name: 'myFooId'
  }
});
```
As shown above, the foreignKey option accepts a string or an object. When receiving an object, this object will be used as the definition for the column just like it would do in a standard `sequelize.define` call. Therefore, specifying options such as `type`, `allowNull`, `defaultValue`, etc, just work.


## One-To-Many relationships :
One-To-Many associations are connecting one source with multiple targets, while all these targets are connected only with this single source.

This means that, unlike the One-To-One association, in which we had to choose where the foreign key would be placed, there is only one option in One-To-Many associations.

### Implementation:
The main way to do this is as follows:
```
Team.hasMany(Player);
Player.belongsTo(Team);
```
Again, as mentioned, the main way to do it used a pair of Sequelize associations (`hasMany` and `belongsTo`).

```
For example, in PostgreSQL, the above setup will yield the following SQL upon sync():

CREATE TABLE IF NOT EXISTS "Teams" (
  /*...*/
);
CREATE TABLE IF NOT EXISTS "Players" (
  /*...*/
  "TeamId" INTEGER REFERENCES "Teams" ("id") ON DELETE SET NULL ON UPDATE CASCADE,
  /*...*/
);
```

### Options :
The options to be applied in this case are the same from the One-To-One case

## Many-To-Many relationships :
Many-To-Many associations connect one source with multiple targets, while all these targets can in turn be connected to other sources beyond the first.

This cannot be represented by adding one foreign key to one of the tables, like the other relationships did. Instead, the concept of a `Junction Model` is used. This will be an extra model (and extra table in the database) which will have two foreign key columns and will keep track of the associations. The junction table is also sometimes called `join table` or `through table`.

### Implementation :

The main way to do this in Sequelize is as follows:

```
const Movie = sequelize.define('Movie', { name: DataTypes.STRING });
const Actor = sequelize.define('Actor', { name: DataTypes.STRING });
Movie.belongsToMany(Actor, { through: 'ActorMovies' });
Actor.belongsToMany(Movie, { through: 'ActorMovies' });
```

Since a string was given in the through option of the belongsToMany call, Sequelize will automatically create the ActorMovies model which will act as the junction model. 

Instead of a string, passing a model directly is also supported, and in that case the given model will be used as the junction model (and no model will be created automatically). For example:

```
const Movie = sequelize.define('Movie', { name: DataTypes.STRING });
const Actor = sequelize.define('Actor', { name: DataTypes.STRING });
const ActorMovies = sequelize.define('ActorMovies', {
  MovieId: {
    type: DataTypes.INTEGER,
    references: {
      model: Movie, // 'Movies' would also work
      key: 'id'
    }
  },
  ActorId: {
    type: DataTypes.INTEGER,
    references: {
      model: Actor, // 'Actors' would also work
      key: 'id'
    }
  }
});
Movie.belongsToMany(Actor, { through: ActorMovies });
Actor.belongsToMany(Movie, { through: ActorMovies });
```

### Options:

Unlike One-To-One and One-To-Many relationships, the defaults for both ON UPDATE and ON DELETE are CASCADE for Many-To-Many relationships.

Belongs-To-Many creates a unique key on through model. This unique key name can be overridden using uniqueKey option. To prevent creating this unique key, use the unique: false option.

```
Project.belongsToMany(User, { through: UserProjects, uniqueKey: 'my_custom_unique' })
```
## Association Aliases & Custom Foreign Keys :
There are three ways to specify a different name for the foreign key:

- By providing the foreign key name directly
- By defining an Alias
- By doing both things

Aliases are especially useful when you need to define two different associations between the same models. For example, if we have the models Mail and Person, we may want to associate them twice, to represent the sender and receiver of the Mail. In this case we must use an alias for each association, since otherwise a call like mail.getPerson() would be ambiguous. With the sender and receiver aliases, we would have the two methods available and working: mail.getSender() and mail.getReceiver(), both of them returning a Promise<Person>.

## Special methods/mixins added to instances :

### `Foo.hasOne(Bar)`

```
fooInstance.getBar()
fooInstance.setBar()
fooInstance.createBar()
```
### `Foo.belongsTo(Bar)`
The same ones from `Foo.hasOne(Bar)`:

### `Foo.hasMany(Bar)`

```
fooInstance.getBars()
fooInstance.countBars()
fooInstance.hasBar()
fooInstance.hasBars()
fooInstance.setBars()
fooInstance.addBar()
fooInstance.addBars()
fooInstance.removeBar()
fooInstance.removeBars()
fooInstance.createBar()
```

### `Foo.belongsToMany(Bar, { through: Baz })`
The same ones from `Foo.hasMany(Bar)`

For belongsToMany relationships, by default getBars() will return all fields from the join table. Note that any include options will apply to the target Bar object, so trying to set options for the join table as you would when eager loading with find methods is not possible. To choose what attributes of the join table to include, getBars() supports a joinTableAttributes option that can be used similarly to setting through.attributes in an include.

## References :

## [Sequelize/Associations](https://sequelize.org/docs/v6/core-concepts/assocs/)

## [Back To Home Page](../../README.md)
