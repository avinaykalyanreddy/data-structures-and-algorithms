```python
import heapq

graph = {
    'A': [(4, 'B'), (2, 'C')],
    'B': [(5, 'C'), (10, 'D')],
    'C': [(3, 'D')],
    'D': [(7, 'E')],
    'E': [(1, 'F')],
    'F': []
}

pq = []
visited = set()
res = []

heapq.heappush(pq, (0, "A", None))  # Start from A with cost 0

while pq:
    dis, node, p = heapq.heappop(pq)

    if node not in visited:
        visited.add(node)

        if p is not None:  # Avoid appending the initial (0, None, 'A')
            res.append((dis, p, node))

        for d, n in graph[node]:
            if n not in visited:
                heapq.heappush(pq, (d, n, node))

print(res)

```
