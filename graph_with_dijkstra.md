
# Implementation of Graph data structure and Dijkstra algorithm

```python
class Vertex:

    def __init__(self, id):
        self.id = id
        self.connectTo = {}  # object and distance

        self.visted = False
        self.distance_from_source = float("inf")

    def addNeigbour(self, nbr, cost=0):
        self.connectTo[nbr] = cost

    def getConnections(self):
        return list(self.connectTo.keys())

    def getWeight(self, nbr):
        if nbr in self.connectTo:
            return self.connectTo[nbr]

        return None

    def __str__(self):
        return f"{self.id} connected to {[i.id for i in self.connectTo]}"


class Graph:

    def __init__(self):

        self.vertList = {}

    def addVertex(self, id):

        nv = Vertex(id)

        self.vertList[id] = nv

        return nv

    def addEdge(self, f, t, cost=0):

        if f not in self.vertList:
            self.addVertex(f)

        if t not in self.vertList:
            self.addVertex(t)

        self.vertList[f].addNeigbour(self.vertList[t], cost)

    def getVertex(self, n):

        if n in self.vertList:
            return self.vertList[n]  # object
        return None

    def getVertices(self):

        return list(self.vertList.keys())

    def __iter__(self):

        return iter(self.vertList.values())

    def __contains__(self, item):

        return item in self.vertList


g = Graph()

g.addEdge("A", "B", 3)
g.addEdge("A", "D", 1)
g.addEdge("B", "D", 3)
g.addEdge("B", "E", 5)
g.addEdge("D", "E", 1)
g.addEdge("D", "C", 6)
g.addEdge("E", "C", 2)



sourec = "A"

sourec_node = g.getVertex(sourec)


def min_length(node):
    min = float("inf")
    n = None

    for i, j in node.items():

        if j < min:
            min = j
            n = i
    if n != None:
        del node[n]
    return [min, n]


def dijkstra(source_node):
    explore = {}
    unexplore = {}

    source_node.distance_from_source = 0

    current_node = [[0, sourec_node]]

    while current_node:

        w, n = current_node.pop()

        if n not in explore:

            for i in n.connectTo:

                if i not in explore:
                    if i not in unexplore:

                        unexplore[i] = n.connectTo[i] + w

                    else:

                        if unexplore[i] > n.connectTo[i] + w:
                            unexplore[i] = n.connectTo[i] + w

        min = min_length(unexplore)  # [min,n]

        explore[n] = w

        if min[1] != None:
            current_node.append(min)

    return explore


x = (dijkstra(sourec_node))

for i in x:
    print(f"source A: to {i.id}, costs {x[i]}")
```
