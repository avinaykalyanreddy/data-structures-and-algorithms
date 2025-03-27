```python

import heapq

class Vertex:
    def __init__(self, id):
        self.id = id
        self.connectedTo = {}

    def addNeighbor(self, nbr, weight=0):
        self.connectedTo[nbr] = weight

    def getConnections(self):
        return self.connectedTo.keys()

    def getId(self):
        return self.id

    def getWeight(self, nbr):
        return self.connectedTo[nbr]

    def __str__(self):
        return str(self.id) + " Connected To " + str([x.id for x in self.connectedTo])

class Graph:
    def __init__(self):
        self.vertList = {}
        self.numVertices = 0

    def addVertex(self, key):
        self.numVertices += 1
        nv = Vertex(key)
        self.vertList[key] = nv
        return nv

    def addEdge(self, f, t, cost=0):
        if f not in self.vertList:
            self.addVertex(f)
        if t not in self.vertList:
            self.addVertex(t)
        self.vertList[f].addNeighbor(self.vertList[t], cost)

    def getVertex(self, n):
        if n in self.vertList:
            return self.vertList[n]
        return None

    def getVertices(self):
        return self.vertList.keys()

    def __contains__(self, item):
        return item in self.vertList

    def __iter__(self):
        return iter(self.vertList.values())

# Creating Graph
g = Graph()
g.addEdge('A', 'B', 7)
g.addEdge('A', 'C', 12)
g.addEdge('B', 'D', 9)
g.addEdge('B', 'C', 2)
g.addEdge('D', 'F', 1)
g.addEdge('C', 'E', 10)
g.addEdge('E', 'D', 4)
g.addEdge('E', 'F', 5)

for i in g:
    print(i)

# Dijkstra's Algorithm

def dijkstra(graph, start):
    pq = []  # Priority queue (min-heap)
    distances = {v: float('inf') for v in graph.getVertices()}
    distances[start] = 0

    heapq.heappush(pq, (0, start))  # Push (distance, vertex)

    while pq:
        current_distance, current_vertex = heapq.heappop(pq)

        # Skip if we already found a shorter path
        if current_distance > distances[current_vertex]:
            continue

        # Get current vertex from the graph
        current_node = graph.getVertex(current_vertex)

        for neighbor in current_node.getConnections():
            weight = current_node.getWeight(neighbor)
            distance = current_distance + weight

            if distance < distances[neighbor.getId()]:  # Found a shorter path
                distances[neighbor.getId()] = distance
                heapq.heappush(pq, (distance, neighbor.getId()))

    return distances



# Running Dijkstra from 'A'
res = dijkstra(g, 'A')
print(res)
```
