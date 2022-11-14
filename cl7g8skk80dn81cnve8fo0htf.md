# The browser's localStorage

### Introduction

The Web storage api is a set of mechanisms that enable browsers to store **key-value** pairs. Before HTML5, application data had to be sorted in cookies, included in every server request. Its intended to be far more user-friendly than using cookies. 

Web storage is more secure, and large amounts of data can be stored locally, without affecting website performance. 

There are 2 types of web storage,
1. Local Storage
2. Session Storage

### We already have cookies. Why additional objects?

Unlike cookies, web storage objects are **not sent** to server with each request. Because of that, we can store much more. Most modern browsers allow at least 5 megabytes of data (or more) and have settings to configure that.
Also unlike cookies, the server can’t manipulate storage objects via HTTP headers. Everything’s done in JavaScript.The storage is bound to the origin (domain/protocol/port triplet). That is, different protocols or subdomains infer different storage objects, they can’t access data from each other.

In this guide, you will learn/refresh about LocalStorage.

### LocalStorage

The localStorage is property of the window  (browser window object) interface allows you to access a Storage object for the Document's origin; the stored data is saved across browser sessions.

1. Data is kept for a longtime in local storage (with no expiration date.). This could be one day, one week, or even one year as per the developer preference ( Data in local storage maintained even if the browser is closed). 
2. Local storage only stores strings. So, if you intend to store objects, lists or arrays, you must convert them into a string using JSON.stringfy()
3. Local storage will be available via the window.localstorage property. 
4. What’s interesting about them is that the data survives a page refresh (for sessionStorage) and even a full browser restart (for localStorage).


### Main methods of LocalStorage

- #### setItem(key, value)

**Functionality:** Add key and value to localStorage. setItem returns undefined. Every key, value pair stored is converted to a string. So it’s better to convert an object to string using JSON.stringify(<object>) prior to storing it in local storage. 

**Examples:**

- For a simple key, value strings. 
```
// setItem normal strings
window.localStorage.setItem("name", "goku");
```

- Inorder to store objects, we need to convert them to JSON strings using JSON.stringify()

```
// Storing an Object without JSON stringify
const data = {
  "commodity":"apple",
  "price":43
};
window.localStorage.setItem('commodity', data);
var result = window.localStorage.getItem('commodity');
console.log("Retrived data without jsonified, "+ result);
```

%[https://gist.github.com/syedjafer/e0e2317b39a36413665e91aced35363b#file-localstorage-js]



- #### getItem(key)

**Functionality:** This is how you get items from localStorage. If the given key is not present then it will return null.

**Examples**
Get a simple key value pair
```
// setItem normal strings
window.localStorage.setItem("name", "goku");

// getItem 
const name = window.localStorage.getItem("name");
console.log("name from localstorage, "+name);
```

%[https://gist.github.com/syedjafer/e0e2317b39a36413665e91aced35363b#file-localstorage-js]

- #### removeItem(key)
**Functionality:** Remove an item by key from localStorage. If the given key is not present then it wont do anything. 

**Examples:**

- After removing the value will be null. 
```
// remove item 
window.localStorage.removeItem("commodity");
var result = window.localStorage.getItem('commodity');
console.log("Data after removing the key "+ result);
```

%[https://gist.github.com/syedjafer/e0e2317b39a36413665e91aced35363b#file-localstorage-js]

- #### clear()
**Functionality:** Clears the entire localStorage
**Examples:**
- Simple clear of localStorage
```
// clear
window.localStorage.clear();
console.log("length of local storage - after clear " + window.localStorage.length);
```

%[https://gist.github.com/syedjafer/e0e2317b39a36413665e91aced35363b#file-localstorage-js]

- #### length
**Functionality:** We can use this like the property access. It returns number of items stored. 
**Examples: **

```
//length
console.log("length of local storage " + window.localStorage.length);
```
%[https://gist.github.com/syedjafer/e0e2317b39a36413665e91aced35363b#file-localstorage-js]

### Codepen Tryout

Give a try in the below codepen.

<iframe src="https://codepen.io/syedjafer/embed/preview/dymxdWG?default-tab=js,result&amp;theme-id=dark&amp;editable=true" scrolling="no" allowfullscreen="true" loading="lazy" width="850" height="480" frameborder="no"></iframe>

### When to use Local Storage
1. Data stored in Local Storage can be easily accessed by third party individuals. 
2. So its important to know that any sensitive data must not sorted in Local Storage. 
3. Local Storage can help in storing temporary data before it is pushed to the server. 
4. Always clear local storage once the operation is completed. 


### localStorage browser support
localStorage as a type of web storage is an HTML5 specification. It is supported by major browsers including IE8. To be sure the browser supports localStorage, you can check using the following snippet:

```
if (typeof(Storage) !== "undefined") {
    // Code for localStorage
    } else {
    // No web storage Support.
}
```

### Where the local storage is saved ?

#### Windows

- **Firefox: **C:\Users\<Windows login/user name>\AppData\Roaming\Mozilla\Firefox\Profiles\<profile folder>\webappsstore.sqlite, %APPDATA%\Mozilla\Firefox\Profiles\<profile folder>\webappsstore.sqlite

- **Chrome: **%LocalAppData%\Google\Chrome\User Data\Default\Local Storage\

#### Linux

- **Firefox:** ~/.mozilla/firefox/<profile folder>/webappsstore.sqlite
- **Chrome:** ~/.config/google-chrome/Default/Local Storage/

#### Mac

- **Firefox:** ~/Library/Application Support/Firefox/Profiles/<profile folder>/webappsstore.sqlite, ~/Library/Mozilla/Firefox/Profiles/<profile folder>/webappsstore.sqlite
- **Chrome:** ~/Library/Application Support/Google/Chrome/<Profile>/Local Storage/, ~/Library/Application Support/Google/Chrome/Default/Local Storage/

### Simple handson

<iframe src="https://syedjafer.github.io/localStrorage/index.html" scrolling="no" allowfullscreen="true" width="850" height="400" frameborder="no"></iframe>

Source Code: [github](https://github.com/syedjafer/localStrorage)

### Limitations: 

1. Do not store sensitive user information in localStorage
2. It is not a substitute for a server based database as information is only stored on the browser
3. localStorage is limited to 5MB across all major browsers
4. localStorage is quite insecure as it has no form of data protection and can be accessed by any code on your web page
5. localStorage is synchronous, meaning each operation called would only execute one after the other


 


