<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="utf-8"/>
<title>Lucas & Deniene - Convite de Casamento</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500&family=Roboto&display=swap');
* { box-sizing: border-box; }
html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  overflow-x: hidden;
  min-width: 1024px;
}
body {
  font-family: 'Roboto', sans-serif;
  color: #001f3f;
  background-image: url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRPYzYAwnOatRYLcJjtyXPUyCYC0y3Dgo31z9kw7SppT8XSNL5ybhB0kqw&s=10');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.envelope {
  width: 520px;
  height: 340px;
  background-color: #001f3f;
  position: relative;
  transform-style: preserve-3d;
  perspective: 1000px;
  border-radius: 8px;
  box-shadow: 0 0 25px rgba(0, 31, 63, 0.5);
  z-index: 2;
  transition: opacity 0.5s ease-out;
}
.flap {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: #001f3f;
  transform-origin: top;
  z-index: 3;
  border-radius: 8px;
}
.seal {
  width: 80px;
  height: 80px;
  background-color: #c0392b;
  border-radius: 50%;
  position: absolute;
  top: 100px;
  left: calc(50% - 40px);
  z-index: 4;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-size: 1.2em;
  color: white;
  box-shadow: 0 0 8px rgba(0,0,0,0.3);
  font-family: 'Playfair Display', serif;
  line-height: 1.2;
  text-align: center;
  transition: transform 1s ease, opacity 1s ease;
}
.seal span {
  font-size: 1.5em;
}
.seal div {
  font-size: 1.2em;
}
.seal.sair {
  transform: translateY(-80px);
  opacity: 0;
}
@keyframes flapOpen {
  0% { transform: rotateX(0deg); }
  100% { transform: rotateX(-120deg); }
}
@keyframes openEnvelope {
  0% { transform: scale(1); }
  100% { transform: scale(1.1) translateY(-100px); }
}
.container {
  opacity: 0;
  transform: translateY(80px);
  transition: opacity 1s ease-out, transform 1s ease-out;
  width: 950px;
  max-width: 95%;
  background-color: rgba(255, 255, 255, 0.95);
  background-image: url('https://www.transparenttextures.com/patterns/paper-fibers.png');
  background-repeat: repeat;
  padding: 70px 60px;
  border: 2px solid #001f3f;
  border-radius: 12px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  position: absolute;
  text-align: center;
  z-index: 1;
  pointer-events: none;
}
.container.mostrar {
  opacity: 1;
  transform: translateY(0);
  pointer-events: all;
}
.monogram {
  font-family: 'Playfair Display', serif;
  font-size: 4em;
  color: #001f3f;
  margin-bottom: 10px;
  letter-spacing: 2px;
}
h1 {
  font-family: 'Playfair Display', serif;
  font-size: 3.4em;
  color: #001f3f;
  margin-bottom: 0.2em;
}
h2 {
  font-weight: normal;
  font-size: 1.7em;
  color: #001f3f;
}
.message {
  font-style: italic;
  font-size: 1.4em;
  color: #001f3f;
  margin: 25px 0;
}
.info {
  margin: 40px 0;
  color: #001f3f;
}
.info .data-bloco {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 30px;
  flex-wrap: wrap;
  font-family: 'Playfair Display', serif;
  font-size: 1.3em;
}
.info .data-centro {
  border-left: 1px solid #ccc;
  border-right: 1px solid #ccc;
  padding: 0 20px;
}
.local {
  margin-top: 20px;
  font-size: 1.2em;
  color: #001f3f;
}
.footer {
  margin-top: 40px;
  font-size: 1.1em;
  color: #001f3f;
}
.petal {
  position: fixed;
  top: -50px;
  width: 20px;
  height: 20px;
  background-color: white;
  border-radius: 50%;
  opacity: 0.8;
  animation: fall 6s linear infinite;
  pointer-events: none;
  z-index: 5;
}
.petal.blue {
  background-color: #001f3f;
}
@keyframes fall {
  0% { transform: translateY(0) rotate(0deg); opacity: 1; }
  100% { transform: translateY(100vh) rotate(360deg); opacity: 0; }
}
.rsvp-button {
  margin-top: 20px;
  padding: 14px 32px;
  font-size: 1.3em;
  background-color: #001f3f;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background 0.3s;
}
.rsvp-button:hover {
  background-color: #003366;
}
</style>
</head>
<body>
<audio id="openSound" preload="auto" src="https://app.filemail.com/d/rzwmuohatucwyvj"></audio>
<audio id="bgMusic" preload="auto" loop autoplay>
  <source src="https://www.bensound.com/bensound-music/bensound-love.mp3" type="audio/mpeg">
