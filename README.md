<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SkillMint</title>

<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:Arial,Helvetica,sans-serif}
body{background:#f4f6fb;color:#111;padding-bottom:90px}
.container{max-width:900px;margin:auto;padding:14px}
section{margin-bottom:26px}

/* Header */
header{text-align:center;padding:20px 10px}
header h1{font-size:26px}
header p{font-size:14px;color:#555;margin-top:6px}

/* Cards */
.cards{display:flex;flex-direction:column;gap:12px}
.card{
 background:#fff;
 border-radius:14px;
 padding:16px;
 box-shadow:0 6px 18px rgba(0,0,0,.08)
}
.card h3{font-size:16px;margin-bottom:6px}
.card p{font-size:14px;color:#555}

/* Titles */
h2{font-size:20px;margin-bottom:12px;text-align:center}

/* Buttons */
.btn{
 width:100%;
 padding:14px;
 border:none;
 border-radius:12px;
 background:#2563eb;
 color:#fff;
 font-size:15px;
 margin-top:8px
}
.btn.green{background:#16a34a}

/* Inputs */
input{
 width:100%;
 padding:12px;
 border-radius:10px;
 border:1px solid #ccc;
 margin-top:6px;
 font-size:14px
}

/* Reviews */
.review{
 background:#fff;
 border-radius:12px;
 padding:14px;
 box-shadow:0 4px 14px rgba(0,0,0,.08)
}
.review p{font-size:14px}
.review span{font-size:13px;color:#2563eb}

/* FAQ */
.faq{
 background:#fff;
 border-radius:12px;
 padding:14px;
 box-shadow:0 4px 12px rgba(0,0,0,.06)
}
.faq h4{font-size:15px}
.faq p{display:none;font-size:14px;color:#555;margin-top:6px}

/* Chatbot */
.bot-qs{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:8px}
.bot-qs button{
 background:#eef2ff;
 border:none;
 padding:6px 10px;
 border-radius:8px;
 font-size:12px
}

/* Bottom Nav */
.bottom-nav{
 position:fixed;
 bottom:0;left:0;
 width:100%;
 background:#fff;
 display:flex;
 justify-content:space-around;
 padding:10px 0;
 box-shadow:0 -3px 12px rgba(0,0,0,.15)
}
.bottom-nav a{text-align:center;font-size:11px;color:#444}

/* WhatsApp */
.whatsapp{
 position:fixed;
 right:16px;
 bottom:90px;
 background:#25D366;
 color:#fff;
 padding:14px;
 border-radius:50%;
 font-size:22px
}
</style>
</head>

<body>

<div class="container">

<header>
<h1>SkillMint</h1>
<p>Beginner-friendly platform to learn skills & earn online</p>
</header>

<section id="learn-skills">
<h2>What You Will Learn</h2>
<div class="cards">
 <div class="card"><h3>YouTube Earning</h3><p>Channel setup, content, SEO, monetization step-by-step.</p></div>
 <div class="card"><h3>Freelancing</h3><p>Fiverr & Upwork setup, gigs, clients & earnings.</p></div>
 <div class="card"><h3>Affiliate Marketing</h3><p>Products promote karna aur commission earn karna.</p></div>
 <div class="card"><h3>Social Media Growth</h3><p>Instagram & Facebook organic growth strategies.</p></div>
</div>
</section>

<section>
<h2>Student Reviews</h2>
<div class="review"><p>“Mujhe YouTube bilkul zero se samajh aya.”</p><span>— Ali</span></div>
<br>
<div class="review"><p>“Freelancing ka complete roadmap mil gaya.”</p><span>— Sara</span></div>
</section>

<section id="buy-course">
<h2>Buy SkillMint Course</h2>

<label>Price</label>
<input id="price" readonly placeholder="Select payment method">

<label>Deposit Number</label>
<input id="number" readonly placeholder="Auto fill hoga">

<button class="btn" onclick="pay('JazzCash')">JazzCash</button>
<button class="btn" onclick="pay('EasyPaisa')">EasyPaisa</button>
<button class="btn" onclick="pay('Binance')">Binance</button>

<label>Upload Payment Proof</label>
<input type="file" id="proof">

<p id="timer" style="margin-top:8px;font-size:14px"></p>
<button class="btn green" id="openCourse" disabled>Open Course</button>
</section>

<section id="faq">
<h2>FAQ</h2>
<div class="faq"><h4>Verification time?</h4><p>Normally 5 minutes.</p></div>
<br>
<div class="faq"><h4>Beginners ke liye?</h4><p>Yes, bilkul zero level se.</p></div>
</section>

<section id="chatbot">
<h2>SkillMint Bot 🤖</h2>

<div class="bot-qs">
<button onclick="ask('skillmint')">What is SkillMint?</button>
<button onclick="ask('buy')">How to buy?</button>
<button onclick="ask('payment')">Payment methods?</button>
<button onclick="ask('beginner')">For beginners?</button>
</div>

<input id="q" placeholder="Type your question">
<button class="btn" onclick="reply()">Ask</button>
<p id="ans" style="margin-top:8px"></p>
</section>

</div>

<a class="whatsapp" href="https://wa.me/923379827882" target="_blank">💬</a>

<div class="bottom-nav">
<a href="#learn-skills">🏠<br>Home</a>
<a href="#buy-course">🎓<br>Course</a>
<a href="#faq">❓<br>FAQ</a>
<a href="#chatbot">🤖<br>Bot</a>
</div>

<script>
function pay(m){
 price.value="500 PKR";
 if(m==="JazzCash") number.value="03705519562";
 if(m==="EasyPaisa") number.value="03379827882";
 if(m==="Binance") number.value="0xBfB9E5b2baA8202850DfFb2CB1D739278b83f47F";
 navigator.clipboard.writeText(number.value);
}

proof.onchange=()=>{
 let t=300;
 let i=setInterval(()=>{
  timer.innerText="Access unlock in "+t+" seconds";
  t--;
  if(t<0){
   clearInterval(i);
   timer.innerText="Access unlocked ✔";
   openCourse.disabled=false;
  }
 },1000);
};

openCourse.onclick=()=>{
 window.open("https://gtv140.github.io/SkillMint-complete-course-/","_blank");
};

const bot=[
 {k:["skillmint"],r:"SkillMint ek beginner platform hai jahan online earning skills sikhai jati hain."},
 {k:["buy"],r:"Payment select karo, proof upload karo, 5 min baad access milega."},
 {k:["payment"],r:"JazzCash, EasyPaisa aur Binance available hain."},
 {k:["beginner"],r:"Yes, bilkul beginners ke liye hai."}
];
function reply(){
 let t=q.value.toLowerCase(),r="Simple words use karo.";
 bot.forEach(b=>{if(b.k.some(k=>t.includes(k)))r=b.r});
 ans.innerText=r;
}
function ask(x){q.value=x;reply();}
document.querySelectorAll(".faq h4").forEach(f=>{
 f.onclick=()=>f.nextElementSibling.style.display=
 f.nextElementSibling.style.display==="block"?"none":"block";
});
</script>

</body>
</html>
