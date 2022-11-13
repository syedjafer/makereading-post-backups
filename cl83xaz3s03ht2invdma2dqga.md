# Object Immutability in Javascript

### Introduction
When working with values and objects in jaavscript, you may sometimes need to restrict what can be done with them.  By doing so we can prevent to modify application-wide configuration objects, state objects, or global constants. 

We have freeze(), seal() and preventExtensions() methods of Object which help us in securing any JS object from being mutated. ( or it will help us to create Immutable Object).

> Object immutable means that further changes to it will not apply. Essentially, its state becomes read-only. 

### Object.freeze()

- Object.freeze() method completely freeze an object. 
- So if an object is frozen, then:
   1. we can't add new property to it. ❌
   2. can't update any existing property value. ❌
   3. can't delete any existing properties. ❌

```javascript
const user = {
      firstName: 'Syed',
      lastName: 'Jafer'
}

Object.freeze(user);
console.log(user.firstName); // Syed

// add new property
user.city = "Delhi";
// {firstName: "Syed", lastName: "Jafer"}

// delete any property
delete user.firstName;

console.log(user);
// { firstName: "Syed", lastName: "Jafer"}
```

**Output : **

![object.freeze()](https://cdn.hashnode.com/res/hashnode/image/upload/v1662703790001/7cqY_OLE7.png align="left")

### Object.seal()

- Object.seal() method will seal the object.
- So if an object is sealed, then:
    1. we can't add new property to it ❌
    2. can only update the value of existing properties ✅
    3. can't delete any existing properties ❌

```javascript
const user = {
    firstName: 'Syed',
    lastName: 'Jafer'
}

Object.seal(user);
console.log(user, firstName); // Syed

// Update existing property
user.firstName = "k syed";

console.log(user.firstName); // k syed

// add new property
user.city = "Delhi";
// {firstName: "k syed", lastName: "Jafer"}

// delete any property
delete user.firstName;

console.log(user);
// { firstName: "k syed", lastName: "Jafer" }

```

**Output:**

![Object.seal()](https://cdn.hashnode.com/res/hashnode/image/upload/v1662704196851/PANBewzrf.png align="left")

### Object.preventExtensions()

So if an object use preventExtensions, then:
- we can't add new property to it ❌
- can update the value of existing properties ✅
- can delete any existing properties ✅

```javascript
const user = {
    firstName: 'Syed',
    lastName: 'Jafer'
}

Object.preventExtensions(user);

console.log(user.firstName); // Syed

// update existing property
user.firstName = "k syed";

console.log(user.firstName); // k syed

// add new property
user.city = "Delhi";
// { firstName: 'k syed', lastName: 'Jafer' }

// delete any property
delete user.firstName;

console.log(user);
// {  lastName: 'Jafer' }

```

**Output:**


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662704494194/wFRsJtIop.png align="left")

### How to check ?

How to check if object is frozen, sealed or prevented from extensions. Use below methods for the same

#### isFrozen()

```
const user = { name: "Syed" };

console.log(Object.isFrozen(user)); // false
Object.freeze(user);
console.log(Object.isFrozen(user)); // true 
```
<u>Output :</u>

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662704725812/77T5NC-yd.png align="left")

#### isSealed()

```
const user = { name: "Syed" };

console.log(Object.isSealed(user)); // false
Object.seal(user);
console.log(Object.isSealed(user)); // true
```
<u>Output:</u>

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662704853381/ycqvynkWq.png align="left")

#### isExtensible()

```
const user = { name: "Syed" };

console.log(Object.isExtensible(user)); // true
Object.preventExtensions(user);
console.log(Object.isExtensible(user)); // false
```
<u>Output: </u>

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662704945934/uesOTO15T.png align="left")

### Using Strict Mode

- If you have noticed, that any of the above methods don't give any error when you try to mutate it. 
- When we use "Strict Mode", it throws an error in such cases. 

- Let's try with one method, same will work for other methods as well

```
"use strict";

const user = { name: "Syed" };
Object.preventExtensions(user);
user.city = "Chennai";

```

<u>Output: </u>

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662705144942/WanE23sun.png align="left")

### Working with Nested Objects

- Freeze(), seal() and preventExtensions() methods apply only to the first level of properties.
- If any nested objects are there in an object, then modifying the nested object works as normal.

```javascript
const user = {
    address: {
        city: "Delhi"
    }
}
Object.freeze(user);

user.address.city = "Chennai"; // No Error, it will work

console.log(user);
```
<u> Output: </u>

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662705356775/gGOXaYWD2.png align="left")

So to fix the previous issue, we need to apply these methods to all nested objects and for that we need to make recursive calls and apply these methods to each level of objects individually..

```javascript
const user = {
    address: {
        city: "Trivandrum"
    }
}

// Create recursice funtion

function freezeNestedObjects(obj){
    Object.freeze(obj);
    Object.values(obj).forEach((ob) => {
          if(typeof ob === 'object') freezeNestedObjects(ob);
    })
}

freezeNestedObjects(user);

user.address.city = "Chennai"; 

// { address: { city: "Delhi" }}
```
<u> Output: </u>


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662705850104/SjHG4C3Se.png align="left")


### Final thoughts

To Summarize,

- We can freeze an object to make it **immutable**.
- You use the method **Object.freeze** to freeze an object.
- You can not create a new property, modify or delete an existing property, or extend the object when a freeze is applied.
- Declaring a variable with the const keyword with an object value is not same as freezing the object.
- You can freeze an array using the same freeze method.
- The freeze method does a shallow freeze. Use recursion to do a deep freeze.
- The **seal**() and **preventExtentions**() methods provide partial immutability.
- **Unfreezing** is not supported in the language (yet).


































