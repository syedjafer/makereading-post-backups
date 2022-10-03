## Set cookie value from Server Side

### Introduction: 
In the previous post, we saw how to set a cookie using javascript. In the current post, we will see how we can set cookies from the server side. 

### Servide Side

In order to set the cookie from the server side, we need to use the **set-cookie** header in the response. 

The Set-cookie response header from the server directs the client to set a cookie on that particular domain. The implementation to actually create and store the cookie lies in the browser. For subsequent requests to the same domain, the browser automatically sets the Cookie request header for each request, thereby letting the server have some state to an otherwise stateless HTTP protocol. The browser uses the Domain and Path cookie attributes to determine which cookies are to be sent to a server. The server only receives name=value pairs, and nothing more.

### Explanation, 

We shall create a node file to have a better understanding, 

```javascript

const app = require("express")();

app.get("/", (req, res) => {
	res.setHeader("set-cookie", ["sample-cookie=1"]);
	res.send('Hello World');
});

app.listen(8080, ()=>console.log('listening...'));

```

Now, lets run this node app, 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663681112329/zZmtFq1GY.png align="left")

Let's check whether we have any cookies stored in browsers, 


![Screenshot from 2022-09-20 19-04-44.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663681157095/YOUMYbCQz.png align="left")

Now we can hit the node app, localhost:8080/


![Screenshot from 2022-09-20 19-05-34.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663681189939/Iezkilj74.png align="left")

On the initial hit, we can see the cookie is from the response headers also no details of cookies are mentioned in the request header. 

But on refresh, you will be able to see the cookie will be sent in request headers also, 


![Screenshot from 2022-09-20 19-06-19.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663681287756/hC5Fc9qvx.png align="left")

This cookie value will be stored in the browser itself, 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663681337069/rSLVZQxsr.png align="left")


### Final Thoughts

In this blog post, we just saw how to create a cookie from the server-side. In the upcoming post, we will see cookies with more details on their types and properties. 


