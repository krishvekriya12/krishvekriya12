<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Krish Vekriya – Flutter & Android Dev</title>
<link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0d1117;
    --bg2: #161b22;
    --bg3: #21262d;
    --violet: #a78bfa;
    --violet-dim: #7c3aed;
    --violet-glow: rgba(167,139,250,0.15);
    --violet-border: rgba(167,139,250,0.3);
    --indigo: #818cf8;
    --text: #e6edf3;
    --text-muted: #8b949e;
    --text-dim: #6e7681;
    --border: rgba(255,255,255,0.08);
    --radius: 12px;
    --font-code: 'Fira Code', monospace;
    --font-ui: 'Inter', sans-serif;
  }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-ui);
    line-height: 1.6;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── HERO ── */
  .hero {
    position: relative;
    padding: 60px 24px 48px;
    text-align: center;
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 50% -10%, rgba(124,58,237,0.18) 0%, transparent 70%),
      radial-gradient(ellipse 50% 40% at 80% 80%, rgba(129,140,248,0.08) 0%, transparent 60%);
    pointer-events: none;
  }

  .grid-bg {
    position: absolute;
    inset: 0;
    background-image:
      linear-gradient(rgba(167,139,250,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(167,139,250,0.04) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
  }

  /* Phone SVG Frame */
  .phone-frame {
    position: relative;
    width: 120px;
    margin: 0 auto 28px;
    animation: float 4s ease-in-out infinite;
    filter: drop-shadow(0 0 24px rgba(167,139,250,0.4));
  }

  @keyframes float {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-8px); }
  }

  .status-dot {
    width: 10px; height: 10px;
    background: #22c55e;
    border-radius: 50%;
    display: inline-block;
    margin-right: 6px;
    animation: pulse-dot 2s ease-in-out infinite;
    box-shadow: 0 0 8px #22c55e;
  }
  @keyframes pulse-dot {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.4; }
  }

  .badge-status {
    display: inline-flex;
    align-items: center;
    font-family: var(--font-code);
    font-size: 12px;
    color: #22c55e;
    background: rgba(34,197,94,0.1);
    border: 1px solid rgba(34,197,94,0.25);
    border-radius: 20px;
    padding: 4px 12px;
    margin-bottom: 20px;
    letter-spacing: 0.04em;
  }

  .hero-name {
    font-size: clamp(36px, 8vw, 64px);
    font-weight: 700;
    letter-spacing: -1.5px;
    line-height: 1.1;
    margin-bottom: 12px;
    background: linear-gradient(135deg, #e6edf3 30%, var(--violet) 70%, var(--indigo) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-title {
    font-family: var(--font-code);
    font-size: 16px;
    color: var(--violet);
    margin-bottom: 8px;
    letter-spacing: 0.02em;
  }

  .hero-studio {
    font-size: 14px;
    color: var(--text-muted);
    margin-bottom: 32px;
  }
  .hero-studio span {
    color: var(--indigo);
    font-weight: 500;
  }

  /* Floating tech chips */
  .chips {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    justify-content: center;
    margin-bottom: 36px;
  }
  .chip {
    font-family: var(--font-code);
    font-size: 12px;
    padding: 5px 14px;
    border-radius: 20px;
    border: 1px solid var(--violet-border);
    background: var(--violet-glow);
    color: var(--violet);
    letter-spacing: 0.03em;
    animation: chip-in 0.5s ease both;
    transition: transform 0.2s, box-shadow 0.2s;
  }
  .chip:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 16px rgba(167,139,250,0.2);
  }
  @keyframes chip-in {
    from { opacity: 0; transform: translateY(8px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .chip:nth-child(1) { animation-delay: 0.05s; }
  .chip:nth-child(2) { animation-delay: 0.1s; }
  .chip:nth-child(3) { animation-delay: 0.15s; }
  .chip:nth-child(4) { animation-delay: 0.2s; }
  .chip:nth-child(5) { animation-delay: 0.25s; }
  .chip:nth-child(6) { animation-delay: 0.3s; }
  .chip:nth-child(7) { animation-delay: 0.35s; }

  /* Social links */
  .socials {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
  }
  .social-link {
    display: inline-flex;
    align-items: center;
    gap: 7px;
    padding: 8px 16px;
    border-radius: 8px;
    border: 1px solid var(--border);
    background: var(--bg2);
    color: var(--text-muted);
    font-size: 13px;
    font-weight: 500;
    text-decoration: none;
    transition: all 0.2s;
    letter-spacing: 0.01em;
  }
  .social-link:hover {
    border-color: var(--violet-border);
    color: var(--violet);
    background: var(--violet-glow);
    transform: translateY(-1px);
  }
  .social-link svg { flex-shrink: 0; }

  /* ── SECTION ── */
  .section {
    max-width: 860px;
    margin: 0 auto;
    padding: 0 24px 48px;
  }

  .section-label {
    font-family: var(--font-code);
    font-size: 11px;
    color: var(--violet);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-bottom: 6px;
  }

  .section-title {
    font-size: 22px;
    font-weight: 600;
    color: var(--text);
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--violet-border), transparent);
  }

  /* ── ABOUT CARD ── */
  .about-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 24px;
    font-family: var(--font-code);
    font-size: 14px;
    line-height: 2;
    position: relative;
    overflow: hidden;
  }
  .about-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px; height: 100%;
    background: linear-gradient(180deg, var(--violet), var(--indigo));
    border-radius: 3px 0 0 3px;
  }
  .about-card .key { color: var(--indigo); }
  .about-card .val { color: var(--text); }
  .about-card .str { color: #a5f3fc; }
  .about-card .brace { color: var(--text-muted); }
  .about-card .cmt { color: var(--text-dim); }

  /* ── STACK GRID ── */
  .stack-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
    gap: 12px;
  }
  .stack-item {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 14px 10px;
    text-align: center;
    transition: all 0.2s;
    cursor: default;
  }
  .stack-item:hover {
    border-color: var(--violet-border);
    background: var(--violet-glow);
    transform: translateY(-3px);
    box-shadow: 0 8px 24px rgba(167,139,250,0.12);
  }
  .stack-icon {
    width: 36px; height: 36px;
    margin: 0 auto 8px;
    display: flex; align-items: center; justify-content: center;
  }
  .stack-icon img { width: 100%; height: 100%; object-fit: contain; }
  .stack-name {
    font-size: 11px;
    font-weight: 500;
    color: var(--text-muted);
    letter-spacing: 0.02em;
  }

  /* ── STATS GRID ── */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 12px;
    margin-bottom: 20px;
  }
  .stat-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    overflow: hidden;
  }
  .stat-card img {
    width: 100%;
    display: block;
    border-radius: var(--radius);
  }

  .stat-wide {
    grid-column: 1 / -1;
  }

  /* ── DIVIDER ── */
  .divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--violet-border) 40%, var(--violet-border) 60%, transparent);
    margin: 0 24px 48px;
    max-width: 860px;
    margin-left: auto;
    margin-right: auto;
  }

  /* ── FOOTER ── */
  .footer {
    text-align: center;
    padding: 32px 24px 48px;
    font-size: 13px;
    color: var(--text-dim);
    font-family: var(--font-code);
  }
  .footer span { color: var(--violet); }

  /* ── VIEWS BADGE ── */
  .meta-badges {
    display: flex;
    gap: 10px;
    justify-content: center;
    flex-wrap: wrap;
    margin-bottom: 28px;
  }
  .meta-badge {
    font-family: var(--font-code);
    font-size: 12px;
    padding: 5px 14px;
    border-radius: 6px;
    background: var(--bg3);
    border: 1px solid var(--border);
    color: var(--text-muted);
    display: inline-flex;
    align-items: center;
    gap: 6px;
  }
  .meta-badge .dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--violet);
  }
