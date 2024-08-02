# cookie-security-flags

ref: https://www.invicti.com/learn/cookie-security-flags/

### The HttpOnly attribute
**Increased Security Against XSS Attacks**: The primary purpose of the HttpOnly flag is to mitigate the risk of client-side script accessing sensitive cookie data. By setting the HttpOnly flag, you prevent JavaScript (via document.cookie) running on the page from accessing the cookie. This means that even if an attacker manages to inject malicious scripts into your website (through a cross-site scripting or XSS attack), those scripts won't be able to read or manipulate cookies marked as HttpOnly.

**Use Cas**e: The HttpOnly flag is commonly used for session cookies or any other cookies that store sensitive information, such as authentication tokens. By marking these cookies as HttpOnly, you help ensure that their data cannot be easily stolen by attackers through client-side scripts.
eg .**Set-Cookie: sessionId=abc123; HttpOnly**

###Limitations of HttpOnly
**Cookie Overwriting**: While HttpOnly protects the cookie from being accessed via JavaScript, it does not protect it from being overwritten by server-side responses or other mechanisms. If an attacker can manipulate the server's responses or intercept requests, they might be able to overwrite cookies, including those with the HttpOnly flag.

**Cookie Jar Overflow Attack**:

**Concept**: Browsers typically have a limit on the number of cookies they can store per domain. This limit varies by browser but is generally in the range of around 50 to 100 cookies per domain.
**Attack**: An attacker can exploit this limitation by sending a large number of cookies for a domain, exceeding the browser's storage capacity. As a result, older cookies (including those marked as HttpOnly) might be removed to make space for new cookies.
Result: If an HttpOnly cookie is evicted from storage, it no longer exists in the browser's cookie jar. The attacker could then set a new cookie with the same name but without the HttpOnly flag, thereby making it accessible via JavaScript.
