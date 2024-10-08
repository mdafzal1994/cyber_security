**HTTP Request Smuggling** or **HTTP Desync Attacks** occur when there’s a mismatch in how frontend and backend servers handle HTTP requests (consider a load balancer or a CDN is sitting in front of the origin additionally handling the request. ). This can lead to confusion about where one request ends and another begins. In modern applications, especially those using microservices, it can be challenging to ensure that all components process requests in the same way. If they don’t, it creates vulnerabilities that attackers can exploit.


eg. CL.TE vulnerability which means the frontend honors the Content-Length (CL) header, and the backend honors the Transfer-Encoding (TE) header. Since we now see how desync happens when both headers are present for a CL.TE vulnerability


reff- https://sc.scomurr.com/http-request-smuggling-cl-te-vulnerability/

https://siunam321.github.io/ctf/portswigger-labs/HTTP-Request-Smuggling/smuggling-1/