</style>
</head>
<body>

<!-- ══ HERO ══ -->
<section class="hero">
  <div class="grid-bg"></div>

  <!-- Floating Phone -->
  <div class="phone-frame">
    <svg viewBox="0 0 120 200" fill="none" xmlns="http://www.w3.org/2000/svg">
      <rect x="4" y="4" width="112" height="192" rx="18" fill="#161b22" stroke="rgba(167,139,250,0.4)" stroke-width="1.5"/>
      <rect x="8" y="8" width="104" height="184" rx="15" fill="#0d1117"/>
      <!-- notch -->
      <rect x="42" y="12" width="36" height="8" rx="4" fill="#161b22"/>
      <!-- screen content lines -->
      <rect x="18" y="36" width="30" height="6" rx="3" fill="rgba(167,139,250,0.5)"/>
      <rect x="18" y="48" width="50" height="4" rx="2" fill="rgba(255,255,255,0.1)"/>
      <rect x="18" y="57" width="40" height="4" rx="2" fill="rgba(255,255,255,0.07)"/>
      <!-- app icon grid -->
      <rect x="18" y="74" width="20" height="20" rx="6" fill="rgba(124,58,237,0.6)"/>
      <rect x="44" y="74" width="20" height="20" rx="6" fill="rgba(129,140,248,0.5)"/>
      <rect x="70" y="74" width="20" height="20" rx="6" fill="rgba(34,197,94,0.4)"/>
      <rect x="18" y="100" width="20" height="20" rx="6" fill="rgba(249,115,22,0.4)"/>
      <rect x="44" y="100" width="20" height="20" rx="6" fill="rgba(167,139,250,0.4)"/>
      <rect x="70" y="100" width="20" height="20" rx="6" fill="rgba(96,165,250,0.4)"/>
      <!-- bottom bar -->
      <rect x="42" y="186" width="36" height="4" rx="2" fill="rgba(255,255,255,0.15)"/>
      <!-- glow -->
      <ellipse cx="60" cy="100" rx="50" ry="60" fill="rgba(124,58,237,0.05)"/>
    </svg>
  </div>

  <div class="badge-status">
    <span class="status-dot"></span>available for collaboration
  </div>

  <h1 class="hero-name">Krish Vekriya</h1>

  <p class="hero-title">Flutter &amp; Android App Developer</p>
  <p class="hero-studio">Founder @ <span>Setubandh Tech</span> &nbsp;·&nbsp; Surat, India</p>

  <div class="meta-badges">
    <span class="meta-badge"><span class="dot"></span>Profile Views: 1.2K+</span>
    <span class="meta-badge"><span class="dot"></span>Play Store Publisher</span>
    <span class="meta-badge"><span class="dot"></span>Open Source</span>
  </div>

  <div class="chips">
    <span class="chip">📱 Flutter</span>
    <span class="chip">🎯 Dart</span>
    <span class="chip">⚡ Kotlin</span>
    <span class="chip">☕ Java</span>
    <span class="chip">🔥 Firebase</span>
    <span class="chip">🗄️ SQLite</span>
    <span class="chip">🚀 Play Store</span>
  </div>

  <div class="socials">
    <a class="social-link" href="https://krishvekriya12.github.io" target="_blank">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>
      Portfolio
    </a>
    <a class="social-link" href="https://www.linkedin.com/in/krish-vekriya-aa7a72311/" target="_blank">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
      LinkedIn
    </a>
    <a class="social-link" href="https://play.google.com/store/apps/dev?id=7084161944711464301" target="_blank">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M3 20.5v-17c0-.83 1-.83 1.5-.5l15 8.5-15 8.5c-.5.33-1.5.33-1.5-.5z"/></svg>
      Play Store
    </a>
    <a class="social-link" href="https://www.instagram.com/krish_.1240/" target="_blank">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"/><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"/><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"/></svg>
      Instagram
    </a>
    <a class="social-link" href="https://x.com/VekriyaKri81240" target="_blank">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
      X / Twitter
    </a>
    <a class="social-link" href="mailto:krishvekriya44@gmail.com">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
      Gmail
    </a>
    <a class="social-link" href="https://www.reddit.com/user/Rare_Oven_8888/" target="_blank">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><circle cx="12" cy="12" r="10"/><path fill="#0d1117" d="M6.5 10.5c-.8 0-1.5.7-1.5 1.5s.7 1.5 1.5 1.5 1.5-.7 1.5-1.5-.7-1.5-1.5-1.5zm11 0c-.8 0-1.5.7-1.5 1.5s.7 1.5 1.5 1.5 1.5-.7 1.5-1.5-.7-1.5-1.5-1.5zM12 8c-2.2 0-4.3.6-5.8 1.6-.3-.3-.7-.4-1.2-.4-1.1 0-2 .9-2 2 0 .7.4 1.4 1 1.7 0 .2.1.4.1.6 0 2.8 3.1 5 7 5s7-2.2 7-5c0-.2 0-.4.1-.6.6-.3 1-.9 1-1.7 0-1.1-.9-2-2-2-.4 0-.8.1-1.2.4C16.3 8.6 14.2 8 12 8zm-2 5.5c-.6 0-1-.4-1-1s.4-1 1-1 1 .4 1 1-.4 1-1 1zm4 0c-.6 0-1-.4-1-1s.4-1 1-1 1 .4 1 1-.4 1-1 1zm-4 2h4c.3 0 .5.2.5.5s-.2.5-.5.5h-4c-.3 0-.5-.2-.5-.5s.2-.5.5-.5zM19 7c0 1.1-.9 2-2 2s-2-.9-2-2 .9-2 2-2 2 .9 2 2zm-1 0c0-.6-.4-1-1-1s-1 .4-1 1 .4 1 1 1 1-.4 1-1z"/></svg>
      Reddit
    </a>
  </div>
