
**Clickjacking** is a type of web-based attack where a user is tricked into clicking something they didn't intend to. It works by placing a hidden, malicious element (like a button or a link) on top 
of a page the user is interacting with. The user sees and clicks on a visible, harmless element (for example, a "Click here to win a prize" button), but in reality, they are unknowingly clicking on a hidden, 
malicious button that performs an unwanted action, such as transferring money or changing account settings.

Here’s how it typically works:

1. The attacker creates a decoy (fake) webpage, often offering something enticing like a game or a reward ("Win a prize!" button).
2. On top of this page, they overlay an invisible, malicious button that performs a harmful action (like making a payment or changing security settings).
3. When the user clicks the visible button, they also unknowingly trigger the hidden malicious button in the background.

The key difference between clickjacking and other attacks, like **CSRF (Cross-Site Request Forgery)**, is that clickjacking requires the user to actively click something, whereas CSRF doesn't require
any user interaction—it can send a request without the user’s knowledge.


**How to prevent clickjacking attacks**

To prevent clickjacking attacks, there are several effective strategies you can implement. Here's a breakdown of the most common and straightforward methods:

### 1. **Use X-Frame-Options Header**
   - This HTTP header prevents your website from being embedded in an iframe on another website, which is the key vector for clickjacking attacks.
   - You can set it to one of the following values:
     - **`DENY`**: This prevents the page from being displayed in any iframe, regardless of the site.
     - **`SAMEORIGIN`**: This allows the page to be displayed in an iframe, but only if the iframe is on the same origin (domain).
   - Example:
     ```http
     X-Frame-Options: DENY
     ```
   - This is a quick and effective way to block clickjacking.

### 2. **Content Security Policy (CSP)**
   - CSP is a more modern, flexible approach that allows you to specify which sites are allowed to embed your content in an iframe.
   - You can set the `frame-ancestors` directive to restrict which domains can embed your page.
   - Example:
     ```http
     Content-Security-Policy: frame-ancestors 'self'
     ```
   - This will only allow your site to be embedded within iframes on your own domain.

### 3. **Avoid Using iframes for Sensitive Actions**
   - If possible, avoid embedding your website or any sensitive page in an iframe, especially if the page contains critical actions like logging in, making payments, or changing settings.
   - If an iframe is necessary, make sure it’s from trusted sources and uses proper security measures.

### 4. **Frame Busting Scripts (Less Recommended)**
   - Frame busting is an older technique where JavaScript is used to break out of iframes by detecting when a page is being loaded within an iframe and then forcing it to load in the top window.
   - Example:
     ```javascript
     if (top != self) {
       top.location = self.location;
     }
     ```
   - While this used to be a common defense, it’s considered less reliable and less secure than the methods above, so it’s not recommended as the primary solution.

### 5. **Use SameSite Cookies**
   - This isn’t directly related to clickjacking, but using **SameSite cookies** (in your authentication and session management) can reduce the risk of attacks that require the user to be logged in to a site when being tricked into an action via clickjacking.

---

By combining these methods, especially using `X-Frame-Options` or a strong **Content Security Policy**, you can greatly reduce the risk of clickjacking on your website.
