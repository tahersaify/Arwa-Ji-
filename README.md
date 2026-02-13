<!doctype html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Will you be my Valentine Arwa ji 🌹💗</title>

<style>
:root{
  --brightRed:#d10000;
  --rose1:#ff4d8d;
  --rose2:#ff85a1;
  --card:rgba(255,255,255,.92);
}

*{box-sizing:border-box;}

body{
  margin:0;
  height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial;
  background:url("https://images.unsplash.com/photo-1518199266791-5375a83190b7?auto=format&fit=crop&w=1920&q=80") center/cover no-repeat;
  overflow:hidden;
}

.overlay{
  position:absolute;
  inset:0;
  background:rgba(150,0,0,0.25);
  backdrop-filter:blur(2px);
}

/* 🌹 Falling petals */
.petals{
  position:fixed;
  inset:0;
  pointer-events:none;
  z-index:1;
}
.petal{
  position:absolute;
  top:-10vh;
  font-size:22px;
  opacity:0;
  animation: fall var(--dur) linear infinite;
}
@keyframes fall{
  0%{transform:translateX(var(--x)) translateY(-12vh);opacity:0;}
  10%{opacity:.9;}
  100%{transform:translateX(calc(var(--x)+var(--drift))) translateY(112vh);opacity:0;}
}

.card{
  width:min(780px,92vw);
  background:var(--card);
  border-radius:20px;
  padding:34px 34px 30px;
  text-align:center;
  position:relative;
  z-index:2;
}

.title{
  color:var(--brightRed);
  font-weight:900;
  font-size:clamp(22px,3.8vw,40px);
  line-height:1.15;
  margin:0;
  white-space:nowrap;
}

.caption{
  font-weight:700;
  font-size:16px;
  min-height:22px;
  margin:12px 0 22px;
}

.frame{
  width:min(420px,90%);
  margin:0 auto 22px;
  border-radius:18px;
  overflow:hidden;
}
.frame img{
  width:100%;
  display:block;
}

.controls{
  display:flex;
  justify-content:center;
  gap:18px;
  margin-bottom:10px;
}

button{
  border:0;
  padding:12px 28px;
  border-radius:999px;
  font-weight:700;
  font-size:15px;
  cursor:pointer;
  transition:.2s ease;
}

.yes{
  color:#fff;
  background:linear-gradient(135deg,var(--rose1),var(--rose2));
}

.no{
  background:#fff;
  border:1px solid #ccc;
}

/* ❤️ Signature */
.signature{
  position:absolute;
  right:18px;
  bottom:14px;
  font-size:15px;
  font-weight:900;
  color:var(--brightRed);
}

.heart{
  position:fixed;
  pointer-events:none;
  animation:floatUp 2.4s ease forwards;
  z-index:3;
}
@keyframes floatUp{
  0%{transform:translate(var(--x),110vh);opacity:0;}
  10%{opacity:1;}
  100%{transform:translate(calc(var(--x)+40px),-20vh);opacity:0;}
}
</style>
</head>

<body>
<div class="overlay"></div>
<div class="petals" id="petals"></div>

<div class="card" id="card">
  <h1 class="title">Will you be my Valentine Arwa ji 🌹💗</h1>

  <p class="caption" id="caption"></p>

  <div class="frame">
    <img id="mainGif"
      src="https://media.tenor.com/4bV9ylEOWpgAAAAj/bubu-dudu-sseeyall.gif">
  </div>

  <div class="controls">
    <button class="yes" id="yesBtn">Yes 💖</button>
    <button class="no" id="noBtn">No 🙃</button>
  </div>

  <div class="signature">- Taher ❤️</div>
</div>

<script>
const card=document.getElementById("card");
const yesBtn=document.getElementById("yesBtn");
const noBtn=document.getElementById("noBtn");
const mainGif=document.getElementById("mainGif");
const caption=document.getElementById("caption");
const petalsLayer=document.getElementById("petals");

let noActivated=false;

function showCaption(text){
  caption.innerHTML="<strong>"+text+"</strong>";
}

function heartsBurst(count=25){
  const hearts=["💗","💖","💞","💕","❤️"];
  for(let i=0;i<count;i++){
    const h=document.createElement("div");
    h.className="heart";
    h.textContent=hearts[Math.floor(Math.random()*hearts.length)];
    h.style.setProperty("--x",(Math.random()*100)+"vw");
    h.style.fontSize=(16+Math.random()*18)+"px";
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),2400);
  }
}

function makePetals(count=16){
  const symbols=["🌹","🌸"];
  for(let i=0;i<count;i++){
    const p=document.createElement("div");
    p.className="petal";
    p.textContent=symbols[Math.floor(Math.random()*symbols.length)];
    p.style.setProperty("--x",(Math.random()*100)+"vw");
    p.style.setProperty("--drift",(Math.random()*60-30)+"px");
    p.style.setProperty("--dur",(14+Math.random()*6)+"s");
    p.style.fontSize=(16+Math.random()*14)+"px";
    p.style.animationDelay=(-Math.random()*10)+"s";
    petalsLayer.appendChild(p);
  }
}
makePetals();

yesBtn.addEventListener("click",()=>{
  mainGif.src="https://media.tenor.com/5XOehZUJ1MAAAAAj/cute-cat-couple.gif";
  showCaption("Thank you, wifey — you are the cutest 🥺💖✨");
  heartsBurst();
  yesBtn.style.display="none";
  noBtn.style.display="none";
});

function runNoWithinRange(){
  const rect=card.getBoundingClientRect();
  const minX=Math.max(20,rect.left-80);
  const minY=Math.max(20,rect.top-80);
  const maxX=Math.min(window.innerWidth-120,rect.right+80);
  const maxY=Math.min(window.innerHeight-60,rect.bottom+80);

  noBtn.style.position="fixed";
  noBtn.style.left=(minX+Math.random()*(maxX-minX))+"px";
  noBtn.style.top=(minY+Math.random()*(maxY-minY))+"px";
}

noBtn.addEventListener("click",()=>{
  if(noActivated) return;
  noActivated=true;
  mainGif.src="https://media1.tenor.com/m/lJMs4YFWUgAAAAAd/big-bang-theory-sheldon-cooper.gif";
  showCaption("I am sad, try again 😒");
  noBtn.style.cursor="not-allowed";
});

noBtn.addEventListener("mouseenter",()=>{
  if(noActivated) runNoWithinRange();
});
</script>

</body>
</html>