</section>

<!-- ══ ABOUT ══ -->
<section class="section">
  <p class="section-label">// who i am</p>
  <h2 class="section-title">About Me</h2>
  <div class="about-card">
    <span class="brace">{</span><br/>
    &nbsp;&nbsp;<span class="key">"name"</span><span class="brace">:</span> <span class="str">"Krish Vekriya"</span><span class="brace">,</span><br/>
    &nbsp;&nbsp;<span class="key">"location"</span><span class="brace">:</span> <span class="str">"Surat, India 🇮🇳"</span><span class="brace">,</span><br/>
    &nbsp;&nbsp;<span class="key">"role"</span><span class="brace">:</span> <span class="str">"Flutter & Android App Developer"</span><span class="brace">,</span><br/>
    &nbsp;&nbsp;<span class="key">"studio"</span><span class="brace">:</span> <span class="str">"Setubandh Tech (Founder)"</span><span class="brace">,</span><br/>
    &nbsp;&nbsp;<span class="key">"portfolio"</span><span class="brace">:</span> <span class="str">"krishvekriya12.github.io"</span><span class="brace">,</span><br/>
    &nbsp;&nbsp;<span class="key">"focus"</span><span class="brace">:</span> <span class="brace">[</span><br/>
    &nbsp;&nbsp;&nbsp;&nbsp;<span class="str">"Shipping real apps to the Play Store 🚀"</span><span class="brace">,</span><br/>
    &nbsp;&nbsp;&nbsp;&nbsp;<span class="str">"Clean architecture & smooth UX 📱"</span><span class="brace">,</span><br/>
    &nbsp;&nbsp;&nbsp;&nbsp;<span class="str">"Building products that solve real problems 💡"</span><br/>
    &nbsp;&nbsp;<span class="brace">]</span><br/>
    <span class="brace">}</span>
  </div>
