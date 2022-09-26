## Does the CORS Preflight check is enabled for every request?

### Github and Live Demo

**Repository**: https://github.com/makereading/cors-simple-complex <br>
**Live** **Demo**: https://makereading.github.io/cors-simple-complex/index.html

### After the invention of CORS 
A CORS request consists of two sides: the client making the request, and the server receiving the request. On the client side, the developer writes JavaScript code to send the request to the server. The server responds to the request by setting special CORS-specific headers to indicate that the cross-origin request is allowed. Without both the client’s and the server’s participation, the CORS request will fail.

### Does preflight triggered for every call?

No, the preflight mechanism is not triggered for every request. There are some requests (simple requests), for which there is no call is been made. 

### What are Simple Requests?

**1. **A request that has the request method ```get```, ```post```, ```head``` and there are no custom request headers except for the following request header fields. 

- Accept
- Accept-Language
- Content-Language
- Content-Type
- DPR
- Downlink
- Save-Data
- Viewport-Width
- Width

**2. **Also, only three values for content type(content-type generally refers to that in post request, the settings in get request have no practical significance.) are allowed. 

- text/plain
- multipart/form-data
- application/x-www-form-urlencoded

**3. **No event listener is registered for any ```xmlhttprequestupload``` object in the request(not verified)

Xmlhttprequestupload object can be used XMLHttpRequest.upload Property access
Readablestream object is not used in the request(not verified)

### Let's check whether the above claim is true. 

We can use ```https://jsonplaceholder.typicode.com``` mocked external API for our experiment. 

**Simple Request**

```
		function simplereq(){
			fetch('https://jsonplaceholder.typicode.com/posts/1')
			  .then((response) => response.json())
			  .then((json) => console.log(json));
		}
```

![simple request](https://cdn.hashnode.com/res/hashnode/image/upload/v1663383816915/d_YuB9TdP.png align="left")

**Request header's of Simple Request**

![simple request headers](https://cdn.hashnode.com/res/hashnode/image/upload/v1663383865019/E2oo3_bQl.png align="left")

It follows the properties non-preflight request. 

**Complex Request**

```
function complexreq() {
			fetch('https://jsonplaceholder.typicode.com/posts', {
			  method: 'POST',
			  body: JSON.stringify({
			    title: 'foo',
			    body: 'bar',
			    userId: 1,
			  }),
			  headers: {
			    'Content-type': 'application/json; charset=UTF-8',
			  },
			})
			  .then((response) => response.json())
			  .then((json) => console.log(json));
		}
```

![complex requests - with preflight](https://cdn.hashnode.com/res/hashnode/image/upload/v1663383984338/SusgmCh1r.png align="left")

Let's look at the response headers, 


![Screenshot from 2022-09-17 08-22-49.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663384019567/4MR-PVOZZ.png align="left")

Here, you can see the content-type is application/json, 

![complex request](https://cdn.hashnode.com/res/hashnode/image/upload/v1663384068040/RcRHqLMxN.png align="left")

### Final Thoughts
Unlike simple requests, for "preflighted" requests the browser first sends an HTTP request using the OPTIONS method to the resource on the other origin, in order to determine if the actual request is safe to send. 

