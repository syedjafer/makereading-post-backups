# Pure function vs Impure function in JS

### Key rules of a function

While writing functions we should take care of certain conditions. We need to make sure that our functions are, 

- **Predictable**: It produces a predictable output for the same input. 
- **Reusable**: Can reuse the function at multiple places without altering its behavior and the caller's behavior. 
- **Readable**: Anyone reading the function as a standalone unit can understand its purpose completely. 
- **Testable**: Function should be testable as an independent unit. 

### Pure Function

A **pure function** has all of the above-discussed characteristics. It is predictable (always produces the same result for the same input) and it is reusable and testable as well. 

```javascript
const displayStatus = (name) => 'Hello ${name}';
```

So, we can see this function is always going to return the same output for the same input because it doesn't have any outside dependency that will change its output (or we can say it doesn't have any **side-effects**)

### Impure Function

An **Impure function** is a function that contains one or more side effects. 

```javascript
const users = ["Syed", "Jafer"];

function addUser(user) {
    users.push(user);
    return users;
}

console.log(addUser("Filza"));

```

So, the output of the above function is predictable and it will also return the same output for the same input but still, it's not a pure function. 

**It is an Impure function** because it is modifying my global variable (users) and introducing side-effects in my addUser function. 

### Side Effects

A side effect occurs in a program whenever you use external code in your function - which, as a result, impacts the function's ability to perform its tasks. 

Few examples of side effects: 

- Modifying a global variable
- Modifying an argument
- Making HTTP requests
- DOM manipulation
- Reading/writing files. 

A **pure function** must both be predictable and without side effects. If either of these criteria is not met, we're dealing with **an impure function.**

### Pure vs Impure Javascript Functions

In-built impure functions, 

- Math.random()
- Date.now()
- array.splice()
- array.push()
- array.sort()

Below JS methods are typically associated with pure functions, 

- array.map()
- array.filter()
- array.concat()
- array.reduce()
- array.slice()
- Math.floor()
- string.toLowerCase()
- array.each()
- array.every()

### Final thoughts

**Can I make all functions Pure Function ?**

Ideally, we can, but applications with only Pure functions may not do much. Code needs to introduce side effects like HTTP calls, I/O operations, DOM Manipulation, and many more. 

As a best practice, we can do, try to use as much as pure functions as we can. Isolate Impure functions (side effects) as much as possible. 

It will improve your code's readability, debugging, and testability a lot. 