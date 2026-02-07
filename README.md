<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Future-Ready Game Hub</title>
<style>
body{margin:0;font-family:Arial;background:#020617;color:white;text-align:center;}
button{padding:10px 20px;margin:5px;font-size:16px;}
canvas{background:#111;display:block;margin:auto;}
.game{display:none;}
#ball{width:50px;height:50px;background:red;border-radius:50%;position:absolute;}
</style>
</head>
<body>

<h1>🌟 Future-Ready Game Hub</h1>
<div id="menu">
  <button onclick="show('game1')">Catch The Ball</button>
  <button onclick="show('game2')">Tap Challenge</button>
  <button onclick="show('game3')">Guess Number</button>
  <button onclick="show('game4')">Math Quiz</button>
  <button onclick="show('game5')">Car Racing</button>
  <p>Points: <span id="points">0</span></p>
</div>

<!-- Game 1: Catch The Ball -->
<div id="game1" class="game">
  <h2>Catch The Ball</h2>
  <p>Score: <span id="score1">0</span></p>
  <div id="ball"></div>
  <button onclick="back()">Back</button>
</div>

<!-- Game 2: Tap Challenge -->
<div id="game2" class="game">
  <h2>Tap Challenge</h2>
  <p>Taps: <span id="taps">0</span></p>
  <button onclick="tap()">TAP FAST</button>
  <button onclick="back()">Back</button>
</div>

<!-- Game 3: Guess Number -->
<div id="game3" class="game">
  <h2>Guess The Number (1–10)</h2>
  <input id="guess" type="number">
  <button onclick="check()">Guess</button>
  <p id="result"></p>
  <button onclick="back()">Back</button>
</div>

<!-- Game 4: Math Quiz -->
<div id="game4" class="game">
  <h2>Math Quiz</h2>
  <p id="quizQ">?</p>
  <input id="quizA" type="number">
  <button onclick="quizCheck()">Submit</button>
  <p id="quizResult"></p>
  <button onclick="back()">Back</button>
</div>

<!-- Game 5: Car Racing -->
<div id="game5" class="game">
  <h2>Car Racing</h2>
  <p>Score: <span id="raceScore">0</span></p>
  <canvas id="race" width="300" height="400"></canvas>
  <button onclick="raceMove(-1)">⬅️</button>
  <button onclick="raceMove(1)">➡️</button>
  <button onclick="backRace()">Back</button>
</div>

<script>
// General functions
let points=0;
function show(id){
  document.getElementById("menu").style.display="none";
  document.querySelectorAll(".game").forEach(g=>g.style.display="none");
  document.getElementById(id).style.display="block";
}
function back(){
  document.getElementById("menu").style.display="block";
  document.querySelectorAll(".game").forEach(g=>g.style.display="none");
}

// Game 1: Catch The Ball
let score1=0, ball=document.getElementById("ball");
ball.onclick=()=>{
  score1++; points++;
  document.getElementById("score1").innerText=score1;
  document.getElementById("points").innerText=points;
  ball.style.left=Math.random()*(window.innerWidth-50)+"px";
  ball.style.top=Math.random()*(window.innerHeight-150)+"px";
}

// Game 2: Tap Challenge
let taps=0;
function tap(){taps++; points++; document.getElementById("taps").innerText=taps; document.getElementById("points").innerText=points;}

// Game 3: Guess Number
let num=Math.floor(Math.random()*10)+1;
function check(){
  let g=document.getElementById("guess").value;
  if(g==num){document.getElementById("result").innerText="🎉 Correct"; points+=2;} 
  else {document.getElementById("result").innerText="❌ Try Again";}
  document.getElementById("points").innerText=points;
}

// Game 4: Math Quiz
let a=Math.floor(Math.random()*10)+1;
let b=Math.floor(Math.random()*10)+1;
document.getElementById("quizQ").innerText=`${a} + ${b} = ?`;
function quizCheck(){
  let ans=document.getElementById("quizA").value;
  if(ans==a+b){document.getElementById("quizResult").innerText="✅ Correct"; points+=3;} 
  else {document.getElementById("quizResult").innerText="❌ Wrong";}
  document.getElementById("points").innerText=points;
  a=Math.floor(Math.random()*10)+1; b=Math.floor(Math.random()*10)+1;
  document.getElementById("quizQ").innerText=`${a} + ${b} = ?`;
}

// Game 5: Car Racing
const raceCanvas=document.getElementById("race");
const raceCtx=raceCanvas.getContext("2d");
let raceCar={x:130,y:330,w:40,h:70};
let raceEnemies=[];
let raceScore=0;
let raceSpeed=3;

function raceMove(dir){
  raceCar.x += dir*40;
  if(raceCar.x<0) raceCar.x=0;
  if(raceCar.x>260) raceCar.x=260;
}

function addRaceEnemy(){raceEnemies.push({x:Math.random()*260,y:-80,w:40,h:70});}

function drawRace(){
  raceCtx.clearRect(0,0,300,400);
  raceCtx.fillStyle="lime";
  raceCtx.fillRect(raceCar.x,raceCar.y,raceCar.w,raceCar.h);
  raceCtx.fillStyle="red";
  raceEnemies.forEach(e=>{
    e.y += raceSpeed;
    raceCtx.fillRect(e.x,e.y,e.w,e.h);
    if(e.x<raceCar.x+40 && e.x+40>raceCar.x && e.y<raceCar.y+70 && e.y+70>raceCar.y){
      alert("💥 Crash! Score: "+raceScore);
      location.reload();
    }
  });
  raceScore++;
  points++; // points increase automatically
  raceSpeed += 0.002;
  document.getElementById("raceScore").innerText=raceScore;
  document.getElementById("points").innerText=points;
}
setInterval(addRaceEnemy,1500);
setInterval(drawRace,30);
function backRace(){back();}
</script>

</body>
</html>
