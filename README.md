import art
word=art.text2art("Welcome to My Game!")
print(word)



import signal


class InputTimedOut(Exception):
    pass


def inputTimeOutHandler(signum, frame):
    raise InputTimedOut


signal.signal(signal.SIGALRM, inputTimeOutHandler)


def input_with_timeout(question , timeout=0  ):
    output = ""
    try:
        print('You have {0} seconds to type in your stuff...'.format(timeout))
        print(question)
        signal.alarm(timeout)
        output = input()
        signal.alarm(0)
    except InputTimedOut:
        pass
    return output

def display_result(points, points_gained, message ):
    points = points + points_gained 
    print(message)
    print("Your score is ", points)
    return points

print("Hi, Welcome to the Jabari Jumps Literacy Game. You will be tested on your vocabulary, reading, grammar, and typing skills and speed.")
name = input("Please Type your name: ")
greeting = "Good  Luck   " + name
word=art.text2art(greeting)
print (word)


validInput = True
score = 0
while validInput == True:
    command = input("Which difficulty would you like to try first? easy, medium, hard, or quit: ")
    if "easy" in command.lower():
        if "no" in command.lower() and EasyQuestionOne == False:
            print()
        print("You are entering easy difficulty! Questions here are worth 1 point. This is where you will be tested on your typing skills and speed. The sentences you type will be sentences from Jabari Jumps. MAKE SURE YOU PUT PERIODS AFTER YOUR SENTENCES!") 
        print()
           
        EasyQuestionOne = input("You see Jabari trying to jump in the pool. Do you want to approach him? (yes/no): ")
        print()
        count = 0
        if "yes" in EasyQuestionOne.lower():
             
            EasyQuestionOne = input_with_timeout("Jabari jumps in a pool and he asks you to type Jabari jumps. Splash!", timeout=10)
            allowed = ['Jabari jumps. Splash!'] 


            if not EasyQuestionOne:
                score = display_result(score, 0,'Jabari did not get an answer.')
            elif EasyQuestionOne not in allowed:
                score = display_result(score, 0, 'Jabari is dissapointed, but wishes you luck next time.')
            else:
                score = display_result(score, 1, 'Jabari is proud of you.')
            print ()
            EasyQuestionTwo = input_with_timeout("Jabari jumps into the water, but he remembers to assign you another task. He wants you to type: Jabari remembered.", timeout=15)
            allowed = ['Jabari remembered.']

            if not EasyQuestionTwo:
                score = display_result(score, 0,'Jabari lost his memory because you took to long to respond.')
            elif EasyQuestionTwo not in allowed:
                score = display_result(score, 0, 'Jabari remembered you were going to be wrong.')
            else:
                score = display_result(score, 1, 'Jabari remembered you were going to be correct.')

            EasyQuestionThree = input_with_timeout("After jumping into the pool many times, Jabari is tired. He wants you to type: I am just a little tired.", timeout=15)
            allowed = ['I am just a little tired.']

            if not EasyQuestionThree:
                score = display_result(score, 0,'Jabari fell asleep waiting for your answer.')
            elif EasyQuestionThree not in allowed:
                score = display_result(score, 0, 'Jabari believes that you are tired and need sleep because you got the answer wrong.')
            else:
                score = display_result(score, 1, 'Jabari is proud of you and is not tired anymore.')

            EasyQuestionFour = input_with_timeout("Proud of taking risks, Jabari wants you to type: I am not scared at all.", timeout = 15)
            allowed = ['I am not scared at all.']
            if not EasyQuestionFour:
                score = display_result(score, 0,'Jabari is wondering why you took so long.')
            elif EasyQuestionFour not in allowed:
                score = display_result(score, 0, 'You scared Jabari for getting the question wrong.')
            else:
                score = display_result(score, 1, 'Jabari is proud of you and believes you are brave.')
            
            EasyQuestionFive = input_with_timeout("Jabari has a surprise for you. However in order to get your surprise you must type: Jabari loves surprises.", timeout = 15)
            allowed = ['Jabari loves surprises.']

            if not EasyQuestionFive:
                score = display_result(score, 0,'You did not answer the question Jabari asked for, so he did not give you your surprise.')
            elif EasyQuestionFive not in allowed:
                score = display_result(score, 0, 'Your surprise is that your answer is wrong and you must retake easy difficulty.')
            else:
                score = display_result(score, 1, 'Your surprise is that YOU HAVE COMPLETED EASY LEVEL!!! Remember you can always return to this difficulty to get a higher score or fix your errors. You have now mastered the art of typing.')
            
    elif "medium" in command.lower():
        print("You are entering medium difficulty! You will be tested on your vocabulary guessing the synonym for the word. The words here are all valuable themes, lessons, and morals from Jabari jumps, that you can use in your real life and future. You can use the google thesaurus for this section! Points here are worth 2 points.")
        print()
        MediumQuestion0ne = input("Jabari is trying to jump off a higher diving board, but he is scared. Do you want to approach him? (yes/no): ")
        print()
        if "yes" in MediumQuestion0ne.lower():
             MediumQuestion0ne = input_with_timeout("I need some motivation to jump by you finding the synonym of the word courage. Can you help motivate me?", timeout=15)
        allowed = ['bravery', 'fearless','heroic','daring']

        if not MediumQuestion0ne:
            score = display_result(score, 0,'Jabari took too long to jump and the lifeguard had to ask him to get down.')
        elif MediumQuestion0ne not in allowed:
            score = display_result(score, 0, 'Jabari sadly climbed down the ladder, maybe he will gain come courage next time.')
        else:
            score = display_result(score, 2, 'Jabari jumped and he had a fun experience, thanking you for the motivation')
       
        MediumQuestionTwo = input_with_timeout("Jabari has tried and tried again eventhough his tries have failed, can you help Jabari succeed by typing a synonym for the word perseverance?", timeout = 20)
        allowed = ['persistence', 'determination', 'never give up',]

        if not MediumQuestionTwo:
            score = display_result(score, 0,'Jabari gave up waiting for your answer.')
        elif MediumQuestionTwo not in allowed:
            score = display_result(score, 0, 'Jabari persevered, but sadly failed. Keep persevering next time!')
        else:
            score = display_result(score, 2, 'Jabari used his perseverance and managed to succeed!')

        MediumQuestionThree = input_with_timeout("Jabari keeps waiting at the ladder of the diving board waiting for his turn. Eventhough the wait is long, Jabari stays in control of himself. Can you help Jabari get his chance on the diving board by typing a synonym for the word patience?", timeout = 20)
        allowed = ['composure', 'calmness', 'endurance', 'tolerance']
        if not MediumQuestionThree:
            score = display_result(score, 0,'Your patience was too long, that you did not even answer the question!')
        elif MediumQuestionThree not in allowed:
            score = display_result(score, 0, 'You were not patient. As punishment Jabari has made your answer wrong.')
        else:
            score = display_result(score, 2, 'Jabari loved how you showed great patience and has made your answer correct!')
        
        MediumQuestionFour = input_with_timeout("Jabari wants some encouragement after showing all these wonderful chracter traits. To encourage him can you type the synonym for the word encouragement?", timeout = 20 )
        allowed = ['inspiration', 'cheering', 'motivation', 'heartening']
        if not MediumQuestionFour:
            score = display_result(score, 0,'You did not answer the question, so you did not get any encouragement from Jabari. Jabari suggests you retake the course again.')
        elif MediumQuestionFour not in allowed:
            score = display_result(score, 0, 'You got the answer wrong, so you did not get any encouragement from Jabari. Jabari suggests you retake Medium Difficulty.')
        else:
            score = display_result(score, 2, 'You got the answer correct and Jabari has encouraged you. YOU HAVE COMPLETED MEDIUM LEVEL! You have now become a word master, Jabari says.Remember you can always return to this difficulty to get a higher score or fix your errors. You have now mastered the art of typing.')

    elif "hard" in command.lower():
        print("You are entering hard difficulty! Reading comphrehension from Jabari Jumps will be tested here. In this difficulty, you can use your Jabari Jumps book when answering the questions. Questions here are 3 points each. ")
        print()
        said_no = True
        while said_no == True:
            HardQuestionOne = input("Jabari is completing a word puzzle, do you want to help him? (yes/no): ")
            print()
            if "yes" in HardQuestionOne.lower():
                said_no = False
        HardQuestionOne = input_with_timeout("Can you help me fill in the blank for this sentence? They looked up at the diving board _ _ _ _ _ _ _ _.", timeout=25)
        allowed = ['together']

        if not HardQuestionOne:
            score = display_result(score, 0,'You and Jabari could not finish the puzzle.')
        elif HardQuestionOne not in allowed:
            score = display_result(score, 0,'You and Jabari answered the puzzle wrong.')
        else:
            score = display_result(score, 3,'You and Jabari answered the puzzle correctly!')
        
        HardQuestionTwo = input_with_timeout("Can you help me fill in the blank for this sentence? Jabari watched the other kids climb the long _ _ _ _ _ _.", timeout=25)
        allowed = ['ladder']

        if not HardQuestionTwo:
            score = display_result(score, 0,'You and Jabari could not finish the puzzle.')
        elif HardQuestionTwo not in allowed:
            score = display_result(score, 0,'You and Jabari answered the puzzle wrong.')
        else:
            score = display_result(score, 3,'You and Jabari answered the puzzle correctly!')
        
        HardQuestionThree = input_with_timeout("Can you help me fill in the blank for this sentence? It's ok to feel a little _ _ _ _ _ _.", timeout = 25)
        allowed = ['scared']

        if not HardQuestionThree:
            score = display_result(score, 0,'You and Jabari could not finish the puzzle.')
        elif HardQuestionThree not in allowed:
            score = display_result(score, 0,'You and Jabari answered the puzzle wrong.')
        else:
            score = display_result(score, 3,'You and Jabari answered the puzzle correctly!') 
        
        HardQuestionFour = input_with_timeout("Can you help me fill in the blank for this sentence? Stretches are _ _ _ _ _ _ _ _ _.", timeout = 25)
        allowed = ['important']
       

        if not HardQuestionFour:
            score = display_result(score, 0,'You and Jabari could not finish the puzzle.')
        elif HardQuestionFour not in allowed:
            score = display_result(score, 0,'You and Jabari answered the puzzle wrong.')
        else:
            score = display_result(score, 3,'You and Jabari answered the puzzle correctly!')
        
        HardQuestionFive = input_with_timeout("Can you help me fill in the blank for this sentence? And then back up! _ _ _ _ _ _!", timeout = 25)
        allowed = ['whoosh']
        if not HardQuestionFive:
            score = display_result(score, 0,'You and Jabari could not finish the puzzle.')
        elif HardQuestionFive not in allowed:
            score = display_result(score, 0,'You and Jabari answered the puzzle wrong.')
        else:
            score = display_result(score, 3,'You and Jabari have whooshed me away with all your smartness!')
        
        HardQuestionSix = input_with_timeout("Can you help me fill in the blank for this sentence? Maybe you should climb down and take a tiny _ _ _ _.", timeout = 25)
        allowed = ['rest']
        if not HardQuestionSix:
            score = display_result(score, 0,'You and Jabari could not finish the puzzle.')
        elif HardQuestionSix not in allowed:
            score = display_result(score, 0,'This was the hardest level and I am glad you were courageous enough to attempt this level. Keep peresevering next time!')
        else:
            score = display_result(score, 3,'You are one courageous and persevering legend to try this level!')
        
        



       

        


    elif "quit" in command.lower():
        print("You are quitting. Your final score is ", score)
        validInput = False
    else: print("Your answer is not valid. Try again.")
