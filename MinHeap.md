# Implementation of Heap Tree

```python

class MinHeap:

    def __init__(self):

        self.heap = []

    def _insert(self,val):

        self.heap.append(val)

        self.heapify_up(len(self.heap)-1)  # last index because comparing parent index

    def heapify_up(self,last_node):

        parent = (last_node-1)//2   # parent formula

        if last_node > 0 and self.heap[last_node] < self.heap[parent]:

            self.heap[last_node],self.heap[parent]  = self.heap[parent],self.heap[last_node]



            self.heapify_up(parent)

    def extract_min(self):

        if not(self.heap):

            return None

        elif len(self.heap) == 1:

            return self.heap.pop()

        min_val = self.heap[0]

        self.heap[0] = self.heap.pop()

        self.heapify_down(0)

        return min_val


    def heapify_down(self,index):

        smallest = index

        left = (2*index+1)   # child node formula
        right = (2*index+2)

        if left < len(self.heap) and self.heap[smallest] > self.heap[left]:

            smallest = left

        if right < len(self.heap) and self.heap[smallest] > self.heap[right]:
            smallest = right

        if smallest != index:

            self.heap[index],self.heap[smallest] = self.heap[smallest],self.heap[index]


            self.heapify_down(smallest)


    def __str__(self):

        return f"{self.heap}"

m = MinHeap()

m._insert(35);m._insert(33);m._insert(42);m._insert(10);m._insert(14);m._insert(19);m._insert(27);m._insert(44);m._insert(26);m._insert(31);

for i in range(10):

    print(m.extract_min())
```
