# Binary Search Trees (BST) 

**BST meaning** --> Nodes value in left sub tree is less than its root node value and each node value in right sub tree is greater than its root node value.   

## Note
When inserting or deleting nodes in a BST, the BST property should not be violated.

```python

class node:

      def __init__(self,data):
              self.data = data
              self.left = None
              self.right = None

      def insert(self,val):

            if val < self.data:

                    if self.left == None:
                          self.left = node(val)
                    else:
                          self.left.insert(val)

            else:
                 if self.right == None:
                            self.right = node(val)
                 else:
                      self.right.insert(val)

      def inorder(self,root): # root is the head of BST

            if root:  # avoid the none object
                  self.inorder(root.left)
                  print(root.data)
                  self.inorder(root.right)

      def preorder(self,root):

            if root:
                  print(root.data)
                  self.preorder(root.left)
                  self.preorder(root.right)

      def postorder(self,root):

            if root:
                  self.postorder(root.left)
                  self.postorder(root.right)
                  print(root.data)

      def delete(self,val):

                  if val < self.data:

                       

                        self.left = self.left.delete(val)                        

                  elif val > self.data:

                             

                              self.right = self.right.delete(val)

                  else:
                       if self.left == None:
                                    return self.right
                       elif self.right == None:
                                    return self.left

                       else:
                           min_node = self.right.minimum()
                           self.data = min_node.data
                  return self

      def minimum(self):
          previous = None
          temp = self
          while temp.left:
             previous = temp
             temp = temp.left
          if previous:

                previous.left = temp.right
          return temp

      def find_large(self,root):
            if root.right:
                  return self.find_large(root.right)
            else:
                  return data

      def find_small(self,root):
            if root.left:
                  return self.find_small(root.left)
            else:
                  return data

```
creating objects  
```
root = node(50)

root.insert(25)
root.insert(75)
root.insert(12)
root.insert(30)
root.insert(60)
root.insert(6)
root.insert(52)
root.insert(70)


print(root.find_large(root))
print(root.find_small(root))
```
## Output  

```
75
6
```

**Time complexity**  

worst case for searching,traversing,insert,delete O(N)  

average case for searching,insert,delete O(logN)


