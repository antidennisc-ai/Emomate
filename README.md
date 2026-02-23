<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>情緒隊友 EmoMate — README</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,700;0,900;1,700&family=Noto+Serif+TC:wght@400;700;900&family=Noto+Sans+TC:wght@300;400;500&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #0d0a08;
  --bg2: #141009;
  --surface: #1c1510;
  --surface2: #231a13;
  --border: #2e2118;
  --rose: #e8614a;
  --rose-dim: rgba(232,97,74,.15);
  --amber: #f5a842;
  --amber-dim: rgba(245,168,66,.12);
  --mint: #3db88a;
  --mint-dim: rgba(61,184,138,.12);
  --text: #f0e8df;
  --text2: #9e8878;
  --text3: #5c4a3c;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  font-family: 'Noto Sans TC', sans-serif;
  background: var(--bg);
  color: var(--text);
  overflow-x: hidden;
  line-height: 1.6;
}

/* ── NOISE TEXTURE ── */
body::before {
  content: '';
  position: fixed; inset: 0; z-index: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='.03'/%3E%3C/svg%3E");
  pointer-events: none;
}

/* ── HERO ── */
.hero {
  position: relative;
  min-height: 100vh;
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  text-align: center;
  padding: 60px 24px;
  overflow: hidden;
}

.hero-glow {
  position: absolute;
  width: 700px; height: 700px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(232,97,74,.18) 0%, transparent 70%);
  top: 50%; left: 50%;
  transform: translate(-50%, -60%);
  pointer-events: none;
  animation: glowPulse 6s ease-in-out infinite;
}
.hero-glow2 {
  position: absolute;
  width: 400px; height: 400px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(245,168,66,.1) 0%, transparent 70%);
  bottom: 10%; right: 5%;
  pointer-events: none;
  animation: glowPulse 8s ease-in-out infinite reverse;
}

@keyframes glowPulse {
  0%,100% { transform: translate(-50%,-60%) scale(1); opacity: 1; }
  50% { transform: translate(-50%,-60%) scale(1.1); opacity: .7; }
}

.badge-top {
  display: inline-flex; align-items: center; gap: 8px;
  border: 1px solid var(--border);
  background: var(--surface);
  border-radius: 99px; padding: 6px 18px;
  font-size: .75rem; letter-spacing: .12em;
  text-transform: uppercase; color: var(--text2);
  margin-bottom: 32px;
  animation: fadeUp .8s ease both;
}
.badge-top .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--rose); animation: blink 2s infinite; }
@keyframes blink { 0%,100%{opacity:1} 50%{opacity:.3} }

.hero-title {
  font-family: 'Playfair Display', 'Noto Serif TC', serif;
  font-size: clamp(2.8rem, 8vw, 5.5rem);
  font-weight: 900;
  line-height: 1.1;
  letter-spacing: -.02em;
  animation: fadeUp .9s .1s ease both;
}
.hero-title .en { display: block; color: var(--rose); font-style: italic; }
.hero-title .zh { display: block; font-size: clamp(1.4rem, 4vw, 2.2rem); color: var(--text2); margin-top: 8px; font-weight: 400; letter-spacing: .04em; }

.hero-sub {
  max-width: 520px; margin: 28px auto 0;
  font-size: clamp(.9rem, 2.5vw, 1.05rem);
  color: var(--text2); line-height: 1.8;
  animation: fadeUp 1s .2s ease both;
}

.hero-cta {
  display: flex; gap: 14px; flex-wrap: wrap;
  justify-content: center; margin-top: 42px;
  animation: fadeUp 1s .35s ease both;
}

.btn-main {
  display: inline-flex; align-items: center; gap: 10px;
  padding: 14px 30px; border-radius: 12px; border: none;
  background: var(--rose); color: white;
  font-family: 'Noto Sans TC', sans-serif;
  font-size: .92rem; font-weight: 500; cursor: pointer;
  text-decoration: none;
  box-shadow: 0 0 40px rgba(232,97,74,.35);
  transition: all .25s;
}
.btn-main:hover { transform: translateY(-2px); box-shadow: 0 0 60px rgba(232,97,74,.5); }

