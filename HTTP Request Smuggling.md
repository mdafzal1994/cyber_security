**HTTP Request Smuggling** or **HTTP Desync Attacks** occur when there’s a mismatch in how frontend and backend servers handle HTTP requests (consider a load balancer or a CDN is sitting in front of the origin additionally handling the request. ). This can lead to confusion about where one request ends and another begins. In modern applications, especially those using microservices, it can be challenging to ensure that all components process requests in the same way. If they don’t, it creates vulnerabilities that attackers can exploit.


eg. CL.TE vulnerability which means the frontend honors the Content-Length (CL) header, and the backend honors the Transfer-Encoding (TE) header. Since we now see how desync happens when both headers are present for a CL.TE vulnerability

Types of HTTP Smuggling Attacks
There are three main ways to exploit HRS vulnerabilities:

CL-TE: the front-end server uses the Content-Length header and the back-end server uses the Transfer-Encoding header.
TE-CL: the front-end server uses the Transfer-Encoding header and the back-end server uses the Content-Length header.
TE-TE: the front-end and back-end servers both support the Transfer-Encoding header, but one of the servers can be induced not to process it by obfuscating the header in some way.


> Disable reuse of back-end connections
> Use HTTP/2 end to end and disable HTTP downgrading if possible. HTTP/2 uses a robust mechanism for determining the length of requests and, when used end to end, is inherently protected against request smuggling.
> Make the front-end server normalize ambiguous requests and make the back-end server reject any that are still ambiguous, closing the TCP connection in the process.
> If you route traffic through a forward proxy, ensure that upstream HTTP/2 is enabled if possible.
> Prefer a WAF that has built-in mitigation to detect abnormal requests

reff-
https://brightsec.com/blog/http-request-smuggling-hrs/
https://sc.scomurr.com/http-request-smuggling-cl-te-vulnerability/

https://siunam321.github.io/ctf/portswigger-labs/HTTP-Request-Smuggling/smuggling-1/
