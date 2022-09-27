## Same-Origin Policy

### Introduction

The same-origin policy is a **critical security mechanism** that restricts how a document or script loaded by one **origin** can interact with a resource from another origin. It is a **browser security feature** that restricts a document or script loaded by one origin, to access or interact with documents or scripts from another origin.

In this blog post, we will see the policies of same-origin and how it behaves with examples. 

### What is Origin? 

Origin in same-origin is made up of the, 
1. the **protocol** (HTTP, HTTPS, etc...)
2. the **host** (domain name)
3. the **port** number. 

Two URLs have the same origin if the protocol, port (if specified), and host are the same for both. 

For reference, the following table gives an overview of typical outcomes for checks against the URL "http://www.makereading.com".

| URL      | Status | Description                                  |
|--------------------------------------|:-------:|---------------------------------------------------------------|
| http://www.makereading.com/foss      | Success | Same protocol, host and port                                  |
| http://www.makereading.com/cp        | Success | Same protocol, host and port                                  |
| http://www.makereading.com:9000/foss | Failure | Same protocol and host but different port                     |  
| https://www.makereading.com/foss     | Failure | Different protocol                                            |
| https://syedjafer.github.io          | Failure | Different host                                                |
| https://makereading.com/foss         | Failure | Different host (exact match required; here www is not there ) |

### Example

If frontend and backend are deployed in the same server with the same origin then they can communicate easily. But if there is any other external server trying to communicate then it will block the request. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663413892558/fk0SIbLvE.png align="center")

### Why is the same-origin policy necessary?

A browser can load and display resources from multiple sites at once. You might have multiple tabs open at the same time, or a site could embed multiple iframes from different sites. If there is no restriction on interactions between these resources, and a script is compromised by an attacker, the script could expose everything in a user's browser.

When a browser sends an HTTP request from one origin to another, any **cookies**, including **authentication session cookies**, relevant to the other domain are also sent as part of the request. This means that the response will be generated within the user's session, and include any relevant data that is specific to the user. Without the same-origin policy, if you visited a malicious website, it would be able to read your emails from GMail, private messages from Facebook, etc.


### How is the same-origin policy implemented?
The same-origin policy generally controls the access that JavaScript code has to content that is loaded cross-domain. Cross-origin loading of page resources is generally permitted. For example, the SOP allows the embedding of images via the ```<img>``` tag, media via the ```<video>``` tag and JavaScript includes the ```<script>``` tag. However, while these external resources can be loaded by the page, any JavaScript on the page won't be able to read the contents of these resources.



### Benefits of same-origin policy

Here are some benefits of the same-origin policy.

**1. ** Prevents Malicious Attacks
The same-origin policy helps remove potentially malicious attack vectors on a webpage or origin, especially on webpages that house or store sensitive user data. It does this by waging perceived potential attacks spot on before they escalate.

If you implement the same-origin policy on your webpage or browser, there's a significant decrease in malicious attacks.

**2. ** Restriction of Interaction
The same-origin policy helps restrict how a script from a website interacts with a script of another webpage.

When there's a restriction in the shared data, all resources from an origin are highly protected. A vivid example of this is the one we mentioned about myexample.com scoping the script of example.com.

**3. ** Prevent Unauthorized Read Access
The same-origin policy helps in protecting sites that use authentication sessions. This can be seen in sites that use the "remember me" functionality.

The policy works by keeping privileged information safe. It prevents unauthorized read access from one origin to another.

**4. ** Effective for Cookies
The same-origin policy prohibits an attacker from reading or establishing cookies on the targeted source domain. It prevents them from inserting a valid token into their devised form. The permit doesn't need to be stashed on the server, which is an added benefit of this technique over the timing pattern.


### Is there any exceptions to the same-origin policy

**1. **Some objects are writable but not readable cross-domain, such as the location object or the **location.href** property from iframes or new windows.

**2. **Some objects are readable but not writable cross-domain, such as the length property of the window object (which stores the number of frames being used on the page) and the closed property.

**3. **The replace function can generally be called cross-domain on the location object.