.btn-sec {
  display: inline-flex; align-items: center; gap: 10px;
  padding: 14px 30px; border-radius: 12px;
  border: 1px solid var(--border);
  background: transparent; color: var(--text2);
  font-family: 'Noto Sans TC', sans-serif;
  font-size: .92rem; font-weight: 500; cursor: pointer;
  text-decoration: none;
  transition: all .25s;
}
.btn-sec:hover { border-color: var(--text2); color: var(--text); }

@keyframes fadeUp { from { opacity:0; transform: translateY(20px); } to { opacity:1; transform: translateY(0); } }

/* ── DIVIDER ── */
.section-divider {
  display: flex; align-items: center; gap: 16px;
  padding: 0 40px; margin: 0 auto 60px;
  max-width: 900px;
}
.section-divider::before, .section-divider::after {
  content: ''; flex: 1; height: 1px; background: var(--border);
}
.section-divider span {
  font-size: .7rem; letter-spacing: .2em;
  text-transform: uppercase; color: var(--text3);
  white-space: nowrap;
}

/* ── SECTIONS ── */
section { padding: 100px 24px; position: relative; z-index: 1; }

.section-label {
  font-size: .72rem; letter-spacing: .18em;
  text-transform: uppercase; color: var(--rose);
  margin-bottom: 14px; font-weight: 500;
}
.section-heading {
  font-family: 'Playfair Display', 'Noto Serif TC', serif;
  font-size: clamp(1.8rem, 5vw, 2.8rem);
  font-weight: 700; line-height: 1.2;
  margin-bottom: 20px;
}
.section-body {
  font-size: .95rem; color: var(--text2);
  line-height: 1.85; max-width: 560px;
}

/* ── PROBLEM ── */
.problem-section { background: var(--bg2); }
.problem-inner {
  max-width: 900px; margin: 0 auto;
  display: grid; grid-template-columns: 1fr 1fr; gap: 60px;
  align-items: center;
}
@media(max-width:680px) { .problem-inner { grid-template-columns: 1fr; gap: 40px; } }

.quote-stack { display: flex; flex-direction: column; gap: 14px; }
.quote-bubble {
  background: var(--surface2);
  border: 1px solid var(--border);
  border-radius: 16px 16px 16px 4px;
  padding: 16px 20px;
  font-size: .88rem; color: var(--text2); line-height: 1.65;
  position: relative;
  animation: slideInLeft .6s ease both;
}
.quote-bubble:nth-child(2) { animation-delay: .15s; border-radius: 16px 16px 4px 16px; margin-left: 24px; }
.quote-bubble:nth-child(3) { animation-delay: .3s; }
.quote-bubble strong { color: var(--rose); display: block; font-size: .72rem; margin-bottom: 4px; letter-spacing: .08em; text-transform: uppercase; }
@keyframes slideInLeft { from{opacity:0;transform:translateX(-16px)} to{opacity:1;transform:translateX(0)} }

/* ── FEATURES ── */
.features-grid {
  max-width: 960px; margin: 0 auto;
  display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px;
}
@media(max-width:760px) { .features-grid { grid-template-columns: 1fr; } }
@media(max-width:960px) and (min-width:761px) { .features-grid { grid-template-columns: 1fr 1fr; } }

