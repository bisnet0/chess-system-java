# Chess Game in Java ♟️

This is a Chess game implemented in Java. It includes the core board game structure, chess-specific rules, and functionalities for piece movement and game management. Below is an overview of the main classes and their responsibilities.

---

## **Project Structure**

- `boardgame` package:
  - **`Board`**: Represents the chessboard and manages pieces.
  - **`Piece`**: Abstract class for a generic piece.
  - **`Position`**: Represents a position on the board.

- `chess` package:
  - **`ChessMatch`**: Manages the chess game, including turns, moves, and game state.
  - **`ChessPiece`**: Abstract class for a chess-specific piece.
  - **`ChessPosition`**: Converts between chess notation (e.g., `a1`) and internal board positions.
  - **`Color`**: Enum for piece colors (WHITE/BLACK).

---

## **Classes Overview**

### **`Board`**
Manages the chessboard and its pieces.

- **Attributes**:
  - `rows`, `columns`: Dimensions of the board.
  - `pieces`: 2D array to store pieces.

- **Methods**:
  - `placePiece(Piece piece, Position position)`: Places a piece on the board.
  - `removePiece(Position position)`: Removes a piece from a position.
  - `positionExists(int row, int column)`: Validates a position on the board.

---

### **`Piece`**
Abstract representation of a board piece.

- **Attributes**:
  - `position`: Current position of the piece.
  - `board`: Reference to the board.

- **Methods**:
  - `possibleMoves()`: Abstract method for valid moves.
  - `possibleMove(Position position)`: Checks if a move to a specific position is possible.
  - `isThereAnyPossibleMove()`: Validates if the piece has at least one valid move.

---

### **`Position`**
Represents a position on the board.

- **Attributes**:
  - `row`, `column`: Coordinates of the position.

- **Methods**:
  - `setValues(int row, int column)`: Updates position coordinates.
  - `toString()`: String representation (`row, column`).

---

### **`ChessMatch`**
Main class for managing the chess game.

- **Attributes**:
  - `board`: Instance of `Board`.
  - `turn`, `currentPlayer`: Track game progress and active player.
  - `pieceOnTheBoard`, `capturedPieces`: Lists for pieces.

- **Methods**:
  - `getPieces()`: Returns the current state of the board.
  - `performChessMove(ChessPosition source, ChessPosition target)`: Executes a move and validates its legality.
  - `testCheck(Color color)`: Tests if a player is in check.
  - `initialSetup()`: Sets up the initial configuration of the chessboard.

---

### **`ChessPiece`**
Abstract class extending `Piece` for chess-specific functionality.

- **Attributes**:
  - `color`: Color of the piece.

- **Methods**:
  - `isThereOpponentPiece(Position position)`: Checks if an opponent's piece is at a position.

---

### **`ChessPosition`**
Handles chess notation for positions.

- **Attributes**:
  - `column`, `row`: Chess notation (e.g., `a1`).

- **Methods**:
  - `toPosition()`: Converts to a `Position`.
  - `fromPosition(Position position)`: Converts a `Position` to chess notation.
  - `toString()`: Chess notation representation.

---

### **`Color`**
Enumeration for piece colors.

- Values:
  - `BLACK`
  - `WHITE`

---

## **Highlights**
- **Board Validation**: Ensures all positions and moves are valid.
- **Abstract Moves**: Allows specific piece behaviors (e.g., `King`, `Rook`).
- **Check Detection**: Validates if a move places a player in check.
- **Chess Notation**: Converts between internal representation and user-friendly notation.

---

## **Usage**
1. Create a `ChessMatch` instance.
2. Use `performChessMove` to make moves.
3. Retrieve board state with `getPieces`.
4. Implement additional rules (e.g., checkmate) for a full chess experience.
