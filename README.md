<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>Deep Sorathiya — Full-Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #050810;
    --surface: #0c1120;
    --border: #1a2540;
    --accent: #3584E4;
    --accent2: #00d4ff;
    --accent3: #7c3aed;
    --text: #e8edf5;
    --muted: #6b7fa3;
    --card: #0f1829;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Syne', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── BACKGROUND GRID ── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image:
      linear-gradient(rgba(53,132,228,.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(53,132,228,.04) 1px, transparent 1px);
    background-size: 48px 48px;
    pointer-events: none;
    z-index: 0;
  }

  /* ── GLOW ORBS ── */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    pointer-events: none;
    z-index: 0;
    opacity: .35;
  }
  .orb1 { width: 500px; height: 500px; background: var(--accent3); top: -150px; right: -150px; animation: drift 14s ease-in-out infinite alternate; }
  .orb2 { width: 400px; height: 400px; background: var(--accent); bottom: 10%; left: -100px; animation: drift 18s ease-in-out infinite alternate-reverse; }

  @keyframes drift { from { transform: translate(0,0); } to { transform: translate(30px,40px); } }

  /* ── WRAPPER ── */
  .wrapper {
    position: relative; z-index: 1;
    max-width: 860px;
    margin: 0 auto;
    padding: 0 24px 80px;
  }

  /* ── HERO ── */
  .hero {
    display: flex; flex-direction: column; align-items: center;
    padding: 100px 0 60px;
    text-align: center;
  }

  .hero-badge {
    display: inline-flex; align-items: center; gap: 8px;
    font-family: 'Space Mono', monospace;
    font-size: .7rem;
    color: var(--accent2);
    border: 1px solid rgba(0,212,255,.2);
    background: rgba(0,212,255,.06);
    padding: 6px 14px; border-radius: 100px;
    margin-bottom: 28px;
    animation: fadeUp .8s ease both;
  }
  .hero-badge span { width: 6px; height: 6px; background: var(--accent2); border-radius: 50%; animation: pulse 2s ease infinite; }

  @keyframes pulse { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:.4;transform:scale(1.3)} }

  .hero h1 {
    font-size: clamp(2.6rem, 7vw, 4.6rem);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -2px;
    animation: fadeUp .9s .1s ease both;
  }

  .hero h1 .name-accent {
    background: linear-gradient(135deg, var(--accent) 0%, var(--accent2) 60%, var(--accent3) 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
  }

  .hero-sub {
    font-family: 'Space Mono', monospace;
    font-size: .85rem;
    color: var(--muted);
    margin-top: 16px;
    animation: fadeUp 1s .2s ease both;
  }

  .hero-sub b { color: var(--accent); font-weight: 400; }

  .hero-actions {
    display: flex; gap: 12px; flex-wrap: wrap; justify-content: center;
    margin-top: 40px;
    animation: fadeUp 1s .35s ease both;
  }

  .btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 12px 26px;
    border-radius: 8px;
    font-family: 'Space Mono', monospace;
    font-size: .78rem;
    font-weight: 700;
    cursor: pointer; text-decoration: none;
    transition: transform .18s, box-shadow .18s;
    letter-spacing: .04em;
  }
  .btn:hover { transform: translateY(-2px); }

  .btn-primary {
    background: var(--accent);
    color: #fff;
    box-shadow: 0 0 24px rgba(53,132,228,.4);
  }
  .btn-primary:hover { box-shadow: 0 0 40px rgba(53,132,228,.65); }

  .btn-ghost {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border);
  }
  .btn-ghost:hover { border-color: var(--accent); color: var(--accent); }

  /* ── SECTION ── */
  section { margin-top: 80px; }

  .section-label {
    display: flex; align-items: center; gap: 14px;
    font-family: 'Space Mono', monospace;
    font-size: .7rem;
    color: var(--accent2);
    text-transform: uppercase;
    letter-spacing: .15em;
    margin-bottom: 28px;
  }
  .section-label::after { content: ''; flex: 1; height: 1px; background: var(--border); }

  /* ── CARDS ── */
  .card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 28px;
    transition: border-color .2s, transform .2s, box-shadow .2s;
  }
  .card:hover {
    border-color: var(--accent);
    transform: translateY(-3px);
    box-shadow: 0 12px 40px rgba(53,132,228,.12);
  }

  /* ── TECH GRID ── */
  .tech-outer { display: flex; flex-direction: column; gap: 28px; }

  .tech-group h4 {
    font-family: 'Space Mono', monospace;
    font-size: .68rem;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: .12em;
    margin-bottom: 14px;
  }

  .tech-chips { display: flex; flex-wrap: wrap; gap: 8px; }

  .chip {
    display: inline-flex; align-items: center; gap: 7px;
    padding: 7px 14px;
    border-radius: 8px;
    border: 1px solid var(--border);
    background: var(--surface);
    font-size: .78rem;
    font-weight: 600;
    color: var(--text);
    transition: border-color .18s, background .18s, transform .18s;
    cursor: default;
  }
  .chip:hover { border-color: var(--accent); background: rgba(53,132,228,.08); transform: scale(1.04); }
  .chip img { width: 16px; height: 16px; object-fit: contain; }

  /* ── STATS ── */
  .stats-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));
    gap: 16px;
  }
  .stat-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px 20px;
    text-align: center;
    transition: border-color .2s, box-shadow .2s;
  }
  .stat-card:hover { border-color: var(--accent); box-shadow: 0 8px 32px rgba(53,132,228,.12); }

  .stat-card .num {
    font-size: 2.2rem; font-weight: 800;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
    display: block;
  }
  .stat-card .lbl {
    font-family: 'Space Mono', monospace;
    font-size: .65rem; color: var(--muted);
    text-transform: uppercase; letter-spacing: .1em;
    margin-top: 4px; display: block;
  }

  /* ── LEARNING CARDS ── */
  .learning-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 16px; }
  .learn-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px;
    display: flex; flex-direction: column; gap: 10px;
    transition: border-color .2s, transform .2s;
  }
  .learn-card:hover { border-color: var(--accent2); transform: translateY(-3px); }
  .learn-icon { font-size: 1.5rem; }
  .learn-card h3 { font-size: 1rem; font-weight: 700; }
  .learn-card p { font-family: 'Space Mono', monospace; font-size: .68rem; color: var(--muted); line-height: 1.6; }

  /* ── PROGRESS BAR ── */
  .progress-wrap { margin-top: 8px; }
  .progress-bar {
    height: 4px; background: var(--border); border-radius: 4px; overflow: hidden;
  }
  .progress-fill {
    height: 100%; border-radius: 4px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    animation: grow 1.4s cubic-bezier(.4,0,.2,1) both;
    transform-origin: left;
  }
  @keyframes grow { from { transform: scaleX(0); } to { transform: scaleX(1); } }

  /* ── QUOTE ── */
  .quote-box {
    text-align: center;
    padding: 48px 32px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 20px;
    position: relative; overflow: hidden;
  }
  .quote-box::before {
    content: '"';
    position: absolute; top: -20px; left: 24px;
    font-size: 10rem; font-weight: 800; line-height: 1;
    color: rgba(53,132,228,.07);
    font-family: Georgia, serif;
    pointer-events: none;
  }
  .quote-box p {
    font-size: clamp(1rem, 2.5vw, 1.3rem);
    font-style: italic;
    color: var(--muted);
    max-width: 560px; margin: 0 auto;
    line-height: 1.6;
  }
  .quote-box p em { color: var(--accent2); font-style: normal; font-weight: 700; }

  /* ── GITHUB CARDS (iframes replaced with img wrappers) ── */
  .gh-grid { display: flex; flex-wrap: wrap; gap: 16px; justify-content: center; }
  .gh-img { border-radius: 12px; overflow: hidden; border: 1px solid var(--border); transition: border-color .2s; }
  .gh-img:hover { border-color: var(--accent); }
  .gh-img img { display: block; max-width: 100%; height: auto; }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* ── SCROLL REVEAL (JS-driven) ── */
  .reveal { opacity: 0; transform: translateY(28px); transition: opacity .55s ease, transform .55s ease; }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 3px; }
  ::-webkit-scrollbar-thumb:hover { background: var(--accent); }

  /* ── RESPONSIVE ── */
  @media (max-width: 560px) {
    .gh-img img { width: 100%; }
  }
