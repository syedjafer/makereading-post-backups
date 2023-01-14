# Learn Python With Us - Lists

### ❗ Important Links

\*\*Series Link : \*\*https://makereading.com/series/python  
\*\*Challenges : \*\*https://www.hackerrank.com/contests/makereading/challenges  
\*\*Google Classroom: \*\* https://classroom.google.com/c/NTA3NzI5NTUzMDQz?cjc=2qcqsu5

### Youtube

<iframe src="https://www.youtube.com/embed/Nr3ZJSob-2c" width="720" height="420"></iframe>

### What is a List?

A simple data structure in Python that is a `mutable`, or `changeable`, `ordered` sequence of elements.

### Properties of the list

1. Lists are ordered, Which means they will **maintain the order of insertion.**
    
2. Lists can contain **any arbitrary objects** (eg: list, dictionary, set, tuple, string, numbers, None).
    
3. List elements can be **accessed by index** (position).
    
4. Lists are **mutable**.
    
5. Lists are **dynamic**, in memory allocation.
    
6. Lists can contain duplicate values; Since lists are **indexed**, lists can have items with the same value
    

### How the list is built internally?

Python lists are internally built on top of Arrays using C. Specifically, they are **dynamic arrays** with exponential over-allocation. Python’s lists are really variable-length arrays. The implementation uses a contiguous array of references to other objects and keeps a pointer to this array and the array’s length in a list head structure.

When items are appended or inserted, the array of references is resized. Some cleverness is applied to repeatedly improve appending items' performance; when the array must be grown, some extra space is allocated so the next few times don’t require an actual resize.

> 💡 To know more about how the memory allocation happens in the dynamic array for python list, please check out this http://www.laurentluce.com/posts/python-list-implementation/

### Declaration

A list data structure can be defined in two different methods,

1. **\[\]** using square brackets.
    
2. **list()** method.
    

#### 1\. Using square brackets

You can declare the list below,

```python
data = ['d1', 'd2', 'd3']
print(data)
```

