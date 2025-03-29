```python
class Vertex:

    def __init__(self,key):

        self.key = key
        self.connectedTo = {}


    def addNeighbor(self,nbr,weight=0):

        self.connectedTo[nbr] = weight


    def getWeight(self,nbr):

       return  self.connectedTo[nbr]

    def getConnections(self):

        return self.connectedTo.keys()

    def getId(self):

        return self.key

class Graph:

    def __init__(self):

        self.vertList = {}


    def addVertex(self,key):

        nv = Vertex(key)

        self.vertList[key] = nv

        return nv

    def addEdge(self,f,t,cost=0):

        if f not in self.vertList:

            nv = self.addVertex(f)

        if t not in self.vertList:

            nv = self.addVertex(t)


        self.vertList[f].addNeighbor(self.vertList[t],cost)


    def getVertex(self,key):

        return self.vertList[key]

    def getVertices(self):

        return self.vertList.keys()


g = Graph()

g.addEdge('A','B',11)
g.addEdge('A','D',2)
g.addEdge('A','C',9)
g.addEdge('B','D',10)
g.addEdge('C','D',14)
g.addEdge('C','E',16)
g.addEdge('D','E',15)

def findShortestPath(source,destination):

    path = None
    path_sum = float("inf")

    def findingPath(source,destination,s,arr,visited):
        nonlocal path_sum,path
        if source in visited:

            return
        arr.append(source)
        if source == destination:

            if  s < path_sum:

                path_sum = s
                path = arr.copy()
            arr.pop()
            return

        visited.add(source)


        for nbr in g.getVertex(source).getConnections():

            findingPath(nbr.getId(),destination,s+g.getVertex(source).getWeight(nbr),arr,visited)


        visited.remove(source)
        arr.pop()


    findingPath(source,destination,0,[],set())

    return path,path_sum


res = findShortestPath('A','E')

print(res)

```
