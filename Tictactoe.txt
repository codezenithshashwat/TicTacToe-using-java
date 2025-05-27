import java.util.*;

public class Tictactoe {
    public static void display(int[][] display){
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
        if (display[i][j] == 0) {
            System.out.print("- ");
        } else if (display[i][j] == 1) {
            System.out.print("X ");  
        } else if (display[i][j] == 2) {
            System.out.print("O ");  
        }
    }
    System.out.println();  
}
    }
    public static boolean check(int[][] tictactoe) {
        // null checking

        // row check
        if (tictactoe[0][0] != 0) {
            if (tictactoe[0][0] == tictactoe[0][1] && tictactoe[0][1] == tictactoe[0][2]) {
                return true;
            }
        }
        if (tictactoe[1][0] != 0) {
            if (tictactoe[1][0] == tictactoe[1][1] && tictactoe[1][1] == tictactoe[1][2]) {
                return true;
            }
        }
        if (tictactoe[2][0] != 0) {
            if (tictactoe[2][0] == tictactoe[2][1] && tictactoe[2][1] == tictactoe[2][2]) {
                return true;
            }
        }
        // column check
        if (tictactoe[0][0] != 0) {
            if (tictactoe[0][0] == tictactoe[1][0] && tictactoe[1][0] == tictactoe[2][0]) {
                return true;
            }
        }

        if (tictactoe[0][1] != 0) {
            if (tictactoe[0][1] == tictactoe[1][1] && tictactoe[1][1] == tictactoe[2][1]) {
                return true;
            }
        }

        if (tictactoe[0][2] != 0) {
            if (tictactoe[0][2] == tictactoe[1][2] && tictactoe[1][2] == tictactoe[2][2]) {
                return true;
            }
        }
        // diagonal check
        if (tictactoe[0][0] != 0) {
            if (tictactoe[0][0] == tictactoe[1][1] && tictactoe[1][1] == tictactoe[2][2]) {
                return true;
            }
        }
        if (tictactoe[0][2] != 0) {
            if (tictactoe[0][2] == tictactoe[1][1] && tictactoe[1][1] == tictactoe[2][0]) {
                return true;
            }
        }

        return false;
    }

    public static void main(String[] args) {
        int[][] display= new int[3][3];
        int[][] tictactoe = new int[3][3];
        int player1 = 1;
        int player2 = 2;
        display(display);

        // considering player 1 will start with the firsg move
        int lastmove = 1;
        int count=1;
        while (!check(tictactoe) && count<=9) {
            Scanner sc = new Scanner(System.in);
            System.out.println("Player" + " " + lastmove + " " + "Enter the value of R");
            int R = sc.nextInt();
            System.out.println("Player" + " " + lastmove + " " + "Enter the value of C");
            int C = sc.nextInt();
            count++;
            if (R > 2 || R < 0 || C > 2 || C < 0) {
                System.out.println("Enter valid values of R and C (between 0 and 2)");
                continue;
            }
            if (lastmove == 1) {
                tictactoe[R][C] = 1;
                display[R][C]=1;
                display(display);
            } else {
                tictactoe[R][C] = 2;
                 display[R][C]=2;
                 display(display);
            }
            if (lastmove == 1) {
                lastmove = 2;
            } else {
                lastmove = 1;
            }

        }


        if (check(tictactoe)) {
            if (lastmove == 1) {
                System.out.println("Player 2 won");
            } else {
                System.out.println("Player 1 won");
            }
        } else {
            System.out.println("it's a tie");
        }
    }
}