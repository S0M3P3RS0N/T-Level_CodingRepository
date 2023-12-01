# T-Level_CodingRepository

Welcome to my portfolio, this will look at the python projects that i have created this year:

## Mastermind
Code for my mastermind game:
```python
import random

### FUNCTIONS AREA ###

def CodeMakerGenerator():
    FirstDig = str(random.randint(0,9))
    SecondDig = str(random.randint(0,9))
    ThirdDig = str(random.randint(0,9))
    FourthDig = str(random.randint(0,9))
    FinalCode = FirstDig + SecondDig + ThirdDig + FourthDig
    return FinalCode

def Game(CodeMakerCode, UserGuess):
    CorrectNumbers = 0
    CorrectPosition = 0
    for i in range(len(UserGuess)):
        if CodeMakerCode[i] == UserGuess[i]:
            CorrectPosition += 1
        if CodeMakerCode[i] in UserGuess:
            CorrectNumbers += 1
    return CorrectNumbers, CorrectPosition

def UserReplayResponse():
    replay = True
    while replay == True:
        strUserInput = input("Would you like to play again [Y/N]: ")
        if strUserInput.upper() == "Y":
            replay == False
            ReturnedValue = 1
            break
        elif strUserInput.upper() == "N":
            print("Goodbye")
            replay = False
            ReturnedValue = 0
            break
        else:
            print("Incorrect please input either [Y/N]")
    return ReturnedValue

### MAIN AREA ###
play = True
intCorrectNumbers = 0
intCorrectPosition = 0
strUserGuess = 0

print("Welcome to Mastermind have fun!!!")

while play == True:
    Guesses = 0
    try:
        if UserResponse == 1:
            pass
        elif UserResponse == 0:
            break
    except:
        UserResponse = 1
    Code = CodeMakerGenerator()
    while Code != strUserGuess:
        strUserGuess = input("Guess the 4 digit code the Code Master has created: ")
        if strUserGuess.isdigit() == True and len(strUserGuess) == 4:
            intCorrectNumbers, intCorrectPosition = Game(Code, strUserGuess)
        else:
            continue
        if intCorrectPosition == 4:
            print("Well done you guessed the correct code")
            UserResponse = UserReplayResponse()
            if UserResponse == 1:
                continue
            elif UserResponse == 0:
                break
        else:
            print("You had", intCorrectNumbers,"Correct Numbers and", intCorrectPosition,"numbers in the correct position.")
            Guesses += 1
            if Guesses == 10:
                print("You have ran out of guesses\nThe code was",Code)
                UserResponse = UserReplayResponse()
                if UserResponse == 1:
                    continue
                elif UserResponse == 0:
                    break
```