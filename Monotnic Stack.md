
# Monotonic Stack   

Monotonic stack is special type of stack that maintains elements in specific order (increasing or decreasing). It commonly used in **next greater element**,**next smaller element**.  


### Key points  

1. ###### Monotonic Increasing Stack:
   * Keeps elements in increasing order (smallest at the bottom, largest at the top).
   * While adding new element, remove elements from the stack if they are greater than the new element.

2. ###### Monotonic Decreasing Stack:

    * Keeps elements in decreasing order (bottom element is largest, top element is smallest).
    * While adding new element, remove elements from the stack if they are smaller than the current element.  

### Steps to Build a Monotonic Increasing Stack:

1. Initialize the empty stack
2. Iterate through the array elements one by one and for each element:  
   * While stack is not empty and top element should be more than current element.   
     *  pop element from the stack
   * Push the current element to the stack
3. At the end of the iteration, the stack will contain the monotonic increasing order of elements.

```python
arr = [3, 7, 1, 8]

monotonic_stack = []

for i in arr:
    
    while monotonic_stack and monotonic_stack[-1] > i:
        
        monotonic_stack.pop()
        
    monotonic_stack.append(i)
    
print(monotonic_stack)


```
            

