# Hangman_Game_Project
import random

class Hangman:
    def Perform(self):
        answerlist = ["pigeon", "peacock", "crow", "parrot", "swan","goose","sparrow","kingfisher"]

        random.shuffle(answerlist)

        answer = list(answerlist[0])

        # print("The answer is :",answer)
        # empty list called display
        display = []
        # this will contain the used letters
        used = []

        # adds the variable answer to display
        display.extend(answer)
        # adds what is in display ie the answer to used
        # so we can take letters out
        used.extend(display)

        # print(display)
        # print(used)
        for i in range(len(display)):
            # replace each index in the list with '_'
            display[i] = "_"
        print("This is a bird name please try to guess: ")

        # the join command puts a space between each '_'
        print(' '.join(display))
        print()

        count = 0
        chance = 5
        f = chance
        temp = []
        # keep asking the user until all letters guessed
        while count < len(answer):
            guess = input("please guess a letter(s) in the word : ")
            guess = guess.lower()
            # print("You have completed ",count+1," Gusse(s)")

            for i in range(len(answer)):
                # if the guessed letter maches a letter
                # in the answer
                if answer[i] == guess:
                    # replace the index of the guess with
                    # The actual letter they guessed
                    display[i] = guess

                    count = count + 1
                    temp.append(guess)
                    # print("printing the temp ",temp)
                    # print(answer)

                    # print(used)
                    used.remove(guess)

                    print("You have guessed: ", count, "correct letters.")
                    # print out the new string with the guessed letters in
                    print(' '.join(display))

                if temp == answer:
                    print()
                    print("Well done, you guess the word")

            if guess not in answer:
                f -= 1
                print("Sorry, wrong guess")
                print("You have still :", f, " Gusses")

            if f == 0:
                print("Sorry you have lost: ")
                print("Better luk next time: ")
                break


obj1 = Hangman()
obj1.Perform()
