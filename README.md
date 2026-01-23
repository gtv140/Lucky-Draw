<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SkillMint - AI Chat + Courses</title>

<style>
body{margin:0;font-family:Arial,sans-serif;background:#f4f7fb;color:#222;padding-bottom:100px;}
header{background:linear-gradient(135deg,#0f9d58,#0b7d46);color:#fff;padding:18px;text-align:center;}
header h1{margin:0;font-size:24px}
header p{margin:4px 0;font-size:13px}
.container{padding:15px}
.card{background:#fff;border-radius:10px;padding:14px;margin-bottom:14px;box-shadow:0 4px 8px rgba(0,0,0,0.08);}
button{background:#0f9d58;color:#fff;border:none;padding:10px 14px;border-radius:8px;cursor:pointer;font-size:14px;margin-top:8px;}
button:hover{opacity:.9}
input,textarea{width:100%;padding:10px;border:1px solid #ccc;border-radius:8px;margin-top:6px;}
.hidden{display:none;}
#chatbot{position:fixed;bottom:20px;right:20px;width:320px;background:#fff;border-radius:12px;box-shadow:0 4px 12px rgba(0,0,0,0.2);overflow:hidden;display:flex;flex-direction:column;height:420px;}
#chatHeader{background:#0f9d58;color:#fff;padding:10px;text-align:center;cursor:pointer;font-weight:bold;}
#chatBody{flex:1;padding:10px;overflow-y:auto;font-size:14px;}
#chatInput{display:flex;border-top:1px solid #ccc;}
#chatInput input{flex:1;padding:8px;border:none;}
#chatInput button{padding:8px;background:#0f9d58;color:#fff;border:none;cursor:pointer;}
.nav{position:fixed;bottom:0;left:0;width:100%;background:#fff;display:flex;justify-content:space-around;padding:10px 0;box-shadow:0 -4px 12px rgba(0,0,0,0.15);}
.nav a{text-align:center;font-size:11px;color:#222;text-decoration:none;}
</style>

</head>
<body>

<header>
<h1>SkillMint</h1>
<p>Learn Skills • Earn Online • AI Chat & Courses</p>
</header>

<div class="container">

<div class="card">
<h3>About SkillMint</h3>
<p>SkillMint ek modern online platform hai jahan beginners real skills seekh kar online earning start karte hain. Courses step‑by‑step, practical aur trusted hain.</p>
</div>

<div class="card">
<h3>Courses</h3>
<div class="course">
<b>Digital Marketing</b><br>
<button onclick="selectCourse('Digital Marketing')">Buy Course</button>
</div>
<div class="course">
<b>Graphic Designing</b><br>
<button onclick="selectCourse('Graphic Designing')">Buy Course</button>
</div>
<div class="course">
<b>Web Development</b><br>
<button onclick="selectCourse('Web Development')">Buy Course</button>
</div>
</div>

<div class="card" id="buySection" style="display:none">
<h3>Buy Course</h3>
<p id="selectedCourse"></p>

<label>Deposit Number</label>
<input id="depositNumber" readonly>

<button onclick="pay('jazz')">JazzCash</button>
<button onclick="pay('easy')">EasyPaisa</button>
<button onclick="pay('binance')">Binance</button>

<label>Upload Payment Proof</label>
<input type="file" id="proof">

<p id="verifyStatus"></p>
<button id="openBtn" disabled>Open Course</button>
</div>

</div>

<!-- AI CHATBOT -->
<div id="chatbot">
<div id="chatHeader" onclick="toggleChat()">🤖 AI Chat</div>
<div id="chatBody"></div>
<div id="chatInput">
<input type="text" id="userMsg" placeholder="Ask your question...">
<button onclick="sendMsg()">Send</button>
</div>
</div>

<div class="nav">
<a href="#">🏠<br>Home</a>
<a href="#buySection">🎓<br>Buy</a>
<a href="https://www.facebook.com/profile.php?id=100084218946114">📘<br>FB</a>
<a href="https://www.instagram.com/mr_nazim073">📸<br>IG</a>
<a href="mailto:Rock.earn92@gmail.com">✉️<br>Email</a>
</div>

<script>
// ===== COURSE BUY =====
let currentCourse="";
function selectCourse(name){
 document.getElementById("selectedCourse").innerText="Selected: "+name+" (500 PKR)";
 document.getElementById("buySection").style.display="block";
}

function pay(method){
 let nums = {
   jazz:"03705519562",
   easy:"03379827882",
   binance:"0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F"
 };
 let num=nums[method];
 depositNumber.value=num;
 navigator.clipboard.writeText(num);
 alert("Deposit number copied");
}

// ===== AI CHATBOT =====
let chatOpen=true;
function toggleChat(){
 let body=document.getElementById("chatBody");
 let parent=body.parentElement;
 parent.style.height = chatOpen?"40px":"420px";
 chatOpen=!chatOpen;
}

async function sendMsg(){
 let input=document.getElementById("userMsg");
 let text=input.value.trim();
 if(!text) return;
 addChat("You",text);
 input.value="";
 addChat("Bot","Typing...");

 // ---- GPT API CALL ----
 let response = await fetch("https://api.openai.com/v1/chat/completions", {
   method:"POST",
   headers:{
     "Content-Type":"application/json",
     "Authorization":"Bearer YOUR_OPENAI_API_KEY"
   },
   body:JSON.stringify({
     model:"gpt-4o-mini",
     messages:[
       {role:"system",content:"You are a helpful assistant for SkillMint website."},
       {role:"user",content:text}
     ]
   })
 });

 let data = await response.json();
 let botText = data.choices?.[0]?.message?.content || "Sorry, I can't answer right now.";

 // replace last "Typing..." message
 let bodyDiv=document.getElementById("chatBody");
 bodyDiv.lastElementChild.innerHTML = "<b>Bot:</b> "+botText;
 bodyDiv.scrollTop=bodyDiv.scrollHeight;
}
// chat add helper
function addChat(sender,msg){
 let body=document.getElementById("chatBody");
 let div=document.createElement("div");
 div.innerHTML="<b>"+sender+":</b> "+msg;
 body.appendChild(div);
 body.scrollTop=body.scrollHeight;
}
</script>

</body>
</html>
