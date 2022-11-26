# Learn Python With Us - Python Tuple

### Important Links

**Series Link: ** https://makereading.com/series/python <br>
**Challenges : ** https://www.hackerrank.com/contests/makereading/challenges

### Youtube

<iframe src="https://www.youtube.com/embed/WGFkXVia9Cw?vq=hd1080&modestbranding=1&rel=0&color=white" width="700" height="400" title="[makereading] Python Tuple - Learn Python With Us" frameborder="0" allowfullscreen></iframe>

### What is a Tuple?

Tuples are ordered collections of both mutable and immutable data that are unchangeable. It can contain both the mutable and immutable data types. 

### How tuple works internally ?

Both lists and tuples are implemented as a list of pointers to the Python objects (items). Tuple is stored in a single block of memory. Creating a tuple is faster than creating a list. Creating a list is slower because two memory blocks need to be accessed. An element in a tuple cannot be removed or replaced.

### Declaration

A tuple data structure can be defined in two different methods,

1. **()** using smooth parentheses.
2. **tuple()** method.

#### 1. Using smooth parentheses

You can declare the tuple like, 

```python
data = ('d1', 'd2', 'd3')
print(data)
```

But there is one thing to be noted (i.e,) If you want to declare a tuple with one value, then you should not use closed parentheses. 

Let's see why 

```python
data = (1)
print(data, type(data))
```

