
**Content Security Policy (CSP)** is a crucial security mechanism used in web applications to mitigate risks associated with Cross-Site Scripting (XSS) and 
other code injection attacks. By defining a set of directives in the HTTP response headers, CSP allows developers to specify which sources of content are trusted,
such as scripts, styles, and images. This reduces the attack surface by preventing unauthorized scripts from executing and blocking potentially harmful content from
being loaded.

The Content-Security-Policy header allows you to restrict which resources (such as JavaScript, CSS, Images, etc.) can be loaded, and the URLs that they can be loaded
from, to enable this configure the response header with Content-Securiy-Policy.



**How CSP Works**

When a browser loads a web page that has a Content Security Policy, it will check the CSP rules to see whether the content on the page is allowed to load or not .

If the content is not allowed to load then the browser will block it from loading, and will display an error message also . This helps to prevent attackers from 
code injections and cross-site-scripting (XSS) attacks into a page, and can help protect users from attacks.

Directives: Some common directives include:

**default-src**: Serves as a fallback for other resource types.

**script-src**: Specifies valid sources for JavaScript.

**style-src**: Specifies valid sources for CSS styles.

**img-src**: Specifies valid sources for images.

**connect-src**: Specifies valid sources for XMLHttpRequests (AJAX).

**frame-ancestors**: Restricts which domains can embed the page in a frame.

**Content Restrictions**: If a resource is not from an allowed source as defined in the CSP, the browser will block it from loading. This helps prevent the 
execution of potentially harmful scripts.


![image](https://github.com/user-attachments/assets/28a0bf50-374c-46b1-9a6a-5dcc9a811186)



To block the loading of any content apart from scripts loaded from domain example.com over https.


Content-Security-Policy: default-src 'none'; script-src https://example.com



==========================================================================================================


	// server.js
const express = require('express');
const app = express();
const PORT = 3000;

// Set CSP headers
app.use((req, res, next) => {
    res.setHeader("Content-Security-Policy", "default-src 'self'; script-src 'self'; style-src 'self' 'unsafe-inline';");
    next();
});

// Serve a simple HTML page
app.get('/', (req, res) => {
    res.send(`
        <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="UTF-8">
            <title>CSP Demo</title>
            <style>
                body { font-family: Arial, sans-serif; }
            </style>
        </head>
        <body>
            <h1>Hello, CSP!</h1>
            <p>This page has a Content Security Policy.</p>
            <script>
                console.log('This script runs because it is from the same origin.');
            </script>
            <script src="https://example.com/some-script.js"></script> <!-- This will be blocked -->
        </body>
        </html>
    `);
});

// Start the server
app.listen(PORT, () => {
    console.log(`Server is running on http://localhost:${PORT}`);
});
