<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Mother's Day Card for Suzie Lue</title>
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #fff0f5;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
    }

    .card {
      width: 800px;
      height: 500px;
      perspective: 1000px;
      position: relative;
    }

    .card-inner {
      width: 100%;
      height: 100%;
      transition: transform 1s;
      transform-style: preserve-3d;
      position: relative;
      cursor: pointer;
    }

    .card.open .card-inner {
      transform: rotateY(180deg);
    }

    .card-front, .card-back {
      position: absolute;
      width: 100%;
      height: 100%;
      backface-visibility: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
      border: 4px solid #ff69b4;
      border-radius: 12px;
      box-shadow: 0 6px 15px rgba(0,0,0,0.2);
    }

    .card-front {
      background: linear-gradient(to right, #ffe4e1, #fff0f5);
      font-size: 2.5em;
      color: #b30059;
      font-weight: bold;
      text-align: center;
      flex-direction: column;
    }

    .card-back {
      background: linear-gradient(to right, #fff5f8, #fffde7, #ffe6f0);
      transform: rotateY(180deg);
      flex-direction: column;
      overflow-y: auto;
      padding: 30px;
      box-sizing: border-box;
      justify-content: flex-start;
      align-items: center;
    }

    .card-back header {
      font-size: 2.5em;
      color: #b30059;
      margin-bottom: 20px;
      font-weight: bold;
    }

    .message {
      max-width: 600px;
      font-size: 1.3em;
      color: #a80038;
      margin-bottom: 20px;
      text-align: center;
    }

    .signature {
      font-family: 'Dancing Script', cursive;
      font-size: 1.8em;
      color: #ff4d6d;
    }

    .gallery {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      margin-top: 20px;
      gap: 10px;
    }

    .reveal-card {
      width: 150px;
      height: 150px;
      background-color: #ffe6e6;
      border: 2px solid #ff9999;
      border-radius: 10px;
      position: relative;
      cursor: pointer;
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #a80038;
      font-weight: bold;
      font-size: 1em;
    }

    .reveal-card img {
      display: none;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .reveal-card.clicked img {
      display: block;
    }

    .reveal-card.clicked span {
      display: none;
    }

    .confetti {
      position: absolute;
      width: 100%;
      height: 100%;
      pointer-events: none;
      overflow: hidden;
      z-index: 10;
    }

    .confetti-piece {
      width: 10px;
      height: 10px;
      background-color: pink;
      position: absolute;
      top: 0;
      left: 50%;
      animation: fall 3s linear infinite;
    }

    @keyframes fall {
      0% { transform: translateY(0) rotate(0deg); opacity: 1; }
      100% { transform: translateY(500px) rotate(360deg); opacity: 0; }
    }

    audio {
      display: none;
    }
  </style>
</head>
<body>
  <div class="card" id="card">
    <div class="card-inner">
      <div class="card-front">
        💐 Happy Mother's Day Sue! 💖<br><br>
        <small>Click to open your card</small>
      </div>
      <div class="card-back">
        <header>💐 Happy Mother's Day Sue! 💖</header>
        <div class="message">
          Dear Momzy,<br><br>
          Your strength, love, and unwavering support have carried us through every season. 
          You're the one we turn to when the world gets hard, and the one who celebrates with us when joy comes easy. 
          You’ve been our constant cheerleader, comforter, and compass. Your love is fierce, your spirit is unshakable, 
          and your heart is gold. We are forever grateful for you. 💛❤️💗
        </div>

        <div class="signature">From your bestie – Brinny 💖</div>

        <div class="gallery">
          <div class="reveal-card" onclick="reveal(this)">
            <span>Click to reveal 🌼</span>
            <img src="photosuzie1.jpeg" alt="Photo 1">
          </div>
          <div class="reveal-card" onclick="reveal(this)">
            <span>Tap to see 💕</span>
            <img src="photosuzie2.jpeg" alt="Photo 2">
          </div>
          <div class="reveal-card" onclick="reveal(this)">
            <span>Peek inside 🌸</span>
            <img src="photsuzie3.jpeg" alt="Photo 3">
          </div>
        </div>
      </div>
    </div>
  </div>

  <audio id="music" autoplay>
    <source src="Mama lyrics Christopher Martin-yt.savetube.me.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
  </audio>

  <div class="confetti" id="confetti"></div>

  <script>
    const card = document.getElementById('card');
    const music = document.getElementById('music');
    const confettiContainer = document.getElementById('confetti');

    card.addEventListener('click', () => {
      card.classList.add('open');
      music.play();
      launchConfetti();
    });

    function reveal(card) {
      card.classList.add('clicked');
    }

    function launchConfetti() {
      for (let i = 0; i < 100; i++) {
        const piece = document.createElement('div');
        piece.classList.add('confetti-piece');
        piece.style.left = Math.random() * 100 + '%';
        piece.style.backgroundColor = ['#ff69b4', '#ffff66', '#ffcccb'][Math.floor(Math.random() * 3)];
        piece.style.animationDuration = 2 + Math.random() * 2 + 's';
        piece.style.width = piece.style.height = Math.random() * 10 + 5 + 'px';
        confettiContainer.appendChild(piece);
        setTimeout(() => confettiContainer.removeChild(piece), 4000);
      }
    }
  </script>
</body>
</html>
