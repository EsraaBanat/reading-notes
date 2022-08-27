# `<Login />` and `<Auth />`

**Role-based access control (RBAC)** restricts network access based on a person's role within an organization and has become one of the main methods for advanced access control

### EXAMPLES OF ROLE-BASED ACCESS CONTROL

Some of the designations in an RBAC tool can include:

- **Management role scope** – it limits what objects the role group is allowed to manage.
- **Management role group** – you can add and remove members.
- **Management role** – these are the types of tasks that can be performed by a specific role group.
- **Management role assignment** – this links a role to a role group.

By adding a user to a role group, the user has access to all the roles in that group. If they are removed, access becomes restricted. Users may also be assigned to multiple groups in the event they need temporary access to certain data or programs and then removed once the project is complete.

Other options for user access may include:

- **Primary** – the primary contact for a specific account or role.
- **Billing** – access for one end-user to the billing account.
- **Technical** – assigned to users that perform technical tasks.
- **Administrative** – access for users that perform administrative tasks.

### BENEFITS OF RBAC

**1. Reducing administrative work and IT support** : With RBAC, you can reduce the need for paperwork and password changes when an employee is hired or changes their role. Instead, you can use RBAC to add and switch roles quickly and implement them globally across operating systems, platforms and applications.

**2. Maximizing operational efficiency**: RBAC offers a streamlined approach that is logical in definition. Instead of trying to administer lower-level access control, all the roles can be aligned with the organizational structure of the business and users can do their jobs more efficiently and autonomously.

**3. Improving compliance:** All organizations are subject to federal, state and local regulations. With an RBAC system in place, companies can more easily meet statutory and regulatory requirements for privacy and confidentiality as IT departments and executives have the ability to manage how data is being accessed and used. This is especially significant for health care and financial institutions, which manage lots of sensitive data such as PHI and PCI data.

### BEST PRACTICES FOR IMPLEMENTING RBAC

- **Current Status:** Create a list of every software, hardware and app that has some sort of security. For most of these things, it will be a password. However, you may also want to list server rooms that are under lock and key. Physical security can be a vital part of data protection. Also, list the status of who has access to all of these programs and areas. This will give you a snapshot of your current data scenario.

- **Current Roles:** Even if you do not have a formal roster and list of roles, determining what each individual team member does may only take a little discussion. Try to organize the team in such a way that it doesn’t stifle creativity and the current culture (if enjoyed).

- **Write a Policy:** Any changes made need to be written for all current and future employees to see. Even with the use of a RBAC tool, a document clearly articulating your new system will help avoid potential issues.

- **Make Changes:** Once the current security status and roles are understood (not to mention a policy is written), it’s time to make the changes.

- **Continually Adapt:** It’s likely that the first iteration of RBAC will require some tweaking. Early on, you should evaluate your roles and security status frequently. Assess first, how well the creative/production process is working and secondly, how secure your process happens to be.

# react-cookie

Getting started

```js
npm install react-cookie
```

### useCookies([dependencies])

Access and modify cookies using React hooks.
```js
const [cookies, setCookie, removeCookie] = useCookies(['cookie-name']);
```

## Cookies Methods : 

### `get(name, [options])`

Get a cookie value

- name (string): cookie name
- options (object):
doNotParse (boolean): do not convert the cookie into an object no matter what


### `getAll([options])`

Get all cookies

- options (object):
    - doNotParse (boolean): do not convert the cookie into an object no matter what

### `set(name, value, [options])`

Set a cookie value

- name (string): cookie name
- value (string|object): save the value and stringify the object if needed
- options (object): Support all the cookie options from RFC 6265
    - path (string): cookie path, use / as the path if you want your cookie to be accessible on all pages
    - expires (Date): absolute expiration date for the cookie
    - maxAge (number): relative max age of the cookie from when the client receives it in seconds
    - domain (string): domain for the cookie (sub.domain.com or .allsubdomains.com)
    - secure (boolean): Is only accessible through HTTPS?
    - httpOnly (boolean): Can only the server access the cookie? Note: You cannot get or set httpOnly cookies from the browser, only the server.
    - sameSite (boolean|none|lax|strict): Strict or Lax enforcement

### `remove(name, [options])`

Remove a cookie

- name (string): cookie name
- options (object): Support all the cookie options from RFC 6265
    - path (string): cookie path, use / as the path if you want your cookie to be accessible on all pages
    - expires (Date): absolute expiration date for the cookie
    - maxAge (number): relative max age of the cookie from when the client receives it in seconds
    - domain (string): domain for the cookie (sub.domain.com or .allsubdomains.com)
    - secure (boolean): Is only accessible through HTTPS?
    - httpOnly (boolean): Can only the server access the cookie? Note: You cannot get or set httpOnly cookies from the browser, only the server.
    - sameSite (boolean|none|lax|strict): Strict or Lax enforcement


# References

## [What is Role Based Access Control (RBAC)?](https://digitalguardian.com/blog/what-role-based-access-control-rbac-examples-benefits-and-more)

## [react-cookie library](https://www.npmjs.com/package/react-cookie)

## [react-cookies component](https://www.npmjs.com/package/react-cookies)

## [Back To Home Page](../../README.md)
