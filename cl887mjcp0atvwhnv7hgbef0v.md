# WeakMap & WeakSet in Javascript

### Garbage Collection

Javascript garbage collection is a form of memory management whereby objects that are no longer referenced are automatically deleted and their resources are reclaimed (like cascade delete.)

### Weak Collections

- Map and Set's references to objects are strongly held and will not allow for garbage collections.
- WeakMap and WeakSet collections are 'weak' because they allow for object which are not longer needed to be cleared from memory. 

### WeakMap

The WeakMap object is a collection of **key/value pairs** in which the keys are **weakly** referenced. In this case, keys **must be objects** (primitive data types as keys are not allowed)  and values can be arbitary values. 

It does not support iteration and methods **keys(), values(), entries()** so there's no way to get all keys or values from it. 

<u>Syntax</u>

```javascript
new WeakMap([iterable])
```

> **Iterable** - it represents an array and other iterable object whose elements are in the form of key-value pair.

#### Methods available in WeakMaps

- **get(), set(), delete() and has()**

```
const weakMap = new WeakMap();
console.log(weakMap); // WeakMap {}

let obj = {};

// adding object (element) to WeakMap
weakMap.set(obj, 'hello');

console.log(weakMap); // WeakMap {{} => "hello"}

// get the element of a WeakMap
console.log(weakMap.get(obj)); // hellpo

// check if an element is present in WeakMap
console.log(weakMap.has(obj)); // true

// delete the element of WeakMap
console.log(weakMap.delete(obj)); // true

console.log(weakMap); // WeakMap
```

<u>Output:</u>


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662883906819/9TkY3bvxR.png align="left")


### WeakSet

The Javascript WeakSet object is the type of collection that allows us to store weakly help object. Unlike Set, the WeakSet are the collections of objects only. It doesn't contain the arbitary values. 

<u>syntax</u>

```
new WeakSet([iterable]);
```

> **Iterable** - it represents an array and other iterable object whose elements are in the form of key-value pair.

#### Methods available in WeakSets

**add(), delete() and has()**

```
const weakSet = new WeakSet();
console.log(weakSet); // WeakSet {}

const obj = { 'rank' : 1};

// add to a weakset
weakSet.add(obj);
console.log(weakSet); // WeakSet {{ 'rank' : 1}}

// check if an element is in Set
console.log(weakSet.has(obj)); // true

// delete elements
weakSet.delete(obj);
console.log(weakSet); // WeakSet {}
```

<u>output:</u>


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662886709105/D9ePzHauH.png align="left")

### Use cases of WeakMap and WeakSet
- Keeping data about library objects without changing them or incurring overhead.
- Keeping data about a small set of objects where many objects of the type exist to not incur problems with hidden classes JS engines use for objects of the same type.
- Keeping data about host objects like DOM nodes in the browser.
- Adding a capability to an object from the outside (like the event emitter example in the other answer).
- The average Javascript developer might not need to even use them, opting to use a conventional Map instead.