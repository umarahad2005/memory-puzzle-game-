# Memory Puzzle Challenge 🎮🧠

## Building a Memory Puzzle Game with Amazon Q CLI: My AI-Assisted Coding Journey

Welcome to the Memory Puzzle Challenge! This project was created for the AWS "Build Games with Amazon Q CLI" challenge. I crafted a web-based memory puzzle game with the help of Amazon’s AI-powered command-line assistant, Amazon Q CLI. This README documents my coding adventure: from game concept and prompting techniques, to notable AI-generated code, time-saving automation, and the finished product.

---

**Developed by Umar Ahad Usmani with the help of Amazon Q CLI.**

---

## Table of Contents

- [Why Memory Puzzle Challenge?](#why-memory-puzzle-challenge)
- [Tech Stack](#tech-stack)
- [Effective AI Prompting Techniques](#effective-ai-prompting-techniques)
- [How Amazon Q CLI Tackled Programming Challenges](#how-amazon-q-cli-tackled-programming-challenges)
- [Development Automation That Saved Time](#development-automation-that-saved-time)
- [Interesting AI-Generated Code Examples](#interesting-ai-generated-code-examples)
- [Final Creation: Gameplay & Screenshots](#final-creation-gameplay--screenshots)
- [Conclusion](#conclusion)

---

## Why Memory Puzzle Challenge?

I chose to build a Memory Puzzle Challenge for several reasons:

- **Engaging Concept:** The game tests your short-term memory by briefly showing characters in random grid positions, then challenging you to recall their locations. It’s fun and mentally stimulating.
- **Moderate Complexity:** With simple mechanics—displaying characters, tracking user clicks, and scoring—the game fits well within a hackathon’s scope, yet allows creative enhancements (timers, accuracy).
- **Web-Friendly:** The grid-based design is ideal for HTML, CSS, and JavaScript, making it visually appealing and interactive.

**Gameplay Goal:**  
A 3x3 grid shows three unique characters for 5 seconds. After they disappear, players click the correct tiles to score points. Features include a countdown timer, score tracking, round counter, accuracy percentage, and a best score record.

---

## Tech Stack

- **HTML (`enhanced_memory_puzzle.html`):** Structures the 3x3 grid and UI elements (score, round, accuracy, best score, start/reset buttons).
- **CSS (embedded in HTML):** Styles the grid, tiles, characters, and UI for a clean, responsive look.
- **JavaScript (embedded in HTML):** Handles game logic, random character placement, timers, click validation, and scoring.
- **Amazon Q CLI:** My AI coding sidekick for generating code snippets, suggesting solutions, and automating development.

---

## Effective AI Prompting Techniques

To get the best results from Amazon Q CLI, I refined my prompting approach:

- **Clear & Focused Prompts:** Instead of vague requests (e.g., `/q write a memory game`), I used specific ones:  
  `/q generate JavaScript to display 3 random characters in a 3x3 grid for 5 seconds`
- **Modular Tasks:** Broke features into chunks:  
  `/q suggest JavaScript for a 5-second countdown timer with visual update`
- **Refinement:** Iterated on code:  
  `/q modify this function to ensure no two characters appear in the same grid cell`
- **Context Inclusion:** Supplied details for complex logic:  
  `/q write a JavaScript function to check if clicked grid cells match 3 previously shown character positions, awarding 100 points per correct click`
- **Best Practices:** Asked for advice:  
  `/q what’s the best way to handle click events on a grid in JavaScript?`

---

## How Amazon Q CLI Tackled Programming Challenges

### Randomization Without Duplicates

To place three unique characters in random grid cells, Q CLI suggested a shuffle-based function:

```js
function getRandomPositions(total, count) {
  const indices = Array.from({length: total}, (_, i) => i);
  for (let i = indices.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [indices[i], indices[j]] = [indices[j], indices[i]];
  }
  return indices.slice(0, count);
}
```

### Timer Synchronization

For the 5-second display phase, Q CLI generated a setInterval-based countdown:

```js
function startCountdown(duration, callback) {
  let timeLeft = duration;
  const timerDisplay = document.getElementById('timer');
  const interval = setInterval(() => {
    timerDisplay.textContent = timeLeft;
    timeLeft--;
    if (timeLeft < 0) {
      clearInterval(interval);
      callback();
    }
  }, 1000);
}
```

### Click Validation

To validate player clicks, Q CLI suggested:

```js
function checkClick(index, correctPositions, clickedPositions) {
  if (clickedPositions.includes(index)) return false;
  clickedPositions.push(index);
  return correctPositions.includes(index);
}
```

---

## Development Automation That Saved Time

Amazon Q CLI boosted my productivity by:

- **HTML Boilerplate:**  
  `/q provide an HTML structure for a 3x3 grid memory game with score, round, and timer displays`
- **CSS Styling:**  
  `/q suggest CSS for a responsive 3x3 grid with hover effects on tiles`
- **Function Templates:**  
  `/q write a JavaScript function to reset a game’s score, round, and grid state`
- **Debugging Aid:**  
  `/q how to prevent multiple click events on a grid in JavaScript`

---

## Interesting AI-Generated Code Examples

### Character Display Function

Q CLI helped create a function to show three unique characters (emojis) in random grid positions:

```js
function showCharacters() {
  const tiles = document.querySelectorAll('.tile');
  const characters = ['😺', '🐶', '🦊'];
  const positions = getRandomPositions(9, 3);
  positions.forEach((pos, i) => {
    tiles[pos].textContent = characters[i];
    tiles[pos].classList.add('active');
  });
  startCountdown(5, () => {
    tiles.forEach(tile => {
      tile.textContent = '';
      tile.classList.remove('active');
    });
    enablePlayerClicks();
  });
}
```

### Scoring and Accuracy Calculation

Q CLI provided a scoring system and accuracy percentage:

```js
function updateScore(correctClicks, totalClicks) {
  const scoreElement = document.getElementById('score');
  const accuracyElement = document.getElementById('accuracy');
  const bestScoreElement = document.getElementById('best-score');
  let score = parseInt(scoreElement.textContent);
  score += correctClicks * 100;
  scoreElement.textContent = score;
  const accuracy = totalClicks ? ((correctClicks / totalClicks) * 100).toFixed(1) : 0;
  accuracyElement.textContent = `${accuracy}%`;
  if (score > parseInt(bestScoreElement.textContent)) {
    bestScoreElement.textContent = score;
  }
}
```

---

## Final Creation: Gameplay & Screenshots

- **Gameplay:**  
  A 3x3 grid displays three unique emojis (e.g., 😺, 🐶, 🦊) for 5 seconds with a visible countdown. After they vanish, click the tiles where they appeared. Score 100 points per correct click, with a perfect round bonus (300 points). The game tracks score, round, accuracy, and best score.

- **Visuals:**  
  Responsive grid, animated tiles, vibrant UI, and a custom pointer cursor.

- **Screenshots:**  
  *(Add your screenshots/images here)*

- **Play it here:** [Memory Puzzle Challenge](#)  
  **Explore the code:** [GitHub Repository]
  https://github.com/umarahad2005/memory-puzzle-game-
  (#)

---

## Conclusion

Building the Memory Puzzle Challenge with Amazon Q CLI was a rewarding experience. The AI’s ability to generate modular code, solve programming challenges, and automate repetitive tasks made development efficient and enjoyable. From randomization to timer management, Q CLI handled classic issues with finesse, and its output served as a strong foundation for further customization.

If you’re curious about AI-driven coding, give Amazon Q CLI a try — it’s a game-changer!

---

## Want to Create Your Own Game?

Check out my [DevOps Workshop Walkthrough](#) for a step-by-step guide on using Q CLI, building a web game, and deploying with Kinsta.  
Share your project with **#AmazonQCLI** and show off your skills!

---
