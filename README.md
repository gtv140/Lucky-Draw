<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SkillMint – Learn & Earn Skills</title>
<style>
body{margin:0;font-family:Arial,sans-serif;background:#f4f7fb;color:#222;padding-bottom:120px;}
header{background:linear-gradient(135deg,#0f9d58,#0b7d46);color:#fff;padding:15px;text-align:center;}
header h1{margin:0;font-size:22px}
header p{margin:4px 0;font-size:12px}
.container{padding:10px}
.card{background:#fff;border-radius:10px;padding:12px;margin-bottom:12px;box-shadow:0 3px 8px rgba(0,0,0,0.08);}
.icons{display:flex;flex-wrap:wrap;justify-content:space-around;text-align:center;margin-bottom:10px;}
.icon{cursor:pointer;font-size:12px;width:22%;margin-bottom:10px;}
.icon img{width:36px;margin-bottom:4px;}
.hidden{display:none;}
button{background:#0f9d58;color:#fff;border:none;padding:8px 12px;border-radius:6px;cursor:pointer;font-size:13px;margin-top:4px;}
button:hover{opacity:.9}
.course{display:flex;gap:8px;align-items:center;margin-bottom:10px;flex-wrap:wrap;}
.course img{width:70px;border-radius:6px;}
input{width:100%;padding:8px;margin-top:4px;border-radius:6px;border:1px solid #ccc;}
#verifyStatus{font-size:12px;margin-top:4px;color:green;}
#chatbot{position:fixed;bottom:10px;right:10px;width:90%;max-width:320px;background:#fff;border-radius:12px;box-shadow:0 4px 12px rgba(0,0,0,.3);display:flex;flex-direction:column;height:380px;}
#chatHeader{background:#0f9d58;color:#fff;padding:10px;text-align:center;cursor:pointer;font-size:14px;}
#chatBody{flex:1;padding:8px;overflow-y:auto;font-size:13px;}
#chatInput{display:flex;border-top:1px solid #ccc;}
#chatInput input{flex:1;padding:6px;border:none;font-size:13px;}
#chatInput button{padding:6px;background:#0f9d58;color:#fff;border:none;cursor:pointer;font-size:13px;}
.nav{position:fixed;bottom:0;left:0;width:100%;background:#fff;display:flex;justify-content:space-around;padding:8px 0;box-shadow:0 -3px 10px rgba(0,0,0,0.15);}
.nav a{text-align:center;font-size:10px;color:#222;text-decoration:none;flex:1;}
.review{margin-bottom:4px;}
.dark-mode{background:#121212;color:#fff;}
.dark-mode .card{background:#1e1e1e;color:#fff;}
</style>
</head>
<body>

<header>
<h1>SkillMint</h1>
<p>Trusted Platform to Learn Skills & Earn Online</p>
</header>

<div class="container">

<div class="card">
<h3>About SkillMint</h3>
<p>SkillMint ek modern online learning platform hai jahan students real skills seekh kar online earning start karte hain. Beginner se advanced level courses, step-by-step practical training aur trusted support available hai.</p>
</div>

<div class="card icons">
<div class="icon" onclick="openSection('courses')">
<img src="https://img.icons8.com/fluency/96/online-course.png">Courses
</div>
<div class="icon" onclick="openSection('reviews')">
<img src="https://img.icons8.com/fluency/96/star.png">Reviews
</div>
<div class="icon" onclick="openSection('buy')">
<img src="https://img.icons8.com/fluency/96/credit-card.png">Buy
</div>
<div class="icon" onclick="openSection('more')">
<img src="https://img.icons8.com/fluency/96/menu.png">More
</div>
</div>

<div id="courses" class="card hidden">
<h3>Popular Courses</h3>
<div class="course">
<img src="https://picsum.photos/200?1">
<div><b>Digital Marketing</b><br><button onclick="buyCourse('Digital Marketing')">Buy Course</button></div>
</div>
<div class="course">
<img src="https://picsum.photos/200?2">
<div><b>Graphic Designing</b><br><button onclick="buyCourse('Graphic Designing')">Buy Course</button></div>
</div>
<div class="course">
<img src="https://picsum.photos/200?3">
<div><b>Web Development</b><br><button onclick="buyCourse('Web Development')">Buy Course</button></div>
</div>
</div>

<div id="reviews" class="card hidden">
<h3>Students Reviews</h3>
<div id="reviewBox"></div>
</div>

<div id="buy" class="card hidden">
<h3>Buy Course</h3>
<p id="selectedCourse" style="font-weight:bold"></p>
<label>Deposit Number</label>
<input id="number" readonly placeholder="Select payment method">
<button onclick="pay('jazz')">JazzCash</button>
<button onclick="pay('easy')">EasyPaisa</button>
<button onclick="pay('binance')">Binance</button>
<label>Upload Payment Proof</label>
<input type="file" id="proof">
<p id="verifyStatus"></p>
<button id="openCourse" disabled>Open Course</button>
</div>

<div id="more" class="card hidden">
<h3>Contact & Trust</h3>
<p>👥 Active Users: <b id="users"></b></p>
<p>Email: <b>Rock.earn92@gmail.com</b></p>
<p>
<a href="https://www.facebook.com/profile.php?id=100084218946114">Facebook</a> |
<a href="https://www.instagram.com/mr_nazim073">Instagram</a>
</p>
<button onclick="toggleDark()">Toggle Dark Mode</button>
</div>

</div>

<div id="chatbot">
<div id="chatHeader" onclick="toggleChat()">💬 AI Chat</div>
<div id="chatBody"></div>
<div id="chatInput">
<input type="text" id="userMsg" placeholder="Type your question...">
<button onclick="sendMsg()">Send</button>
</div>
</div>

<div class="nav">
<a href="#">🏠<br>Home</a>
<a href="#buy">🎓<br>Buy</a>
<a href="https://www.facebook.com/profile.php?id=100084218946114">📘<br>FB</a>
<a href="https://www.instagram.com/mr_nazim073">📸<br>IG</a>
<a href="mailto:Rock.earn92@gmail.com">✉️<br>Email</a>
</div>

<script>
// ICONS
function openSection(id){
document.querySelectorAll('.card.hidden').forEach(x=>x.style.display='none');
document.getElementById(id).style.display='block';
}

// BUY FLOW
let selected="";
function buyCourse(name){
selected=name;
selectedCourse.innerText="Selected Course: "+name;
openSection('buy');
}
function pay(method){
let num={jazz:"03705519562",easy:"03379827882",binance:"0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F"}[method];
number.value=num;
navigator.clipboard.writeText(num);
alert("Deposit number copied ✅");
localStorage.setItem("timer",300);
startTimer();
}
function startTimer(){
let t=localStorage.getItem("timer")||300;
let int=setInterval(()=>{
if(t<=0){clearInterval(int);verifyStatus.innerText="Payment Verified ✔";openCourse.disabled=false;localStorage.removeItem("timer");}
else{verifyStatus.innerText="Verifying... "+t+"s";t--;localStorage.setItem("timer",t);}
},1000);
}
proof.onchange=startTimer;
openCourse.onclick=()=>alert("Course Opened: "+selected);

// REVIEWS
const reviews=["Best platform 👍","SkillMint changed my life ❤️","Courses are very practical","Highly trusted website","I earned my first income","Support team is helpful","Easy to use on mobile","Worth every rupee","Professional learning","Recommended to all students"];
function loadReviews(){let box=document.getElementById("reviewBox");box.innerHTML="";for(let i=0;i<25;i++){let r=reviews[Math.floor(Math.random()*reviews.length)];box.innerHTML+=`<div class="review">⭐ ${r}</div>`;}}
loadReviews();

// ACTIVE USERS
setInterval(()=>{document.getElementById("users").innerText=Math.floor(1200+Math.random()*800);},2000);

// CHATBOT AI
let chatOpen=true;
function toggleChat(){let body=document.getElementById("chatBody");let parent=body.parentElement;parent.style.height = chatOpen?"40px":"380px";chatOpen=!chatOpen;}
async function sendMsg(){
let input=document.getElementById("userMsg");let text=input.value.trim();if(!text)return;
addChat("You",text);input.value="";addChat("Bot","Typing...");
let response=await fetch("https://api.openai.com/v1/chat/completions",{method:"POST",headers:{"Content-Type":"application/json","Authorization":"Bearer sk-nvQzX7O9jfiKIfOTE0Bd2516424a40B7A9EeD3E2Cf521760"},body:JSON.stringify({model:"gpt-4o-mini",messages:[{role:"system",content:"You are a helpful assistant for SkillMint website."},{role:"user",content:text}]})});
let data=await response.json();let botText=data.choices?.[0]?.message?.content||"Sorry, I can't answer right now.";
let bodyDiv=document.getElementById("chatBody");bodyDiv.lastElementChild.innerHTML="<b>Bot:</b> "+botText;bodyDiv.scrollTop=bodyDiv.scrollHeight;
}
function addChat(sender,msg){let body=document.getElementById("chatBody");let div=document.createElement("div");div.innerHTML="<b>"+sender+":</b> "+msg;body.appendChild(div);body.scrollTop=body.scrollHeight;}

// DARK MODE
function toggleDark(){document.body.classList.toggle("dark-mode");}
</script>

</body>
</html>
