
<html>
<head>
<title>Rose Day Surprise 🌹</title>

<style>
body{
  margin:0;
  height:100vh;
  font-family:'Poppins',sans-serif;
  background:linear-gradient(135deg,#ff758c,#ffb199);
  overflow:hidden;
  display:flex;
  justify-content:center;
  align-items:center;
  text-align:center;
  color:white;
}

/* intro screen */
#intro{
  position:absolute;
  width:100%;
  height:100%;
  display:flex;
  justify-content:center;
  align-items:center;
  font-size:26px;
  cursor:pointer;
}

/* card */
.box{
  display:none;
  background:rgba(0,0,0,0.6);
  padding:35px;
  border-radius:25px;
  max-width:420px;
}

/* falling roses */
.rose{
  position:absolute;
  animation:fall linear infinite;
}

@keyframes fall{
  from{transform:translateY(-10vh);}
  to{transform:translateY(110vh);}
}

/* sparkles */
.spark{
  position:absolute;
  color:#fff;
  animation:twinkle 2s infinite;
}

@keyframes twinkle{
  50%{opacity:0.2;}
}

/* envelope */
#envelope{
  font-size:70px;
  cursor:pointer;
  display:none;
  animation:bounce 1.2s infinite;
}

@keyframes bounce{
  50%{transform:translateY(-10px);}
}

.fade{animation:fade 1.5s;}
@keyframes fade{from{opacity:0}to{opacity:1}}
</style>
</head>

<body>

<div id="intro">🌹 Tap to open your Rose Day surprise 🌹</div>

<!-- Romantic music -->
<audio id="music" loop>
<source src="https://cdn.pixabay.com/audio/2022/03/15/audio_c8c8a73467.mp3">
</audio>

<div class="box" id="box">
  <h2 id="text"></h2>
  <h2 id="countdown"></h2>
  <div id="envelope">💌</div>
</div>

<script>

/* start */
document.getElementById("intro").onclick=function(){
  this.style.display="none";
  document.getElementById("box").style.display="block";
  document.getElementById("music").play();
}

/* typing letter */
const msg =
"Happy Rose Day Ankita 🌹❤️\n\nSome people give roses…\nBut I wanted to give you something special.\nBecause you are the most special part of my life.\n\nWait for your surprise...";

let i=0;
function type(){
  if(i<msg.length){
    document.getElementById("text").innerHTML+=msg.charAt(i);
    i++;
    setTimeout(type,35);
  } else {
    startCountdown();
  }
}
type();

/* countdown */
function startCountdown(){
  let c=3;
  let el=document.getElementById("countdown");

  let timer=setInterval(()=>{
    el.innerHTML=c;
    c--;
    if(c<0){
      clearInterval(timer);
      el.innerHTML="Open it ❤️";
      document.getElementById("envelope").style.display="block";
    }
  },800);
}

/* roses */
for(let j=0;j<35;j++){
  let r=document.createElement("div");
  r.innerHTML="🌹";
  r.className="rose";
  r.style.left=Math.random()*100+"vw";
  r.style.fontSize=(15+Math.random()*20)+"px";
  r.style.animationDuration=(3+Math.random()*5)+"s";
  document.body.appendChild(r);
}

/* sparkles */
for(let s=0;s<25;s++){
  let sp=document.createElement("div");
  sp.innerHTML="✨";
  sp.className="spark";
  sp.style.left=Math.random()*100+"vw";
  sp.style.top=Math.random()*100+"vh";
  document.body.appendChild(sp);
}

/* final surprise */
document.getElementById("envelope").onclick=function(){
  document.body.innerHTML=`
  <div class="fade" style="padding:30px">
    <h1 style="font-size:40px">For You Ankita ❤️</h1>
    <p style="font-size:20px">
      You are my today, tomorrow and forever 🌹<br>
      Thank you for being my happiness.
    </p>
    <h2>Forever yours,<br>Nitish 💍</h2>
    <br>
    <img src="https://media.giphy.com/media/l0HlBO7eyXzSZkJri/giphy.gif" width="260">
  </div>
  `;
}
</script>

</body>
</html>
