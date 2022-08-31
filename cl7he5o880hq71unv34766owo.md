## Binary Insertion Sort

### Introduction

Binary insertion sort is a sorting algorithm similar to insertion sort, but instead of using linear search to find the position where the element should be inserted, we use binary search. Thus, we reduce the number of comparisons for inserting one element from O(N) (Time complexity in Insertion Sort) to O(log N).

### Best of two worlds

Binary insertion sort is a combination of insertion sort and binary search. 

Insertion sort is sorting technique that works by finding the correct position of the element in the array and then inserting it into its correct position. Binary search is searching technique that works by finding the middle of the array for finding the element.

As the complexity of binary search is of *logarithmic order, the searching algorithm’s time complexity will also decrease to of logarithmic order*. Implementation of binary Insertion sort. this program is a simple Insertion sort program but instead of the standard searching technique binary search is used.

### How Binary Insertion Sort works ?

#### Process flow:
In binary insertion sort, we divide the array into **two** subarrays — **sorted and unsorted**. The first element of the array is in the sorted subarray, and the rest of the elements are in the unsorted one. 

We then iterate from the second element to the last element. For the i-th iteration, we make the current element our “key.” This key is the element that we have to add to our existing sorted subarray.

#### Example

Consider the array 29, 10, 14, 37, 14,

![binary insertion sort - array](https://cdn.hashnode.com/res/hashnode/image/upload/v1661929956266/DSLKdODLR.png align="center")


**First Pass**

Key = 1

Since we consider the first element is in the sorted array, we will be starting from the second element. Then we apply the binary search on the sorted array. 

![first pass - binary insertion sort ](https://cdn.hashnode.com/res/hashnode/image/upload/v1661934538052/qqF1rB3Qq.png align="center")

In this scenario, we can see that the middle element in sorted array  (29) is greater than the key element 10. So the position of the key element is 0. Then we can shift the remaining elements by 1 position.


![after binary search first pass - binary insertion sort](https://cdn.hashnode.com/res/hashnode/image/upload/v1661934765696/rVvhl09gD.png align="center")

Increment the value of key. 

**Second Pass**

Key = 2

Now the key element is 14. We will apply binary search in the sorted array to find the position of the key element. 


![binary insertion sort -  second pass](https://cdn.hashnode.com/res/hashnode/image/upload/v1661934886050/hO3y2uCQ7.png align="center")

In this scenario, by applying binary search, we can see key element to be placed at index 1 (between 10 and 29). Then we can shift the remaining elements by 1 position.


![binary insertion sort - after binary search, second pass](https://cdn.hashnode.com/res/hashnode/image/upload/v1661934956931/sbe6VJ_2K.png align="center")


**Third Pass**

Key = 3

Now the key element is 37. We will apply binary search in the sorted array to find the position of the key element. 


![binary insertion sort - third pass](https://cdn.hashnode.com/res/hashnode/image/upload/v1661935075142/N6zvcH73Q.png align="center")

In this scenario, by applying binary search, we can see key element is placed in its correct position. 

![binary insertion sort - after binary search](https://cdn.hashnode.com/res/hashnode/image/upload/v1661935158835/52ZGwrAOF.png align="center")


**Fourth Pass**

Key = 4

Now the key element is 14. We will apply binary search in the sorted array to find the position of the key element. 


![binary insertion sort - fourth pass ](https://cdn.hashnode.com/res/hashnode/image/upload/v1661935242311/YX7lhAazo.png align="center")

In this scenario, by applying binary search, we can see key element to be placed at index 2 (between 14 and 29). Then we can shift the remaining elements by 1 position.


![binary insertion sort - after binary search](https://cdn.hashnode.com/res/hashnode/image/upload/v1661935283231/zCdCYPErq.png align="center")

Now we can see all the elements are sorted.

### Code

%[https://gist.github.com/syedjafer/c0a08d7f9bc5977dd9916386f963eae4#file-binary_insertion_sort-py]
 

### Binary Insertion Sort Algorithm

Consider the array **Arr**,

1. Iterate the array from the second element to the last element.
2. Store the current element Arr[i] in a variable key.
3. Find the position of the element just greater than Arr[i] in the subarray from Arr[0] to Arr[i-1] using binary search. Say this element is at index pos.
4. Shift all the elements from index pos to i-1 towards the right.
5. Arr[pos] = key.

### Complexity Analysis

#### Worst Case
For inserting the i-th element in its correct position in the sorted, finding the position (pos) will take O(log i) steps. However, to insert the element, we need to shift all the elements from pos to i-1. This will take i steps in the worst case (when we have to insert at the starting position). 

We make a total of N insertions.  so, the worst-case time complexity of binary insertion sort is **O(N^2)**.

This occurs when the array is initially sorted in descending order.

#### Best Case
The best case will be when the element is already in its sorted position. In this case, we don’t have to shift any of the elements; we can insert the element in O(1). 

But we are using binary search to find the position where we need to insert. If the element is already in its sorted position, binary search will take (log i) steps. Thus, for the i-th element, we make (log i) operations, so its best-case time complexity is **O(N log N).**

This occurs when the array is initially sorted in ascending order.

#### Average Case
For average-case time complexity, we assume that the elements of the array are jumbled. Thus, on average, we will need O(i /2) steps for inserting the i-th element, so the average time complexity of binary insertion sort is **O(N^2).**


![binary insertion sort - time complexity](https://cdn.hashnode.com/res/hashnode/image/upload/v1661936454741/Wp1RW39K4.png align="center")

### Space Complexity Analysis
Binary insertion sort is an in-place sorting algorithm. This means that it only requires a constant amount of additional space. We sort the given array by shifting and inserting the elements. 

Therefore, the space complexity of this algorithm is O(1) if we use iterative binary search. It will be O(logN) if we use recursive binary search because of O(log N) recursive calls.

### Is Binary Insertion Sort a stable algorithm

It is a stable sorting algorithm, the elements with the same values appear in the same order in the final array as they were in the initial array.

### Cons and Pros

1. Binary insertion sort works efficiently for smaller arrays. 
2. This algorithm also works well for almost-sorted arrays, where the elements are near their position in the sorted array.
3. However, when the size of the array is large, the binary insertion sort doesn’t perform well. We can use other sorting algorithms like merge sort or quicksort in such cases.
4. Making fewer comparisons is also one of the strengths of this sorting algorithm; therefore, it is efficient to use it when the cost of comparison is high.
5. Its efficient when the cost of comparison between keys is sufficiently high. For example, if we want to sort an array of strings, the comparison operation of two strings will be high.

### Bonus Section

Binary Insertion Sort has a quadratic time complexity just as Insertion Sort. Still, it is usually faster than Insertion Sort in practice, which is apparent when comparison takes significantly more time than swapping two elements.


























