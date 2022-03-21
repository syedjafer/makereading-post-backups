## Insertion Sorting Algorithm

### Introduction

Insertion sort is a **simple and efficient comparison** sort. In this algorithm, each iteration removes an element from the input data and inserts it into the correct position in the list is sorted.

Insertion Sort repeatedly invokes an insert helper function to ensure A[0, i] is properly sorted; eventually, I reach the rightmost element, sorting A entirely.

The choice of the element being removed from the input is random and this process is repeated until all input elements have gone through.

### Explanation

1. Consider we are having an array,
> arr = [3,1,10,2,8]

2. We are iterating through each element and will be checking whether the current element is greater than the elements on the left side of the current element. If not, we will be swapping the elements.

3. **1st Iteration:** 
> Cur. Element = 3 <br>
 So on the first iteration, no elements are present to the left of 3. <br>
 arr = [ 3, 1, 10, 2, 8 ] <br>

4. ** 2nd Iteration:**
> Cur. Element = 1 <br>
 Now there is an element to the left of 1 ( 3 ). So we will be swapping 3 and 1. <br>
 so the resultant array will be, <br>
 arr = [ 1, 3, 10, 2, 8] <br>

5. **3rd Iteration:**
> Cur. Element = 10 <br>
 Now, elements 1, 3 are to the left of 10. Since they are in order we need not to swap. <br>
 arr = [1, 3, 10, 2, 8] <br>

6. **4th Iteration:**
> Cur. Element = 2 <br>
 Now there are elements to the left of 2 which are greater than 2.  <br>
 arr = [1, 3, 2, 10, 8] <br>
 arr = [1, 2, 3, 10, 8] <br>

7. **5th Iteration:**
> Cur. Element = 8 <br>
 Now there is an element 10 to the left of 8 , which is greater than 8. <br>
 We will be swapping 8 and 10. <br>
 arr = [1, 2, 3, 8, 10] <br>

8. So, now we will be having the sorted array.


### Characteristics of Insertion Sort

1. Insertion Sort requires very little extra space to function; it only needs to reserve space for a single element.
2. The optimal performance occurs when the array is already sorted, and arrays sorted in reverse order produce the worst performance for Insertion Sort.
3. Insertion sort is used when the data is nearly sorted (due to its adaptiveness) or when the input size is small (due to its low overhead).
4. Insertion sort is almost linear for partially sorted input.


### Time Complexity

| BEST CASE | AVERAGE CASE  | WORST CASE |
|-----------|---------------|------------|
| O(N)      | O(N2)         | O(N2)      |