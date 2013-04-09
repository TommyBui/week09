week09
======







import java.util.Scanner;

import javax.swing.JOptionPane;

 

public class TicTacToeV1

{

 //=============== start the game ===============================

//================= Set up ====================================

    public static char pos1, pos2, pos3, pos4, pos5, pos6, pos7, pos8, pos9;

    public static String sBoard;

    public static String retString;

    public static int userMove, compMove;

    public static int moves;

 //================ determine user move and check if position is availabe (not taken) ===================

    public static boolean nextMove (int move, char symbol)

    {

        if (move == 1)

        {

            if (pos1 != '1')

                return false;

 

            pos1 = symbol;

            return true;

        }

 

        else if (move == 2)

        {

            if (pos2 != '2')

                return false;

 

            pos2 = symbol;

            return true;

        }

 

        else if (move == 3)

        {

            if (pos3 != '3')

                return false;

 

            pos3 = symbol;

            return true;

        }

 

        else if (move == 4)

        {

            if (pos4 != '4')

                return false;

 

            pos4 = symbol;

            return true;

        }

 

 

        else if (move == 5)

        {

            if (pos5 != '5')

                return false;

 

            pos5 = symbol;

            return true;

        }

 

 

        else if (move == 6)

        {

            if (pos6 != '6')

                return false;

 

            pos6 = symbol;

            return true;

        }

 

        else if (move == 7)

        {

            if (pos7 != '7')

                return false;

 

            pos7 = symbol;

            return true;

        }

 

        else if (move == 8)

        {

            if (pos8 != '8')

                return false;

 

 

            pos8 = symbol;

            return true;

        }

 

        else if (move == 9)

        {

            if (pos9 != '9')

                return false;

 

            pos9 = symbol;

            return true;

        }

 

        return false;

    }

 //================= Determine computer move (random) and check if it is not taken position ===================

    public static int randomMove(int pos)

    {

        int temp = pos;

        if (pos1 == '1')

        {

            temp--;

            if (temp == 0)

                return pos1 - '0';

        }

 

        if (pos2 == '2')

        {

            temp--;

            if (temp == 0)

                return pos2 - '0';

        }

 

        if (pos3 == '3')

        {

            temp--;

            if (temp == 0)

                return pos3 - '0';

        }

 

        if (pos4 == '4')

        {

            temp--;

            if (temp == 0)

                return pos4 - '0';

        }

 

        if (pos5 == '5')

        {

            temp--;

            if (temp == 0)

                return pos5 - '0';

        }

 

        if (pos6 == '6')

        {

            temp--;

            if (temp == 0)

                return pos6 - '0';

        }

 

        if (pos7 == '7')

        {

            temp--;

            if (temp == 0)

                return pos7 - '0';

        }

 

        if (pos8 == '8')

        {

            temp--;

            if (temp == 0)

                return pos8 - '0';

        }

 

        if (pos9 == '9')

        {

            temp--;

            if (temp == 0)

                return pos9 - '0';

        }

 

        return 0;

    }

 //=============== Set up the game board =============================

    public static String getBoard()

    {

        return "_" + pos1 + "_" + "|" + "_" + pos2 + "_" + "|" + "_" + pos3 + "_\n" +

               "_" + pos4 + "_" + "|" + "_" + pos5 + "_" + "|" + "_" + pos6 + "_\n" +

               "_" + pos7 + "_" + "|" + "_" + pos8 + "_" + "|" + "_" + pos9 + "_\n";

    }

 //========================Check winning combination ( horizontal, vertical, diagonal)=====================

    public static boolean won()

    {

        if (pos1 == pos2 && pos2 == pos3)

            return true;

 

        if (pos4 == pos5 && pos5 == pos6)

            return true;

 

        if (pos7 == pos8 && pos8 == pos9)

            return true;

 

        if (pos1 == pos4 && pos4 == pos7)

            return true;

 

       if  (pos2 == pos5 && pos5 == pos8)

           return true;

 

        if (pos3 == pos6 && pos6 == pos9)

            return true;

 

        if (pos1 == pos5 && pos5 == pos9)

            return true;

 

        if (pos3 == pos5 && pos5 == pos7)

            return true;

 

        return false;

    }

 //=================== Main process==============================

    public static void main(String[] args)

    {

        Scanner input = new Scanner( System.in );

 

        boolean bPlaying = true;

        boolean inValidInput;

 

        // initialize board

        pos1 = '1';

        pos2 = '2';

        pos3 = '3';

        pos4 = '4';

        pos5 = '5';

        pos6 = '6';

        pos7 = '7';

        pos8 = '8';

        pos9 = '9';

        moves = 0;

      JOptionPane.showMessageDialog( null,  "Welcome to tictactoe game\n" + "You will play against computer\n" + "Your move will be 'X' and computer will be 'O'\n" + "You will make a move first");

 

        do

        {

            // human

            do

            {

                inValidInput = true;

                sBoard = getBoard() + "Enter 1-9 to make your move";

                retString = JOptionPane.showInputDialog(null, sBoard);

                if (retString.length() != 1 || retString.charAt(0) > '9' || retString.charAt(0) < '0')

                {

                    JOptionPane.showMessageDialog(null, "Invalid inputs. Please try again");

                    continue;

                }

                userMove = retString.charAt(0) - '0';

                if (nextMove(userMove, 'X'))

                    inValidInput = false;

                else

                    JOptionPane.showMessageDialog(null, "Sorry this number already taken. Please try again");

            }

            while (inValidInput = false);

            moves++;

            if (won())

            {

                sBoard = getBoard() +  "Congratulation. You have won the game!";

                JOptionPane.showMessageDialog(null, sBoard);

                bPlaying = false;

            }

            else if (moves == 9)

            {

                sBoard = getBoard() +  "You have drawn the game!!";

                JOptionPane.showMessageDialog(null, sBoard);

            }

 

            if (!bPlaying)

                break;

 

            // computer

            compMove = 1 + (int) ( Math.random() * (9-moves));

            if (nextMove(randomMove(compMove), 'O'))

            {

                moves++;

                if (won())

                {

                    sBoard = getBoard() +  "Sorry. You have lost the game!";

                    JOptionPane.showMessageDialog(null, sBoard);

                    bPlaying = false;

                }

                else if (moves == 9)

                {

                    sBoard = getBoard() +  "You have drawn the game!!";

                    JOptionPane.showMessageDialog(null, sBoard);

                    bPlaying = false;

                }

            }

            else

            {

                sBoard = getBoard() +  "Error!!! invalid move! " + compMove + " " + randomMove(compMove);

                JOptionPane.showMessageDialog(null, sBoard);

            }

 

        }

        while (bPlaying);

 

    }

}