.feature-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 18px; padding: 28px 24px;
  transition: all .3s;
  position: relative; overflow: hidden;
}
.feature-card::before {
  content: ''; position: absolute;
  top: 0; left: 0; right: 0; height: 2px;
  background: linear-gradient(90deg, var(--rose), var(--amber));
  transform: scaleX(0); transform-origin: left;
  transition: transform .4s;
}
.feature-card:hover { border-color: #3e2e22; transform: translateY(-4px); }
.feature-card:hover::before { transform: scaleX(1); }

.feature-icon {
  width: 48px; height: 48px; border-radius: 14px;
  display: flex; align-items: center; justify-content: center;
  font-size: 1.4rem; margin-bottom: 18px;
}
.icon-rose { background: var(--rose-dim); }
.icon-amber { background: var(--amber-dim); }
.icon-mint { background: var(--mint-dim); }

.feature-card h3 {
  font-family: 'Noto Serif TC', serif;
  font-size: 1rem; font-weight: 700; margin-bottom: 10px;
}
.feature-card p { font-size: .83rem; color: var(--text2); line-height: 1.7; }
.feature-tag {
  display: inline-block; margin-top: 14px;
  font-size: .68rem; letter-spacing: .1em; text-transform: uppercase;
  padding: 3px 10px; border-radius: 99px;
  background: var(--surface2); color: var(--text3);
}

/* ── FLOW ── */
.flow-section { background: var(--bg2); }
.flow-inner { max-width: 760px; margin: 0 auto; }
.flow-steps { display: flex; flex-direction: column; gap: 0; margin-top: 50px; }
.flow-step {
  display: flex; gap: 28px; align-items: flex-start;
  padding-bottom: 44px; position: relative;
}
.flow-step:not(:last-child)::after {
  content: ''; position: absolute;
  left: 19px; top: 44px; bottom: 0; width: 1px;
  background: linear-gradient(to bottom, var(--border), transparent);
}
.flow-num {
  width: 40px; height: 40px; border-radius: 50%; flex-shrink: 0;
  border: 1px solid var(--border);
  display: flex; align-items: center; justify-content: center;
  font-family: 'Playfair Display', serif; font-size: 1rem;
  color: var(--rose); background: var(--surface);
}
.flow-content h4 { font-size: .95rem; font-weight: 700; margin-bottom: 6px; }
.flow-content p { font-size: .85rem; color: var(--text2); line-height: 1.7; }
.flow-chip {
  display: inline-flex; align-items: center; gap: 6px;
  margin-top: 10px; background: var(--surface2);
  border: 1px solid var(--border); border-radius: 8px;
  padding: 6px 12px; font-size: .78rem; color: var(--text2);
}

/* ── METRICS ── */
.metrics-grid {
  max-width: 800px; margin: 50px auto 0;
  display: grid; grid-template-columns: repeat(4, 1fr); gap: 16px;
}
@media(max-width:600px) { .metrics-grid { grid-template-columns: 1fr 1fr; } }
.metric-card {
  background: var(--surface); border: 1px solid var(--border);
  border-radius: 16px; padding: 24px 16px; text-align: center;
}
.metric-num {
  font-family: 'Playfair Display', serif;
  font-size: 2.2rem; font-weight: 700; color: var(--rose);
  line-height: 1;
}
.metric-unit { font-size: .85rem; color: var(--amber); margin-left: 2px; }
.metric-label { font-size: .75rem; color: var(--text2); margin-top: 8px; line-height: 1.4; }

/* ── RISKS ── */
.risks-inner { max-width: 760px; margin: 0 auto; }
.risk-item {
  display: flex; gap: 20px;
  background: var(--surface); border: 1px solid var(--border);
  border-radius: 16px; padding: 22px 24px; margin-bottom: 14px;
  align-items: flex-start;
}
.risk-icon { font-size: 1.4rem; flex-shrink: 0; margin-top: 2px; }
.risk-content strong { display: block; font-size: .9rem; margin-bottom: 6px; }
.risk-content p { font-size: .83rem; color: var(--text2); line-height: 1.7; }

/* ── MVP ── */
.mvp-section { background: var(--bg2); }
.mvp-inner {
  max-width: 860px; margin: 0 auto;
  display: grid; grid-template-columns: 1fr 1fr; gap: 32px;
  margin-top: 50px;
}
@media(max-width:600px) { .mvp-inner { grid-template-columns: 1fr; } }
.mvp-col { }
.mvp-col h4 {
  font-size: .75rem; letter-spacing: .14em; text-transform: uppercase;
  margin-bottom: 18px; padding-bottom: 10px;
  border-bottom: 1px solid var(--border);
}
.mvp-col h4.v1 { color: var(--mint); }
.mvp-col h4.v2 { color: var(--text3); }
.mvp-item {
  display: flex; align-items: flex-start; gap: 12px;
  margin-bottom: 14px;
}
.mvp-dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; margin-top: 6px; }
.v1-dot { background: var(--mint); }
.v2-dot { background: var(--text3); }
.mvp-item p { font-size: .85rem; color: var(--text2); line-height: 1.6; }
.mvp-item p strong { color: var(--text); }

