# CODSOFT
TASKS
//Simple Calculator
#include <iostream>
using namespace std;
int main() {
    int num1, num2;
    char operation;
    cout << "Simple Calculator" << endl;
    cout << "Enter two numbers: ";
    cin >> num1 >> num2;
    cout << "Enter the operation (+, -, *, /, %): ";
    cin >> operation;
    switch (operation) {
        case '+':
            cout << "Result: " << num1 + num2 << endl;
            break;
        case '-':
            cout << "Result: " << num1 - num2 << endl;
            break;
        case '*':
            cout << "Result: " << num1 * num2 << endl;
            break;
        case '/':
            if (num2 != 0) {
                cout << "Result: " << num1 / num2 << endl;
            } else {
                cout << "Error: Division by zero!" << endl;
            }
            break;
        case '%':
            cout<<"Result: "<<num1 % num2<<endl;
            break;
        default:
            cout << "Invalid operation!" << endl;
            break;
    }
    return 0;
}

// Number guessing game 
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;
int main() {
    int number, guess;
    int tries = 0;
    srand(static_cast<unsigned int>(time(0)));
    number = rand() % 100 + 1;
    cout << "Welcome to the Number Guessing Game!" << endl;
    cout << "I have generated a number between 1 and 100." << endl;
    cout << "Can you guess what it is?" << endl;
    do {
        cout << "Enter your guess: ";
        cin >> guess;
        tries++;
        if (guess > number) {
            cout << "Too high!" << endl;
        } else if (guess < number) {
            cout << "Too low!" << endl;
        } else {
            cout << "Congratulations! You've guessed the number in " << tries << " tries." << endl;
        }
    } while (guess != number);
    return 0;
}

//Tic-Tac-Toe Game
#include <iostream>
using namespace std;
const int SIZE = 3;
char board[SIZE][SIZE];
char currentPlayer = 'X';
void initializeBoard() {
    for (int i = 0; i < SIZE; ++i) {
        for (int j = 0; j < SIZE; ++j) {
            board[i][j] = '1' + i * SIZE + j;
        }
    }
}
void displayBoard() {
    cout << "Current board state:" << endl;
    for (int i = 0; i < SIZE; ++i) {
        for (int j = 0; j < SIZE; ++j) {
            cout << board[i][j];
            if (j < SIZE - 1) cout << " | ";
        }
        cout << endl;
        if (i < SIZE - 1) cout << "--|---|--" << endl;
    }
}
bool isWinner() {
    for (int i = 0; i < SIZE; ++i) {
        if (board[i][0] == board[i][1] && board[i][1] == board[i][2]) return true;
    }
    for (int j = 0; j < SIZE; ++j) {
        if (board[0][j] == board[1][j] && board[1][j] == board[2][j]) return true;
    }
    if (board[0][0] == board[1][1] && board[1][1] == board[2][2]) return true;
    if (board[0][2] == board[1][1] && board[1][1] == board[2][0]) return true;
    return false;
}
bool isDraw() {
    for (int i = 0; i < SIZE; ++i) {
        for (int j = 0; j < SIZE; ++j) {
            if (board[i][j] != 'X' && board[i][j] != 'O') return false;
        }
    }
    return true;
}
void switchPlayer() {
    currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
}
void playGame() {
    int choice;
    bool gameWon = false;
    bool gameDraw = false;
    while (!gameWon && !gameDraw) {
        displayBoard();
        cout << "Player " << currentPlayer << ", enter your move (1-9): ";
        cin >> choice;
        int row = (choice - 1) / SIZE;
        int col = (choice - 1) % SIZE;
        if (board[row][col] != 'X' && board[row][col] != 'O') {
            board[row][col] = currentPlayer;
            gameWon = isWinner();
            gameDraw = isDraw();
            if (!gameWon && !gameDraw) {
                switchPlayer();
            }
        } else {
            cout << "Invalid move! Try again." << endl;
        }
    }
    displayBoard();
    if (gameWon) {
        cout << "Congratulations! Player " << currentPlayer << " wins!" << endl;
    } else if (gameDraw) {
        cout << "It's a draw!" << endl;
    }
}
int main() {
    char playAgain = 'Y';
    do {
        initializeBoard();
        playGame();
        cout << "Do you want to play again? (Y/N): ";
        cin >> playAgain;
    } while (playAgain == 'Y' || playAgain == 'y');
    return 0;
}

