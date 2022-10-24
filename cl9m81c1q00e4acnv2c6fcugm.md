# Understanding isObject Method in JavaScript

### Introduction
In the JavaScript world, almost everything you see is an object. If you understand objects, you understand Javascript. There are lots of static methods where you can create objects, copy objects, seal objects, freeze objects, compare objects, and much more. But there is one method that JavaScript does not have built-in which is checking if the object is truly an object or array of objects, strings, or boolean and number.

Unlike ```Array.isArray()``` in JavaScript which checks if the object or variable is an array or not, there is no ```Object.isObject()``` method in JavaScript.

There are different JavaScript libraries like underscore, lodash, etc. which have a method ```isObject()``` in it but using those libraries just to check if the variable is an object or not is not worth it.

Hence, in this article, we will see how to create an ```isObject``` function and use it to check if an object is actually an object.

### What is an Object?
An object is simply a collection of properties, and a property is an association between a name (or key) and a value. An object in programming is the same as an object in the real-life world. For example, in the real world, a cup is an object and its color, size, weight, etc. are its properties. So, in the same way, JavaScript objects have properties that define their characteristics. Let's see how to create an object in JavaScript.

```
var cup = {};
```

We just created an empty object in JavaScript, it's as simple as that. Now, we can assign the properties in it and use it in whichever way we want. Let us assign the properties to the cup object.

```
var cup = {color: 'black',	weight: '500gm' };
```

### Checking the data type of an object
Checking the data type of an object is very easy. We can use the built-in JavaScript method of ```typeof```. Since in JavaScript almost everything is an object, it also treats an array as an object. Let's see an example of this behavior.
```javascript
var animals = ['tiger', 'lion', 'zebra'];
var cup = {color: 'black',	weight: '500gm' };
```
Here above we have 2 variables and now if we check the data type of them then we can see both are treated as objects. We are using the console.log method to print the result in the console.
```javascript
console.log(typeof animals) // returns object console.log(typeof cup) // returns object
```

It's true that both are objects, but we need a mechanism to differentiate the variables if it's an array or just a simple object. In JavaScript, there is a built-in method to check if a variable is an array. Array.isArray() methods can tell us if the variable is an array or not, but unfortunately there is no method like ```Object.isObject()``` in JavaScript.


Anyway, we can create a method to test if a variable is an object or not by creating a simple function. There are many ways to test, and we will look at one of them. Let us create a method

```javascript
function isObject(obj) 
    {	
      return typeof obj === 'object' && obj !== null && ! Array.isArray(obj)
    };
```

So, what we did in the above function is:

- Check the type of the parameter passed with the method typeof
- Check if the parameter passed is not null
- Check if the parameter passed is not an array


If all of the above conditions are met, then it is 100% sure that the parameter passed or variable reference passed to the function is an object. Let us do some testing by passing the above variables which we have created.

```javascript
console.log(isObject(animals)) //returns false 
console.log(isObject(cup)) // returns true
```

### Conclusion

So, with simple condition checks in the function, we can easily test if a variable is an object or not.
