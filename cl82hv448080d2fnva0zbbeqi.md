## Coercion in Javascript

Converting a value from one type to another is often called "**type** **casting**", when done explicitly, and "coercion" when done implicitly ( forced by the rules of how a value is used ). 

We can check the implicit coercion using the identity(===) and equality(==) operators. The identity ( === ) operator behaves identically to the equality ( == ) operator except no type conversion is done, and the types must be the same to be considered equal. 

- The == operator will compare for equality after doing any necessary type conversions.
- The === operator will not do the conversion, so if two values are not the same type === will simply return false. 
- It's this case where === will be faster, and may return a different result than ==. In all other cases performance will be the same. 

### **Coercion for different data types and equality checks in JS**

#### Implicit conversion of interger.
```javascript
function coercionExample() {
	const x = 42;
	const y = x + "";
	console.log(y, typeof y);
	
	const z = String(x);
	console.log(z, typeof z);
}

console.log(coercionExample());
```
<u>Output:</u>
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662701342307/BSyt24mTS.png align="left")

#### Equality checks

```javascript
console.log('' == '0'); // false
console.log(0 == ''); // true
console.log(0 == '0'); // true

console.log(false == 'false'); // false
console.log(false == '0'); // true

console.log(false == undefined); // false
console.log(false == null); // false
console.log(null == undefined); // true

console.log(' \t\r\n ' == 0); //true

```
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662701598344/9oR4lI3lb.png align="left")



**Array**

```
var a = [1, 2, 3];
var b = [1, 2, 3];

console.log(a == b); \\false
console.log(a === b); \\false
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662701746767/1V2xowJaX.png align="left")

**Object** 

```
var c = {x: 1, y:2};
var d = {x: 1, y:2};

console.log(c == d); \\ false
console.log(c === d); \\ false
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662701769691/O9rhu5U6Q.png align="left")


**String**

```
var e = "text";
var f = "te" + "xt";

console.log(e == f); \\ true
console.log(e === f); \\ true
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662701802541/lWZogw4S6.png align="left")


Here the == operator is checking the values of the two objects and returning true, but the === is seeing that they're not the same type and returning false. 

```
console.log("abc" == new String("abc")); //true
console.log("abc" === new String("abc")); // false
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662701820293/qFsI6_OT8.png align="left")
