## Why is not possible to cancel an HTTP request?

### Introduction

As a developer, we will always have a doubt about how to cancel an HTTP request which is been triggered. In the frontend, we have an abort() call, or we can unsubscribe() from the observable. It will just not actually cancel the request but it will not take care of the triggered request. 

### TL;DR

To answer the question, in short, No, you can not cancel an HTTP Request once it is submitted. 

### HTTP is Stateless

**HTTP** is **stateless** by design, so what happens when there is no state for a request? It means we do not know the destination, or what is happening with that specific request at the back, but only can acknowledge the response. For example, if you have a REST API behind a load balancer. If you put a POST request to the API, you will not know which server going to serve your requests out of the many HTTP servers behind the load balancer. 

For such cases, we create ‘**cookies**’ or ‘**sessions**’ on our application end for our full-fledged web applications and extend the functionality of HTTP, to store the state of a request and follow it. For each form request, for example, we submit a state along with the app, to let the load balancer understand the state and follow me to the destination. Isn’t it? But we have to remember, that this is not an HTTP feature, this is done at the application level to add statefulness to HTTP requests.

What does this mean? It means, that as there is no state for REST, we are not aware of the destination here, but only the response. So how can we cancel requests, whose actual destination we are not aware of? Now you might think that, how about adding cookies and canceling it? Yes, we do that on the web applications layer, but can REST HTTP Requests be stateful? Not really, that is not by design of HTTP or REST, unfortunately.

### Is this to say that we can never cancel an API call?

If you are using REST, then it means you can never cancel the API call. If it gets submitted, it will continue processing in the backend even if you stop it in the frontend. But if ‘**Cancelling**’ is much more important for your application through the API call, then you must consider other alternatives, like **SOAP** or **RPC**. RPC is **stateful** API architecture, and it is possible to design a cancel request for this. Please note, that RPC doesn’t implement ‘cancel’ by default, but as this is stateful, you are able to design a ‘cancel’ request with the RPC call. Google has an RPC called ‘**gRPC**’, which is a stateful API architecture. That means, it is possible for you to implement cancel/abort or event rollback/restore a state with gRPC.

### Final Comments

1. REST - You can't cancel a request. 
2. RPC, SOAP - You can cancel a request.