<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Be My Valentine 💖</title>

<!-- Cute Google Font -->
<link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">

<style>
  body {
    margin: 0;
    height: 100vh;
    background: linear-gradient(180deg, #ffc0cb, #ffd6e5);
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: "Poppins", sans-serif;
    overflow: hidden;
  }

  .popup {
    background: #fff0f6;
    padding: 30px 25px;
    border-radius: 25px;
    text-align: center;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
    max-width: 360px;
    animation: popIn 0.6s ease;
    position: relative;
  }

  @keyframes popIn {
    from { transform: scale(0.6); opacity: 0; }
    to { transform: scale(1); opacity: 1; }
  }

  h1 {
    font-family: "Pacifico", cursive;
    color: #c2185b;
    margin-bottom: 10px;
    font-size: 28px;
  }

  .dolls {
    font-size: 40px;
    margin: 10px 0;
  }

  .buttons {
    display: flex;
    justify-content: space-around;
    margin-top: 20px;
  }

  button {
    border: none;
    padding: 12px 26px;
    border-radius: 25px;
    font-size: 16px;
    cursor: pointer;
    color: white;
    background: #d81b60;
    transition: transform 0.2s, box-shadow 0.2s;
  }

  button:hover {
    transform: scale(1.1);
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
  }

  #noBtn {
    background: #ad1457;
  }

  .success {
    font-family: "Pacifico", cursive;
    font-size: 22px;
    color: #c2185b;
    margin-top: 15px;
  }

  .balloon {
    position: absolute;
    bottom: -100px;
    border-radius: 50%;
    animation: floatUp 6s linear forwards;
    opacity: 0.95;
  }

  .balloon::after {
    content: "";
    position: absolute;
    width: 2px;
    height: 30px;
    background: #555;
    bottom: -30px;
    left: 50%;
    transform: translateX(-50%);
  }

  @keyframes floatUp {
    from { transform: translateY(0); opacity: 1; }
    to { transform: translateY(-120vh); opacity: 0; }
  }

  .bubble {
    position: absolute;
    bottom: -50px;
    border-radius: 50%;
    background: rgba(173, 216, 230, 0.7);
    animation: bubbleUp 5s linear forwards;
  }

  @keyframes bubbleUp {
    from { transform: translateY(0) scale(1); opacity: 1; }
    to { transform: translateY(-120vh) scale(1.5); opacity: 0; }
  }
</style>
</head>
<body>

<audio id="bgMusic" loop>
  <source src="https://cdn.pixabay.com/audio/2022/10/25/audio_7b0b4a3f52.mp3" type="audio/mpeg">
</audio>

<audio id="yaySound">
  <source src="https://cdn.pixabay.com/audio/2022/03/15/audio_9f8b9b3f7b.mp3" type="audio/mpeg">
</audio>

<div class="popup">
  <div class="dolls"></div>
  <h1>Be my Valentine </h1>
  <div class="dolls"></div>

  <div class="buttons">
    <button onclick="sayYes()">Yes </button>
    <button id="noBtn" onclick="moveNo()">No </button>
  </div>

  <div id="message" class="success"></div>
</div>

<script>
  const bgMusic = document.getElementById("bgMusic");
  const yaySound = document.getElementById("yaySound");

  document.body.addEventListener("click", () => {
    bgMusic.play().catch(() => {});
  }, { once: true });

  function sayYes() {
    document.getElementById("message").innerText = "YAY! You made me the happiest ";
    yaySound.play();
    createBalloons();
    createBubbles();
  }

  function moveNo() {
    const noBtn = document.getElementById("noBtn");
    const x = Math.random() * (window.innerWidth - 100);
    const y = Math.random() * (window.innerHeight - 100);
    noBtn.style.position = "absolute";
    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";
  }

  function createBalloons() {
    for (let i = 0; i < 80; i++) {
      const balloon = document.createElement("div");
      balloon.className = "balloon";
      balloon.style.left = Math.random() * 100 + "vw";
      balloon.style.background = randomColor();
      balloon.style.animationDuration = (4 + Math.random() * 4) + "s";
      balloon.style.width = (30 + Math.random() * 25) + "px";
      balloon.style.height = (40 + Math.random() * 35) + "px";
      document.body.appendChild(balloon);
      setTimeout(() => balloon.remove(), 8000);
    }
  }

  function createBubbles() {
    for (let i = 0; i < 100; i++) {
      const bubble = document.createElement("div");
      bubble.className = "bubble";
      bubble.style.left = Math.random() * 100 + "vw";
      const size = 10 + Math.random() * 25;
      bubble.style.width = size + "px";
      bubble.style.height = size + "px";
      bubble.style.animationDuration = (3 + Math.random() * 4) + "s";
      document.body.appendChild(bubble);
      setTimeout(() => bubble.remove(), 7000);
    }
  }

  function randomColor() {
    const colors = ["#ff69b4", "#ff4081", "#f50057", "#ec407a", "#f06292", "#ba68c8", "#64b5f6", "#4db6ac", "#ffd54f"];
    return colors[Math.floor(Math.random() * colors.length)];
  }
</script>

</body>
</html>