/* ── FOOTER ── */
footer {
  padding: 60px 24px;
  text-align: center;
  border-top: 1px solid var(--border);
  position: relative; z-index: 1;
}
.footer-logo {
  font-family: 'Playfair Display', serif;
  font-size: 1.6rem; font-weight: 700; color: var(--rose);
  margin-bottom: 12px;
}
footer p { font-size: .82rem; color: var(--text3); line-height: 1.8; }
.footer-tags { display: flex; gap: 10px; flex-wrap: wrap; justify-content: center; margin-top: 20px; }
.footer-tag {
  border: 1px solid var(--border); border-radius: 99px;
  padding: 4px 14px; font-size: .72rem; color: var(--text3);
  letter-spacing: .06em;
}

/* ── NAV ── */
.top-nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  display: flex; align-items: center; justify-content: space-between;
  padding: 16px 32px;
  background: rgba(13,10,8,.85);
  backdrop-filter: blur(16px);
  border-bottom: 1px solid var(--border);
}
.nav-logo {
  font-family: 'Playfair Display', serif;
  font-size: 1.1rem; font-weight: 700; color: var(--rose);
}
.nav-links { display: flex; gap: 28px; }
.nav-links a {
  font-size: .8rem; color: var(--text2); text-decoration: none;
  letter-spacing: .04em; transition: color .2s;
}
.nav-links a:hover { color: var(--text); }

/* ── SCROLL REVEAL ── */
.reveal { opacity: 0; transform: translateY(24px); transition: opacity .7s ease, transform .7s ease; }
.reveal.visible { opacity: 1; transform: translateY(0); }

/* ── CODE BLOCK (README style) ── */
.code-block {
  background: var(--surface2); border: 1px solid var(--border);
  border-radius: 12px; padding: 20px 24px; margin-top: 24px;
  font-family: 'Courier New', monospace; font-size: .82rem;
  color: #c9b99a; line-height: 1.8; overflow-x: auto;
}
.code-block .c-comment { color: var(--text3); }
.code-block .c-key { color: var(--rose); }
.code-block .c-val { color: var(--amber); }
.code-block .c-str { color: var(--mint); }

/* ── HERO SCROLL INDICATOR ── */
.scroll-hint {
  position: absolute; bottom: 36px;
  display: flex; flex-direction: column; align-items: center; gap: 8px;
  animation: fadeUp 1s .6s ease both;
}
.scroll-line {
  width: 1px; height: 40px;
  background: linear-gradient(to bottom, var(--rose), transparent);
  animation: scrollDown 2s ease-in-out infinite;
}
.scroll-hint span { font-size: .68rem; letter-spacing: .14em; text-transform: uppercase; color: var(--text3); }
@keyframes scrollDown { 0%{transform:scaleY(0);transform-origin:top} 50%{transform:scaleY(1);transform-origin:top} 51%{transform:scaleY(1);transform-origin:bottom} 100%{transform:scaleY(0);transform-origin:bottom} }

</style>
</head>
<body>

