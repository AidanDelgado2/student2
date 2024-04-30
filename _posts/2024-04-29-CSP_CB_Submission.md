---
toc: true
comments: true
layout: post
title: Animal Guessing Game
type: hacks
courses: {'csp': {'week': 20}}
---


<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Animal Guessing Game</title>
<style>
    body {
        font-family: Arial, sans-serif;
        text-align: center;
        background-image: url('');
        background-size: cover;
        background-position: center;
        height: 100vh; /* Ensures full coverage of the viewport height */
        margin: 0; /* Removes default margin */
        padding: 0; /* Removes default padding */
    }
    #game-container {
        padding: 20px; /* Add some padding to the game container */
    }
    .result {
        font-size: 18px;
        margin-top: 10px;
    }
    .result.correct {
        color: green;
    }
    .result.incorrect {
        color: red;
    }
</style>
</head>
<body>

<div id="game-container">

    <p>Guess the animal! Here are three facts... good luck!:</p>

    <div id="animal-facts">
        <span id="fact1"></span><br>
        <span id="fact2"></span><br>
        <span id="fact3"></span><br>
    </div>

    <p class="result" id="result"></p>

    <input type="text" id="guess-input" placeholder="Enter your guess">
    <button onclick="checkGuess()">Guess</button>
    <button onclick="resetGame()">Play Again</button>
</div>

<script>
    // Animal facts
    const animals = [
        { name: "giraffe", facts: ["Tallest land animal", "Has a long neck", "Spots on body"] },
        { name: "hippo", facts: ["Large herbivorous mammal", "Semi-aquatic", "Has large jaws"] },
        { name: "gorilla", facts: ["Largest primate", "Native to Africa", "Highly intelligent"] },
        { name: "lion", facts: ["King of the jungle", "Social animals", "Distinctive mane"] },
        { name: "cheetah", facts: ["Fastest land animal", "Can accelerate from 0 to 60 mph in just a few seconds", "Distinctive black tear stripes"] },
        { name: "elephant", facts: ["Largest land animal", "Has tusks", "Highly intelligent and social"] }
    ];

    let selectedAnimal;

    function startGame() {
        // Select a random animal
        const randomAnimalIndex = Math.floor(Math.random() * animals.length);
        selectedAnimal = animals[randomAnimalIndex];

        // Display facts
        document.getElementById('fact1').textContent = selectedAnimal.facts[0];
        document.getElementById('fact2').textContent = selectedAnimal.facts[1];
        document.getElementById('fact3').textContent = selectedAnimal.facts[2];

        // Clear previous result
        document.getElementById('result').textContent = "";
    }

    startGame(); // Start the game initially

    // Check the user's guess
    function checkGuess() {
        const guessInput = document.getElementById('guess-input').value.trim().toLowerCase();
        if (guessInput === selectedAnimal.name) {
            document.getElementById('result').textContent = "Congratulations you got it right!";
            document.getElementById('result').className = "result correct";
        } else {
            document.getElementById('result').textContent = "Nice try";
            document.getElementById('result').className = "result incorrect";
        }
    }

    // Reset the game
    function resetGame() {
        document.getElementById('guess-input').value = ""; // Clear guess input
        startGame(); // Start a new game
    }
</script>

</body>
</html>