</style>
</head>
<body>

<div class="orb orb1"></div>
<div class="orb orb2"></div>

<div class="wrapper">

  <!-- ── HERO ── -->
  <section class="hero">
    <div class="hero-badge"><span></span> Available for Projects &amp; Collaboration</div>
    <h1>Hi, I'm<br><span class="name-accent">Deep Sorathiya</span></h1>
    <p class="hero-sub">Full-Stack Developer &nbsp;·&nbsp; <b>Nirma University</b> &nbsp;·&nbsp; Create · Conquer · Code</p>
    <p style="color:var(--muted);font-size:.85rem;margin-top:10px;font-family:'Space Mono',monospace;">Building innovative solutions with code and creativity</p>
    <div class="hero-actions">
      <a href="mailto:deepsorathiya803@gmail.com" class="btn btn-primary">
        <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
        Say Hello
      </a>
      <a href="https://www.linkedin.com/in/deepsorathiya7990/" target="_blank" class="btn btn-ghost">
        <svg width="15" height="15" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
        LinkedIn
      </a>
    </div>
  </section>

  <!-- ── STATS ── -->
  <section class="reveal">
    <div class="section-label">GitHub at a Glance</div>
    <div class="stats-grid">
      <div class="stat-card"><span class="num" id="s-commits">—</span><span class="lbl">Total Commits</span></div>
      <div class="stat-card"><span class="num" id="s-repos">—</span><span class="lbl">Public Repos</span></div>
      <div class="stat-card"><span class="num" id="s-streak">🔥</span><span class="lbl">Current Streak</span></div>
    </div>
    <!-- GitHub image cards -->
    <div class="gh-grid" style="margin-top:20px;">
      <div class="gh-img">
        <img src="https://github-readme-stats.vercel.app/api?username=Lerner-11052025-20&show_icons=true&theme=tokyonight&hide_border=true&count_private=true&include_all_commits=true&rank_icon=github" alt="GitHub Stats"/>
      </div>
      <div class="gh-img">
        <img src="https://streak-stats.demolab.com?user=Lerner-11052025-20&theme=tokyonight&hide_border=true" alt="GitHub Streak"/>
      </div>
    </div>
    <div class="gh-grid" style="margin-top:16px;">
      <div class="gh-img">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Lerner-11052025-20&layout=compact&theme=tokyonight&hide_border=true&langs_count=8" alt="Top Languages"/>
      </div>
      <div class="gh-img">
        <img src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=Lerner-11052025-20&theme=tokyonight" alt="Profile Details"/>
      </div>
    </div>
  </section>

  <!-- ── TECH STACK ── -->
  <section class="reveal">
    <div class="section-label">Tech Stack</div>
    <div class="card tech-outer">

      <div class="tech-group">
        <h4>Frontend</h4>
        <div class="tech-chips">
          <span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" alt=""/>HTML5</span>
          <span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" alt=""/>CSS3</span>
          <span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" alt=""/>JavaScript</span>
          <span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" alt=""/>React</span>
          <span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg" alt=""/>Figma</span>
        </div>
      </div>

      <div class="tech-group">
        <h4>Backend &amp; Database</h4>
        <div class="tech-chips">
          <span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg" alt=""/>MySQL</span>
        </div>
      </div>

      <div class="tech-group">
        <h4>Languages</h4>
        <div class="tech-chips">
          <span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt=""/>Python</span>
          <span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" alt=""/>Java</span>
          <span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/c/c-original.svg" alt=""/>C</span>
        </div>
      </div>

      <div class="tech-group">
        <h4>Tools &amp; Environment</h4>
        <div class="tech-chips">
          <span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" alt=""/>Git</span>
          <span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" alt=""/>Linux</span>
          <span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" alt=""/>VS Code</span>
        </div>
      </div>

    </div>
  </section>

  <!-- ── CURRENTLY LEARNING ── -->
  <section class="reveal">
    <div class="section-label">Currently Learning</div>
    <div class="learning-grid">
      <div class="learn-card">
        <div class="learn-icon">⚛️</div>
        <h3>React</h3>
        <p>Building component-driven UIs with hooks, context &amp; modern patterns.</p>
        <div class="progress-wrap">
          <div style="display:flex;justify-content:space-between;font-family:'Space Mono',monospace;font-size:.65rem;color:var(--muted);margin-bottom:6px;">
            <span>Progress</span><span>70%</span>
          </div>
          <div class="progress-bar"><div class="progress-fill" style="width:70%"></div></div>
        </div>
      </div>
      <div class="learn-card">
        <div class="learn-icon">🔌</div>
        <h3>API Development</h3>
        <p>Designing REST APIs, auth flows, and integrating third-party services.</p>
        <div class="progress-wrap">
          <div style="display:flex;justify-content:space-between;font-family:'Space Mono',monospace;font-size:.65rem;color:var(--muted);margin-bottom:6px;">
            <span>Progress</span><span>55%</span>
          </div>
          <div class="progress-bar"><div class="progress-fill" style="width:55%"></div></div>
        </div>
      </div>
    </div>
  </section>

  <!-- ── QUOTE ── -->
  <section class="reveal" style="margin-top:60px;">
    <div class="quote-box">
      <p><em>Code is like poetry;</em> it's all about finding the right rhythm.</p>
    </div>
  </section>

</div>

<script>
  // ── SCROLL REVEAL ──
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); observer.unobserve(e.target); } });
  }, { threshold: 0.1 });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  // ── COUNTER ANIMATION ──
  function animateCount(el, target, suffix='') {
    let start = 0, dur = 1600, step = dur / target;
    const timer = setInterval(() => {
      start += Math.ceil(target / 60);
      if (start >= target) { start = target; clearInterval(timer); }
      el.textContent = start.toLocaleString() + suffix;
    }, step < 16 ? 16 : step);
  }

  // Animate when stats section visible
  const statsObs = new IntersectionObserver(entries => {
    if (entries[0].isIntersecting) {
      animateCount(document.getElementById('s-commits'), 120, '+');
      animateCount(document.getElementById('s-repos'), 18);
      document.getElementById('s-streak').textContent = '🔥 Active';
      statsObs.disconnect();
    }
  }, { threshold: 0.3 });
  const statsSection = document.querySelector('.stats-grid');
  if (statsSection) statsObs.observe(statsSection);
</script>
</body>
</html>