![declaring tuple with one value](https://cdn.hashnode.com/res/hashnode/image/upload/v1669390662727/uY9wxonpM.png align="left")

So if you want to declare an tuple with only one value, then we need to specify a comma at the end. 

```python
data = (1,)
print(data, type(data))
```

![declaring tuple with only one value](https://cdn.hashnode.com/res/hashnode/image/upload/v1669390858303/UxTX3IZO0.png align="left")

#### 2. Using constructor **tuple()**

Using tuple() constructor, we can convert a list, tuple, set to a tuple.

**List to Tuple**

```python
data = [1, 2, 3]
tuple_data = tuple(data)
print(tuple_data, type(tuple_data))
```

![list to tuple conversion](https://cdn.hashnode.com/res/hashnode/image/upload/v1669391075668/tiR852Foh.png align="left")

**Set to Tuple**

```python
data = {1, 2, 3, 4}
tuple_data = tuple(data)
print(tuple_data, type(tuple_data))
```

![set to tuple conversion](https://cdn.hashnode.com/res/hashnode/image/upload/v1669391150249/-XEiNIUZM.png align="left")

**Dictionary to Tuple**

```python
data = {"name":"makereading"}
tuple_data = tuple(data)
print(tuple_data, type(tuple_data))
```

![dictionary to tuple](https://cdn.hashnode.com/res/hashnode/image/upload/v1669391237452/frHozZi1w.png align="left")


**Tuple to Tuple**

```python
data = (1, 2, 3, 4)
tuple_data = tuple(data)
print(tuple_data, type(tuple_data))
```

![tuple to tuple](https://cdn.hashnode.com/res/hashnode/image/upload/v1669391317509/I0ifbpwqk.png align="left")

### Tuple with basic built-in function

#### Length

To find the length of the tuple, 

```python
data = (1, 2, 3, 4, 5)
print(len(data))
```

![python length](https://cdn.hashnode.com/res/hashnode/image/upload/v1669434683222/KK9GKesA2.png align="left")

#### Max and Min value

```python
data = (1, 2, 3, 4, 5, 6)
print("Max value, ", max(data), "Min value", min(data))
```

![max min value](https://cdn.hashnode.com/res/hashnode/image/upload/v1669434821843/8d2kIK0LT.png align="left")

#### Type of the Datastructure

To find the type of the datastructure used, we can use `type()`,

```python
data = (1, 2, 3, 4, 5)
print(type(data))
```

![Type of Datastructure](https://cdn.hashnode.com/res/hashnode/image/upload/v1669435021635/TK0gPICHV.png align="left")

#### Any 

If `any` of the values in the set is true (i.e,) Non-Zero , Non-Empty String, False values then it will return True, else False. 

```python
data = (1, 0, '', False)
print(any(data))
```

![any python method](https://cdn.hashnode.com/res/hashnode/image/upload/v1669435118978/-i0y6t4-w.png align="left")

#### All

If `all` of the values in the set is true (i.e,) Non-Zero , Non-Empty String, False values then it will return True, else False. 

```python
data = (1, 2, 3)
print(all(data))

data = ("", 0, False)
print(all(data))

```

![all python true value](https://cdn.hashnode.com/res/hashnode/image/upload/v1669435300806/cGENAuNAg.png align="left")


#### To find the index of an element

For finding the index of the element in a datastructure, we can use `index()` method. 
`index()` method in python has 3 parameters (with 2 optional)

> **index**(element, start, stop) <br>
> **element** - Element to be found<br>
> **start** - Start index to search from specific index.<br>
> **stop** - Stop index to search till which index (stop index will not be included)

![index element](https://cdn.hashnode.com/res/hashnode/image/upload/v1669436370543/KIg_Sndl3.png align="left")

In the last example of the above image, we can see the stop index is not being considered for search. If the element is not fount it will throw `ValueError`.


#### To find the occurrences of an element

`count()` method is used to find the total occurrences of an element in the given array. 

```python
data = (1, 2, 3, 4, 5, 6)
data.count(5)
```

![count python](https://cdn.hashnode.com/res/hashnode/image/upload/v1669436870375/wTGPw_jqv.png align="left")

> 🙋 What would happen if the element is not present in the tuple ? Will it return an error or what ?

### Accessing Elements of Set

Tuple items are indexed and you can access them by referring to the index number. Python supports positive zero-based indexing and negative indexing that starts from -1. Negative indexing in Python means the indexing starts from the end of the iterable. The last element is at index -1, the second last at -2, and so on.

consider the list, `arr = ('a', 'b', 'c', 'd', 'e', 'f')`, which is having 6 elements. From the below image, you can see the values of the positive indexing and negative indexing. 

![positive indexing](https://cdn.hashnode.com/res/hashnode/image/upload/v1669043290827/z8QMW2-_e.png align="left")

#### Positive Indexing
In this type of Indexing, we pass a `positive index` (which we want to access) in closed brackets. The index number starts from index number 0 (which denotes the first element of a list).

```python
fruits = ("apple", "banana", "cherry")
print(fruits[1])
```

![list index positive indexing](https://cdn.hashnode.com/res/hashnode/image/upload/v1669445833327/MSkqD7Hug.png align="left")


#### Negative Indexing

Negative indexing means starting from the end. `-1` refers to the last item, `-2` refers to the second last item, etc.

```python
fruits = ("apple", "banana", "cherry")
print(fruits[-1])
```

![negative indexing](https://cdn.hashnode.com/res/hashnode/image/upload/v1669445878229/u9w_5KeXw.png align="left")

#### Slicing

**1. **You can specify a range of indexes by specifying where to start and where to end the range.
When specifying a range, the return value will be a new list with the specified items. 

> tuple[start : stop : step]

The format for tuple slicing is `[start: stop: step]`.

- **start** is the index of the tuple where slicing starts. (starting position is included)
- **stop** is the index of the tuple where slicing ends. (stop position is excluded)
- **step** allows you to select an nth item within the range start to stop (**default** value is **1**)

> 🖊️ If the **stop** value is greater than the tuple of the array, it won't throw an error. It will just consider till the end of the array. 

**Example: **

```python
fruits = ("apple", "banana", "cherry", "orange", "kiwi", "melon", "mango")
print(fruits[2:5])
```

> 📝 Note: The search will start at index 2 (included) and end at index 5 (not included).


![python slicing](https://cdn.hashnode.com/res/hashnode/image/upload/v1669445990632/BhtkBvbR5.png align="left")

![python slicing explanation](https://cdn.hashnode.com/res/hashnode/image/upload/v1669045555362/kgX2TJlsr.png align="left")

**2. ** If you aren't specifying the `start` value it will take index 0 as the start value. The same thing to the end, if you aren't specifying the end value it will take `len(arr)`.

```python
fruits = ("apple", "banana", "cherry", "orange", "kiwi", "melon", "mango")
print(fruits[:4])

fruits = ("apple", "banana", "cherry", "orange", "kiwi", "melon", "mango")
print(fruits[1:])
```

![python slicing without start or end](https://cdn.hashnode.com/res/hashnode/image/upload/v1669446062982/mlpFuV98D.png align="left")

**3. ** If you aren't specifying both the start and end, then for `start ` it's value will be `0` and for the `end`, its value will be `len of the tuple. `

**4. ** Let's try with negative indexing, 

```python
fruits = ("apple", "banana", "cherry", "orange", "kiwi", "melon", "mango")
print(fruits[-4:-1])
```

![slicing with negative indexing](https://cdn.hashnode.com/res/hashnode/image/upload/v1669446144339/tJ1t9SXSu.png align="left")


![negative indexing explanation](https://cdn.hashnode.com/res/hashnode/image/upload/v1669112345410/i-Dvze1C0.png align="left")

**5. ** `Step Size` specifies which element to picking while indexing. So a step size of 1 tells python to pick every element, a step size of 2 means picking alternate elements, and so on. 

> 🗝️ Default step size is 1. 

![positive negative step index](https://cdn.hashnode.com/res/hashnode/image/upload/v1669116427086/mNri8WryZ.png align="left")


### Modifying Tuple  Elements

We can't replace a value in the tuple based on the index, or the range of indexes; since the tuple is an `immutable` data structure. 

#### 1. Change value based on the index will throw error

```python
fruits = ("apple", "banana", "cherry")
fruits[1] = "blackcurrant"  
print(fruits)
```

![Change value based on the index will throw error](https://cdn.hashnode.com/res/hashnode/image/upload/v1669446735571/ocdMPWQiq.png align="left")

#### 2. Workaround to modify a tuple

For modifying a tuple, we need to first `convert a tuple to a list` and then modify all operations on top of the list, then convert back to a `tuple`.

```
data = (1, 2, 3, 4)
list_data = list(data)

# Adding some values to the list
list_data.append(100)

# Converting back to tuple
data = tuple(list_data)
print(data, type(data))
```

![workaround to modify to a tuple](https://cdn.hashnode.com/res/hashnode/image/upload/v1669447258898/xhig8y9uU.png align="left")

### Removing an element

Same as adding an element to a tuple (workaround), we need to follow the same steps. But to delete an object, we can use `del` . 

```python
data = (1, 2, 3, 4 ,5)
del data
print(data)
```

![Removing an element](https://cdn.hashnode.com/res/hashnode/image/upload/v1669447447162/52X754Dqq.png align="left")


### Sorting 

Sorting a tuple is also not possible, because tuple is an `immutable` datatype. But we can use `sorted` function to sort the tuple, but remember it will return a list.

```python
data = (10, 2, 3, 1, 5)
sorted_data = sorted(data)
print(sorted_data, type(sorted_data))
```

![sorted tuple](https://cdn.hashnode.com/res/hashnode/image/upload/v1669447917482/CJGifJEGt.png align="left")

Now we have came to the conclusion on using the Tuple data type. Now let us solve some excersice. 

### Excersice

1. Write a Python program to create a tuple with different data types.
2. Write a Python program to unpack a tuple in several variables
3. Write a Python program to add an item in a tuple.
4. Write a Python program to get the 4th element and 4th element from last of a tuple.
5. Write a Python program to remove an item from a tuple
6. Counts the number of occurrences of item 50 from a tuple
7. Check if all items in the tuple are the same

### Challenges

**Hackerrank: ** https://www.hackerrank.com/contests/makereading 