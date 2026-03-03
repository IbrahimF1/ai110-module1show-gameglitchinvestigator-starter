# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?

The first time I ran it it displayed a Streamlit app that displayed a text box that allows a user to take a guess along with a button to submit their guess or start a new game. The user can also choose to have hints that nudge them towards the secret number. There is also Developer Debug Info that displays additional information that would normally be hidden to the user like the secret number, number of attempts, score, difficulty, and history.

- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").

Two bugs I noticed are the flipped hints, and the state doesn't get reset when a user wins the guessing game and wants to start over. I also noticed that the difficulty was always set to normal.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?

I used Claude Code in VS Code.

- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).

I asked Claude Code about the New Game after correctly guessing the number issue and it correctly identified that the session_state.status wasn't being set to "playing" after clicking New Game.

- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

The AI was having issues resolving and explaining the race condition issue I found later between input state updates and button clicks. I tested the solution it gave and was still having the same issue.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?

I rediced a bug was fixed after testing it out with custom test cases.

- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
  
I tested a series of identical guesses followed by a series of all different guesses. Through these tests, I noticed if a user enters a new guess that is different from their previous guess then it won't register until the second time, but if they are spamming the same guess multiple times then it will register on first try.

**Example:**
User Input: 1, 2, 3, 4, 5

History: 1, 3, 5

- Did AI help you design or understand any tests? How?

When I encountered this issue during my testing the AI was able to explain to me the reason a race condition was causing this issue and how to solve this problem.

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.

The secret number didn't keep changing in my original app.

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

The best way I would describe reruns is whenever a user takes an action on the Streamlit site it will cause the website to refresh. When the website refreshes we want some information to carry over across refreshes. We use session state to carry over information across refreshes.

- What change did you make that finally gave the game a stable secret number?

I never had this issue.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.

Creating Mermaid diagrams helped with understanding code logic.

- What is one thing you would do differently next time you work with AI on a coding task?

Creating micro controlled changes that can be easily rolled back after testing is a change that I will make in future projects.

- In one or two sentences, describe how this project changed the way you think about AI generated code.

If I speak confidently enough, the AI will believe me. That is why it is very important to know what I are looking for before I write one word to an LLM for help.