</section>

<div class="divider"></div>

<!-- ══ STACK ══ -->
<section class="section">
  <p class="section-label">// what i build with</p>
  <h2 class="section-title">Tech Stack</h2>
  <div class="stack-grid">

    <div class="stack-item">
      <div class="stack-icon">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/flutter/flutter-original.svg" alt="Flutter" onerror="this.style.display='none';this.parentNode.innerHTML='📱'"/>
      </div>
      <div class="stack-name">Flutter</div>
    </div>

    <div class="stack-item">
      <div class="stack-icon">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/dart/dart-original.svg" alt="Dart" onerror="this.style.display='none';this.parentNode.innerHTML='🎯'"/>
      </div>
      <div class="stack-name">Dart</div>
    </div>

    <div class="stack-item">
      <div class="stack-icon">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/kotlin/kotlin-original.svg" alt="Kotlin" onerror="this.style.display='none';this.parentNode.innerHTML='⚡'"/>
      </div>
      <div class="stack-name">Kotlin</div>
    </div>

    <div class="stack-item">
      <div class="stack-icon">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" alt="Java" onerror="this.style.display='none';this.parentNode.innerHTML='☕'"/>
      </div>
      <div class="stack-name">Java</div>
    </div>

    <div class="stack-item">
      <div class="stack-icon">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/firebase/firebase-plain.svg" alt="Firebase" onerror="this.style.display='none';this.parentNode.innerHTML='🔥'"/>
      </div>
      <div class="stack-name">Firebase</div>
    </div>

    <div class="stack-item">
      <div class="stack-icon">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/sqlite/sqlite-original.svg" alt="SQLite" onerror="this.style.display='none';this.parentNode.innerHTML='🗄️'"/>
      </div>
      <div class="stack-name">SQLite</div>
    </div>

    <div class="stack-item">
      <div class="stack-icon">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/androidstudio/androidstudio-original.svg" alt="Android Studio" onerror="this.style.display='none';this.parentNode.innerHTML='🤖'"/>
      </div>
      <div class="stack-name">Android Studio</div>
    </div>

    <div class="stack-item">
      <div class="stack-icon">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" alt="Git" onerror="this.style.display='none';this.parentNode.innerHTML='🌿'"/>
      </div>
      <div class="stack-name">Git</div>
    </div>

    <div class="stack-item">
      <div class="stack-icon">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" alt="GitHub" onerror="this.style.display='none';this.parentNode.innerHTML='🐙'"/>
      </div>
      <div class="stack-name">GitHub</div>
    </div>

    <div class="stack-item">
      <div class="stack-icon">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/gradle/gradle-plain.svg" alt="Gradle" onerror="this.style.display='none';this.parentNode.innerHTML='🔧'"/>
      </div>
      <div class="stack-name">Gradle</div>
    </div>

  </div>
