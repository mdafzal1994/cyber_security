https://learn.snyk.io/lesson/prototype-pollution/

https://portswigger.net/web-security/prototype-pollution

https://portswigger.net/web-security/prototype-pollution/javascript-prototypes-and-inheritance#the-prototype-chain


**What is prototype pollution?**

Prototype pollution is a JavaScript vulnerability that enables an attacker to add arbitrary properties to global object prototypes, which may then be inherited by user-defined objects.
This allows the attacker to tamper with the logic of the application and can also lead to denial of service or, in extreme cases, remote code execution.



**How do prototype pollution vulnerabilities arise?**

Prototype pollution vulnerabilities typically arise when a JavaScript function recursively merges an object containing user-controllable properties into an existing object, without first sanitizing the keys. This can allow an attacker to inject a property with a key like `__proto__`, along with arbitrary nested properties.

For example, an attacker could submit a payload like {"`__proto__`": {"isPolluted": true}} through an API or form, and all objects in the application could inherit the isPolluted property.



**What is a prototype in JavaScript?**


![image](https://github.com/user-attachments/assets/2be2fcaa-7e7b-43a3-8183-38d5aeb641ef)

Every object in JavaScript has a prototype, which is another object from which it inherits properties and methods. By default, JavaScript automatically assigns new objects one of its built-in prototypes.
For example, strings are automatically assigned the built-in **String.prototype**. You can see some more examples of these global prototypes below:

let myObject = {};
Object.getPrototypeOf(myObject);    // Object.prototype

let myString = "";
Object.getPrototypeOf(myString);    // String.prototype

let myArray = [];
Object.getPrototypeOf(myArray);	    // Array.prototype

let myNumber = 1;
Object.getPrototypeOf(myNumber);    // Number.prototype
Objects automatically inherit all of the properties of their assigned prototype, unless they already have their own property with the same key.
This enables developers to create new objects that can reuse the properties and methods of existing objects.

The built-in prototypes provide useful properties and methods for working with basic data types. For example, the String.prototype object has a toLowerCase() method. 
As a result, all strings automatically have a ready-to-use method for converting them to lowercase. This saves developers having to manually add this behavior to each new string that they create.

**how to detect prototype pollution vulnerabilities**

Manually, you can test an application by sending payloads like {"`__proto__`": {"polluted": true}} through user input fields or API endpoints, and then checking if unintended properties appear on global objects, such as {}.polluted."


POST /user/update HTTP/1.1
Host: vulnerable-website.com
...
{
    "user":"wiener",
    "firstName":"Peter",
    "lastName":"Wiener",
    "__proto__":{
        "foo":"bar"
    }
}
![image](https://github.com/user-attachments/assets/881514ea-6fdb-407f-97ca-fe3f497521a7)

**Prototype pollution mitigation**
1. **Sanitizing property keys**

One of the more obvious ways to prevent prototype pollution vulnerabilities is to sanitize property keys before merging them into existing objects.
 This way, you can prevent an attacker from injecting keys such as`__proto__`, which reference the object's prototype.

2. **Create objects without prototypes: Object.create(null)**
   
Another way to avoid prototype pollution is to consider using the Object.create() method instead of the object literal {} or the object constructor new Object() when creating new objects. 
This way, we can set the prototype of the created object directly via the first argument passed to Object.create(). If we pass null, the created object will not have a prototype and therefore cannot be polluted.

3. **Prevent any changes to the prototype: use Object.freeze()**
   
JavaScript comes with an Object.freeze() method, which we can use to prevent any changes to the attributes of an object.
Since the prototype is just an object, we can freeze it, too. We can freeze the default prototype by invoking Object.freeze(Object.prototype), which prevents the default prototype from getting polluted.
