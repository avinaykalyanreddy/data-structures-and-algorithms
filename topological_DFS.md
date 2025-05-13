```python
graph = {

    0:[],
    1:[],
    2:[3],
    3:[1],
    5:[0,2],
    4: [0,1]

}

stack = []
visited = set()
def dfs(node):

    if node not in visited:

        visited.add(node)

        for nbr in graph[node]:

            dfs(nbr)

        stack.append(node)




for i in range(6):

    if i not in visited:

        dfs(i)

stack.reverse()
print(stack)
```
