### Web Cache Deception

Web cache deception is a vulnerability that enables an attacker to trick a web cache into storing sensitive, dynamic content. It’s caused by discrepancies
between how the cache server and origin server handle requests.

In a web cache deception attack, An attacker convinces a victim to click on or visit a malicious URL, inducing the victim’s browser to make an ambiguous request for 
sensitive content. The cache misinterprets this as a request for a static resource and stores the response. The attacker can then request the same URL to access
the cached response, gaining unauthorized access to private information.

Note

It’s important to distinguish web cache deception from web cache poisoning. While both exploit caching mechanisms, they do so in different ways:

 > Web cache poisoning manipulates cache keys to inject malicious content into a cached response, which is then served to other users.
 > Web cache deception exploits cache rules to trick the cache into storing sensitive or private content, which the attacker can then access.

![image](https://github.com/user-attachments/assets/63ac5d8b-5fa2-46bf-bbc2-882a9ddb9974)

### Cache keys
When the cache receives an HTTP request, it must decide whether there is a cached response that it can serve directly, or whether it has to forward the request to
the origin server. The cache makes this decision by generating a 'cache key' from elements of the HTTP request. Typically, this includes the URL path and query
parameters, but it can also include a variety of other elements like headers and content type.

If the incoming request's cache key matches that of a previous request, the cache considers them to be equivalent and serves a copy of the cached response.

### Cache rules
Cache rules determine what can be cached and for how long. Cache rules are often set up to store static resources, which generally don't change frequently and 
are reused across multiple pages. Dynamic content is not cached as it's more likely to contain sensitive information, ensuring users get the latest data directly
from the server.

Web cache deception attacks exploit how cache rules are applied, so it's important to know about some different types of rules, particularly those based on
defined strings in the URL path of the request. For example:

**Static file extension rules** - These rules match the file extension of the requested resource, for example .css for stylesheets or .js for JavaScript files.
**Static directory rules** - These rules match all URL paths that start with a specific prefix. These are often used to target specific directories that contain
only static resources, for example /static or /assets.
**File name rules** - These rules match specific file names to target files that are universally required for web operations and change rarely, such as robots.txt 
and favicon.ico.

Caches may also implement custom rules based on other criteria, such as URL parameters or dynamic analysis.


### Exploiting Static Extension Cache Rules

Cache rules often target static resources by matching common file extensions like .css or .js. This is the default behavior in most CDNs.

If there are discrepancies in how the cache and origin server map the URL path to resources or use delimiters, an attacker may be able to craft a request for
a dynamic resource with a static extension that is ignored by the origin server but viewed by the cache.

### Path Mapping Discrepancies

URL path mapping is the process of associating URL paths with resources on a server, such as files, scripts, or command executions. There are a range of different
mapping styles used by different frameworks and technologies. Two common styles are traditional URL mapping and RESTful URL mapping.

Traditional URL mapping represents a direct path to a resource located on the file system. Here’s a typical example:

http://example.com/path/in/filesystem/resource.html

http://example.com points to the server.

/path/in/filesystem/ represents the directory path in the server’s file system.

resource.html is the specific file being accessed.

In contrast, REST-style URLs don’t directly match the physical file structure. They abstract file paths into logical parts of the API:

http://example.com/path/resource/param1/param2

http://example.com points to the server.

/path/resource/ is an endpoint representing a resource.

param1 and param2 are path parameters used by the server to process the request.

**Discrepancies in how the cache and origin server map the URL path to resources can result in web cache deception vulnerabilities**. 
Consider the following example:

http://example.com/user/123/profile/wcd.css


An origin server using REST-style URL mapping may interpret this as a request for the /user/123/profile endpoint and returns the profile information for user
123, ignoring wcd.css as a non-significant parameter.

A cache that uses traditional URL mapping may view this as a request for a file named wcd.css located in the /profile directory under /user/123. It interprets
the URL path as /user/123/profile/wcd.css. If the cache is configured to store responses for requests where the path ends in .css, it would cache and serve the
profile information as if it were a CSS file.
