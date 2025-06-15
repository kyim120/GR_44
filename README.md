Absolutely! Let's walk through **every part of the Tic-Tac-Toe C++ program** step by step and explain what each section does.

---

### ✅ **Header and Namespace**

```cpp
#include <iostream>
using namespace std;
```

* `#include <iostream>`: Includes the Input/Output library for using `cin` (input) and `cout` (output).
* `using namespace std;`: So we don’t have to write `std::cout` every time.

---

### ✅ **Class Definition: TicTacToe**

```cpp
class TicTacToe {
private:
    char board[3][3];       // 3x3 grid for the game
    char currentPlayer;     // Tracks whether it's X or O's turn
```

* This is the definition of the `TicTacToe` class.
* It has two **private members**:

  * `board[3][3]`: A 2D array representing the 3x3 game board.
  * `currentPlayer`: A character variable to track who's playing ('X' or 'O').

---

### ✅ **Constructor**

```cpp
public:
    TicTacToe() {
        resetBoard();          // Initialize the board to empty
        currentPlayer = 'X';   // Player X starts first
    }
```

* Constructor runs automatically when a `TicTacToe` object is created.
* It resets the board and sets the first player to 'X'.

---

### ✅ **Reset Board Function**

```cpp
    void resetBoard() {
        for (int i = 0; i < 3; ++i)
            for (int j = 0; j < 3; ++j)
                board[i][j] = ' ';
    }
```

* Clears the board by setting all cells to `' '` (blank).
* Called at the start and every time you replay.

---

### ✅ **Display the Board**

```cpp
    void displayBoard() {
        cout << "\n";
        cout << "  0   1   2\n";
        for (int i = 0; i < 3; ++i) {
            cout << i << " ";
            for (int j = 0; j < 3; ++j) {
                cout << board[i][j];
                if (j < 2) cout << " | ";
            }
            cout << "\n";
            if (i < 2) cout << "  ---------\n";
        }
        cout << "\n";
    }
```

* Prints the current board layout with row and column numbers.
* Uses formatting to make it look like a real Tic-Tac-Toe grid.

---

### ✅ **Make a Move**

```cpp
    bool makeMove(int row, int col) {
        if (row >= 0 && row < 3 && col >= 0 && col < 3 && board[row][col] == ' ') {
            board[row][col] = currentPlayer;
            return true;
        }
        return false;
    }
```

* This function takes a `row` and `col` and places the current player's symbol (`X` or `O`) on the board.
* Checks if the move is valid (within bounds and empty).
* Returns `true` if successful, `false` if not.

---

### ✅ **Check for Win**

```cpp
    bool checkWin() {
        for (int i = 0; i < 3; ++i) {
            if ((board[i][0] == currentPlayer &&
                 board[i][1] == currentPlayer &&
                 board[i][2] == currentPlayer) ||
                (board[0][i] == currentPlayer &&
                 board[1][i] == currentPlayer &&
                 board[2][i] == currentPlayer))
                return true;
        }

        if ((board[0][0] == currentPlayer &&
             board[1][1] == currentPlayer &&
             board[2][2] == currentPlayer) ||
            (board[0][2] == currentPlayer &&
             board[1][1] == currentPlayer &&
             board[2][0] == currentPlayer))
            return true;

        return false;
    }
```

* Checks if the current player has won:

  * Horizontally (rows)
  * Vertically (columns)
  * Diagonally (2 diagonals)
* Returns `true` if a win condition is met.

---

### ✅ **Check for Draw**

```cpp
    bool checkDraw() {
        for (int i = 0; i < 3; ++i)
            for (int j = 0; j < 3; ++j)
                if (board[i][j] == ' ')
                    return false;
        return true;
    }
```

* Checks if the board is full (no empty spaces left).
* If full and no winner: it’s a draw.

---

### ✅ **Switch Player**

```cpp
    void switchPlayer() {
        currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
    }
```

* Switches the turn between `X` and `O`.

---

### ✅ **Get Current Player**

```cpp
    char getCurrentPlayer() {
        return currentPlayer;
    }
};
```

* Returns the symbol of the current player.

---

### ✅ **Main Function**

```cpp
int main() {
    TicTacToe game;
    int row, col;
    char playAgain;
```

* `TicTacToe game;`: Creates an instance of the game.
* Variables `row`, `col` are used for input.
* `playAgain` handles the replay option.

---

### ✅ **Main Game Loop**

```cpp
    do {
        game.resetBoard();
        game.displayBoard();
```

* Game starts fresh every time.

---

### ✅ **Inner Gameplay Loop**

