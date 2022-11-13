# Destructuring Assignment

### Introduction

**Destructuring assignment ** was introduced in ES6 as a special syntax in javascript that enable unpacking (assigning) values from arrays or object properties directly into variables.

### Example 1

To picture how this works, lets take a look at a simple example. Instead of writing this:

```javascript
const animalNames = ['simbaa', 'sherkhan'];

const lionName = animalNames[0];
const tigerName = animalNames[1];
```

write this,

```
const animalNames = ['Lion', 'Tiger'];
const [lionName, tigerName] = animalNames;
```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662997192707/DAA-g18_P.png align="left")

The above prescribed way is a neat way of assigning the values. 

### Example 2

In the second example lets work with objects. First let's assign to separate variables the name, age and breed of a dog. 

```javascript

const lion = {
    name: 'simba',
    age: 10,
    breed: 'Mountain Lion'
}

const {name, age, breed } = lion;

console.log(name) // simba
console.log(age) // 5
console.log(breed) // Mountain Lion
```

<u>Output:</u>

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662998464548/AMa6AbbWI.png align="left")


Now lets get the name and the age and breed store in the rest variable, 

```
const tiger = {
  name: "sherkhan",
  age: 20,
  breed: "Mountain tiger"
};

const {name, ...rest} = tiger;
console.log(name); // sherkhan
console.log(rest); // {age: 20, breed: "Mountain Tiger"}

```

<u> Output </u>

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662998521377/XebDbQpkH.png align="left")

### Example 3

Lets see how we can change the names of the variables, 

```
const lion = {
     name: 'simba',
    age: 10,
    breed: 'Mountain Lion'
};

const {name: lionName, age: lionAge, breed: lionBreed } = lion;

console.log(lionName) // simba
console.log(lionAge) // 10
console.log(lionBreed) // Mountain Lion
```

<u> Output</u>


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662998555098/WDAA5mmp4.png align="left")


### Example 4

Another example is related to removing an object from an array and storing it in a new one. Out data:

```
const data = [
  {id: 1, name: 'first element'},
  {id: 2, name: 'second element'},
  {id: 3, name: 'third element'},
  {id: 4, name: 'fourth element'},
  {id: 5, name: 'fifth element'}
];
```

In a "traditional way" the splice method returns a new array: 

```
const itemCut = data.splice(0, 1);
console.log(itemCut);
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662998592670/MBIyLdyEj.png align="left")


While destructuring assignment we can get an object instead of an array: 

```
const [itemCut, ...data] = data;
console.log(itemCut);
console.log(data);
```

<u>Output</u>

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662998941653/sfpWXRq1Z.png align="left")

### Example 5 

We can swap variables using destructuring, 

```
let lionName = 'simba';
let tigerName = 'sherkhan';

[lionName, tigerName] = [tigerName, lionName];
console.log(lionName) // sherkhan
console.log(tigerName) // simba
```
<u>Output</u>
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662998973484/DZYweR4vU.png align="left")

### Example 6

Nested destructuring assignment, 

```
const nestedArr = [1, [7, 5], [3, 2, 0]];

const [first, [second, third], fourth] = nestedArr;

console.log(first) // 1
console.log(second) // 7
console.log(third) // 5
console.log(fourth) // [3, 2, 0]
```
<u>Output</u>

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662998990585/vjQS9H9do.png align="left")
