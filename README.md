<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GrahamTheDev – GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --pb-50: #fdf4ff;
    --pb-100: #f3e0ff;
    --pb-200: #e5b8ff;
    --pb-300: #d07fff;
    --pb-400: #bf40ff;
    --pb-500: #a200ff;
    --pb-600: #8200cc;
    --pb-700: #5e0099;
    --pb-800: #3d0066;
    --pb-900: #1e0033;
    --bg: #0a0010;
    --bg2: #110018;
    --bg3: #1a0026;
    --card: #160020;
    --glow: rgba(191, 64, 255, 0.4);
    --glow2: rgba(208, 127, 255, 0.2);
    --text: #f3e0ff;
    --text-muted: #d07fff;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ─── Background grid ─── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image:
      linear-gradient(rgba(191,64,255,.07) 1px, transparent 1px),
      linear-gradient(90deg, rgba(191,64,255,.07) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .wrapper {
    position: relative; z-index: 1;
    max-width: 960px;
    margin: 0 auto;
    padding: 24px 20px;
    display: grid;
    grid-template-columns: 230px 1fr;
    grid-template-rows: auto;
    gap: 16px;
  }

  /* ─── Sidebar ─── */
  .sidebar {
    grid-column: 1;
    grid-row: 1 / 4;
    display: flex; flex-direction: column; gap: 14px;
  }

  .avatar-wrap {
    position: relative;
    width: 100%;
    aspect-ratio: 1;
    max-width: 190px;
    margin: 0 auto;
  }

  .avatar-ring {
    position: absolute; inset: -4px;
    border-radius: 50%;
    background: conic-gradient(from 0deg, var(--pb-400), var(--pb-200), var(--pb-600), var(--pb-400));
    animation: spin 6s linear infinite;
  }

  @keyframes spin { to { transform: rotate(360deg); } }

  .avatar-inner {
    position: relative; z-index: 1;
    width: 100%; height: 100%;
    border-radius: 50%;
    background: var(--bg3);
    border: 3px solid var(--bg);
    overflow: hidden;
    display: flex; align-items: center; justify-content: center;
    font-size: 64px;
  }

  .avatar-inner img {
    width: 100%; height: 100%; object-fit: cover;
  }

  .username-block { text-align: center; }
  .username-block h1 { font-size: 1.15rem; font-weight: 800; color: var(--pb-100); }
  .username-block .handle {
    font-family: 'Space Mono', monospace;
    font-size: .7rem;
    color: var(--pb-400);
    margin-top: 2px;
  }

  .bio {
    font-size: .78rem;
    color: var(--text-muted);
    line-height: 1.5;
    text-align: center;
  }
  .bio a { color: var(--pb-300); text-decoration: none; font-weight: 700; }
  .bio a:hover { color: var(--pb-100); }

  .btn-group { display: flex; flex-direction: column; gap: 8px; }

  .btn {
    display: block; text-align: center;
    padding: 8px 14px;
    border-radius: 8px;
    font-family: 'Syne', sans-serif;
    font-weight: 700; font-size: .8rem;
    cursor: pointer;
    text-decoration: none;
    transition: all .2s;
    letter-spacing: .04em;
  }

  .btn-primary {
    background: transparent;
    border: 1.5px solid var(--pb-400);
    color: var(--pb-200);
    box-shadow: 0 0 12px var(--glow);
  }
  .btn-primary:hover {
    background: var(--pb-400);
    color: #0a0010;
    box-shadow: 0 0 24px var(--glow);
  }

  .btn-ghost {
    background: var(--bg3);
    border: 1.5px solid rgba(191,64,255,.25);
    color: var(--pb-300);
  }
  .btn-ghost:hover { border-color: var(--pb-400); color: var(--pb-100); }

  .meta-list { display: flex; flex-direction: column; gap: 6px; }
  .meta-item {
    display: flex; align-items: center; gap: 8px;
    font-size: .75rem; color: var(--text-muted);
    font-family: 'Space Mono', monospace;
  }
  .meta-item .icon { color: var(--pb-400); font-size: .85rem; }

  .followers-row {
    display: flex; gap: 14px;
    font-size: .75rem;
    font-family: 'Space Mono', monospace;
    color: var(--text-muted);
  }
  .followers-row span { color: var(--pb-200); font-weight: 700; }

  .section-label {
    font-size: .65rem;
    text-transform: uppercase;
    letter-spacing: .12em;
    color: var(--pb-500);
    font-family: 'Space Mono', monospace;
    margin-bottom: 6px;
  }

  .achievements { display: flex; gap: 8px; flex-wrap: wrap; }
  .badge {
    width: 36px; height: 36px;
    border-radius: 50%;
    background: var(--bg3);
    border: 1.5px solid var(--pb-700);
    display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem;
    transition: all .2s;
    cursor: pointer;
  }
  .badge:hover {
    border-color: var(--pb-400);
    box-shadow: 0 0 10px var(--glow);
    transform: translateY(-2px);
  }

  .highlights-list { display: flex; flex-direction: column; gap: 5px; }
  .highlight-item {
    display: flex; align-items: center; gap: 6px;
    font-size: .72rem;
    color: var(--pb-300);
    font-family: 'Space Mono', monospace;
  }
  .pro-badge {
    display: inline-block;
    padding: 1px 7px;
    border-radius: 4px;
    background: linear-gradient(135deg, var(--pb-500), var(--pb-300));
    color: #0a0010;
    font-size: .62rem;
    font-weight: 800;
    letter-spacing: .06em;
  }

  .org-list { display: flex; gap: 8px; flex-wrap: wrap; }
  .org-icon {
    width: 32px; height: 32px;
    border-radius: 8px;
    background: var(--bg3);
    border: 1.5px solid var(--pb-700);
    display: flex; align-items: center; justify-content: center;
    font-size: .85rem;
    transition: all .2s;
  }
  .org-icon:hover { border-color: var(--pb-400); box-shadow: 0 0 10px var(--glow); }

  /* ─── Main area ─── */
  .main-area {
    grid-column: 2;
    display: flex; flex-direction: column; gap: 16px;
  }

  /* ─── Top bar ─── */
  .topbar {
    background: var(--bg2);
    border: 1px solid rgba(74,174,232,.2);
    border-radius: 14px;
    padding: 10px 16px;
    display: flex; align-items: center; gap: 8px;
    font-family: 'Space Mono', monospace;
    font-size: .72rem;
    color: var(--pb-500);
    box-shadow: inset 0 0 30px rgba(80,0,120,.3);
  }
  .topbar .path { color: var(--pb-300); }
  .topbar .ref {
    margin-left: auto;
    background: var(--bg3);
    border: 1px solid var(--pb-700);
    border-radius: 6px;
    padding: 3px 8px;
    color: var(--pb-400);
  }

  /* ─── Social links ─── */
  .socials {
    display: flex; gap: 10px; flex-wrap: wrap;
  }

  .social-btn {
    display: flex; align-items: center; gap: 7px;
    padding: 8px 14px;
    border-radius: 10px;
    background: var(--card);
    border: 1.5px solid var(--pb-700);
    color: var(--pb-200);
    font-weight: 700; font-size: .78rem;
    text-decoration: none;
    transition: all .22s;
    cursor: pointer;
  }
  .social-btn:hover {
    border-color: var(--pb-400);
    color: #fff;
    box-shadow: 0 0 14px var(--glow);
    transform: translateY(-2px);
  }
  .social-btn .s-icon { font-size: 1rem; }

  /* ─── Hero banner ─── */
  .hero-banner {
    position: relative;
    border-radius: 16px;
    overflow: hidden;
    background: var(--card);
    border: 1px solid rgba(191,64,255,.25);
    min-height: 160px;
    display: flex; align-items: center;
    padding: 24px;
    box-shadow: 0 0 40px rgba(162,0,255,.15);
  }

  .hero-banner::before {
    content: '';
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse 60% 80% at 70% 50%, rgba(191,64,255,.12) 0%, transparent 70%),
      radial-gradient(ellipse 40% 60% at 20% 50%, rgba(162,0,255,.08) 0%, transparent 70%);
  }

  .hero-text { position: relative; z-index: 1; max-width: 55%; }
  .hero-text h2 {
    font-size: 1.5rem; font-weight: 800;
    line-height: 1.2;
    color: var(--pb-100);
    margin-bottom: 8px;
  }
  .hero-text h2 .accent { color: var(--pb-400); }
  .hero-text p { font-size: .82rem; color: var(--text-muted); line-height: 1.5; }

  .speech-bubble {
    position: absolute; right: 24px; top: 50%; transform: translateY(-50%);
    background: var(--pb-500);
    color: #fdf4ff;
    font-size: .72rem;
    font-weight: 700;
    padding: 10px 14px;
    border-radius: 14px 14px 14px 4px;
    max-width: 160px;
    text-align: center;
    line-height: 1.4;
    box-shadow: 0 0 20px rgba(162,0,255,.6);
    animation: float 3s ease-in-out infinite;
  }
  .speech-bubble::after {
    content: '';
    position: absolute;
    bottom: -10px; left: 20px;
    border: 6px solid transparent;
    border-top-color: var(--pb-500);
  }

  @keyframes float {
    0%, 100% { transform: translateY(-50%); }
    50% { transform: translateY(calc(-50% - 6px)); }
  }

  /* ─── Cards grid ─── */
  .cards-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 14px;
  }

  .card {
    background: var(--card);
    border: 1px solid rgba(191,64,255,.2);
    border-radius: 14px;
    padding: 20px;
    position: relative;
    overflow: hidden;
    transition: all .25s;
    cursor: pointer;
  }
  .card::before {
    content: '';
    position: absolute; inset: 0;
    background: radial-gradient(ellipse 80% 80% at 50% 0%, rgba(191,64,255,.08) 0%, transparent 70%);
    opacity: 0;
    transition: opacity .3s;
  }
  .card:hover {
    border-color: var(--pb-400);
    box-shadow: 0 0 24px var(--glow);
    transform: translateY(-3px);
  }
  .card:hover::before { opacity: 1; }

  .card-header {
    display: flex; align-items: flex-start; justify-content: space-between;
    margin-bottom: 10px;
  }
  .card-title { font-size: .95rem; font-weight: 800; color: var(--pb-100); }
  .card-tag {
    font-size: .62rem;
    font-family: 'Space Mono', monospace;
    padding: 3px 9px;
    border-radius: 20px;
    background: rgba(191,64,255,.15);
    border: 1px solid var(--pb-600);
    color: var(--pb-300);
    font-weight: 700;
    letter-spacing: .06em;
    text-transform: uppercase;
  }
  .card-desc { font-size: .75rem; color: var(--text-muted); line-height: 1.5; }

  .card-logo {
    margin-top: 14px;
    display: inline-flex; align-items: center; justify-content: center;
    padding: 8px 14px;
    border-radius: 10px;
    font-weight: 800;
    font-size: .85rem;
    letter-spacing: .04em;
  }

  .card-dev .card-logo {
    background: var(--pb-700);
    color: var(--pb-100);
    border: 1.5px solid var(--pb-500);
    font-family: 'Space Mono', monospace;
  }

  .card-wcag .card-logo {
    background: transparent;
    color: var(--pb-300);
    border: 1.5px solid var(--pb-600);
    font-family: 'Space Mono', monospace;
    font-size: .7rem;
  }

  .card-a11y .monster-emoji {
    font-size: 2.5rem;
    filter: drop-shadow(0 0 12px var(--pb-400));
    animation: wiggle 2.5s ease-in-out infinite;
    display: block; margin-top: 10px;
  }

  @keyframes wiggle {
    0%, 100% { transform: rotate(-5deg); }
    50% { transform: rotate(5deg); }
  }

  .card-totaly .site-badge {
    margin-top: 12px;
    display: inline-block;
    font-family: 'Space Mono', monospace;
    font-size: .72rem;
    color: var(--pb-400);
    font-weight: 700;
    letter-spacing: .08em;
    border-bottom: 2px solid var(--pb-500);
    padding-bottom: 2px;
  }

  .card-btn {
    display: inline-flex; align-items: center; gap: 5px;
    margin-top: 14px;
    padding: 6px 12px;
    border-radius: 7px;
    font-size: .7rem; font-weight: 700;
    background: transparent;
    border: 1.5px solid var(--pb-500);
    color: var(--pb-300);
    cursor: pointer;
    transition: all .2s;
    text-decoration: none;
    font-family: 'Syne', sans-serif;
  }
  .card-btn:hover {
    background: var(--pb-500);
    color: #0a0010;
    box-shadow: 0 0 14px var(--glow);
  }

  /* ─── Scanline overlay ─── */
  body::after {
    content: '';
    position: fixed; inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(10,0,16,.07) 2px,
      rgba(10,0,16,.07) 4px
    );
    pointer-events: none;
    z-index: 999;
  }

  /* ─── Animations on load ─── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .sidebar   { animation: fadeUp .5s ease both; }
  .topbar    { animation: fadeUp .5s .1s ease both; }
  .socials   { animation: fadeUp .5s .18s ease both; }
  .hero-banner { animation: fadeUp .5s .26s ease both; }
  .cards-grid  { animation: fadeUp .5s .34s ease both; }

  /* responsive */
  @media (max-width: 680px) {
    .wrapper { grid-template-columns: 1fr; }
    .sidebar { grid-column: 1; grid-row: auto; }
    .main-area { grid-column: 1; }
    .speech-bubble { display: none; }
    .hero-text { max-width: 100%; }
  }
