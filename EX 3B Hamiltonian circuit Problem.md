# EX 3B Hamiltonian Circuit Problem
## DATE:17-07-2025
## AIM:
To write a python program to check whether Hamiltonian path exits in the given graph.

## Algorithm


1. Initialize an adjacency matrix for the graph with `V` vertices.  
2. Start the Hamiltonian cycle at vertex `0`, initializing the path with `-1`s.  
3. Recursively try all vertices as candidates for the next position in the path.  
4. Check if the vertex is connected to the last vertex in the path and not already in the path (`isSafe`).  
5. If valid, add the vertex to the current position in the path and continue to the next position.  
6. If all vertices are included and the last connects to the first, a cycle is found.  
7. If not, backtrack by resetting the current position and trying other vertices.  
8. Print the Hamiltonian cycle if found; otherwise, state that no solution exists.  

## Program:
```
Program to implement to check whether Hamiltonian path exits in the given graph.
Developed by: GANESH PRABHU J
Register Number: 212223220023
```PY
class Graph():
    def __init__(self, vertices):
        self.graph = [[0 for column in range(vertices)]
                            for row in range(vertices)]
        self.V = vertices
    def isSafe(self, v, pos, path):
        if self.graph[ path[pos-1] ][v] == 0:
            return False
        for vertex in path:
            if vertex == v:
                return False
 
        return True
    def hamCycleUtil(self, path, pos):
        if pos==self.V:
            if self.graph[path[pos-1]][path[0]]==1:
                return True
            else:
                return False
        for v in range(1,self.V):
            if self.isSafe(v,pos,path)==True:
                path[pos]=v
                if self.hamCycleUtil(path, pos+1)==True:
                    return True
                path[pos]=-1
        return False
 
    def hamCycle(self):
        path = [-1] * self.V
        path[0] = 0
 
        if self.hamCycleUtil(path,1) == False:
            print ("Solution does not exist\n")
            return False
 
        self.printSolution(path)
        return True
 
    def printSolution(self, path):
        print ("Solution Exists: Following",
                 "is one Hamiltonian Cycle")
        for vertex in path:
            print (vertex, end = " ")
        print (path[0], "\n")
g1 = Graph(5)
g1.graph = [ [0, 1, 0, 1, 0], [1, 0, 1, 1, 1],
            [0, 1, 0, 0, 1,],[1, 1, 0, 0, 1],
            [0, 1, 1, 1, 0], ]
g1.hamCycle();
```
## Output:

![image](https://github.com/user-attachments/assets/a5634ce5-87ac-4f14-bf5c-4e0212a971f9)

## Result:
The Hamiltonian path program executed successfully, and it determined whether a Hamiltonian path exists in the given graph.
