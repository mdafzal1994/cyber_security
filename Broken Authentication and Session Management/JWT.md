**What is a JWT?**

JWT stands for JSON Web Token, These tokens are typically used for authentication and authorization, as they can contain information that verifies 
the identity of a user, and their permissions.

**Structure of a JWT**
The three main components of a JWT are the:

1. Header

2. Payload

3. Signature

With these three components, JWTs allow developers to build a stateless authentication or authorization flow that is easily scalable and eliminates 
the need for servers to maintain session information.

All three of these parts are Base64Url encoded strings concatenated with periods ('.').

The header is a JSON object that typically contains two properties: The type of token (JWT) and the encryption algorithm used (e.g., HMAC SHA256, RSA, etc). 

Example of JSON header:


{

  "alg": "HS256",
  
  "typ": "JWT"
  
}

the header’s **alg** field specifies the algorithm used to sign the token. This field indicates which cryptographic algorithm is used to ensure the integrity
and authenticity of the token. Common algorithms include:


HS256 (HMAC with SHA-256)

RS256 (RSA with SHA-256)

ES256 (ECDSA with P-256 and SHA-256)

The **alg field** helps the recipient of the JWT to understand how to verify the token's signature.

The **payload** is another JSON object where all of the transmitted data lives. Also called a claim, this data typically contains user information 
(username, email address), session data (IP address, time or last login), or authorization permissions (roles or groups the user belongs to). 


There are four types of claims:


Commonly used: Registered and public


Not commonly used: Private and custom


Example of JWT payload:


Open menu

{

  "drn": "DS",
  
  "exp": 1680902696,
  
  "rexp": "2023-05-05T21:14:56Z"
  
}

The signature is created by signing the Base64Url encoded header and payload with a secret key and an algorithm specified by the developers.
It is used to verify that the sender of the JWT is who they claim to be and ensure the token's integrity.

### What are JWT attacks?

JWT attacks involve a user sending modified JWTs to the server in order to achieve a malicious goal. Typically, this goal is to bypass authentication and access controls by impersonating another user who has already been authenticated.

1. **Information leakage**:

Since JSON web tokens are used for access control, they often contain information about the user.

2. **None Algorithm Attack**:

JWT supports a “none” algorithm. If the alg field is set to “none”, any token would be considered valid if their signature section is set to empty.


3. **JWT header parameter injections**
   
    1. **Kid Parameter attack**:

KID is parameter seen in jwt token, and if the parameter is not properly validated it leads to attacks like Command injection, LFI, SQLi etc. Since the KID is often used to retrieve a key file from the file system, if it is not sanitized before use, it can lead to a directory traversal attack.

4. **JWT authentication bypass via weak signing key**
   
   Brute-forcing secret keys
Some signing algorithms, such as HS256 (HMAC + SHA-256), use an arbitrary, standalone string as the secret key. Just like a password, it's crucial that this secret can't be easily guessed or brute-forced by an attacker. Otherwise, they may be able to create JWTs with any header and payload values they like, then use the key to re-sign the token with a valid signature.
