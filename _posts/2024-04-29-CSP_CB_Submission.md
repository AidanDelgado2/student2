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
<style>
    body {
        font-family: Arial, sans-serif;
        text-align: center;
        background-image: url('your-background-image-url.jpg');
        background-size: cover;
        background-position: center;
        height: 100vh;
        margin: 0;
        padding: 0;
        color: black; 
    }
    #game-container {
        padding: 20px; 
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
    button {
        color: black; 
        background-color: white; 
    }
    .animal-image {
        display: none; 
        max-width: 200px; 
        margin-top: 20px; 
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

    <!-- Animal images -->
    <img src="https://AidanDelgado2.github.io/student2/images/giraffe.png" alt="Giraffe" class="animal-image" id="giraffe-image">
    <img src="https://AidanDelgado2.github.io/student2/images/hippo.jpg" alt="Hippo" class="animal-image" id="hippo-image">
    <img src="https://AidanDelgado2.github.io/student2/images/gorilla.jpg" alt="Gorilla" class="animal-image" id="gorilla-image">
    <img src="https://AidanDelgado2.github.io/student2/images/lion.jpg" alt="Lion" class="animal-image" id="lion-image">
    <img src="https://AidanDelgado2.github.io/student2/images/cheetah.jpg" alt="Cheetah" class="animal-image" id="cheetah-image">
    <img src="https://AidanDelgado2.github.io/student2/images/elephant.jpg" alt="Elephant" class="animal-image" id="elephant-image">
</div>

<script>
    const animals = [
        { name: "giraffe", facts: ["Tallest land animal", "Has a long neck", "Spots on body"], imageId: "giraffe-image" },
        { name: "hippo", facts: ["Large herbivorous mammal", "Semi-aquatic", "Has large jaws"], imageId: "hippo-image" },
        { name: "gorilla", facts: ["Largest primate", "Native to Africa", "Highly intelligent"], imageId: "gorilla-image" },
        { name: "lion", facts: ["King of the jungle", "Social animals", "Distinctive mane"], imageId: "lion-image" },
        { name: "cheetah", facts: ["Fastest land animal", "Can accelerate from 0 to 60 mph in just a few seconds", "Distinctive black tear stripes"], imageId: "cheetah-image" },
        { name: "elephant", facts: ["Largest land animal", "Has tusks", "Highly intelligent and social"], imageId: "elephant-image" }
    ];

    let selectedAnimal;

    function startGame() {
        const randomAnimalIndex = Math.floor(Math.random() * animals.length);
        selectedAnimal = animals[randomAnimalIndex];
        document.getElementById('fact1').textContent = selectedAnimal.facts[0];
        document.getElementById('fact2').textContent = selectedAnimal.facts[1];
        document.getElementById('fact3').textContent = selectedAnimal.facts[2];
        document.getElementById('result').textContent = "";
        const animalImages = document.querySelectorAll('.animal-image');
        animalImages.forEach(image => {
            image.style.display = 'none';
        });
    }

    startGame();
 function checkGuess() {
    const guessInput = document.getElementById('guess-input').value.trim().toLowerCase();
    let correctGuess = false;
    
    animals.forEach(animal => {
        if (guessInput === animal.name) {
            document.getElementById('result').textContent = "Congratulations you got it right!";
            document.getElementById('result').className = "result correct";
            document.getElementById(animal.imageId).style.display = 'block';
            correctGuess = true;
        }
    });

    
    if (!correctGuess) {
        document.getElementById('result').textContent = "Nice try";
        document.getElementById('result').className = "result incorrect";
    }
}


    function resetGame() {
        document.getElementById('guess-input').value = ""; 
        startGame(); 
    }
</script>

</body>
</html>
