<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>محمود رأفت أبو شنب | مطور بايثون ومحلل بيانات</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
  /* ===== المتغيرات الأساسية ===== */
  :root {
    --bg-main: #0a0f1d;
    --bg-card: rgba(30, 41, 59, 0.7);
    --primary: #38bdf8;
    --primary-dark: #0ea5e9;
    --accent: #facc15;
    --text-main: #e2e8f0;
    --text-muted: #94a3b8;
    --glass-border: rgba(255, 255, 255, 0.08);
    --glass-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
    --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Cairo', sans-serif;
    background-color: var(--bg-main);
    color: var(--text-main);
    line-height: 1.8;
    overflow-x: hidden;
    scroll-behavior: smooth;
  }

  a { color: inherit; text-decoration: none; }

  /* ===== القائمة العلوية ===== */
  nav {
    position: fixed; top: 0; width: 100%; z-index: 1000;
    padding: 18px 5%;
    display: flex; justify-content: space-between; align-items: center;
    transition: var(--transition);
    background: transparent;
  }
  nav.scrolled {
    background: rgba(10, 15, 29, 0.85);
    backdrop-filter: blur(15px);
    -webkit-backdrop-filter: blur(15px);
    border-bottom: 1px solid var(--glass-border);
    padding: 12px 5%;
  }
  nav .logo {
    font-weight: 900; font-size: 1.3rem;
    background: linear-gradient(135deg, #fff, var(--primary));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  }
  nav ul { display: flex; gap: 30px; list-style: none; }
  nav ul a { font-size: 0.95rem; font-weight: 600; color: var(--text-muted); transition: var(--transition); position: relative; }
  nav ul a::after {
    content: ''; position: absolute; bottom: -5px; right: 0; width: 0; height: 2px;
    background: var(--primary); transition: var(--transition);
  }
  nav ul a:hover { color: var(--primary); }
  nav ul a:hover::after { width: 100%; }
  
  .menu-toggle { display: none; font-size: 1.8rem; color: var(--text-main); cursor: pointer; }

  @media(max-width: 768px) {
    nav ul {
      position: absolute; top: 100%; right: 0; width: 100%;
      flex-direction: column; gap: 0; text-align: center;
      background: rgba(10, 15, 29, 0.98); backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--glass-border);
      max-height: 0; overflow: hidden; transition: max-height 0.4s ease;
    }
    nav ul.active { max-height: 400px; }
    nav ul li { width: 100%; }
    nav ul a { display: block; padding: 15px; }
    nav ul a::after { display: none; }
    .menu-toggle { display: block; }
  }

  /* ===== قسم الواجهة الرئيسية ===== */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column; justify-content: center; align-items: center;
    text-align: center; padding: 120px 20px 60px;
    position: relative;
  }
  .hero::before {
    content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 100%;
    background: radial-gradient(circle at 50% 30%, rgba(56, 189, 248, 0.12), transparent 60%);
    z-index: -1;
  }
  
  /* ✨ صورة الملف الشخصي */
  .profile-img-container {
    position: relative; margin-bottom: 30px;
  }
  .profile-img {
    width: 200px; height: 200px; border-radius: 50%; object-fit: cover;
    border: 4px solid var(--primary);
    box-shadow: 0 0 40px rgba(56, 189, 248, 0.6);
    transition: var(--transition);
    animation: floatImg 5s ease-in-out infinite;
  }
  .profile-img:hover {
    transform: scale(1.08);
    box-shadow: 0 0 60px rgba(56, 189, 248, 1);
    border-color: #fff;
  }
  @keyframes floatImg {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-12px); }
  }
  @media(max-width: 768px) {
    .profile-img { width: 160px; height: 160px; }
  }

  .hero .hi { color: var(--primary); font-size: 1.2rem; margin-bottom: 10px; letter-spacing: 1px; }
  .hero h1 {
    font-size: clamp(2.2rem, 6vw, 4rem); font-weight: 900; margin-bottom: 15px;
    background: linear-gradient(135deg, #fff, var(--primary));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    animation: fadeInUp 1s ease;
  }
  .hero h2 {
    font-size: clamp(1.2rem, 3vw, 1.8rem); color: var(--text-muted);
    font-weight: 400; margin-bottom: 25px; min-height: 60px;
  }
  .typed-text { color: var(--accent); font-weight: 700; border-left: 3px solid var(--primary); padding-right: 8px; animation: blink 0.8s infinite; }
  @keyframes blink { 0%, 100% { border-color: transparent; } 50% { border-color: var(--primary); } }
  
  .hero p { max-width: 700px; color: var(--text-muted); margin-bottom: 40px; font-size: 1.05rem; }

  /* ===== الأزرار ===== */
  .btn {
    display: inline-flex; align-items: center; gap: 10px; padding: 14px 35px;
    border-radius: 50px; font-weight: 700; font-size: 1rem; transition: var(--transition);
    cursor: pointer; border: none; font-family: inherit;
  }
  .btn-primary {
    background: linear-gradient(135deg, var(--primary), var(--primary-dark));
    color: #0f172a;
    box-shadow: 0 4px 20px rgba(56, 189, 248, 0.4);
  }
  .btn-primary:hover { transform: translateY(-4px); box-shadow: 0 8px 30px rgba(56, 189, 248, 0.7); }
  .btn-whatsapp {
    background: linear-gradient(135deg, #25D366, #128C7E);
    color: #fff; box-shadow: 0 4px 20px rgba(37, 211, 102, 0.4);
  }
  .btn-whatsapp:hover { transform: translateY(-4px); box-shadow: 0 8px 30px rgba(37, 211, 102, 0.8); }
  .btn-outline {
    background: transparent; color: var(--primary);
    border: 2px solid var(--primary);
  }
  .btn-outline:hover { background: var(--primary); color: #0f172a; transform: translateY(-4px); }

  .hero-buttons { display: flex; gap: 15px; flex-wrap: wrap; justify-content: center; margin-bottom: 40px; }

  .badges { display: flex; gap: 12px; flex-wrap: wrap; justify-content: center; }
  .badge {
    padding: 8px 22px; border: 1px solid var(--glass-border);
    background: var(--bg-card); backdrop-filter: blur(10px);
    border-radius: 50px; font-size: 0.85rem; color: var(--primary);
    transition: var(--transition);
  }
  .badge:hover { border-color: var(--primary); background: rgba(56, 189, 248, 0.1); }

  /* ===== عناوين الأقسام ===== */
  section { padding: 100px 5%; max-width: 1200px; margin: 0 auto; }
  .section-title {
    text-align: center; font-size: 2.2rem; font-weight: 900; margin-bottom: 70px; position: relative;
  }
  .section-title::after {
    content: ''; display: block; width: 80px; height: 4px; margin: 18px auto 0;
    background: linear-gradient(90deg, var(--primary), var(--accent));
    border-radius: 5px;
  }

  /* ===== نبذة عني ===== */
  .about-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 25px; }
  .about-card {
    background: var(--bg-card); backdrop-filter: blur(10px);
    padding: 35px 30px; border-radius: 20px;
    border: 1px solid var(--glass-border); transition: var(--transition);
    position: relative; overflow: hidden;
  }
  .about-card::before {
    content: ''; position: absolute; top: 0; right: 0; width: 4px; height: 100%;
    background: linear-gradient(to bottom, var(--primary), var(--accent));
    border-radius: 0 4px 4px 0; opacity: 0; transition: var(--transition);
  }
  .about-card:hover { transform: translateY(-8px); box-shadow: var(--glass-shadow); border-color: rgba(56, 189, 248, 0.3); }
  .about-card:hover::before { opacity: 1; }
  .about-card h3 { color: var(--primary); margin-bottom: 15px; font-size: 1.3rem; display: flex; align-items: center; gap: 10px; }
  .about-card p { color: var(--text-muted); font-size: 0.95rem; }

  /* ===== الإحصائيات ===== */
  .stats { display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 20px; margin-top: 80px; }
  .stat {
    text-align: center; padding: 35px 20px; background: var(--bg-card);
    backdrop-filter: blur(10px); border-radius: 20px; border: 1px solid var(--glass-border);
    transition: var(--transition);
  }
  .stat:hover { transform: translateY(-5px); border-color: var(--primary); }
  .stat .num { font-size: 2.5rem; font-weight: 900; color: var(--primary); display: block; margin-bottom: 5px; }
  .stat .label { color: var(--text-muted); font-size: 0.9rem; font-weight: 600; }

  /* ===== المهارات ===== */
  .skills-container { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 40px; }
  .skill { margin-bottom: 25px; }
  .skill-head { display: flex; justify-content: space-between; margin-bottom: 10px; font-size: 1rem; font-weight: 600; }
  .skill-head span:last-child { color: var(--primary); }
  .skill-bar { height: 10px; background: rgba(255, 255, 255, 0.05); border-radius: 10px; overflow: hidden; border: 1px solid var(--glass-border); }
  .skill-fill {
    height: 100%; width: 0; background: linear-gradient(90deg, var(--primary), var(--accent));
    border-radius: 10px; transition: width 1.5s ease-in-out;
    position: relative;
  }
  .skill-fill::after {
    content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
    animation: shimmer 2s infinite;
  }
  @keyframes shimmer { 0% { transform: translateX(-100%); } 100% { transform: translateX(100%); } }

  /* ===== المشاريع ===== */
  .projects-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 30px; }
  .project {
    background: var(--bg-card); backdrop-filter: blur(10px); border-radius: 20px;
    overflow: hidden; border: 1px solid var(--glass-border); transition: var(--transition);
    display: flex; flex-direction: column;
  }
  .project:hover { transform: translateY(-10px); border-color: var(--primary); box-shadow: var(--glass-shadow); }
  .project-img-placeholder {
    height: 180px; background: linear-gradient(135deg, rgba(56, 189, 248, 0.1), rgba(250, 204, 21, 0.05));
    display: flex; align-items: center; justify-content: center; font-size: 3.5rem;
    border-bottom: 1px solid var(--glass-border);
  }
  .project-body { padding: 25px; flex-grow: 1; display: flex; flex-direction: column; }
  .project h3 { color: var(--primary); margin-bottom: 12px; font-size: 1.2rem; }
  .project p { color: var(--text-muted); font-size: 0.9rem; margin-bottom: 20px; flex-grow: 1; }
  .tags { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 20px; }
  .tag { font-size: 0.75rem; padding: 5px 14px; background: rgba(56, 189, 248, 0.1); color: var(--primary); border-radius: 50px; border: 1px solid rgba(56, 189, 248, 0.2); }
  .project-link { font-size: 0.9rem; font-weight: 700; color: var(--accent); display: inline-flex; align-items: center; gap: 5px; transition: var(--transition); }
  .project-link:hover { gap: 10px; }

  /* ===== تواصل معي ===== */
  .contact-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 20px; max-width: 900px; margin: 0 auto 40px; }
  .contact-card {
    display: flex; align-items: center; gap: 20px; padding: 25px;
    background: var(--bg-card); backdrop-filter: blur(10px); border-radius: 18px;
    border: 1px solid var(--glass-border); transition: var(--transition);
  }
  .contact-card:hover { transform: translateY(-5px); border-color: var(--primary); box-shadow: var(--glass-shadow); }
  .contact-card .icon {
    width: 55px; height: 55px; border-radius: 50%; display: flex; align-items: center; justify-content: center;
    font-size: 1.6rem; flex-shrink: 0; transition: var(--transition);
  }
  .contact-card:hover .icon { transform: scale(1.1) rotate(5deg); }
  .contact-card.wa .icon { background: rgba(37, 211, 102, 0.15); color: #25D366; border: 1px solid rgba(37, 211, 102, 0.3); }
  .contact-card.gm .icon { background: rgba(234, 67, 53, 0.15); color: #ea4335; border: 1px solid rgba(234, 67, 53, 0.3); }
  .contact-card .info { display: flex; flex-direction: column; text-align: right; }
  .contact-card .info span:first-child { font-weight: 700; margin-bottom: 3px; font-size: 1.05rem; }
  .contact-card .info span:last-child { color: var(--text-muted); font-size: 0.85rem; direction: ltr; text-align: left; font-family: 'Poppins', sans-serif; }

  .contact-form { max-width: 650px; margin: 0 auto; display: flex; flex-direction: column; gap: 20px; }
  .contact-form input, .contact-form textarea {
    padding: 18px 20px; border-radius: 15px; background: var(--bg-card);
    border: 1px solid var(--glass-border); color: var(--text-main);
    font-family: inherit; font-size: 1rem; outline: none; transition: var(--transition);
    backdrop-filter: blur(10px);
  }
  .contact-form input:focus, .contact-form textarea:focus {
    border-color: var(--primary); box-shadow: 0 0 0 4px rgba(56, 189, 248, 0.1); background: rgba(30, 41, 59, 0.9);
  }
  .contact-form textarea { resize: vertical; min-height: 150px; }
  .contact-form button { padding: 18px; background: linear-gradient(135deg, var(--primary), var(--primary-dark)); color: #0f172a; font-weight: 800; font-size: 1.05rem; border: none; border-radius: 15px; cursor: pointer; font-family: inherit; transition: var(--transition); }
  .contact-form button:hover { transform: translateY(-3px); box-shadow: 0 8px 25px rgba(56, 189, 248, 0.4); }

  .success {
    display: none; text-align: center; margin-top: 30px; padding: 30px;
    background: rgba(56, 189, 248, 0.1); border: 1px solid var(--primary); border-radius: 20px;
    animation: fadeInUp 0.5s ease;
  }
  .success h3 { color: var(--primary); margin-bottom: 10px; font-size: 1.3rem; }
  .success p { color: var(--text-muted); }

  /* ===== الفوتر ===== */
  footer {
    text-align: center; padding: 40px 20px; border-top: 1px solid var(--glass-border);
    color: var(--text-muted); font-size: 0.9rem; background: rgba(10, 15, 29, 0.8);
  }
  footer strong { color: var(--primary); }

  /* ===== زر الواتساب العائم ===== */
  .wa-float {
    position: fixed; bottom: 30px; left: 30px; z-index: 999;
    width: 65px; height: 65px; border-radius: 50%;
    background: linear-gradient(135deg, #25D366, #128C7E);
    display: flex; align-items: center; justify-content: center;
    font-size: 2rem; color: #fff; box-shadow: 0 8px 30px rgba(37, 211, 102, 0.6);
    transition: var(--transition); animation: pulse 2s infinite;
  }
  .wa-float:hover { transform: scale(1.1) rotate(10deg); box-shadow: 0 12px 40px rgba(37, 211, 102, 0.9); }
  @keyframes pulse { 0%, 100% { box-shadow: 0 8px 30px rgba(37, 211, 102, 0.6); } 50% { box-shadow: 0 8px 40px rgba(37, 211, 102, 1); } }

  @keyframes fadeInUp { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
</style>
</head>
<body>

<!-- القائمة العلوية -->
<nav id="navbar">
  <div class="logo">محمود رأفت</div>
  <ul id="nav-menu">
    <li><a href="#about">نبذة عني</a></li>
    <li><a href="#skills">المهارات</a></li>
    <li><a href="#projects">المشاريع</a></li>
    <li><a href="#contact">تواصل معي</a></li>
  </ul>
  <div class="menu-toggle" id="menu-toggle">☰</div>
</nav>

<!-- الواجهة الرئيسية -->
<section class="hero">
  <div class="profile-img-container">
    <img src="profile.jpg" alt="محمود رأفت أبو شنب" class="profile-img">
  </div>
  
  <div class="hi">مرحباً بك في موقعي الشخصي 👋</div>
  <h1>أهلاً، أنا محمود رأفت أبو شنب</h1>
  <h2>ومطوّر متخصص في <span class="typed-text" id="typed-text"></span></h2>
  <p>
    مطوّر شغوف بلغة بايثون، أعمل على بناء حلول برمجية ذكية وأدوات فعّالة،
    وأركّز على كتابة كود نظيف وقابل للتطوير. أسعى دائماً لتطوير مهاراتي
    وتحويل الأفكار إلى مشاريع عملية بسيطة وقوية.
  </p>
  
  <div class="hero-buttons">
    <a href="https://wa.me/972592279239" target="_blank" class="btn btn-whatsapp">💬 تواصل عبر واتساب</a>
    <a href="#projects" class="btn btn-primary">🚀 مشاريعي</a>
    <a href="#" class="btn btn-outline" download>📄 تحميل السيرة الذاتية</a>
  </div>
  
  <div class="badges">
    <span class="badge">🐍 Python Developer</span>
    <span class="badge">📊 Data Analyst</span>
    <span class="badge">🌐 Web Developer</span>
  </div>
</section>

<!-- نبذة عني -->
<section id="about">
  <h2 class="section-title">نبذة عنّي</h2>
  <div class="about-grid">
    <div class="about-card">
      <h3>🐍 إتقان لغة بايثون</h3>
      <p>خبرة في كتابة سكربتات وتطبيقات بايثون، من الأتمتة البسيطة إلى بناء حلول برمجية متكاملة تعتمد على أحدث مكتبات وأطر العمل.</p>
    </div>
    <div class="about-card">
      <h3>📊 تحليل البيانات</h3>
      <p>قدرة على استخراج البيانات وتنظيفها وتحليلها باستخدام مكتبات بايثون مثل Pandas و NumPy واستخراج رؤى قابلة للتنفيذ.</p>
    </div>
    <div class="about-card">
      <h3>💡 حل المشكلات</h3>
      <p>أستمتع بتفكيك المشاكل البرمجية المعقدة وبناء خوارزميات فعّالة وكود سلس يسهل صيانته وتطويره مستقبلاً.</p>
    </div>
  </div>

  <div class="stats">
    <div class="stat"><span class="num" data-count="10">+0</span><span class="label">مشروع مكتمل</span></div>
    <div class="stat"><span class="num" data-count="100">0%</span><span class="label">رضا عن الأداء</span></div>
    <div class="stat"><span class="num" data-count="2">+0</span><span class="label">سنوات خبرة</span></div>
    <div class="stat"><span class="num">24/7</span><span class="label">شغف وتطوير</span></div>
  </div>
</section>

<!-- المهارات -->
<section id="skills">
  <h2 class="section-title">المهارات التقنية</h2>
  <div class="skills-container">
    <div class="skill">
      <div class="skill-head"><span>🐍 لغة بايثون</span><span>95%</span></div>
      <div class="skill-bar"><div class="skill-fill" data-width="95"></div></div>
    </div>
    <div class="skill">
      <div class="skill-head"><span>📊 تحليل البيانات</span><span>90%</span></div>
      <div class="skill-bar"><div class="skill-fill" data-width="90"></div></div>
    </div>
    <div class="skill">
      <div class="skill-head"><span>🌐 تطوير الويب</span><span>85%</span></div>
      <div class="skill-bar"><div class="skill-fill" data-width="85"></div></div>
    </div>
    <div class="skill">
      <div class="skill-head"><span>🗄️ قواعد البيانات (SQL)</span><span>80%</span></div>
      <div class="skill-bar"><div class="skill-fill" data-width="80"></div></div>
    </div>
    <div class="skill">
      <div class="skill-head"><span>⚙️ أتمتة المهام Scripting</span><span>88%</span></div>
      <div class="skill-bar"><div class="skill-fill" data-width="88"></div></div>
    </div>
    <div class="skill">
      <div class="skill-head"><span>🔧 Git & GitHub</span><span>85%</span></div>
      <div class="skill-bar"><div class="skill-fill" data-width="85"></div></div>
    </div>
  </div>
</section>

<!-- المشاريع -->
<section id="projects">
  <h2 class="section-title">أحدث المشاريع</h2>
  <div class="projects-grid">
    <div class="project">
      <div class="project-img-placeholder">🤖</div>
      <div class="project-body">
        <h3>بوت أتمتة المهام</h3>
        <p>سكربت بايثون يقوم بأتمتة المهام المتكررة وتوفير الوقت والجهد بشكل ذكي.</p>
        <div class="tags"><span class="tag">Python</span><span class="tag">Automation</span></div>
        <a href="#" class="project-link">عرض المشروع ←</a>
      </div>
    </div>
    <div class="project">
      <div class="project-img-placeholder">📊</div>
      <div class="project-body">
        <h3>محلل البيانات الذكي</h3>
        <p>أداة بلغة بايثون لتحليل البيانات واستخراج التقارير والرسوم البيانية بشكل تلقائي.</p>
        <div class="tags"><span class="tag">Python</span><span class="tag">Pandas</span><span class="tag">Matplotlib</span></div>
        <a href="#" class="project-link">عرض المشروع ←</a>
      </div>
    </div>
    <div class="project">
      <div class="project-img-placeholder">🌐</div>
      <div class="project-body">
        <h3>تطبيق ويب متكامل</h3>
        <p>تطبيق ويب باستخدام Python مع واجهة تفاعلية وإدارة قاعدة بيانات كاملة.</p>
        <div class="tags"><span class="tag">Python</span><span class="tag">Flask</span><span class="tag">SQLite</span></div>
        <a href="#" class="project-link">عرض المشروع ←</a>
      </div>
    </div>
  </div>
</section>

<!-- تواصل معي -->
<section id="contact">
  <h2 class="section-title">تواصل معي</h2>
  <p style="text-align:center;color:var(--text-muted);margin-bottom:50px;font-size:1.05rem;">
    هل لديك فكرة مشروع؟ أو ترغب في العمل معاً؟ تواصل معي مباشرة 👇
  </p>

  <div class="contact-grid">
    <a href="https://wa.me/972592279239" target="_blank" class="contact-card wa">
      <div class="icon">💬</div>
      <div class="info"><span>واتساب</span><span>+972 59 227 9239</span></div>
    </a>
    <a href="mailto:mahmoud63862@gmail.com" class="contact-card gm">
      <div class="icon">✉️</div>
      <div class="info"><span>البريد الإلكتروني</span><span>mahmoud63862@gmail.com</span></div>
    </a>
  </div>

  <form class="contact-form" id="contactForm">
    <input type="text" placeholder="الاسم الكامل" required>
    <input type="email" placeholder="البريد الإلكتروني" required>
    <textarea placeholder="رسالتك..." required></textarea>
    <button type="submit">إرسال الرسالة</button>
  </form>
  <div class="success" id="successMsg">
    <h3>تم الإرسال بنجاح! ✅</h3>
    <p>شكراً لتواصلك يا محمود، سأرد عليك في أقرب وقت ممكن.</p>
  </div>
</section>

<footer>
  © 2025 <strong>محمود رأفت أبو شنب</strong> — جميع الحقوق محفوظة.
</footer>

<!-- زر الواتساب العائم -->
<a href="https://wa.me/972592279239" target="_blank" class="wa-float" title="تواصل عبر واتساب">💬</a>

<script>
  // 1. تأثير الكتابة الحية (Typing Effect)
  const typedTextElement = document.getElementById('typed-text');
  const textArray = ['مطور بايثون', 'محلل بيانات', 'مطور ويب'];
  let textIndex = 0;
  let charIndex = 0;
  let isDeleting = false;

  function type() {
    const currentText = textArray[textIndex];
    if (isDeleting) {
      typedTextElement.textContent = currentText.substring(0, charIndex - 1);
      charIndex--;
    } else {
      typedTextElement.textContent = currentText.substring(0, charIndex + 1);
      charIndex++;
    }

    let typeSpeed = isDeleting ? 60 : 120;

    if (!isDeleting && charIndex === currentText.length) {
      typeSpeed = 2000; // Pause at end
      isDeleting = true;
    } else if (isDeleting && charIndex === 0) {
      isDeleting = false;
      textIndex = (textIndex + 1) % textArray.length;
      typeSpeed = 500;
    }

    setTimeout(type, typeSpeed);
  }
  type();

  // 2. تأثير التمرير للقائمة العلوية (Navbar Scroll Effect)
  const navbar = document.getElementById('navbar');
  window.addEventListener('scroll', () => {
    if (window.scrollY > 50) {
      navbar.classList.add('scrolled');
    } else {
      navbar.classList.remove('scrolled');
    }
  });

  // 3. قائمة الجوال (Mobile Menu Toggle)
  const menuToggle = document.getElementById('menu-toggle');
  const navMenu = document.getElementById('nav-menu');
  menuToggle.addEventListener('click', () => {
    navMenu.classList.toggle('active');
  });

  // 4. أنيميشن المهارات (Skill Bars Animation)
  const skillFills = document.querySelectorAll('.skill-fill');
  const skillsObserver = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.style.width = e.target.dataset.width + '%';
      }
    });
  }, { threshold: 0.4 });
  skillFills.forEach(f => skillsObserver.observe(f));

  // 5. أنيميشن العدادات (Counter Animation)
  const counters = document.querySelectorAll('.stat .num[data-count]');
  const counterObserver = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        const el = e.target;
        const target = +el.dataset.count;
        let cur = 0;
        const step = Math.max(1, target / 50);
        const timer = setInterval(() => {
          cur += step;
          if (cur >= target) {
            cur = target;
            clearInterval(timer);
          }
          el.textContent = (target === 100 ? '' : '+') + Math.floor(cur) + (target === 100 ? '%' : '');
        }, 25);
        counterObserver.unobserve(el);
      }
    });
  }, { threshold: 0.5 });
  counters.forEach(c => counterObserver.observe(c));

  // 6. نموذج التواصل (Contact Form)
  document.getElementById('contactForm').addEventListener('submit', function(e) {
    e.preventDefault();
    this.style.display = 'none';
    document.getElementById('successMsg').style.display = 'block';
  });

  // 7. التمرير الناعم للروابط الداخلية (Smooth Scroll)
  document.querySelectorAll('a[href^="#"]').forEach(a => {
    a.addEventListener('click', e => {
      e.preventDefault();
      const t = document.querySelector(a.getAttribute('href'));
      if (t) {
        t.scrollIntoView({ behavior: 'smooth' });
        navMenu.classList.remove('active'); // إغلاق قائمة الجوال بعد الضغط
      }
    });
  });
</script>
</body>
</html>
