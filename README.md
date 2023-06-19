<!DOCTYPE html>
<html>
<head>
  <title>Flappy Bird</title>
  <style>
    canvas {
      border: 1px solid black;
      display: block;
      margin: 0 auto;
    }
  </style>
</head>
<body>
  <canvas id="canvas" width="400" height="600"></canvas>

  <script>
    // Flappy Bird game logic

    // Get the canvas element
    const canvas = document.getElementById("canvas");
    const context = canvas.getContext("2d");

    // Bird properties
    const bird = {
      x: 50,
      y: canvas.height / 2,
      width: 50,
      height: 40,
      gravity: 2,
      velocity: 0,
      jump: -30,
    };

    // Pipes properties
    const pipes = [];
    const pipeGap = 150;
    const pipeWidth = 80;

    let score = 0;
    let gameOver = false;

    // Function to draw the bird
    function drawBird() {
      context.fillStyle = "yellow";
      context.fillRect(bird.x, bird.y, bird.width, bird.height);
    }

    // Function to draw the pipes
    function drawPipes() {
      context.fillStyle = "green";
      for (let i = 0; i < pipes.length; i++) {
        const pipe = pipes[i];
        context.fillRect(pipe.x, 0, pipeWidth, pipe.top);
        context.fillRect(pipe.x, pipe.top + pipeGap, pipeWidth, canvas.height - (pipe.top + pipeGap));
      }
    }

    // Function to move the bird
    function moveBird() {
      bird.velocity += bird.gravity;
      bird.y += bird.velocity;
    }

    // Function to move the pipes
    function movePipes() {
      for (let i = 0; i < pipes.length; i++) {
        const pipe = pipes[i];
        pipe.x -= 5;

        // Remove the pipe when it's off the screen
        if (pipe.x + pipeWidth <= 0) {
          pipes.splice(i, 1);
          i--;
        }

        // Check for collision
        if (
          bird.x + bird.width > pipe.x && bird.x < pipe.x + pipeWidth &&
          (bird.y < pipe.top || bird.y + bird.height > pipe.top + pipeGap)
        ) {
          gameOver = true;
        }

        // Update score when passing a pipe
        if (pipe.x + pipeWidth === bird.x) {
          score++;
        }
      }
    }

    // Function to generate new pipes
    function generatePipes() {
      const pipePosition = canvas.width;
      const randomY = Math.floor(Math.random() * (canvas.height - pipeGap));

      pipes.push({
        x: pipePosition,
        top: randomY,
      });
    }

    // Game loop
    function gameLoop() {
      if (gameOver) {
        return;
      }

      context.clearRect(0, 0, canvas.width, canvas.height);

      drawBird();
      moveBird();

      if (bird.y + bird.height > canvas.height || bird.y < 0) {
        gameOver = true;
      }

      drawPipes();
      movePipes();

      if (pipes.length < 5 && pipes[pipes.length - 1].x < canvas.width - 200) {
        generatePipes();
      }

      context.fillStyle = "black";
      context.font = "20px Arial";
      context.fillText("Score: " + score, 10, 25);

      requestAnimationFrame(gameLoop);
    }

    // Function to handle bird jump
    function jump() {
      if (gameOver) {
        resetGame();
        return;
      }

      bird.velocity = bird.jump;
    }

    // Function to reset the game
    function resetGame() {
      bird.y = canvas.height / 2;
      bird.velocity = 0;
      pipes.length = 0;
      score = 0;
      gameOver = false;
    }

    // Event listener for key press
    document.addEventListener("keydown", jump);

    // Start the game
    gameLoop();
  </script>
</body>
</html>
You can save this code in an HTML file and open it in a web browser to see the Flappy Bird game in action. The game involves controlling the bird's flight by pressing any key, and you need to navigate it through the gaps between the pipes to score points. When the bird collides with a pipe or hits the top or bottom of the screen, the game ends. Pressing any key after that will reset the game and start over.





