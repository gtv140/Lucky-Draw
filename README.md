<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Future Skill & Productivity Hub</title>
<style>
body{margin:0;font-family:Arial;background:#f4f4f4;color:#111;}
header{background:#0f172a;color:white;padding:20px;text-align:center;}
nav{display:flex;justify-content:center;gap:15px;padding:10px;background:#111;color:white;flex-wrap:wrap;}
nav a{color:white;text-decoration:none;padding:8px 12px;border-radius:5px;}
nav a:hover{background:#0f172a;}
section{padding:20px;max-width:900px;margin:auto;}
.card{background:white;padding:15px;margin:10px 0;border-radius:8px;box-shadow:0 2px 5px rgba(0,0,0,0.2);}
button{padding:10px 15px;margin-top:10px;background:#0f172a;color:white;border:none;border-radius:5px;cursor:pointer;}
button:hover{background:#1e293b;}
input{padding:8px;margin-top:5px;width:80%;}
#pointsDisplay{font-weight:bold;color:#0f172a;}
</style>
</head>
<body>

<header>
  <h1>🌟 Future Skill & Productivity Hub</h1>
  <p>Learn, Track, Earn – All in One</p>
  <p>Points: <span id="pointsDisplay">0</span></p>
</header>

<nav>
  <a href="#learning">Learning</a>
  <a href="#tools">Tools</a>
  <a href="#portfolio">Portfolio</a>
</nav>

<section id="learning">
  <h2>💡 Learning Hub</h2>
  <div class="card">
    <h3>HTML/CSS Basics</h3>
    <p>Learn to build professional websites.</p>
    <button onclick="gainPoints(5)">Start Learning (+5 points)</button>
  </div>
  <div class="card">
    <h3>Freelancing Tips</h3>
    <p>Earn online by offering services.</p>
    <button onclick="gainPoints(5)">Start Learning (+5 points)</button>
  </div>
</section>

<section id="tools">
  <h2>🛠 Productivity Tools</h2>
  <div class="card">
    <h3>Expense Tracker</h3>
    <p>Track your income & expenses efficiently.</p>
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
</section>

<section id="portfolio">
  <h2>💼 My Portfolio</h2>
  <div class="card">
    <h3>Web Development</h3>
    <p>Projects showcase for clients.</p>
    <button onclick="gainPoints(3)">View Projects (+3 points)</button>
  </div>
  <div class="card">
    <h3>Freelance Services</h3>
    <p>Hire me for web, design, or automation tasks.</p>
    <button onclick="alert('Contact Me!')">Contact</button>
  </div>
</section>

<footer style="text-align:center;padding:15px;background:#111;color:white;">
  <p>© 2026 Future Hub | All Rights Reserved</p>
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
    gainPoints(1); // reward points for using tool
  } else {
    alert('Please enter valid numbers!');
  }
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
