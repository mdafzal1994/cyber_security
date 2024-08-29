# Cross-site Scripting (XSS)

reflected,stored XSS https://www.acunetix.com/websitesecurity/cross-site-scripting/

DOM XSS https://www.invicti.com/learn/dom-based-cross-site-scripting-dom-xss/

## How to Prevent Cross-site Scripting (XSS) 
 XSS attacks occur when an attacker injects malicious scripts into web pages viewed by other users. Here's a comprehensive approach to preventing XSS:

### 1. Input Validation and Sanitization
**Validate Input**: Ensure that input conforms to expected formats, lengths, and types. Use server-side validation to check for valid input.
**Sanitize Input**: Remove or escape characters that could be used in an XSS attack. For example, escape characters like <, >, ", and ' in HTML contexts.
### 2. Output Encoding 
use proper Encoding techniques when including user input in server responses
**HTML Encoding**: Focuses on converting special characters in user input into a safe format to prevent them from being interpreted as code when displayed or used in a specific context. (e.g., < becomes '& lt;).
**JavaScript Encoding**: If inserting data into JavaScript contexts, ensure that characters are properly encoded to prevent script injection.
**CSS Encoding**: If inserting data into CSS, ensure it is properly escaped to prevent injection.

Note: Difference in Sanitization and  Escaping Techniques

**Sanitization**: Focuses on removing or altering harmful content from user input before processing or storing it.
Eg . <img width="548" alt="image" src="https://github.com/user-attachments/assets/cfdbee56-c500-4842-a0f0-0ee560d641ca">


**Escaping**: Focuses on converting special characters in user input into a safe format to prevent them from being interpreted as code when displayed or used in a specific context.
eg .<img width="549" alt="image" src="https://github.com/user-attachments/assets/b9f779d2-1493-43c5-ac0e-4655241155fd">


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
