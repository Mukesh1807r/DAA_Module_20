# EX 2D BACKTRACKING - GRAPH COLORING PROBLEM
## DATE:19:04:2025

# Graph Coloring Problem

## Aim
To solve the graph coloring problem using backtracking. The goal is to assign colors to vertices in a graph such that no two adjacent vertices have the same color, using at most `m` colors.

## Algorithm
1. Define a helper function `is_safe(v, color, c)` to check if it is safe to color vertex `v` with color `c`:
   - Check if any adjacent vertex has the same color.
2. Define a recursive function `graph_coloring_util(m, color, v)`:
   - Try assigning colors from 1 to `m` for vertex `v`.
   - If assigning a color leads to a valid solution, recursively attempt to color the next vertex.
   - If a solution is found, return `True`. If not, backtrack and try a different color.
3. Define the main function `graph_coloring(m)` to initiate the coloring process and return the result.
4. Print the color assigned to each vertex if a solution exists, otherwise print that no solution is possible.

## Program
```python
class Graph:
    def __init__(self, vertices):
        self.v = vertices
        self.graph = [[0] * vertices for _ in range(vertices)]

    def is_safe(self, v, color, c):
        for i in range(self.v):
            if self.graph[v][i] == 1 and color[i] == c:
                return False
        return True

    def graph_coloring_util(self, m, color, v):
        if v == self.v:
            return True
        for c in range(1, m + 1):
            if self.is_safe(v, color, c):
                color[v] = c
                if self.graph_coloring_util(m, color, v + 1):
                    return True
                color[v] = 0
        return False

    def graph_coloring(self, m):
        color = [0] * self.v
        if not self.graph_coloring_util(m, color, 0):
            return False
        return color

g = Graph(4)
g.graph = [[0, 1, 1, 1], [1, 0, 1, 0], [1, 1, 0, 1], [1, 0, 1, 0]]

m = 3

result = g.graph_coloring(m)

if result:
    print("Solution Exists: Following are the assigned colors")
    for i, c in enumerate(result, start=1):
        print(f"Vertex {i}  is given color:  {c}")
else:
    print("Solution does not exist")
```
## Output 
![image](https://github.com/user-attachments/assets/f52f218c-1939-40f3-90c8-26c5a8b46063)

## Result 
The program successfully solves the graph coloring problem and assigns colors to the vertices in such a way that no two adjacent vertices have the same color. It prints the color assigned to each vertex, or reports that no solution exists if it's not possible to color the graph with the given number of colors.
