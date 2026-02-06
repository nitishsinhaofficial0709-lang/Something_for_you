
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
  color:white;
  display:flex;
  justify-content:center;
  align-items:center;
  text-align:center;
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
  padding:35px;
  border-radius:25px;
  max-width:420px;
}

/* roses */
.rose{
  position:absolute;
  font-size:22px;
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

/* heart task */
#heart{
  font-size:70px;
  cursor:pointer;
  animation:pulse 1s infinite;
}
@keyframes pulse{
  50%{transform:scale(1.2);}
}

/* rose drag */
#finalRose{
  font-size:70px;
  cursor:grab;
}

/* fade */
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
  <h2 id="text"></h2>
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

/* typing letter */
const msg=
"Happy Rose Day Ankita 🌹❤️\n\nBefore I give you your rose…\nI have something fun for you 😌\n\nComplete the tasks below 👇";

let i=0;
function type(){
  if(i<msg.length){
    text.innerHTML+=msg.charAt(i++);
    setTimeout(type,35);
  } else {
    heartTask();
  }
}

/* falling roses + sparkles */
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

/* TASK 1 */
let taps=0;
function heartTask(){
  task.innerHTML=`
    <p>💖 Task 1: Tap the heart 3 times 💖</p>
    <div id="heart">❤️</div>
  `;
  heart.onclick=()=>{
    taps++;
    if(taps===3) roseTask();
  };
}

/* TASK 2 */
function roseTask(){
  task.innerHTML=`
    <p>🌹 Task 2: Drag the rose to your heart 🌹</p>
    <div id="finalRose" draggable="true">🌹</div>
  `;
  finalRose.ondragend=finalSurprise;
}

/* FINAL */
function finalSurprise(){
  document.body.innerHTML=`
  <div class="fade" style="padding:30px">
    <h1 style="font-size:42px">🌹 Happy Rose Day Ankita 🌹</h1>
    <p style="font-size:20px">
      This rose is not just a flower…<br>
      It’s my love, my respect, my promise.
    </p>
    <h2>Will you accept this rose<br>and be my forever? 💍</h2>
    <h3>— Nitish ❤️</h3>
    <img src="https://media.giphy.com/media/26BRv0ThflsHCqDrG/giphy.gif" width="260">
  </div>
  `;
}
</script>

</body>
</html>