<!-- NAV -->
<nav class="top-nav">
  <div class="nav-logo">EmoMate ♡</div>
  <div class="nav-links">
    <a href="#problem">問題</a>
    <a href="#features">功能</a>
    <a href="#flow">使用流程</a>
    <a href="#mvp">MVP</a>
    <a href="#metrics">成功指標</a>
  </div>
</nav>

<!-- HERO -->
<div class="hero" style="padding-top:90px">
  <div class="hero-glow"></div>
  <div class="hero-glow2"></div>

  <div class="badge-top">
    <div class="dot"></div>
    Product Requirements Document · v1.0
  </div>

  <h1 class="hero-title">
    <span class="en">EmoMate</span>
    <span class="zh">情緒隊友</span>
  </h1>

  <p class="hero-sub">
    一款讓男朋友／老公學會提供情緒價值的行動 App。
    用「簡單、可練習、可回饋」的方式，幫助男性在親密關係中學會聆聽、共情與情緒驗證。
  </p>

  <div class="hero-cta">
    <a href="emotional-value-app.html" class="btn-main">▶ 開啟 App 原型</a>
    <a href="#problem" class="btn-sec">閱讀 PRD →</a>
  </div>

  <div class="scroll-hint">
    <span>Scroll</span>
    <div class="scroll-line"></div>
  </div>
</div>

<!-- DIVIDER -->
<div class="section-divider"><span>背景與問題</span></div>

<!-- PROBLEM -->
<section class="problem-section" id="problem">
  <div class="problem-inner">
    <div class="reveal">
      <div class="section-label">Problem Statement</div>
      <h2 class="section-heading">「你根本不懂我」</h2>
      <p class="section-body">
        男性往往在成長過程中缺乏情緒表達的教育，面對伴侶的情緒時習慣用「解決問題」的模式回應。這不是壞心，是從來沒學過。<br><br>
        EmoMate 的核心信念：情緒支持是一套<strong style="color:var(--text)">可以訓練的技能</strong>，不是天生有或沒有的天賦。
      </p>
    </div>
    <div class="quote-stack reveal">
      <div class="quote-bubble">
        <strong>她說</strong>
        「你每次都只會講大道理，我根本不需要你給我解決方案。」
      </div>
      <div class="quote-bubble">
        <strong>他說</strong>
        「我已經很用心給建議了，但她還是不開心，我真的不知道怎麼做。」
      </div>
      <div class="quote-bubble">
        <strong>她說</strong>
        「你根本不記得我上次說過什麼，我覺得你不在乎我。」
      </div>
    </div>
  </div>
</section>

<!-- DIVIDER -->
<div class="section-divider"><span>核心功能</span></div>

