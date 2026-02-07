<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Future Pro Hub</title>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:'Roboto',sans-serif;}
body{background:#f0f2f5;color:#111;}
header{background:#0f172a;color:white;padding:50px;text-align:center;}
header h1{font-size:2.5em;margin-bottom:10px;}
header p{font-size:1.2em;color:#a0aec0;}
nav{display:flex;justify-content:center;gap:20px;padding:15px;background:white;box-shadow:0 2px 5px rgba(0,0,0,0.1);flex-wrap:wrap;}
nav a{text-decoration:none;color:#0f172a;font-weight:500;padding:8px 15px;border-radius:5px;transition:0.3s;}
nav a:hover{background:#0f172a;color:white;}
section{padding:60px 20px;max-width:1200px;margin:auto;}
h2{font-size:2em;color:#0f172a;margin-bottom:20px;text-align:center;}
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:30px;}
.card{background:white;padding:25px;border-radius:12px;box-shadow:0 4px 15px rgba(0,0,0,0.1);transition:0.3s;}
.card:hover{transform:translateY(-5px);box-shadow:0 6px 20px rgba(0,0,0,0.15);}
.card h3{margin-bottom:15px;color:#0f172a;}
.card p{color:#4a5568;}
.card button{margin-top:10px;padding:10px 15px;border:none;border-radius:6px;background:#0f172a;color:white;cursor:pointer;transition:0.3s;}
.card button:hover{background:#1e293b;}
input{padding:8px;margin-top:5px;width:80%;}
#pointsDisplay{font-weight:bold;color:#0f172a;}
</style>
<link rel="manifest" href="manifest.json">
</head>
<body>

<header>
  <h1>Future Pro Hub</h1>
  <p>Learn, Track, Earn – All in One</p>
  <p>Points: <span id="pointsDisplay">0</span></p>
</header>

<nav>
  <a href="#services">Services</a>
  <a href="#portfolio">Portfolio</a>
  <a href="#tools">Tools</a>
  <a href="#contact">Contact</a>
</nav>

<section id="services">
  <h2>🚀 My Services</h2>
  <div class="cards">
    <div class="card">
      <h3>Web Development</h3>
      <p>Build modern responsive websites for clients.</p>
      <button onclick="gainPoints(5)">Hire Me (+5 points)</button>
    </div>
    <div class="card">
      <h3>UI/UX Design</h3>
      <p>Design sleek interfaces and apps.</p>
      <button onclick="gainPoints(5)">Hire Me (+5 points)</button>
    </div>
    <div class="card">
      <h3>Freelance Consulting</h3>
      <p>Guide freelancers to earn online.</p>
      <button onclick="gainPoints(5)">Consult (+5 points)</button>
    </div>
  </div>
</section>

<section id="portfolio">
  <h2>💼 Portfolio</h2>
  <div class="cards">
    <div class="card">
      <h3>Project 1</h3>
      <p>Responsive website with modern UI & client-ready design.</p>
      <button onclick="alert('View Project!')">View</button>
    </div>
    <div class="card">
      <h3>Project 2</h3>
      <p>Interactive dashboard for productivity & analytics.</p>
      <button onclick="alert('View Project!')">View</button>
    </div>
    <div class="card">
      <h3>Project 3</h3>
      <p>Freelance platform prototype with earning features.</p>
      <button onclick="alert('View Project!')">View</button>
    </div>
  </div>
</section>

<section id="tools">
  <h2>🛠 Mini Tools</h2>
  <div class="cards">
    <div class="card">
      <h3>Expense Tracker</h3>
      <input type="number" id="income" placeholder="Enter Income">
      <input type="number" id="expense" placeholder="Enter Expense">
      <button onclick="trackExpense()">Add & Calculate</button>
      <p id="expenseResult"></p>
    </div>
    <div class="card">
      <h3>Habit Tracker</h3>
      <input type="text" id="habit" placeholder="Enter Habit">
      <button onclick="addHabit()">Add Habit</button>
      <ul id="habitList"></ul>
    </div>
  </div>
</section>

<section id="contact">
  <h2>📩 Contact Me</h2>
  <div class="cards">
    <div class="card">
      <h3>Email</h3>
      <p>yourname@example.com</p>
      <button onclick="alert('Send Email!')">Send</button>
    </div>
    <div class="card">
      <h3>LinkedIn</h3>
      <p>linkedin.com/in/yourprofile</p>
      <button onclick="alert('Visit LinkedIn!')">Visit</button>
    </div>
    <div class="card">
      <h3>Portfolio</h3>
      <p>Full project showcase.</p>
      <button onclick="alert('View Portfolio!')">View</button>
    </div>
  </div>
</section>

<footer style="text-align:center;padding:20px;background:#0f172a;color:white;">
  <p>© 2026 Future Pro Hub | All Rights Reserved</p>
</footer>

<script>
let points = 0;
function gainPoints(p){
  points += p;
  document.getElementById('pointsDisplay').innerText = points;
}

// Expense Tracker
function trackExpense(){
  let inc = Number(document.getElementById('income').value);
  let exp = Number(document.getElementById('expense').value);
  if(!isNaN(inc) && !isNaN(exp)){
    let balance = inc - exp;
    document.getElementById('expenseResult').innerText = 'Balance: ' + balance;
    gainPoints(1);
  } else { alert('Enter valid numbers'); }
}

// Habit Tracker
function addHabit(){
  let habit = document.getElementById('habit').value;
  if(habit){
    let li = document.createElement('li');
    li.innerText = habit;
    document.getElementById('habitList').appendChild(li);
    document.getElementById('habit').value = '';
    gainPoints(1);
  }
}
</script>

</body>
</html>
