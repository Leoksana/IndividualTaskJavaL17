# IndividualTaskJavaL17

```java
import java.util.Scanner;

public class Main { 
    public static void main(String[] args) {
        System.out.println("Welcome to Tic-Tac-Toe! On the grid we have row 1, 2, 3 and column 1, 2, 3. Please enter the row and column number, for example R1C1. \n");
        char[][] grid = new char[3][3];  
        makeGrid(grid);  
        printGrid(grid);  
        playGame(grid);  
    }

    public static void makeGrid(char[][] grid) {  
        for (int i = 0; i < 3; i++) {  
            for (int j = 0; j < 3; j++) { 
                grid[i][j] = ' '; 
            }
        }
    }

    public static void printGrid(char[][] grid) {  
        for (int i = 0; i < 3; i++) { 
            for (int j = 0; j < 3; j++) { 
                System.out.print(" " + grid[i][j]); 
                if (j < 2) System.out.print(" |"); 
            }
            System.out.println(); 
            if (i < 2) System.out.println("- - - - - -"); 
        }
    }

    public static void playGame(char[][] grid) {  
        Scanner scan = new Scanner(System.in); 
        char player1 = 'X'; 
        char player2 = 'O'; 
        char currentPlayer = player1;  
        int moves = 0; 
        boolean gameWon = false; 

        while (moves < 9 && !gameWon) { 
            System.out.println("\nPlayer " + (currentPlayer == player1 ? "1" : "2") + ", please enter the row and column number, for example R1C1."); 
            String input = scan.nextLine(); 
            int row = input.charAt(1) - '1'; 
            int col = input.charAt(3) - '1'; 

            if (grid[row][col] == ' ') { 
                grid[row][col] = currentPlayer; 
                moves++; 
                printGrid(grid); 
                if (checkWin(grid, currentPlayer)) { 
                    System.out.println("Player " + (currentPlayer == player1 ? "1" : "2") + " wins!"); 
                    gameWon = true;
                } else if (moves == 9) {
                    System.out.println("The game is a draw!"); 
                } else {

                    currentPlayer = (currentPlayer == player1) ? player2 : player1; 
                }
            } else {
                System.out.println("That space is already taken. Please choose another space."); 
            }
        }
        scan.close(); 
    }

    public static boolean checkWin(char[][] grid, char player) { 
        for (int i = 0; i < 3; i++) { 
            if (grid[i][0] == player && grid[i][1] == player && grid[i][2] == player) return true; 
            if (grid[0][i] == player && grid[1][i] == player && grid[2][i] == player) return true; 
        }
        if (grid[0][0] == player && grid[1][1] == player && grid[2][2] == player) return true; 
        if (grid[0][2] == player && grid[1][1] == player && grid[2][0] == player) return true; 

        return false; 
    }
}
```
