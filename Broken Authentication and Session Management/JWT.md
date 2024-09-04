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

Open menu
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
