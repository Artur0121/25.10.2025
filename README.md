

<html lang="hy">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Դարի Հրավիրյալ</title>
<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Montserrat:wght@400;700&display=swap" rel="stylesheet">
<style>
  body {
    margin: 0;
    font-family: 'Montserrat', sans-serif;
    background: linear-gradient(to bottom, #fff8f0, #fbe8f1);
    overflow-x: hidden;
    color: #3e2c2a;
    perspective: 1000px;
  }

  a { text-decoration: none; color: inherit; }

  .invitation-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 50px 20px;
  }

  .invitation-header {
    text-align: center;
    margin-bottom: 40px;
  }

  .invitation-header h1 {
    font-family: 'Great Vibes', cursive;
    font-size: 4rem;
    margin: 0;
    color: #b33c86;
    text-shadow: 1px 1px 5px rgba(0,0,0,0.2);
  }

  .invitation-header p {
    font-size: 1.3rem;
    color: #7a4a6b;
    margin-top: 10px;
    font-style: italic;
  }

  #countdown {
    margin-top: 20px;
    font-size: 1.5rem;
    color: #b33c86;
    font-weight: 600;
  }

  /* 3D Slideshow Cards */
  .slideshow {
    display: flex;
    justify-content: center;
    perspective: 1200px;
    margin-bottom: 50px;
    gap: 20px;
    flex-wrap: wrap;
  }

  .slide-card {
    width: 250px;
    height: 350px;
    border-radius: 20px;
    overflow: hidden;
    background: white;
    box-shadow: 0 20px 40px rgba(0,0,0,0.2);
    transform-style: preserve-3d;
    transition: transform 0.5s;
  }

  .slide-card img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    transition: transform 0.5s;
  }

  .slide-card:hover {
    transform: rotateY(15deg) rotateX(10deg);
  }

  /* Schedule / Locations */
  .schedule {
    max-width: 700px;
    text-align: center;
  }

  .schedule h2 {
    font-family: 'Great Vibes', cursive;
    font-size: 2.5rem;
    margin-bottom: 20px;
    color: #b33c86;
  }

  .schedule .event {
    background: rgba(255,255,255,0.85);
    margin: 20px 0;
    padding: 20px;
    border-radius: 15px;
    box-shadow: 0 8px 20px rgba(0,0,0,0.15);
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .event h3 {
    margin: 0 0 10px 0;
    font-size: 1.5rem;
    color: #7a4a6b;
  }

  .event p {
    margin: 5px 0;
  }

  .event img {
    width: 100%;
    max-width: 400px;
    border-radius: 15px;
    margin-bottom: 10px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
  }

  .event a {
    display: inline-block;
    margin-top: 10px;
    padding: 8px 18px;
    background: #b33c86;
    color: white;
    border-radius: 8px;
    transition: 0.3s;
  }

  .event a:hover { background: #8e2a64; }

  footer {
    text-align: center;
    padding: 30px 20px;
    font-size: 1rem;
    color: #7a4a6b;
  }

  /* Երաժշտության կոճակ (fixed վերևի մասում) */
  #musicBtn {
    position: fixed;
    top: 20px;
    right: 20px;
    background: #b33c86;
    border: none;
    border-radius: 50%;
    width: 60px;
    height: 60px;
    font-size: 24px;
    color: white;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(0,0,0,0.4);
    z-index: 1000;
    transition: transform 0.3s;
  }

  #musicBtn:hover {
    transform: scale(1.1);
  }
</style>
</head>
<body>

<!-- Երաժշտություն -->
<audio id="bgMusic" loop>
  <source src="music.mp3" type="audio/mpeg">
</audio>
<button id="musicBtn">🎵</button>

<div class="invitation-container">
  <div class="invitation-header">
    <h1>Վարդան &amp; Սեդա</h1>
    <p>Սիրով հրավիրում ենք Ձեզ մեր հարսանիքին</p>
    <div id="countdown"></div>
  </div>

  <!-- 3D Slideshow -->
  <div class="slideshow">
    <div class="slide-card"><img src="IMG-20250923-WA0003.jpg" alt=""></div>

  

  <!-- Schedule -->
  <div class="schedule">
    <h2>Ծրագիր</h2>
    <div class="event">
      <h3>⛪ Եկեղեցի</h3>
      <img src="church.jpg" alt="Եկեղեցի">
      <p>Ժամը՝ 15:00</p>
      <a href="https://maps.app.goo.gl/ktm925BiCbS7feqo7" target="_blank"> Բացել Maps-ում</a>
    </div>
    <div class="event">
      <h3>🍽️ Ռեստորան</h3>
      <img src="restaurant.jpg" alt="Ռեստորան">
      <p>Ժամը՝ 17:00</p>
      <a href="https://maps.app.goo.gl/MfGsyDTba316jarD7" target="_blank">Բացել Maps-ում</a>
    </div>
  </div>

  <footer>
    Սիրով սպասում ենք քեզ 🌸
  </footer>
</div>

<script>
  // Հետհաշվարկ
  const weddingDate = new Date("2025-10-25 00:00:00").getTime();
  const countdown = document.getElementById("countdown");

  setInterval(() => {
    const now = new Date().getTime();
    const distance = weddingDate - now;
    if(distance < 0){
      countdown.innerHTML = "Օրը եկել է 💖";
      return;
    }
    const days = Math.floor(distance / (1000*60*60*24));
    const hours = Math.floor((distance % (1000*60*60*24)) / (1000*60*60));
    const minutes = Math.floor((distance % (1000*60*60)) / (1000*60));
    const seconds = Math.floor((distance % (1000*60)) / 1000);
    countdown.innerHTML = `${days} օր ${hours} ժ ${minutes} ր ${seconds} վ`;
  },1000);

  // Երաժշտության կոճակ
  const musicBtn = document.getElementById("musicBtn");
  const bgMusic = document.getElementById("bgMusic");
  let isPlaying = false;
  musicBtn.addEventListener("click", () => {
    if(!isPlaying){
      bgMusic.play();
      musicBtn.innerHTML = "⏸";
    } else {
      bgMusic.pause();
      musicBtn.innerHTML = "🎵";
    }
    isPlaying = !isPlaying;
  });
</script>

</body>
</html>
