<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Endless Runner</title>
<style>
body{margin:0;background:#020617;color:white;font-family:Arial;text-align:center}
canvas{background:#0f172a;display:block;margin:auto}
button{padding:10px 20px;font-size:16px;margin:5px}
</style>
</head>
<body>

<h2>🏃 Endless Runner</h2>
<p>Score: <span id="score">0</span></p>
<button onclick="move(-1)">⬅️</button>
<button onclick="move(1)">➡️</button>

<canvas id="game" width="300" height="500"></canvas>

<script>
const c = document.getElementById("game");
const ctx = c.getContext("2d");

let player = {x:130,y:420,w:40,h:40};
let obs = [];
let score = 0;
let speed = 3;
let over = false;

function move(dir){
  player.x += dir*40;
  if(player.x<0)player.x=0;
  if(player.x>260)player.x=260;
}

function addObs(){
  obs.push({x:Math.random()*260,y:-40,w:40,h:40});
}

function draw(){
  ctx.clearRect(0,0,300,500);

  ctx.fillStyle="lime";
  ctx.fillRect(player.x,player.y,player.w,player.h);

  ctx.fillStyle="red";
  obs.forEach(o=>{
    o.y+=speed;
    ctx.fillRect(o.x,o.y,o.w,o.h);

    if(
      o.x<player.x+40 &&
      o.x+40>player.x &&
      o.y<player.y+40 &&
      o.y+40>player.y
    ){
      over=true;
      alert("Game Over! Score: "+score);
      location.reload();
    }
  });

  score++;
  document.getElementById("score").innerText=score;
}

setInterval(addObs,1500);
setInterval(draw,30);
</script>

</body>
</html>
