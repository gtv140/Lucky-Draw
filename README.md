<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Lucky Casino App Demo</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
body {margin:0; padding:0; overflow:hidden; background:#0a0a0a; font-family:Arial;}
h1{color:#ff00ff;text-align:center; text-shadow:0 0 20px #ff00ff; margin-top:5px;}
#coins{position:absolute; top:10px; left:50%; transform:translateX(-50%); font-size:22px; color:#ffcc00; text-shadow:0 0 20px #ffcc00; z-index:200;}
#gameContainer{position:relative; width:100%; height:100vh; display:flex; flex-direction:column;}
canvas{background:#0a0a0a; flex:1; display:block;}
#menu{position:absolute; top:50px; left:50%; transform:translateX(-50%); display:flex; gap:15px; z-index:200;}
#menu button{padding:10px 20px; border:none; border-radius:8px; font-weight:bold; color:#0a0a0a; background:#ff00ff; box-shadow:0 0 15px #ff00ff; cursor:pointer;}
.bottomUI{background:rgba(0,0,0,0.9); padding:12px; display:flex; justify-content:center; align-items:center; flex-wrap:wrap; box-shadow:0 -2px 15px #00ffff;}
.bottomUI input, .bottomUI select, .bottomUI button{margin:5px; padding:10px; border:none; border-radius:8px; font-weight:bold; color:#0a0a0a; cursor:pointer;}
.start{background:#00ff99; box-shadow:0 0 15px #00ff99;}
.cash{background:#ff00ff; box-shadow:0 0 15px #ff00ff;}
#history,#botBox{position:absolute; right:10px; background:rgba(0,0,0,0.55); padding:12px; border-radius:12px; font-size:14px; color:#fff; text-shadow:0 0 5px #0fffe0; max-height:250px; overflow-y:auto;}
#botBox{top:180px;} #history{top:470px;}
</style>
</head>
<body>

<h1>Lucky Casino App</h1>
<div id="coins">Coins: 100</div>
<div id="gameContainer">
  <canvas id="gameCanvas"></canvas>
  <div id="menu">
    <button onclick="selectGame('aviator')">Aviator</button>
    <button onclick="selectGame('slots')">Slots</button>
    <button onclick="selectGame('dice')">Dice</button>
    <button onclick="selectGame('coinflip')">Coin Flip</button>
    <button onclick="selectGame('spin')">Spin / Gift</button>
  </div>
  <div class="bottomUI">
    Bet Amount: <input type="number" id="betAmount" value="10" min="10" max="1000" step="10">
    Multiplier: <select id="betMultiplier"><option>1.5</option><option>2</option><option>3</option><option>5</option></select>
    <button class="start" onclick="startRound()">Start / Spin</button>
    <button class="cash" onclick="cashOut()">Cash Out</button>
  </div>
  <div id="botBox">Bots Info:</div>
  <div id="history">History:</div>
</div>

<script>
let canvas=document.getElementById('gameCanvas');
let ctx=canvas.getContext('2d');
canvas.width=window.innerWidth; canvas.height=window.innerHeight-200;
let coins=100; document.getElementById('coins').innerText='Coins: '+coins;
let currentGame='aviator';

// Bot Users & History Arrays
let botUsers=[];
let history=[];

// Game States
let aviator={running:false,multiplier:1,crashAt:0};
let slots={symbols:['🍒','🍋','🍉','🍇','⭐'], reels:[0,0,0], running:false};
let dice={running:false,roll:0};
let coinflip={running:false,result:''};
let spin={running:false,result:''};

// Select game
function selectGame(game){currentGame=game; resetGame();}

// Reset canvas and game states
function resetGame(){
  aviator.running=false; slots.running=false; dice.running=false; coinflip.running=false; spin.running=false;
  ctx.clearRect(0,0,canvas.width,canvas.height);
}

// Update history display
function updateHistory(){document.getElementById('history').innerHTML='History:<br>'+history.slice(-15).join('<br>');}

<script>
// --- Aviator / Crash Game ---
function startAviator(amount,mul){
  aviator.running=true;
  aviator.multiplier=1;
  aviator.crashAt=Math.random()*5+1.5; // Random crash point
  history.push('Aviator round started'); updateHistory();

  let interval=setInterval(()=>{
    if(!aviator.running){clearInterval(interval); return;}
    
    // Increase multiplier smoothly
    aviator.multiplier += 0.02*(1+aviator.multiplier/10);

    drawAviator();

    // Crash check
    if(aviator.multiplier >= aviator.crashAt){
      aviator.running=false;
      history.push('CRASH @ '+aviator.crashAt.toFixed(2)+'x');
      updateHistory();
      playCrashSound();
      clearInterval(interval);
    }
  },50);
}

// Draw plane, multiplier, neon trail
function drawAviator(){
  ctx.clearRect(0,0,canvas.width,canvas.height);

  // Neon crash line
  ctx.strokeStyle='#ff00ff';
  ctx.lineWidth=4;
  ctx.beginPath();
  ctx.moveTo(50,canvas.height-50);
  let y=canvas.height-50-aviator.multiplier*50;
  ctx.lineTo(canvas.width-50,y);
  ctx.stroke();

  // Plane
  ctx.fillStyle='#00ffff';
  ctx.font='50px Arial';
  ctx.fillText('✈️',canvas.width/2-25,y-50);

  // Multiplier display
  ctx.fillStyle='#ffcc00';
  ctx.font='40px Arial';
  ctx.fillText(aviator.multiplier.toFixed(2)+'x',canvas.width/2-50,y-100);
}

// Cash out function for Aviator
function cashOut(){
  if(currentGame=='aviator' && aviator.running){
    aviator.running=false;
    let betAmt=parseInt(document.getElementById('betAmount').value);
    coins += Math.floor(aviator.multiplier*betAmt);
    document.getElementById('coins').innerText='Coins: '+coins;
    history.push('Cashed out @ '+aviator.multiplier.toFixed(2)+'x');
    updateHistory();
    playCashoutSound();
  }
}

// Sound Effects
function playCrashSound(){
  let audio=new Audio('https://www.myinstants.com/media/sounds/airplane-crash.mp3');
  audio.play();
}
function playCashoutSound(){
  let audio=new Audio('https://www.myinstants.com/media/sounds/coin-drop-1.mp3');
  audio.play();
}
<script>
// --- Slots Game ---
function startSlots(amount){
  slots.running=true;
  slots.reels = [
    Math.floor(Math.random()*slots.symbols.length),
    Math.floor(Math.random()*slots.symbols.length),
    Math.floor(Math.random()*slots.symbols.length)
  ];
  drawSlots();
  setTimeout(()=>{
    let win=false;
    if(slots.reels[0]==slots.reels[1] && slots.reels[1]==slots.reels[2]){win=true; coins+=amount*3;}
    history.push('Slots: '+slots.symbols[slots.reels[0]]+' | '+slots.symbols[slots.reels[1]]+' | '+slots.symbols[slots.reels[2]]+(win?' WIN':' LOSS'));
    updateHistory(); document.getElementById('coins').innerText='Coins: '+coins;
    slots.running=false;
  },1000);
}
function drawSlots(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  ctx.font='80px Arial'; ctx.fillStyle='#ffcc00';
  ctx.fillText(slots.symbols[slots.reels[0]],canvas.width/2-120,canvas.height/2);
  ctx.fillText(slots.symbols[slots.reels[1]],canvas.width/2,canvas.height/2);
  ctx.fillText(slots.symbols[slots.reels[2]],canvas.width/2+120,canvas.height/2);
}

// --- Dice Game ---
function startDice(amount,mul){
  dice.running=true; dice.roll=Math.floor(Math.random()*6)+1;
  drawDice();
  setTimeout(()=>{
    let win=dice.roll>=4; if(win) coins+=amount*mul;
    history.push('Dice rolled '+dice.roll+(win?' WIN':' LOSS')); updateHistory();
    document.getElementById('coins').innerText='Coins: '+coins; dice.running=false;
  },1000);
}
function drawDice(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  ctx.font='100px Arial'; ctx.fillStyle='#00ffcc';
  ctx.fillText('🎲 '+dice.roll,canvas.width/2-80,canvas.height/2);
}

// --- Coin Flip ---
function startCoinFlip(amount){
  coinflip.running=true;
  coinflip.result=Math.random()>0.5?'Heads':'Tails';
  drawCoinFlip();
  setTimeout(()=>{
    let win=Math.random()>0.5; if(win) coins+=amount*2;
    history.push('Coin Flip: '+coinflip.result+(win?' WIN':' LOSS'));
    updateHistory(); document.getElementById('coins').innerText='Coins: '+coins; coinflip.running=false;
  },1000);
}
function drawCoinFlip(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  ctx.font='80px Arial'; ctx.fillStyle='#ff00ff';
  ctx.fillText('🪙 '+coinflip.result,canvas.width/2-80,canvas.height/2);
}

// --- Spin / Gift Wheel ---
function startSpin(){
  spin.running=true;
  let gifts=[50,100,150,200,500];
  spin.result=gifts[Math.floor(Math.random()*gifts.length)];
  ctx.clearRect(0,0,canvas.width,canvas.height);
  ctx.font='80px Arial'; ctx.fillStyle='#00ff99';
  ctx.fillText('🎁 +'+spin.result+' Coins!',canvas.width/2-150,canvas.height/2);
  setTimeout(()=>{
    coins+=spin.result;
    document.getElementById('coins').innerText='Coins: '+coins;
    history.push('Spin Gift: '+spin.result+' coins');
    updateHistory(); spin.running=false;
  },1000);
}

// --- Bot Users & Random Bets ---
function generateBots(num){
  botUsers=[];
  for(let i=0;i<num;i++){
    botUsers.push({
      name:'Bot'+(i+1),
      bet:Math.floor(Math.random()*1000)+10,
      game:['aviator','slots','dice','coinflip'][Math.floor(Math.random()*4)],
      cashOut:parseFloat((Math.random()*5+1).toFixed(2))
    });
  }
  updateBots();
}
function updateBots(){
  let botDiv=document.getElementById('botBox');
  botDiv.innerHTML='Bots Info:<br>';
  botUsers.forEach(bot=>{
    botDiv.innerHTML+=bot.name+' | Bet: '+bot.bet+' | Game: '+bot.game+' | CashOut: '+bot.cashOut+'x<br>';
  });
}

// Generate 50 random bots for demo
generateBots(50);
setInterval(()=>{
  generateBots(50);
},5000); // Refresh bot bets every 5 seconds
<script>
// --- Coin Rain Animation ---
let coinsParticles=[];
function spawnCoins(num){
  for(let i=0;i<num;i++){
    coinsParticles.push({
      x:Math.random()*canvas.width,
      y:-50,
      speed:2+Math.random()*3,
      symbol:'💰',
      size:20+Math.random()*20
    });
  }
}
function drawCoinsParticles(){
  coinsParticles.forEach(p=>{
    ctx.font=p.size+'px Arial';
    ctx.fillStyle='#ffff00';
    ctx.fillText(p.symbol,p.x,p.y);
    p.y+=p.speed;
  });
  // Remove coins out of screen
  coinsParticles=coinsParticles.filter(p=>p.y<canvas.height+50);
}

// --- Jackpot Sparkle Animation ---
let jackpotParticles=[];
function spawnJackpot(){
  for(let i=0;i<50;i++){
    jackpotParticles.push({
      x:Math.random()*canvas.width,
      y:Math.random()*canvas.height,
      vx:(Math.random()-0.5)*5,
      vy:(Math.random()-0.5)*5,
      size:5+Math.random()*10,
      color:'hsl('+(Math.random()*360)+',100%,50%)'
    });
  }
}
function drawJackpot(){
  jackpotParticles.forEach(p=>{
    ctx.fillStyle=p.color;
    ctx.beginPath();
    ctx.arc(p.x,p.y,p.size,0,Math.PI*2);
    ctx.fill();
    p.x+=p.vx; p.y+=p.vy;
  });
  // Remove particles slowly
  jackpotParticles=jackpotParticles.filter(p=>p.size>0);
}

// --- Neon Particles Background ---
let neonParticles=[];
for(let i=0;i<100;i++){
  neonParticles.push({
    x:Math.random()*canvas.width,
    y:Math.random()*canvas.height,
    size:2+Math.random()*4,
    vx:(Math.random()-0.5)*1,
    vy:(Math.random()-0.5)*1,
    color:'hsl('+(Math.random()*360)+',100%,50%)'
  });
});
function drawNeonParticles(){
  neonParticles.forEach(p=>{
    ctx.fillStyle=p.color;
    ctx.beginPath();
    ctx.arc(p.x,p.y,p.size,0,Math.PI*2);
    ctx.fill();
    p.x+=p.vx; p.y+=p.vy;
    if(p.x<0)p.x=canvas.width; if(p.x>canvas.width)p.x=0;
    if(p.y<0)p.y=canvas.height; if(p.y>canvas.height)p.y=0;
  });
}

// --- Main Animation Loop ---
function animate(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  drawNeonParticles();
  drawCoinsParticles();
  drawJackpot();

  // Redraw current game objects
  if(currentGame=='aviator' && aviator.running) drawAviator();
  else if(currentGame=='slots' && slots.running) drawSlots();
  else if(currentGame=='dice' && dice.running) drawDice();
  else if(currentGame=='coinflip' && coinflip.running) drawCoinFlip();
  else if(currentGame=='spin' && spin.running) drawSpin();

  requestAnimationFrame(animate);
}

// Start animation
animate();

// --- Trigger Coin Rain on big win ---
function triggerCoinRain(){
  spawnCoins(50);
  let audio=new Audio('https://www.myinstants.com/media/sounds/coin-drop-1.mp3');
  audio.play();
}

// --- Trigger Jackpot Sparkle ---
function triggerJackpot(){
  spawnJackpot();
  let audio=new Audio('https://www.myinstants.com/media/sounds/jackpot.mp3');
  audio.play();
}
</script>