```cpp
        while (true) {
            cout << "Player " << game.getCurrentPlayer() << ", enter row and column (0-2): ";
            cin >> row >> col;

            if (!game.makeMove(row, col)) {
                cout << "Invalid move! Try again.\n";
                continue;
            }

            game.displayBoard();

            if (game.checkWin()) {
                cout << "Player " << game.getCurrentPlayer() << " wins!\n";
                break;
            }

            if (game.checkDraw()) {
                cout << "It's a draw!\n";
                break;
            }

            game.switchPlayer();
        }
```

* Keeps running until there's a win or draw.
* Takes input for the move.
* Makes the move if valid.
* Checks for win/draw.
* Switches player turn.

---

### ✅ **Replay Option**

```cpp
        cout << "Do you want to play again? (y/n): ";
        cin >> playAgain;

    } while (playAgain == 'y' || playAgain == 'Y');

    cout << "Thanks for playing!\n";
    return 0;
}
```

* After each game, asks user if they want to replay.
* Loop continues if they enter `y` or `Y`.

---

### ✅ Summary of Concepts Used:

| Feature         | Used Concept             |
| --------------- | ------------------------ |
| Game logic      | **If-else**, **Loops**   |
| Board state     | **2D arrays**            |
| Players turn    | **Switch logic**         |
| Win/Draw check  | **Conditionals**         |
| Replay system   | **do-while loop**        |
| Encapsulation   | **Classes**              |
| Object-oriented | **Methods inside class** |

---

# **Code**

* 2-player mode
* Win/draw check
* Reset and replay option

---

### ✅ **TicTacToe Game in C++ (OOP)**

```cpp
#include <iostream>
using namespace std;

class TicTacToe {
private:
    char board[3][3];
    char currentPlayer;

public:
    TicTacToe() {
        resetBoard();
        currentPlayer = 'X';
    }

    void resetBoard() {
        for (int i = 0; i < 3; ++i)
            for (int j = 0; j < 3; ++j)
                board[i][j] = ' ';
    }

    void displayBoard() {
        cout << "\n";
        cout << "  0   1   2\n";
        for (int i = 0; i < 3; ++i) {
            cout << i << " ";
            for (int j = 0; j < 3; ++j) {
                cout << board[i][j];
                if (j < 2) cout << " | ";
            }
            cout << "\n";
            if (i < 2) cout << "  ---------\n";
        }
        cout << "\n";
    }

    bool makeMove(int row, int col) {
        if (row >= 0 && row < 3 && col >= 0 && col < 3 && board[row][col] == ' ') {
            board[row][col] = currentPlayer;
            return true;
        }
        return false;
    }

    bool checkWin() {
        // Rows and columns
        for (int i = 0; i < 3; ++i) {
            if ((board[i][0] == currentPlayer &&
                 board[i][1] == currentPlayer &&
                 board[i][2] == currentPlayer) ||
                (board[0][i] == currentPlayer &&
                 board[1][i] == currentPlayer &&
                 board[2][i] == currentPlayer))
                return true;
        }

        // Diagonals
        if ((board[0][0] == currentPlayer &&
             board[1][1] == currentPlayer &&
             board[2][2] == currentPlayer) ||
            (board[0][2] == currentPlayer &&
             board[1][1] == currentPlayer &&
             board[2][0] == currentPlayer))
            return true;

        return false;
    }

    bool checkDraw() {
        for (int i = 0; i < 3; ++i)
            for (int j = 0; j < 3; ++j)
                if (board[i][j] == ' ')
                    return false;
        return true;
    }

    void switchPlayer() {
        currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
    }

    char getCurrentPlayer() {
        return currentPlayer;
    }
};

int main() {
    TicTacToe game;
    int row, col;
    char playAgain;

    do {
        game.resetBoard();
        game.displayBoard();

        while (true) {
            cout << "Player " << game.getCurrentPlayer() << ", enter row and column (0-2): ";
            cin >> row >> col;

            if (!game.makeMove(row, col)) {
                cout << "Invalid move! Try again.\n";
                continue;
            }

            game.displayBoard();

            if (game.checkWin()) {
                cout << "Player " << game.getCurrentPlayer() << " wins!\n";
                break;
            }

            if (game.checkDraw()) {
                cout << "It's a draw!\n";
                break;
            }

            game.switchPlayer();
        }

        cout << "Do you want to play again? (y/n): ";
        cin >> playAgain;

    } while (playAgain == 'y' || playAgain == 'Y');

    cout << "Thanks for playing!\n";
    return 0;
}
```

---

### 🔧 **How to Run:**

1. Save as `TicTacToe.cpp`
2. Compile:
