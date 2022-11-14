# Server Sent Events

### Introduction

While you are developing real-time projects, there is always a one-question mark on “**how to send messages/updates from server to client**”. We can talk about three different ways to perform server-to-client updates: Client polling, Web Socket, Server-Sent Events (SSE). When the web browser asks data from the server, it's called **Client Poll**; similarly, when the server keeps on pushing updates to the browser, its called **Server Push**. 

### Transfer of data from server-to-client

#### Client Polling

The client sends requests to the server at **regular intervals** for new updates.  It is easy to implement but not recommended. This technique does not provide a fully-real time system that depends on the request intervals (like n seconds).

In the polling technique, requests are sent and managed by the client side. Requests are sent by the client **even if there is no update on the server.**

#### Web Socket

Websocket is a very popular technology that provides** bi-directional data transfer** for client and server communication on real-time applications. Websocket is not based on HTTP protocol, so it requires additional installation and integrations to use it. It is difficult to implement compared to other technologies.

#### Server Sent Events

Server Sent Events is a technology that provides **asynchronous communication** with event stream from server to the client over HTTP for web applications. The server can send **un-directional messages/events** to the client and can update the client asynchronously. Almost every browser is supporting the SSE except Internet Explorer, Deno. (https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events#browser_compatibility)

### Server Sent Events

Server sent events is a **server push** techology that aims to establish a long persistent connection between the client and the server. It enables a server to automatically send updates to a client via an HTTP connection by making an initial request. They open a **single directional** channel between client and server for data delivery. 

#### EventSource API

SSE are commonly used to send message updates or **continuous data streams** to a browser client and designed to enhance native, cross-browser streaming through a JavaScript API called **EventSource**, through which a client requests a particular URL in order to receive an event stream. The EventSource API is standardized as part of **HTML5** by the WHATWG. The mime type for SSE is <i>**text/event-stream**</i>. They are designed to enhance the native crossbrowser streaming by establishing a unidirectional connection to send updates and continous data streams to the client. 

An EventSource instance **opens a persistent connection to an HTTP server**, which sends events in text/event-stream format. The connection remains open until closed by calling **EventSource.close()**.

![connection alive](https://cdn.hashnode.com/res/hashnode/image/upload/v1662429386393/n0sXlN_WI.png align="center")

#### Overview of the API

The client-side API is rather simple, and it hands-down beats the insane hacks required to get real-time events to the browser back in the bad old days.

The main points fo interest: 

- **new EventSource(url)** - this creates our EventSource object, which immediately starts listening for events on the given URL.
- **readyState** - as with XHR, we have a readyState for the EventSource that tells us if we’re connecting (0), open (1), or closed (2).
- **onopen, onmessage** - two events that we can listen for on the new EventSource object. By default, the message event will fire when new messages are received, unless the server explicitly sets the event type.
- **addEventListener** - not only can we listen for the default message event, but we can also listen for custom messages using the addEventListener on the EventSource object, just as if we were listening for a click event.
- **event.data** - as with most messaging APIs, the contents of the message reside in the data property of the event object. This is a string, so if we want to pass around an object, we need to encode and decode it with JSON.
- **close** - closes the connection from the client side.

It also support CORS using an optiosn argument to the EventSource Object ( 
{ withCredentials: true }).

### Workflow of SSE

Let’s look at how Client and Server are implemented in SSE

### Client Side Implementation

#### Flow
The Client creates a new EventSource object for receiving the events from the Server. EventSource takes a URL from where the events have to be drawn as “**text/event-stream**.” The client initiates by sending a get request,

<pre>
GET /api/v1/<url>
Accept: text/event-stream
Cache-Control: no-cache
Connection: keep-alive
</pre>

Let's discuss the parameters used,

- **Accept** : 'text/event-stream' indicates the client waiting for event stream from the server.
- **Cache-Control: no-cache** : It indicates that disabling the caching.
- **Connection: keep-alive** : It indicates the persistent connection. This request will give us an open connection which we are going to use to fetch updates. After the connection, the server can send messages when the events are ready to send by the server.

The Client receives the events and processes them in a **listener callback function**. Callback functions are event handlers, which are registered to handle events. A method named **addEventListener**  of the EventSource object is used to register these handlers. 

Suppose in the original event message, multiple data lines existed. In that case, these all will be concatenated together by the browser to form one string, and then only the callback functions are called. 

However, there is a limit to the SSE connections that one can have at any instant. Each browser is limited to only six SSE connections (for a particular domain).

#### Sample Client Code

```
let sse = new EventSource("http://localhost:8080/stream");
sse.onmessage = console.log
```

#### Closing the Event
 The Client has the facility to stop the events using the** .close() method of the EventSource** object. When this method is called, the Server detects this and stops sending events to the Client by closing the corresponding HTTP response.

### Server Side Implementation

#### Flow
As compared to Client Side Implementation, the server-side can be coded in any language like Java, C, Python, Go, etc., while Client-Side has relied on JavaScript.

The Server received an HTTP request from the Client and responded with valid Server Sent Event messages. The Server instructs the Client about the content type and guides the Client to keep the connection alive so that the events can be easily sent over the same established connection.

The Server can only accept EventSource requests, and at the same time, it needs to maintain a list of all the connected users for emitting new stream events. Server also has to maintain a history of messages so that it would be easy to catch up with the missed messages. Servers should also be able to remove the dropped connections from the connected user’s list.

#### Sample Code

```
from flask import Flask,jsonify
from flask_sse import sse
import logging
from apscheduler.schedulers.background import BackgroundScheduler
from flask_cors import CORS
import datetime
from helper import get_data,get_schd_time

app = Flask(__name__)
CORS(app)
app.config["REDIS_URL"] = "redis://localhost:6379/0"
app.register_blueprint(sse, url_prefix='/events')
log = logging.getLogger('apscheduler.executors.default')
log.setLevel(logging.INFO)
fmt = logging.Formatter('%(levelname)s:%(name)s:%(message)s')
h = logging.StreamHandler()
h.setFormatter(fmt)
log.addHandler(h)


def server_side_event():
    """ Function to publish server side event """
    with app.app_context():
        print(get_data())
        sse.publish(get_data(), type='dataUpdate')
        print("Event Scheduled at ",datetime.datetime.now())


sched = BackgroundScheduler(daemon=True)
sched.add_job(server_side_event,'interval',seconds=get_schd_time())
sched.start()


@app.route('/')
def index():
    return jsonify(get_data())


if __name__ == '__main__':
   app.run(debug=True,host='0.0.0.0',port=5000)

```
Referred from : https://github.com/sagar-khangan/flask-react-sse

#### Closing the Event

  The Server can also stop the event stream by sending a final event with a unique ID which corresponds to the “end of stream” event. Or the Server can also stop the event stream by closing the HTTP response connection with the Client.

### API Flows


![Event Stream Data](https://cdn.hashnode.com/res/hashnode/image/upload/v1662429131025/ZtuDZI-ro.png align="center")

In the above flask app, we have configured like for any seconds between 5-20 we will be triggering the event to the client. 


![request flow](https://cdn.hashnode.com/res/hashnode/image/upload/v1662429200223/HilR8hlO4.png align="center")

- Client: Sends the initial request like, 

<pre>
Request URL: http://localhost:5000/events
Request Method: GET
Status Code: 200 OK
Remote Address: 127.0.0.1:5000
Referrer Policy: strict-origin-when-cross-origin
</pre>

With the headers like, 

<pre>
GET /events HTTP/1.1
Accept: text/event-stream
Accept-Encoding: gzip, deflate, br
Accept-Language: en-GB,en-US;q=0.9,en;q=0.8
Cache-Control: no-cache
Connection: keep-alive
Host: localhost:5000
Origin: null
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: cross-site
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36
sec-ch-ua: "Chromium";v="104", " Not A;Brand";v="99", "Google Chrome";v="104"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Linux"
</pre>

- Server - After receiving the client request on enabling event stream with connection alive (refer the above headers). It will fire out the events on a timely basis (random seconds between 5 to 20). 

The Response headers will look like, 

<pre>
Access-Control-Allow-Origin: null
Connection: close
Content-Type: text/event-stream; charset=utf-8
Date: Tue, 06 Sep 2022 01:32:57 GMT
Server: Werkzeug/2.2.2 Python/3.8.10
Transfer-Encoding: chunked
Vary: Origin
</pre> 

The event message will consist of the below values (which would be considered for triggering request in event of failure.)

<pre>
isTrusted: true
bubbles: false
cancelBubble: false
cancelable: false
composed: false
currentTarget: EventSource {url: 'http://localhost:5000/events', withCredentials: false, readyState: 1, onopen: null, onmessage: null, …}
data: "some Data"
defaultPrevented: false
eventPhase: 0
lastEventId: ""
origin: "http://localhost:5000"
path: []
ports: []
returnValue: true
source: null
srcElement: EventSource {url: 'http://localhost:5000/events', withCredentials: false, readyState: 1, onopen: null, onmessage: null, …}
target: EventSource {url: 'http://localhost:5000/events', withCredentials: false, readyState: 1, onopen: null, onmessage: null, …}
timeStamp: 592160.3000000003
type: "dataUpdate"
userActivation: null

</pre>


![event connection](https://cdn.hashnode.com/res/hashnode/image/upload/v1662429280491/COw8K_Ysr.png align="center")

One of the important value is the **lastEventId**. On connection failure, the client will send the request again with this last event id to receive the missed messages. 

At the end of events, any one of them can trigger the close connection call to end the stream. 

### Handling Connection Failure

  In the real world, nothing can be fully persistent. In Server Side Events, the connection is established via HTTP, and the connection may probably get dropped out due to the network inconsistency. This may affect the event transfer and sometimes even results in an incomplete event message. Hence there must be some mechanism to deal with this issue, right!
  
  
  To mitigate this, the Client tries to reconnect to an event source by sending the ID of the last event as HTTP header “**Last-Event-ID**” to the Server via a new HTTP request. The Server listens to this and again start sending events that have happened since the supplied ID.

### Properties of SSE
1. It is a server sent a communication that is carried out from server to web browser client only. It supports one-way communication.
2. It doesn’t support binary. Its uses only **UTF-8**.
3. It has a maximum open connection limit.
4. It has built-in support for re-connect and event **ID**.
5. You should optionally maintain a history of messages so that reconnecting clients can catch up on missed messages.


### Usage Areas of SSE
1. A real-time chart of streaming stock prices.
2. Real-time news coverage of an important event (posting links, tweets, and images).
3. A monitor for server statistics like uptime, health, and running processes.
4. A live Twitter wall fed by Twitter’s streaming API.
5. Server-Sent Events are highly applicable in systems where there is a need for real-time unidirectional data flows.
6. Alarm/Alert Projects.
7. E-commerce Projects (notify whenever the user needs the information)

### Why not use WebSockets ?

- EventSource (as we saw earlier) works over regular HTTP and can therefore be replicated entirely using JavaScript if it’s not available natively. 

- You should always use the right technology for the job. If your real-time data is sourced from your web site, and the user doesn’t interact in real-time, it’s likely you need Server-Sent Events.

### Final Thoughts

1. The event source is very good to update or refresh browser data with real-time data. 
2. This protocol is very less complicated because it gives flexibility by not adding any external JavaScript library. 
3. JavaScript itself provides the EventSource interface to receive the real-time data or message sent by the server.
4. Light Weight than Web Sockets
5. HTTP and HTTP/2 Compatible

### Code

#### Frontend

%[https://gist.github.com/syedjafer/7f5231d9d1e45f32a11e37e8975ea2a1#file-sse-index-html]


#### Backend

- app.py
%[https://gist.github.com/syedjafer/9dc46c5cf4248ff7e575643f8280e3fd#file-app-py]

- helper.py
%[https://gist.github.com/syedjafer/3bdef700d77afda65565902eae8b9fa8#file-helper-py]