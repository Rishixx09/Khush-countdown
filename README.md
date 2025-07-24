<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Happy Birthday Khushuu 💙</title>
  <link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Nunito:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      padding: 0;
      background: linear-gradient(to bottom right, #0b3c5d, #1f77b4);
      font-family: 'Nunito', sans-serif;
      color: #ffffff;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      overflow: hidden;
      position: relative;
    }

    .box {
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(8px);
      padding: 30px;
      border-radius: 20px;
      box-shadow: 0 8px 25px rgba(0, 0, 0, 0.4);
      text-align: center;
      max-width: 90%;
      width: 400px;
      transition: all 0.5s ease-in-out;
      position: relative;
      z-index: 2;
      cursor: pointer;
    }

    .box h2 {
      font-family: 'Pacifico', cursive;
      font-size: 2rem;
      color: #ffffff;
    }

    .heart {
      font-size: 3rem;
      animation: pulse 1.5s infinite;
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.2); }
      100% { transform: scale(1); }
    }

    .content {
      margin-top: 20px;
      opacity: 0;
      max-height: 0;
      overflow: hidden;
      transition: max-height 1s ease, opacity 0.6s ease;
    }

    .content.show {
      opacity: 1;
      max-height: 2000px;
    }

    .content img {
      width: 170px;
      border-radius: 15px;
      margin-bottom: 15px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.4);
    }

    .quote {
      font-size: 1.1rem;
      margin-top: 15px;
      font-style: italic;
    }

    .countdown {
      font-size: 1.4rem;
      margin-top: 15px;
    }

    .countdown span {
      display: inline-block;
      min-width: 55px;
      background: rgba(255, 255, 255, 0.2);
      border-radius: 10px;
      padding: 8px;
      margin: 6px;
      font-weight: bold;
    }

    .footer {
      margin-top: 25px;
      font-size: 1rem;
      color: #c4ebff;
    }

    video {
      margin-top: 20px;
      width: 100%;
      border-radius: 10px;
      box-shadow: 0 0 15px rgba(0,0,0,0.3);
    }

    .music-control {
      position: absolute;
      top: 15px;
      right: 15px;
      font-size: 1.3rem;
      cursor: pointer;
      background: #ffffff22;
      border-radius: 30px;
      padding: 5px 10px;
      backdrop-filter: blur(5px);
      z-index: 3;
    }

    .emoji-rain span {
      position: absolute;
      animation: fall 5s linear infinite;
      font-size: 2rem;
      z-index: 0;
    }

    @keyframes fall {
      0% { top: -5%; opacity: 1; }
      100% { top: 105%; opacity: 0; transform: rotate(360deg); }
    }
  </style>
</head>
<body>

  <div class="music-control" id="musicBtn">🔊</div>

  <div class="box" id="birthdayBox">
    <div class="heart">💙</div>
    <h2>For Khushuu 💙</h2>
    <h4 style="color:#fff;">Tap the heart to reveal your surprise!</h4>

    <div class="content" id="content">
      <img src="IMG-20250626-WA0018.jpg" alt="Khushuu Photo" />

      <div class="countdown">
        <span id="days">00</span> Days
        <span id="hours">00</span> Hours
        <span id="minutes">00</span> Minutes
        <span id="seconds">00</span> Seconds
      </div>

      <p class="quote">
        "Good things take time, and your birthday is one of them.<br> Just waiting for the 28th to celebrate YOU!"
      </p>

      <p style="color: #ffd; font-size: 0.9rem; margin-top: 10px;">
        🔊 Tap the speaker icon on the video to hear it!
      </p>

      <video autoplay muted loop controls>
        <source src="HappyEdit.mp4" type="video/mp4">
        Your browser does not support the video tag.
      </video>

      <div class="footer">
        Made with 💖 by your best friend Rishu
      </div>
    </div>
  </div>

  <!-- Background Music -->
  <audio id="bg-music" autoplay loop>
    <source src="https://dl.dropboxusercontent.com/scl/fi/jgfsj66vsywky05j72ehe/kabhi-kabhi-aditi.mp3?rlkey=xdxj6o0q06z4w3sda3xlwo1ns&raw=1" type="audio/mpeg">
  </audio>

  <!-- Emoji Rain -->
  <div class="emoji-rain" id="emojiRain"></div>

  <script>
    const box = document.getElementById('birthdayBox');
    const content = document.getElementById('content');
    const music = document.getElementById('bg-music');
    const musicBtn = document.getElementById('musicBtn');

    box.addEventListener('click', () => {
      content.classList.add('show');
    });

    musicBtn.addEventListener('click', () => {
      if (music.paused) {
        music.play();
        musicBtn.textContent = '🔊';
      } else {
        music.pause();
        musicBtn.textContent = '🔇';
      }
    });

    function updateCountdown() {
      const now = new Date().getTime();
      const birthday = new Date(`August 28, ${new Date().getFullYear()} 00:00:00`).getTime();
      const gap = birthday > now ? birthday - now : new Date(`August 28, ${new Date().getFullYear() + 1} 00:00:00`).getTime() - now;

      const second = 1000, minute = second * 60, hour = minute * 60, day = hour * 24;
      const d = Math.floor(gap / day),
            h = Math.floor((gap % day) / hour),
            m = Math.floor((gap % hour) / minute),
            s = Math.floor((gap % minute) / second);

      document.getElementById('days').innerText = d;
      document.getElementById('hours').innerText = h;
      document.getElementById('minutes').innerText = m;
      document.getElementById('seconds').innerText = s;
    }

    updateCountdown();
    setInterval(updateCountdown, 1000);

    const emojis = ['💙', '💖', '🎉', '✨', '🌸', '🎂'];
    const emojiContainer = document.getElementById('emojiRain');

    function createEmoji() {
      const emoji = document.createElement('span');
      emoji.textContent = emojis[Math.floor(Math.random() * emojis.length)];
      emoji.style.left = Math.random() * 100 + 'vw';
      emoji.style.animationDuration = (2 + Math.random() * 3) + 's';
      emojiContainer.appendChild(emoji);
      setTimeout(() => emoji.remove(), 5000);
    }

    setInterval(createEmoji, 400);
  </script>
</body>
</html>
