```cs
# крестики нолики

using System;

namespace TicTacToeGame
{
    class Program
    {
        static char[,] board = InitializeBoard();
        static int turns = 0;

        static void Main(string[] args)
        {
            char currentPlayer = 'X';
            bool gameEnded = false;

            while (!gameEnded)
            {
                DrawBoard();
                PlayerMove(currentPlayer);

                if (CheckWin(currentPlayer))
                {
                    DrawBoard();
                    Console.WriteLine($"\nПоздравляем! Игрок '{currentPlayer}' победил!");
                    gameEnded = true;
                }
                else if (turns == 9)
                {
                    DrawBoard();
                    Console.WriteLine("\nНичья! Места на поле закончились.");
                    gameEnded = true;
                }
                else
                {
                    currentPlayer = currentPlayer == 'X' ? 'O' : 'X';
                }
            }
        }

        static char[,] InitializeBoard()
        {
            return new char[,]{
                { '1', '2', '3' },
                { '4', '5', '6' },
                { '7', '8', '9' }
            };
        }

        static void DrawBoard()
        {
            Console.Clear();
            Console.WriteLine("Крестики-Нолики");
            Console.WriteLine("-------------------------------------");
            for (int i = 0; i < 3; i++)
            {
                Console.Write(" ");
                for (int j = 0; j < 3; j++)
                {
                    Console.Write($" {board[i,j]} ");
                    if (j < 2) Console.Write("|");
                }
                Console.WriteLine();
                if (i < 2) Console.WriteLine("---|---|---");
            }
            Console.WriteLine("-------------------------------------");
        }

        static void PlayerMove(char playerSymbol)
        {
            bool validMove = false;

            while (!validMove)
            {
                Console.Write($"\nХод игрока '{playerSymbol}'. Введите номер клетки (1-9): ");
                string input = Console.ReadLine();

                if (int.TryParse(input, out int cell) && cell >= 1 && cell <= 9)
                {
                    int row = (cell - 1) / 3;
                    int col = (cell - 1) % 3;

                    if (board[row, col] != 'X' && board[row, col] != 'O')
                    {
                        board[row, col] = playerSymbol;
                        turns++;
                        validMove = true;
                    }
                    else
                    {
                        Console.WriteLine("Ошибка: Эта клетка уже занята!");
                    }
                }
                else
                {
                    Console.WriteLine("Ошибка: Введите корректное число от 1 до 9!");
                }
            }
        }

        static bool CheckWin(char playerSymbol)
        {
            // Проверка по горизонтали и вертикали
            for (int i = 0; i < 3; i++)
            {
                if (board[i,0] == playerSymbol && board[i,1] == playerSymbol && board[i,2] == playerSymbol)
                    return true;
                if (board[0,i] == playerSymbol && board[1,i] == playerSymbol && board[2,i] == playerSymbol)
                    return true;
            }

            // Проверка по диагоналям
            if (board[0,0] == playerSymbol && board[1,1] == playerSymbol && board[2,2] == playerSymbol)
                return true;
            if (board[0,2] == playerSymbol && board[1,1] == playerSymbol && board[2,0] == playerSymbol)
                return true;

            return false;
        }
    }
}
```