<!-- FEATURES -->
<section id="features" style="padding-top:80px">
  <div style="text-align:center;max-width:600px;margin:0 auto 60px;">
    <div class="section-label reveal">Core Features</div>
    <h2 class="section-heading reveal">六大核心功能</h2>
    <p class="section-body reveal" style="max-width:100%">每一個功能都圍繞一個核心：讓男方真正內化情緒共情能力，而不只是複製話術。</p>
  </div>
  <div class="features-grid">
    <div class="feature-card reveal">
      <div class="feature-icon icon-rose">📖</div>
      <h3>情緒技能課</h3>
      <p>每課 3–5 分鐘，只教一個技能。動畫範例＋互動選擇題，完成後解鎖對應任務與句式。</p>
      <span class="feature-tag">Micro-Learning</span>
    </div>
    <div class="feature-card reveal" style="animation-delay:.1s">
      <div class="feature-icon icon-amber">💬</div>
      <h3>即時教練</h3>
      <p>輸入她說的話，AI 分析情緒並生成 3 個有情緒價值的回應，每個都附上「為什麼這樣說更好」的解釋。</p>
      <span class="feature-tag">Real-time Coach</span>
    </div>
    <div class="feature-card reveal" style="animation-delay:.2s">
      <div class="feature-icon icon-mint">✅</div>
      <h3>每日情緒任務</h3>
      <p>每天推送 1–2 個低成本任務，例如「問她今天哪一刻最辛苦」，完成後獲得點數與成就徽章。</p>
      <span class="feature-tag">Daily Missions</span>
    </div>
    <div class="feature-card reveal" style="animation-delay:.1s">
      <div class="feature-icon icon-rose">📅</div>
      <h3>情緒日曆</h3>
      <p>自動記住她的重要日子、考試、面試，提前給提醒和話術建議，讓她感覺你真的在意。</p>
      <span class="feature-tag">Smart Calendar</span>
    </div>
    <div class="feature-card reveal" style="animation-delay:.2s">
      <div class="feature-icon icon-amber">💑</div>
      <h3>伴侶回饋通道</h3>
      <p>女方可選擇加入，每週填寫簡短問卷，反饋抽象化後轉為男方的成長建議，保護隱私。</p>
      <span class="feature-tag">Partner Feedback · V2</span>
    </div>
    <div class="feature-card reveal" style="animation-delay:.3s">
      <div class="feature-icon icon-mint">🏅</div>
      <h3>遊戲化成就系統</h3>
      <p>從「工具人」升至「情緒隊友」，徽章與等級讓進步有感。預設低調模式，不強迫分享。</p>
      <span class="feature-tag">Gamification</span>
    </div>
  </div>
</section>

<!-- DIVIDER -->
<div class="section-divider"><span>使用流程</span></div>

<!-- FLOW -->
<section class="flow-section" id="flow">
  <div class="flow-inner">
    <div style="text-align:center;margin-bottom:0">
      <div class="section-label reveal">User Flow</div>
      <h2 class="section-heading reveal">典型使用場景</h2>
    </div>
    <div class="flow-steps">
      <div class="flow-step reveal">
        <div class="flow-num">1</div>
        <div class="flow-content">
          <h4>她說了讓你不知怎麼回應的話</h4>
          <p>例如：「今天好累，上司又在挑剔我的報告，真的很沮喪…」你打開 EmoMate 的即時教練。</p>
          <div class="flow-chip">💬 即時教練</div>
        </div>
      </div>
      <div class="flow-step reveal">
        <div class="flow-num">2</div>
        <div class="flow-content">
          <h4>EmoMate 分析她的情緒狀態</h4>
          <p>App 識別出「委屈＋職場壓力」，並解釋她現在最需要的不是解決方案，而是被理解。</p>
          <div class="flow-chip">🧠 AI 情緒分析</div>
        </div>
      </div>
      <div class="flow-step reveal">
        <div class="flow-num">3</div>
        <div class="flow-content">
          <h4>獲得 3 個情緒價值回應選項</h4>
          <p>每個選項標注策略（先共情、陪伴、肯定），並附上為什麼這樣說比直接給建議更有效。</p>
          <div class="flow-chip">✍️ 句式＋原理說明</div>
        </div>
      </div>
      <div class="flow-step reveal">
        <div class="flow-num">4</div>
        <div class="flow-content">
          <h4>用自己的語氣說出來，而非照抄</h4>
          <p>App 鼓勵你理解原則後用自己的方式表達，因為真誠比完美更重要。長期內化才是目標。</p>
          <div class="flow-chip">💡 強調內化，不鼓勵照抄</div>
        </div>
      </div>
      <div class="flow-step reveal">
        <div class="flow-num">5</div>
        <div class="flow-content">
          <h4>每日任務＋課程持續精進</h4>
          <p>完成任務、上課程，獲得點數，等級從「工具人」一路升至「情緒隊友」。</p>
          <div class="flow-chip">🏅 遊戲化成長系統</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- DIVIDER -->
<div class="section-divider"><span>MVP 規劃</span></div>

