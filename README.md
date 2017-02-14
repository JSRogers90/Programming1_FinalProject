# Programming1_FinalProject

The goal for this project was to create a program that allowed a user to play blackjack in the console.

Psuedocode for assignment:
1.	Main
1.1.	Declare variables and objects
1.1.1.	String Array playDeck
1.1.2.	String rules
1.1.3.	String cont
1.1.4.	String Array List playerHand
1.1.5.	Integer playerValue
1.1.6.	String Array List dealerHand
1.1.7.	Integer dealerValue
1.1.8.	Integer deckPos
1.1.9.	String hitStay
1.1.10.	Boolean bust, initialized false
1.1.11.	Boolean containsAce, initialized false
1.1.12.	Scanner keyboard, as system input Scanner
1.2.	Display “BLACKJACK” and simple game objective
1.3.	Display “Would you like to view the rules?”
1.4.	Store keyboard input as rules
1.5.	Check if rules equals “yes”
1.5.1.	Run showRules
1.6.	Else begin do/while
1.6.1.	Set playDeck as return from shuffleDeck
1.6.2.	Set deckPos equal 0
1.6.3.	Add playDeck[deckPos] to playerHand
1.6.4.	Increment deckPos
1.6.5.	Add playDeck[deckPos] to dealerHand
1.6.6.	Increment deckPos
1.6.7.	Repeat 1.6.3 – 1.6.6
1.6.8.	Set playerValue as return from handValue(playerHand)
1.6.9.	Set dealerValue as return from handValue(dealerHand)
1.6.10.	Check if player has blackjack and dealer does not
1.6.10.1.	Run displayPlayerHand(playerHand, playerValue)
1.6.10.2.	Run displayDealerHand(dealerHand,dealerValue)
1.6.10.3.	Display Blackjack win message
1.6.11.	Else check if player has blackjack and dealer does too
1.6.11.1.	Run displayPlayerHand and displayDealerHand
1.6.11.2.	Display push message
1.6.12.	Else
1.6.12.1.	Run displayPlayerHand and displayShows(dealerHand)
1.6.12.2.	Display “Hit or Stay?”
1.6.12.3.	Store keyboard input as hitStay
1.6.12.4.	While hitStay equals “hit”
1.6.12.4.1.	Add playDeck[deckPos] to playerHand, set playerValue and increment deckPos
1.6.12.4.2.	Check if playerValue <= 21
1.6.12.4.2.1.	Display playerHand and displayShows
1.6.12.4.2.2.	Display “Hit or Stay?”
1.6.12.4.2.3.	Store input as hitStay
1.6.12.4.3.	Else
1.6.12.4.3.1.	Set bust equal true and hitStay equal “bust”
1.6.12.5.	If bust true
1.6.12.5.1.	Run displayPlayerHand and displayDealerHand
1.6.12.5.2.	Display bust lose message
1.6.12.5.3.	Set bust equal false
1.6.12.6.	Else
1.6.12.6.1.	Run displayPlayerHand and displayDealerHand
1.6.12.6.2.	While dealerValue < 18
1.6.12.6.2.1.	Check if dealerHand contains an ace
1.6.12.6.2.1.1.	Set containsAce = true
1.6.12.6.2.2.	Check if containsAce true and dealerValue equal 17
1.6.12.6.2.2.1.	Add playDeck[deckPos] to dealerHand, set dealerValue, and increment deckPos
1.6.12.6.2.2.2.	Run displayPlayerHand and displayDealerHand
1.6.12.6.2.3.	Else if dealerValue < 17
1.6.12.6.2.3.1.	Add playDeck[deckPos] to dealerHand, set dealerValue, and increment deckPos
1.6.12.6.2.3.2.	Run displayPlayerHnad and display DealerHand
1.6.12.6.2.4.	Else exit while
1.6.12.6.3.	Check if player wins
1.6.12.6.3.1.	Display win message
1.6.12.6.4.	Else if playerValue = dealerValue
1.6.12.6.4.1.	Display push message
1.6.12.6.5.	Else
1.6.12.6.5.1.	Display lose message
1.6.13.	Display “Do you want to play again?”
1.6.14.	Store keyboard input as cont
1.6.15.	Check if cont is “yes”
1.6.15.1.	Run clearHand on playerHand and dealerHand
1.6.16.	Check if cont is “yes” for while loop
1.7.	End main
2.	Public void showRules
2.1.	Displays rules
3.	Public integer array shuffleOrder
3.1.	Declare variables and objects
3.1.1.	Final integer deckSize = 52
3.1.2.	Integer array shuffleOrder
3.1.3.	Integer s
3.1.4.	Integer hold
3.1.5.	Random rand
3.2.	For(s=0, s<deckSize)
3.2.1.	Set hold = rand nextint(deckSize)+1
3.2.2.	For(int h=0, h<=s)
3.2.2.1.	If hold = shuffleOrder[s]
3.2.2.1.1.	Set hold = rand nextint(deckSize)+1
3.2.2.1.2.	Set h = -1
3.2.3.	Set shuffleOrder[s] = hold
3.3.	Return shuffleOrder
4.	Public string array shuffleDeck
4.1.	Declare variable and objects
4.1.1.	Final integer deckSize = 52
4.1.2.	String array deck, initialized with cards from standard 52 card deck
4.1.3.	Integer array deckIndex
4.1.4.	String array shuffleDeck
4.2.	Set deckIndex as return from shuffleOrder
4.3.	For(int d = 0, d<deckSize)
4.3.1.	Set shuffleDeck[d] = deck[deckIndex[d]-1]
4.4.	Return shuffleDeck
5.	Public string array clearHand input string array list hand
5.1.	Integer count = hand.size
5.2.	For(int Index = 0, Index < count)
5.2.1.	hand.remove[0]
5.3.	return hand
6.	Public void displayPlayerHand input string array list hand and integer value
6.1.	For(int Index = 0, Index<hand.size)
6.1.1.	Display hand.get[Index]
6.2.	Display value
7.	Public void displayShows input string array list hand
7.1.	Display hand.get[0]
8.	Public void displayDealerHand input string array list hand and integer value
8.1.	For(int Index = 0, Index<hand.size)
8.1.1.	Display hand.get[Index]
8.2.	Display value
9.	Public integer handValue input string array list hand
9.1.	Declare variables and objects
9.1.1.	String card
9.1.2.	Integer cardValue
9.1.3.	Integer handValue, initialize as 0
9.1.4.	Boolean containsAce, initialize as false
9.2.	For(int Index = 0, Index<hand.size)
9.2.1.	Set card = hand.get[Index]
9.2.2.	Check if card is king, queen, jack or 10
9.2.2.1.	Set cardValue = 10
9.2.3.	Check if card is 9
9.2.3.1.	Set cardValue = 9
9.2.4.	Check if card is and set cardValue for 8-2 as with 9
9.2.5.	Check if card is ace
9.2.5.1.	Set containsAce = true
9.2.6.	Set handValue += cardValue
9.3.	If contains Ace is true
9.3.1.	If (handValue + 11) <= 21
9.3.1.1.	handValue += 11
9.3.2.	else
9.3.2.1.	handValue += 1