</audio>
<div class="envelope" id="envelope">
  <div class="flap"></div>
  <div class="seal" id="seal"><span>❤</span><div>L & D</div></div>
</div>
<button class="rsvp-button" id="openEnvelopeBtn">Abrir Carta</button>
<div class="container" id="invitationContainer">
  <div class="monogram">L & D</div>
  <h1>Lucas & Deniene</h1>
  <h2>Convidam você para um dia inesquecível</h2>
  <p class="message">"Assim, eles já não são dois, mas sim uma só carne. Portanto, o que Deus uniu, ninguém o separe."<br/><em>Mateus 19:6</em></p>
  <div class="info">
    <div class="data-bloco">
      <div style="text-align: center;">SÁBADO</div>
      <div class="data-centro" style="text-align: center;">
        <div style="font-size: 0.8em;">JUNHO</div>
        <div style="font-size: 1.8em;">07</div>
        <div style="letter-spacing: 2px; font-size: 0.8em;">2025</div>
      </div>
      <div style="text-align: center;">19 HORAS</div>
    </div>
    <div class="local">Rua Olímpio de Góes / Igreja Presbiteriana Renovada / Nova Ponte-MG</div>
  </div>
  <div style="display: flex; justify-content: center; gap: 40px; margin-top: 30px;">
    <a href="https://maps.app.goo.gl/MRPgSwZVadWqGkfE9" target="_blank" style="text-align: center; text-decoration: none; color: #001f3f;">
      <div style="width: 80px; height: 80px; background-color: #d0e3f5; border-radius: 50%; display: flex; align-items: center; justify-content: center; margin: 0 auto;">
        <img src="https://cdn-icons-png.flaticon.com/512/684/684908.png" alt="Localização" style="width: 36px; height: 36px;">
      </div>
      <div style="margin-top: 10px; font-weight: bold;">COMO<br>CHEGAR</div>
    </a>
    <a href="https://nysyj9aq.forms.app/confirmacao-de-presenca-casamento" target="_blank" style="text-align: center; text-decoration: none; color: #001f3f;">
      <div style="width: 80px; height: 80px; background-color: #d0e3f5; border-radius: 50%; display: flex; align-items: center; justify-content: center; margin: 0 auto;">
        <img src="https://cdn-icons-png.flaticon.com/512/190/190411.png" alt="Confirmação" style="width: 36px; height: 36px;">
      </div>
      <div style="margin-top: 10px; font-weight: bold;">CONFIRMAR<br>PRESENÇA</div>
    </a>
  </div>
  <div class="footer">Aguardamos com alegria sua presença neste momento especial!</div>
  <div style="margin-top: 40px; font-style: italic; font-size: 1.3em;">Com amor, Lucas & Deniene</div>
</div>
<script>
const openSound = document.getElementById("openSound");
const envelope = document.getElementById("envelope");
const button = document.getElementById("openEnvelopeBtn");
const container = document.getElementById("invitationContainer");
const seal = document.getElementById("seal");

button.addEventListener("click", function () {
  envelope.style.animation = "openEnvelope 2s ease-out forwards";
  document.querySelector(".flap").style.animation = "flapOpen 2s ease-in-out forwards";
  seal.classList.add("sair");
  openSound.play();

  setTimeout(() => {
    envelope.style.opacity = 0;
    envelope.style.zIndex = -1;
    button.style.display = "none";
  }, 2200);

  setTimeout(() => {
    container.classList.add("mostrar");
    const bgMusic = document.getElementById("bgMusic");
    bgMusic.volume = 0.3;
    bgMusic.play().catch(() => {});
    startPetals();
  }, 2500);
});

function startPetals() {
  const container = document.getElementById("petalContainer");
  setInterval(() => {
    const petal = document.createElement("div");
    petal.classList.add("petal");
    if (Math.random() > 0.5) petal.classList.add("blue");
    petal.style.left = Math.random() * 100 + "vw";
    petal.style.animationDuration = (Math.random() * 3 + 4) + "s";
    container.appendChild(petal);
    setTimeout(() => {
      petal.remove();
    }, 8000);
  }, 300);
}
</script>
<div id="petalContainer"></div>
</body>
</html>
