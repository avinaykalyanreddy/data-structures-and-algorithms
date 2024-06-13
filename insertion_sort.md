
### Algorithm  

1. Start with the second element, assume first element is sorted.
2. now compare the current element with privious element.

3. if current element is less than privious element then swap the elements,until current element finds correct position.
4. repeat until all elements are sorted.


```python
def insertion_sort(nums):

      for i in range(1,len(nums)):

              j = i
              while nums[j-1] > nums[j] and j > 0:

                    nums[j-1],nums[j] = nums[j],nums[j-1]
                    j = j-1

nums = [64, 34, 25, 5, 22, 11, 90, 12]
insertion_sort(nums)
print(nums)
```
### Output
```
[5, 11, 12, 22, 25, 34, 64, 90]
```

### Explaination  

* let consider nums[0] is sorted array and nums[1::] unsorted array
* now start from  index 1 is 34 compare with privious element 64 if current element (34) is less than privious element then swap the poistions of element.
    1. 34 < 64 swap the position --> [34,64,25,5,22,11,90,12]
    2. 25 < 64 swap the position --> [34,25,64,5,22,11,90,12]
    3. 25 < 34 swap the position --> [25,34,64,5,22,11,90,12]
* Continue this process for each element until the list is sorted.