Regenerate<!DOCTYPE html>
<html>
<head>
  <title>Flappy Bird</title>
  <style>
    canvas {
      border: 1px solid black;
      display: block;
      margin: 0 auto;
    }
  </style>
</head>
<body>
  <canvas id="canvas" width="400" height="600"></canvas>

  <script>
    // Flappy Bird game logic

    // Get the canvas element
    const canvas = document.getElementById("canvas");
    const context = canvas.getContext("2d");

    // Bird properties
    const bird = {
      x: 50,
      y: canvas.height / 2,
      width: 50,
      height: 40,
      gravity: 2,
      velocity: 0,
      jump: -30,
    };

    // Pipes properties
    const pipes = [];
    const pipeGap = 150;
    const pipeWidth = 80;

    let score = 0;
    let gameOver = false;

    // Function to draw the bird
    function drawBird() {
      context.fillStyle = "yellow";
      context.fillRect(bird.x, bird.y, bird.width, bird.height);
    }

    // Function to draw the pipes
    function drawPipes() {
      context.fillStyle = "green";
      for (let i = 0; i < pipes.length; i++) {
        const pipe = pipes[i];
        context.fillRect(pipe.x, 0, pipeWidth, pipe.top);
        context.fillRect(pipe.x, pipe.top + pipeGap, pipeWidth, canvas.height - (pipe.top + pipeGap));
      }
    }

    // Function to move the bird
    function moveBird() {
      bird.velocity += bird.gravity;
      bird.y += bird.velocity;
    }

    // Function to move the pipes
    function movePipes() {
      for (let i = 0; i < pipes.length; i++) {
        const pipe = pipes[i];
        pipe.x -= 5;

        // Remove the pipe when it's off the screen
        if (pipe.x + pipeWidth <= 0) {
          pipes.splice(i, 1);
          i--;
        }

        // Check for collision
        if (
          bird.x + bird.width > pipe.x && bird.x < pipe.x + pipeWidth &&
          (bird.y < pipe.top || bird.y + bird.height > pipe.top + pipeGap)
        ) {
          gameOver = true;
        }

        // Update score when passing a pipe
        if (pipe.x + pipeWidth === bird.x) {
          score++;
        }
      }
    }

    // Function to generate new pipes
    function generatePipes() {
      const pipePosition = canvas.width;
      const randomY = Math.floor(Math.random() * (canvas.height - pipeGap));

      pipes.push({
        x: pipePosition,
        top: randomY,
      });
    }

    // Game loop
    function gameLoop() {
      if (gameOver) {
        return;
      }

      context.clearRect(0, 0, canvas.width, canvas.height);

      drawBird();
      moveBird();

      if (bird.y + bird.height > canvas.height || bird.y < 0) {
        gameOver = true;
      }

      drawPipes();
      movePipes();

      if (pipes.length < 5 && pipes[pipes.length - 1].x < canvas.width - 200) {
        generatePipes();
      }

      context.fillStyle = "black";
      context.font = "20px Arial";
      context.fillText("Score: " + score, 10, 25);

      requestAnimationFrame(gameLoop);
    }

    // Function to handle bird jump
    function jump() {
      if (gameOver) {
        resetGame();
        return;
      }

      bird.velocity = bird.jump;
    }

    // Function to reset the game
    function resetGame() {
      bird.y = canvas.height / 2;
      bird.velocity = 0;
      pipes.length = 0;
      score = 0;
      gameOver = false;
    }

    // Event listener for key press
    document.addEventListener("keydown", jump);

    // Start the game
    gameLoop();
  </script>
</body>
</html>
You can save this code in an HTML file and open it in a web browser to see the Flappy Bird game in action. The game involves controlling the bird's flight by pressing any key, and you need to navigate it through the gaps between the pipes to score points. When the bird collides with a pipe or hits the top or bottom of the screen, the game ends. Pressing any key after that will reset the game and start over.





Regenerate
