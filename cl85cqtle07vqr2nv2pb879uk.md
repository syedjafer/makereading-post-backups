## How to handle a big request to avoid user holding time ?

### Introduction
In a normal request-response cycle, server will be getting the request from client, process the request and sends the response back to the client (browser). During this cycle, browser won't allow the user to interact with the application (since, the web app would be having some kind of loader to block the user until the request is completed.). In most of the cases, the process time would be in hundreds of milliseconds, so the user wont feel the pain. 

Also if the process is taking more time, then it may lead to request timeout aswell. In that case the response is lost by the user. 

In this post you will understand how to resolve the user holding process if there is a request with higher processing time. 

### Synchronous Request
Synchronous responses are typically used when the client must wait to receive the response before processing continues on the client side. A request is processed in real time, and the gateway returns the response via the HTTP connection created by the client. If a validation error occurs, the error is returned synchronously.

Eg: Consider a get request to collect the profile data of the user, 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662740919063/qUMKHYTY0.png align="left")

Now imagine, what would happen if the time taken by the server to process the request is more. For example, consider you are uploading a video to the server, which is taking some amount of time in the backend to complete it. So the browser will hold the user until the request is completed. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662740879425/eOHlHU3u4.png align="left")

### Asynchronous Request

Asynchronous request is also a synchronous request, but the server will put the heavy task in to the queue and will send the response immediately to the user stating the progress of the task with an id for future reference. so now the user is not blocked by the browser, and he has an **id** to check with the server about the status of the task (running at the background).


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662741206576/DJGcPrcCm.png align="left")

In an asynchronous mechanism, the task added to the queue would be taken and processed by a worker and those status will be updated. 

Client might use methods like polling, long polling, server sent events mechanism to know the status of the process.

### Final thoughts
In this blog post, we saw how an asynchronous process mechanism will help the user from being blocked by the client. But do you know how an asynchronous will be executing the tasks at the backend ? Whether it would be using a database or a queuing mechanism ? Let's see in the next post. 


