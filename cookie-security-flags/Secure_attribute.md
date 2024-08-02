#  The Secure attribute

The Secure flag specifies that the cookie may only be transmitted using HTTPS connections (SSL/TLS encryption) and never sent in clear text. If the cookie is set with the Secure flag and the browser sends a subsequent request using the HTTP protocol, the web page will not send this cookie to the web server in its HTTP response.

The Secure attribute is meant to protect against man-in-the-middle (MITM) attacks. However, it protects only the confidentiality of the cookie, not its integrity. In a MITM attack, an attacker located between the browser and the server will not receive the cookie from the server via an unencrypted connection but can still send a forged cookie to the server in plain text.

Note that you can only set the Secure flag when using a secure connection.
