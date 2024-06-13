## Selection Sort 
 1. An array with values to sort
 2. An inner loop goes through the array, finds the lowest value, and moves to the front of the array. This loop must loop through one less value each time it runs ( suppose it loop 5 times then next time it loop 4 times ...).
 3. The outer loop controls how many times the inner loop must run. for n values the outer loop should loop n-1 times.

### Python  
```python

def selection_sort(nums):

      for i in range(len(nums)-1):
          min_index = i
          for k in range(i+1,len(nums)):

              if nums[k] < nums[min_index]:

                      min_index = k
          nums[i],nums[min_index] = nums[min_index], nums[i]
nums = [64, 34, 25, 5, 22, 11, 90, 12]
selection_sort(nums)

print(nums)

```

### output  
```
[5, 11, 12, 22, 25, 34, 64, 90]
```
