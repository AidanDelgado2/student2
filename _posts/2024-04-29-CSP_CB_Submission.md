<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<!-- Game styling -->
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
<!-- This is where the game elements are established -->
<div id="game-container">
      <!-- Intro to the game -->
    <p>Guess the animal! Here are three facts... good luck!:</p>

    <div id="animal-facts">
        <span id="fact1"></span><br>
        <span id="fact2"></span><br>
        <span id="fact3"></span><br>
    </div>
     <!-- This part displays the result of the guess -->
    <p class="result" id="result"></p>

    <!-- This part is where the user can click the button to guess or to play again -->
    <input type="text" id="guess-input" placeholder="Enter your guess">
    <button onclick="checkGuess()">Guess</button>
    <button onclick="resetGame()">Play Again</button>

    <!-- Images of each animal that show when the user is correct -->
    <img src="/student2/images/giraffe.png" alt="Giraffe" class="animal-image" id="giraffe-image">
    <img src="/student2/images/hippo.jpg" alt="Hippo" class="animal-image" id="hippo-image">
    <img src="/student2/images/gorilla.jpg" alt="Gorilla" class="animal-image" id="gorilla-image">
    <img src="/student2/images/lion.jpg" alt="Lion" class="animal-image" id="lion-image">
    <img src="/student2/images/cheetah.jpg" alt="Cheetah" class="animal-image" id="cheetah-image">
    <img src="/student2/images/elephant.jpg" alt="Elephant" class="animal-image" id="elephant-image">
</div>

<script>
    //List of animals with facts for each one to be listed, along with their corresponding image ids
    const animals = [
        { name: "giraffe", facts: ["Tallest land animal", "Has a long neck", "Spots on body"], imageId: "giraffe-image" },
        { name: "hippo", facts: ["Large herbivorous mammal", "Semi-aquatic", "Has large jaws"], imageId: "hippo-image" },
        { name: "gorilla", facts: ["Largest primate", "Native to Africa", "Highly intelligent"], imageId: "gorilla-image" },
        { name: "lion", facts: ["King of the jungle", "Social animals", "Distinctive mane"], imageId: "lion-image" },
        { name: "cheetah", facts: ["Fastest land animal", "Can accelerate from 0 to 60 mph in just a few seconds", "Distinctive black tear stripes"], imageId: "cheetah-image" },
        { name: "elephant", facts: ["Largest land animal", "Has tusks", "Highly intelligent and social"], imageId: "elephant-image" }
    ];

    let selectedAnimal;
    //This function starts the game by listing the animal's facts
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
    
    //This calls the startgame procedure
    startGame();

    //This function checks the user's guess
 function checkGuess() {
    const guessInput = document.getElementById('guess-input').value.trim().toLowerCase();
    let correctGuess = false;
    
    //This iterates through each animal to compare the guess with the animal's name (this code segment was partially generated using {chatgpt})
    animals.forEach(animal => {
        if (guessInput === animal.name) {
            //If their guess is correct then the program displays a congratulations message
            if (selectedAnimal.name === guessInput) {
                document.getElementById('result').textContent = "Congratulations you got it right!";
                document.getElementById('result').className = "result correct";
                document.getElementById(animal.imageId).style.display = 'block';
                correctGuess = true;
            //If their guess is not correct, it shows a nice try message
            } else {
                document.getElementById('result').textContent = "You guessed the animal, but it's not the one we're thinking of!";
                document.getElementById('result').className = "result incorrect";
            }
        }
    });
    //This is for when the user guesses an animal that is not in the defined animal list
    if (!correctGuess) {
        document.getElementById('result').textContent = "Nice try, but that's not the correct animal.";
        document.getElementById('result').className = "result incorrect";
    }
}

    //This function restarts the game
    function resetGame() {
        document.getElementById('guess-input').value = ""; 
        startGame(); 
    }
</script>

</body>
</html>
