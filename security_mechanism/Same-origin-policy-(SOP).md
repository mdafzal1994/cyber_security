#  What is the same-origin policy (SOP)?

ref:- https://www.invicti.com/learn/same-origin-policy-sop/

The same-origin policy (SOP) is a web security mechanism built into web browsers that influences how websites can access one another. 

The same-origin policy restricts scripts on one origin from accessing data from another origin. An origin consists of a URI scheme, domain and port number. For example, consider the following URL:

http://normal-website.com/example/example.html
This uses the scheme http, the domain normal-website.com, and the port number 80

Without SOP, a malicious website or web application could access another without restrictions. That would allow attackers to easily steal sensitive information from other websites or even perform actions on other sites without user consent.

SOP does not need to be turned on – it is automatically enabled in every browser that supports it. Developers must be aware of this mechanism when creating web apps that communicate with one another, so they know how to disable it in special circumstances safely.

### Diff csp vs sop
The same-origin policy is often confused with content security policies. The difference is that content security policies prevent calls to external resources (outbound) while the same-origin policy prevents calls from external resources (inbound). Also, content security policies are not enabled by default and must be defined by developers.
