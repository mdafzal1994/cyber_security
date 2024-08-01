# Cross-site Scripting (XSS)

reflected,stored XSS and DOM XSS

## How to Prevent Cross-site Scripting (XSS) 
 XSS attacks occur when an attacker injects malicious scripts into web pages viewed by other users. Here's a comprehensive approach to preventing XSS:

### 1. Input Validation and Sanitization
**Validate Input**: Ensure that input conforms to expected formats, lengths, and types. Use server-side validation to check for valid input.
**Sanitize Input**: Remove or escape characters that could be used in an XSS attack. For example, escape characters like <, >, ", and ' in HTML contexts.
### 2. Output Encoding
**HTML Encoding**: Encode output data when it is inserted into HTML. This means converting special characters to their HTML entity equivalents (e.g., < becomes '&lt;).
**JavaScript Encoding**: If inserting data into JavaScript contexts, ensure that characters are properly encoded to prevent script injection.
**CSS Encoding**: If inserting data into CSS, ensure it is properly escaped to prevent injection.
### 3. Use Safe Methods for Rendering Data
**Avoid Direct DOM Manipulation**: Use frameworks or libraries that handle DOM manipulation securely, such as React or Angular, which automatically escape data.
**Use Safe APIs**: Prefer using safe APIs that do not expose raw data to the DOM.
### 4. Implement Content Security Policy (CSP)
**Define CSP**: Use Content Security Policy headers to restrict where content can be loaded from. This can help mitigate XSS by blocking unauthorized script sources.

or To mitigate the **consequences** of a possible XSS vulnerability, also use a Content Security Policy (CSP). CSP is an HTTP response header that lets you declare the dynamic resources that are allowed to load depending on the request source.
### 5. HTTP Security Headers
**X-Content-Type-Options**: Set this header to nosniff to prevent browsers from interpreting files as a different MIME type.

OR To mitigate the **consequences** of a possible XSS vulnerability, set the HttpOnly flag for cookies. If you do, such cookies will not be accessible 
via client-side JavaScript.
