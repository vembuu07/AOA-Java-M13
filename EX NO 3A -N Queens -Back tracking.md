
# EX 3A N Queens Problem - Backtracking Approach.

## AIM:
To Write a Java program for N queens using backtracking approach.
You are given an integer N. For a given N x N chessboard, find a way to place 'N' queens such that no queen can attack any other queen on the chessboard.
A queen can be attacked when it lies in the same row, column, or the same diagonal as any of the other queens. You have to print one such configuration.
Chess Board
<img width="241" height="209" alt="image" src="https://github.com/user-attachments/assets/96aacb61-4f34-423f-b324-5e34454e42b8" />


Note :

Get the input from the user for N . The value of N must be from 1 to 4

If solution exists Print a binary matrix as output that has 1s for the cells where queens are placed

If there is no solution to the problem  print  "Solution does not exist"

## Algorithm
1.Start and read the value of N (chessboard size).

2.Place queens column by column using recursion.

3.Check if the current position is safe (no queen in row, upper-left, or lower-left diagonal).

4.If safe, place the queen and recursively place the rest; if not, backtrack.

5.Print the board if all queens are placed, else display “No solution exists.”   

## Program:
```

import java.util.Scanner;

public class NQueens {
    static int N;

    
    static void printSolution(int[][] board) {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }

    
    static boolean isSafe(int[][] board, int row, int col) {
        // Check left side of current row
        for (int i = 0; i < col; i++)
            if (board[row][i] == 1)
                return false;

       
        for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 1)
                return false;

        
        for (int i = row, j = col; i < N && j >= 0; i++, j--)
            if (board[i][j] == 1)
                return false;

        return true;
    }

    // Recursive utility function to solve N-Queens
    static boolean solveNQUtil(int[][] board, int col) {
        //Add your code Here
        if(col>=N)
        {
            return true;
        }
        for(int i=0;i<N;i++)
        {
            if(isSafe(board,i,col))
            {
                board[i][col]=1;
                if(solveNQUtil(board,col+1))
                {
                    return true;
                }
                board[i][col]=0;
            }
        }
        return false;
    }

    
    static boolean solveNQ() {
        int[][] board = new int[N][N];

        if (!solveNQUtil(board, 0)) {
            System.out.println("Solution does not exist");
            return false;
        }

        printSolution(board);
        return true;
    }

   
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        N = scanner.nextInt(); // Accept board size
        solveNQ();
    }
}

```

## Output:

<img width="618" height="256" alt="image" src="https://github.com/user-attachments/assets/3f470b8d-bf9c-487e-8478-2a12b2c9581a" />


## Result:
The program successfully implemented and the ouput is verified. 
