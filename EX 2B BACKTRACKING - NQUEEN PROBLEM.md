# EX 2B BACKTRACKING - NQUEEN PROBLEM
## DATE:12:04:2025
# N-Queens Problem

## Aim
To solve the N-Queens problem using backtracking, where the goal is to place N queens on an NxN chessboard such that no two queens attack each other.

## Algorithm
1. Define a function `isSafe(board, row, col)` to check if it is safe to place a queen at `board[row][col]`.
   - Check if there is a queen on the same row.
   - Check if there is a queen on the upper and lower diagonals.
2. Define a function `solveNQUtil(board, col)` to solve the problem recursively:
   - Try placing a queen in each row of the current column.
   - If placing the queen leads to a valid solution, recurse to the next column.
   - If a solution is found, return `True`; otherwise, backtrack by removing the queen.
3. Define the main function `solveNQ()` to initialize the board and call the recursive solver.
4. Print the solution board if a solution is found.

## Program
```python
global N
N = int(input())

def printSolution(board):
    for i in range(N):
        for j in range(N):
            print(board[i][j], end=" ")
        print()

def isSafe(board, row, col):
    # Check this row on left side
    for i in range(col):
        if board[row][i] == 1:
            return False

    # Check upper diagonal on left side
    for i, j in zip(range(row, -1, -1), range(col, -1, -1)):
        if board[i][j] == 1:
            return False

    # Check lower diagonal on left side
    for i, j in zip(range(row, N, 1), range(col, -1, -1)):
        if board[i][j] == 1:
            return False

    return True

def solveNQUtil(board, col):
    if col >= N:
        return True
    for i in range(N):
        if isSafe(board, i, col):
            board[i][col] = 1

            if solveNQUtil(board, col + 1):
                return True

            board[i][col] = 0
    return False

def solveNQ():
    if N < 1 or N > N:
        print("Solution does not exist")
        return False

    board = [[0 for _ in range(N)] for _ in range(N)]

    if not solveNQUtil(board, 0):
        print("Solution does not exist")
        return False

    printSolution(board)
    return True

# Driver Code
solveNQ()
```
## Output 
![image](https://github.com/user-attachments/assets/5c85b043-0d0b-4fc6-95e4-3affdee03c58)

## Result 
The Python program successfully solves the N-Queens problem by placing N queens on an NxN board such that no two queens attack each other, and prints the solution in the form of a chessboard.
