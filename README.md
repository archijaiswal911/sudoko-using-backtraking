

```java
import java.util.*;

public class SudokuSolver {
    private static final int N = 9;

    // print grid
    static void printGrid(int[][] grid) {
        for (int r = 0; r < N; r++) {
            for (int c = 0; c < N; c++) {
                System.out.print(grid[r][c] + " ");
            }
            System.out.println();
        }
    }

    // check if num can be placed at grid[row][col]
    static boolean isSafe(int[][] grid, int row, int col, int num) {
        // check row
        for (int d = 0; d < N; d++) {
            if (grid[row][d] == num) return false;
        }
        // check column
        for (int r = 0; r < N; r++) {
            if (grid[r][col] == num) return false;
        }
        // check 3x3 box
        int boxRowStart = row - row % 3;
        int boxColStart = col - col % 3;
        for (int r = boxRowStart; r < boxRowStart + 3; r++) {
            for (int c = boxColStart; c < boxColStart + 3; c++) {
                if (grid[r][c] == num) return false;
            }
        }
        return true;
    }

    // find next empty cell, return boolean; row & col returned via array
    static boolean findEmpty(int[][] grid, int[] pos) {
        for (int r = 0; r < N; r++) {
            for (int c = 0; c < N; c++) {
                if (grid[r][c] == 0) {
                    pos[0] = r;
                    pos[1] = c;
                    return true;
                }
            }
        }
        return false;
    }

    // backtracking solver
    static boolean solveSudoku(int[][] grid) {
        int[] pos = new int[2];
        if (!findEmpty(grid, pos)) return true; // no empty -> solved

        int row = pos[0];
        int col = pos[1];

        for (int num = 1; num <= 9; num++) {
            if (isSafe(grid, row, col, num)) {
                grid[row][col] = num;
                if (solveSudoku(grid)) return true;
                grid[row][col] = 0; // backtrack
            }
        }
        return false; // trigger backtracking
    }

    public static void main(String[] args) {
        // Sample puzzle: 0 represents empty cells
        int[][] board = {
            {5,3,0, 0,7,0, 0,0,0},
            {6,0,0, 1,9,5, 0,0,0},
            {0,9,8, 0,0,0, 0,6,0},

            {8,0,0, 0,6,0, 0,0,3},
            {4,0,0, 8,0,3, 0,0,1},
            {7,0,0, 0,2,0, 0,0,6},

            {0,6,0, 0,0,0, 2,8,0},
            {0,0,0, 4,1,9, 0,0,5},
            {0,0,0, 0,8,0, 0,7,9}
        };

        System.out.println("Input puzzle (0 = empty):");
        printGrid(board);
        System.out.println();

        boolean solved = solveSudoku(board);
        if (solved) {
            System.out.println("Solved puzzle:");
            printGrid(board);
        } else {
            System.out.println("No solution exists for the given puzzle.");
        }

        // --- Optional: Accept custom puzzle from user ---
        // Uncomment below to allow console input of 81 numbers.
        /*
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter 81 numbers (0 for empty) row-wise:");
        int[][] userGrid = new int[9][9];
        for (int i=0;i<9;i++) for(int j=0;j<9;j++) userGrid[i][j] = sc.nextInt();
        if (solveSudoku(userGrid)) {
            System.out.println("Solution:");
            printGrid(userGrid);
        } else {
            System.out.println("No solution.");
        }
        sc.close();
        */
    }
}

