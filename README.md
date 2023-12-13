# assignment1
char[,] board = new char[3, 3];
for (int row = 0; row < 3; row++)
{
    for (int col = 0; col < 3; col++)
    {
        board[row, col] = ' ';
    }
}
char currentPlayer = 'X';
bool gameOver = false;

while (!gameOver)
{
    // Display the current state of the board
    DisplayBoard(board);

    // Ask the user for their move
    Console.WriteLine($"Player {currentPlayer}, enter your move (row column):");
    int row = int.Parse(Console.ReadLine());
    int col = int.Parse(Console.ReadLine());

    // Check if the move is valid
    if (IsValidMove(board, row, col))
    {
        // Place the symbol on the board
        board[row, col] = currentPlayer;

        // Check if the board is filled
        if (IsBoardFilled(board))
        {
            gameOver = true;
            Console.WriteLine("Game over!");
        }
        else
        {
            // Switch to the next player
            currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
        }
    }
    else
    {
        Console.WriteLine("Invalid move! Please try again.");
    }
}
static void DisplayBoard(char[,] board)
{
    for (int row = 0; row < 3; row++)
    {
        for (int col = 0; col < 3; col++)
        {
            Console.Write(board[row, col]);
        }
        Console.WriteLine();
    }
}
static bool IsValidMove(char[,] board, int row, int col)
{
    if (row >= 0 && row < 3 && col >= 0 && col < 3 && board[row, col] == ' ')
    {
        return true;
    }
    return false;
}
static bool IsBoardFilled(char[,] board)
{
    for (int row = 0; row < 3; row++)
    {
        for (int col = 0; col < 3; col++)
        {
            if (board[row, col] == ' ')
            {
                return false;
            }
        }
    }
    return true;
}