![list square brackets declaration](https://cdn.hashnode.com/res/hashnode/image/upload/v1669037157875/i88ebQjuJ.png align="left")

#### 2\. Using list() constructor

Using the list() constructor, we can convert a set, tuple, dictionary, or list to a list.

**Set to list:**

```python
set_data = {1, 2, 3, 4}
print("set data type", type(set_data))
data = list(set_data)
print(data, type(data))
```

![set to list conversion python](https://cdn.hashnode.com/res/hashnode/image/upload/v1669037358884/v61vEhG7u.png align="left")

**Dictionary to list**

While converting Dictionary to a list, the list value comprises only the key values.

```python
dict_data = {"name": "makereading", "type": "blog"}
print("dict_data type", type(dict_data))
data = list(dict_data)
print(data, type(data))
```

![python dictionary to list conversion](https://cdn.hashnode.com/res/hashnode/image/upload/v1669037600008/Sy9A2OZT6.png align="left")

**Tuple to list**

```python
tuple_data = (1, 2, 3)
print("Type of tuple_data", type(tuple_data))
data = list(tuple_data)
print(data, type(data))
```

![tuple to list conversion](https://cdn.hashnode.com/res/hashnode/image/upload/v1669039659957/02lpQ2lYZ.png align="left")

### Data Types

**List** is a **mutable** with both **mutable & immutable** data types.

```python
data = [1, 'makereading', True, [1, 2, 3], {"name":"makereading"}, (1, 2, 3), {1, 2, 3}]
print(data)
```

![python list support different data types](https://cdn.hashnode.com/res/hashnode/image/upload/v1669040104388/n1v51B-vt.png align="left")

As you see in the above list output, we can see that the list can contain all kind of datatypes. (i.e) number, string, boolean, list, dictionary, tuple, set.

### Built-in Functions with a list

#### Length - len()

To find the length of the list,

```python
data = [1, 2, 3, 4, 5, 6]
print("length of data list ,", len(data))
```

![length of list](https://cdn.hashnode.com/res/hashnode/image/upload/v1669040375597/49K9rH_vC.png align="left")

#### Type of data structure - type()

To find the type of data structure,

```python
data = [1, 2, 3, 4, 5, 'string']
print(type(data))
```

![type of the data structure - list](https://cdn.hashnode.com/res/hashnode/image/upload/v1669040500685/-Lg3KBAow.png align="left")

For the list datastructure, type() method will output `<class list>`

#### max() & min()

To find the maximum value and the minimum value of a list,

```python
data = [0, 10, 1, 89, 10]
print("Max - ", max(data), "Min - ", min(data))
```

![maximum and minimum value of list](https://cdn.hashnode.com/res/hashnode/image/upload/v1669040788568/6zHs6WEMZ.png align="left")

#### any()

If any of the values in the set is true (i.e,) **Non-Zero, Non-Empty String, False** values then it will return True, else False.

```python
data = [0, 10, 1, 89, 10]
print(any(data))
```

![any method in list](https://cdn.hashnode.com/res/hashnode/image/upload/v1669042184062/jmt8BCQSK.png align="left")

#### all()

The all() function returns True if all items in an iterable are true, otherwise, it returns False. If the iterable object is empty, the all() function also returns True.

```python
data = [0, 10, 1, 89, 10]
print(all(data)) # Since it has zero, it will return False

data = [1, 10, 1, 89, 10]
print(all(data)) # Since it has all true values, it will return True
```

![all python method in list](https://cdn.hashnode.com/res/hashnode/image/upload/v1669042335518/eJeWokpUw.png align="left")

### Accessing Elements of List

List items are `indexed` and you can access them by referring to the `index number`. Python supports positive `zero-based indexing` and `negative indexing` that starts from `-1.` Negative indexing in Python means the indexing starts from the end of the iterable. The last element is at index -1, the second last at -2, and so on.

consider the list, `arr = ['a', 'b', 'c', 'd', 'e', 'f']`, which is having 6 elements. From the below image, you can see the values of the positive indexing and negative indexing.

![positive indexing](https://cdn.hashnode.com/res/hashnode/image/upload/v1669043290827/z8QMW2-_e.png align="left")

#### Positive Indexing

In this type of Indexing, we pass a `positive index` (which we want to access) in square brackets. The index number starts from index number 0 (which denotes the first element of a list).

```python
fruits = ["apple", "banana", "cherry"]  
print(fruits[1])
```

![list index positive indexing](https://cdn.hashnode.com/res/hashnode/image/upload/v1669042819762/0ptKZhI1J.png align="left")

#### Negative Indexing

Negative indexing means starting from the end. `-1` refers to the last item, `-2` refers to the second last item, etc.

```python
fruits = ["apple", "banana", "cherry"]  
print(fruits[-1])
```

![negative indexing](https://cdn.hashnode.com/res/hashnode/image/upload/v1669044028043/jCKGfO2Yh.png align="left")

#### Slicing

\*\*1. \*\*You can specify a range of indexes by specifying where to start and where to end the range. When specifying a range, the return value will be a new list with the specified items.

> list\[start : stop : step\]

The format for list slicing is `[start: stop: step]`.

* **start** is the index of the list where slicing starts. (starting position is included)
    
* **stop** is the index of the list where slicing ends. (stop position is excluded)
    
* **step** allows you to select an nth item within the range start to stop (**default** value is **1**)
    

> 🖊️ If the **stop** value is greater than the list of the array, it won't throw an error. It will just consider till the end of the array.

\*\*Example: \*\*

```python
fruits = ["apple", "banana", "cherry", "orange", "kiwi", "melon", "mango"]  
print(fruits[2:5])
```

> 📝 Note: The search will start at index 2 (included) and end at index 5 (not included).

![python slicing](https://cdn.hashnode.com/res/hashnode/image/upload/v1669045010980/Do0I45gLa.png align="left")

![python slicing explanation](https://cdn.hashnode.com/res/hashnode/image/upload/v1669045555362/kgX2TJlsr.png align="left")

\*\*2. \*\* If you aren't specifying the `start` value it will take index 0 as the start value. The same thing to the end, if you aren't specifying the end value it will take `len(arr)`.

```python
fruits = ["apple", "banana", "cherry", "orange", "kiwi", "melon", "mango"]
print(fruits[:4])

fruits = ["apple", "banana", "cherry", "orange", "kiwi", "melon", "mango"]
print(fruits[1:])
```

![python slicing without start or end](https://cdn.hashnode.com/res/hashnode/image/upload/v1669111612911/CQ4nX1fF2.png align="left")

\*\*3. \*\* If you aren't specifying both the start and end, then for `start` it's value will be `0` and for the `end`, its value will be `len of the array.`

\*\*4. \*\* Let's try with negative indexing,

```python
fruits = ["apple", "banana", "cherry", "orange", "kiwi", "melon", "mango"]  
print(fruits[-4:-1])
```

![slicing with negative indexing](https://cdn.hashnode.com/res/hashnode/image/upload/v1669112040197/CUtCuVkj_.png align="left")

![negative indexing explanation](https://cdn.hashnode.com/res/hashnode/image/upload/v1669112345410/i-Dvze1C0.png align="left")

\*\*5. \*\* `Step Size` specifies which element to picking while indexing. So a step size of 1 tells python to pick every element, a step size of 2 means picking alternate elements, and so on.

> 🗝️ Default step size is 1.

![positive negative step index](https://cdn.hashnode.com/res/hashnode/image/upload/v1669116427086/mNri8WryZ.png align="left")

**Examples**:

**Positive step size**  

![positive step size](https://cdn.hashnode.com/res/hashnode/image/upload/v1669116561843/mJKRQiCT1.png align="left")

**Negative step size**  

![negative step size](https://cdn.hashnode.com/res/hashnode/image/upload/v1669116642825/Wwi90HucN.png align="left")

### Modifying List Elements

We can replace a value in the list based on the index, or the range of indexes.

#### 1\. Change value based on the index

```python
fruits = ["apple", "banana", "cherry"]  
fruits[1] = "blackcurrant"  
print(fruits)
```

In the above list, we are changing the value of the list with `index 1` from `banana` to `blackcurrant.`

![Change value based on the index](https://cdn.hashnode.com/res/hashnode/image/upload/v1669116974023/07nqQdavc.png align="left")

#### 2\. Change the value based on ranges (slice)

```python
fruits = ["apple", "banana", "cherry", "orange", "kiwi", "mango"]  
fruits[1:3] = ["blackcurrant", "watermelon"]  
print(fruits)
```

![Change the value based on ranges](https://cdn.hashnode.com/res/hashnode/image/upload/v1669117142240/qKfqHPvP4.png align="left")

💥 If you insert more items than you replace, the new items will be inserted where you specified, and the remaining items will move accordingly.

### Methods to add values to list

#### 1\. insert()

> The insert() method takes two parameters:  
> **index** - the index where the element needs to be inserted  
> **element** - this is the element to be inserted in the list  

Insert an item at a given position. The **first argument** is the index of the element before which to insert, so `a.insert(0, x)` inserts at the front of the list, and `a.insert(len(a), x)` is equivalent to `a.append(x)`.

```python
fruits = ['apple', 'papaya', 'banana', 'orange', 'pear', 'lemon']
fruits.insert(2, 'berry')
print(fruits)
```

![before insert operation](https://cdn.hashnode.com/res/hashnode/image/upload/v1669122188628/6TbG9u2vB.png align="left")

All the elements after the element are shifted to the right.

![before insertion](https://cdn.hashnode.com/res/hashnode/image/upload/v1669122489573/jpkKK96fX.png align="left")

After the insertion of the element,

![after insertion](https://cdn.hashnode.com/res/hashnode/image/upload/v1669122539692/5AP-E8y6r.png align="left")

This `insert()` method will work with the negative indexing as well.

```python
fruits = ['apple', 'papaya', 'banana', 'orange', 'pear', 'lemon']
fruits.insert(-1, 'pear')
print(fruits)
```

![insert method with negative indexing](https://cdn.hashnode.com/res/hashnode/image/upload/v1669122825089/-kWwIZnPf.png align="left")

#### 2\. append()

`append()` method will add an element at the end of the list. Since the list is a mutable data structure, this append() method is an in-place change.

```python
fruits = ['apple', 'papaya', 'banana', 'orange', 'pear', 'lemon']
fruits.append('lemon orange')
print(fruits)
```

![python append last element](https://cdn.hashnode.com/res/hashnode/image/upload/v1669123037093/coUxW4jxT.png align="left")

#### 3\. extend()

extend() method takes only a single argument. The single argument can be a set, list, tuples, or dictionary. It automatically converts into a list and adds to the list. extend() method will take only an iterable as a parameter.

**With Sets**

```python
data = [1, 2, 3, 4, 5]
data.extend({'a', 'b', 'c', 'd'})
print(data)
```

![extend - set to list](https://cdn.hashnode.com/res/hashnode/image/upload/v1669123423310/LLbbIqrlk.png align="left")

**With Dictionary**

```python
data = [1, 2, 3, 4, 5]
data.extend({"name": "makereading", "blog": "educational"})
print(data)
```

![extend - dictionary to list ](https://cdn.hashnode.com/res/hashnode/image/upload/v1669123544858/XuRTMhfTa.png align="left")

**With String**

```python
data = [1, 2, 3, 4, 5]
data.extend("makereading")
print(data)
```

![extend - string to list](https://cdn.hashnode.com/res/hashnode/image/upload/v1669123644532/uH6CUpwhC.png align="left")

### Method to remove values from a list

We have many methods to delete, remove the items from the list,

1. remove()
    
2. pop()
    
3. del()
    
4. clear()
    

#### 1\. remove()

`remove()` method will take one parameter (the element that is to be removed). It will delete the **first occurrence** of the element.

```python
fruits = ["apple", "banana", "cherry"]  
fruits.remove("banana")  
print(fruits)
```

![remove element](https://cdn.hashnode.com/res/hashnode/image/upload/v1669124072167/fACyAmX6f.png align="left")

#### 2\. pop()

The `pop()` method removes the specified index. The default value of the index is -1.

\*\*With default value: \*\*  

```python
fruits = ["apple", "banana", "cherry"]  
fruits.pop()  
print(fruits)
```

![pop default index -1](https://cdn.hashnode.com/res/hashnode/image/upload/v1669124352588/adiUhwn63.png align="left")

\*\*With specified index: \*\*  

```python
fruits = ["apple", "banana", "cherry"]  
fruits.pop(1)  
print(fruits)
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669124408136/NOUNXbY60.png align="left")

#### 3\. del

It removes the `particular index`; also the `whole list`.

\*\*With the specified index: \*\*

```python
fruits = ["apple", "banana", "cherry"]  
del fruits[0]  
print(fruits)
```

![With the specified index](https://cdn.hashnode.com/res/hashnode/image/upload/v1669124616393/HphNRDah6.png align="left")

**Delete the object itself**

```python
fruits = ["apple", "banana", "cherry"]  
del fruits 
print(fruits)
```

![Delete the object itself](https://cdn.hashnode.com/res/hashnode/image/upload/v1669124690706/fRajGhC3Y.png align="left")

#### 4\. clear

Clear the python lists. It removes all the elements in the list.

```python
fruits = ["apple", "banana", "cherry"]  
fruits.clear()  
print(fruits)
```

![python clear](https://cdn.hashnode.com/res/hashnode/image/upload/v1669124804831/jpHRG7XZg.png align="left")

### Method to sort values from list

#### .sort()

Sorting is `Case Sensitive` in list. The sort() method sorts the list ascending by default. You can also make a function to decide the sorting criteria(s).

**Ascending Order**

```python
states = ['Tamil Nadu', 'Kerala', 'Andra', 'Telengana']
states.sort()
print(states)
```

![sort ascending order](https://cdn.hashnode.com/res/hashnode/image/upload/v1669125003430/p6N1x7rgD.png align="left")

**Descending Order**

```python
states = ['Tamil Nadu', 'Kerala', 'Andra', 'Telengana']
states.sort(reverse=True)
print(states)
```

![descending order](https://cdn.hashnode.com/res/hashnode/image/upload/v1669125059710/M7adHhOkm.png align="left")

**With key**

A function to specify the sorting criteria(s)

```python
def sortFunc(e):
  return len(e)

fruits = ["big apple", "banana", "cherry"]  

fruits.sort(key=sortFunc)
```

![sort with key function](https://cdn.hashnode.com/res/hashnode/image/upload/v1669125240098/e6thd58bc.png align="left")

### Method to copy

The copy() method returns a shallow copy of the list.

```python
# mixed list
fruits = ["apple", "orange", "lemon"]

# copying a list
fruits_fav = fruits.copy()

print('Copied List:', fruits_fav)

# Output: Copied List: ["apple", "orange", "lemon"]
```

![method copy python](https://cdn.hashnode.com/res/hashnode/image/upload/v1669125452173/VtPGuVvxA.png align="left")

### Exercise

1: Reverse a list in Python. **clue :** use slicing.  
2: Remove empty strings from the list of strings. **clue :** use remove, del, pop  
3: Add a new item to the list after a specified item. \*\*clue: \*\* use insert  
4: Extend the nested list by adding the sublist. \*\*clue: \*\* use extend  
5: Replace the list’s item with a new value if found. \*\*clue: \*\* use remove, replace  
6: Remove all occurrences of a specific item from a list. **clue** use removeAll  
7: Reverse a list. **clue** use reverse() or slicing method

### Challenges

* Hackerrank https://www.hackerrank.com/contests/makereading