</style>
</head>
<body>

<div class="wrapper">

  <!-- ── SIDEBAR ── -->
  <aside class="sidebar">

    <div class="avatar-wrap">
      <div class="avatar-ring"></div>
      <div class="avatar-inner">👨‍💻</div>
    </div>

    <div class="username-block">
      <h1>GrahamTheDev</h1>
      <div class="handle">@GrahamTheDev</div>
    </div>

    <p class="bio">
      You really should check out my AaaS, by which I mean
      <a href="https://tota11y.dev">Accessibility as a Service</a>
      company, <a href="https://tota11y.dev">tota11y.dev</a>!
    </p>

    <div class="btn-group">
      <a href="#" class="btn btn-primary">Edit profile</a>
      <a href="#" class="btn btn-ghost">Sponsors dashboard</a>
    </div>

    <div class="followers-row">
      <div><span>41</span> followers</div>
      <div><span>2</span> following</div>
    </div>

    <div class="meta-list">
      <div class="meta-item"><span class="icon">🌍</span> UK</div>
      <div class="meta-item"><span class="icon">🕐</span> 10:13 (UTC)</div>
      <div class="meta-item"><span class="icon">🔗</span> thegraham.dev</div>
      <div class="meta-item"><span class="icon">𝕏</span> @GrahamTheDev</div>
    </div>

    <div>
      <div class="section-label">Achievements</div>
      <div class="achievements">
        <div class="badge" title="Arctic Code Vault">🌊</div>
        <div class="badge" title="Starstruck">⭐</div>
        <div class="badge" title="Pull Shark">🦈</div>
        <div class="badge" title="YOLO">🎯</div>
      </div>
    </div>

    <div>
      <div class="section-label">Highlights</div>
      <div class="highlights-list">
        <div class="highlight-item">
          <span class="pro-badge">PRO</span>
          GitHub Pro
        </div>
      </div>
    </div>

    <div>
      <div class="section-label">Organizations</div>
      <div class="org-list">
        <div class="org-icon">♿</div>
        <div class="org-icon">🔷</div>
        <div class="org-icon">🌐</div>
      </div>
    </div>

  </aside>

  <!-- ── MAIN ── -->
  <div class="main-area">

    <!-- Topbar -->
    <div class="topbar">
      <span>GrahamTheDev</span>
      <span style="color:var(--pb-700)">/</span>
      <span class="path">GrahamTheDev</span>
      <span style="color:var(--pb-700)">Public</span>
      <div class="ref">✦ README</div>
    </div>

    <!-- Social links -->
    <div class="socials">
      <a href="#" class="social-btn"><span class="s-icon">𝕏</span> X / Twitter</a>
      <a href="#" class="social-btn"><span class="s-icon">in</span> LinkedIn</a>
      <a href="#" class="social-btn"><span class="s-icon">◇</span> Portfolio</a>
      <a href="#" class="social-btn"><span class="s-icon">▶</span> YouTube</a>
      <a href="#" class="social-btn"><span class="s-icon">📡</span> Twitch</a>
    </div>

    <!-- Hero -->
    <div class="hero-banner">
      <div class="hero-text">
        <h2>Building a more<br><span class="accent">accessible</span> web.</h2>
        <p>Accessibility advocate, developer educator, and founder of tota11y.dev — giving teams the tools to deliver world-class accessibility.</p>
      </div>
      <div class="speech-bubble">
        Nice, using dark mode I see, like a true developer! hehe!
      </div>
    </div>

    <!-- Cards -->
    <div class="cards-grid">

      <!-- My Writing -->
      <div class="card card-dev">
        <div class="card-header">
          <span class="card-title">My Writing</span>
          <div style="display:flex;gap:6px">
            <span class="card-tag">Read</span>
            <span class="card-tag">Study</span>
          </div>
        </div>
        <p class="card-desc">You will find me writing about tech, web dev, accessibility, "breaking the internet" and more on DEV.</p>
        <div class="card-logo">{ DEV }</div>
      </div>

      <!-- A11y Monsters -->
      <div class="card card-a11y">
        <div class="card-header">
          <span class="card-title">A11y Monsters</span>
        </div>
        <p class="card-desc">An Accessibility cohort to take you from zero to hero on accessibility in no time.</p>
        <span class="monster-emoji">👾</span>
      </div>

      <!-- WCAG 101 -->
      <div class="card card-wcag">
        <div class="card-header">
          <span class="card-title">WCAG 101</span>
          <span class="card-tag">Learn</span>
        </div>
        <p class="card-desc">The Web Content Accessibility Guidelines (WCAG) are complicated — this project aims to simplify them!</p>
        <div class="card-logo">⫿ WCAG 101</div>
      </div>

      <!-- tota11y.dev -->
      <div class="card card-totaly">
        <div class="card-header">
          <span class="card-title">tota11y.dev</span>
          <span class="card-tag">Grow</span>
        </div>
        <p class="card-desc">Accessibility as a Service — one click away from giving your team the training and knowledge it needs to deliver world-class accessibility.</p>
        <div class="site-badge">tota11y.dev →</div>
      </div>

    </div>

  </div>
</div>

</body>
</html>
