---
layout: post
title: Tic Tac Toe
---

17:49 - Just finished building Tic Tac Toe in Ruby.  It was... more of a struggle than I anticipated, partly because I had a head swimming with best practices that seemed to get in the way of just making the darn thing work.  Also, thinking in an Object-oriented way rather than procedural is interesting because it's not super linear, so I think this was a great exercise for me.

I just wanted to save my notes somewhere:

classses:

Game is made up of board and players
board is made of
  rows (3) 1-3 with
    spaces (3)          look like this: "[ #{filling} ]"
      at different positions A-C, 1-3.  Can be X, O, or Empty (start empty)
players (2) take turns placing an X or an O into spaces
winning combinations
the game is over when one of the players gets 3 in a row (8 possible configurations)

gameplay:

Player 1 is X's

Player 2 is O's

Show Board:

    A    B    C
  ---------------
1 [   ][   ][   ]
  ---------------
2 [   ][   ][   ]
  ---------------
3 [   ][   ][   ]
  ---------------

Player 1 pick a space:  "B2"

    A    B    C
  ---------------
1 [   ][   ][   ]
  ---------------
2 [   ][ X ][   ]
  ---------------
3 [   ][   ][   ]
  ---------------

players continue picking spaces until either all spaces are taken or a winning combination is played
