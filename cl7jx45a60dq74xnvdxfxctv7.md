## Binary Search

### Introduction
Binary search compares the target value to the middle element of the array. If they are not equal, the half in which the target cannot lie is eliminated and the search continues on the remaining half, again taking the middle element to compare to the target value, and repeating this until the target value is found.

### How Binary Search Algorithm works ?
#### Process Flow
1. Consider the search_num is x.
2. Now we have to check whether the middle element is same as x.
3. If the middle element is same as search element, then return the index of middle element. 
4. If the middle element is greater than the search element, then repeat the process from index 0 to index of middle element.
5. If the middle element is lower than the search element, then repeat the process from index of middle element till the last element

### Example

Consider the array  [10, 23, 45, 54, 64, 101, 134, 200, 345, 500]


![binary search algorithm - array](https://cdn.hashnode.com/res/hashnode/image/upload/v1661960782820/rZV5wIiXy.png align="left")

**First Pass**

Consider two pointers. Left and Right. 			
Left = 0
Right = Total Number - 1 = 10 - 1 = 9

Middle index =    ( left + ( right - left ) / 2 ) = 0 + (9 - 0)/2 = 4 (floor value)

![first pass - binary search](https://cdn.hashnode.com/res/hashnode/image/upload/v1661961228571/g17xPS1Er.png align="center")

array[middle] (64)  is not equal to search num (23), also array[middle] (64) is greater than search num (23). So searching in the second half makes no sense. 

We need to search in the first half.  So set value of right pointer to middle index; and recompute the middle value. 

**Second Pass**

Left = 0
Right = 4

Middle index =    ( left + ( right - left ) / 2 ) = 0 + (4 - 0)/2 = 2 (floor value)

![second pass - binary search](https://cdn.hashnode.com/res/hashnode/image/upload/v1661961340937/TlyJe35dI.png align="center")

array[middle] (45)  is not equal to search num (23), also array[middle] (45) is greater than search num (23). So searching in the second half makes no sense. 

We need to search in the first half.  So set value of right pointer to middle index; and recompute the middle value. 

**Third Pass**

Left = 0
Right = 2

Middle index =    ( left + ( right - left ) / 2 ) = 0 + (2 - 0)/2 = 1 (floor value)


![third pass - binary search](https://cdn.hashnode.com/res/hashnode/image/upload/v1661961580981/sZpFsm0FJ.png align="center")

array[middle] (23)  is equal to search num (23), So we can return the middle index.

By using the workflow, we had reduced the number of comparisons and able to achieve the search functionality.

After 3 iteration, we were able to find the search num. 


### Applications of Binary Search
There are many applications of Binary Search. Some of them are listed below:

1. Git bisect: Suppose we have a large number of commits and some particular commit is facing some errors, so instead of linear searching over all the commits, we can use git bisect which uses binary search to find out the commit causing the error.
2. Find if a number is a square of any integer: To check if a number is a square of any integer, run a binary search from 1 to num and check if the square of mid is equal to num.
3. Dictionary: In the dictionary, all the words are arranged in lexicographical order, therefore, to find a particular word, we can simply binary search to find the alphabets without having to go through each word.

### Advantages of Binary search
1. It is a much faster algorithm.
2. It works on the divide and conquers principle.
3. It is a simple algorithm to understand.
4. It is better than a linear search algorithm since its run time complexity is O(logN).

### Disadvantages of Binary Search
1. It can be used only when data is sorted.
2. It is more complicated.
3. If random access is not supported then efficiency might be lost.
4. It can be implemented only for two-way transversal data structures.

### Problems 
1. Binary Search - https://leetcode.com/problems/binary-search/
2. Search Insert Position - https://leetcode.com/problems/search-insert-position/





