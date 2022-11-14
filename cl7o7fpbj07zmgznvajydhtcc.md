# When not to use Local storage in your development ?

### Introduction

 You may get a Storage object for the Document's origin using the [localStorage](https://syedjaferk.hashnode.dev/the-browsers-localstorage) property of the window (browser window object) interface; the data is preserved throughout browser sessions. In local storage, data is preserved **for a very long period (with no expiration date.)**. Depending on the developer's taste, this may be one day, one week, or even one year ( Data in local storage maintained even if the browser is closed).

The benefit of the **data persistance is what's causing the issue.** What and how we handle it will depend on **what we keep**.


### Downside of Localstorage

The majority of local storage's drawbacks aren't really significant. You may still not use it, but your app will run a little slower and you'll experience a tiny developer inconvenience. Security, however, is distinct. Knowing and understanding the security model of local storage is crucial since it will have a significant impact on your website in ways you might not have anticipated.

[Local storage](https://syedjaferk.hashnode.dev/the-browsers-localstorage) also has the drawback of being insecure. In no way! Everyone who stores sensitive information in local storage, such as session data, user information, credit card information (even momentarily! ), and anything else you wouldn't want shared publicly on social media, is doing it incorrectly.

The purpose of local storage in a browser for **safe storage was not intended**. It was intended to be a straightforward key/value store for strings only that programmers could use to create somewhat more complicated single page apps.

### What's the most dangerous thing in the entire world?

It's not nuke! It's Javascript 😂

Think about it like this: when you store sensitive information in [local storage](https://syedjaferk.hashnode.dev/the-browsers-localstorage), you're essentially using the most dangerous thing in the world to store your most **sensitive information in the worst vault ever created: not the best idea.**

What the problem really boils down to is cross-site scripting attacks (XSS). I won't bore you with a full explanation of XSS, but here's the high level:

If an attacker can run JavaScript on your website, they can retrieve all the data you've stored in local storage and send it off to their own domain. This means anything sensitive you've got in local storage (like a user's session data) can be compromised.

### So what? My website is secure. No attacker can run JavaScript on my website


And that's a good point. If your website is truly secure and no attacker can run JavaScript code on your website then you are technically safe, but in reality that is incredibly hard to achieve. Let me explain.

If your website contains any third party JavaScript code included from a source outside your domain:

- Links to bootstrap
- Links to jQuery
- Links to Vue, React, Angular, etc.
- Links to any ad network code
- Links to Google Analytics
- Links to any tracking code
- Some npm packages

#### Scenario

Let's say your website has the following script tag embedded inside it:

```
<script src="https://somejslibrary.com/minified.js"></script>
```

In this case, if somejslibrary.com is compromised and their minified.js script gets altered to:

- Loop through all data in local storage
- Send it to an API built to collect stolen information
    
then you are completely screwed. In this situation the attacker would have easily been able to compromise anything you had stored in local storage and you would never notice. Not ideal.


As developer, we think we're frequently susceptible to thinking that we would never embed third-party JavaScript in our websites. But in the real world, (due to demo release) this scenario rarely plays out.

So to err on the side of caution and dramatically reduce your risk for a security incident: don't store anything sensitive in local storage.

### Don't Store Tokens in Local Storage


Although I believe I made it clear in the preceding section that you should never, ever save sensitive information in local storage, I feel the need to expressly include **JSON Web Tokens **(JWTs).

I believe that those of us who save JWTs (session data) in local storage are the worst security violators right now. Many people are unaware that JWTs and username/password combinations are practically the same.

If a hacker manages to obtain a copy of your JWT, they are able to send **requests to the website **on your behalf without your knowledge. Never save your JWTs in local storage, just as you wouldn't with a credit card information or password.

### Other Downsides


- [Local storage](https://syedjaferk.hashnode.dev/the-browsers-localstorage) is synchronous: LocalStorage is **synchronous** It blocks the execution of the main thread until the operation is complete, which has a negative effect on the performance of an application, especially when there are many operations.

- LocalStorage can only contain strings: 
However, the data can be serialized with JSON.stringify:
localStorage.setItem(key, JSON.stringify(object));

- LocalStorage is limited to only 5MB (across all major browsers)

    This may seem like a huge limit for storing strings, but there are certain types of applications that need to store a lot of data to support offline mode, etc.
    
- LocalStorage is not accessible from the Web or Service Workers

    If the application uses different Workers, the data stored in [Local storage](https://syedjaferk.hashnode.dev/the-browsers-localstorage) cannot be accessed within the Worker.
    
- On a developer machine these issues can look deceptively minor as the operating system cached these requests – for an end user on the web they could mean a few seconds of waiting during which the web site stalls

- LocalStorage is persistent. If you don’t use a service or never visit a web site again, the data is still loaded when you start the browser

### General Preventions

1. For example, if we are using third party JavaScript libraries and they are injected with some scripts which extract the storage objects, our storage data won’t be secure anymore. Therefore it’s not recommended to save sensitive data as

    - Username/Password
    - Credit card info
    - JWT tokens
    - API keys
    - Personal info
    - Session ids
2. Do not use the same origin for multiple web applications. Instead, **use subdomains** since otherwise, the storage will be shared with all. Reason is, for each subdomain it will have an unique localstorage; and they can't communicate between subdomain instances. 

3. Once some data are stored in [Local storage](https://syedjaferk.hashnode.dev/the-browsers-localstorage), the developers don’t have any control over it until the user clears it. **If you want the data to be removed once the session ends, use SessionStorage**.

4. Validate, encode and escape data read from browser storage
5. Encrypt data before saving
    