**4. **You can call certain functions cross-domain. For example, you can call the functions close, blur, and focus on a new window. The postMessage function can also be called on iframes and new windows in order to send messages from one domain to another.

**5. **Due to legacy requirements, the same-origin policy is more relaxed when dealing with cookies, so they are often accessible from all subdomains of a site even though each subdomain is technically a different origin. You can partially mitigate this risk using the HttpOnly cookie flag.


### What is permitted and what is blocked?
Generally, embedding a cross-origin resource is permitted, while reading a cross-origin resource is blocked. 

**1. Iframes: ** Cross-origin embedding is usually permitted (depending on the X-Frame-Options directive), but cross-origin reading (such as using JavaScript to access a document in an iframe) isn't.

**2. CSS: ** Cross-origin CSS can be embedded using a <link> element or an import in a CSS file. The correct Content-Type header may be required.

**3. forms: ** Cross-origin URLs can be used as the action attribute value of form elements. A web application can write form data to a cross-origin destination.

**4. images: **	Embedding cross-origin images is permitted. However, reading cross-origin image data (such as retrieving binary data from a cross-origin image using JavaScript) is blocked.

**5. multimedia: **	Cross-origin video and audio can be embedded using <video> and <audio> elements.

**6. script: **	Cross-origin scripts can be embedded; however, access to certain APIs (such as cross-origin fetch requests) might be blocked.

### Let's tryout the above exceptions 

**1. Iframes: ** <br>

Even though embedding is usually permitter, since the iframe is not on the same origin as the host webpage, the browser doesn't allow reading of the embedded page.

[IFRAME same origin policy](https://makereading.github.io/same-origin-policy-experiment/iframe.html)

<iframe src="https://makereading.github.io/same-origin-policy-experiment/iframe.html" style="height:300px;width:100%;" title="Iframe Example"></iframe>

**2. Forms: ** <br>

Form data can be written to a cross-origin URL specified in the action attribute of the <form> element.
 
[Form submission](https://makereading.github.io/same-origin-policy-experiment/forms.html)

<iframe src="https://makereading.github.io/same-origin-policy-experiment/forms.html" style="height:300px;width:100%;" title="forms"></iframe>

**3. Forms with X-Frame-Options: same-origin **

If X-Frame-Options are added to the header, then embedding iframe is not possible. For more details, please check on https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options


**4. imgs **
 
Embedding cross-origin images are permitted. Although the image is of a different origin, loading it as an img source does not require CORS. However, accessing the binary of the image using JavaScript such as getImageData, toBlob or toDataURL requires explicit permission by CORS.

[Canvas Img](https://makereading.github.io/same-origin-policy-experiment/canvas-img.html)

<iframe src="https://makereading.github.io/same-origin-policy-experiment/canvas-img.html" style="height:300px;width:100%;" title="forms"></iframe>

### Is Same Origin Policy enough?
Same Origin Policy enforces some security but it is not enough to prevent all kinds of attacks. Some of them are:

- **Cross-Site Request Forgery(CSRF)** attack which basically takes advantage of different origins. This is why anti-CSRF tokens should be used in addition to the Same Origin Policy.
- **Cross-Site Scripting(XSS)** attacks can also be prevented by the Same Origin Policy but in order to prevent it will have to restrict the loading of scripts from external sources, which may break the functionality of web applications.


### Is there any problem with the Same-Origin Principle?

Since SOP is very restrictive. We can't enable communication between different servers. So some mechanism is needed to enable cross-domain communications. 

There are some ways like setting up values of the document.domain. This special property allows you to relax SOP for a specific domain, but only if it's part of your FQDN (fully qualified domain name). For example, you might have a domain marketing.example.com and you would like to read the contents of that domain on example.com. To do so, both domains need to set document.domain to example.com. Then SOP will allow access between the two domains despite their different origins. In the past, it was possible to set the document.domain to a TLD such as com, which allowed access between any domains on the same TLD, but now modern browsers prevent this.

There is also another mechanism called CORS - Cross Origin Resource Sharing Protocol which also enables cross-domain communication with different servers under some conditions. We will discuss more this in upcoming posts. 

