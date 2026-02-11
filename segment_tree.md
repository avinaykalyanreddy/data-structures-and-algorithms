```python
arr = [1, 3, 5, 7, 9, 11]

class Node:


    def __init__(self,start,end,total):

        self.start = start
        self.end = end
        self.total = total

        self.left = None
        self.right = None



def build_segment_tree(arr,start,end):

    if start == end:

        return Node(start,end,arr[start])

    mid = (start+end)//2

    left_child = build_segment_tree(arr,start,mid)
    right_child = build_segment_tree(arr,mid+1,end)

    total_sum = left_child.total    + right_child.total

    root = Node(start,end,total_sum)

    root.left = left_child
    root.right = right_child

    return root


root = build_segment_tree(arr,0,len(arr)-1)



def query(node,L,R):

    if node.end < L or node.start > R:

        return 0

    if L <= node.start and node.end <= R:

        return  node.total

    return query(node.left,L,R) + query(node.right,L,R)


def update(node,idx,val):

    if node.start == node.end == idx:

        node.total = val

        return node.total


    mid = (node.start + node.end)//2

    if (idx <= mid):

        left_sum = update(node.left,idx,val)

        right_sum = node.right.total

    else:

        left_sum = node.left.total
        right_sum = update(node.right,idx,val)

    node.total =  left_sum+right_sum

    return node.total



update(root,2,40)

print(query(root,2,2))
```