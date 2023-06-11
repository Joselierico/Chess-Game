class ChessGame:
    def __init__(self):
        self.board = self.setup_board()

    def setup_board(self):
        board = [['R', 'N', 'B', 'Q', 'K', 'B', 'N', 'R'],
                 ['P', 'P', 'P', 'P', 'P', 'P', 'P', 'P'],
                 [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
                 [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
                 [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
                 [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
                 ['p', 'p', 'p', 'p', 'p', 'p', 'p', 'p'],
                 ['r', 'n', 'b', 'q', 'k', 'b', 'n', 'r']]
        return board

    def print_board(self):
        for row in self.board:
            print(' '.join(row))

    def is_valid_move(self, from_pos, to_pos):
        # Check if the move is valid according to the rules of chess
        # Implement your validation logic here
        return True

    def make_move(self, from_pos, to_pos):
        if self.is_valid_move(from_pos, to_pos):
            piece = self.board[from_pos[0]][from_pos[1]]
            self.board[from_pos[0]][from_pos[1]] = ' '
            self.board[to_pos[0]][to_pos[1]] = piece
            return True
        else:
            return False

    def play_game(self):
        while True:
            self.print_board()

            # Get user input for the move
            from_pos = input("Enter the position of the piece you want to move (e.g., 'A2'): ")
            to_pos = input("Enter the destination position for the move (e.g., 'A4'): ")

            # Convert user input to board indices
            from_pos = (int(from_pos[1]) - 1, ord(from_pos[0].upper()) - 65)
            to_pos = (int(to_pos[1]) - 1, ord(to_pos[0].upper()) - 65)

            if self.make_move(from_pos, to_pos):
                print("Move successful!")
            else:
                print("Invalid move! Please try again.")

chess_game = ChessGame()
chess_game.play_game()
