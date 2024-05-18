**AVL Tree**: An AVL Tree is a self balancing binary tree named after its inventors, Georgy Adelson Velsky and Landis who published it in 1962.  
<br>
**Balancing factor:** Height of the left subtree - heigth of the right subtree is called balancing factor.

* if balancing factor is 1 it means left subtree is one level greater than right subtree.
* if balancing factor is -1 it means right subtree is one level greater than left subtree.
* if balancing factor is 0 it mean right subtree and left subtree contains equal height.

# Rotations

## Single rotation
1. LL rotation: node is inserted in left subtree of left subtree of A(node).
2. RR rotation: node is inserted in right subtree of right subtree of A.

## Double rotation
1. LR : node is inserted in right subtree of left subtree of A.
2. RL: node is inserted in left subtree of right subtree of A.

# Implementation

```python
class node:

    def __init__(self,val):

        self.val = val
        self.right = None
        self.left  = None
        self.height = 1

class AVLTree:

    def get_height(self,root):

        if not root:
            return 0
        
        return root.height
    
    def update_height(self,root):

        root.height = 1+max(self.get_height(root.left),self.get_height(root.right))

    def get_balance(self,root):

        if not root :

            return 0
        
        return self.get_height(root.left) - self.get_height(root.right)
    
    def left_rotation(self,x):

        y = x.right
        lc = y.left

        y.left = x
        x.right = lc

        self.update_height(x)
        self.update_height(y)

        return y
    
    def right_rotation(self,y):
        x = y.left
        rc = x.right

        x.right = y
        y.left = rc

        self.update_height(y)
        self.update_height(x)

        return x
    
    def insert(self,root,val):

        if not root:
            return node(val)
        
        elif val < root.val:

            root.left = self.insert(root.left,val)

        else:

            root.right = self.insert(root.right,val)

        self.update_height(root)

        balance = self.get_balance(root)

        if balance > 1 and val < root.left.val:
            return self.right_rotation(root)
        
        if balance < -1 and val > root.right.val:

            return self.left_rotation(root)
        
        if balance > 1 and val > root.left.val:

            root.left = self.left_rotation(root.left)

            return self.right_rotation(root)
        
        if balance < -1 and val < root.right.val:

            root.right = self.right_rotation(root.right)

            return self.left_rotation(root)

        return root
    
    def delete(self,root,val):

        if not root:
            return root
        
        elif val < root.val:

            root.left = self.delete(root.left,val)

        elif val > root.val:

            root.right = self.delete(root.right,val)

        else:

            if root.left == None:

                return root.right
            
            if root.right == None:

                return root.left
            


            min_node = self.minimum(root.right)

            root.val = min_node.val

            root.right = self.delete(root.right,min_node.val)

        self.update_height(root)

        balance = self.get_balance(root)

        if balance > 1 and self.get_balance(root.left) >= 0:

            return self.right_rotation(root)
        
        if balance < -1 and self.get_balance(root.right) <= 0:

            return self.left_rotation(root)
        
        if balance > 1 and self.get_balance(root.left) < 0:

            root.left = self.left_rotation(root.left)

            return self.right_rotation(root)
        
        if balance < -1 and self.get_balance(root.right) > 0:

            root.right = self.right_rotation(root.right)

            return self.left_rotation(root)
        
        return root

    
    def minimum(self,node):
        if node:
            temp = node.left

            while temp.left:

                temp = temp.left

            return temp

        return node
    def inorder(self,root):
            if root:

                 self.inorder(root.left)
                 print(root.val)
                 self.inorder(root.right)

tree  = AVLTree()
root= None

for i in range(1,10):
    root = tree.insert(root,i)

```
## Complexity 

insertion: O(logn)  
deletion: O(logn)  
searching: O(logn) <br>
space: O(n)

