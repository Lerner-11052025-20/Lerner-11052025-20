<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Deep Sorathiya — Full Stack Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet" />
<style>
  :root {
    --bg: #080b10;
    --surface: #0e1420;
    --surface2: #131926;
    --border: #1e2a3a;
    --accent: #00d4ff;
    --accent2: #3b82f6;
    --accent3: #a78bfa;
    --text: #e2e8f0;
    --muted: #64748b;
    --success: #22d3a5;
    --warn: #f59e0b;
    --glow: 0 0 40px rgba(0,212,255,0.12);
    --glow2: 0 0 60px rgba(59,130,246,0.1);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
    font-size: 15px;
    line-height: 1.7;
  }

  /* ── NOISE OVERLAY ── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 0; opacity: 0.4;
  }

  /* ── AMBIENT ORBS ── */
  .orb {
    position: fixed; border-radius: 50%;
    filter: blur(120px); pointer-events: none; z-index: 0;
    animation: float 10s ease-in-out infinite alternate;
  }
  .orb1 { width: 500px; height: 500px; background: rgba(0,212,255,0.05); top: -150px; right: -100px; animation-delay: 0s; }
  .orb2 { width: 400px; height: 400px; background: rgba(59,130,246,0.06); bottom: 0; left: -100px; animation-delay: -4s; }
  .orb3 { width: 300px; height: 300px; background: rgba(167,139,250,0.04); top: 40%; left: 40%; animation-delay: -7s; }

  @keyframes float {
    from { transform: translateY(0) scale(1); }
    to   { transform: translateY(-30px) scale(1.05); }
  }

  /* ── LAYOUT ── */
  .container {
    max-width: 860px;
    margin: 0 auto;
    padding: 0 24px 80px;
    position: relative; z-index: 1;
  }

  /* ── NAV BAR ── */
  nav {
    position: sticky; top: 0; z-index: 100;
    background: rgba(8,11,16,0.85);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border);
    padding: 14px 24px;
  }
  .nav-inner {
    max-width: 860px; margin: 0 auto;
    display: flex; align-items: center; justify-content: space-between;
  }
  .nav-logo {
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: 16px; color: var(--accent); letter-spacing: 0.5px;
  }
  .nav-links { display: flex; gap: 6px; }
  .nav-links a {
    font-family: 'DM Mono', monospace; font-size: 11px;
    color: var(--muted); text-decoration: none;
    padding: 5px 12px; border-radius: 6px;
    border: 1px solid transparent;
    transition: all 0.2s;
  }
  .nav-links a:hover { color: var(--accent); border-color: var(--border); background: var(--surface); }

  /* ── HERO ── */
  .hero {
    padding: 72px 0 56px;
    text-align: center;
  }
  .hero-eyebrow {
    font-family: 'DM Mono', monospace; font-size: 11px;
    color: var(--accent); letter-spacing: 3px; text-transform: uppercase;
    margin-bottom: 20px;
    display: inline-flex; align-items: center; gap: 8px;
  }
  .hero-eyebrow::before, .hero-eyebrow::after {
    content: ''; flex: 1; height: 1px;
    background: linear-gradient(to right, transparent, var(--accent));
    width: 40px;
  }
  .hero-eyebrow::after { background: linear-gradient(to left, transparent, var(--accent)); }
  .hero h1 {
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: clamp(42px, 8vw, 72px);
    line-height: 1.05; letter-spacing: -2px;
    margin-bottom: 16px;
  }
  .hero h1 .line1 { display: block; color: var(--text); }
  .hero h1 .line2 {
    display: block;
    background: linear-gradient(135deg, var(--accent), var(--accent2), var(--accent3));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .hero-sub {
    font-size: 16px; color: var(--muted); margin-bottom: 32px;
    max-width: 480px; margin-left: auto; margin-right: auto;
  }
  .hero-badges { display: flex; flex-wrap: wrap; gap: 10px; justify-content: center; margin-bottom: 36px; }
  .badge {
    display: inline-flex; align-items: center; gap: 6px;
    padding: 7px 14px; border-radius: 100px;
    border: 1px solid var(--border);
    background: var(--surface);
    font-family: 'DM Mono', monospace; font-size: 11px;
    color: var(--muted); transition: all 0.2s;
  }
  .badge:hover { border-color: var(--accent); color: var(--accent); }
  .badge .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--success); animation: pulse 2s infinite; }
  @keyframes pulse { 0%,100% { opacity:1; } 50% { opacity:0.4; } }

  .hero-ctas { display: flex; gap: 12px; justify-content: center; }
  .btn {
    padding: 11px 24px; border-radius: 8px; font-size: 13px; font-weight: 600;
    text-decoration: none; display: inline-flex; align-items: center; gap: 7px;
    transition: all 0.2s; cursor: pointer; border: none; font-family: 'DM Sans', sans-serif;
  }
  .btn-primary {
    background: var(--accent); color: #080b10;
  }
  .btn-primary:hover { background: #fff; transform: translateY(-1px); box-shadow: 0 8px 24px rgba(0,212,255,0.25); }
  .btn-ghost {
    background: var(--surface); color: var(--text); border: 1px solid var(--border);
  }
  .btn-ghost:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-1px); }

  /* ── SECTION ── */
  section { margin-bottom: 56px; }
  .section-header {
    display: flex; align-items: center; gap: 14px;
    margin-bottom: 28px;
  }
  .section-icon {
    width: 36px; height: 36px; border-radius: 9px;
    background: var(--surface2); border: 1px solid var(--border);
    display: flex; align-items: center; justify-content: center;
    font-size: 16px;
  }
  .section-title {
    font-family: 'Syne', sans-serif; font-weight: 700;
    font-size: 13px; letter-spacing: 2px; text-transform: uppercase;
    color: var(--muted);
  }
  .section-line { flex: 1; height: 1px; background: var(--border); }

  /* ── ABOUT ── */
  .about-grid {
    display: grid; grid-template-columns: 1fr 220px;
    gap: 24px; align-items: start;
  }
  .about-text { font-size: 15px; color: #94a3b8; line-height: 1.8; }
  .about-text strong { color: var(--text); }
  .about-card {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 14px; padding: 20px; display: flex; flex-direction: column; gap: 14px;
  }
  .stat-row { display: flex; align-items: baseline; gap: 8px; }
  .stat-num {
    font-family: 'Syne', sans-serif; font-weight: 800; font-size: 28px;
    color: var(--accent);
  }
  .stat-label { font-size: 11px; color: var(--muted); font-family: 'DM Mono', monospace; }
  .stat-divider { height: 1px; background: var(--border); }

  /* ── SKILLS ── */
  .skills-grid { display: flex; flex-direction: column; gap: 20px; }
  .skill-group {}
  .skill-group-label {
    font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 2px;
    text-transform: uppercase; color: var(--muted); margin-bottom: 12px;
  }
  .skill-chips { display: flex; flex-wrap: wrap; gap: 8px; }
  .chip {
    padding: 6px 13px; border-radius: 7px;
    border: 1px solid var(--border); background: var(--surface);
    font-family: 'DM Mono', monospace; font-size: 12px;
    color: var(--text); transition: all 0.18s;
  }
  .chip:hover { border-color: var(--accent); color: var(--accent); background: rgba(0,212,255,0.04); transform: translateY(-1px); }
  .chip.accent { border-color: rgba(0,212,255,0.3); color: var(--accent); background: rgba(0,212,255,0.06); }
  .chip.blue { border-color: rgba(59,130,246,0.3); color: #93c5fd; background: rgba(59,130,246,0.06); }
  .chip.purple { border-color: rgba(167,139,250,0.3); color: #c4b5fd; background: rgba(167,139,250,0.06); }

  /* ── PROJECTS ── */
  .projects { display: flex; flex-direction: column; gap: 18px; }
  .project-card {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 16px; padding: 26px 28px;
    transition: all 0.25s; position: relative; overflow: hidden;
  }
  .project-card::before {
    content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    opacity: 0; transition: opacity 0.25s;
  }
  .project-card:hover { border-color: rgba(0,212,255,0.25); transform: translateY(-2px); box-shadow: 0 12px 40px rgba(0,0,0,0.3); }
  .project-card:hover::before { opacity: 1; }

  .project-head { display: flex; align-items: flex-start; justify-content: space-between; gap: 16px; margin-bottom: 14px; }
  .project-title-group {}
  .project-label {
    font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 1.5px;
    text-transform: uppercase; color: var(--accent); margin-bottom: 5px;
  }
  .project-title {
    font-family: 'Syne', sans-serif; font-weight: 700; font-size: 19px;
    color: var(--text); margin-bottom: 4px;
  }
  .project-date { font-size: 11px; color: var(--muted); font-family: 'DM Mono', monospace; }
  .project-links { display: flex; gap: 8px; flex-shrink: 0; }
  .proj-link {
    padding: 5px 12px; border-radius: 6px; font-size: 11px;
    border: 1px solid var(--border); background: var(--surface2);
    color: var(--muted); text-decoration: none;
    font-family: 'DM Mono', monospace; transition: all 0.2s;
    display: flex; align-items: center; gap: 5px;
  }
  .proj-link:hover { border-color: var(--accent); color: var(--accent); }
  .proj-link svg { width: 11px; height: 11px; }

  .project-desc { font-size: 14px; color: #94a3b8; line-height: 1.75; margin-bottom: 16px; }
  .project-bullets { list-style: none; padding: 0; display: flex; flex-direction: column; gap: 8px; margin-bottom: 18px; }
  .project-bullets li {
    font-size: 13.5px; color: #94a3b8; line-height: 1.65;
    padding-left: 18px; position: relative;
  }
  .project-bullets li::before {
    content: '→'; position: absolute; left: 0;
    color: var(--accent); font-size: 11px; top: 3px;
  }
  .project-bullets li strong { color: var(--text); }
  .project-stack { display: flex; flex-wrap: wrap; gap: 6px; }
  .stack-tag {
    padding: 3px 9px; border-radius: 5px; font-size: 11px;
    background: rgba(255,255,255,0.04); border: 1px solid var(--border);
    color: var(--muted); font-family: 'DM Mono', monospace;
  }

  /* ── EDUCATION ── */
  .edu-card {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 16px; padding: 26px 28px;
    display: grid; grid-template-columns: 1fr auto; gap: 16px;
  }
  .edu-uni { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 17px; color: var(--text); margin-bottom: 4px; }
  .edu-degree { font-size: 14px; color: var(--muted); margin-bottom: 12px; }
  .edu-stats { display: flex; gap: 16px; flex-wrap: wrap; }
  .edu-stat { font-size: 12px; font-family: 'DM Mono', monospace; }
  .edu-stat .val { color: var(--success); font-weight: 500; }
  .edu-stat .key { color: var(--muted); }
  .edu-badge-col { display: flex; align-items: flex-start; }
  .gpa-ring {
    width: 72px; height: 72px; position: relative;
    display: flex; align-items: center; justify-content: center;
  }
  .gpa-ring svg { position: absolute; top: 0; left: 0; transform: rotate(-90deg); }
  .gpa-text { font-family: 'Syne', sans-serif; font-weight: 800; font-size: 15px; color: var(--accent); z-index: 1; }

  /* ── HACKATHON ── */
  .hack-card {
    background: linear-gradient(135deg, rgba(0,212,255,0.04), rgba(59,130,246,0.06));
    border: 1px solid rgba(0,212,255,0.18); border-radius: 16px; padding: 26px 28px;
    position: relative; overflow: hidden;
  }
  .hack-card::after {
    content: '⚡'; position: absolute; right: 28px; top: 20px;
    font-size: 48px; opacity: 0.06;
  }
  .hack-title { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 16px; color: var(--text); margin-bottom: 4px; }
  .hack-sub { font-size: 12px; font-family: 'DM Mono', monospace; color: var(--accent); margin-bottom: 14px; }
  .hack-bullets { list-style: none; padding: 0; display: flex; flex-direction: column; gap: 8px; }
  .hack-bullets li { font-size: 13.5px; color: #94a3b8; padding-left: 18px; position: relative; }
  .hack-bullets li::before { content: '⚡'; position: absolute; left: 0; font-size: 10px; top: 4px; }
  .hack-bullets li strong { color: var(--text); }

  /* ── ACHIEVEMENTS ── */
  .ach-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; }
  .ach-card {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 12px; padding: 18px 20px;
    transition: all 0.2s;
  }
  .ach-card:hover { border-color: rgba(0,212,255,0.2); transform: translateY(-2px); }
  .ach-icon { font-size: 22px; margin-bottom: 10px; }
  .ach-title { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 13px; color: var(--text); margin-bottom: 5px; }
  .ach-desc { font-size: 12.5px; color: var(--muted); line-height: 1.6; }
  .ach-desc strong { color: var(--accent); }

  /* ── PRINCIPLES ── */
  .principles { display: flex; flex-direction: column; gap: 2px; }
  .principle {
    display: grid; grid-template-columns: 200px 1fr;
    gap: 0; padding: 16px 0; border-bottom: 1px solid var(--border);
    transition: background 0.2s; border-radius: 8px;
  }
  .principle:last-child { border-bottom: none; }
  .principle:hover { background: rgba(255,255,255,0.02); padding-left: 8px; }
  .p-title { font-family: 'DM Mono', monospace; font-size: 12px; color: var(--accent); display: flex; align-items: center; gap: 8px; }
  .p-desc { font-size: 13.5px; color: var(--muted); line-height: 1.65; }

  /* ── CONTACT FOOTER ── */
  .footer-card {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 20px; padding: 40px; text-align: center;
    position: relative; overflow: hidden;
    margin-top: 16px;
  }
  .footer-card::before {
    content: ''; position: absolute; inset: 0;
    background: radial-gradient(ellipse at 50% 0%, rgba(0,212,255,0.06), transparent 60%);
  }
  .footer-card h2 {
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: 28px; margin-bottom: 10px; color: var(--text);
    position: relative;
  }
  .footer-card p { font-size: 14px; color: var(--muted); margin-bottom: 24px; position: relative; }
  .contact-links { display: flex; gap: 12px; justify-content: center; flex-wrap: wrap; position: relative; }
  .c-link {
    padding: 10px 20px; border-radius: 9px; font-size: 13px;
    border: 1px solid var(--border); background: var(--surface2);
    color: var(--text); text-decoration: none;
    font-family: 'DM Mono', monospace; transition: all 0.2s;
    display: flex; align-items: center; gap: 7px;
  }
  .c-link:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-2px); box-shadow: 0 6px 20px rgba(0,0,0,0.2); }

  /* ── CODE BLOCK ── */
  .code-block {
    background: var(--surface2); border: 1px solid var(--border);
    border-radius: 12px; padding: 22px 24px;
    font-family: 'DM Mono', monospace; font-size: 12.5px;
    line-height: 1.9; overflow-x: auto;
  }
  .code-block .c-kw { color: #818cf8; }
  .code-block .c-var { color: var(--accent); }
  .code-block .c-str { color: #86efac; }
  .code-block .c-key { color: #f9a8d4; }
  .code-block .c-arr { color: #fcd34d; }
  .code-block .c-cm { color: #374151; }
  .code-block .c-type { color: #67e8f9; }

  /* ── PROGRESS BARS ── */
  .progress-list { display: flex; flex-direction: column; gap: 14px; }
  .prog-item {}
  .prog-head { display: flex; justify-content: space-between; margin-bottom: 7px; font-family: 'DM Mono', monospace; font-size: 11.5px; }
  .prog-name { color: var(--text); }
  .prog-pct { color: var(--accent); }
  .prog-bar { height: 4px; background: var(--border); border-radius: 99px; overflow: hidden; }
  .prog-fill {
    height: 100%; border-radius: 99px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    transform-origin: left;
    animation: grow 1.4s cubic-bezier(.16,1,.3,1) forwards;
    transform: scaleX(0);
  }
  @keyframes grow { to { transform: scaleX(1); } }

  /* ── SCROLL REVEAL ── */
  .reveal { opacity: 0; transform: translateY(20px); transition: opacity 0.6s ease, transform 0.6s ease; }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* ── RESPONSIVE ── */
  @media (max-width: 640px) {
    .about-grid { grid-template-columns: 1fr; }
    .ach-grid { grid-template-columns: 1fr; }
    .principle { grid-template-columns: 1fr; gap: 6px; }
    .edu-card { grid-template-columns: 1fr; }
    .project-head { flex-direction: column; }
    .nav-links { display: none; }
  }
</style>
</head>
<body>

<div class="orb orb1"></div>
<div class="orb orb2"></div>
<div class="orb orb3"></div>

<!-- NAV -->
<nav>
  <div class="nav-inner">
    <span class="nav-logo">DS /</span>
    <div class="nav-links">
      <a href="#about">About</a>
      <a href="#skills">Skills</a>
      <a href="#projects">Projects</a>
      <a href="#education">Education</a>
      <a href="#contact">Contact</a>
    </div>
  </div>
</nav>

<div class="container">

  <!-- HERO -->
  <div class="hero reveal">
    <div class="hero-eyebrow">Full Stack Developer</div>
    <h1>
      <span class="line1">Deep</span>
      <span class="line2">Sorathiya</span>
    </h1>
    <p class="hero-sub">MERN Stack Specialist · SaaS Architect · Nirma University, Class of 2027</p>
    <div class="hero-badges">
      <span class="badge"><span class="dot"></span> Open to Internships</span>
      <span class="badge">📍 Ahmedabad, India</span>
      <span class="badge">🎓 CGPA 8.5 / 10.0</span>
      <span class="badge">⚡ 200+ LeetCode</span>
    </div>
    <div class="hero-ctas">
      <a href="mailto:deep.professional803@gmail.com" class="btn btn-primary">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
        Say Hello
      </a>
      <a href="https://github.com/Lerner-11052025-20" target="_blank" class="btn btn-ghost">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844a9.59 9.59 0 0 1 2.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>
        GitHub
      </a>
      <a href="https://www.linkedin.com/in/deepsorathiya7990/" target="_blank" class="btn btn-ghost">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
        LinkedIn
      </a>
    </div>
  </div>

  <!-- ABOUT -->
  <section id="about" class="reveal">
    <div class="section-header">
      <div class="section-icon">👤</div>
      <span class="section-title">$ whoami</span>
      <div class="section-line"></div>
    </div>

    <div class="code-block" style="margin-bottom:20px;">
<span class="c-kw">const</span> <span class="c-var">deep</span>: <span class="c-type">Developer</span> = {<br>
&nbsp;&nbsp;<span class="c-key">name</span>        : <span class="c-str">"Deep R. Sorathiya"</span>,<br>
&nbsp;&nbsp;<span class="c-key">role</span>        : <span class="c-str">"Full Stack Developer · MERN Specialist"</span>,<br>
&nbsp;&nbsp;<span class="c-key">university</span>  : <span class="c-str">"Nirma University, Ahmedabad (2027)"</span>,<br>
&nbsp;&nbsp;<span class="c-key">contact</span>     : <span class="c-str">"deep.professional803@gmail.com"</span>,<br>
&nbsp;&nbsp;<span class="c-key">focus</span>       : <span class="c-arr">[<span class="c-str">"SaaS Platforms"</span>, <span class="c-str">"REST API Design"</span>, <span class="c-str">"Scalable Architecture"</span>]</span>,<br>
&nbsp;&nbsp;<span class="c-key">availableFor</span>: <span class="c-arr">[<span class="c-str">"Internships"</span>, <span class="c-str">"SWE Roles"</span>, <span class="c-str">"Freelance"</span>]</span>,<br>
};
    </div>

    <div class="about-grid">
      <div class="about-text">
        CS undergraduate at <strong>Nirma University</strong> specializing in Full Stack Development. I build production-grade applications — from pixel-perfect UIs to structured backend logic. Proven track record with real shipped products, real users, and real results.<br><br>
        Currently sharpening my MERN stack skills while pursuing a <strong>SWE internship or entry-level role</strong> to contribute to scalable backend systems and data-driven product features. I care about code that's readable, systems that are resilient, and products that actually get used.
      </div>
      <div class="about-card">
        <div class="stat-row">
          <span class="stat-num">75+</span>
          <span class="stat-label">SaaS users served</span>
        </div>
        <div class="stat-divider"></div>
        <div class="stat-row">
          <span class="stat-num">200+</span>
          <span class="stat-label">LeetCode solved</span>
        </div>
        <div class="stat-divider"></div>
        <div class="stat-row">
          <span class="stat-num">3</span>
          <span class="stat-label">production projects</span>
        </div>
        <div class="stat-divider"></div>
        <div class="stat-row">
          <span class="stat-num">Top 10%</span>
          <span class="stat-label">of CS cohort</span>
        </div>
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section id="skills" class="reveal">
    <div class="section-header">
      <div class="section-icon">⚡</div>
      <span class="section-title">Tech Stack</span>
      <div class="section-line"></div>
    </div>

    <div class="skills-grid">
      <div class="skill-group">
        <div class="skill-group-label">Languages</div>
        <div class="skill-chips">
          <span class="chip accent">JavaScript ES6+</span>
          <span class="chip accent">TypeScript</span>
          <span class="chip">Python</span>
          <span class="chip">Java</span>
          <span class="chip">C</span>
          <span class="chip">SQL</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-label">Frontend</div>
        <div class="skill-chips">
          <span class="chip blue">React 18</span>
          <span class="chip blue">Tailwind CSS</span>
          <span class="chip blue">Shadcn UI</span>
          <span class="chip">HTML5</span>
          <span class="chip">CSS3</span>
          <span class="chip">Bootstrap</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-label">Backend & APIs</div>
        <div class="skill-chips">
          <span class="chip accent">Node.js</span>
          <span class="chip accent">Express.js</span>
          <span class="chip">REST APIs</span>
          <span class="chip">JWT Auth</span>
          <span class="chip">MVC</span>
          <span class="chip">RBAC</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-label">Databases</div>
        <div class="skill-chips">
          <span class="chip blue">MongoDB</span>
          <span class="chip blue">Supabase</span>
          <span class="chip">MySQL</span>
          <span class="chip">PostgreSQL</span>
          <span class="chip">Oracle SQL</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-label">Libraries & Tools</div>
        <div class="skill-chips">
          <span class="chip purple">Zustand</span>
          <span class="chip purple">TanStack Query</span>
          <span class="chip purple">Zod</span>
          <span class="chip purple">Razorpay SDK</span>
          <span class="chip">NumPy</span>
          <span class="chip">Pandas</span>
          <span class="chip">scikit-learn</span>
          <span class="chip">Git</span>
          <span class="chip">Vercel</span>
          <span class="chip">Render</span>
          <span class="chip">Postman</span>
        </div>
      </div>
    </div>

    <!-- Progress bars -->
    <div style="margin-top:28px;">
      <div class="skill-group-label" style="margin-bottom:18px;">Proficiency</div>
      <div class="progress-list">
        <div class="prog-item">
          <div class="prog-head"><span class="prog-name">React 18 (Hooks · State · Context)</span><span class="prog-pct">85%</span></div>
          <div class="prog-bar"><div class="prog-fill" style="width:85%;animation-delay:0.1s"></div></div>
        </div>
        <div class="prog-item">
          <div class="prog-head"><span class="prog-name">Node.js / Express.js APIs</span><span class="prog-pct">80%</span></div>
          <div class="prog-bar"><div class="prog-fill" style="width:80%;animation-delay:0.2s"></div></div>
        </div>
        <div class="prog-item">
          <div class="prog-head"><span class="prog-name">TypeScript & Zod Validation</span><span class="prog-pct">75%</span></div>
          <div class="prog-bar"><div class="prog-fill" style="width:75%;animation-delay:0.3s"></div></div>
        </div>
        <div class="prog-item">
          <div class="prog-head"><span class="prog-name">MongoDB / Supabase (PostgreSQL)</span><span class="prog-pct">78%</span></div>
          <div class="prog-bar"><div class="prog-fill" style="width:78%;animation-delay:0.4s"></div></div>
        </div>
        <div class="prog-item">
          <div class="prog-head"><span class="prog-name">UI/UX · Tailwind · Figma</span><span class="prog-pct">82%</span></div>
          <div class="prog-bar"><div class="prog-fill" style="width:82%;animation-delay:0.5s"></div></div>
        </div>
      </div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects" class="reveal">
    <div class="section-header">
      <div class="section-icon">🚀</div>
      <span class="section-title">Shipped Projects</span>
      <div class="section-line"></div>
    </div>
    <div class="projects">

      <!-- SnapCut -->
      <div class="project-card">
        <div class="project-head">
          <div class="project-title-group">
            <div class="project-label">SaaS Platform · Production</div>
            <div class="project-title">SnapCut AI</div>
            <div class="project-date">Aug – Nov 2025</div>
          </div>
          <div class="project-links">
            <a href="https://github.com/Lerner-11052025-20/snapcut-ai" target="_blank" class="proj-link">
              <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844a9.59 9.59 0 0 1 2.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>
              GitHub
            </a>
            <a href="https://snapcut-ai-beta.vercel.app" target="_blank" class="proj-link">↗ Live</a>
          </div>
        </div>
        <ul class="project-bullets">
          <li>Architected production SaaS serving <strong>75+ active users</strong> with AI background removal at <strong>0.8s avg</strong> processing time via optimized API integration and state management.</li>
          <li>Implemented Razorpay webhook pipeline for <strong>Free/Pro subscription</strong> management and live credit tracking across user sessions.</li>
          <li>Optimized Core Web Vitals via <strong>LCP-first rendering & lazy hydration</strong> — resulting in 40% faster initial page load.</li>
          <li>End-to-end <strong>TypeScript + Zod schema validation</strong> across all API structures, reducing runtime errors by 60%.</li>
        </ul>
        <div class="project-stack">
          <span class="stack-tag">React 18</span><span class="stack-tag">TypeScript</span>
          <span class="stack-tag">Supabase</span><span class="stack-tag">Razorpay</span>
          <span class="stack-tag">Zustand</span><span class="stack-tag">TanStack Query</span>
          <span class="stack-tag">Tailwind CSS</span>
        </div>
      </div>

      <!-- TiffinConnect -->
      <div class="project-card">
        <div class="project-head">
          <div class="project-title-group">
            <div class="project-label">Food Delivery · Full Stack</div>
            <div class="project-title">TiffinConnect</div>
            <div class="project-date">Dec 2025 – Jan 2026</div>
          </div>
          <div class="project-links">
            <a href="https://github.com/Lerner-11052025-20/tiffin-connect-hub-59" target="_blank" class="proj-link">
              <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844a9.59 9.59 0 0 1 2.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>
              GitHub
            </a>
            <a href="https://tiffin-connect-hub-59.vercel.app" target="_blank" class="proj-link">↗ Live</a>
          </div>
        </div>
        <ul class="project-bullets">
          <li>Built dual-panel platform (Customer + Admin) with <strong>Node.js/Express.js backend</strong>, Supabase auth, and RBAC across all user roles.</li>
          <li>Designed end-to-end <strong>order lifecycle</strong> — browsing, cart, placement, status tracking, and fulfillment.</li>
          <li>Engineered live UI state sync via <strong>React Context API</strong> ensuring consistent data across all views without page refresh.</li>
          <li>RESTful API endpoints for menu management, auth, order processing with full error handling and input validation.</li>
        </ul>
        <div class="project-stack">
          <span class="stack-tag">React 18</span><span class="stack-tag">Node.js</span>
          <span class="stack-tag">Express.js</span><span class="stack-tag">MongoDB Atlas</span>
          <span class="stack-tag">Supabase</span><span class="stack-tag">Shadcn UI</span>
          <span class="stack-tag">Tailwind CSS</span>
        </div>
      </div>

      <!-- FleetFlow -->
      <div class="project-card">
        <div class="project-head">
          <div class="project-title-group">
            <div class="project-label">Logistics Platform · Hackathon</div>
            <div class="project-title">FleetFlow</div>
            <div class="project-date">Feb 2026</div>
          </div>
          <div class="project-links">
            <a href="https://github.com/Lerner-11052025-20/fleetflow" target="_blank" class="proj-link">
              <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844a9.59 9.59 0 0 1 2.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>
              GitHub
            </a>
            <a href="https://fleetflow-logistic-management-system-ge60.onrender.com" target="_blank" class="proj-link">↗ Live</a>
          </div>
        </div>
        <ul class="project-bullets">
          <li>Built at <strong>Odoo Hackathon</strong> — full logistics platform with RBAC spanning Admin, Driver, and Manager roles with isolated dashboards.</li>
          <li>RESTful API layer managing vehicle registry, driver assignments, and <strong>shipment lifecycle with full CRUD</strong> over structured MongoDB model.</li>
          <li>Real-time tracking dashboard with live vehicle locations, shipment statuses, and automated route optimization suggestions.</li>
          <li>Delivered production-ready MERN app within <strong>48-hour hackathon timeline</strong> in a team environment.</li>
        </ul>
        <div class="project-stack">
          <span class="stack-tag">React.js</span><span class="stack-tag">Node.js</span>
          <span class="stack-tag">Express.js</span><span class="stack-tag">MongoDB</span>
          <span class="stack-tag">REST APIs</span><span class="stack-tag">JavaScript</span>
        </div>
      </div>

    </div>
  </section>

  <!-- EDUCATION -->
  <section id="education" class="reveal">
    <div class="section-header">
      <div class="section-icon">🎓</div>
      <span class="section-title">Education</span>
      <div class="section-line"></div>
    </div>
    <div class="edu-card">
      <div>
        <div class="edu-uni">Institute of Technology, Nirma University</div>
        <div class="edu-degree">B.Tech in Computer Science & Engineering &nbsp;·&nbsp; Aug 2023 – May 2027</div>
        <div class="edu-stats">
          <div class="edu-stat"><span class="val">8.5 / 10.0</span> <span class="key">CGPA</span></div>
          <div class="edu-stat"><span class="val">92%</span> <span class="key">Sem 1</span></div>
          <div class="edu-stat"><span class="val">Top 10%</span> <span class="key">of cohort</span></div>
          <div class="edu-stat"><span class="val">🏆</span> <span class="key">Academic Excellence Cert (2023)</span></div>
        </div>
      </div>
      <div class="edu-badge-col">
        <div class="gpa-ring">
          <svg width="72" height="72" viewBox="0 0 72 72">
            <circle cx="36" cy="36" r="29" fill="none" stroke="#1e2a3a" stroke-width="5"/>
            <circle cx="36" cy="36" r="29" fill="none" stroke="url(#gpaGrad)" stroke-width="5"
              stroke-dasharray="182.2" stroke-dashoffset="30.97" stroke-linecap="round"/>
            <defs>
              <linearGradient id="gpaGrad" x1="0%" y1="0%" x2="100%" y2="0%">
                <stop offset="0%" stop-color="#00d4ff"/>
                <stop offset="100%" stop-color="#3b82f6"/>
              </linearGradient>
            </defs>
          </svg>
          <span class="gpa-text">8.5</span>
        </div>
      </div>
    </div>

    <div style="margin-top:18px;">
      <div class="skill-group-label" style="margin-bottom:14px;">Relevant Coursework</div>
      <div class="skill-chips">
        <span class="chip">Data Structures & Algorithms</span>
        <span class="chip">Database Management Systems</span>
        <span class="chip">Computer Networks</span>
        <span class="chip">Operating Systems</span>
        <span class="chip">Software Engineering</span>
        <span class="chip">Machine Learning</span>
        <span class="chip">Cloud Computing</span>
        <span class="chip">UI/UX Design</span>
      </div>
    </div>
  </section>

  <!-- HACKATHON -->
  <section class="reveal">
    <div class="section-header">
      <div class="section-icon">⚡</div>
      <span class="section-title">Hackathon</span>
      <div class="section-line"></div>
    </div>
    <div class="hack-card">
      <div class="hack-title">Odoo Hackathon 2024 — Full Stack Developer</div>
      <div class="hack-sub">Nirma University · October 2024 · Team of 4</div>
      <ul class="hack-bullets">
        <li>Built & shipped a production-ready <strong>MERN application in 48 hours</strong> with a team of 4 developers.</li>
        <li>Implemented <strong>JWT Authentication</strong> with session management, bcrypt hashing, and token refresh mechanisms.</li>
        <li>Architected <strong>10+ RESTful API endpoints</strong> achieving sub-200ms avg response time under concurrent load via efficient DB queries and indexing.</li>
        <li>Responsive mobile-first UI using <strong>React.js + Tailwind CSS</strong> with MVC architecture and modular component design.</li>
      </ul>
    </div>
  </section>

  <!-- ACHIEVEMENTS -->
  <section class="reveal">
    <div class="section-header">
      <div class="section-icon">🏆</div>
      <span class="section-title">Achievements</span>
      <div class="section-line"></div>
    </div>
    <div class="ach-grid">
      <div class="ach-card">
        <div class="ach-icon">🎓</div>
        <div class="ach-title">Academic Excellence</div>
        <div class="ach-desc">Achieved <strong>92%</strong> in Semester 1 at Nirma University — ranked in top 10% of B.Tech CS cohort. Awarded Academic Excellence Certificate (2023).</div>
      </div>
      <div class="ach-card">
        <div class="ach-icon">⚡</div>
        <div class="ach-title">Hackathon Recognition</div>
        <div class="ach-desc">Delivered a full-stack MERN application at <strong>Odoo Hackathon 2024</strong> with JWT Auth and REST APIs within a 48-hour deadline.</div>
      </div>
      <div class="ach-card">
        <div class="ach-icon">🧠</div>
        <div class="ach-title">Competitive Programming</div>
        <div class="ach-desc">Solved <strong>200+ LeetCode problems</strong> across DSA, dynamic programming, and graphs to strengthen SWE interview readiness.</div>
      </div>
      <div class="ach-card">
        <div class="ach-icon">📦</div>
        <div class="ach-title">SaaS Launched</div>
        <div class="ach-desc">Shipped SnapCut AI — a production SaaS platform serving <strong>75+ active users</strong> with payment integration and real-time credit tracking.</div>
      </div>
    </div>
  </section>

  <!-- PRINCIPLES -->
  <section class="reveal">
    <div class="section-header">
      <div class="section-icon">🧭</div>
      <span class="section-title">Dev Principles</span>
      <div class="section-line"></div>
    </div>
    <div class="principles">
      <div class="principle">
        <div class="p-title">🎯 Clarity over Cleverness</div>
        <div class="p-desc">Code is read far more than it is written. Optimize for the next developer.</div>
      </div>
      <div class="principle">
        <div class="p-title">🔩 Systems Before Features</div>
        <div class="p-desc">A weak foundation amplifies every future mistake. Architect first, ship right.</div>
      </div>
      <div class="principle">
        <div class="p-title">🔁 Ship, Learn, Iterate</div>
        <div class="p-desc">Perfect is the enemy of deployed. Release, measure, improve relentlessly.</div>
      </div>
      <div class="principle">
        <div class="p-title">🧩 Design is Logic</div>
        <div class="p-desc">Good UI is not decoration — it is problem-solving made visible and usable.</div>
      </div>
      <div class="principle">
        <div class="p-title">📖 Teach to Solidify</div>
        <div class="p-desc">If you cannot explain it simply, you do not understand it yet.</div>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact" class="reveal">
    <div class="footer-card">
      <h2>Let's build something worth shipping.</h2>
      <p>Open to SWE internships, entry-level roles, and collaborative projects. Let's talk.</p>
      <div class="contact-links">
        <a href="mailto:deep.professional803@gmail.com" class="c-link">
          <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
          deep.professional803@gmail.com
        </a>
        <a href="https://www.linkedin.com/in/deepsorathiya7990/" target="_blank" class="c-link">
          <svg width="13" height="13" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
          LinkedIn
        </a>
        <a href="https://github.com/Lerner-11052025-20" target="_blank" class="c-link">
          <svg width="13" height="13" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844a9.59 9.59 0 0 1 2.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>
          GitHub
        </a>
        <a href="tel:+917990082149" class="c-link">
          <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.99 12a19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 3.9 1.18h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L8.09 8.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7a2 2 0 0 1 1.72 2.02z"/></svg>
          +91 7990082149
        </a>
      </div>
    </div>
    <p style="text-align:center;font-family:'DM Mono',monospace;font-size:11px;color:var(--muted);margin-top:28px;">
      Crafted with intent by <strong style="color:var(--text)">Deep Sorathiya</strong> — <em>Create · Conquer · Code</em>
    </p>
  </section>

</div>

<script>
  // Scroll reveal
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        e.target.style.transitionDelay = `${i * 0.05}s`;
        e.target.classList.add('visible');
      }
    });
  }, { threshold: 0.1 });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  // Progress bars trigger on scroll
  const progObs = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.querySelectorAll('.prog-fill').forEach(bar => {
          bar.style.animationPlayState = 'running';
        });
      }
    });
  }, { threshold: 0.3 });
  document.querySelectorAll('.progress-list').forEach(el => {
    el.querySelectorAll('.prog-fill').forEach(b => b.style.animationPlayState = 'paused');
    progObs.observe(el);
  });

  // Active nav link
  const sections = document.querySelectorAll('section[id]');
  const navLinks = document.querySelectorAll('.nav-links a');
  window.addEventListener('scroll', () => {
    let cur = '';
    sections.forEach(s => { if (window.scrollY >= s.offsetTop - 100) cur = s.id; });
    navLinks.forEach(a => {
      a.style.color = a.getAttribute('href') === '#' + cur ? 'var(--accent)' : '';
    });
  });
</script>
</body>
</html>
