# EX 3C Sudoku Solver
## DATE:17-07-2025
## AIM:
To write a python program to find the solution of sudoku puzzle using Backtracking.


## Algorithm

1. Start by scanning the Sudoku board to find the first empty cell (value 0).  
2. For that empty cell, try placing values from 1 to 9 one by one.  
3. For each value, check if it is valid in the current row, column, and 3x3 subgrid (`isPossible`).  
4. If the value is valid, place it temporarily in the cell.  
5. Recursively attempt to solve the rest of the board with this new placement.  
6. If a solution is not found, backtrack by resetting the cell to 0.  
7. Repeat the process for all empty cells.  
8. Once the board is completely filled without violations, print the solved board.


## Program:
```

Program to implement to to find the solution of sudoku puzzle using Backtracking.
Developed by: GANESH PRABHU J
Register Number: 212223220023

```
```PY
board = [
    [0, 0, 0, 8, 0, 0, 4, 0, 3],
    [2, 0, 0, 0, 0, 4, 8, 9, 0],
    [0, 9, 0, 0, 0, 0, 0, 0, 2],
    [0, 0, 0, 0, 2, 9, 0, 1, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 7, 0, 6, 5, 0, 0, 0, 0],
    [9, 0, 0, 0, 0, 0, 0, 8, 0],
    [0, 6, 2, 7, 0, 0, 0, 0, 1],
    [4, 0, 3, 0, 0, 6, 0, 0, 0]
]

def printBoard(board):
    for i in range(0, 9):
        for j in range(0, 9):
            print(board[i][j], end=" ")
        print()

def isPossible(board, row, col, val):
    for j in range(0, 9):
        if board[row][j] == val:
            return False

    for i in range(0, 9):
        if board[i][col] == val:
            return False

    startRow = (row // 3) * 3
    startCol = (col // 3) * 3
    for i in range(0, 3):
        for j in range(0, 3):
            if board[startRow+i][startCol+j] == val:
                return False
    return True

def solve():
    for i in range(0,9):
        for j in range(0,9):
            if board[i][j]==0:
                for val in range(1,10):
                    if isPossible(board,i,j,val):
                        board[i][j]=val
                        solve()
                        board[i][j]=0
                return 
    printBoard(board)
    
solve()
```
## Output:

![image](https://github.com/user-attachments/assets/5befbbec-d268-47fb-a468-391035de7b10)

## Result:
The Sudoku solver program executed successfully and found the solution for the given puzzle.
