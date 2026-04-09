#include <iostream>
using namespace std;

int main()
{
    
    char board[3][3] = { {'1','2','3'},
                         {'4','5','6'},
                         {'7','8','9'} };

    int choice;
    char player = 'A';  // Player 1 symbol
    int moves = 0;
    bool win = false;
    int menu;

    
    cout << "===== TIC TAC TOE GAME =====" << endl;
    cout << "=== By Anaqshay Jamshaid ===" << endl;
    cout << "1. Start Game" << endl;
    cout << "2. Exit" << endl;
    cout << "Enter choice: ";
    cin >> menu;

    if(menu == 2)
        return 0;

    cout << "Player 1 = A" << endl;
    cout << "Player 2 = J" << endl;
    cout << "Choose box number from 1 to 9" << endl;

   
    while(win == false && moves < 9)
    {
        cout << endl;

        
        for(int i=0;i<3;i++)
        {
            for(int j=0;j<3;j++)
            {
                cout << " " << board[i][j] << " ";
                if(j<2) cout << "|";
            }
            cout << endl;
            if(i<2) cout << "---|---|---" << endl;
        }

        cout << endl;

        
        cout << "Player " << player << ", enter box number: ";
        cin >> choice;

        
        int row = (choice - 1) / 3;
        int col = (choice - 1) % 3;

        // checking if the move is valid
        if(choice >= 1 && choice <= 9 &&
           board[row][col] != 'A' &&
           board[row][col] != 'J')
        {
            board[row][col] = player;
            moves++;
        }
        else
        {
            cout << "Invalid move! Box already filled or wrong number." << endl;
            continue;
        }

        // check all win conditions
        if ((board[0][0] == board[0][1] && board[0][1] == board[0][2]) ||
            (board[1][0] == board[1][1] && board[1][1] == board[1][2]) ||
            (board[2][0] == board[2][1] && board[2][1] == board[2][2]) ||

            (board[0][0] == board[1][0] && board[1][0] == board[2][0]) ||
            (board[0][1] == board[1][1] && board[1][1] == board[2][1]) ||
            (board[0][2] == board[1][2] && board[1][2] == board[2][2]) ||

            (board[0][0] == board[1][1] && board[1][1] == board[2][2]) ||
            (board[0][2] == board[1][1] && board[1][1] == board[2][0]))
        {
            win = true;
        }
        else
        {
            // switching player
            if(player == 'A')
                player = 'J';
            else
                player = 'A';
        }
    }

    // And the final board display
    cout << endl << "Final Board:" << endl;
    for(int i=0;i<3;i++)
    {
        for(int j=0;j<3;j++)
        {
            cout << " " << board[i][j] << " ";
            if(j<2) cout << "|";
        }
        cout << endl;
        if(i<2) cout << "---|---|---" << endl;
    }

    cout << endl;

    // Who won is shown
    if(win == true)
        cout << "Player " << player << " wins the game!" << endl;
    else
        cout << "Game is a draw!" << endl;

    return 0;
}
