import random

bank= ["cat","by"]
word= random.choice(bank)
gameover= False
wordlen= len(word)
display = []
bank = []

print(f"The word is {word}.")

for pos in range(wordlen):
    display+="🤔"

lives = 5

while not gameover:
    print(f"🏦 {bank}")
    print(f"🧍‍♂️:{lives}")
    print(f"{display}\n")
    guess= input("Pick a letter: ")

    if guess not in word:
        bank += guess
        lives -= 1
        print("❌ Letter not found.\n")
        if lives == 0:
            gameover = True
            print(f"You have no more lives! The word was '{word}'. Game Over!")
    else:
        for pos2 in range(wordlen):
            letters = word[pos2]
            if guess == letters:
                bank+= guess
                display[pos2] = letters
                correctletters= "".join(display)
                if correctletters == word:
                    gameover = True
                    print(f"🥳 The word is '{word}'. YOU WIN!")
