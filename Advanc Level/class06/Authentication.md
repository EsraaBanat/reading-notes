# Authentication

# Securing Passwords :

Passwords are the first line of defense against cyber criminals. It is the most vital secret of every activity we do over the internet and also a final check to get into any of your user account, whether it is your bank account, email account, shopping cart account or any other account you have.

Cryptographic hash algorithms MD5, SHA1, SHA256, SHA512, SHA-3 are general purpose hash functions, designed to calculate a digest of huge amounts of data in as short a time as possible. Hashing is the greatest way for protecting passwords and considered to be pretty safe for ensuring the integrity of data or password.

The benefit of hashing is that if someone steals the database with hashed passwords, they only make off with the hashes and not the actual plaintext passwords.

###  PROBLEMS WITH CRYPTOGRAPHIC HASH ALGORITHM :

- **Brute Force attack:** Hashes can't be reversed, so instead of reversing the hash of the password, an attacker can simply keep trying different inputs until he does not find the right now that generates the same hash value, called brute force attack

- **Hash Collision attack:** Hash functions have infinite input length and a predefined output length, so there is inevitably going to be the possibility of two different inputs that produce the same output hash.

As a PHP developer, you can simply use the crypt() function with a Blowfish required salt.

```
<?php
// Generate a password using a random salt
password_hash($password, PASSWORD_BCRYPT);
// Generate a password with a known salt
password_hash($password, PASSWORD_BCRYPT, array("salt" => $salt));
// This will cause crypt to generate a bcrypt hash
$salt = '$2y$10$' . mcrypt_create_iv(22);
$salted_password = crypt($password, $salt)
```
This method of hashing passwords is solid enough for most web applications that stores users' passwords and other sensitive data.


# Basic Auth :

 - **basic access authentication** is a method for an HTTP user agent (e.g. a web browser) to provide a user name and password when making a request

 HTTP Basic authentication (BA) implementation is the simplest technique for enforcing access controls to web resources because it does not require cookies, session identifiers, or login pages; rather, HTTP Basic authentication uses standard fields in the HTTP header.

 ### Security

The BA mechanism does not provide confidentiality protection for the transmitted credentials. They are merely encoded with Base64 in transit and not encrypted or hashed in any way. Therefore, basic authentication is typically used in conjunction with HTTPS to provide confidentiality.

Because the BA field has to be sent in the header of each HTTP request, the web browser needs to cache credentials for a reasonable period of time to avoid constantly prompting the user for their username and password. Caching policy differs between browsers.

### Protocol

#### Server side

When the server wants the user agent to authenticate itself towards the server after receiving an unauthenticated request, it must send a response with a HTTP 401 Unauthorized status line and a WWW-Authenticate header field.

The WWW-Authenticate header field for basic authentication is constructed as following:

```
WWW-Authenticate: Basic realm="User Visible Realm"
```

The server may choose to include the charset parameter from RFC 7617:

```
WWW-Authenticate: Basic realm="User Visible Realm", charset="UTF-8"
```

This parameter indicates that the server expects the client to use UTF-8 for encoding username and password

#### Client side

When the user agent wants to send authentication credentials to the server, it may use the Authorization header field.

The Authorization header field is constructed as follows:

1. The username and password are combined with a single colon (:). This means that the username itself cannot contain a colon.
2. The resulting string is encoded into an octet sequence. The character set to use for this encoding is by default unspecified, as long as it is compatible with US-ASCII, but the server may suggest use of UTF-8 by sending the charset parameter.
3. The resulting string is encoded using a variant of Base64 (+/ and with padding).
4. The authorization method and a space (e.g. "Basic ") is then prepended to the encoded string.

For example, if the browser uses Aladdin as the username and open sesame as the password, then the field's value is the Base64 encoding of Aladdin:open sesame, or QWxhZGRpbjpvcGVuIHNlc2FtZQ==. Then the Authorization header field will appear as:

```
Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==
```


# OWASP auth cheatsheet:

**Authentication** is the process of verifying that an individual, entity or website is whom it claims to be. Authentication in the context of web applications is commonly performed by submitting a username or ID and one or more items of private information that only a given user should know.

**Session Management** is a process by which a server maintains the state of an entity interacting with it

### **Authentication General Guidelines**:

User IDs :
Make sure your usernames/user IDs are case-insensitive

#### **Authentication Solution and Sensitive Accounts**

- Do **NOT** allow login with sensitive accounts (i.e. accounts that can be used internally within the solution such as to a back-end / middle-ware / DB) to any front-end user-interface

- Do **NOT** use the same authentication solution (e.g. IDP / AD) used internally for unsecured access (e.g. public access / DMZ)

### **Authentication and Error Messages**:
Using any of the authentication mechanisms (login, password reset or password recovery), an application must respond with a generic error message regardless of whether:

- The user ID or password was incorrect.
- The account does not exist.
- The account is locked or disabled.

The account registration feature should also be taken into consideration, and the same approach of generic error message can be applied regarding the case in which the user exists.

The objective is to prevent the creation of a discrepancy factor, allowing an attacker to mount a user enumeration action against the application.

It is interesting to note that the business logic itself can bring a discrepancy factor related to the processing time taken. Indeed, depending on the implementation, the processing time can be significantly different according to the case (success vs failure) allowing an attacker to mount a time-based attack (delta of some seconds for example).

### **Protect Against Automated Attacks**

There are a number of different types of automated attacks that attackers can use to try and compromise user accounts. The most common types are listed below:

| Attack Type         | Description                                                                             |
|---------------------|-----------------------------------------------------------------------------------------|
| Brute Force         | Testing multiple passwords from a dictionary or other source against a single account.  |
| Credential Stuffing | Testing username/password pairs obtained from the breach of another site.               |
| Password Spraying   | Testing a single weak password against a large number of different accounts.            |



# bcrypt docs :

- A library to help you hash passwords.

### **Install via NPM**

```
npm install bcrypt
```

## Usage
```
async (recommended)
const bcrypt = require('bcrypt');
const saltRounds = 10;
const myPlaintextPassword = 's0/\/\P4$$w0rD';
const someOtherPlaintextPassword = 'not_bacon';
```

### To hash a password:
**Technique 1** (generate a salt and hash on separate function calls):

```
bcrypt.genSalt(saltRounds, function(err, salt) {
    bcrypt.hash(myPlaintextPassword, salt, function(err, hash) {
        // Store hash in your password DB.
    });
});
```

**Technique 2** (auto-gen a salt and hash):

```
bcrypt.hash(myPlaintextPassword, saltRounds, function(err, hash) {
    // Store hash in your password DB.
});
```
Note that both techniques achieve the same end-result.

To check a password:

```
// Load hash from your password DB.
bcrypt.compare(myPlaintextPassword, hash, function(err, result) {
    // result == true
});
bcrypt.compare(someOtherPlaintextPassword, hash, function(err, result) {
    // result == false
});
```

### **Hash Info**
The characters that comprise the resultant hash are
```
./ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789$.
 ```

Resultant hashes will be 60 characters long and they will include the salt among other parameters, as follows:

```
$[algorithm]$[cost]$[salt][hash]
```

- 2 chars hash algorithm identifier prefix. `"$2a$" or "$2b$" `indicates BCrypt

- Cost-factor (n). Represents the exponent used to determine how many iterations 2^n

- 16-byte (128-bit) salt, base64 encoded to 22 characters

- 24-byte (192-bit) hash, base64 encoded to 31 characters

**Example:**

```
$2b$10$nOUIs5kJ7naTuTFkBy1veuK0kSxUFXfuaOKdOKf9xYT0KKIGSJwFa
 |  |  |                     |
 |  |  |                     hash-value = K0kSxUFXfuaOKdOKf9xYT0KKIGSJwFa
 |  |  |
 |  |  salt = nOUIs5kJ7naTuTFkBy1veu
 |  |
 |  cost-factor => 10 = 2^10 rounds
 |
 hash-algorithm identifier => 2b = BCrypt
```

### **Testing** :

If you create a pull request, tests better pass :)

```
npm install
npm test
```
<br>
<hr>

## References

## [Securing Passwords](https://thehackernews.com/2014/04/securing-passwords-with-bcrypt-hashing.html)

## [Basic Auth](https://en.wikipedia.org/wiki/Basic_access_authentication)

## [OWASP auth cheatsheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)

## [bcrypt docs](https://www.npmjs.com/package/bcrypt)

## [Back To Home Page](../../README.md)
