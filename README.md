### Hello, I am Matheus Redondo. 🙋‍♂️😁

## Technologies I work with on a daily basis

<div style="display: inline_block"><br/>
    <img align="center" alt="html15" src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white">
    <img align="center" alt="css" src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white">
    <img align="center" alt="js" src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black">
    <img align="center" alt="php" src="https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white">
    <img align="center" alt="python" src=https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white>
     <img align="center" alt="bootstrap" src=https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white>
</div><br/>

###  GitHub Stats 

<table>
  <tr>
    <td>
      <img src="https://github-readme-stats.vercel.app/api?username=devMathes&hide_title=true&show_icons=true&include_all_commits=false&count_private=true&line_height=25&hide=issues&bg_color=000000&title_color=FF00F6&text_color=FFFFFF&border_radius=3&border_color=36123c&icon_color=FF00F6&theme=jolly" alt="GitHub stats">
    </td>
    <td>
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=devMathes&line_height=10&card_width=290&layout=compact&count_private=true&langs_count=4&show_icons=true&title_color=FF00F6&hide=html,scss,less&bg_color=000000&text_color=8B8B8B&border_radius=3&border_color=561760" alt="Most Used Languages">
    </td>
  </tr>
</table>

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Jogo da Cobrinha - devMathes</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      background: #000;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      font-family: monospace;
      color: #fff;
    }
    canvas {
      background: #111;
      border: 2px solid #FF00F6;
    }
    h1 {
      margin: 10px;
      color: #FF00F6;
    }
    .score {
      margin-bottom: 10px;
      font-size: 20px;
      color: #00FF88;
    }
  </style>
</head>
<body>
  <h1>Jogo da Cobrinha - devMathes 🐍</h1>
  <div class="score">Pontuação: <span id="score">0</span></div>
  <canvas id="game" width="400" height="400"></canvas>
  <audio id="eatSound" src="sounds/eat.mp3" preload="auto"></audio>

  <script>
    const canvas = document.getElementById("game");
    const ctx = canvas.getContext("2d");
    const scoreEl = document.getElementById("score");
    const eatSound = document.getElementById("eatSound");

    const grid = 20;
    let count = 0;
    let score = 0;

    let snake = {
      x: 160,
      y: 160,
      dx: grid,
      dy: 0,
      cells: [],
      maxCells: 4
    };

    let apple = {
      x: 320,
      y: 320
    };

    function getRandomInt(min, max) {
      return Math.floor(Math.random() * (max - min)) + min;
    }

    function resetGame() {
      snake.x = 160;
      snake.y = 160;
      snake.cells = [];
      snake.maxCells = 4;
      snake.dx = grid;
      snake.dy = 0;
      score = 0;
      scoreEl.textContent = score;
      apple.x = getRandomInt(0, 20) * grid;
      apple.y = getRandomInt(0, 20) * grid;
    }

    function loop() {
      requestAnimationFrame(loop);

      if (++count < 4) return;
      count = 0;

      ctx.clearRect(0, 0, canvas.width, canvas.height);

      snake.x += snake.dx;
      snake.y += snake.dy;

      if (snake.x < 0) snake.x = canvas.width - grid;
      else if (snake.x >= canvas.width) snake.x = 0;

      if (snake.y < 0) snake.y = canvas.height - grid;
      else if (snake.y >= canvas.height) snake.y = 0;

      snake.cells.unshift({ x: snake.x, y: snake.y });

      if (snake.cells.length > snake.maxCells) {
        snake.cells.pop();
      }

      ctx.fillStyle = "#FF00F6";
      ctx.fillRect(apple.x, apple.y, grid - 1, grid - 1);

      ctx.fillStyle = "#00FF88";
      snake.cells.forEach((cell, index) => {
        ctx.fillRect(cell.x, cell.y, grid - 1, grid - 1);

        if (cell.x === apple.x && cell.y === apple.y) {
          snake.maxCells++;
          score++;
          scoreEl.textContent = score;
          eatSound.currentTime = 0;
          eatSound.play();

          apple.x = getRandomInt(0, 20) * grid;
          apple.y = getRandomInt(0, 20) * grid;
        }

        for (let i = index + 1; i < snake.cells.length; i++) {
          if (cell.x === snake.cells[i].x && cell.y === snake.cells[i].y) {
            resetGame();
          }
        }
      });
    }

    document.addEventListener("keydown", function (e) {
      if (e.key === "ArrowLeft" && snake.dx === 0) {
        snake.dx = -grid;
        snake.dy = 0;
      } else if (e.key === "ArrowUp" && snake.dy === 0) {
        snake.dy = -grid;
        snake.dx = 0;
      } else if (e.key === "ArrowRight" && snake.dx === 0) {
        snake.dx = grid;
        snake.dy = 0;
      } else if (e.key === "ArrowDown" && snake.dy === 0) {
        snake.dy = grid;
        snake.dx = 0;
      }
    });

    requestAnimationFrame(loop);
  </script>
</body>
</html>



    
</picture>
<br><br>
<h3>Passionate about technology and constantly seeking to grow and improve.</h3>
