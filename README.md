import random

# List of preferred words that the players need to guess
word_list = ["banana", "naruto", "boruto", "superman", "batman"]

word_to_guess= random.choice(word_list)
def initialize():
    display_word = "_" * len(word_to_guess)  # Initialize display_word with underscores
    attempts_left = 5

    return word_to_guess, display_word, attempts_left

def main():
    print("Welcome to Hangman")
    word_to_guess, display_word, attempts_left = initialize()

  while attempts_left > 0:
        print(f"Word: {display_word}")
        print(f"Attempts left = {attempts_left}")

        # Receive player guess
  guess = input("Your guess is: ").lower()

  if guess in word_to_guess:
            print("Congrats, you are correct")
            new_display_word = ""
            attempts_left=attempts_left-1
            for i in range(len(word_to_guess)):
                if word_to_guess[i] == guess:
                    new_display_word += guess
                else:
                    new_display_word += display_word[i]
            display_word = new_display_word

  if display_word == word_to_guess:
                print(f"Congrats! You guessed the word: {word_to_guess}")
                break
        else:
            attempts_left -= 1
            print(f"Sorry, {guess} is not in the word. You have {attempts_left} attempts left.")

 if attempts_left == 0:
        print(f"Sorry, you lose the game. The word was: {word_to_guess}")

if __name__ == "__main__":
    main()
