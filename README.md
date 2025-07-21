<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Efekt Pisania</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background-color: #0d0d0d;
      color: #00ff99;
      font-family: 'Courier New', monospace;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      text-align: center;
    }

    .container {
      width: 90%;
      max-width: 800px;
      font-size: 5vw;
    }

    @media (min-width: 768px) {
      .container {
        font-size: 24px;
      }
    }

    .typewriter::after {
      content: '|';
      animation: blink 0.7s infinite;
    }

    @keyframes blink {
      0%, 100% { opacity: 1; }
      50% { opacity: 0; }
    }
  </style>
</head>
<body>

  <div class="container">
    <div id="tekst" class="typewriter"></div>
  </div>

  <!-- Dźwięk pisania -->
  <audio id="dzwiek">
    <source src="https://www.soundjay.com/mechanical/typewriter-key-1.mp3" type="audio/mpeg">
  </audio>

  <script>
    const tekst = "Witaj na mojej stronie. Piszę ten tekst specjalnie dla Ciebie...";
    const element = document.getElementById("tekst");
    const dzwiek = document.getElementById("dzwiek");
    let i = 0;

    function pisz() {
      if (i < tekst.length) {
        element.textContent += tekst.charAt(i);
        if (tekst.charAt(i) !== ' ') {
          dzwiek.currentTime = 0;
          dzwiek.play();
        }
        i++;
        setTimeout(pisz, 60); // czas między literami
      }
    }

    window.onload = pisz;
  </script>

</body>
</html>
