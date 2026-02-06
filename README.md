<!DOCTYPE html>
<html>
<head>
<title>For Ankita 🌹</title>

<style>
body{
  margin:0;
  height:100vh;
  font-family:'Poppins',sans-serif;
  background:linear-gradient(135deg,#ff758c,#ffb199);
  display:flex;
  justify-content:center;
  align-items:center;
  overflow:hidden;
  color:white;
  text-align:center;
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
  background:rgba(0,0,0,0.65);
  padding:35px;
  border-radius:25px;
  max-width:420px;
}

/* bounce */
.bounce{
  animation:bounce 1.2s infinite;
}
@keyframes bounce{
  50%{transform:translateY(-10px);}
}

.fade{animation:fade 1s;}
@keyframes fade{from{opacity:0}to{opacity:1}}
</style>
</head>

<body>

<div id="intro">🌹 Tap to open your surprise 🌹</div>

<audio id="music" loop>
<source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3">
</audio>

<div class="box" id="mainBox">
  <h2 id="text"></h2>
</div>

<script>

/* falling roses */
for(let j=0;j<40;j++){
  let r=document.createElement("div");
  r.innerHTML="🌹";
  r.className="rose";
  r.style.left=Math.random()*100+"vw";
  r.style.fontSize=(15+Math.random()*20)+"px";
  r.style.animationDuration=(3+Math.random()*5)+"s";
  document.body.appendChild(r);
}

const box=document.getElementById("mainBox");

/* start */
document.getElementById("intro").onclick=function(){
  this.style.display="none";
  box.style.display="block";
  document.getElementById("music").play();
  typeLetter();
}

/* typing message */
const msg =
"Happy Rose Day Ankita ❤️\n\nI didn’t want to just send a flower…\nI wanted to send something special…";

let i=0;
function typeLetter(){
  if(i<msg.length){
    document.getElementById("text").innerHTML+=msg.charAt(i);
    i++;
    setTimeout(typeLetter,35);
  }else{
    setTimeout(showReasons,1200);
  }
}

/* suspense + reasons */
function showReasons(){
  box.innerHTML="<h2>Wait... there's more 💕</h2>";
  
  setTimeout(()=>{
    const reasons=[
      "Your smile makes my day ☀️",
      "You understand me 🤍",
      "You make me laugh 😂",
      "You care so much 💗",
      "You are my comfort 🫶",
      "You support my dreams 🌟",
      "You look cutest when angry 😝",
      "You are my best friend 💕",
      "Life feels easy with you 🌈",
      "I just love YOU ❤️"
    ];

    let idx=0;
    box.innerHTML="<h2 id='r'></h2>";

    function show(){
      if(idx<reasons.length){
        document.getElementById("r").innerHTML=reasons[idx];
        idx++;
        setTimeout(show,900);
      }else{
        showGift();
      }
    }
    show();

  },1000);
}

/* gift */
function showGift(){
  box.innerHTML=`
  <h2>Open your gift 🎁</h2>
  <div id="gift" class="bounce" style="font-size:70px;cursor:pointer">🎁</div>
  `;

  document.getElementById("gift").onclick=function(){
    document.body.innerHTML=`
    <div class="fade" style="padding:30px">
      <h1 style="font-size:42px">For You Ankita ❤️</h1>
      <p style="font-size:20px">
      Thank you for being my happiness,<br>
      my peace, my forever person 🌹
      </p>
      <h2>Forever yours,<br>Nitish 💍</h2>
      <br>
      <img src="https://media.giphy.com/media/l0MYt5jPR6QX5pnqM/giphy.gif" width="260">
    </div>
    `;
  }
}

</script>
</body>
</html>
# rose_for_you
