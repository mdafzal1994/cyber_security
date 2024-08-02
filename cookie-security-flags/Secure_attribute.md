#  The Secure attribute

The Secure flag specifies that the cookie may only be transmitted using HTTPS connections (SSL/TLS encryption) and never sent in clear text. If the cookie is set with the Secure flag and the browser sends a subsequent request using the HTTP protocol, the web page will not send this cookie to the web server in its HTTP response.

The Secure attribute is meant to protect against man-in-the-middle (MITM) attacks. However, it protects only the confidentiality of the cookie, not its integrity. In a MITM attack, an attacker located between the browser and the server will not receive the cookie from the server via an unencrypted connection but can still send a forged cookie to the server in plain text.

Note that you can only set the Secure flag when using a secure connection.

# The SameSite attribute

The SameSite flag instructs web browsers to send cookies differently depending on how a visitor interacts with the site that set the cookie. This flag is used to help protect against CSRF attacks.

The SameSite cookie attribute may have one of the following values:

**SameSite=Stric**t: The cookie is only sent if you are currently on the site that the cookie is set for. If you are on a different site and click a link to the site that the cookie is set for, the cookie is not sent with the first request.
**SameSite=Lax**: The cookie is not sent for embedded content, but it is sent if you trigger top-level navigation, e.g. by clicking on a link to the site that the cookie is set for. It is sent only with safe request types that do not change state, such as GET.
**SameSite=None**: The cookie is sent even for embedded content.
Note that you can expect different browser behaviors when the SameSite attribute is not set. For example, in 2019, the Google Chrome browser changed its default behavior for same-site cookies. Since this may change again over time, we recommend regularly checking how your applications behave with new browser versions.

**ref** -: https://www.invicti.com/learn/cookie-security-flags/
