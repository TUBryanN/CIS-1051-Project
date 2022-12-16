# CIS-1051-Project
import random

def buildDeck():
    deck = []
    colours = ["Red", "Green", "Yellow", "Blue"]
    values = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, "Draw Two", "Skip", "Reverse"]
    wilds = ["Wild", "Wild Draw Four"]
    
    for colour in colours:
        for value in values:
            cardVal = "{} {}".format(colour, value)
            deck.append(cardVal)
            if value != 0:
                deck.append(cardVal)
    
    for i in range(4):
        deck.append([wilds[0]])
        deck.append(wilds[1])
    
    return deck

def shuffleDeck(deck):
    for cardPos in range(len(deck)):
        randPos = random.randint(0, 107)
        deck[cardPos], deck[randPos] = deck[randPos], deck[cardPos]
    return deck

def drawCards(numCards):
    cardsDrawn = []
    for x in range (numCards):
        cardsDrawn.append(unoDeck.pop(0))
    return cardsDrawn

def showHand(player, playerHand):
    print("{}'s turn".format(player))
    print("Your Hand")
    print("-----------------------------")
    y = 1
    for card in playerHand:
        print("{}) {}".format(y, card))
        y += 1
    print("")

unoDeck = buildDeck()
unoDeck = shuffleDeck(unoDeck)
discards = []

players = [] #List to store player cards
playerNames = [] #List to store player names
colours = ["Blue", "Red", "Green", "Yellow"]
numPlayers = None
print("Enter --help to display the rules of the game\n")

numPlayers = input("How many players? ")
if numPlayers == "--help" or numPlayers == "--resume":
    checkInput(numPlayers)
else:
    numPlayers = int(numPlayers)
    while len(playerNames) < numPlayers:
        tempName = input("Enter player's name: ")
        if tempName == "--help" or tempName == "--resume":
            checkInput(tempName)
        else:
            playerNames.append(tempName)
            players.append(drawCards(5))

print("The cards are:")
for (x,y) in zip(playerNames, players):
    print("Player {} has {}".format(x, y))
print("")
