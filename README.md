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


