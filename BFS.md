
```python

import heapq
from collections import deque


class Vertex:

    def __init__(self,id):
        self.id = id

        self.connectedTo = {}


    def addNeighbor(self,nbr,weight=0):

        self.connectedTo[nbr] = weight


    def getWeight(self,nbr):

        return self.connectedTo[nbr]


    def getConnections(self):

        return self.connectedTo.keys()

    def getId(self):

        return self.id

    def __str__(self):

        return str(self.id) + " connected to " + str([x.id for x in self.connectedTo])


class Graph:

    def __init__(self):

        self.vertList = {}



    def addVertex(self,key):

        nv = Vertex(key)

        self.vertList[key] = nv

        return nv

    def addEdge(self,f,t,cost):

        if f not in self.vertList:

            nv = self.addVertex(f)

        if t not in self.vertList:

            nv = self.addVertex(t)



        self.vertList[f].addNeighbor(self.vertList[t],cost)


    def getVertex(self,n):

        if n in self.vertList:

            return self.vertList[n]

        return None

    def getVertices(self):

        return self.vertList.keys()

    def __contains__(self, item):

        return item in self.vertList

    def __iter__(self):

        return iter(self.vertList.values())


g = Graph()

g.addEdge('A','B',7)
g.addEdge('B','D',9)
g.addEdge('A','C',12)
g.addEdge('B','C',2)
g.addEdge('D','F',1)
g.addEdge('C','E',10)
g.addEdge('E','D',4)
g.addEdge('E','F',5)

def BFS(graph,start):

    explore = set()
    d = deque([start])
    
    while d :
        
        current = d.popleft()
        
        if current not in explore:
            
            print(current)
            
            explore.add(current)
            
            for neighbor in graph.getVertex(current).getConnections():
                
                nbr_id = neighbor.getId()
                
                if nbr_id not in explore:
                    
                    d.append(nbr_id)

BFS(g,'A')
```
