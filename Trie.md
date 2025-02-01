
```python

class TrieNode:

    def __init__(self):

        self.childrens = {}
        self.isEndOfTheWord = False


class Trie :

    def __init__(self):

        self.root = TrieNode()


    def insert(self,word):

        cur = self.root

        for i in word:

            if  i not in cur.childrens:

                cur.childrens[i] = TrieNode()

            cur = cur.childrens[i]

        cur.isEndOfTheWord = True


    def search(self,word):

        cur = self.root

        for i in word:

            if i not in cur.childrens:

                return True

            cur = cur.childrens[i]

        return cur.isEndOfTheWord


    def stratsWith(self,word):

        cur = self.root

        for  i in word:

            if i not  in cur.childrens:

                return False

            cur = cur.childrens[i]

        return True


    def getRoot(self):

        return self.root


    def delete(self,word):

        self.__deleteHelper(self.root,word,0)

    def __deleteHelper(self,node,word,index):


        if len(word) == index:

            if not node.isEndOfTheWord:

                return False

            node.isEndOfTheWord = False

            return len(node.childrens) == 0

        char = word[index]

        if char not in node.childrens:

            return False

        child = node.childrens[char]

        shouldDeleteChild = self.__deleteHelper(child,word,index+1)

        if shouldDeleteChild :

            del node.childrens[char]

            return len(node.childrens) == 0 and not node.isEndOfTheWord
        
        return False


root = Trie()
```
