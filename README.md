<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>HMS Enterprise — README</title>
<link href="https://fonts.googleapis.com/css2?family=Geist:wght@300;400;500;600;700;800;900&family=Geist+Mono:wght@400;500;700&display=swap" rel="stylesheet">
<style>
  :root {
    --bg:        #0d1117;
    --bg2:       #161b22;
    --bg3:       #21262d;
    --border:    rgba(48,54,61,1);
    --border-hi: rgba(99,110,123,0.6);
    --text:      #e6edf3;
    --text2:     #8b949e;
    --text3:     #6e7681;
    --blue:      #58a6ff;
    --green:     #3fb950;
    --orange:    #d29922;
    --red:       #f85149;
    --purple:    #bc8cff;
    --teal:      #39d353;
    --accent:    #007aff;
    --font:      'Geist', -apple-system, sans-serif;
    --mono:      'Geist Mono', 'SF Mono', monospace;
    --r:         8px;
    --ease:      cubic-bezier(0.16,1,0.3,1);
  }

  * { box-sizing:border-box; margin:0; padding:0; }

  body {
    font-family: var(--font);
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    line-height: 1.7;
  }

  /* ── LAYOUT ── */
  .page { max-width: 900px; margin: 0 auto; padding: 40px 24px 100px; }

  /* ── HERO ── */
  .hero {
    text-align: center;
    padding: 56px 0 48px;
    border-bottom: 1px solid var(--border);
    margin-bottom: 44px;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse 60% 50% at 20% 50%, rgba(0,122,255,0.08) 0%, transparent 70%),
      radial-gradient(ellipse 50% 60% at 80% 30%, rgba(88,86,214,0.07) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero-icon { font-size: 72px; display: block; margin-bottom: 20px; filter: drop-shadow(0 8px 24px rgba(0,122,255,0.3)); animation: float 4s ease-in-out infinite; }
  @keyframes float { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-8px)} }

  .hero h1 {
    font-size: clamp(32px,5vw,52px);
    font-weight: 900;
    letter-spacing: -2.5px;
    background: linear-gradient(135deg, #e6edf3 0%, #8b949e 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    margin-bottom: 10px;
  }
  .hero-sub { color: var(--text2); font-size: 16px; font-weight: 400; margin-bottom: 28px; }

  /* ── BADGES ── */
  .badges { display: flex; flex-wrap: wrap; justify-content: center; gap: 8px; margin-bottom: 28px; }
  .badge {
    display: inline-flex; align-items: center; gap: 6px;
    padding: 5px 12px;
    border-radius: 99px;
    font-size: 11.5px; font-weight: 700;
    border: 1px solid;
    transition: transform 0.2s var(--ease), box-shadow 0.2s;
    cursor: default;
    animation: badgeIn 0.6s var(--ease) both;
  }
  .badge:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(0,0,0,0.3); }
  @keyframes badgeIn { from{opacity:0;transform:translateY(8px) scale(0.9)} to{opacity:1;transform:none} }

  .badge-blue   { background:rgba(0,122,255,0.12); border-color:rgba(0,122,255,0.3); color:#58a6ff; }
  .badge-green  { background:rgba(63,185,80,0.1);  border-color:rgba(63,185,80,0.3); color:#3fb950; }
  .badge-orange { background:rgba(210,153,34,0.1); border-color:rgba(210,153,34,0.3); color:#d29922; }
  .badge-purple { background:rgba(188,140,255,0.1);border-color:rgba(188,140,255,0.3);color:#bc8cff; }
  .badge-red    { background:rgba(248,81,73,0.1);  border-color:rgba(248,81,73,0.3); color:#f85149; }

  /* ── NAV TOC ── */
  .toc {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px 24px;
    margin-bottom: 44px;
  }
  .toc-title { font-size: 12px; font-weight: 800; text-transform: uppercase; letter-spacing: 1.5px; color: var(--text3); margin-bottom: 12px; }
  .toc-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 4px; }
  .toc-link {
    display: flex; align-items: center; gap: 8px;
    padding: 7px 10px; border-radius: 7px;
    font-size: 13.5px; color: var(--blue); text-decoration: none; font-weight: 500;
    transition: background 0.15s, color 0.15s;
  }
  .toc-link:hover { background: rgba(88,166,255,0.08); color: var(--text); }

  /* ── SECTIONS ── */
  .section { margin-bottom: 52px; }
  .section-heading {
    font-size: 22px; font-weight: 800; letter-spacing: -0.8px;
    color: var(--text);
    display: flex; align-items: center; gap: 10px;
    padding-bottom: 14px;
    border-bottom: 1px solid var(--border);
    margin-bottom: 24px;
    scroll-margin-top: 24px;
  }
  .section-heading .emoji { font-size: 22px; }

  p { color: var(--text2); font-size: 14.5px; margin-bottom: 14px; }
  strong { color: var(--text); }

  /* ── FEATURE GRID ── */
  .feature-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px,1fr)); gap: 14px; }
  .feature-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px; padding: 20px 22px;
    transition: border-color 0.25s, transform 0.3s var(--ease), box-shadow 0.3s;
    cursor: default;
  }
  .feature-card:hover {
    border-color: var(--border-hi);
    transform: translateY(-3px);
    box-shadow: 0 12px 40px rgba(0,0,0,0.3);
  }
  .feature-icon { font-size: 26px; margin-bottom: 10px; }
  .feature-title { font-size: 13.5px; font-weight: 700; color: var(--text); margin-bottom: 5px; }
  .feature-desc  { font-size: 12.5px; color: var(--text2); line-height: 1.6; margin:0; }

  /* ── CODE BLOCKS ── */
  .code-wrap {
    position: relative;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 10px;
    margin-bottom: 18px;
    overflow: hidden;
  }
  .code-header {
    display: flex; align-items: center; justify-content: space-between;
    padding: 10px 16px;
    background: var(--bg3);
    border-bottom: 1px solid var(--border);
    font-size: 11.5px; color: var(--text3); font-family: var(--mono);
  }
  .code-header .dots { display:flex; gap:6px; }
  .code-header .dots span { width:10px;height:10px;border-radius:50%; }
  .dot-r{background:#f85149} .dot-y{background:#d29922} .dot-g{background:#3fb950}
  pre {
    padding: 18px 20px;
    overflow-x: auto;
    font-family: var(--mono);
    font-size: 12.5px;
    line-height: 1.8;
    color: var(--text);
    margin: 0;
  }
  .copy-btn {
    background: var(--bg3);
    border: 1px solid var(--border);
    color: var(--text2);
    padding: 5px 12px;
    border-radius: 6px;
    font-size: 11px; font-weight: 600; font-family: var(--font);
    cursor: pointer;
    transition: all 0.2s;
    display: flex; align-items: center; gap: 5px;
  }
  .copy-btn:hover { background: rgba(88,166,255,0.1); border-color: var(--blue); color: var(--blue); }
  .copy-btn.copied { background: rgba(63,185,80,0.1); border-color: var(--green); color: var(--green); }

  /* syntax */
  .c-k { color: #ff7b72; }  /* keyword */
  .c-s { color: #a5d6ff; }  /* string */
  .c-c { color: #8b949e; font-style:italic; }  /* comment */
  .c-f { color: #d2a8ff; }  /* function */
  .c-n { color: #ffa657; }  /* number/const */
  .c-p { color: #79c0ff; }  /* property */

  /* ── CREDENTIALS TABLE ── */
  .cred-table {
    width: 100%; border-collapse: collapse;
    font-size: 13.5px; margin-bottom: 18px;
  }
  .cred-table th {
    background: var(--bg3); color: var(--text2);
    font-size: 10px; font-weight: 800; text-transform: uppercase; letter-spacing: 1.5px;
    padding: 10px 16px; text-align: left; border-bottom: 1px solid var(--border);
  }
  .cred-table td {
    padding: 12px 16px; border-bottom: 1px solid var(--border);
    color: var(--text2);
  }
  .cred-table tr:last-child td { border-bottom: none; }
  .cred-table tr:hover td { background: rgba(255,255,255,0.02); }
  .cred-table code { font-family: var(--mono); background: var(--bg3); padding: 2px 7px; border-radius: 4px; font-size: 12px; color: var(--orange); }

  .role-pill {
    display: inline-block; padding: 2px 9px; border-radius: 99px;
    font-size: 10.5px; font-weight: 700;
  }
  .role-admin  { background:rgba(248,81,73,0.12);  color:#f85149; }
  .role-doctor { background:rgba(0,122,255,0.12);  color:#58a6ff; }
  .role-pharm  { background:rgba(63,185,80,0.12);  color:#3fb950; }
  .role-user   { background:rgba(139,148,158,0.15);color:#8b949e; }

  /* ── ACCORDION ── */
  .accordion { border: 1px solid var(--border); border-radius: 10px; overflow: hidden; margin-bottom: 12px; }
  .accordion-head {
    display: flex; align-items: center; justify-content: space-between;
    padding: 15px 18px;
    background: var(--bg2);
    cursor: pointer;
    font-size: 14px; font-weight: 600; color: var(--text);
    transition: background 0.2s;
    user-select: none;
  }
  .accordion-head:hover { background: var(--bg3); }
  .accordion-arrow { transition: transform 0.35s var(--ease); font-size: 12px; color: var(--text3); }
  .accordion.open .accordion-arrow { transform: rotate(180deg); }
  .accordion-body {
    max-height: 0; overflow: hidden;
    transition: max-height 0.45s var(--ease), padding 0.3s;
    background: var(--bg);
    border-top: 0px solid var(--border);
    font-size: 13.5px; color: var(--text2); line-height: 1.75;
  }
  .accordion.open .accordion-body { max-height: 600px; border-top-width: 1px; }
  .accordion-body-inner { padding: 18px 20px; }

  /* ── TECH STACK ── */
  .stack-grid { display: flex; flex-wrap: wrap; gap: 10px; }
  .stack-chip {
    display: inline-flex; align-items: center; gap: 7px;
    padding: 7px 14px;
    background: var(--bg2); border: 1px solid var(--border); border-radius: 8px;
    font-size: 12.5px; font-weight: 600; color: var(--text);
    transition: border-color 0.2s, transform 0.2s var(--ease);
    cursor: default;
  }
  .stack-chip:hover { border-color: var(--border-hi); transform: translateY(-2px); }

  /* ── WORKFLOW ── */
  .workflow {
    display: flex; align-items: center; gap: 0;
    flex-wrap: wrap; margin-bottom: 18px;
  }
  .wf-step {
    background: var(--bg2); border: 1px solid var(--border);
    border-radius: 10px; padding: 14px 18px;
    font-size: 13px; font-weight: 600;
    display: flex; align-items: center; gap: 9px;
    transition: border-color 0.2s, transform 0.2s var(--ease);
  }
  .wf-step:hover { border-color: var(--blue); transform: scale(1.03); }
  .wf-arrow { color: var(--text3); font-size: 18px; padding: 0 4px; }

  /* ── PERMISSION MATRIX ── */
  .perm-table { width:100%; border-collapse:collapse; font-size:13px; }
  .perm-table th, .perm-table td { padding:10px 14px; border:1px solid var(--border); text-align:center; }
  .perm-table th { background:var(--bg3); color:var(--text2); font-size:10px; text-transform:uppercase; letter-spacing:1px; }
  .perm-table td:first-child { text-align:left; font-weight:600; color:var(--text); }
  .perm-yes { color: var(--green); font-size:15px; }
  .perm-no  { color: var(--border-hi); font-size:15px; }

  /* ── CALLOUT ── */
  .callout {
    display: flex; gap: 14px; align-items: flex-start;
    padding: 16px 18px;
    border-radius: 10px; margin-bottom: 18px;
    font-size: 13.5px; line-height: 1.65;
  }
  .callout-icon { font-size: 18px; flex-shrink:0; margin-top:1px; }
  .callout-info   { background:rgba(88,166,255,0.07); border:1px solid rgba(88,166,255,0.18); }
  .callout-warn   { background:rgba(210,153,34,0.07); border:1px solid rgba(210,153,34,0.2); }
  .callout-tip    { background:rgba(63,185,80,0.07);  border:1px solid rgba(63,185,80,0.2); }

  /* ── FOOTER ── */
  .footer {
    border-top: 1px solid var(--border);
    padding-top: 32px;
    text-align: center; color: var(--text3); font-size: 12.5px;
  }
  .footer a { color: var(--blue); text-decoration: none; }
  .footer a:hover { text-decoration: underline; }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: transparent; }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 99px; }

  /* ── STAGGER ANIMATIONS ── */
  .fade-in { animation: fadeUp 0.6s var(--ease) both; }
  @keyframes fadeUp { from{opacity:0;transform:translateY(16px)} to{opacity:1;transform:none} }
  .delay-1{animation-delay:0.05s} .delay-2{animation-delay:0.1s} .delay-3{animation-delay:0.15s}
  .delay-4{animation-delay:0.2s}  .delay-5{animation-delay:0.25s} .delay-6{animation-delay:0.3s}
</style>
</head>
<body>
<div class="page">

  <!-- ══ HERO ══ -->
  <div class="hero fade-in">
    <span class="hero-icon">🏥</span>
    <h1>HMS Enterprise</h1>
    <p class="hero-sub">Hospital Management System · iOS 26 Liquid Glass Edition · v26.0.3</p>

    <div class="badges">
      <span class="badge badge-blue" style="animation-delay:0.1s">🔢 v26.0.3</span>
      <span class="badge badge-green" style="animation-delay:0.15s">✅ Zero Dependencies</span>
      <span class="badge badge-purple" style="animation-delay:0.2s">🍎 iOS 26 Design</span>
      <span class="badge badge-orange" style="animation-delay:0.25s">⚡ Vanilla JS</span>
      <span class="badge badge-red" style="animation-delay:0.3s">🔒 Role-Based Auth</span>
      <span class="badge badge-blue" style="animation-delay:0.35s">📱 Responsive</span>
    </div>

    <div class="callout callout-tip" style="max-width:560px;margin:0 auto;text-align:left;">
      <span class="callout-icon">💡</span>
      <span><strong>Single-file app.</strong> Drop <code style="font-family:var(--mono);background:var(--bg3);padding:1px 6px;border-radius:4px;color:var(--orange)">hms_ios26.html</code> anywhere and open it — no server, no install, no build step needed.</span>
    </div>
  </div>

  <!-- ══ TABLE OF CONTENTS ══ -->
  <div class="toc fade-in delay-1">
    <div class="toc-title">📋 Table of Contents</div>
    <div class="toc-grid">
      <a href="#overview"    class="toc-link">🌟 Overview</a>
      <a href="#features"    class="toc-link">✨ Features</a>
      <a href="#design"      class="toc-link">🍎 iOS 26 Design</a>
      <a href="#quickstart"  class="toc-link">🚀 Quick Start</a>
      <a href="#credentials" class="toc-link">🔑 Credentials</a>
      <a href="#roles"       class="toc-link">👥 Role Matrix</a>
      <a href="#workflow"    class="toc-link">🔄 Workflow</a>
      <a href="#modules"     class="toc-link">📦 Modules</a>
      <a href="#tech"        class="toc-link">🛠️ Tech Stack</a>
      <a href="#structure"   class="toc-link">🗂️ File Structure</a>
      <a href="#faq"         class="toc-link">❓ FAQ</a>
    </div>
  </div>


  <!-- ══ OVERVIEW ══ -->
  <div class="section fade-in delay-2" id="overview">
    <h2 class="section-heading"><span class="emoji">🌟</span> Overview</h2>
    <p>
      <strong>HMS Enterprise</strong> is a fully self-contained, single-file hospital management system built with pure HTML, CSS, and vanilla JavaScript.
      It handles the complete clinical lifecycle — from patient admission to final billing — across four distinct user roles with real-time permission enforcement.
    </p>
    <p>
      The v26.0 edition is a complete visual overhaul inspired by <strong>Apple's iOS 26 Liquid Glass</strong> design language, featuring authentic SVG-based refraction filters,
      specular rim highlights, physics-based spring animations, and a multi-layer glass material system — all running at 60fps with zero external dependencies beyond Chart.js.
    </p>

    <div class="callout callout-info">
      <span class="callout-icon">ℹ️</span>
      <span>All data is persisted in <strong>localStorage</strong>. This means your patients, staff, and fiscal data survive browser refreshes automatically — no backend required.</span>
    </div>
  </div>


  <!-- ══ FEATURES ══ -->
  <div class="section fade-in" id="features">
    <h2 class="section-heading"><span class="emoji">✨</span> Features</h2>
    <div class="feature-grid">
      <div class="feature-card">
        <div class="feature-icon">🔐</div>
        <div class="feature-title">Role-Based Authentication</div>
        <p class="feature-desc">4 login roles with granular nav permissions. Each role sees only its authorized modules.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🛌</div>
        <div class="feature-title">Clinical Intake Engine</div>
        <p class="feature-desc">Full patient admission with in-patient, OPD, and emergency trauma pathways. AI symptom sector suggestion.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🩺</div>
        <div class="feature-title">Prescription Workflow</div>
        <p class="feature-desc">Doctor prescribes → Pharmacist views pending → Dispenses and auto-bills to patient account.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🔬</div>
        <div class="feature-title">Laboratory Suite</div>
        <p class="feature-desc">Issue diagnostic tests with live cost tracking. Hematology, Neural MRI, and Genomic Sequencing.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">💰</div>
        <div class="feature-title">Revenue & GST Ledger</div>
        <p class="feature-desc">Real-time gross revenue, staff commissions, and 18% GST liability calculation with fiscal wipe.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🧾</div>
        <div class="feature-title">Auto Invoice Generation</div>
        <p class="feature-desc">Final settlement generates a printable fiscal receipt with itemized ward, diagnostic, and medicine costs.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">👨‍⚕️</div>
        <div class="feature-title">HR Personnel Registry</div>
        <p class="feature-desc">Onboard staff with specialty, salary, shift pattern, and consultation fee. Track earnings per doctor.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🤖</div>
        <div class="feature-title">AI Symptom Analyzer</div>
        <p class="feature-desc">Keyword-matching recommendation engine that suggests the correct hospital sector as you type symptoms.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">📊</div>
        <div class="feature-title">Admin Dashboard</div>
        <p class="feature-desc">Live patient count, revenue tracking, Chart.js revenue graph, and a full security audit trail.</p>
      </div>
    </div>
  </div>


  <!-- ══ iOS 26 DESIGN ══ -->
  <div class="section fade-in" id="design">
    <h2 class="section-heading"><span class="emoji">🍎</span> iOS 26 Liquid Glass Design</h2>
    <p>Every visual component is built using Apple's 4-layer glass material system from iOS 26:</p>

    <div class="code-wrap">
      <div class="code-header">
        <div class="dots"><span class="dot-r"></span><span class="dot-y"></span><span class="dot-g"></span></div>
        <span>glass-material-layers.css</span>
        <button class="copy-btn" onclick="copyCode(this)">📋 Copy</button>
      </div>
      <pre><span class="c-c">/* Layer 1 — Blur + Refraction (SVG feDisplacementMap) */</span>
<span class="c-p">::before</span> { backdrop-filter: <span class="c-s">saturate(180%) blur(28px)</span>; filter: <span class="c-s">url(#lg-refract)</span>; }

<span class="c-c">/* Layer 2 — Translucent tint */</span>
<span class="c-p">::after</span>  { background: <span class="c-s">rgba(255,255,255,0.18)</span>; }

<span class="c-c">/* Layer 3 — Specular rim (top-left light catch) */</span>
<span class="c-p">.glass-shine</span> { box-shadow: inset <span class="c-n">1.5px 1.5px 0</span> <span class="c-s">rgba(255,255,255,0.8)</span>; }

<span class="c-c">/* Layer 4 — Content (always on top, z-index: 3) */</span></pre>
    </div>

    <div class="feature-grid" style="margin-top:18px;">
      <div class="feature-card">
        <div class="feature-icon">🔭</div>
        <div class="feature-title">SVG feDisplacementMap</div>
        <p class="feature-desc">Physically accurate background refraction at glass edges using turbulence noise + displacement maps.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">💡</div>
        <div class="feature-title">feSpecularLighting</div>
        <p class="feature-desc">Point-light specular highlights that simulate real glass surface reflections.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🌊</div>
        <div class="feature-title">Liquid Nav Blob</div>
        <p class="feature-desc">The active nav indicator morphs between items using cubic-bezier(0.7,0,0.3,1) — a true liquid motion curve.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🖱️</div>
        <div class="feature-title">Mouse-Driven Light</div>
        <p class="feature-desc">Glass panels track cursor position and update their specular highlight in real time.</p>
      </div>
    </div>
  </div>


  <!-- ══ QUICK START ══ -->
  <div class="section fade-in" id="quickstart">
    <h2 class="section-heading"><span class="emoji">🚀</span> Quick Start</h2>

    <p><strong>Option 1 — Direct open (recommended)</strong></p>
    <div class="code-wrap">
      <div class="code-header">
        <div class="dots"><span class="dot-r"></span><span class="dot-y"></span><span class="dot-g"></span></div>
        <span>terminal</span>
        <button class="copy-btn" onclick="copyCode(this)">📋 Copy</button>
      </div>
      <pre><span class="c-c"># Just open the file in your browser — no server needed</span>
open hms_ios26.html

<span class="c-c"># Or on Windows</span>
start hms_ios26.html</pre>
    </div>

    <p><strong>Option 2 — Serve locally (for full backdrop-filter support)</strong></p>
    <div class="code-wrap">
      <div class="code-header">
        <div class="dots"><span class="dot-r"></span><span class="dot-y"></span><span class="dot-g"></span></div>
        <span>terminal</span>
        <button class="copy-btn" onclick="copyCode(this)">📋 Copy</button>
      </div>
      <pre><span class="c-c"># Python 3</span>
python3 -m http.server <span class="c-n">8080</span>

<span class="c-c"># Node (npx)</span>
npx serve .

<span class="c-c"># Then open</span>
open http://localhost:<span class="c-n">8080</span>/hms_ios26.html</pre>
    </div>

    <div class="callout callout-warn">
      <span class="callout-icon">⚠️</span>
      <span><strong>backdrop-filter</strong> requires a secure context or localhost in some browsers. For full glass effects, use Option 2 or deploy to HTTPS.</span>
    </div>

    <p><strong>Option 3 — Deploy to GitHub Pages</strong></p>
    <div class="code-wrap">
      <div class="code-header">
        <div class="dots"><span class="dot-r"></span><span class="dot-y"></span><span class="dot-g"></span></div>
        <span>terminal</span>
        <button class="copy-btn" onclick="copyCode(this)">📋 Copy</button>
      </div>
      <pre>git init
git add hms_ios26.html README.md
git commit -m <span class="c-s">"🏥 Initial HMS Enterprise v26.0"</span>
git branch -M main
git remote add origin https://github.com/<span class="c-n">YOUR_USER</span>/<span class="c-n">hms-enterprise</span>.git
git push -u origin main
<span class="c-c"># Then enable GitHub Pages → Settings → Pages → Branch: main</span></pre>
    </div>
  </div>


  <!-- ══ CREDENTIALS ══ -->
  <div class="section fade-in" id="credentials">
    <h2 class="section-heading"><span class="emoji">🔑</span> Login Credentials</h2>
    <p>Four built-in accounts cover every access tier. All credentials are hardcoded — update <code style="font-family:var(--mono);background:var(--bg3);padding:1px 6px;border-radius:4px;color:var(--orange)">SYS_CREDENTIALS</code> in the script to change them.</p>

    <table class="cred-table">
      <thead>
        <tr>
          <th>Role</th>
          <th>Username</th>
          <th>Password</th>
          <th>Access Level</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td><span class="role-pill role-admin">🔴 Admin</span></td>
          <td><code>admin</code></td>
          <td><code>admin</code></td>
          <td>Full system access — all 10 modules</td>
        </tr>
        <tr>
          <td><span class="role-pill role-doctor">🔵 Doctor</span></td>
          <td><code>doc</code></td>
          <td><code>123</code></td>
          <td>Clinical intake, prescriptions, lab, break room</td>
        </tr>
        <tr>
          <td><span class="role-pill role-pharm">🟢 Pharmacist</span></td>
          <td><code>pharm</code></td>
          <td><code>123</code></td>
          <td>Inventory dispensing, break room</td>
        </tr>
        <tr>
          <td><span class="role-pill role-user">⚪ Guest</span></td>
          <td><code>user</code></td>
          <td><code>0</code></td>
          <td>My Medical Bill, Specs, Gallery</td>
        </tr>
      </tbody>
    </table>
  </div>


  <!-- ══ ROLE MATRIX ══ -->
  <div class="section fade-in" id="roles">
    <h2 class="section-heading"><span class="emoji">👥</span> Permission Matrix</h2>
    <div style="overflow-x:auto;">
      <table class="perm-table">
        <thead>
          <tr>
            <th style="text-align:left">Module</th>
            <th>Admin</th>
            <th>Doctor</th>
            <th>Pharmacist</th>
            <th>Guest</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>📊 Dashboard Matrix</td><td><span class="perm-yes">✓</span></td><td><span class="perm-no">–</span></td><td><span class="perm-no">–</span></td><td><span class="perm-no">–</span></td></tr>
          <tr><td>👨‍⚕️ Human Resources</td><td><span class="perm-yes">✓</span></td><td><span class="perm-no">–</span></td><td><span class="perm-no">–</span></td><td><span class="perm-no">–</span></td></tr>
          <tr><td>🛌 Clinical Intake</td><td><span class="perm-yes">✓</span></td><td><span class="perm-yes">✓</span></td><td><span class="perm-no">–</span></td><td><span class="perm-no">–</span></td></tr>
          <tr><td>💊 Inventory / Pharmacy</td><td><span class="perm-yes">✓</span></td><td><span class="perm-no">–</span></td><td><span class="perm-yes">✓</span></td><td><span class="perm-no">–</span></td></tr>
          <tr><td>🔬 Laboratory</td><td><span class="perm-yes">✓</span></td><td><span class="perm-yes">✓</span></td><td><span class="perm-no">–</span></td><td><span class="perm-no">–</span></td></tr>
          <tr><td>💰 Revenue & GST</td><td><span class="perm-yes">✓</span></td><td><span class="perm-no">–</span></td><td><span class="perm-no">–</span></td><td><span class="perm-no">–</span></td></tr>
          <tr><td>🔍 My Medical Bill</td><td><span class="perm-yes">✓</span></td><td><span class="perm-yes">✓</span></td><td><span class="perm-yes">✓</span></td><td><span class="perm-yes">✓</span></td></tr>
          <tr><td>✨ Specifications</td><td><span class="perm-yes">✓</span></td><td><span class="perm-yes">✓</span></td><td><span class="perm-yes">✓</span></td><td><span class="perm-yes">✓</span></td></tr>
          <tr><td>🖼️ Facility Gallery</td><td><span class="perm-yes">✓</span></td><td><span class="perm-yes">✓</span></td><td><span class="perm-yes">✓</span></td><td><span class="perm-yes">✓</span></td></tr>
          <tr><td>🎮 Staff Break Room</td><td><span class="perm-yes">✓</span></td><td><span class="perm-yes">✓</span></td><td><span class="perm-yes">✓</span></td><td><span class="perm-no">–</span></td></tr>
        </tbody>
      </table>
    </div>
  </div>


  <!-- ══ WORKFLOW ══ -->
  <div class="section fade-in" id="workflow">
    <h2 class="section-heading"><span class="emoji">🔄</span> Clinical Workflow</h2>
    <p>The core loop follows a three-role handoff chain:</p>

    <div class="workflow">
      <div class="wf-step">🛌 <span><strong>Admin</strong><br><small style="color:var(--text3);font-weight:400">Admits patient</small></span></div>
      <div class="wf-arrow">→</div>
      <div class="wf-step">🩺 <span><strong>Doctor</strong><br><small style="color:var(--text3);font-weight:400">Prescribes meds</small></span></div>
      <div class="wf-arrow">→</div>
      <div class="wf-step">💊 <span><strong>Pharmacist</strong><br><small style="color:var(--text3);font-weight:400">Dispenses &amp; bills</small></span></div>
      <div class="wf-arrow">→</div>
      <div class="wf-step">🧾 <span><strong>Admin</strong><br><small style="color:var(--text3);font-weight:400">Final settlement</small></span></div>
    </div>

    <div class="code-wrap" style="margin-top:18px;">
      <div class="code-header">
        <div class="dots"><span class="dot-r"></span><span class="dot-y"></span><span class="dot-g"></span></div>
        <span>billing-formula.js</span>
        <button class="copy-btn" onclick="copyCode(this)">📋 Copy</button>
      </div>
      <pre><span class="c-k">function</span> <span class="c-f">calcBill</span>(patient) {
  <span class="c-k">const</span> days  = Math.<span class="c-f">ceil</span>((new <span class="c-f">Date</span>() - new <span class="c-f">Date</span>(patient.intakeDate)) / <span class="c-n">86400000</span>) || <span class="c-n">1</span>;
  <span class="c-k">const</span> ward  = patient.type === <span class="c-s">'checkup'</span> ? <span class="c-n">0</span> : (days * patient.roomPrice);
  <span class="c-k">const</span> sub   = ward + patient.labCost + patient.phaCost + patient.consultationFee;
  <span class="c-k">const</span> gst   = sub * <span class="c-n">0.18</span>;  <span class="c-c">// 18% GST</span>
  <span class="c-k">const</span> total = Math.<span class="c-f">max</span>(<span class="c-n">0</span>, sub + gst - patient.deposit);
  <span class="c-k">return</span> { subtotal: sub, tax: gst, total };
}</pre>
    </div>
  </div>


  <!-- ══ MODULES ══ -->
  <div class="section fade-in" id="modules">
    <h2 class="section-heading"><span class="emoji">📦</span> Module Reference</h2>

    <div class="accordion" onclick="toggleAccordion(this)">
      <div class="accordion-head">📊 Dashboard Matrix <span class="accordion-arrow">▼</span></div>
      <div class="accordion-body"><div class="accordion-body-inner">
        Live telemetry panel showing active patient count, outstanding revenue, a Chart.js line graph of hourly revenue flux, and a real-time security audit trail. Only accessible to <span class="role-pill role-admin">Admin</span>.
      </div></div>
    </div>

    <div class="accordion" onclick="toggleAccordion(this)">
      <div class="accordion-head">👨‍⚕️ Human Resources <span class="accordion-arrow">▼</span></div>
      <div class="accordion-body"><div class="accordion-body-inner">
        Add/remove staff with name, role (Specialist/Surgeon/Nurse/Pharmacist), specialty, salary, consultation fee, and shift. Doctors added here become selectable when admitting patients. Their 15% commission is calculated at patient discharge and added to their <code style="font-family:var(--mono)">earnings</code> field.
      </div></div>
    </div>

    <div class="accordion" onclick="toggleAccordion(this)">
      <div class="accordion-head">🛌 Clinical Intake <span class="accordion-arrow">▼</span></div>
      <div class="accordion-body"><div class="accordion-body-inner">
        Admit patients with type (In-Patient / OPD / Emergency), room class, doctor assignment, blood group, deposit, and diagnosis. The AI Symptom Analyzer parses the symptoms textarea in real time and suggests a hospital sector (e.g. "Cardiology Unit") using keyword matching. Doctors can also write prescriptions for active patients from this view.
      </div></div>
    </div>

    <div class="accordion" onclick="toggleAccordion(this)">
      <div class="accordion-head">💊 Inventory / Pharmacy <span class="accordion-arrow">▼</span></div>
      <div class="accordion-body"><div class="accordion-body-inner">
        Pharmacists select an active patient, view the pending doctor prescription, enter the compound price, and dispatch. The cost is appended to the patient's <code style="font-family:var(--mono)">phaCost</code> and the prescription is cleared. Every transaction logs to the Pharmacy Ledger Sync console.
      </div></div>
    </div>

    <div class="accordion" onclick="toggleAccordion(this)">
      <div class="accordion-head">🔬 Laboratory <span class="accordion-arrow">▼</span></div>
      <div class="accordion-body"><div class="accordion-body-inner">
        Issue diagnostic suites to patients: Hematology Core (₹2,800), Neural MRI Suite (₹24,000), or Full Genomic Sequencing (₹85,000). Each test adds to the patient's <code style="font-family:var(--mono)">labCost</code> and logs to the workflow queue.
      </div></div>
    </div>

    <div class="accordion" onclick="toggleAccordion(this)">
      <div class="accordion-head">💰 Revenue & GST <span class="accordion-arrow">▼</span></div>
      <div class="accordion-body"><div class="accordion-body-inner">
        A real-time ledger showing gross revenue collected, total staff commission payouts, and computed GST liability (18% of gross). The WIPE button clears all fiscal data. Revenue is updated on each patient discharge/settlement.
      </div></div>
    </div>

    <div class="accordion" onclick="toggleAccordion(this)">
      <div class="accordion-head">🔍 My Medical Bill <span class="accordion-arrow">▼</span></div>
      <div class="accordion-body"><div class="accordion-body-inner">
        Any role can search active patients by name to view their live outstanding balance. Admins see a FINAL SETTLEMENT button that discharges the patient, generates the invoice, and updates the fiscal ledger. Guest users see a read-only view with no settlement option.
      </div></div>
    </div>
  </div>


  <!-- ══ TECH STACK ══ -->
  <div class="section fade-in" id="tech">
    <h2 class="section-heading"><span class="emoji">🛠️</span> Tech Stack</h2>
    <div class="stack-grid">
      <div class="stack-chip">🌐 HTML5</div>
      <div class="stack-chip">🎨 CSS3 + Custom Properties</div>
      <div class="stack-chip">⚡ Vanilla JavaScript (ES6+)</div>
      <div class="stack-chip">📊 Chart.js 4.x</div>
      <div class="stack-chip">🔠 Geist Font (Vercel)</div>
      <div class="stack-chip">💾 localStorage API</div>
      <div class="stack-chip">🔭 SVG Filter Primitives</div>
      <div class="stack-chip">🍎 backdrop-filter CSS</div>
      <div class="stack-chip">🎮 Canvas API (Snake)</div>
      <div class="stack-chip">📱 CSS Grid + Flexbox</div>
    </div>

    <div class="callout callout-info" style="margin-top:20px;">
      <span class="callout-icon">ℹ️</span>
      <span>Only <strong>one external script</strong> is loaded: Chart.js from jsDelivr CDN. The Google Fonts stylesheet is optional — the app falls back to <code style="font-family:var(--mono);background:var(--bg3);padding:1px 6px;border-radius:4px">-apple-system</code> gracefully.</span>
    </div>
  </div>


  <!-- ══ FILE STRUCTURE ══ -->
  <div class="section fade-in" id="structure">
    <h2 class="section-heading"><span class="emoji">🗂️</span> File Structure</h2>
    <div class="code-wrap">
      <div class="code-header">
        <div class="dots"><span class="dot-r"></span><span class="dot-y"></span><span class="dot-g"></span></div>
        <span>repository</span>
        <button class="copy-btn" onclick="copyCode(this)">📋 Copy</button>
      </div>
      <pre>hms-enterprise/
├── <span class="c-p">hms_ios26.html</span>        <span class="c-c"># ← The entire app (single file)</span>
│   ├── &lt;style&gt;          <span class="c-c"># iOS 26 Liquid Glass CSS (~400 lines)</span>
│   ├── &lt;svg filters&gt;   <span class="c-c"># feDisplacementMap + feSpecularLighting</span>
│   ├── &lt;html&gt;           <span class="c-c"># Login, sidebar, 10 section panels</span>
│   └── &lt;script&gt;         <span class="c-c"># Core logic + state + Chart.js (~350 lines)</span>
│
└── <span class="c-p">README.md</span>             <span class="c-c"># This file</span></pre>
    </div>

    <p>The internal script is organized into clearly commented blocks:</p>
    <div class="code-wrap">
      <div class="code-header">
        <div class="dots"><span class="dot-r"></span><span class="dot-y"></span><span class="dot-g"></span></div>
        <span>script-architecture.js</span>
        <button class="copy-btn" onclick="copyCode(this)">📋 Copy</button>
      </div>
      <pre><span class="c-c">// ══ CORE STATE (ROSTER, PATIENTS, AUDIT, FISCAL) ══</span>
<span class="c-c">// ══ AUTH (runAuth, applyPermissions) ══</span>
<span class="c-c">// ══ NAV MORPHING (morphTo + liquid blob) ══</span>
<span class="c-c">// ══ THEME (toggleTheme) ══</span>
<span class="c-c">// ══ AI SYMPTOM ANALYZER (analyzeSymptoms) ══</span>
<span class="c-c">// ══ HR (onboardStaff, renderRoster, voidStaff) ══</span>
<span class="c-c">// ══ ADMISSIONS (admitPatient, renderPatients) ══</span>
<span class="c-c">// ══ PRESCRIPTIONS (addPrescription) ══</span>
<span class="c-c">// ══ PHARMACY (showPrescribed, dispenseMed) ══</span>
<span class="c-c">// ══ LAB (issueLab) ══</span>
<span class="c-c">// ══ BILLING (calcBill) ══</span>
<span class="c-c">// ══ FINANCE (updateFinance, wipeFiscal) ══</span>
<span class="c-c">// ══ SEARCH & SETTLE (runSearch, settle, renderInvoice) ══</span>
<span class="c-c">// ══ DASHBOARD (updateDashboard, audit) ══</span>
<span class="c-c">// ══ GALLERY (renderGallery) ══</span>
<span class="c-c">// ══ SAVE (localStorage persistence) ══</span>
<span class="c-c">// ══ SNAKE (initSnake) ══</span>
<span class="c-c">// ══ CHART (initChart — Chart.js) ══</span></pre>
    </div>
  </div>


  <!-- ══ FAQ ══ -->
  <div class="section fade-in" id="faq">
    <h2 class="section-heading"><span class="emoji">❓</span> FAQ</h2>

    <div class="accordion" onclick="toggleAccordion(this)">
      <div class="accordion-head">How do I reset all data? <span class="accordion-arrow">▼</span></div>
      <div class="accordion-body"><div class="accordion-body-inner">
        Open browser DevTools → Application → Local Storage → delete all <code style="font-family:var(--mono)">hms_v34_*</code> keys. Or run <code style="font-family:var(--mono)">Object.keys(localStorage).filter(k=>k.startsWith('hms')).forEach(k=>localStorage.removeItem(k))</code> in the console.
      </div></div>
    </div>

    <div class="accordion" onclick="toggleAccordion(this)">
      <div class="accordion-head">Why doesn't the glass blur show on file:// protocol? <span class="accordion-arrow">▼</span></div>
      <div class="accordion-body"><div class="accordion-body-inner">
        <code style="font-family:var(--mono)">backdrop-filter</code> is restricted on <code style="font-family:var(--mono)">file://</code> in Chromium-based browsers for security reasons. Serve the file via localhost (<code style="font-family:var(--mono)">python3 -m http.server</code>) or deploy to HTTPS to get full glass effects.
      </div></div>
    </div>

    <div class="accordion" onclick="toggleAccordion(this)">
      <div class="accordion-head">Can I add more user roles? <span class="accordion-arrow">▼</span></div>
      <div class="accordion-body"><div class="accordion-body-inner">
        Yes. Add an entry to <code style="font-family:var(--mono)">SYS_CREDENTIALS</code> with a new role string, then add a corresponding CSS class (e.g. <code style="font-family:var(--mono)">.ni-nurse</code>) to the nav items you want visible, and handle it in <code style="font-family:var(--mono)">applyPermissions()</code>.
      </div></div>
    </div>

    <div class="accordion" onclick="toggleAccordion(this)">
      <div class="accordion-head">How do I change room pricing? <span class="accordion-arrow">▼</span></div>
      <div class="accordion-body"><div class="accordion-body-inner">
        Update the <code style="font-family:var(--mono)">value</code> attributes on the <code style="font-family:var(--mono)">&lt;option&gt;</code> elements inside <code style="font-family:var(--mono)">#pRoom</code>. Values are per-day rates in Rupees (integers).
      </div></div>
    </div>

    <div class="accordion" onclick="toggleAccordion(this)">
      <div class="accordion-head">Is this production-ready? <span class="accordion-arrow">▼</span></div>
      <div class="accordion-body"><div class="accordion-body-inner">
        HMS Enterprise is a demonstration/prototype system. Credentials are hardcoded in plain JS, localStorage has no encryption, and there's no server-side validation. For production healthcare use, you'd need a proper backend, authentication service, encrypted database, and HIPAA/local compliance review.
      </div></div>
    </div>
  </div>


  <!-- ══ FOOTER ══ -->
  <div class="footer fade-in">
    <p style="margin-bottom:10px;">Built with ❤️ using pure HTML · CSS · JavaScript &nbsp;·&nbsp; iOS 26 Liquid Glass Design System</p>
    <p>No frameworks. No build tools. No dependencies (except Chart.js). <a href="#">Back to top ↑</a></p>
  </div>

</div>

<script>
  /* ── COPY BUTTONS ── */
  function copyCode(btn) {
    const pre = btn.closest('.code-wrap').querySelector('pre');
    // Strip HTML tags to get plain text
    const text = pre.innerText || pre.textContent;
    navigator.clipboard.writeText(text).then(() => {
      btn.classList.add('copied');
      btn.innerHTML = '✅ Copied!';
      setTimeout(() => { btn.classList.remove('copied'); btn.innerHTML = '📋 Copy'; }, 2000);
    }).catch(() => {
      // Fallback
      const ta = document.createElement('textarea');
      ta.value = text; document.body.appendChild(ta); ta.select();
      document.execCommand('copy'); document.body.removeChild(ta);
      btn.innerHTML = '✅ Copied!';
      setTimeout(() => btn.innerHTML = '📋 Copy', 2000);
    });
  }

  /* ── ACCORDIONS ── */
  function toggleAccordion(el) {
    const isOpen = el.classList.contains('open');
    // Close all
    document.querySelectorAll('.accordion.open').forEach(a => a.classList.remove('open'));
    // Open clicked if it was closed
    if (!isOpen) el.classList.add('open');
  }

  /* ── SMOOTH SCROLL ── */
  document.querySelectorAll('.toc-link').forEach(link => {
    link.addEventListener('click', e => {
      e.preventDefault();
      const target = document.querySelector(link.getAttribute('href'));
      if (target) target.scrollIntoView({ behavior: 'smooth', block: 'start' });
    });
  });

  /* ── INTERSECTION OBSERVER (reveal on scroll) ── */
  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.style.opacity = '1';
        entry.target.style.transform = 'none';
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.08 });

  document.querySelectorAll('.feature-card, .accordion, .stack-chip').forEach(el => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(14px)';
    el.style.transition = 'opacity 0.5s cubic-bezier(0.16,1,0.3,1), transform 0.5s cubic-bezier(0.16,1,0.3,1)';
    observer.observe(el);
  });

  /* ── BADGE STAGGER ── */
  document.querySelectorAll('.badge').forEach((b, i) => {
    b.style.animationDelay = (0.08 + i * 0.05) + 's';
  });

  /* ── BACK TO TOP ── */
  document.querySelector('.footer a').addEventListener('click', e => {
    e.preventDefault(); window.scrollTo({ top: 0, behavior: 'smooth' });
  });
</script>
</body>
</html>
