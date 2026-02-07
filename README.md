<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Future Pro Hub</title>
<meta name="description" content="Future Pro Hub - Modern Portfolio, Skills, Tools & Freelance Hub">
<style>
:root{
  --primary:#0f172a;--secondary:#1e293b;--accent:#3b82f6;--bg:#f0f2f5;--text:#111;
}
*{margin:0;padding:0;box-sizing:border-box;font-family:'Roboto',sans-serif;}
body{background:var(--bg);color:var(--text);transition:0.3s;}
header{background:var(--primary);color:white;padding:60px 20px;text-align:center;position:relative;}
header h1{font-size:3em;margin-bottom:10px;}
header p{font-size:1.3em;color:#a0aec0;}
nav{display:flex;justify-content:center;gap:20px;padding:15px;background:white;box-shadow:0 2px 10px rgba(0,0,0,0.1);flex-wrap:wrap;position:sticky;top:0;z-index:100;}
nav a{text-decoration:none;color:var(--primary);font-weight:500;padding:10px 20px;border-radius:8px;transition:0.3s;font-size:1em;}
nav a:hover{background:var(--accent);color:white;transform:scale(1.05);}
section{padding:80px 20px;max-width:1200px;margin:auto;}
h2{font-size:2.2em;color:var(--primary);margin-bottom:30px;text-align:center;position:relative;}
h2::after{content:"";width:60px;height:3px;background:var(--accent);display:block;margin:10px auto 0;border-radius:2px;}
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:25px;}
.card{background:white;padding:20px;border-radius:15px;box-shadow:0 6px 20px rgba(0,0,0,0.1);transition:0.4s;cursor:pointer;}
.card:hover{transform:translateY(-8px) scale(1.02);box-shadow:0 10px 25px rgba(0,0,0,0.2);}
.card img{width:100%;border-radius:10px;margin-bottom:15px;}
.card h3{margin-bottom:10px;}
.card p{color:#4a5568;line-height:1.5;}
.card button{margin-top:10px;padding:10px 15px;border:none;border-radius:8px;background:var(--accent);color:white;cursor:pointer;transition:0.3s;}
.card button:hover{background:var(--secondary);transform:scale(1.05);}
input{padding:10px;margin:8px 0;width:90%;border-radius:8px;border:1px solid #ccc;transition:0.3s;}
input:focus{outline:none;border-color:var(--accent);box-shadow:0 0 5px var(--accent);}
footer{background:var(--primary);color:white;text-align:center;padding:25px;letter-spacing:1px;}
footer p{font-size:0.9em;}
.toggle-container{position:absolute;top:20px;right:20px;}
.toggle-container input{display:none;}
.toggle-container label{cursor:pointer;width:50px;height:26px;background:#ccc;display:block;border-radius:15px;position:relative;}
.toggle-container label::after{content:"";width:22px;height:22px;background:white;position:absolute;top:2px;left:2px;border-radius:50%;transition:0.3s;}
.toggle-container input:checked + label::after{transform:translateX(24px);}
.toggle-container input:checked + label{background:var(--accent);}
body.dark{background:#111;color:white;}
body.dark header{background:#1e293b;}
body.dark nav{background:#0f172a;}
body.dark .card{background:#1a202c;color:white;}
body.dark input{background:#111;color:white;border:1px solid #555;}
body.dark footer{background:#1e293b;}
</style>

<!-- Manifest inside HTML for single-file PWA -->
<link rel="manifest" href="data:application/manifest+json,{&quot;name&quot;:&quot;Future Pro Hub&quot;,&quot;short_name&quot;:&quot;FP Hub&quot;,&quot;start_url&quot;:&quot;/&quot;,&quot;display&quot;:&quot;standalone&quot;,&quot;background_color&quot;:&quot;#0f172a&quot;,&quot;theme_color&quot;:&quot;#3b82f6&quot;,&quot;icons&quot;:[{&quot;src&quot;:&quot;https://images.pexels.com/photos/3184398/pexels-photo-3184398.jpeg?auto=compress&amp;cs=tinysrgb&amp;w=600&quot;,&quot;sizes&quot;:&quot;192x192&quot;,&quot;type&quot;:&quot;image/png&quot;},{&quot;src&quot;:&quot;https://images.pexels.com/photos/3184398/pexels-photo-3184398.jpeg?auto=compress&amp;cs=tinysrgb&amp;w=600&quot;,&quot;sizes&quot;:&quot;512x512&quot;,&quot;type&quot;:&quot;image/png&quot;}]}">

</head>
<body>

<header>
  <h1>Future Pro Hub</h1>
  <p>Modern Interactive Portfolio & Freelance Hub</p>
  <div class="toggle-container">
    <input type="checkbox" id="darkToggle">
    <label for="darkToggle"></label>
  </div>
</header>

<nav>
  <a href="#services">Services</a>
  <a href="#portfolio">Portfolio</a>
  <a href="#tools">Tools</a>
  <a href="#contact">Contact</a>
</nav>

<section id="services">
  <h2>🚀 Our Services</h2>
  <div class="cards">
    <div class="card">
      <img src="https://images.pexels.com/photos/1181675/pexels-photo-1181675.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Web Development">
      <h3>Web Development</h3>
      <p>Professional responsive websites for clients.</p>
      <button onclick="gainPoints(5)">Hire Me (+5 pts)</button>
    </div>
    <div class="card">
      <img src="https://images.pexels.com/photos/3184325/pexels-photo-3184325.jpeg?auto=compress&cs=tinysrgb&w=600" alt="UI/UX Design">
      <h3>UI/UX Design</h3>
      <p>Sleek, modern interface design services.</p>
      <button onclick="gainPoints(5)">Hire Me (+5 pts)</button>
    </div>
    <div class="card">
      <img src="https://images.pexels.com/photos/3184630/pexels-photo-3184630.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Consulting">
      <h3>Freelance Consulting</h3>
      <p>Guidance to start earning online.</p>
      <button onclick="gainPoints(5)">Consult (+5 pts)</button>
    </div>
  </div>
</section>

<section id="portfolio">
  <h2>💼 Portfolio</h2>
  <div class="cards">
    <div class="card">
      <img src="https://images.pexels.com/photos/3184465/pexels-photo-3184465.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Project 1">
      <h3>Project 1</h3>
      <button onclick="alert('View Project 1')">View</button>
    </div>
    <div class="card">
      <img src="https://images.pexels.com/photos/3184638/pexels-photo-3184638.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Project 2">
      <h3>Project 2</h3>
      <button onclick="alert('View Project 2')">View</button>
    </div>
    <div class="card">
      <img src="https://images.pexels.com/photos/3184336/pexels-photo-3184336.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Project 3">
      <h3>Project 3</h3>
      <button onclick="alert('View Project 3')">View</button>
    </div>
  </div>
</section>

<section id="tools">
  <h2>🛠 Mini Tools</h2>
  <div class="cards">
    <div class="card">
      <img src="https://images.pexels.com/photos/3184299/pexels-photo-3184299.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Expense Tracker">
      <h3>Expense Tracker</h3>
      <input type="number" id="income" placeholder="Income">
      <input type="number" id="expense" placeholder="Expense">
      <button onclick="trackExpense()">Calculate</button>
      <p id="balance"></p>
    </div>
    <div class="card">
      <img src="https://images.pexels.com/photos/3183163/pexels-photo-3183163.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Habit Tracker">
      <h3>Habit Tracker</h3>
      <input type="text" id="habit" placeholder="Enter Habit">
      <button onclick="addHabit()">Add Habit</button>
      <ul id="habitList"></ul>
    </div>
  </div>
</section>

<section id="contact">
  <h2>📩 Contact</h2>
  <div class="cards">
    <div class="card">
      <img src="https://images.pexels.com/photos/3184398/pexels-photo-3184398.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Email">
      <h3>Email</h3>
      <button onclick="alert('Send Email')">Send</button>
    </div>
  </div>
</section>

<footer>
  <p>© 2026 Future Pro Hub | PWA + Installable Version</p>
</footer>

<script>
// Dark mode toggle
document.getElementById('darkToggle').addEventListener('change',()=>{document.body.classList.toggle('dark');});

// Points system
let points=0;
function gainPoints(p){points+=p;alert('Points: '+points);}

// Expense tracker
function trackExpense(){let inc=Number(document.getElementById('income').value),exp=Number(document.getElementById('expense').value);document.getElementById('balance').innerText="Balance: "+(inc-exp);}

// Habit tracker
function addHabit(){let h=document.getElementById('habit').value;if(h){let li=document.createElement('li');li.innerText=h;document.getElementById('habitList').appendChild(li);}}

// Service worker registration (PWA)
if('serviceWorker' in navigator){
  navigator.serviceWorker.register(URL.createObjectURL(new Blob([`
    const CACHE_NAME='future-pro-hub-cache-v1';
    const urlsToCache=['/','index.html','https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap'];
    self.addEventListener('install',e=>{e.waitUntil(caches.open(CACHE_NAME).then(c=>c.addAll(urlsToCache)))});
    self.addEventListener('fetch',e=>{e.respondWith(caches.match(e.request).then(r=>r||fetch(e.request)))});
  `],{type:'application/javascript'})));
}
</script>

</body>
</html>
