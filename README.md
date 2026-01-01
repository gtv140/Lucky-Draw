<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Aviator Crash Game Demo</title>
<style>
body {margin:0; padding:0; overflow:hidden; background:#0a0a0a; font-family:Arial;}
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
  <h3>Aviator Crash Game ✈️</h3>
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
let plane={x:canvas.width/2, y:canvas.height-100, size:80, trail:[]};
let graphData=[];
let particles=[];
let clouds=[];

// Sounds
let coinSound=new Audio('https://freesound.org/data/previews/341/341695_5260870-lq.mp3');
let crashSound=new Audio('https://freesound.org/data/previews/198/198841_285997-lq.mp3');

// -------- Clouds --------
for(let i=0;i<10;i++){
  clouds.push({x:Math.random()*canvas.width, y:Math.random()*canvas.height/2, size:Math.random()*50+30});
}

// -------- Draw Scene --------
function drawScene(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  
  // Background
  ctx.fillStyle="#0a0a0a";
  ctx.fillRect(0,0,canvas.width,canvas.height);
  
  // Clouds
  ctx.fillStyle="rgba(200,200,200,0.3)";
  clouds.forEach(c=>{
    ctx.beginPath();
    ctx.arc(c.x, c.y, c.size,0,Math.PI*2);
    ctx.fill();
  });
  
  // Multiplier graph
  ctx.strokeStyle="#00ff00";
  ctx.lineWidth=3;
  ctx.beginPath();
  for(let i=0;i<graphData.length;i++){
    let x = i*5;
    let y = canvas.height - 50 - graphData[i]*50;
    if(i==0) ctx.moveTo(x,y);
    else ctx.lineTo(x,y);
  }
  ctx.stroke();
  
  // Plane trail
  plane.trail.forEach(p=>{
    ctx.fillStyle="rgba(0,255,255,0.3)";
    ctx.beginPath();
    ctx.arc(p.x, p.y, 10,0,Math.PI*2);
    ctx.fill();
  });
  
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

// -------- Particles --------
function createParticles(x,y){
  for(let i=0;i<60;i++){
    particles.push({
      x:x, y:y,
      vx:(Math.random()-0.5)*6,
      vy:(Math.random()-0.5)*6,
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
  plane.trail=[];
  graphData=[];
  particles=[];
  document.getElementById('status').innerText="";
  
  let interval=setInterval(()=>{
    if(!running){clearInterval(interval); return;}
    
    // Smooth easing multiplier growth
    multiplier += 0.02 * (1 + multiplier/10);
    document.getElementById('multiplier').innerText=multiplier.toFixed(2)+'x';
    
    // Plane movement
    let planeY = canvas.height-100 - multiplier*50;
    plane.trail.push({x:plane.x, y:plane.y});
    if(plane.trail.length>20) plane.trail.shift();
    plane.y = planeY;
    
    graphData.push(multiplier);
    
    // Clouds move slowly
    clouds.forEach(c=>{
      c.x -= 0.3;
      if(c.x<0) c.x = canvas.width + Math.random()*100;
    });
    
    updateParticles();
    drawScene();
    
    // Crash
    if(multiplier>=crashAt){
      running=false;
      document.getElementById('status').innerHTML="<span style='color:#ff6b6b; font-size:24px;'>CRASH 💥 @ "+crashAt+"x</span>";
      coins-=10; updateCoins();
      crashSound.play();
      createParticles(plane.x, plane.y);
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
