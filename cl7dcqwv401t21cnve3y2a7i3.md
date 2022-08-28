## Selection Sort Algorithm

### Selection Sort

The selection sort algorithm sorts an array by iteratively finding the **minimum** (for ascending order) / **maximum** (for descending order) element from the unsorted part and putting it at the beginning of the array. 

The algorithm will be considering two subarrays in a given array.
1. The subarray which is already sorted. 
2. Remaining subarray which is unsorted.

In every iteration of selection sort, the minimum element (considering ascending order)/ the maximum element (considering descending order) from the unsorted subarray is picked and moved to the sorted subarray. The movement is the process of swapping the minimum element with the current element. 

### How selection sort works ? 

We will see the implementation of sorting in ascending order. 

Consider the array : 29,10,14,37,14


![selection sort array](https://cdn.hashnode.com/res/hashnode/image/upload/v1661685034486/r3kJeMXbn.png align="left")

#### First Iteration
 
Initially the val of **min_index** is 0. The element at the min_index is 29.
 
Then we can iterate over the rest of the array to find if there are any element which are minimum than the element at min_index. 


![first pass - selection sort](https://cdn.hashnode.com/res/hashnode/image/upload/v1661685945853/zAlTE1BLK.png align="center")
 
By iterating, we found 10 is the minimum element present in the array. Thus, replace 29 with 10. After one iteration 10, which happens to be the least value in the array, tends to appear in the first position of the sorted list.


![after first pass - selection sort](https://cdn.hashnode.com/res/hashnode/image/upload/v1661686073044/iJIpj7Ihc.png align="center")



#### Second Iteration

Now the value of **min_index** will be incremented by 1. So now it will be **min_index = 1** . Then we can iterate over the rest of the array to find if the there are any element which are minimum than the element at min_index. 


![second pass](https://cdn.hashnode.com/res/hashnode/image/upload/v1661687692031/mjWd0tFs4.png align="center")

By iterating, we found 14 is the minimum element present in the array. Thus, swap 29 with 14. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661687795605/WN1Fz1e0u.png align="center")


#### Third Iteration

We can repeat the same process till the entire array is sorted. 

Now the value of **min_index** will be incremented by 1. So now it will be **min_index = 2** . Then we can iterate over the rest of the array to find if the there are any element which are minimum than the element at min_index. 


![third pass](https://cdn.hashnode.com/res/hashnode/image/upload/v1661688008150/8AwWgseO_.png align="center")

By iterating, we found 14 is the minimum element present in the array. Thus, swap 29 with 14. 


![after third pass](https://cdn.hashnode.com/res/hashnode/image/upload/v1661688079587/TSIoAJj5k.png align="center")

#### Fourth Iteration

Now the value of **min_index** will be incremented by 3. So now it will be **min_index = 3** . Then we can iterate over the rest of the array to find if the there are any element which are minimum than the element at min_index. 


![fourth pass](https://cdn.hashnode.com/res/hashnode/image/upload/v1661688191005/AJa_okLfp.png align="center")

By iterating, we found 29 is the minimum element present in the array. Thus, swap 29 with 37. 

![after fourth pass](https://cdn.hashnode.com/res/hashnode/image/upload/v1661688354801/AGFPPh-93.png align="center")


#### Its Done.

After 4th iteration, the entire array is sorted. 

![selection sort completed](https://cdn.hashnode.com/res/hashnode/image/upload/v1661688429245/sFPTtzdet.png align="center")

So we can define the approach like, 

- Initialize minimum value(min_index) to location 0
- Traverse the array to find the minimum element in the array
- While traversing if any element smaller than min_index is found then swap both the values.
- Then, increment min_index to point to next element
- Repeat until array is sorted

### Code

%[https://gist.github.com/syedjafer/cf993d0613e3d0b182972077ad98e0c0#file-selection_sort-py]

### Complexity analysis

#### Time Complexity

The sort complexity is used to express the number of execution times it takes to sort the list. The implementation has two loops. The outer loop which picks the values one by one from the list is executed n times where n is the total number of values in the list. The inner loop, which compares the value from the outer loop with the rest of the values, is also executed n times where n is the total number of elements in the list.

Therefore, the number of executions is (n * n), which can also be expressed as O(n2). 

1. **Worst case** – this is where the list provided is in descending order. The algorithm performs the maximum number of executions which is expressed as [Big-O] O(n2)
2. **Best case** – this occurs when the provided list is already sorted. The algorithm performs the minimum number of executions which is expressed as [Big-Omega] Ω(n2)
3. **Average case** – this occurs when the list is in random order. The average complexity is expressed as [Big-theta] Θ(n2)


![Time Complexity - selection sort](https://cdn.hashnode.com/res/hashnode/image/upload/v1661688719102/Pa8LT2GeC.png align="center")

#### Space Complexity
Since selection sort is an inplace sorting algorithm, it has a space complexity of O(1) as it requires one temporal variable used for swapping values.

### Is Selection sort algorithm stable ?
The default implementation is not stable. However it can be made stable. But it can be achived using stable selection sort.

### Is Selection Sort Algorithm in-place?
Yes, it does not require extra space.

### When to use selection sort ?

1. Selection sort can be good at checking if everything is already sorted 😂. 
2. It is also good to use when **memory space is limited**. This is because unlike other sorting algorithms, selection sort doesn't go around swapping things until the very end, resulting in **less temporary storage space** used.
3. When a simple sorting implementation is desired
4. When the array to be sorted is relatively small

### When to avoid selection sort ?

1. The array to be sorted has a large number of elements
2. The array is nearly sorted
3. You want a faster run time and memory is not a concern.

### Summary

1. Selection sort is an in-place comparison algorithm that is used to sort a random list into an ordered list. It has a time complexity of O(n2)
2. The list is divided into two sections, sorted and unsorted. The minimum value is picked from the unsorted section and placed into the sorted section.
3. This thing is repeated until all items have been sorted.
4. The time complexity measures the number of steps required to sort the list.
5. The worst-case time complexity happens when the list is in descending order. It has a time complexity of [Big-O] O(n2)
6. The best-case time complexity happens when the list is already in ascending order. It has a time complexity of [Big-Omega] O(n2)
7. The average-case time complexity happens when the list is in random order. It has a time complexity of [Big-theta] O(n2)
8. The selection sort is best used when you have a small list of items to sort, the cost of swapping values does not matter, and checking of all the values is mandatory.
9. The selection sort does not perform well on huge lists

### Bonus Section

**For the bigger array, how selection sort will work with insertion sort ?**

The size of the array involved is rarely of much consequence. The real question is the speed of comparison vs. copying. The time a selection sort will win is when a comparison is a lot faster than copying. Just for example, let's assume two fields: a single int as a key, and another megabyte of data attached to it.In such a case, comparisons involve only that single int, so it's really fast, but copying involves the entire megabyte, so it's almost certainly quite a bit slower.
 
Since the selection sort does a lot of comparisons, but relatively few copies, this sort of situation will favor it. 

### Problems to try
1. Sort Colors - https://leetcode.com/problems/sort-colors/
2. Hackerearth - https://www.hackerearth.com/practice/algorithms/sorting/selection-sort/practice-problems/algorithm/old-keypad-in-a-foreign-land-24/













