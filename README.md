<html lang="en">
<head>
<meta charset="UTF-8">
<title>SkillMint – Learn Skills & Earn Online</title>
<meta name="description" content="SkillMint helps you learn digital skills and earn online via AdSense, affiliate marketing, and digital services.">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
*{box-sizing:border-box;}
body{margin:0;font-family:Arial,sans-serif;background:#f4f6f9;color:#222;transition:background 0.3s, color 0.3s;}
header{background:linear-gradient(135deg,#0f2027,#203a43,#2c5364);color:#fff;padding:80px 20px;text-align:center;position:relative;}
header h1{margin:0;font-size:48px;line-height:1.2;}
header p{margin-top:15px;font-size:20px;opacity:0.9;}
header .cta-btn{display:inline-block;margin-top:20px;padding:15px 30px;background:#25D366;color:#fff;text-decoration:none;border-radius:6px;font-weight:bold;font-size:16px;transition:background 0.3s;}
header .cta-btn:hover{background:#128C7E;}
nav{background:#111;padding:12px;text-align:center;position:sticky;top:0;z-index:1000;}
nav a{color:#fff;margin:0 12px;text-decoration:none;font-weight:bold;font-size:14px;}
section{background:#fff;margin:25px auto;padding:30px;max-width:1000px;border-radius:12px;box-shadow:0 6px 15px rgba(0,0,0,0.08);}
h2{margin-top:0;text-align:center;}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:20px;}
.card{background:#f9fafb;padding:20px;border-radius:10px;border:1px solid #e5e7eb;transition:transform 0.3s ease, box-shadow 0.3s;}
.card:hover{transform:translateY(-5px);box-shadow:0 8px 20px rgba(0,0,0,0.2);}
.card img{width:100%;border-radius:8px;margin-bottom:10px;}
.btn{display:inline-block;margin-top:15px;padding:12px 22px;background:#25D366;color:#fff;text-decoration:none;border-radius:6px;font-weight:bold;font-size:14px;transition:background 0.3s;}
.btn:hover{background:#128C7E;}
footer{background:#111;color:#fff;text-align:center;padding:20px;font-size:14px;}
@media(max-width:600px){nav a{display:block;margin:8px 0;}}
#scrollBtn{position:fixed;bottom:20px;right:20px;background:#25D366;color:#fff;padding:12px 15px;border:none;border-radius:50%;cursor:pointer;display:none;font-size:18px;z-index:999;}
.dark-mode{background:#121212;color:#e0e0e0;}
.dark-mode header{background:linear-gradient(135deg,#2c3e50,#34495e,#1c1c1c);}
.dark-mode nav{background:#222;}
.dark-mode section{background:#1e1e1e;color:#e0e0e0;box-shadow:0 6px 15px rgba(0,0,0,0.3);}
.dark-mode .card{background:#2a2a2a;border:1px solid #555;}
#earningGuide {display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.85);color:#fff;overflow-y:auto;z-index:9999;padding:20px;}
#earningGuide .guide-content{max-width:800px;margin:50px auto;background:#222;border-radius:12px;padding:25px;box-shadow:0 10px 30px rgba(0,0,0,0.5);}
#earningGuide h2{color:#25D366;}
#earningGuide button{background:#25D366;color:#fff;padding:10px 15px;border:none;border-radius:5px;margin-top:15px;cursor:pointer;}
#earningGuide ul{margin-left:20px;}
input, textarea{padding:10px;width:100%;margin-bottom:10px;border-radius:5px;border:1px solid #ccc;}
</style>
</head>

<body>

<header>
<h1>SkillMint</h1>
<p>Learn Skills. Build Your Online Income.</p>
<a href="#earn" class="cta-btn">Start Learning & Earning</a>
<button onclick="toggleDarkMode()" style="position:absolute;top:15px;right:15px;padding:10px 12px;border:none;border-radius:5px;cursor:pointer;">🌙</button>
</header>

<nav>
<a href="#about">About</a>
<a href="#earn">Earn</a>
<a href="#services">Services</a>
<a href="#affiliate">Affiliate</a>
<a href="#blog">Blog</a>
<a href="#contact">Contact</a>
</nav>

<section id="about">
<h2>About SkillMint</h2>
<p>SkillMint is your digital learning & earning hub. Learn practical online skills and turn them into real income with AdSense, affiliate marketing, and digital services. Beginner-friendly & future-ready.</p>
<img src="https://picsum.photos/800/300?grayscale&random=1" alt="Learning Skills Image">
</section>

<section id="earn">
<h2>💰 How You Can Earn</h2>
<div class="grid">
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=2" alt="Earn Money Online">
<h3>Google AdSense</h3>
<p>Monetize your content by displaying ads. Drive traffic & earn passive income.</p>
<div class="ads-placeholder">AdSense Placeholder</div>
</div>
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=3" alt="Affiliate Marketing">
<h3>Affiliate Marketing</h3>
<p>Promote products & earn commission for every sale.</p>
<a class="btn" href="#">Visit Affiliate Offer</a>
</div>
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=4" alt="Digital Services">
<h3>Digital Services</h3>
<p>Offer services like website setup, YouTube SEO, thumbnails & logos.</p>
<a class="btn" href="https://wa.me/03705519562">Contact on WhatsApp</a>
</div>
</div>
</section>

<section id="services">
<h2>🛠 Services We Offer</h2>
<div class="grid">
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=5" alt="Website Services">
<p>Website Design & GitHub Pages Setup</p>
</div>
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=6" alt="YouTube SEO">
<p>YouTube SEO & Channel Growth</p>
</div>
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=7" alt="Thumbnail Design">
<p>Thumbnail & Logo Design</p>
</div>
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=8" alt="Affiliate Website">
<p>Affiliate Website Creation</p>
</div>
</div>
<a class="btn" href="https://wa.me/03705519562">Contact on WhatsApp</a>
</section>

<section id="affiliate">
<h2>🔥 Recommended Tools & Affiliate Offers</h2>
<div class="grid">
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=9" alt="Affiliate Tools">
<p>Promote trusted tools for earning online. Small commission possible.</p>
<a class="btn" href="#">Visit Affiliate Offer</a>
</div>
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=10" alt="Affiliate Tools">
<p>Promote more products & services. Monetize your traffic.</p>
<a class="btn" href="#">Visit Affiliate Offer</a>
</div>
</div>
</section>

<section id="blog">
<h2>📝 Blog & Updates</h2>
<div class="grid">
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=11" alt="Blog Writing">
<p>Step by step earning guide for beginners in digital marketing.</p>
</div>
<div class="card">
<img src="https://picsum.photos/400/250?grayscale&random=12" alt="Blog Updates">
<p>Top affiliate programs to start monetizing your website today.</p>
</div>
</div>
</section>

<!-- ✅ Simple Contact Form -->
<section id="contact">
<h2>📞 Contact & Support</h2>
<form action="mailto:rock.earn92@gmail.com" method="post" enctype="text/plain" style="margin-top:15px;">
  <input type="text" name="Name" placeholder="Your Name" required>
  <input type="email" name="Email" placeholder="Your Email" required>
  <textarea name="Message" placeholder="Your Message" required></textarea>
  <button type="submit" class="btn">Send Message</button>
</form>

<p style="margin-top:15px;font-weight:bold;font-size:16px;">Or Contact Directly on WhatsApp!</p>
<a href="https://wa.me/03705519562" class="btn">WhatsApp</a>

<div style="margin-top:15px;">
  <a href="https://www.facebook.com/profile.php?id=100084218946114" target="_blank" class="btn" style="background:#3b5998;">Facebook</a>
  <a href="https://www.instagram.com/mr_nazim073?igsh=MXd4d2hmcWNvNjVsdQ==" target="_blank" class="btn" style="background:#E1306C;">Instagram</a>
</div>

<img src="https://picsum.photos/800/300?grayscale&random=14" alt="Contact Us" style="margin-top:15px;border-radius:10px;">
</section>

<section>
<h2>📄 Legal & Disclaimer (AdSense Ready)</h2>
<p><strong>Privacy Policy:</strong> We respect user privacy and never misuse personal info.<br>
<strong>Disclaimer:</strong> Earnings depend on effort, traffic, and skills. No guaranteed income.</p>
</section>

<footer>
<p>© <span id="year"></span> SkillMint. All Rights Reserved.</p>
</footer>

<button id="scrollBtn" onclick="scrollToTop()">↑</button>

<div id="earningGuide">
<div class="guide-content">
<h2>🔥 First Week Earning Boost Checklist</h2>
<ul>
<li>Day 1: Setup & Launch – Confirm GitHub Pages link live, upload HTML, test buttons.</li>
<li>Day 2: AdSense Setup – Apply & integrate code in placeholders, update SEO.</li>
<li>Day 3: Affiliate Setup – Replace buttons with affiliate links, short URLs & CTA.</li>
<li>Day 4: WhatsApp Services – Offer small services, respond fast.</li>
<li>Day 5: Traffic Push – Share link on social media, Quora, Reddit.</li>
<li>Day 6: Blog Updates – Post small guides with affiliate + ads.</li>
<li>Day 7: Review & Optimize – Check clicks, analytics, improve buttons.</li>
</ul>
<button onclick="closeGuide()">Close Guide</button>
</div>
</div>

<script>
function toggleDarkMode(){document.body.classList.toggle("dark-mode");}
const scrollBtn=document.getElementById("scrollBtn");
window.onscroll=function(){scrollBtn.style.display=(document.body.scrollTop>200||document.documentElement.scrollTop>200)?'block':'none';};
function scrollToTop(){window.scrollTo({top:0,behavior:'smooth'});}
document.getElementById("year").textContent=new Date().getFullYear();
function openGuide(){document.getElementById("earningGuide").style.display="block";}
function closeGuide(){document.getElementById("earningGuide").style.display="none";}
</script>

</body>
</html>
