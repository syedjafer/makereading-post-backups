# What is the Purpose of the Preflight request?

### Introduction

In your software development, you might have noticed an OPTIONS request is been sent for all kinds of complex requests (requests with custom headers). This type of request is a Preflight request. In this post, you will understand the reason for the Preflight request before sending the actual request. 

### CORS - Cross Origin Resource Sharing

Cross-origin resource sharing is a mechanism that allows restricted resources on a web page to be requested from another domain outside the domain from which the first resource was served. This CORS is been introduced in **2004**. From that time both browsers and servers who are aware of CORS were able to communicate cross-domain. But what about the servers and millions of lines of code that are running in old servers? They aren't aware of CORS, they believe in Same-Origin Policy. So preflight is a mechanism to safeguard old servers and servers that aren't aware of CORS. 


### What is Preflight?

The primary intent of pre-flighting is to ensure that servers aren't suddenly sent cross-origin browser-based requests that they could have never received before the CORS spec was implemented.

Before the CORS spec, it was impossible to send any browser-based cross-origin requests other than GET or POST. The browser simply would not allow you to fire up an XHR instance, set the method to PUT (for example), and send it off to an endpoint on a different origin. You couldn't send GET or POST cross-origin requests via XHR either, but you COULD send a cross-origin GET or POST via a form submit, or a cross-origin GET via an <img> or script tag, for example (which made JSONP the only option pre-CORS). Once browsers implemented the CORS spec, this changed. Now it IS possible to send any cross-origin ajax request, provided the server opts in.



### Preflight requests for simple and complex request

The CORS spec defines "simple" methods (GET and POST) along with "simple" request headers. These correspond to the types of cross-origin requests that you could already send from the browser pre-CORS spec. Non-simple cross-origin requests, such as PUT or POST/GET requests with an X-header (for example) could not be sent from a browser pre-CORS spec. So, for these types of requests, the concept of preflight was written into the spec to ensure servers do not receive these types of non-simple cross-origin browser-based requests without explicitly opting in. In other words, if you don't want to allow these types of requests, you don't have to change your server at all. The preflight will fail, and the browser will never send the underlying request.



### Explanation


Let's imagine that a browser user is logged into their banking site at ```A.com```. When they navigate to the malicious B.com, that page includes some Javascript that tries to send a ```DELETE``` request to ```A.com/account```. Since the user is logged into ```A.com```, that request, if sent, would include cookies that identify the user.

Before CORS, the browser's Same Origin Policy would have blocked it from sending this request. But since the purpose of CORS is to make just this kind of cross-origin communication possible, that's no longer appropriate.

The browser could simply send the DELETE and let the server decide how to handle it. But what if ```A.com``` isn't aware of the CORS protocol? It might go ahead and execute the dangerous ```DELETE```. It might have assumed that—due to the browser's ```Same Origin Policy``` it could never receive such a request, and thus it might have never been hardened against such an attack.

To protect such non-CORS-aware servers, then, the protocol requires the browser to first send a preflight request. This new kind of request is something that only CORS-aware servers can respond to properly, allowing the browser to know whether or not it's safe to send the actual DELETE.



### But the attacker can directly send DELETE from other tools (cURL, postman) right?



Sure, but such a request won't include the user's cookies. The attack that this is designed to prevent relies on the fact that the browser will send cookies (in particular, authentication information for the user) for the other domain along with the request.

That sounds like Cross-Site Request Forgery, where a form on site ```B.com``` can be submitted to ```A.com``` with the user's cookies and do damage.

That's right. Another way of putting this is that preflight requests were created so as to not increase the CSRF attack surface for non-CORS-aware servers.

But POST is listed as a method that doesn't require preflights. That can change state and delete data just like a DELETE!

That's true! CORS does not protect your site from CSRF attacks. Then again, without CORS you are also not protected from CSRF attacks. The purpose of preflight requests is just to limit your CSRF exposure to what already existed in the pre-CORS world.












