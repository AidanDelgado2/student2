---
toc: true
comments: true
layout: post
title: Matching Game
type: hacks
courses: {'csp': {'week': 20}}
---

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Matching Game</title>
<style>
  .card {
    width: 100px;
    height: 100px;
    background-color: #aaa;
    margin: 5px;
    display: inline-block;
    cursor: pointer;
    text-align: center;
    line-height: 100px;
    font-size: 24px;
  }
</style>
</head>
<body>
<h1>Matching Game</h1>
<div id="gameBoard"></div>
<script>
  // Function to shuffle an array
  function shuffle(array) {
    for (let i = array.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [array[i], array[j]] = [array[j], array[i]];
    }
    return array;
  }

  // Generate a random pattern for a card
  function generatePattern() {
    const patterns = ['⚫', '⚪', '⚬', '⚭', '⚮', '⚯']; // Add more if needed
    return patterns[Math.floor(Math.random() * patterns.length)];
  }

  // Initialize game
  function initializeGame() {
    const cards = [];
    const gameBoard = document.getElementById('gameBoard');

    // Generate pairs of patterns
    for (let i = 0; i < 8; i++) {
      const pattern = generatePattern();
      cards.push(pattern, pattern);
    }

    // Shuffle the cards
    shuffle(cards);

    // Display cards on the board
    cards.forEach((pattern, index) => {
      const card = document.createElement('div');
      card.classList.add('card');
      card.dataset.index = index;
      card.textContent = pattern;
      card.addEventListener('click', handleCardClick);
      gameBoard.appendChild(card);
    });
  }

  // Handle card click
  let firstCard = null;
  let secondCard = null;
  function handleCardClick(event) {
    const clickedCard = event.target;

    // Ignore if the card is already matched or two cards are already revealed
    if (clickedCard.classList.contains('matched') || secondCard) return;

    // Reveal the clicked card
    clickedCard.classList.add('revealed');

    if (!firstCard) {
      // First card clicked
      firstCard = clickedCard;
    } else {
      // Second card clicked
      secondCard = clickedCard;

      // Check for a match after a short delay
      setTimeout(checkForMatch, 500);
    }
  }

  // Check if two revealed cards match
  function checkForMatch() {
    if (firstCard.textContent === secondCard.textContent) {
      // Match found
      firstCard.classList.add('matched');
      secondCard.classList.add('matched');
    } else {
      // No match, flip the cards back
      firstCard.classList.remove('revealed');
      secondCard.classList.remove('revealed');
    }

    // Reset firstCard and secondCard
    firstCard = null;
    secondCard = null;
  }

  // Initialize the game when the page loads
  window.onload = initializeGame;
</script>
</body>
</html>
