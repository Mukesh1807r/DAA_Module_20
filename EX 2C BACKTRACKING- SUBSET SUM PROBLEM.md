# EX 2C BACKTRACKING- SUBSET SUM PROBLEM
## DATE:15:04:2025
# Subset Sum Problem

## Aim
To find and print all subsets of a given array whose sum equals a target value. The subsets are printed in a specific order based on the position of the first element in the array and the length of the subset.

## Algorithm
1. Define a helper function `findSubsets(arr, i, subset, sum_so_far, target, result)`:
   - Recursively generate all subsets.
   - If the sum of elements in the subset equals the target, add it to the result.
2. In the `subsetSum(n, arr, x)` function:
   - Initialize an empty list `result` to store valid subsets.
   - Call `findSubsets()` to generate all subsets with the target sum.
   - Sort the resulting subsets:
     - First by the index of their first element in the original array.
     - Then by the length of the subset.
3. Print the subsets.

## Program
```python
def findSubsets(arr, i, subset, sum_so_far, target, result):
    if sum_so_far == target:
        result.append(subset[:])  
        return

    if i >= len(arr) or sum_so_far > target:
        return

    subset.append(arr[i])
    findSubsets(arr, i + 1, subset, sum_so_far + arr[i], target, result)
    subset.pop()
    findSubsets(arr, i + 1, subset, sum_so_far, target, result)

def subsetSum(n, arr, x):
    result = []
    findSubsets(arr, 0, [], 0, x, result)
   
    result.sort(key=lambda subset: (arr.index(subset[0]), len(subset)) if subset else (float('inf'), float('inf')))
    
    for subset in result:
        print(subset)

n = int(input())  
arr = []
for i in range(n):
    arr.append(int(input())) 
x = int(input())  

subsetSum(n, arr, x)
```
## Output 
![image](https://github.com/user-attachments/assets/48930d2d-96a2-40dd-b850-9579f0a9c887)

## Result
The program successfully finds all subsets of the given array whose sum equals the target value and prints them in a sorted order based on the criteria specified.
