<!doctype html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Will you be my Valentine Arwa ji 🌹💗</title>

<style>
body{
  margin:0;
  min-height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  font-family:system-ui, -apple-system, Segoe UI, Roboto;
  background:linear-gradient(135deg,#ffe6f0,#e6f7ff);
  overflow:hidden;
}

.card{
  background:white;
  padding:30px;
  border-radius:25px;
  box-shadow:0 20px 45px rgba(0,0,0,.15);
  text-align:center;
  width:min(900px,92vw);
  position:relative;
}

.title{
  color:#d40000;
  font-size:clamp(28px,4.5vw,46px);
  font-weight:900;
  text-shadow:0 5px 15px rgba(212,0,0,0.3);
  white-space:nowrap;
}

.gif{
  width:min(380px,85vw);
  margin:20px auto;
  border-radius:20px;
  overflow:hidden;
  box-shadow:0 18px 40px rgba(255,77,141,.3);
}
.gif img{
  width:100%;
  display:block;
}

.controls{
  display:flex;
  justify-content:center;
  gap:15px;
  flex-wrap:wrap;
  min-height:70px;
}

button{
  border:0;
  padding:14px 24px;
  border-radius:999px;
  font-weight:bold;
  cursor:pointer;
  font-size:16px;
  transition:.2s ease;
}

.yes{
  background:linear-gradient(135deg,#ff4d8d,#ff85a1);
  color:white;
}

.no{
  background:white;
  border:2px solid #ddd;
  position:relative;
}

.result{
  display:none;
  margin-top:20px;
}

.result img{
  width:min(380px,85vw);
  border-radius:20px;
  margin-top:15px;
}
</style>
</head>

<body>

<div class="card" id="card">

  <h1 class="title">Will you be my Valentine Arwa ji 🌹💗</h1>

  <div class="gif">
    <img id="mainGif"
    src="https://media.giphy.com/media/3ohhwk0Y4kHh3LJjzq/giphy.gif"
    alt="Jake proposing">
  </div>

  <div class="controls" id="controls">
    <button class="yes" id="yesBtn">YES 💖</button>
    <button class="no" id="noBtn">No 🙃</button>
  </div>

  <div class="result" id="result">
    <h2 style="color:#d40000;">NOINE NOINE!!! 🥹💞</h2>
    <p>Arwa ji said YES. Legendary love story unlocked 💍💗</p>
    <img src="https://media.giphy.com/media/26Fxy3Iz1ari8oytO/giphy.gif">
  </div>

</div>

<script>
let noBtn = document.getElementById("noBtn");
let yesBtn = document.getElementById("yesBtn");
let controls = document.getElementById("controls");
let mainGif = document.getElementById("mainGif");
let card = document.getElementById("card");

let attempts = 0;
let teleportMode = false;

function sayYes(){
  document.getElementById("result").style.display="block";
  controls.style.display="none";
  mainGif.src = "https://media.giphy.com/media/l0MYt5jPR6QX5pnqM/giphy.gif";
}

yesBtn.addEventListener("click", sayYes);

function teleportButton(){
  if(!teleportMode) return;

  const cardRect = card.getBoundingClientRect();
  const btnRect = noBtn.getBoundingClientRect();

  const maxX = cardRect.width - btnRect.width;
  const maxY = cardRect.height - btnRect.height;

  const randomX = Math.random() * maxX;
  const randomY = Math.random() * maxY;

  noBtn.style.position = "absolute";
  noBtn.style.left = randomX + "px";
  noBtn.style.top = randomY + "px";
}

noBtn.addEventListener("click", function(){

  attempts++;

  // First click → show worstdate gif + activate teleport
  if(attempts === 1){
    mainGif.src = "worstdate.gif";
    teleportMode = true;
  }

  // Add extra YES buttons
  let newYes = document.createElement("button");
  newYes.className="yes";
  newYes.innerText="YES PLEASE 💘";
  newYes.onclick=sayYes;
  controls.appendChild(newYes);

  // Make YES grow
  yesBtn.style.transform = "scale(" + (1 + attempts*0.15) + ")";

  teleportButton();
});

// Teleport when hovered after first click
noBtn.addEventListener("mouseenter", teleportButton);

</script>

</body>
</html>
