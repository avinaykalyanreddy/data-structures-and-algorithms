

``` py
def quick_sort(arr):
       quick_sort_helper(arr,0,len(arr)-1)

def quick_sort_helper(arr,start,end):

      if start < end:

          splitpoint = partition(arr,start,end)
          quick_sort_helper(arr,start,splitpoint-1)
          quick_sort_helper(arr,splitpoint+1,end)
          

def partition(arr,start,end):
 
          left = start+1
          right = end
          piviotvalue = arr[start]

          done = False
          while not done:
              while left <= right and arr[left] <= piviotvalue:
    
                            left = left + 1
              while right >= left and arr[right] >= piviotvalue:
                            right -= 1
    
              if right < left:
    
                    done = True
              else:

                   temp = arr[left]
                   arr[left] = arr[right]
                   arr[right] = temp

          temp = arr[start]
          arr[start] = arr[right]
          arr[right] = temp
          return right
arr = [2,5,4]
quick_sort(arr)
print(arr)
```