<!-- MVP -->
<section class="mvp-section" id="mvp">
  <div style="text-align:center;max-width:600px;margin:0 auto">
    <div class="section-label reveal">Roadmap</div>
    <h2 class="section-heading reveal">MVP 範圍規劃</h2>
    <p class="section-body reveal" style="max-width:100%;margin:0 auto">先做最小可驗證的核心體驗，確認男方願意使用、女方感覺有改善後再擴展。</p>
  </div>
  <div class="mvp-inner">
    <div class="mvp-col reveal">
      <h4 class="v1">✓ MVP · V1 立即做</h4>
      <div class="mvp-item">
        <div class="mvp-dot v1-dot"></div>
        <p><strong>情緒技能課（前 5 課）</strong><br>涵蓋情緒驗證、先共情後建議、開放式問題等核心技能</p>
      </div>
      <div class="mvp-item">
        <div class="mvp-dot v1-dot"></div>
        <p><strong>即時教練（簡化版）</strong><br>文字輸入＋情緒分類＋2 個建議回應，核心閉環體驗</p>
      </div>
      <div class="mvp-item">
        <div class="mvp-dot v1-dot"></div>
        <p><strong>每日任務（基礎 20 個）</strong><br>低門檻、高頻觸達，建立使用習慣</p>
      </div>
      <div class="mvp-item">
        <div class="mvp-dot v1-dot"></div>
        <p><strong>簡易情緒日曆</strong><br>手動添加重要日子＋前一天提醒</p>
      </div>
    </div>
    <div class="mvp-col reveal" style="animation-delay:.15s">
      <h4 class="v2">○ V2 之後再考慮</h4>
      <div class="mvp-item">
        <div class="mvp-dot v2-dot"></div>
        <p><strong>女方伴侶模式</strong><br>匿名回饋機制，需要更多信任基礎才能有效運作</p>
      </div>
      <div class="mvp-item">
        <div class="mvp-dot v2-dot"></div>
        <p><strong>進階 AI 對話分析</strong><br>自動讀取聊天內容，隱私處理複雜度高</p>
      </div>
      <div class="mvp-item">
        <div class="mvp-dot v2-dot"></div>
        <p><strong>視頻／語音教學</strong><br>成本高，等核心 text-based 體驗驗證後再擴展</p>
      </div>
      <div class="mvp-item">
        <div class="mvp-dot v2-dot"></div>
        <p><strong>社群功能</strong><br>男性用戶社群、互相打氣，需要足夠 DAU 才有網路效應</p>
      </div>
    </div>
  </div>

  <div style="max-width:860px;margin:32px auto 0">
    <div class="code-block reveal">
      <span class="c-comment"># 技術棧建議 (MVP)</span><br>
      <span class="c-key">Frontend</span>: <span class="c-str">React Native</span> <span class="c-comment"># 跨平台 iOS + Android</span><br>
      <span class="c-key">AI Engine</span>: <span class="c-str">Claude API</span> <span class="c-comment"># 情緒分析 + 回應生成</span><br>
      <span class="c-key">Privacy</span>: <span class="c-str">本機端加密</span> <span class="c-comment"># 聊天內容不上傳伺服器</span><br>
      <span class="c-key">Language</span>: <span class="c-str">繁中 + 簡中</span> <span class="c-comment"># 港台 + 大陸口語化</span><br>
      <span class="c-key">Interaction</span>: <span class="c-val">10–30s</span> <span class="c-comment"># 所有關鍵操作的目標完成時間</span>
    </div>
  </div>
</section>

<!-- DIVIDER -->
<div class="section-divider"><span>成功指標與風險</span></div>

