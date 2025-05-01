# EX 2A BACKTRACKING - RAT IN MAZE PROBLEM
## DATE:

## Aim
To solve the Rat in a Maze problem using Backtracking. The goal is to find a path from the top-left corner (0, 0) to the bottom-right corner (N-1, N-1) of a maze, moving only through cells that contain a 1 (path), and avoiding cells with 0 (blocked).

## Algorithm
1. Define a function `isSafe(x, y, maze, N)` to check if the cell (x, y) is within bounds and is not blocked.
2. Define a helper function `solveMazeUtil()` that:
   - Marks the current cell as part of the solution path.
   - Recursively tries to move right or down.
   - Backtracks if no valid path is found.
3. Define the main function `solveMaze()` that initializes the solution matrix and calls the utility function to find a solution.
4. Print the solution matrix if a path exists, otherwise display a message indicating no solution.

## Program
```python
def printSolution(sol):
    for i in sol:
        for j in i:
            print(str(j) + " ", end ="")
        print("")

def isSafe(maze, x, y, N):
    return x >= 0 and x < N and y >= 0 and y < N and maze[x][y] == 1

def solveMaze(maze, N):
    sol = [[0 for _ in range(N)] for _ in range(N)]

    if solveMazeUtil(maze, 0, 0, sol, N) == False:
        print("Solution doesn't exist")
        return False

    printSolution(sol)
    return True

def solveMazeUtil(maze, x, y, sol, N):
    if x == N - 1 and y == N - 1:
        sol[x][y] = 1
        return True

    if isSafe(maze, x, y, N):
        sol[x][y] = 1

        if solveMazeUtil(maze, x, y + 1, sol, N):
            return True

        if solveMazeUtil(maze, x + 1, y, sol, N):
            return True

        sol[x][y] = 0
        return False

    return False

if __name__ == "__main__":
    maze = [ 
        [1, 0, 0, 0],
        [1, 1, 0, 1],
        [0, 1, 0, 0],
        [1, 1, 1, 1]
    ]
    
    N = 4  
    solveMaze(maze, N)
```
## Output 
![image](https://github.com/user-attachments/assets/1d937ca7-19d2-427c-b813-e0d98ac4c0fc)

## Result 

The Python program successfully solves the Rat in a Maze problem and prints the path taken by the rat (represented by 1's) from the top-left corner to the bottom-right corner.

