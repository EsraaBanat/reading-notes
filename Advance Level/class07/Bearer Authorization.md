# Bearer Authorization 

# Introdution to JWT

**JSON Web Token (JWT)** : an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object.

### When should you use JSON Web Tokens?

- **Authorization**: This is the most common scenario for using JWT. Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token.

- **Information Exchange**: JSON Web Tokens are a good way of securely transmitting information between parties. Because JWTs can be signed—for example, using public/private key pairs—you can be sure the senders are who they say they are. Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't been tampered with.

## JSON Web Token structure

In its compact form, JSON Web Tokens consist of three parts separated by dots (.), which are:

- **Header :**

  The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.

- **Payload :**

  contains the claims. Claims are statements about an entity (typically, the user) and additional data.

  There are three types of claims: registered, public, and private claims.

- **Signature :**

   The signature is used to verify the message wasn't changed along the way, and, in the case of tokens signed with a private key, it can also verify that the sender of the JWT is who it says it is.

## How do JSON Web Tokens work?

In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned. Since tokens are credentials, great care must be taken to prevent security issues. In general, you should not keep tokens longer than required.

You also should not store sensitive session data in browser storage due to lack of security.

Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the Bearer schema. The content of the header should look like the following:

Authorization: Bearer <token>
This can be, in certain cases, a stateless authorization mechanism. The server's protected routes will check for a valid JWT in the Authorization header, and if it's present, the user will be allowed to access protected resources

# Are JWTs Secure?



## References

## [JWTs Explained](https://www.youtube.com/watch?v=926mknSW9Lo)

## [Intro to JWT](https://jwt.io/introduction/)

## [Are JWTs Secure?](https://stackoverflow.com/questions/27301557/if-you-can-decode-jwt-how-are-they-secure)


## [Back To Home Page](../../README.md)
