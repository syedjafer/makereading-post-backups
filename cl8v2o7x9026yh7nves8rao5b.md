## What is Promise in Javascript?

Promises are used to handle asynchronous operations in javascript. They are easy to manage when dealing with multiple asynchronous operations where callbacks can create callbacks which will lead to unmanageable code. 

Prior to promises events and callback functions were used but they had limited functionalities and created unmanageable code. 

Promises are the ideal choice for handling asynchronous operations in the simplest manner. They can handle multiple asynchronous operations easily and provide better error handling than callbacks and events. 

In other words, also, we can say that promises are the ideal choice for handling multiple callbacks at the same time, thus avoiding the undesired callback hell situation. 

Promises do provide a better chance for a user to read the code in a more effective and efficient manner especially since the particular code is used for implementing multiple asynchronous operations. 

A promise is a statement that you make to a person in which you say that you will definitely do something or give them something. If you make a promise, you should keep it.

### Benefits of Promises
1. Improves code readability.
2. Better handling of asynchronous operations.
3. Better flow of control definition in asynchronous logic.
4. Better error handling

### Promise has four states
1. **fulfilled:** Action related to the promise succeeded.
2. **rejected:** Action related to the promise failed.
3. **pending:** Promise is still pending i.e. not fulfilled or rejected yet.
4. **settled:** Promise has been fulfilled or rejected.

### How to create a promise

A promise can be created using a promise constructor. 

```javascript

var promise = new Promise(function(resolve, reject){
   // do something
}
);

```

1. Promise constructor takes only one argument which is a callback function (and that callback function is also referred to as an anonymous function too)
2. Callback function takes two arguments, resolve and reject. 
3. Perform operations inside the callback function and if everything went well then call resolve. if desired operations do not go well then call reject. 

```javascript
var promise = new Promise(function(resolve, reject){
    const x = "some value";
    const y = "some value";

    if (x === y) {
      resolve();
    } else {
      reject();
    }
});

promise.then(function() {
    console.log("success, both are same");
}).catch(function(){
    console.log("failed, both aren't same");
});

```

