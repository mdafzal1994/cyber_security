WEB CACHE POISONING - BRIEF

1. what is cache ?
2. what is purpose of cache?

Web cache poisoning is an attack where an attacker takes advantage of flaws in the caching mechanism. They attempt to store an altered and malicious response in the cache entry, forcing the website to serve malicious information to its users. 

Web caching allows faster and more smooth surfing by downloading a local copy of a resource and preventing subsequent browser requests from being sent to the remote server. Attackers can exploit vulnerable applications by injecting malicious data into cache memory, which prompts the webserver to send the user a malicious HTTP response.

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


