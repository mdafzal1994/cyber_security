WEB CACHE POISONING - BRIEF

![image](https://github.com/user-attachments/assets/76891678-8ccf-4b79-a261-ce2a0ffb2efe)


1. what is cache ?
2. what is purpose of cache?

Web cache poisoning is an attack where an attacker takes advantage of flaws in the caching mechanism. They attempt to store an altered and malicious response in the cache entry, forcing the website to serve malicious information to its users. 

Web caching allows faster and more smooth surfing by downloading a local copy of a resource and preventing subsequent browser requests from being sent to the remote server. Attackers can exploit vulnerable applications by injecting malicious data into cache memory, which prompts the webserver to send the user a malicious HTTP response.

![image](https://github.com/user-attachments/assets/a5c0f8ba-376f-4a11-9cc0-f768441ed3f6)


**What is a web cache key?**
- **Web Cache Key**: A mechanism used by web caches to determine whether a request can be served from cached content or needs to be forwarded to the web server.
- **Purpose**: The cache key helps decide whether the request is similar enough to a previous one, allowing a cached response to be returned instead of requesting a new one from the server.
- **Components**: A cache key is made up of selected HTTP request elements, including parts of the request line and headers, and their corresponding values.
- **Keyed vs. Unkeyed Inputs**:
  - **Keyed Inputs**: Parts of the HTTP request that are included in the cache key comparison (e.g., path, host, specific headers).
  - **Unkeyed Inputs**: Other parts of the request that are not used for comparison in the cache key.
- **Common Cache Key Elements**: 
  - Path and host are typically included in almost all cache keys.
  - Other header values may also be considered depending on the cache configuration.
  - Sometimes only specific portions of the path or query parameters are included in the cache key, rather than the full path.

![image](https://github.com/user-attachments/assets/8307165b-4d07-457d-bd6e-0226b51b412c)      ![image](https://github.com/user-attachments/assets/c2af427d-b6ca-45b9-a1fd-c783d0a57b0a)

Although the requests have different Accept-Language headers, both will receive a page in English if the first request is cached. The Accept-Language header was used in both requests but not cached, which makes it an unkeyed input. In this instance, attackers can use unkeyed input to serve malicious content to the users.

**Param miner tool**  can be used for listing the Unkeyed Inputs 

**How to prevent web cache poisoning attacks?**

### How to Prevent Web Cache Poisoning Attacks


- **Sanitize Inputs**: Ensure your app doesn't use unsanitized user input (like HTTP headers) in responses to prevent attacks (e.g., Host header attacks).
- **Fix XSS Vulnerabilities**: Web cache poisoning can spread cross-site scripting (XSS) attacks, so secure your app against XSS.
- **Sanitize Response Headers**: Don't generate response headers based on request headers without proper sanitization.
- **Follow Security Best Practices**: Never trust user input and always validate it.
- **Cache Only GET and HEAD Requests**: Do not cache POST requests, as they aren't designed to be cacheable and can lead to poisoning attacks.
- **Reject GET Requests with a Body**: Configure your cache to block such requests.
- **Cache Static Content Only**: Limit caching to static files like images or standalone scripts to reduce risks.


