# Can we store cookies in REST API?


A RESTful API service may send cookies just like a regular web service. Cookies don't always violate the REST pattern. For example, the server might want to have its client remember a certain state so that it can provide this state when requesting another resource at a later point.

However, cookies should not be used by a REST API if they are meant to maintain a client session on the server, such as a Session Token. This would violate the statelessness of the REST endpoint, as the server is required to know the state of each client in order to provide them with the requested resources.

**Cookies** if used to **maintain the client state at the client**, for the client, of the client and by the client then they are restful.

If you are storing **server state into the cookie** then you are basically just shifting the load to the client which** isn't restful**.

### Comments from https://www.ics.uci.edu/ by Roy Fielding 
Cookies also violate REST because they allow data to be passed without sufficiently identifying its semantics, thus becoming a concern for both security and privacy. The combination of cookies with the Referer [sic] header field makes it possible to track a user as they browse between sites.

As a result, cookie-based applications on the Web will never be reliable. The same functionality should have been accomplished via anonymous authentication and a true client-side state. A state mechanism that involves preferences can be more efficiently implemented using judicious use of context-setting URI rather than cookies, where judicious means one URI per state rather than an unbounded number of URI due to the embedding of a user-id. Likewise, the use of cookies to identify a user-specific "shopping basket" within a server-side database could be more efficiently implemented by defining the semantics of shopping items within the hypermedia data formats, allowing the user agent to select and store those items within their own client-side shopping basket, complete with a URI to be used for check-out when the client is ready to purchase.


Most of the time it would be difficult to stick to the rules. 