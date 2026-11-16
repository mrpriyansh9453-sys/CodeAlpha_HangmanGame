# CodeAlpha_HangmanGame


import random

# List of 5 predefined words
words = ["python", "computer", "program", "coding", "developer"]

# Computer selects a random word
word = random.choice(words)

# Display hidden word
guessed_word = ["_"] * len(word)

# Maximum incorrect attempts
attempts = 6

guessed_letters = []

print("================================")
print("       WELCOME TO HANGMAN")
print("================================")

while attempts > 0 and "_" in guessed_word:

    print("\nWord:", " ".join(guessed_word))
    print("Incorrect attempts left:", attempts)

    guess = input("Guess a letter: ").lower()

    # Check input
    if len(guess) != 1 or not guess.isalpha():
        print("Please enter a single letter!")
        continue

    if guess in guessed_letters:
        print("You already guessed this letter!")
        continue

    guessed_letters.append(guess)

    # Check whether letter is correct
    if guess in word:
        print("Correct guess!")

        for i in range(len(word)):
            if word[i] == guess:
                guessed_word[i] = guess

    else:
        print("Wrong guess!")
        attempts -= 1

# Final result
if "_" not in guessed_word:
    print("\nCongratulations! You won!")
    print("The word was:", word)
else:
    print("\nGame Over!")
    print("The correct word was:", word)
