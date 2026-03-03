# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [x] Describe the game's purpose.

The game allows a user to guess a number from 1 to a 100 within 8 guesses.

- [x] Detail which bugs you found.

Bugs:
1) Hints for the user were flipped in the app.
2) The state didn't reset when a user won and wanted to start over.
3) Race condition between input state updates and button clicks where if a user enters a new guess that is different from their previous guess then it won't register until the second time.

- [x] Explain what fixes you applied.

1) I added the `session_state.status = "playing"` line in logic_utils.py after clicking New Game.
2) I changed the hints from "Higher/Lower" to "Lower/Higher".
3) I changed the input field and submit guess button so that it is within a form for atomic operations.

## 📸 Demo

- [x] [Insert a screenshot of your fixed, winning game here]



https://github.com/user-attachments/assets/8a2b2e9b-02ee-4341-83aa-e0381238e379



## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, insert a screenshot of your Enhanced Game UI here]
