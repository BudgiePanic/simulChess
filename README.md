# simulChess
Chess variant where both players move at the same time.

# new rules

- Both players move one of their pieces at the same time.
- There is a countdown between moves, giving each player time to think about their next move.
- Piece movement remains unchanged.
- You still cannot castle through check.
- Along with checkmate, scoring a check against the opponent's king results in victory.
- If two pieces move onto the same square at once during a turn, they capture each other.
- If two pieces move through each other during a move, they capture each other and are both removed from the board. (i.e. two rooks moving along a File, two bishops moving along a diagonal.)
- If two pawns attempt to capture each other at the same time, they are both removed from the board.
- Pawns cannot move through each other via forward movement. If two pawns attempt to move onto the same square at once (DECIDE: nothing happens? one player gets priority?)
- If a piece moves off a square that the opponent's piece moves to, nothing happens, provided the pieces didn't move through each other. (i.e. A rook moves off A8 and a bishop moves onto it.)  
- If the king moves off a square that the opponent then attacks, nothing happens.
- Checks can be blocked by moving a piece to intercept an opponents attack.
- If the king moves into a square that is then attacked (or castles through a square that is then attacked), that is a check and that side loses.

- Because both players move at the same time, the concept of flagging no longer makes sense. Time control needs a novel solution.
    - Perhaps the match has a shared time pool. (whole match lasts 10 minutes, each move time is 5,10,20,30 seconds etc etc.) and if no one wins at the end of the timer, some other criteria (like material captured) is used to decide a winner.
    - Perhaps there is no overall timer and the match continues until someo one wins or by mutual agreement.

# why

this idea came from a 'shower thought'.

# System architecture

- An internal model to represent the state of the game
  - enforces the rules
  - applies the logic
  - configurable (custom starting positions)
  - reversable (undo move)
- A server to host the model and communicate with clients
  - extendable
    - custom messages (i.e. award more time, resignation)
- A client to talk to the server, make moves, display the game.
