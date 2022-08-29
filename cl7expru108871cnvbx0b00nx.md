## The Classical Comparison - Map vs forEach

### Introduction


As a part of your day-to-day JavaScript development, you often need to work with arrays. And when you’re working with arrays, you often need to process array elements, so you need a way to loop through each element of an array. In JavaScript, **forEach** and **map** are two of the most popular methods to work with arrays. The primary purpose of both these methods is to iterate through arrays. Although they may look almost identical, there are certain differences between them. 

Before seeing the differences, lets see the working of both features.


### forEach

The forEach() method receives a f**unction as an argument** and executes it once for each array element.However, instead of returning a new array like map, it **returns undefined**.
forEach() does not mutate the array on which it is called. (However, callback may do so).

Give a try on the below interactive codepen.

<iframe src="https://codepen.io/syedjafer/embed/dymBxQy?default-tab=js,result&amp;theme-id=light&amp;editable=true" scrolling="no" allowfullscreen="true" loading="lazy" width="850" height="480" frameborder="no"></iframe>

### Map

The map method receives a function as a parameter. Then it applies it on each element and **returns an entirely new array** populated with the results of calling the provided function. **map**() does not mutate the array on which it is called (although callback, if invoked, may do so). In simple words, Performs given "transformation" on a "copy" of each element.

Give a try on the below interactive codepen.

<iframe src="https://codepen.io/syedjafer/embed/preview/LYdKwwY?default-tab=js,result&amp;theme-id=light&amp;editable=true" scrolling="no" allowfullscreen="true" loading="lazy" width="850" height="480" frameborder="no"></iframe>


Now we saw the working of these features. Now we will see how they are different (you might have already know by seeing their functionalities)

### Differences: 

Below differences are already mentioned in the above codepens. Give it a shot . 

#### 1. The returning value: 
The first difference between map() and forEach() is the returning value. The forEach() method returns undefined and map() returns a new array with the transformed elements. Even if they do the same job, the returning value remains different.

#### 2. Chaining
The second difference between these array methods is the fact that map() is chainable. This means that you can attach reduce(), sort(), filter() and so on after performing a map() method on an array.
That's something you can't do with forEach() because, as you might guess, it returns undefined.

#### 3. Mutability: 
In both the features, we can perform the mutability. But from the development perspective we should only use the mutability using forEach (it’s designed for that. ). If we are using mutability in map, it would be removed in code review. The map() method returns an entirely new array with transformed elements and the same amount of data. In the case of forEach(), even if it returns undefined, it will mutate the original array with the callback.

Therefore, we see clearly that map() relies on immutability and forEach() is a mutator method.


#### 4. Performance: 
We can’t comment on the performance because it works based on the computation speed of our machine. But many are claiming that map is faster. 


<iframe src="https://codepen.io/syedjafer/embed/MWVNWBj?default-tab=js,result&amp;theme-id=light&amp;editable=true" scrolling="no" allowfullscreen="true" loading="lazy" width="850" height="480" frameborder="no"></iframe>

![performance - map-vs-foreach](https://cdn.hashnode.com/res/hashnode/image/upload/v1661787416768/LIphqNoNR.png align="left")



### When you should not use both of these ?

**forEach** - when you don’t want to create a new array and just want to execute the functions with result on the same array. 

**Map** - Since map builds a new array, using it when you aren't using the returned array is an anti-pattern; use forEach or for...of instead.You shouldn't be using map if you're not using the array it returns; and/or, also if you're not returning a value from the callback.


I hope this clarifies the differences between these two functionalities.

### References: 
- MDN forEach - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach

- MDN map - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map











