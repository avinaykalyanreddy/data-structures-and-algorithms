# Bubble sort

* Bubble sort is the simple sorting algorithm, which compares each pair of adjacent elements and swaps if they are in the wrong order, this process is repeated until no swaps are needed

## Algorithm  

1. Starts from first element, compare with next element.
2. if the first element is greater than next element swap them.
3. After swapping move to the next element in the array.
4. repeat this process until array is sorted.


## Program

```python

def bubble_sort(arr):

      for i in range(len(arr)):
            for k in range(len(arr)-i-1):

                  if arr[k] > arr[k+1]:

                        temp = arr[k]
                        arr[k] = arr[k+1]
                        arr[k+1] = temp
  
arr = [5,3,8,6,7,2]
bubble_sort(arr)
print(arr)
```
## output
```
[2, 3, 5, 6, 7, 8]
```

### Time Complexity  

best case = O(n) <br>
worst case = O(n^2)

### space complexity 

O(n)
