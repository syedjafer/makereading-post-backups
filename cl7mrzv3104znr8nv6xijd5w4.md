# The Browser's Session Storage

### Introduction

The Web storage api is a set of mechanisms that enable browsers to store key-value pairs. Before HTML5, application data had to be sorted
in cookies, included in every server request. Its intended to be far more user-friendly than using cookies. 

Web storage is more secure, and large amounts of data can be stored locally, without affecting website performance. 

There are 2 types of web storage
1. [Local Storage](https://syedjaferk.hashnode.dev/the-browsers-localstorage)
2. Session Storage

### We already have cookies. Why additional objects?
Unlike cookies, web storage objects are not sent to server with each request. Because of that, we can store much more. Most modern browsers allow at least 5 megabytes of data (or more) and have settings to configure that. Also unlike cookies, the server can’t manipulate storage objects via HTTP headers. Everything’s done in JavaScript.The storage is bound to the origin (domain/protocol/port triplet). That is, different protocols or subdomains infer different storage objects, they can’t access data from each other.

In this guide, you will learn/refresh about session storage.

### Session Storage

The **sessionStorage** read-only property of the window interface allows you to access a Storage object for the Document's origin; it similar to localStorage, but the difference is that while data in localStorage doesn't expire, data in sessionStorage is cleared when the page session ends.

### Functionalities of session storage

1. Whenever a document is loaded in a particular tab in the browser, a unique page session gets created and assigned to that particular tab. That page session is valid only for that particular tab.
**Eg: ** Opening hashnode.com will create a unique session storage inside the browser.  

2. A page session lasts as long as the tab or the browser is open, and survives over page reloads and restores. **Eg:** Once you closed the tab, all the details stored in your session storage will get wiped out. 

3. Opening multiple tabs/windows with the same URL creates sessionStorage for each tab/window. **Eg:** Opening hashnode.com on mutliple tabs or multiple windows will generate unique session storage for each tab, and they won't communicate with each other. 

4. Duplicating a tab copies the tab's sessionStorage into the new tab. **Eg:** While duplicating a tab (hashnode.com), all the session storage will get copied aswell. 

5. Closing a tab/window ends the session and clears objects in sessionStorage.

### Main methods of SessionStorage

- **setItem(key, value)**

**Functionality: ** Add key and value to sessionStorage. setItem returns undefined. Every key, value pair stored is converted to a string. So it’s better to convert an object to string using JSON.stringify() prior to storing it in session storage.

**Examples: **
- For a simple key, value strings, 

```
// setItem normal strings
window.sessionStorage.setItem("name", "goku");
```

- Inorder to store objects, we need to convert them to JSON strings using JSON.stringify()

```
// Storing an Object without JSON stringify
const data = {
  "commodity":"apple",
  "price":43
};
window.sessionStorage.setItem('commodity', data);
var result = window.sessionStorage.getItem('commodity');
console.log("Retrived data without jsonified, "+ result);

```

%[https://gist.github.com/syedjafer/2d7c872c1ad7eb279aa8417e39c5f5c7#file-sessionstorage-js]

- **getItem(key)**

**Functionality: ** This is how you get items from sessionStorage. If the given key is not present then it will return null.

**Examples: ** Get a simple key value pair. 
```
// setItem normal strings
window.sessionStorage.setItem("name", "goku");

// getItem 
const name = window.sessionStorage.getItem("name");
console.log("name from sessionStorage, "+name);

```

%[https://gist.github.com/syedjafer/2d7c872c1ad7eb279aa8417e39c5f5c7#file-sessionstorage-js]

- **removeItem(key)**

**Functionality: ** Remove an item by key from sessionStorage. If the given key is not present then it wont do anything.

**Examples**

- After removing the value will be null.

```
// remove item 
window.sessionStorage.removeItem("commodity");
var result = window.sessionStorage.getItem('commodity');
console.log("Data after removing the key "+ result);

```

%[https://gist.github.com/syedjafer/2d7c872c1ad7eb279aa8417e39c5f5c7#file-sessionstorage-js]


- **Clear**

**Functionality: ** Clear the entire session storage. 

**Examples:**

- Simple clear of session storage

```
// clear
window.sessionStorage.clear();
console.log("length of session storage - after clear " + window.sessionStorage.length);

```
%[https://gist.github.com/syedjafer/2d7c872c1ad7eb279aa8417e39c5f5c7#file-sessionstorage-js]

- **length**

**Functionality: ** We can use this like the property access. It returns number of items stored.

**Examples:** 
```
//length
console.log("length of session storage " + window.sessionStorage.length);
```

%[https://gist.github.com/syedjafer/2d7c872c1ad7eb279aa8417e39c5f5c7#file-sessionstorage-js]



### Why JS session storage ?

1. The session storage can be used to store the state of the user interface of the web application. Later, when the user comes back to the page, you can restore the user interface stored in the session storage.

2. The session storage can also be used to pass data between pages instead of using the hidden input fields or URL parameters.

### Where the session storage is saved ?

**Firefox: **
In firefox, As to sessionStorage, it only needs to persist for one browser session. Restarting the browser normally clears it, so it doesn't need to be stored in a database. Firefox still writes it to disk to allow restoring the current browsing session, namely to the sessionstore.js file (JSON format). There is a key storage, its value is a map from URLs to their corresponding sessionStorage data. I am not sure whether this data is complete however given that its main purpose is to recover from crashes.

sessionstore.js is now called sessionstore.jsonlz4 and you will need to use a tool like dejsonlz4 (github.com/avih/dejsonlz4) if you want to decode the file to read it.

- Windows location: C:\Users\<Windows login/user name>\AppData\Roaming\Mozilla\Firefox\Profiles\<profile folder>, %APPDATA%\Mozilla\Firefox\Profiles\<profile folder>
- Linux location: ~/.mozilla/firefox/<profile folder>/
- Mac Location: ~/Library/Application Support/Firefox/Profiles/<profile folder>

**Chrome**
In chrome its stored in the db itself.
- Windows location: %LocalAppData%\Google\Chrome\User Data\Default\Session Storage\
- Linux location: ~/.config/google-chrome/Default/Session Storage/
- Mac location: ~/Library/Application Support/Google/Chrome/<Profile>/Session Storage/, ~/Library/Application Support/Google/Chrome/Default/Session Storage/


### Final thoughts
A session store is also best for storing more sensitive information that you don’t want to keep once the session has ended, such as a login token of a banking application.

Since local storage is not window-specific, one tab can overwrite the data that another tab has stored. That can lead to some unexpected behavior, so session storage is a better option in this case.


