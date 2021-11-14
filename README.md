# FP2-S01-External-Files
#takes previous wins and losses and continues to add 


#Ben Walz
#FP2-S01 External Files
#Oct 13
#this code make and takes game data and will be able to load diffrent iterations of a game

import random




#funtions
def newdata():
    global save_name
    save_name = input("What do you want to name your save? ")
    save_name = save_name + '.txt'
    save = open(save_name, 'w')
    
    
            
            
            
            
def loaddata():
   global save_name
   save_name = input("What is the name of the save, has to be the exact name. ")
   save_name = save_name + '.txt'
   save = open(save_name, 'r')
   read = save.read()
   read = read.split(',')
   W = int(read.pop(0))
   L = int(read.pop(0))
   print(W)
   print(L)

   
   
   
   
   
def diceroller():

    go = True
   
    while go == True:
        
        roll = random.randint(1,6)
        guess = input("guess what the dice rolled. Type 'done' when finished ")
        if guess == 'done' or guess == 'Done':
            go = False
            print("You won", W, "times and lost", L, "times")
            save = open(save_name, 'w')
            
            W = str(W)
            L = str(L)
            save.write(W)
            save.write(",")
            save.write(L)
        else:
            guess = int(guess)
            if guess == roll:
                print("You guessed right!")
                W = W + 1
            elif guess != roll:
                print("You guess wrong!")
                L = L + 1
            
    
    
   
   
   
   
def main():
    print("Do you want to start a new game or load? New, load? ")
    answear = input("> ")
    if answear == 'new' or answear == 'New':
        newdata()
        diceroller()
    elif answear == 'load' or answear == 'Load':
        loaddata()
        diceroller()



main()
            

   
        