<!-- METRICS -->
<section id="metrics">
  <div style="text-align:center;max-width:600px;margin:0 auto">
    <div class="section-label reveal">Success Metrics</div>
    <h2 class="section-heading reveal">北極星與成功指標</h2>
    <p class="section-body reveal" style="max-width:100%;margin:0 auto">
      北極星指標：女友／老婆在 4 週後的「被情緒理解與支持感」自評分提升 ≥ 2 分（1–10 分量表）。
    </p>
  </div>
  <div class="metrics-grid">
    <div class="metric-card reveal">
      <div class="metric-num">35<span class="metric-unit">%</span></div>
      <div class="metric-label">D7 留存率目標</div>
    </div>
    <div class="metric-card reveal" style="animation-delay:.1s">
      <div class="metric-num">4<span class="metric-unit">個</span></div>
      <div class="metric-label">每週平均完成任務數（per user）</div>
    </div>
    <div class="metric-card reveal" style="animation-delay:.2s">
      <div class="metric-num">60<span class="metric-unit">%</span></div>
      <div class="metric-label">4 週後伴侶自評提升 ≥2 分的比例</div>
    </div>
    <div class="metric-card reveal" style="animation-delay:.3s">
      <div class="metric-num">+2<span class="metric-unit">分</span></div>
      <div class="metric-label">男方自評「懂得如何安慰」信心提升</div>
    </div>
  </div>

  <div class="risks-inner" style="margin-top:60px">
    <div class="section-label reveal" style="text-align:center">Risks & Mitigations</div>
    <div style="text-align:center;margin-bottom:32px">
      <h3 class="section-heading reveal" style="font-size:1.6rem">主要風險與應對</h3>
    </div>
    <div class="risk-item reveal">
      <div class="risk-icon">⚠️</div>
      <div class="risk-content">
        <strong>風險：男方覺得學情緒很丟臉，不願意用</strong>
        <p>應對：用「升級自己」的成長敘事框架，而非「你有問題要修正」的框架。遊戲化等級、徽章讓學習有成就感，弱化「情緒課」的標籤。</p>
      </div>
    </div>
    <div class="risk-item reveal">
      <div class="risk-icon">⚠️</div>
      <div class="risk-content">
        <strong>風險：男方只把 App 當話術生成器，沒有真正內化</strong>
        <p>應對：所有建議話術都附「為什麼」說明，強調原則理解。加入「誠實模式」教育：「我還在學，可能說得不好，但我想試著理解你。」</p>
      </div>
    </div>
    <div class="risk-item reveal">
      <div class="risk-icon">⚠️</div>
      <div class="risk-content">
        <strong>風險：女方覺得「你是不是又在用 App 應付我」</strong>
        <p>應對：MVP 不做自動讀取聊天功能，減少「被 AI 操控」的感覺。鼓勵男方主動告訴她「我在學習怎麼更好地支持你」。</p>
      </div>
    </div>
    <div class="risk-item reveal">
      <div class="risk-icon">⚠️</div>
      <div class="risk-content">
        <strong>風險：聊天內容隱私洩露風險</strong>
        <p>應對：所有聊天輸入預設在本機端處理並加密，明確告知用戶數據政策，不強制雲端同步。</p>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo reveal">情緒隊友 EmoMate ♡</div>
  <p class="reveal" style="margin-top:8px">
    Product Requirements Document · Version 1.0<br>
    Designed for 22–40 歲 城市男性用戶 · 中文市場
  </p>
  <div class="footer-tags reveal">
    <span class="footer-tag">Relationship Tech</span>
    <span class="footer-tag">Emotional Intelligence</span>
    <span class="footer-tag">Behavior Change</span>
    <span class="footer-tag">AI Coach</span>
    <span class="footer-tag">中文市場</span>
  </div>
  <p style="margin-top:32px;font-size:.75rem;color:var(--text3)" class="reveal">
    基於 PRD by Perplexity AI · App 原型由 Claude (Anthropic) 生成
  </p>
</footer>

<script>
// Scroll reveal
const reveals = document.querySelectorAll('.reveal');
const io = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if(e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); }
  });
}, { threshold: 0.12 });
reveals.forEach(r => io.observe(r));
</script>
</body>
</html>
