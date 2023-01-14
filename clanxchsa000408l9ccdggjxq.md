# Learn Python With Us - Sets

### Important Links

**Series Link**: https://makereading.com/series/python  
\*\*Challenges: \*\* https://www.hackerrank.com/contests/makereading/challenges

### Youtube

<iframe src="https://www.youtube.com/embed/hCR2giEgRSc" width="760" height="415"></iframe>

### What is a set?

A set is a collection that is `unordered`, `mutable with immutable data types`, and `unindexed`. Since it doesn't maintain the order, we can't use the index.

### Why **Set** is unordered?

So basically a set uses a **hashtable** as its underlying data structure. This explains the **O(1)** membership checking, since looking up an item in a **hashtable is an O(1)** operation, on average. Since the hashtable stores the key-value pair, it doesn't have a need to maintain the order or order of insertion. Now you know the reason for the unordered nature of the set.

### Declaration

A set data structure can be defined in two different methods,

1. **{}** using curly brackets.
    
2. **set()** method.
    

#### 1\. Using curly brackets

You can declare the set like below,

```python
data = {'d1', 'd2', 'd3'}
print(data)
```

But there is one thing to be noted, (i.e) if you want to declare an empty set we can't use this curly brackets {}.

Let's see why,

```python
data = {'d1', 'd2'}
print(type(data))
```

