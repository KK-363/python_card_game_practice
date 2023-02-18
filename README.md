⦁	This python practice project is a card game that has two players.

⦁	It uses a list for a deck of cards that has card values of 1-10, "Jacks", "Queens" and "Kings"

⦁	It has two classes, one for the players(Player) and one for the logic of the game(Game).

⦁	I have two while loops, one inside the other, that run the game play.  The outer loop loops until the game is over and the inner loop loops through a round of the game.

Game Objective:
To be the first player with a 1 card board that has a face up 1 on it (This player wins the game).  Player's start with a board of 10 cards and to get that number decreased, must win rounds in the game.  To win a round a player must be the first to get their board filled with cards who's values match the place they are placed on a player's board (a 4 would be placed at the 4th place on a player's board, a 7 would be placed at the 7th place on a player's board).  

Game Rules:
Both player's get dealt a facedown board of cards (this consists of 10 cards to start with)
A player starts their turn by either drawing from the card deck, or the discard pile
If a player draws a King or Queen their turn is over
If a player draws a Jack they can place it anywhere on their board they wish that does not already have a face up card.
If a player draws a number that is not face up on their board yet and is less then the length of their current board, they can play that card at its cooresponding value on their board.  
When a card is placed on a player's board the face down card at that place is turned over and is the card "in play" and follows the same steps as if it were a drawn card.

Coding:
I started with the card deck and functions to deal the players face down board and one to make the representation of the board that would be shown, using a list that was filled with "*" to represent a face down card. When I had that working I wrote a function to display a player's shown board and then the function to run the game logic.  

After that I was able to write supporting functions, like one to check if the discarded card should be used, and to change which player's turn is was and to see where a Jack would get placed.
I had pretty much all the functions I ended up using written before I switched over to using classes, but I was having trouble being able to keep all the variables I needed the same inside and outside of functions.   I wanted to use functions because they are a lot more organized and reusable.  

By using classes I was able to, a lot more easily, keep track of who the current player was, what each of their boards held, the deck of cards, and the one that had been the hardest one for me to figure out, how to keep track of the discarded card. (Class instance variables can be very useful!)
Changing over to classes wasn't a completely smooth process.  I did have to change some functions and how I was coding some of my game logic, like when it checked if a round was over, and how it knew who the current (active) player was.

My favorite part of all my coding in this game, is the what_cards_in_play function which recursively calls itself, as long as it's the same players turn.  Because you are doing the same 4 things, 
	seeing if the round is over 
 
	(1) seeing if the card is a King or Queen 
 
	(2) seeing if the card is a Jack

	(3) seeing if the card is playable . . . 
 
	(4) or not.
 
This function is really the core of this game.

I learned a lot about functions, classes and how they interact.  About loops and how to control them to get the result I want and about how helpful classes can be when you have a lot of things that need to interact with each other. 

Steps  for Game Logic:

Step 1:  Shuffle cards 

Step 2:  Deal players boards (need to know what the player's  current board length is.)

Step 3:  Draw from deck or discard pile (ask current player which pile to draw from)

Step 4:   Use card "in play" according to game's rules. 

	Step 4.1: If card in play is a "King" or a "Queen"
		Current player's turn is over 
		return current player's board
		goto to Step 3

	Step 4.2 If card in play is a "Jack"
		ask player where on their board they want to place it
		check if current player's board is now complete (all cards showing/positions filled)
			if current player's board is filled and board length is greater than 1 
				round is over, go back to start of Step 1
				if current player's board is equal to 1 and completely filled
				Game is over: show which player won
		if current player's board is not completely filled, turn over the card that was at the position the current  player choose to put the "Jack" (this card is now -> in play)
		return current player's board
		goto to start of Step 4

	Step 4.3  If card in play is a number

		Step 4.3.1  if card in play is already showing on player's board or card is greater than the current player's board length
			discard the card
			current player's turn is over
			return current player's board
			goto Step 3

		Step 4.3.2  if card in play is not already showing on player's board, place card on current player's  board at position of card's value
			check if player's board is complete (all cards showing/completely filled)
				if current player's board is filled and board length is greater	than 1 
				round is over, go back to start of Step 1
				if current player's board is equal to 1 and completely filled
				Game is over: show which player won
			if players board is not complete turn over card that was at the position of card's value on players  board (this card is now -> in play)
			go to start of Step 4

