#Ben Walz
#FP2-S01 External Files
#Oct 13
#this code make and takes game data and will be able to load diffrent iterations of a game
# external files work good for my code because they can save the data and have it be used at another time 
# in my case the code keeps track of wins and loses had by the user and then at the end it will save these vaules onto a text file
# and the same win and lose values can be continued
# my code is a easy demenstrarion but the tool are there for it to be a more complex save data system or save any data needed 
# to be used again and a again
#




#imports
import random




#funtions
def newdata():
    global save_name
    save_name = input("What do you want to name your save? ") #makes a custom file name
    save_name = save_name + '.txt' # adds .txt to make it a text file
    global W #globals the wins and loses to be used by the diceroler()
    global L
    W = 0 #asigns values to wins and loses
    L = 0
    
    
            
            
            
            
def loaddata():
   global save_name
   print("What is the name of the save, has to be the exact name. ") # asks for previous save
   save_name = input("> ") # saves input
   save_name = save_name + '.txt' # makes it a txt file
   save = open(save_name, 'r') #opens file in read mode 
   read = save.read() # takes the information from save and applys them to read
   read = read.split(',') # takes the , out and makes a list
   global W # globals W and L
   global L
   
   W = int(read.pop(0)) # makes W and L = what position 0 in the list and makes that a integer
   L = int(read.pop(0))
   print("You have", W, "Wins and", L, "loses") #tells how many wins and loses they have on this save

   
   
   
   
   
def diceroller():
    global L # globals W and L
    global W
    go = True #makes  the loop continue
    print("""
guess if it's heads or tails. Write '1' for heads or '2' for tails 
Type 'done' when finished
""") # gives information in what to do
    while go == True: # loops 
        
        roll = random.randint(1,2) # assigns a random int to roll
        guess = input("> ") # takes your guess 
        if guess == 'done' or guess == 'Done': # Checks if the guess == done then would print how many w and l and close 
            go = False
            print("You won", W, "times and lost", L, "times")
            save = open(save_name, 'w')
            
            W = str(W)# makes w and l str not a int and writes them in the text file
            L = str(L)
            save.write(W)
            save.write(",")
            save.write(L)
        
        
        else: 
            guess = int(guess)
            if guess == roll:
                print("You guessed right!") # checks if your guess was incorrect or not and then adds a w or a l 
                W = W + 1
            elif guess != roll:
                print("You guessed wrong!")
                L = L + 1
            
    
    
   
   
   
   
def main():
    print("Do you want to start a new game or load? New, load? ") # asks to load or start new
    answear = input("> ")
    if answear == 'new' or answear == 'New': # if you want new it runs new func then diceroller
        newdata()
        diceroller()
    elif answear == 'load' or answear == 'Load':  #if you want to load it runs load func then roller
        loaddata()
        diceroller()


#main code
main() # main code runs it all
            

   
        
