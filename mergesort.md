``` python
def merge_sort(arr):

       if len(arr) > 1:

              mid = len(arr)//2

              lefthalf = arr[:mid]
              righthalf = arr[mid:]

              merge_sort(lefthalf)
              merge_sort(righthalf)

              i = 0
              j = 0
              k = 0

              while i < len(lefthalf) and j < len(righthalf):

                          if lefthalf[i] < righthalf[j]:
                                 arr[k] = lefthalf[i]
                                 i += 1
                          else:
                              arr[k] = righthalf[j]
                              j += 1
                          k += 1
              while i < len(lefthalf):
                      arr[k] = lefthalf[i]
                      i = i+1
                      k = k+1
              while j < len(righthalf):
                      arr[k] = righthalf[j]
                      j = j+1
                      k = k+1
arr = [33,1,10,3,50,60,25,35,5,20]
merge_sort(arr)

print(arr)                    
```


                      
