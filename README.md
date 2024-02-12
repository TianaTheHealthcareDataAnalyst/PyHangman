import random

def choose_word():
    words = ["python", "hangman", "programming", "computer", "science", "algorithm"]
    return random.choice(words)

def display_word(word, guessed_letters):
    display = ""
    for letter in word:
        if letter in guessed_letters:
            display += letter
        else:
            display += "_"
    return display

def hangman():
    word_to_guess = choose_word().lower()
    guessed_letters = []
    attempts = 6

    print("Welcome to Hangman!")

    while True:
        current_display = display_word(word_to_guess, guessed_letters)
        print(f"\nWord: {current_display}")
        print(f"Guessed Letters: {', '.join(guessed_letters)}")
        print(f"Attempts left: {attempts}")

        if "_" not in current_display:
            print("Congratulations! You guessed the word.")
            break

        if attempts == 0:
            print(f"Sorry, you ran out of attempts. The word was: {word_to_guess}")
            break

        guess = input("Enter a letter: ").lower()

        if guess.isalpha() and len(guess) == 1:
            if guess in guessed_letters:
                print("You already guessed that letter. Try again.")
            elif guess in word_to_guess:
                print("Good guess!")
            else:
                print("Incorrect guess.")
                attempts -= 1

            guessed_letters.append(guess)
        else:
            print("Please enter a valid single letter.")

if __name__ == "__main__":
    hangman()