![python-set-data-type](https://cdn.hashnode.com/res/hashnode/image/upload/v1668842333432/jzDtc1NEk.png align="left")

But If we are going to declare an empty set, probably we should not use curly bracket,

```python
data = {}
print(type(data))
```

![python-set-declaring-empty-set](https://cdn.hashnode.com/res/hashnode/image/upload/v1668842378642/h-1qxUv3D.png align="left")

#### 2\. Using **set()**

Using set() constructor, we can convert a list, tuple, set to a set.

**List to Set :**

```python
data = set([1, 2, 3, 4])
print(data)
```

![set python](https://cdn.hashnode.com/res/hashnode/image/upload/v1668842907710/or1JW5XWZ.png align="left")

**Dictionary to Set**

```python
data = set({1:1, 2:2, 3:3})
print(data)
```

![dictionary to set](https://cdn.hashnode.com/res/hashnode/image/upload/v1668843104012/ahbll9qsF.png align="left")

**Tuple to Set**

```python
data = set((1, 2, 3))
print(data)
```

![tuple to set](https://cdn.hashnode.com/res/hashnode/image/upload/v1668843211634/5M2fq0nrX.png align="left")

### Data Types

Set is a **mutable** with the **immutable** data types. (i.e,) Set can comprise only strings, boolean, numbers, set, and tuple. It won't take a list, or dictionary as an element inside the set.

We already saw set is **internally built on top of the Hash Table**, and we can't generate a hash value for mutable data structures.

Let's see,

```python
data = [1, 2, 3]
hash(data)
```

![hash of immutable data](https://cdn.hashnode.com/res/hashnode/image/upload/v1668844023641/c2PVOZK_0.png align="left")

It will result in an error.

### Set with basic built-in functions

#### Length - len()

To find the length of the set,

```python
data = {'a', 'b', 'c'}
print(len(data))
```

![length of a set](https://cdn.hashnode.com/res/hashnode/image/upload/v1668844383372/Bxzvun8R4.png align="left")

#### Type of data structure - type()

```python
data = {'a', 'b', 'c'}
print(type(data))
```

![data type of set](https://cdn.hashnode.com/res/hashnode/image/upload/v1668844649249/_cYEql70C.png align="left")

#### **max() & min()**

To find the maximum value and the minimum value of a set,

```python
values = {1, 2, 3, 4, 5, 6}
print("Max of values is ", max(values))
print("Min of values is ", min(values))
```

![maximum minimum value](https://cdn.hashnode.com/res/hashnode/image/upload/v1668847632112/oeF8H9TL5.png align="left")

#### **any()**

If any of the values in the set is true (i.e,) Non-Zero , Non-Empty String, False values then it will return True, else False.

```python
data = {0, 'makereading', False}
print(any(data)) # Will return True since it has 'makereading' non empty string.

data = {0, '', False}
print(any(data)) # Will return False since all the values are false.
```

![python any](https://cdn.hashnode.com/res/hashnode/image/upload/v1668848171631/G5dNYMrbr.png align="left")

#### **all()**

The all() function returns True if all items in an iterable are true, otherwise it returns False. If the iterable object is empty, the all() function also returns True.

```python
data = {1, 2, 3}
print(all(data)) # True, since all the elements are having true value

data = {1, 2, 0}
print(all(data)) # False, since it has 0
```

![python all](https://cdn.hashnode.com/res/hashnode/image/upload/v1668848397364/3VMA21rDd.png align="left")

### Accessing Elements of Set

Since the set is unordered, we can't access using the index values,

![accessing set element](https://cdn.hashnode.com/res/hashnode/image/upload/v1668848823232/7QTBS4yCo.png align="left")

So the ways to access the set are,

1. **for** loop
    
2. **in** and **not in**
    

#### 1\. **for** loop

```python
fruits = {"apple", "papaya", "banana", "orange"}
for element in fruits:
    print(element)
```

\*\*output: \*\*

![python for](https://cdn.hashnode.com/res/hashnode/image/upload/v1668849002216/Fsg6eeoFL.png align="left")

#### 2\. **in and not in**

```python
fruits = {"apple", "papaya", "banana", "orange"}
print("apple" in fruits)
print("orange" not in fruits)
```

\*\*output: \*\*

![python in notin](https://cdn.hashnode.com/res/hashnode/image/upload/v1668849102520/n_3zwVb_9.png align="left")

### Adding elements to the set

There are two ways of adding element to the set.

1. add() - Method to add an element to the set. It takes the immutable item as a parameter to add to the set.
    
2. update() - Method to merge an existing set with the mutable and immutable data structures.
    

#### **add()**

The add() method adds an element to the set. If the *element already exists*, the add() method **does not add** the element.

```python
data = {1, 2, 3, 4, 5}
data.add(10)

print('data', data)
```

![python add](https://cdn.hashnode.com/res/hashnode/image/upload/v1668849477743/cqwZzKE-d.png align="left")

#### **update()**

Update() method takes only a single argument. The single argument can be a set, list, tuples or a dictionary. It automatically converts into a set and adds to the set.

**With Lists**

```python
data = {1, 2, 3, 4, 5}
data.update([11, 10, 12])
```

![python set lists](https://cdn.hashnode.com/res/hashnode/image/upload/v1668849679118/TWZh9cSVn.png align="left")

**With Dictionary**

```python
data = {1, 2, 3, 4, 5}
data.update({"a":"a", "b":"b", "c":"c"})
print(data)
```

![python set dict to set](https://cdn.hashnode.com/res/hashnode/image/upload/v1668849773299/VWT1FYw7V.png align="left")

**With String**

```python
data = {1, 2, 3, 4, 5}
data.update('makereading')
print(data)
```

![python set update](https://cdn.hashnode.com/res/hashnode/image/upload/v1668849838486/YPZtb0Agq.png align="left")

### Removing Items from the Set

We have many methods to delete, remove the items from the set,

1. remove()
    
2. discard()
    
3. pop()
    
4. del
    
5. clear
    

#### 1\. Remove

If the element is present then it will remove, else it will throw error.

\*\*Example 1: \*\*

```python
data = {1, 'python', 'set', 100}
data.remove('set')
print(data)
```

![python remove](https://cdn.hashnode.com/res/hashnode/image/upload/v1668850203960/fvCd8dHqX.png align="left")

**Example 2:**

```python
data = {1, 'python', 'set', 100}
data.remove('kuku')
print(data)
```

![python remove](https://cdn.hashnode.com/res/hashnode/image/upload/v1668850275177/5iVdr-4c8.png align="left")

#### 2\. discard()

**discard()** method is having the same functionality as the **remove()** method, but it will fail safe. (i.e) Even if the value is not there it wont throw an error.

\*\*Example 1: \*\*

```python
data = {1, 'python', 'set', 100}
data.discard('set')
print(data)
```

![python discard](https://cdn.hashnode.com/res/hashnode/image/upload/v1668850461480/SwhN-fN3q.png align="left")

**Example 2:**

Even if the element 'kuku' is not present, it wont throw an error.

```python
data = {1, 'python', 'set', 100}
data.discard('kuku')
print(data)
```

![python discard](https://cdn.hashnode.com/res/hashnode/image/upload/v1668850514688/bsf2KyOEp.png align="left")

#### 3\. pop()

**pop()** method in set will remove any random element in the set and returns the removed element. Set is unordered, we can specify the index value as list.pop()

```python
fruits = {'apple', 'orange', 'banana'}
removed_element = fruits.pop()
print(removed_element, fruits)
```

![python set pop](https://cdn.hashnode.com/res/hashnode/image/upload/v1668851612201/Gq-iZ1CJc.png align="left")

#### 4\. del

**del** will delete the object itself.

```python
fruits = {'apple', 'orange', 'banana'}
del fruits
print(fruits)
```

![python set - del](https://cdn.hashnode.com/res/hashnode/image/upload/v1668851715162/vKNriq66s.png align="left")

#### 5\. Clear

Clear will empty the set,

```python
fruits = {'apple', 'orange', 'banana'}
fruits.clear()
print(fruits)
```

![set removal - clear](https://cdn.hashnode.com/res/hashnode/image/upload/v1668851799934/nbBU-qBpR.png align="left")

### Sorting

We can sort the set, using `sorted` function, but the return type of the sorted is `list`.

```python
fruits = {"apple", "orange", "lemon", "banana", "papaya"}
print(sorted(fruits))
```

![sorting python set](https://cdn.hashnode.com/res/hashnode/image/upload/v1668851941230/oJ6xLKgLW.png align="left")

### Copying

We can copy the set using the .copy() method,

```python
fruits = {"apple", "orange", "lemon", "banana", "papaya"}
fruits_2 = fruits.copy()

fruits.add('pineapple')
print(fruits, fruits_2, id(fruits), id(fruits_2)
```

![Copying python](https://cdn.hashnode.com/res/hashnode/image/upload/v1668852065784/2tTbHxkAS.png align="left")

#### Mathematical Functionalities

Sets are the fundamental **property of mathematics**. Now as a word of warning, sets, by themselves, seem pretty pointless. But it's only when we apply sets in different situations do they become the powerful building block of mathematics that they are.

Math can get amazingly complicated quite fast. Graph Theory, Abstract Algebra, Real Analysis, Complex Analysis, Linear Algebra, Number Theory, and the list goes on. But there is one thing that all of these share in common: **Sets**.

During our school days, we might have learned about union, intersection, difference, venn diagrams and more.

Using the python sets, we can achieve the above functionalities,

### 1\. Union

![iunion](https://cdn.hashnode.com/res/hashnode/image/upload/v1668854676973/EFMAdwNti.png align="left")

Union of two sets will return all the items present in both sets (all items will be present only once). This can be done with either the `|` operator or the `union()` method.

> 📝 `union()` will return a new set. It's not **inplace** change.

```python
set_a = {"apple", "banana", "orange"}
set_b = {"lemon", "jackfruit", "strawberry"}

union_val = set_a.union(set_b)
print(union_val)
```

![union](https://cdn.hashnode.com/res/hashnode/image/upload/v1668854829185/9px0C_Xpa.png align="left")

### 2\. Intersection

![intersection](https://cdn.hashnode.com/res/hashnode/image/upload/v1668854868141/-6xSSHbva.png align="left")

The intersection of two sets will return only the common elements in both sets. The intersection can be done using the `&` operator and `intersection()` method.

```python
fruits = {"apple", "orange", "banana" }
fav_fruits = {"apple", "jackfruit", "lemon"}

common_fruits = fruits & fav_fruits
print(common_fruits)

common_fruits = fruits.intersection(fav_fruits)
print(common_fruits)
```

![intersection_update](https://cdn.hashnode.com/res/hashnode/image/upload/v1668855028120/zedXZHf4Y.png align="left")

> `intersection()` will return a new set. It's not **inplace** change.

To have an inplace change, python provides `intersection_update` functionality, to update the first set.

```python
fruits = {"apple", "orange", "banana" }
fav_fruits = {"apple", "jackfruit", "lemon"}

fruits.intersection_update(fav_fruits)
print(fruits)
```

![intersection_update](https://cdn.hashnode.com/res/hashnode/image/upload/v1668855245415/R1re0Y7TW.png align="left")

### 3\. Difference

![difference_update](https://cdn.hashnode.com/res/hashnode/image/upload/v1668855313669/AM2u4p8_T.png align="left")

The difference operation will return the items that are present only in the first set i.e the set on which the method is called. This can be done with the help of the `-` operator or the `difference()` method.

```python
fruits = {"apple", "orange", "banana" }
fav_fruits = {"apple", "jackfruit", "lemon"}

result = fruits.difference(fav_fruits)
print(result)
```

![difference_update](https://cdn.hashnode.com/res/hashnode/image/upload/v1668855406173/URvS9YEy0.png align="left")

> `difference()` will return a new set. It's not **inplace** change.

To have an inplace change, python provides `difference_update` functionality, to update the first set.

```python
fruits = {"apple", "orange", "banana" }
fav_fruits = {"apple", "jackfruit", "lemon"}

fruits.difference_update(fav_fruits)
print(fruits)
```

![difference_update](https://cdn.hashnode.com/res/hashnode/image/upload/v1668855498512/8f6T9VqIB.png align="left")

### 4\. Symmetric Difference

![symmetric_difference](https://cdn.hashnode.com/res/hashnode/image/upload/v1668855550742/fmssjcSHB.png align="left")

The Symmetric difference operation returns the elements that are unique in both sets. This is the opposite of the intersection. This is performed using the ^ operator or by using the symmetric\_difference() method.

```python
fruits = {"apple", "orange", "banana" }
fav_fruits = {"apple", "jackfruit", "lemon"}

result = fruits.symmetric_difference(fav_fruits)
print(result)
```

![symmetric_difference](https://cdn.hashnode.com/res/hashnode/image/upload/v1668855596341/yNVQme7KW.png align="left")

> `symmetric_difference()` will return a new set. It's not **in place** change.

To have an in-place change, python provides `symmetric_difference_update` functionality, to update the first set.

```python
fruits = {"apple", "orange", "banana" }
fav_fruits = {"apple", "jackfruit", "lemon"}

fruits.symmetric_difference_update(fav_fruits)
print(fruits)
```

![symmetric difference](https://cdn.hashnode.com/res/hashnode/image/upload/v1668855669476/tovQFW1Qj.png align="left")

### 5\. Disjoint

![disjoint set python](https://cdn.hashnode.com/res/hashnode/image/upload/v1668858473783/gF7vzy0OF.png align="left")

Two sets are called disjoint sets if they don't have any element in common, the intersection of sets is a null set.

```python
set_a = {1, 2, 3}
set_b = {4, 5, 6}

print(set_a.isdisjoint(set_b))
```

![disjoint set](https://cdn.hashnode.com/res/hashnode/image/upload/v1668858626989/HO27hAP9S.png align="left")

### 6\. subset and superset.

![superset and subset](https://cdn.hashnode.com/res/hashnode/image/upload/v1668858655337/tn-RTWwPZ.png align="left")

The issuperset() method returns True if a set has every elements of another set (passed as an argument). If not, it returns False. Set X is said to be the superset of set Y if all elements of Y are in X . Here, set B is a superset of set A and A is a subset of set B .

```python
set_a = {1, 2, 3, 4, 5}
set_b = {2, 4, 5}

print(set_a.issuperset(set_b), set_b.issubset(set_a))
```

![superset and subset python](https://cdn.hashnode.com/res/hashnode/image/upload/v1668858791069/aXkkAVLgS.png align="left")

### Exercise

\*\*1: \*\*Add a list of elements to a set, \*\*clue: \*\* Use a constructor.  
\*\*2: \*\*Return a new set of identical items from two sets, \*\*clue: \*\* Use intersection.  
\*\*3: \*\*Get Only unique items from two sets, \*\*clue: \*\* Use union.  
\*\*4: \*\*Update the first set with items that don’t exist in the second set, \*\*clue: \*\* difference; in place  
\*\*5: \*\*Remove items from the set at once, \*\*clue: \*\* remove, pop, clear  
\*\*6: \*\*Return a set of elements present in Set A or B, but not both, \*\*clue: \*\* symmetric difference  
\*\*7: \*\*Check if two sets have any elements in common. If yes, display the common elements, \*\*clue: \*\* intersection  
\*\*8: \*\*Update set1 by adding items from set2, except common items, \*\*clue: \*\* difference  
\*\*9: \*\*Remove items from set1 that are not common to both set1 and set2, \*\*clue: \*\* intersection update  

### Challenges

* **Hackerrank** - https://www.hackerrank.com/contests/makereading/challenges