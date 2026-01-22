<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SkillMint</title>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;}
body{font-family:'Roboto',sans-serif;background:#f5f5f5;color:#111;}
a{text-decoration:none;color:inherit;}
.container{max-width:1000px;margin:auto;padding:20px;}

/* Header */
header{text-align:center;margin-bottom:30px;}
header h1{font-size:32px;color:#222;font-weight:700;margin-bottom:8px;}
header p{font-size:16px;color:#555;}

/* Sections */
.section{margin-bottom:25px;}
h2{color:#333;margin-bottom:15px;text-align:center;font-size:22px;}

/* Cards */
.card-container{display:flex;flex-wrap:wrap;justify-content:center;gap:15px;}
.card{background:white;border-radius:12px;box-shadow:0 3px 10px rgba(0,0,0,0.1);padding:15px;width:220px;transition:0.3s;}
.card:hover{box-shadow:0 6px 20px rgba(0,0,0,0.15);}
.card img{width:50px;height:50px;margin-bottom:10px;}
.card h3{color:#222;margin-bottom:6px;font-size:16px;}
.card p{font-size:14px;color:#555;}

/* Payment & Inputs */
.payBtn{padding:12px 0;margin:5px 0;border:none;border-radius:8px;color:white;background:#007BFF;cursor:pointer;font-weight:bold;width:100%;transition:0.3s;}
.payBtn:hover{background:#0056b3;}
#openCourse{padding:12px 0;font-size:16px;border:none;border-radius:8px;background:#28a745;color:white;cursor:pointer;width:100%;margin-top:10px;transition:0.3s;}
#openCourse:hover{background:#218838;}
input[type=file], input[type=text]{padding:10px;width:95%;border-radius:6px;border:1px solid #ccc;margin:5px auto;display:block;}

/* Testimonials */
.testimonial{background:white;border-radius:10px;padding:12px;margin:10px 0;box-shadow:0 3px 10px rgba(0,0,0,0.1);}
.testimonial p{font-style:italic;color:#555;font-size:14px;}
.testimonial h4{margin-top:8px;color:#007BFF;font-size:14px;text-align:right;}

/* FAQ */
.faq{background:#fff;border-radius:8px;padding:10px;margin:8px 0;box-shadow:0 2px 8px rgba(0,0,0,0.08);}
.faq h4{cursor:pointer;color:#007BFF;}
.faq p{display:none;padding-left:10px;color:#555;font-size:14px;}

/* Chatbot */
#chatUserInput{padding:10px;width:95%;border-radius:6px;border:1px solid #ccc;margin-bottom:8px;}

/* Footer */
footer{background:#222;color:white;padding:15px 10px;text-align:center;border-radius:8px;font-size:14px;margin-top:20px;}

/* Responsive */
@media(max-width:600px){
  .card-container{flex-direction:column;align-items:center;}
  h2{font-size:20px;}
  header h1{font-size:28px;}
  .card{width:90%;}
  .payBtn,#openCourse{font-size:14px;}
}
</style>
</head>
<body>
<div class="container">

<!-- Header -->
<header>
<h1>SkillMint</h1>
<p>Learn, Earn & Grow Online – Step-by-step guidance for beginners</p>
<img src="https://cdn-icons-png.flaticon.com/512/3135/3135715.png" alt="SkillMint Logo" width="70">
</header>

<!-- How SkillMint Helps -->
<div class="section">
<h2>How SkillMint Helps You</h2>
<div class="card-container">
<div class="card">
<img src="https://cdn-icons-png.flaticon.com/512/1384/1384060.png" alt="YouTube">
<h3>Learn Skills</h3>
<p>Master YouTube, Freelancing, Affiliate Marketing & Social Media from scratch.</p>
</div>
<div class="card">
<img src="https://cdn-icons-png.flaticon.com/512/1828/1828843.png" alt="Step">
<h3>Step by Step</h3>
<p>Beginner-friendly tutorials with practical examples & exercises.</p>
</div>
<div class="card">
<img src="https://cdn-icons-png.flaticon.com/512/1170/1170576.png" alt="Money">
<h3>Earn Online</h3>
<p>Apply your skills to start freelancing, monetize YouTube & affiliate marketing safely.</p>
</div>
<div class="card">
<img src="https://cdn-icons-png.flaticon.com/512/565/565313.png" alt="Support">
<h3>Guidance & Support</h3>
<p>Clear instructions, proof verification, and real-time course access.</p>
</div>
</div>
</div>

<!-- Testimonials -->
<div class="section">
<h2>What Our Learners Say</h2>
<div class="testimonial">
<p>"I learned YouTube and freelancing from scratch with SkillMint. Now I earn online confidently!"</p>
<h4>- Ali R.</h4>
</div>
<div class="testimonial">
<p>"Step-by-step tutorials are easy to follow, even for beginners. Highly recommended!"</p>
<h4>- Sara K.</h4>
</div>
</div>

<!-- Buy Course Section -->
<div class="section">
<h2>Buy SkillMint Complete Course</h2>
<p><strong>Price:</strong> <input type="text" id="priceDisplay" readonly></p>
<p><strong>Deposit Number:</strong> <input type="text" id="depositNumber" readonly> <span id="copyMsg">Copied!</span></p>
<h3>Select Payment Method:</h3>
<button class="payBtn" onclick="setMethod('JazzCash')">JazzCash</button>
<button class="payBtn" onclick="setMethod('EasyPaisa')">EasyPaisa</button>
<button class="payBtn" onclick="setMethod('Binance')">Binance</button>
<h3>Upload Payment Proof</h3>
<input type="file" id="proof" accept="image/*">
<p style="font-size:14px; text-align:center;">Send proof via: 
<a href="mailto:example@example.com">Email</a> | 
<a href="https://wa.me/03379827882" target="_blank">WhatsApp</a> | 
<a href="https://facebook.com/yourprofile" target="_blank">Facebook</a> | 
<a href="https://instagram.com/yourhandle" target="_blank">Instagram</a>
</p>
<div id="timer"></div>
<button id="openCourse" disabled>Open Course</button>
</div>

<!-- FAQ -->
<div class="section">
<h2>Frequently Asked Questions</h2>
<div class="faq" onclick="this.querySelector('p').style.display=this.querySelector('p').style.display==='block'?'none':'block'">
<h4>How long does it take to verify payment?</h4>
<p>Verification usually takes 5 minutes after uploading your proof.</p>
</div>
<div class="faq" onclick="this.querySelector('p').style.display=this.querySelector('p').style.display==='block'?'none':'block'">
<h4>What if my payment proof doesn’t work?</h4>
<p>Ensure the screenshot clearly shows the transaction details and try re-uploading.</p>
</div>
</div>

<!-- Chat Bot Section -->
<div class="section">
<h2>Ask SkillMint Bot ❓</h2>
<input type="text" id="chatUserInput" placeholder="Type your question here...">
<button onclick="chatBotReply()" style="padding:10px 20px; background:#007BFF; color:white; border:none; border-radius:8px; cursor:pointer;">Ask</button>
<p id="chatResponse" style="margin-top:15px; color:#333;"></p>
</div>

<footer>
<p>Contact us: Email | WhatsApp | Facebook | Instagram</p>
<p>© 2026 SkillMint</p>
</footer>

<script>
// Payment auto-fill & copy
let openBtn=document.getElementById('openCourse');
let timerDiv=document.getElementById('timer');
let priceDisplay=document.getElementById('priceDisplay');
let depositField=document.getElementById('depositNumber');
let proofInput=document.getElementById('proof');
let copyMsg=document.getElementById('copyMsg');

function setMethod(method){
    let price=500;
    let depositNum="";
    if(method==='JazzCash') depositNum="03705519562";
    else if(method==='EasyPaisa') depositNum="03379827882";
    else if(method==='Binance') depositNum="0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F";
    priceDisplay.value=price+" PKR";
    depositField.value=depositNum;
    navigator.clipboard.writeText(depositNum).then(()=>{
        copyMsg.style.display="inline";
        setTimeout(()=>{ copyMsg.style.display="none"; },2000);
    });
    localStorage.setItem('paymentMethod',method);
    localStorage.setItem('depositNum',depositNum);
    localStorage.setItem('price',price);
}

// Countdown timer
let savedTime=localStorage.getItem('timer')||0;
let savedProof=localStorage.getItem('proofUploaded')==='true';
if(savedProof && savedTime>0) startCountdown(parseInt(savedTime));

proofInput.addEventListener('change',function(){
    if(this.files.length>0){
        localStorage.setItem('proofUploaded','true');
        startCountdown(300);
    }
});

function startCountdown(duration){
    let time=duration;
    localStorage.setItem('timer',time);
    let countdown=setInterval(()=>{
        let minutes=Math.floor(time/60);
        let seconds=time%60;
        timerDiv.innerText=`Access in: ${minutes.toString().padStart(2,'0')}:${seconds.toString().padStart(2,'0')}`;
        time--;
        localStorage.setItem('timer',time);
        if(time<0){
            clearInterval(countdown);
            timerDiv.innerText="Payment verified! You can now access the course.";
            openBtn.disabled=false;
        }
    },1000);
}

openBtn.onclick=()=>{
    window.open('https://gtv140.github.io/SkillMint-complete-course-/','_blank');
};

// Chatbot system
const botData = {
    "what is skillmint": "SkillMint is a learning platform that helps beginners learn online skills like YouTube, freelancing, affiliate marketing & more.",
    "how do i buy the course": "To buy the course: choose a payment method → deposit amount → upload your payment screenshot → wait 5 minutes → access your course.",
    "what payment methods do you accept": "We accept JazzCash, EasyPaisa & Binance (crypto).",
    "how long does verification take": "Payment verification usually takes about 5 minutes after uploading your proof.",
    "is this course suitable for beginners": "Yes! All tutorials are beginner friendly with step‑by‑step explanations."
};

function chatBotReply(){
    let userQ=document.getElementById('chatUserInput').value.trim().toLowerCase();
    let reply=botData[userQ]||"Sorry, I don't have an answer for that yet. Try using simple words or check the FAQ section!";
    document.getElementById('chatResponse').innerText=reply;
}
</script>
</body>
</html>
