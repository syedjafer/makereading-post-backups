## flat() & flatMap() in Javascript

### flat()

- The flat() method create a new array with all sub-array elements concatenated into it recursively up to the specified depth. 

- **Argument ** - The depth level specifying how deep a nested array structure should be flattened. Default value is 1. 

- The flat method removes empty slots in array. 

```javascript
const arr = [10, 20, [40, 50]];
console.log(arr.flat()) // [10, 20, 40, 50]

const arrTwo = [10, [[20], 30]];
console.log(arrTwo.flat()); // [10, [20 ], 30]

const arrThree = [10, [[20, 30]]];
console.log(arrThree.flat(2)); // depth two
// [10, 20, 30]

const arrFour = [10, [[[[20, 40]]]]]
console.log(arrFour.flat(Infinity));
// [10, 20, 40]
```

<u> Output :</u>


![flat in javascript](https://cdn.hashnode.com/res/hashnode/image/upload/v1662995981321/ob2F16FO3.png align="left")


### flatMap()

- The flatMap() method return a new array formed by applying a given callback function to each eleement of the array, and then flattening the array. 

- It is identical to a map() followed by a flat(). 

<u> Example 1</u>

```javascript
let arr = [1, [2], 3];
const resultingArr = arr.flatMap((x) => {
    return x * 3;
}};

console.log(resultingArr); // [3, 6, 9]

```

<u>Output</u>

![flatMap](https://cdn.hashnode.com/res/hashnode/image/upload/v1662996073701/1DpC2z4k4.png align="left")


<u>Example 2</u>

```javascript
let arr = [1, [2], [[3]]];

const doubleEven = arr.flatMap((x) => {
    return x % 2 == 0 ? 2 * x : [] ;
});

console.log(doubleEven); // [4]
```

<u>Output</u>


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662996135311/SD7FDuXC5.png align="left")
