# codealpha_hangman game 
python
import random

# List of predefined words
words = ["python", "apple", "tiger", "chair", "robot"]

# Choose a random word
word = random.choice(words)

# Store guessed letters
guessed_letters = []

# Number of incorrect guesses allowed
attempts = 6

print("🎮 Welcome to Hangman!")

# Game loop
while attempts > 0:

    # Display the word
    display_word = ""

    for letter in word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "

    print("\nWord:", display_word)

    # Check if player guessed the full word
    if "_" not in display_word:
        print("\n🎉 Congratulations! You guessed the word:", word)
        break

    print("Guessed letters:", " ".join(guessed_letters))

    guess = input("Guess a letter: ").lower()

    # Validate input
    if len(guess) != 1 or not guess.isalpha():
        print("⚠ Please enter only ONE alphabet letter.")
        continue

 
    if guess in guessed_letters:
        print("⚠ You already guessed that letter.")
        continue

    guessed_letters.append(guess)

    # Check guess
    if guess in word:
        print("✅ Correct guess!")
    else:
        attempts -= 1
        print("❌ Wrong guess!")
        print("Attempts left:", attempts)

if attempts == 0:
    print("\n💀 Game Over!")
    print("The word was:", word)
