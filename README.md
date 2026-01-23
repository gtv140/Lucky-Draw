<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>SkillMint</title>
<style>
body{margin:0;font-family:system-ui,sans-serif;background:#eef2ff;color:#222;overflow-x:hidden;}
#splash{position:fixed;top:0;left:0;width:100%;height:100%;background:linear-gradient(135deg,#6366f1,#22c55e);display:flex;justify-content:center;align-items:center;z-index:9999;flex-direction:column;color:#fff;font-size:24px;}
.header{background:linear-gradient(135deg,#6366f1,#22c55e);color:#fff;padding:20px 16px;text-align:center;border-bottom-left-radius:24px;border-bottom-right-radius:24px;position:sticky;top:0;z-index:100;}
.header h1{margin:0;font-size:22px;}
.header p{margin:6px 0 0;font-size:13px;opacity:.9;}
.dashboard{padding:16px;display:grid;grid-template-columns:repeat(4,1fr);gap:14px;}
.icon{background:#fff;border-radius:18px;padding:12px 6px;text-align:center;box-shadow:0 6px 16px rgba(0,0,0,.08);cursor:pointer;transition:all .2s;}
.icon img{width:42px;}
.icon span{display:block;font-size:11px;margin-top:6px;}
.icon.active{box-shadow:0 8px 20px rgba(0,0,0,.2);transform:translateY(-2px);}
.section{display:none;padding:14px;opacity:0;transition:opacity .4s;}
.section.show{display:block;opacity:1;}
.card{background:#fff;border-radius:18px;padding:16px;margin-bottom:14px;box-shadow:0 6px 18px rgba(0,0,0,.08);}
.review{display:flex;gap:10px;margin-bottom:12px;}
.review img{width:42px;height:42px;border-radius:50%;}
.review b{font-size:13px;}
.review p{margin:2px 0 0;font-size:12px;color:#555;}
button{width:100%;border:none;padding:10px;border-radius:12px;background:linear-gradient(135deg,#6366f1,#22c55e);color:#fff;font-size:14px;margin-top:6px;cursor:pointer;transition:all .3s;}
button:hover{opacity:.9;}
.nav{position:fixed;bottom:0;left:0;width:100%;background:#fff;display:flex;justify-content:space-around;padding:8px 0;box-shadow:0 -4px 12px rgba(0,0,0,.15);z-index:999;}
.nav a{text-decoration:none;font-size:11px;color:#222;text-align:center;flex:1;transition:all .2s;}
.nav a.active{color:#22c55e;font-weight:bold;transform:translateY(-2px);}
.loader{border:4px solid #f3f3f3;border-top:4px solid #6366f1;border-radius:50%;width:24px;height:24px;animation:spin 1s linear infinite;margin:auto;display:none;}
@keyframes spin{0%{transform:rotate(0deg);}100%{transform:rotate(360deg);}}
</style>
</head>
<body>
<div id="splash">SkillMint Loading...</div>
<div class="header">
<h1>SkillMint</h1>
<p>Trusted Digital Skills Platform</p>
</div>
<div class="dashboard">
  <div class="icon" onclick="openSec('courses',this)">
    <img src="https://img.icons8.com/fluency/96/online-course.png">
    <span>Courses</span>
  </div>
  <div class="icon" onclick="openSec('reviews',this)">
    <img src="https://img.icons8.com/fluency/96/group.png">
    <span>Reviews</span>
  </div>
  <div class="icon" onclick="openSec('buy',this)">
    <img src="https://img.icons8.com/fluency/96/credit-card.png">
    <span>Buy</span>
  </div>
  <div class="icon" onclick="openSec('contact',this)">
    <img src="https://img.icons8.com/fluency/96/info.png">
    <span>About</span>
  </div>
</div>
<div id="courses" class="section">
  <div class="loader" id="coursesLoader"></div>
  <div class="card">
    <h3>Available Courses</h3>
    <p>Digital Marketing, Web Development, Graphic Designing, AI Tools, Freelancing</p>
    <button onclick="buyCourse()">Buy Course</button>
  </div>
</div>
<div id="reviews" class="section">
  <div class="loader" id="reviewsLoader"></div>
  <div class="card">
    <h3>Student Reviews</h3>
    <div id="reviewList"></div>
  </div>
</div>
<div id="buy" class="section">
  <div class="loader" id="buyLoader"></div>
  <div class="card">
    <h3>Payment</h3>
    <p>JazzCash / EasyPaisa / Binance supported</p>
    <p>Deposit Number: <b id="depositNum">03705519562</b></p>
    <button onclick="startPayment()">Start Verification</button>
    <p id="verifyStatus"></p>
  </div>
</div>
<div id="contact" class="section">
  <div class="loader" id="aboutLoader"></div>
  <div class="card">
    <h3>About SkillMint</h3>
    <p>SkillMint is a trusted platform helping students learn digital skills & earn online.</p>
    <p>Email: Rock.earn92@gmail.com</p>
    <p>👥 Active Users: <b id="users">1200</b></p>
  </div>
</div>
<div class="nav">
  <a href="#" class="active">🏠<br>Home</a>
  <a onclick="openSec('courses',null)">🎓<br>Courses</a>
  <a onclick="openSec('reviews',null)">👥<br>Reviews</a>
  <a href="mailto:Rock.earn92@gmail.com">✉️<br>Email</a>
</div>
<script>
setTimeout(()=>document.getElementById('splash').style.display='none',1500);
function showLoader(id){document.getElementById(id).style.display='block';}
function hideLoader(id){document.getElementById(id).style.display='none';}
function openSec(id,el){
  document.querySelectorAll('.section').forEach(s=>{s.classList.remove('show');});
  showLoader(id+'Loader');
  setTimeout(()=>{
    hideLoader(id+'Loader');
    document.getElementById(id).classList.add('show');
  },800);
  if(el){document.querySelectorAll('.icon').forEach(ic=>ic.classList.remove('active'));el.classList.add('active');}
  window.scrollTo({top:0,behavior:'smooth'});
  document.querySelectorAll('.nav a').forEach(nav=>nav.classList.remove('active'));
}
const names=["Ali Khan","Ayesha Malik","Usman Raza","Hina Shaikh","Bilal Ahmed","Zain Abbas","Maria Noor","Saad Iqbal","Sana Fatima","Hamza Qureshi","Rabia Aslam","Omer Farooq","Nimra Zahid","Hassan Ali","Laiba Khan","Arslan Butt","Iqra Javed","Shahzaib Tariq","Maham Rehman","Danish Akhtar","Fiza Noor","Kashif Mehmood","Anum Saleem","Taha Rauf","Mehwish Ali"];
function loadReviews(){
  let box=document.getElementById("reviewList"); box.innerHTML="";
  for(let i=0;i<25;i++){
    let n=names[Math.floor(Math.random()*names.length)];
    let img=Math.floor(Math.random()*70);
    box.innerHTML+=`<div class="review"><img src="https://i.pravatar.cc/100?img=${img}"><div><b>${n}</b><p>SkillMint helped me gain practical skills and start earning online. Trusted & easy!</p></div></div>`;
  }
}
loadReviews();
let timerInterval;
function startPayment(){
  document.getElementById('verifyStatus').innerText='Processing Payment...';
  setTimeout(()=>{
    let t = parseInt(localStorage.getItem('timer')) || 60;
    document.getElementById('verifyStatus').innerText='Verifying: '+t+'s';
    clearInterval(timerInterval);
    timerInterval=setInterval(()=>{
      t--;
      document.getElementById('verifyStatus').innerText='Verifying: '+t+'s';
      localStorage.setItem('timer',t);
      if(t<=0){clearInterval(timerInterval);document.getElementById('verifyStatus').innerText='Payment Verified ✔';localStorage.removeItem('timer');}
    },1000);
  },1500);
}
function buyCourse(){
  document.getElementById('coursesLoader').style.display='block';
  setTimeout(()=>{
    document.getElementById('coursesLoader').style.display='none';
    alert('Course access after payment');
  },1500);
}
function updateUsers(){
  let users = parseInt(localStorage.getItem('users')) || 1200;
  users += Math.floor(Math.random()*5);
  document.getElementById('users').innerText=users;
  localStorage.setItem('users',users);
}
setInterval(updateUsers,2000);
</script>
</body>
</html>
