import random
import time

# Initialize the high score with a large number
high_score = 0
start_time = time.time()  # Start the timer
for i in range(1000000):
  pass


def game():

    print('''Welcome to the Number Guessing Game!
    I'm thinking of a number between 1 and 100.

    Please select the difficulty level:
    1. Easy (10 chances)
    2. Medium (5 chances)
    3. Hard (3 chances)''')

    selection = int(input("Enter number: "))
    number = random.randint(1, 100)

    if selection == 1:
        play_game(number, 10)
    elif selection == 2:
        play_game(number, 5)
    elif selection == 3:
        play_game(number, 3)
    else:
        print("Invalid selection")

def play_game(number, attempts):
    global high_score
    print(f"Great! You have selected a difficulty level with {attempts} chances.")
    for i in range(attempts):
        guess = int(input("Enter your guess: "))
        if guess == number:
            print(f"Congratulations! You guessed the correct number in {i+1} attempts.")
            if i + 1 > high_score:
                high_score = i + 1
                print(f"New high score: {high_score} attempts!")
            break
        elif guess < number:
            print(f"Incorrect! The number is greater than {guess}.")
        else:
            print(f"Incorrect! The number is less than {guess}.")
    else:
        print(f"Sorry! You've used all your {attempts} chances. The correct number was {number}.")

    print(f"Current high score: {high_score} attempts")

    reply = input("Do you want to continue playing? yes/no: ")
    if reply.lower() == "yes":
        game()
    else:
        print("Thank you for playing!")
        end_time = time.time()  # Stop the timer
        elapsed_time = end_time - start_time
        print(f"Elapsed time: {elapsed_time:.2f} seconds")

game()
