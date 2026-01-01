<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Crash Game Demo with Effects</title>
<style>
body {margin:0; padding:0; overflow:hidden; background:#121212; font-family:Arial;}
#gameCanvas {display:block;}
.ui {
  position:absolute; top:10px; left:50%; transform:translateX(-50%); text-align:center; z-index:100; color:#fff;
}
button {padding:12px 18px; margin:5px; border:none; border-radius:8px; font-size:16px; cursor:pointer;}
.start{background:#2ecc71;}
.cash{background:#f1c40f;}
.status {margin:5px; font-size:18px;}
.mult {font-size:22px; margin:5px;}
.coins {font-size:24px; margin:10px;}
</style>
</head>
<body>

<div class="ui">
  <h2>Coins: <span id="coins">100</span></h2>
  <h3>Crash Game ✈️</h3>
  <div class="status" id="status"></div>
  <button class="start" onclick="startGame()">Start</button>
  <button class="cash" onclick="cashOut()">Cash Out</button>
  <div class="mult" id="multiplier">1.00x</div>
</div>

<canvas id="gameCanvas"></canvas>

<script>
// -------- Variables --------
let coins=100;
function updateCoins(){document.getElementById('coins').innerText=coins;}

let canvas=document.getElementById('gameCanvas');
let ctx=canvas.getContext('2d');
canvas.width=window.innerWidth; canvas.height=window.innerHeight;

let running=false;
let multiplier=1.00;
let crashAt=0;
let plane={x:canvas.width/2, y:canvas.height-100, size:80};
let graphData=[];
let particles=[];

// Sounds
let coinSound=new Audio('https://freesound.org/data/previews/341/341695_5260870-lq.mp3');
let crashSound=new Audio('https://freesound.org/data/previews/198/198841_285997-lq.mp3');

// -------- Draw Scene --------
function drawScene(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  
  // Background
  ctx.fillStyle="#121212";
  ctx.fillRect(0,0,canvas.width,canvas.height);
  
  // Graph
  ctx.strokeStyle="#2ecc71";
  ctx.lineWidth=3;
  ctx.beginPath();
  for(let i=0;i<graphData.length;i++){
    let x = i*5;
    let y = canvas.height - 50 - graphData[i]*50;
    if(i==0) ctx.moveTo(x,y);
    else ctx.lineTo(x,y);
  }
  ctx.stroke();
  
  // Plane
  ctx.font=plane.size+"px Arial";
  ctx.fillText("✈️", plane.x - plane.size/2, plane.y);
  
  // Draw particles
  for(let i=0;i<particles.length;i++){
    let p = particles[i];
    ctx.fillStyle="rgba(255,69,0,"+p.alpha+")";
    ctx.beginPath();
    ctx.arc(p.x,p.y,p.size,0,Math.PI*2);
    ctx.fill();
  }
}
drawScene();

// -------- Particles --------
function createParticles(x,y){
  for(let i=0;i<50;i++){
    particles.push({
      x:x, y:y,
      vx:(Math.random()-0.5)*5,
      vy:(Math.random()-0.5)*5,
      size:Math.random()*5+2,
      alpha:1
    });
  }
}

function updateParticles(){
  for(let i=particles.length-1;i>=0;i--){
    let p=particles[i];
    p.x += p.vx;
    p.y += p.vy;
    p.alpha -= 0.02;
    if(p.alpha<=0) particles.splice(i,1);
  }
}

// -------- Game Functions --------
function startGame(){
  if(running) return;
  running=true;
  multiplier=1.00;
  crashAt=(Math.random()*5+1.5).toFixed(2);
  plane.x=canvas.width/2;
  plane.y=canvas.height-100;
  plane.size=80;
  graphData=[];
  particles=[];
  document.getElementById('status').innerText="";
  
  let interval=setInterval(()=>{
    if(!running){clearInterval(interval); return;}
    multiplier+=0.02;
    document.getElementById('multiplier').innerText=multiplier.toFixed(2)+'x';
    
    // Plane movement along graph
    plane.y=canvas.height-100 - multiplier*50;
    graphData.push(multiplier);
    
    updateParticles();
    drawScene();
    
    // Crash check
    if(multiplier>=crashAt){
      running=false;
      document.getElementById('status').innerHTML="<span style='color:#ff6b6b; font-size:24px;'>CRASH 💥 @ "+crashAt+"x</span>";
      coins-=10; updateCoins();
      crashSound.play();
      createParticles(plane.x, plane.y); // explosion particles
    }
  },50);
}

function cashOut(){
  if(!running) return;
  running=false;
  document.getElementById('status').innerText="Cashed out @ "+multiplier.toFixed(2)+'x';
  coins+=Math.floor(10*multiplier); updateCoins(); coinSound.play();
}
</script>
</body>
</html>