</section>

<div class="divider"></div>

<!-- ══ STATS ══ -->
<section class="section">
  <p class="section-label">// by the numbers</p>
  <h2 class="section-title">GitHub Stats</h2>

  <div class="stats-grid">
    <div class="stat-card">
      <img src="https://github-readme-stats.vercel.app/api?username=krishvekriya12&show_icons=true&theme=radical&hide_border=true&bg_color=161b22&title_color=a78bfa&icon_color=a78bfa&text_color=c9d1d9&count_private=true&border_radius=12" alt="GitHub Stats"/>
    </div>
    <div class="stat-card">
      <img src="https://github-readme-streak-stats.herokuapp.com/?user=krishvekriya12&theme=radical&hide_border=true&background=161b22&ring=a78bfa&fire=a78bfa&currStreakLabel=a78bfa&border_radius=12" alt="GitHub Streak"/>
    </div>
    <div class="stat-card stat-wide">
      <img src="https://github-readme-activity-graph.vercel.app/graph?username=krishvekriya12&theme=react-dark&hide_border=true&bg_color=161b22&color=a78bfa&line=a78bfa&point=ffffff&border_radius=12" alt="Activity Graph"/>
    </div>
  </div>
</section>

<!-- ══ FOOTER ══ -->
<footer class="footer">
  <p>crafted with <span>♥</span> by Krish &nbsp;·&nbsp; Setubandh Tech &nbsp;·&nbsp; Surat, India</p>
  <p style="margin-top:6px; color: rgba(130,139,150,0.5); font-size: 11px;">// ships code, not promises</p>
</footer>

</body>
</html>
