
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

/* intro */
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
  padding:30px;
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

/* sparkle */
.spark{
  position:absolute;
  animation:twinkle 2s infinite;
}
@keyframes twinkle{50%{opacity:0.2;}}

/* buttons */
button{
  padding:12px 22px;
  margin:10px;
  border:none;
  border-radius:12px;
  font-size:16px;
  cursor:pointer;
}

.primary{background:#ff4d6d;color:white;}
.secondary{background:#bbb;position:absolute;}

/* heart pulse */
#heart{
  font-size:70px;
  cursor:pointer;
  animation:pulse 1s infinite;
}
@keyframes pulse{50%{transform:scale(1.2);}}

/* moving rose */
#moveRose{
  font-size:50px;
  cursor:pointer;
  position:absolute;
}

.fade{animation:fade 1.5s;}
@keyframes fade{from{opacity:0}to{opacity:1}}
</style>
</head>

<body>

<div id="intro">🌹 Tap to start your Rose Day surprise 🌹</div>

<audio id="music" loop>
<source src="https://cdn.pixabay.com/audio/2022/03/15/audio_c8c8a73467.mp3">
</audio>

<div class="box" id="box">
  <h3 id="text"></h3>
  <div id="task"></div>
</div>

<script>

/* start */
intro.onclick=()=>{
  intro.style.display="none";
  box.style.display="block";
  music.play();
  type();
};

/* typing message */
const msg =
"Happy Rose Day Ankita 🌹❤️\n\nI made something special for you.\nBut first… complete my little challenges 😄";

let i=0;
function type(){
  if(i<msg.length){
    text.innerHTML+=msg.charAt(i++);
    setTimeout(type,30);
  } else {
    heartTask();
  }
}

/* background animation */
for(let j=0;j<30;j++){
  let r=document.createElement("div");
  r.innerHTML="🌹";
  r.className="rose";
  r.style.left=Math.random()*100+"vw";
  r.style.animationDuration=(3+Math.random()*5)+"s";
  document.body.appendChild(r);
}
for(let s=0;s<20;s++){
  let sp=document.createElement("div");
  sp.innerHTML="✨";
  sp.className="spark";
  sp.style.left=Math.random()*100+"vw";
  sp.style.top=Math.random()*100+"vh";
  document.body.appendChild(sp);
}

/* TASK 1 - tap heart */
let taps=0;
function heartTask(){
  task.innerHTML="<p>💖 Tap the heart 3 times</p><div id='heart'>❤️</div>";
  heart.onclick=()=>{
    taps++;
    if(taps===3) movingRoseTask();
  }
}

/* TASK 2 - catch rose */
function movingRoseTask(){
  task.innerHTML="<p>🌹 Catch the rose 😆</p><div id='moveRose'>🌹</div>";

  const r=document.getElementById("moveRose");

  r.onmouseover=()=>{
    r.style.top=Math.random()*window.innerHeight+"px";
    r.style.left=Math.random()*window.innerWidth+"px";
  };

  r.onclick=buttonStage;
}

/* buttons stage */
function buttonStage(){
  task.innerHTML=`
  <p>Ready for your gift? 🎁</p>
  <button class="primary" id="open">Open your gift ❤️</button>
  <button class="secondary" id="later">Not now 🙈</button>
  `;

  later.onmouseover=()=>{
    later.style.top=Math.random()*window.innerHeight+"px";
    later.style.left=Math.random()*window.innerWidth+"px";
  };

  open.onclick=finalSurprise;
}

/* FINAL PROPOSAL */
function finalSurprise(){
  document.body.innerHTML=`
  <div class="fade" style="padding:30px">
    <h1 style="font-size:40px">🌹 For Ankita 🌹</h1>
    <h2>You are my today, tomorrow & forever ❤️</h2>
    <p>This rose carries my whole heart.</p>
    <h2>Will you stay with me forever? 💍</h2>
    <h3>— Nitish</h3>
    <br>
    <img src="https://media.giphy.com/media/l0HlBO7eyXzSZkJri/giphy.gif" width="260">
  </div>
  `;
}

</script>

</body>
</html>
