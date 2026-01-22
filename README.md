<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SkillMint</title>
<style>
body { margin:0; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background:#eef2f7;}
header { background: linear-gradient(90deg, #0d47a1, #1565c0); color:white; padding:25px 0; text-align:center; box-shadow:0 4px 10px rgba(0,0,0,0.2);}
header h1 { margin:0; font-size:32px; letter-spacing:1px;}
header p { margin:5px 0 0; font-size:16px;}
.hero { text-align:center; padding:40px 20px; background:#bbdefb; color:#0d47a1; border-bottom:5px solid #0d47a1;}
.hero h2 { font-size:28px; margin-bottom:15px;}
.hero p { font-size:16px; max-width:700px; margin:auto;}
.section {text-align:center; padding:40px 20px; max-width:750px; margin:40px auto; background:#f0f4f8; border-radius:15px; box-shadow:0 8px 20px rgba(0,0,0,0.1);}
.section h2 { color:#0d47a1; margin-bottom:15px;}
.section p { color:#555; font-size:15px;}
.course-section { background:#e3f2fd;}
.card-container { display:flex; flex-wrap:wrap; justify-content:center; margin-top:30px;}
.card { background:white; border-radius:12px; padding:20px; margin:10px; width:200px; box-shadow:0 6px 15px rgba(0,0,0,0.1); transition:0.3s;}
.card:hover { transform:translateY(-5px); box-shadow:0 10px 20px rgba(0,0,0,0.2);}
.card h3 { color:#0d47a1; margin-bottom:10px;}
.card p { font-size:14px; color:#555;}
button.payBtn { padding:12px 25px; margin:5px; border:none; border-radius:8px; color:white; cursor:pointer; font-size:16px; transition:0.3s;}
button.payBtn:hover { transform: scale(1.05); box-shadow:0 4px 12px rgba(0,0,0,0.2);}
#openCourse { padding:15px 50px; margin-top:20px; font-size:18px; border:none; border-radius:10px; background:#0d47a1; color:white; cursor:pointer; transition:0.3s;}
#openCourse:hover { transform: scale(1.05); box-shadow:0 4px 12px rgba(0,0,0,0.2);}
input[type=file], input[type=text] { padding:12px; width:300px; border-radius:8px; border:1px solid #ccc; margin-top:10px; text-align:center;}
footer { background:#0d47a1; color:white; padding:20px 0; text-align:center; margin-top:40px;}
@media(max-width:700px){ .card-container{ flex-direction:column; align-items:center;} input[type=file], input[type=text]{width:80%;} }
</style>
</head>
<body>

<header>
  <h1>SkillMint</h1>
  <p>Learn, Earn & Grow – Step by step for beginners</p>
</header>

<div class="hero">
  <h2>Welcome to SkillMint</h2>
  <p>Master YouTube, Freelancing, Affiliate Marketing, Website Setup & Social Media Marketing with step-by-step guidance and practical examples. Beginner-friendly for everyone!</p>
</div>

<div class="section course-section">
  <h2>🎓 Buy SkillMint Complete Course</h2>
  <p><strong>Price:</strong> <span id="priceDisplay">--</span></p>

  <h3>Select Payment Method:</h3>
  <div>
    <button onclick="setMethod('JazzCash')" class="payBtn" style="background:#2e7d32;">JazzCash</button>
    <button onclick="setMethod('EasyPaisa')" class="payBtn" style="background:#f9a825;">EasyPaisa</button>
    <button onclick="setMethod('Binance')" class="payBtn" style="background:#f3ba2f;">Binance</button>
  </div>

  <h3>Payment Details:</h3>
  <input type="text" id="depositNumber" placeholder="Deposit Number will auto-fill"><br><br>

  <h3>Upload Payment Proof:</h3>
  <input type="file" id="proof" accept="image/*"><br><br>

  <p>Send screenshot via: 
    <a href="mailto:example@example.com">Email</a> | 
    <a href="https://wa.me/03379827882" target="_blank">WhatsApp</a> | 
    <a href="https://facebook.com/yourprofile" target="_blank">Facebook</a> | 
    <a href="https://instagram.com/yourhandle" target="_blank">Instagram</a>
  </p>

  <div id="timer" style="margin-top:20px; font-size:18px; color:#e65100;"></div>
  <button id="openCourse" disabled>Open Course</button>
</div>

<div class="section">
  <h2>How SkillMint Helps You</h2>
  <div class="card-container">
    <div class="card">
      <h3>Learn Skills</h3>
      <p>Master YouTube, Freelancing, Affiliate Marketing, Social Media & more from scratch.</p>
    </div>
    <div class="card">
      <h3>Step by Step</h3>
      <p>Beginner-friendly tutorials with practical examples and exercises.</p>
    </div>
    <div class="card">
      <h3>Earn Online</h3>
      <p>Apply your skills to start freelancing, monetize YouTube & affiliate marketing.</p>
    </div>
    <div class="card">
      <h3>Guidance & Support</h3>
      <p>Clear instructions, proof verification, and real-time course access.</p>
    </div>
  </div>
</div>

<footer>
  <p>Contact us: Email | WhatsApp | Facebook | Instagram</p>
  <p>© 2026 SkillMint</p>
</footer>

<script>
let openBtn = document.getElementById('openCourse');
let timerDiv = document.getElementById('timer');
let priceDisplay = document.getElementById('priceDisplay');
let depositField = document.getElementById('depositNumber');

function setMethod(method){
    let price = 500; 
    let depositNum = "";
    if(method==='JazzCash') depositNum="03705519562";
    else if(method==='EasyPaisa') depositNum="03379827882";
    else if(method==='Binance') depositNum="0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F";

    priceDisplay.innerText = `${price} PKR`;
    depositField.value = depositNum;
}

document.getElementById('proof').addEventListener('change', function(){
    if(this.files.length > 0){
        let time = 300; 
        timerDiv.innerText = "Timer started: 05:00";
        let countdown = setInterval(()=>{
            let minutes = Math.floor(time/60);
            let seconds = time%60;
            timerDiv.innerText = `Access in: ${minutes.toString().padStart(2,'0')}:${seconds.toString().padStart(2,'0')}`;
            time--;
            if(time<0){
                clearInterval(countdown);
                timerDiv.innerText = "Payment verified! You can now access the course.";
                openBtn.disabled = false;
            }
        },1000);
    }
});

openBtn.onclick = () => {
    window.open('https://gtv140.github.io/SkillMint-complete-course-/', '_blank');
};
</script>

</body>
</html>
