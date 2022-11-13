# Need of Cookie's

### Need of Cookie: 

You are using an online shopping website. You have some items in your cart. Now you are moving to the checkout page and are surprised to see that there are no items in the cart. This is because HTTP is stateless. So we will be needing a mechanism to maintain the state of the application. Thus the cookie was born. 

### Stateful Cookie inside Stateless HTTP:

HTTP is stateless. This means that HTTP itself has no way to keep track of a user’s previous activities. One way to create a state is by using cookies. A cookie is generally used to store the username and password information on a computer so that the user does need not to enter this information each time when visits a website again. Cookies are a convenient way to carry information from one session on a website to another, or between sessions on related websites, without having to burden a server machine with massive amounts of data storage.


### A Brief History of Cookie: 

Cookies were developed for the first time in 1994 by Lou Montulli, an employee of Netscape Communications. Along with John Giannandrea, Lou developed cookies as a solution to make e-commerce shopping carts possible.

The first actual real-world application of cookies on the web was to determine whether visitors to the Netscape website had been there previously.

### How it became popular:

Initially, cookies were accepted by default by all supported browsers and very few end-users had any idea about their presence or use. That all changed in February of 1996 when the Financial Times published a piece detailing their existence, purpose, and use.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663645080069/Wm7-q2sPu.png align="left")

What followed was intense media scrutiny for the next few years due to the privacy risks inherent to visitor tracking.

The Internet Engineering Task Force (IETF) was given the job of coming up with a formal cookie specification that agreed with the concerns expressed by the media.

Of particular concern were the risks associated with allowing third-party cookies. These are more commonly known as tracking cookies. IETF attempted to require that third-party cookies be explicitly disallowed or only allowed after explicit user opt-in.

> IETF Document on HTTP State Management - https://www.rfc-editor.org/rfc/rfc2109

However, the leading browser developers at that time, Netscape and Microsoft, ignored the IETF recommendation and went along with online advertiser wishes to allow third-party tracking cookies.

In the upcoming blog posts, we will see the usage, properties, types, and security of cookies. 