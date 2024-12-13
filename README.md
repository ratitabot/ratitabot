<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Interacción Divertida</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      height: 100vh;
      background-color: #f7f7f7;
      margin: 0;
      text-align: center;
      overflow: hidden;
      border: 10px solid #ccc;
      box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
      border-radius: 15px;
      transition: background-color 0.5s;
    }
    img {
      max-width: 300px;
      border-radius: 10px;
      border: 5px solid #ddd;
    }
    h1 {
      margin: 20px 0;
      font-size: 24px;
      color: #333;
      text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
    }
    .button-container {
      display: flex;
      gap: 20px;
      margin-top: 20px;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      border: 2px solid;
      border-radius: 5px;
      transition: background-color 0.3s, color 0.3s, transform 0.3s;
    }
    #buttonGreen {
      background-color: #4CAF50;
      color: white;
      border-color: #388E3C;
    }
    #buttonGreen:hover {
      background-color: white;
      color: #4CAF50;
      transform: scale(1.1);
    }
    #buttonRed {
      background-color: #f44336;
      color: white;
      border-color: #d32f2f;
    }
    #buttonRed:hover {
      background-color: white;
      color: #f44336;
      transform: scale(1.1);
    }
    .mode-toggle {
      position: absolute;
      top: 10px;
      right: 10px;
      padding: 5px 10px;
      font-size: 14px;
      cursor: pointer;
      border-radius: 5px;
      border: 2px solid #333;
      background-color: white;
      color: #333;
    }
    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      25% { transform: translateX(-10px); }
      50% { transform: translateX(10px); }
      75% { transform: translateX(-10px); }
    }
    .shake { animation: shake 0.5s ease-in-out; }
  </style>
</head>
<body>
  <!-- Reproductor de música -->
  <audio id="backgroundMusic" loop autoplay>
    <source src="https://www.dropbox.com/scl/fi/spdxbh37yztps226rtiji/patitoonicham.mp3?rlkey=4t981xnyk837aq9ktezw1ewxe&st=hzm58vqe&dl=1" type="audio/mp3">
    Tu navegador no soporta el reproductor de audio.
  </audio>

  <button class="mode-toggle">Modo Oscuro</button>
  <img src="https://i.pinimg.com/736x/3a/b5/c5/3ab5c5d3997d5f2f07321591bb2b2b2a.jpg" alt="Imagen central">
  <h1 id="title">¿Me vas a visitar?</h1>
  <div class="button-container">
    <button id="buttonGreen">Sí</button>
    <button id="buttonRed">No</button>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
  <script>
    let redClickCount = 0;
    let isDarkMode = false;
    const redMessages = [
      'Dale porfis dime que sí',
      'Porfa, no seas así',
      'Anda, di que sí',
      'No seas malo, di que sí'
    ];

    const body = document.body;

    document.getElementById('buttonGreen').addEventListener('click', () => {
      confetti({
        particleCount: 100,
        spread: 70,
        origin: { y: 0.6 }
      });
    });

    document.getElementById('buttonRed').addEventListener('click', () => {
      redClickCount++;
      document.getElementById('buttonRed').textContent = redMessages[redClickCount % redMessages.length];
      if (redClickCount > 4) {
        body.classList.add('shake');
        setTimeout(() => body.classList.remove('shake'), 500);
      }
    });

    document.querySelector('.mode-toggle').addEventListener('click', () => {
      isDarkMode = !isDarkMode;
      body.style.backgroundColor = isDarkMode ? '#333' : '#f7f7f7';
      body.style.color = isDarkMode ? '#f7f7f7' : '#333';
    });
  </script>
</body>
</html>

