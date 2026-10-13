<!doctype html>
<html lang="en" data-theme="dark">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Eyerusalem Aklilu · Web Developer &amp; Automation Builder</title>
  <meta name="description" content="Web developer and automation builder. Open for freelance and part-time work, 4:30 PM to 1:30 AM EAT.">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&family=JetBrains+Mono:wght@500&display=swap">
  <style>
/* ==========================================================
   style.css
   1. Tokens   2. Base   3. Top bar   4. Layout & sidebar
   5. Cards    6. Availability   7. Projects   8. Skills
   9. Contact  10. Footer   11. Responsive   12. Reduced motion
   ========================================================== */

/* ---------- 1. TOKENS ---------- */
:root {
  --bg: #0b100d; --panel: #111a15; --panel2: #16221b; --line: #223128;
  --fg: #e8efe9; --muted: #93a39a;
  --green: #1f4d39; --green-2: #2f7a58;
  --amber: #f6a900; --amber-soft: rgba(246,169,0,.14); --ok: #3ddc84;
  --font: "Plus Jakarta Sans", "Helvetica Neue", Arial, sans-serif;
  --mono: "JetBrains Mono", ui-monospace, Menlo, monospace;
  --gutter: clamp(16px, 4vw, 40px);
  color-scheme: dark;
}
[data-theme="light"] {
  --bg: #f6f7f4; --panel: #ffffff; --panel2: #f1f3ee; --line: #e0e5dd;
  --fg: #1d2b24; --muted: #66706a;
  --amber-soft: #fff1cc; --ok: #1a9d55;
  color-scheme: light;
}

/* ---------- 2. BASE ---------- */
* { box-sizing: border-box; }
html { scroll-behavior: smooth; }
body {
  margin: 0; background: var(--bg); color: var(--fg);
  font: 400 15px/1.6 var(--font); -webkit-font-smoothing: antialiased; overflow-x: clip;
  background-image:
    radial-gradient(900px 400px at 85% -10%, rgba(246,169,0,.10), transparent 60%),
    radial-gradient(700px 400px at -5% 10%, rgba(47,122,88,.18), transparent 60%);
  background-repeat: no-repeat;
}
a { color: inherit; }
h1, h2, h3, p { margin: 0; }
:focus-visible { outline: 2px solid var(--amber); outline-offset: 3px; border-radius: 8px; }
section[id], .layout { scroll-margin-top: 80px; }

/* ---------- 3. TOP BAR ---------- */
.top {
  position: sticky; top: env(safe-area-inset-top, 0px); z-index: 20;
  background: color-mix(in srgb, var(--bg) 82%, transparent);
  -webkit-backdrop-filter: blur(14px); backdrop-filter: blur(14px);
  border-bottom: 1px solid var(--line);
}
.top-in { max-width: 1240px; margin: 0 auto; padding: 12px var(--gutter); display: flex; align-items: center; gap: 18px; }
.logo { display: flex; align-items: center; gap: 10px; text-decoration: none; font-weight: 700; font-family: var(--mono); font-size: 14px; }
.logo i { width: 32px; height: 32px; border-radius: 9px; background: var(--green); color: var(--amber); display: grid; place-items: center; font: 800 15px var(--font); font-style: normal; }
.logo em { color: var(--amber); font-style: normal; margin: 0 2px; }
.top-nav { margin-left: auto; display: flex; gap: 4px; }
.top-nav a { text-decoration: none; color: var(--muted); font-size: 13.5px; font-weight: 500; padding: 7px 12px; border-radius: 999px; transition: background .2s, color .2s; }
.top-nav a:hover, .top-nav a.on { background: var(--panel2); color: var(--fg); }
.theme { width: 38px; height: 38px; border-radius: 50%; border: 1px solid var(--line); background: var(--panel); color: var(--amber); display: grid; place-items: center; cursor: pointer; padding: 0; }
.theme svg { width: 18px; height: 18px; }

/* ---------- 4. LAYOUT & SIDEBAR ---------- */
.layout {
  max-width: 1240px; margin: 0 auto; padding: clamp(22px, 4vw, 44px) var(--gutter) 40px;
  display: grid; grid-template-columns: 300px minmax(0, 1fr); gap: clamp(20px, 3.5vw, 44px); align-items: start;
}
.side { position: sticky; top: 84px; display: grid; gap: 14px; }
.main { display: grid; gap: 22px; min-width: 0; }

.avatar {
  width: 100%; max-width: 280px; aspect-ratio: 1; border-radius: 50%;
  background: linear-gradient(140deg, var(--amber), #ffcf5a 55%, var(--green-2));
  display: grid; place-items: center; position: relative; overflow: hidden;
  border: 3px solid var(--line); box-shadow: 0 24px 50px -28px rgba(246,169,0,.55);
}
.avatar span { font: 800 clamp(5rem, 12vw, 7rem)/1 var(--font); color: var(--green); }
.avatar img { position: absolute; inset: 0; width: 100%; height: 100%; object-fit: cover; }
.name { font-size: 1.9rem; line-height: 1.1; letter-spacing: -.02em; font-weight: 800; margin-top: 6px; }
.user { font: 500 15px var(--mono); color: var(--muted); margin-top: -8px; }
.bio { color: var(--fg); opacity: .9; font-size: 14.5px; }

.status { display: inline-flex; align-items: center; gap: 10px; width: fit-content; padding: 7px 14px; border-radius: 999px; background: var(--panel); border: 1px solid var(--line); font-size: 13px; font-weight: 600; }
.status i { width: 9px; height: 9px; border-radius: 50%; background: var(--muted); flex: none; }
.status.on i { background: var(--ok); box-shadow: 0 0 0 0 rgba(61,220,132,.6); animation: pulse 1.8s infinite; }
.status.off i { background: var(--amber); }
@keyframes pulse { 70% { box-shadow: 0 0 0 9px rgba(61,220,132,0); } 100% { box-shadow: 0 0 0 0 rgba(61,220,132,0); } }

.btn { display: inline-flex; align-items: center; justify-content: center; gap: 8px; border-radius: 999px; padding: 11px 20px; font: 700 14px var(--font); text-decoration: none; border: 1.5px solid var(--line); cursor: pointer; transition: transform .2s, filter .2s, border-color .2s; }
.btn:hover { transform: translateY(-2px); }
.btn-main { background: var(--amber); color: #1a2a20; border-color: var(--amber); }
.btn-main:hover { filter: brightness(1.06); }

.meta { list-style: none; margin: 4px 0 0; padding: 0; display: grid; gap: 10px; font-size: 14px; color: var(--muted); }
.meta li { display: flex; align-items: center; gap: 10px; min-width: 0; }
.meta svg { width: 17px; height: 17px; flex: none; fill: none; stroke: var(--amber); stroke-width: 2; stroke-linecap: round; stroke-linejoin: round; }
.meta a { text-decoration: none; color: var(--fg); overflow-wrap: anywhere; }
.meta a:hover { color: var(--amber); }
.meta b { color: var(--fg); font-family: var(--mono); font-weight: 500; }

.side-stats { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; margin-top: 4px; }
.side-stats div { background: var(--panel); border: 1px solid var(--line); border-radius: 14px; padding: 10px 6px; text-align: center; display: grid; gap: 2px; }
.side-stats b { font-size: 1.15rem; color: var(--amber); line-height: 1; }
.side-stats span { font-size: 11px; color: var(--muted); }

/* ---------- 5. CARDS & README ---------- */
.card { background: var(--panel); border: 1px solid var(--line); border-radius: 20px; overflow: hidden; }
.card-bar { display: flex; align-items: center; justify-content: space-between; gap: 12px; padding: 12px 20px; border-bottom: 1px solid var(--line); background: var(--panel2); }
.card-body { padding: clamp(20px, 3.5vw, 34px); display: grid; gap: 18px; }
.file { display: inline-flex; align-items: center; gap: 10px; font: 500 13px var(--mono); color: var(--muted); }
.file svg { width: 16px; height: 16px; fill: none; stroke: currentColor; stroke-width: 2; stroke-linecap: round; stroke-linejoin: round; }
.pill { font: 600 11px var(--font); padding: 3px 11px; border-radius: 999px; border: 1px solid var(--line); color: var(--muted); }
.pill.live { color: var(--ok); border-color: color-mix(in srgb, var(--ok) 40%, transparent); }

.hello { color: var(--amber); font: 500 14px var(--mono); }
.wave { display: inline-block; animation: wave 2.4s ease-in-out infinite; transform-origin: 70% 80%; }
@keyframes wave { 0%, 60%, 100% { transform: rotate(0); } 10%, 30% { transform: rotate(14deg); } 20%, 40% { transform: rotate(-8deg); } 50% { transform: rotate(10deg); } }
.type-h { font-size: clamp(1.8rem, 4.2vw, 3rem); line-height: 1.12; letter-spacing: -.03em; font-weight: 800; min-height: 2.3em; }
#typed { color: var(--amber); }
.caret { display: inline-block; width: 3px; height: .95em; background: var(--amber); margin-left: 4px; vertical-align: -.1em; animation: blink 1s steps(2) infinite; }
@keyframes blink { 50% { opacity: 0; } }
.lead { color: var(--muted); max-width: 64ch; }

.trio { display: grid; grid-template-columns: repeat(3, minmax(0, 1fr)); gap: 12px; }
.trio div { background: var(--panel2); border: 1px solid var(--line); border-radius: 16px; padding: 16px; display: grid; gap: 4px; align-content: start; }
.trio b { font-size: 14px; }
.trio span { font-size: 13px; color: var(--muted); line-height: 1.5; }

/* ---------- 6. AVAILABILITY ---------- */
.av-top { display: flex; justify-content: space-between; gap: 14px; flex-wrap: wrap; align-items: flex-start; }
.av-state { font-size: clamp(1.4rem, 3vw, 2rem); font-weight: 800; letter-spacing: -.02em; line-height: 1.15; }
.av-state.on { color: var(--ok); }
.av-state.off { color: var(--amber); }
.av-sub { color: var(--muted); font-size: 14px; margin-top: 4px; }
.av-tags { display: flex; gap: 8px; flex-wrap: wrap; }
.av-tags span { font-size: 12px; font-weight: 700; padding: 6px 14px; border-radius: 999px; background: var(--amber-soft); color: var(--amber); border: 1px solid color-mix(in srgb, var(--amber) 35%, transparent); }
[data-theme="light"] .av-tags span { color: #8a5a00; }

.tl-bar { position: relative; height: 16px; border-radius: 999px; background: var(--panel2); border: 1px solid var(--line); }
.seg { position: absolute; top: 0; bottom: 0; background: linear-gradient(90deg, var(--green-2), var(--amber)); border-radius: 999px; }
.now { position: absolute; top: -6px; bottom: -6px; width: 4px; margin-left: -2px; border-radius: 4px; background: var(--fg); box-shadow: 0 0 0 3px var(--panel); transition: left .6s ease; }
.tl-ticks { display: flex; justify-content: space-between; font: 500 11px var(--mono); color: var(--muted); margin-top: 8px; }

.av-grid { display: grid; grid-template-columns: repeat(3, minmax(0, 1fr)); gap: 12px; }
.av-box { background: var(--panel2); border: 1px solid var(--line); border-radius: 16px; padding: 14px 16px; display: grid; gap: 2px; }
.av-box small { font-size: 12px; color: var(--muted); }
.av-box small em { font-style: normal; color: var(--amber); }
.av-box b { font-size: 1.02rem; font-weight: 700; }

.week { display: grid; grid-template-columns: 34px repeat(24, minmax(0, 1fr)); gap: 3px; align-items: center; }
.week .d { font: 500 11px var(--mono); color: var(--muted); }
.week .d.today { color: var(--amber); font-weight: 700; }
.week .c { aspect-ratio: 1; border-radius: 4px; background: var(--panel2); border: 1px solid var(--line); }
.week .c.f { background: var(--amber); border-color: var(--amber); }
.week .c.r { background: linear-gradient(90deg, var(--panel2) 50%, var(--amber) 50%); }
.week .c.l { background: linear-gradient(90deg, var(--amber) 50%, var(--panel2) 50%); }
.week .h { font: 500 9px var(--mono); color: var(--muted); text-align: center; }
.note { font-size: 13px; color: var(--muted); }

/* ---------- 7. PROJECTS ---------- */
.sec-title { display: flex; justify-content: space-between; align-items: baseline; gap: 12px; margin-bottom: 14px; }
.sec-title h3 { font-size: 1.3rem; font-weight: 800; letter-spacing: -.02em; }
.sec-title a { font-size: 13.5px; color: var(--amber); text-decoration: none; font-weight: 600; }

.repos { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 14px; }
.repo { background: var(--panel); border: 1px solid var(--line); border-radius: 18px; padding: 20px; display: grid; gap: 12px; align-content: space-between; text-decoration: none; position: relative; transition: transform .25s ease, border-color .25s ease, box-shadow .25s ease; }
.repo:hover { transform: translateY(-4px); border-color: var(--amber); box-shadow: 0 22px 40px -28px rgba(246,169,0,.55); }
.repo-top { display: flex; align-items: center; gap: 10px; }
.repo-top svg { width: 18px; height: 18px; fill: none; stroke: var(--muted); stroke-width: 2; stroke-linecap: round; stroke-linejoin: round; flex: none; }
.repo-top b { font: 600 15px var(--mono); color: var(--amber); overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
.repo-top .pill { margin-left: auto; }
.repo p { color: var(--muted); font-size: 13.5px; }
.repo-foot { display: flex; flex-wrap: wrap; gap: 8px; align-items: center; font-size: 12px; color: var(--muted); }
.dot { width: 10px; height: 10px; border-radius: 50%; display: inline-block; margin-right: 6px; }
.tag { padding: 3px 10px; border-radius: 999px; background: var(--amber-soft); color: var(--amber); font-weight: 700; font-size: 11px; }
[data-theme="light"] .tag { color: #8a5a00; }

/* ---------- 8. SKILLS ---------- */
.sk-group { display: grid; gap: 10px; }
.sk-group small { font: 600 11px var(--font); letter-spacing: .09em; text-transform: uppercase; color: var(--muted); }
.chips { display: flex; flex-wrap: wrap; gap: 8px; }
.chip { display: inline-flex; align-items: center; gap: 8px; padding: 8px 14px; border-radius: 999px; background: var(--panel2); border: 1px solid var(--line); font-size: 13.5px; font-weight: 600; transition: transform .2s, border-color .2s; }
.chip:hover { transform: translateY(-2px); border-color: var(--amber); }
.chip i { width: 9px; height: 9px; border-radius: 50%; }

/* ---------- 9. CONTACT ---------- */
.cta {
  display: grid; grid-template-columns: minmax(0, 1.2fr) minmax(0, 1fr); gap: 24px; align-items: center;
  padding: clamp(24px, 4.5vw, 44px); border-radius: 24px;
  background: linear-gradient(135deg, var(--green), #173a2b); color: #f4f7f3;
  border: 1px solid rgba(255,255,255,.08); position: relative; overflow: hidden;
}
.cta::after { content: ""; position: absolute; right: -60px; top: -60px; width: 220px; height: 220px; border-radius: 50%; background: radial-gradient(circle, rgba(246,169,0,.5), transparent 70%); pointer-events: none; }
.eyebrow { display: inline-flex; align-items: center; gap: 8px; font-size: 13px; color: #c9d6cd; }
.eyebrow::before { content: ""; width: 10px; height: 2px; background: var(--amber); border-radius: 2px; }
.cta h3 { font-size: clamp(1.6rem, 3.2vw, 2.3rem); line-height: 1.12; letter-spacing: -.02em; font-weight: 800; margin: 8px 0; color: #fff; max-width: 16ch; }
.cta p { color: #d3dfd7; font-size: 14px; max-width: 42ch; }

.cta-links { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 10px; position: relative; z-index: 1; }
.cta-links a { display: flex; align-items: center; gap: 10px; min-width: 0; padding: 10px 14px 10px 10px; border-radius: 999px; background: rgba(255,255,255,.09); border: 1px solid rgba(255,255,255,.2); color: #fff; text-decoration: none; transition: background .2s, border-color .2s, transform .2s; }
.cta-links a.on:hover { background: rgba(255,255,255,.16); border-color: var(--amber); transform: translateY(-2px); }
.cta-links .ic { width: 36px; height: 36px; border-radius: 50%; background: #fff; display: grid; place-items: center; flex: none; }
.cta-links .ic svg { width: 19px; height: 19px; }
.cta-links .tx { display: grid; min-width: 0; }
.cta-links .tx small { font-size: 11px; color: #c9d6cd; line-height: 1.2; }
.cta-links .tx b { font-size: 13px; font-weight: 600; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }

/* ---------- 10. FOOTER ---------- */
footer { max-width: 1240px; margin: 0 auto; padding: 8px var(--gutter) 36px; display: flex; justify-content: space-between; gap: 16px; flex-wrap: wrap; font-size: 13px; color: var(--muted); }
footer a { text-decoration: none; }

/* ---------- 11. RESPONSIVE ---------- */
@media (max-width: 960px) {
  .layout { grid-template-columns: minmax(0, 1fr); }
  .side { position: static; grid-template-columns: 120px minmax(0, 1fr); column-gap: 18px; align-items: center; }
  .side > * { grid-column: 2; }
  .avatar { grid-column: 1; grid-row: 1 / span 3; max-width: 120px; }
  .avatar span { font-size: 3.4rem; }
  .meta, .side-stats, .btn-main { grid-column: 1 / -1; }
  .btn-main { justify-self: start; }
  .cta { grid-template-columns: minmax(0, 1fr); }
}
@media (max-width: 720px) {
  .top-nav { display: none; }
  .theme { margin-left: auto; }
  .trio, .av-grid, .repos { grid-template-columns: minmax(0, 1fr); }
  .week { grid-template-columns: 28px repeat(24, minmax(0, 1fr)); gap: 2px; }
  .week .c { border-radius: 2px; }
  .week .h { visibility: hidden; height: 0; }   /* keep the cells so the grid columns stay aligned */
}
@media (max-width: 460px) {
  .cta-links { grid-template-columns: minmax(0, 1fr); }
}

/* ---------- 12. REDUCED MOTION ---------- */
@media (prefers-reduced-motion: reduce) {
  html { scroll-behavior: auto; }
  *, *::before, *::after { animation: none !important; transition: none !important; }
}

</style>
</head>
<body>

<!-- ================= TOP BAR ================= -->
<header class="top">
  <div class="top-in">
    <a class="logo" href="#top" aria-label="Home"><i id="logoInitial">E</i><span><span id="logoName">E</span><em>/</em>profile</span></a>
    <nav class="top-nav" aria-label="Primary">
      <a href="#readme">Overview</a>
      <a href="#availability">Availability</a>
      <a href="#work">Work</a>
      <a href="#skills">Skills</a>
      <a href="#contact">Contact</a>
    </nav>
    <button class="theme" id="theme" type="button" aria-label="Switch to light theme">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="4"/><path d="M12 2v2M12 20v2M4.9 4.9l1.4 1.4M17.7 17.7l1.4 1.4M2 12h2M20 12h2M4.9 19.1l1.4-1.4M17.7 6.3l1.4-1.4"/></svg>
    </button>
  </div>
</header>

<div class="layout" id="top">

  <!-- ================= SIDEBAR ================= -->
  <aside class="side">
    <div class="avatar" id="avatar"><span id="avatarInitial">E</span></div>
    <h1 class="name" id="name">Your Name</h1>
    <p class="user" id="user">@your-username</p>
    <p class="bio">Web Developer &amp; Automation Builder. I design, build and connect websites and web apps to the tools your team uses.</p>

    <div class="status" id="statusChip"><i></i><span>Checking availability…</span></div>
    <a class="btn btn-main" id="mailBtn" href="#contact">Contact me</a>

    <ul class="meta">
      <li><svg viewBox="0 0 24 24"><path d="M12 22s7-6.2 7-12a7 7 0 10-14 0c0 5.8 7 12 7 12z"/><circle cx="12" cy="10" r="2.5"/></svg><span id="loc"></span></li>
      <li><svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 2"/></svg><span>Local time <b id="clock">--:--</b> EAT</span></li>
      <li><svg viewBox="0 0 24 24"><path d="M10 14a4 4 0 005.7 0l3-3a4 4 0 00-5.7-5.7l-1 1"/><path d="M14 10a4 4 0 00-5.7 0l-3 3a4 4 0 005.7 5.7l1-1"/></svg><a id="lnkSite" href="#" target="_blank" rel="noopener">portfolio</a></li>
      <li><svg viewBox="0 0 24 24"><rect x="3" y="5" width="18" height="14" rx="2"/><path d="M3 7l9 6 9-6"/></svg><a id="lnkMail" href="#contact">your-name@gmail.com</a></li>
    </ul>

    <div class="side-stats">
      <div><b id="statProjects">4</b><span>Projects</span></div>
      <div><b>1</b><span>Automation</span></div>
      <div><b>9h</b><span>Daily window</span></div>
    </div>
  </aside>

  <!-- ================= MAIN ================= -->
  <main class="main">

    <!-- README / overview -->
    <section class="card" id="readme">
      <div class="card-bar">
        <span class="file"><svg viewBox="0 0 24 24"><path d="M6 3h8l4 4v14H6z"/><path d="M14 3v4h4"/></svg><span id="readmeFile">README.md</span></span>
        <span class="pill">Public</span>
      </div>
      <div class="card-body">
        <p class="hello">Hello there <span class="wave">👋</span></p>
        <h2 class="type-h">I'm <span id="firstName">E</span>, I <span id="typed"></span><span class="caret"></span></h2>
        <p class="lead">I work across the whole page: design in Figma, front-end in HTML, CSS and JavaScript, builds in Webflow and WordPress with CMS integration, and the automation around a site with Slack and Jira.</p>
        <div class="trio">
          <div><b>What you get</b><span>Pages that are quick to scan, simple to edit and consistent from first section to last.</span></div>
          <div><b>How I work</b><span>Small, clear updates. I keep the scope tight and confirm everything works first.</span></div>
          <div><b>My value</b><span>One person for design, build and coordination, with no hand-offs.</span></div>
        </div>
      </div>
    </section>

    <!-- Availability -->
    <section class="card" id="availability">
      <div class="card-bar">
        <span class="file"><svg viewBox="0 0 24 24"><rect x="3" y="5" width="18" height="16" rx="2"/><path d="M3 10h18M8 3v4M16 3v4"/></svg>Availability</span>
        <span class="pill live" id="livePill">Live</span>
      </div>
      <div class="card-body">
        <div class="av-top">
          <div>
            <p class="av-state" id="avState">…</p>
            <p class="av-sub" id="avSub"></p>
          </div>
          <div class="av-tags"><span>Freelance</span><span>Part-time</span></div>
        </div>

        <div class="tl" aria-hidden="true">
          <div class="tl-bar"><i class="seg" id="seg1"></i><i class="seg" id="seg2"></i><i class="now" id="now"></i></div>
          <div class="tl-ticks"><span>12 AM</span><span>6 AM</span><span>12 PM</span><span>6 PM</span><span>12 AM</span></div>
        </div>

        <div class="av-grid">
          <div class="av-box"><small>My hours (EAT, UTC+3)</small><b>4:30 PM – 1:30 AM</b></div>
          <div class="av-box"><small>In UTC</small><b>1:30 PM – 10:30 PM</b></div>
          <div class="av-box"><small>In your time <em id="tzName"></em></small><b id="yourTime">--</b></div>
        </div>

        <div class="week" id="week" role="img" aria-label="Weekly availability grid"></div>
        <p class="note">Message me inside these hours for the fastest reply. Outside them I answer the next working day.</p>
      </div>
    </section>

    <!-- Projects -->
    <section id="work">
      <div class="sec-title"><h3>Selected work</h3><a id="allWork" href="#" target="_blank" rel="noopener">View portfolio →</a></div>
      <div class="repos" id="repos"></div>
    </section>

    <!-- Skills -->
    <section class="card" id="skills">
      <div class="card-bar">
        <span class="file"><svg viewBox="0 0 24 24"><path d="M8 8l-5 4 5 4M16 8l5 4-5 4M14 5l-4 14"/></svg>Skills &amp; tools</span>
      </div>
      <div class="card-body" id="skillBody"></div>
    </section>

    <!-- Contact -->
    <section class="cta" id="contact">
      <div>
        <span class="eyebrow">Book a call</span>
        <h3>Let's build something that works.</h3>
        <p>Tell me about your website, web app or workflow and I'll reply with a clear plan and next steps.</p>
      </div>
      <div class="cta-links" id="ctaLinks"></div>
    </section>

  </main>
</div>

<footer><span id="footName">© 2026</span><a href="#top">Back to top ↑</a></footer>

<!-- config first (your data), then the page logic -->
<script>
/* ==========================================================
   config.js — the only file you need to edit
   Your details, hours, projects and skills live here.
   ========================================================== */

/* ---------- 1. PROFILE (from your GitHub profile) ---------- */
var PROFILE = {
  name: "Eyerusalem Aklilu",          /* shown in the sidebar, title and README */
  username: "eyerusalemaklilu",       /* your GitHub username */
  avatar: "",                         /* e.g. "images/me.jpg". Empty keeps the letter badge */
  location: "Addis Ababa, Ethiopia",
  website: "",                        /* your portfolio link, e.g. "https://yourname.com" */
  linkedin: "",                       /* e.g. "linkedin.com/in/your-name" */
  telegram: "",                       /* e.g. "@your_username" */
  email: ""                           /* e.g. "you@gmail.com" */
};

/* ---------- 2. WORKING HOURS ----------
   East Africa Time (UTC+3), 24h clock as [hour, minute].
   Crossing midnight (16:30 -> 01:30) is handled automatically. */
var HOURS = { start: [16, 30], end: [1, 30], zone: "Africa/Addis_Ababa", offset: "+03:00" };

/* Days you work. 0 = Sunday ... 6 = Saturday. Remove a number to mark a day off. */
var DAYS = [0, 1, 2, 3, 4, 5, 6];

/* ---------- 3. TYPING LINES ("I design websites.") ---------- */
var TYPED = ["design websites.", "build web apps.", "connect Slack and Jira.", "automate manual work."];

/* ---------- 4. PROJECTS ----------
   url: link to the live site or repo. Leave "" if it is private. */
var PROJECTS = [
  { name: "[project-one]",        desc: "[Goal, your role and the result.]",                    tags: ["Webflow", "CMS"],          lang: "Webflow",    color: "#4353ff", url: "" },
  { name: "[project-two]",        desc: "[Goal, your role and the result.]",                    tags: ["HTML", "CSS", "JS"],       lang: "JavaScript", color: "#f0db4f", url: "" },
  { name: "[project-three]",      desc: "[Goal, your role and the result.]",                    tags: ["WordPress", "App"],        lang: "WordPress",  color: "#3179a1", url: "" },
  { name: "[automation-project]", desc: "[What it automates and the manual work it removed.]",  tags: ["Slack", "Jira", "GitHub"], lang: "Automation", color: "#2eb57d", url: "" }
];

/* ---------- 5. SKILLS: [name, dot colour] ---------- */
var SKILLS = [
  { group: "Design",                items: [["Figma", "#a259ff"]] },
  { group: "Front-end",             items: [["HTML5", "#e44d26"], ["CSS3", "#1572b6"], ["JavaScript", "#f0db4f"]] },
  { group: "CMS & no-code",         items: [["Webflow", "#4353ff"], ["WordPress", "#3179a1"]] },
  { group: "Automation & teamwork", items: [["Slack", "#de1c59"], ["Jira", "#2684ff"], ["GitHub", "#8b949e"], ["Notion", "#e8efe9"], ["Google Workspace", "#34a853"]] }
];

</script>
<script>
/* ==========================================================
   main.js — page behaviour. You should not need to edit this.
   Reads everything from config.js.
   Sections: helpers, theme, profile, typing, projects, skills,
             contact links, availability, nav highlight
   ========================================================== */
(function () {
  "use strict";

  /* ---------- helpers ---------- */
  var $ = function (id) { return document.getElementById(id); };
  var DAYN = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];
  var START = HOURS.start[0] * 60 + HOURS.start[1];
  var END = HOURS.end[0] * 60 + HOURS.end[1];
  var CROSS = END <= START;                       /* window crosses midnight */

  function pad(n) { return (n < 10 ? "0" : "") + n; }
  function pct(m) { return (m / 1440 * 100) + "%"; }
  function fmtDur(m) { var h = Math.floor(m / 60), r = m % 60; return (h ? h + "h " : "") + r + "m"; }
  function t12(m) { var h = Math.floor(m / 60) % 24, mi = m % 60; return ((h % 12) || 12) + ":" + pad(mi) + " " + (h < 12 ? "AM" : "PM"); }

  /* current time in the working time zone */
  function addisNow() {
    var f = new Intl.DateTimeFormat("en-GB", { timeZone: HOURS.zone, weekday: "short", hour: "2-digit", minute: "2-digit", hour12: false, year: "numeric", month: "2-digit", day: "2-digit" });
    var o = {};
    f.formatToParts(new Date()).forEach(function (p) { o[p.type] = p.value; });
    var hh = parseInt(o.hour, 10) % 24, mm = parseInt(o.minute, 10);
    return { m: hh * 60 + mm, hh: hh, mm: mm, day: DAYN.indexOf(o.weekday), ymd: o.year + "-" + o.month + "-" + o.day };
  }

  /* ---------- theme toggle ---------- */
  (function theme() {
    var root = document.documentElement, btn = $("theme");
    btn.addEventListener("click", function () {
      var toLight = root.getAttribute("data-theme") === "dark";
      root.setAttribute("data-theme", toLight ? "light" : "dark");
      btn.setAttribute("aria-label", toLight ? "Switch to dark theme" : "Switch to light theme");
    });
  })();

  /* ---------- profile ---------- */
  (function profile() {
    var first = PROFILE.name.split(" ")[0], initial = PROFILE.name.charAt(0).toUpperCase();

    document.title = PROFILE.name + " · Web Developer & Automation Builder";
    $("name").textContent = PROFILE.name;
    $("user").textContent = "@" + PROFILE.username;
    $("loc").textContent = PROFILE.location;
    $("firstName").textContent = first;
    $("logoName").textContent = first;
    $("logoInitial").textContent = initial;
    $("avatarInitial").textContent = initial;
    $("readmeFile").textContent = PROFILE.username + " / README.md";
    $("footName").textContent = "© 2026 " + PROFILE.name;
    $("statProjects").textContent = PROJECTS.length;

    if (PROFILE.avatar) {
      var img = document.createElement("img");
      img.alt = "Portrait of " + PROFILE.name;
      img.src = PROFILE.avatar;
      $("avatar").appendChild(img);
    }

    var site = $("lnkSite"), all = $("allWork");
    if (PROFILE.website) {
      site.href = all.href = PROFILE.website;
      site.textContent = PROFILE.website.replace(/^https?:\/\//i, "");
    } else {
      all.hidden = true;
    }

    if (PROFILE.email) {
      $("lnkMail").href = $("mailBtn").href = "mailto:" + PROFILE.email;
      $("lnkMail").textContent = PROFILE.email;
    }
  })();

  /* ---------- typing effect ---------- */
  (function typing() {
    var el = $("typed"), ti = 0, ci = 0, del = false;
    var reduce = window.matchMedia && window.matchMedia("(prefers-reduced-motion: reduce)").matches;
    if (reduce) { el.textContent = TYPED[0]; return; }
    (function tick() {
      var w = TYPED[ti], d = del ? 35 : 70;
      ci += del ? -1 : 1;
      el.textContent = w.slice(0, ci);
      if (!del && ci === w.length) { del = true; d = 1500; }
      else if (del && ci === 0) { del = false; ti = (ti + 1) % TYPED.length; d = 350; }
      setTimeout(tick, d);
    })();
  })();

  /* ---------- projects ---------- */
  (function projects() {
    var icon = '<svg viewBox="0 0 24 24"><path d="M4 5a2 2 0 012-2h12v15H6a2 2 0 00-2 2z"/><path d="M4 20a2 2 0 002 2h12"/></svg>';
    PROJECTS.forEach(function (p) {
      var a = document.createElement(p.url ? "a" : "div");
      a.className = "repo";
      if (p.url) { a.href = p.url; a.target = "_blank"; a.rel = "noopener"; }
      a.innerHTML = '<div class="repo-top">' + icon + '<b></b><span class="pill">Project</span></div><p></p><div class="repo-foot"><span><i class="dot"></i><span class="lg"></span></span></div>';
      a.querySelector("b").textContent = p.name;
      a.querySelector("p").textContent = p.desc;
      a.querySelector(".dot").style.background = p.color;
      a.querySelector(".lg").textContent = p.lang;
      p.tags.forEach(function (t) {
        var s = document.createElement("span");
        s.className = "tag"; s.textContent = t;
        a.querySelector(".repo-foot").appendChild(s);
      });
      $("repos").appendChild(a);
    });
  })();

  /* ---------- skills ---------- */
  (function skills() {
    SKILLS.forEach(function (g) {
      var box = document.createElement("div"); box.className = "sk-group";
      var label = document.createElement("small"); label.textContent = g.group; box.appendChild(label);
      var chips = document.createElement("div"); chips.className = "chips";
      g.items.forEach(function (it) {
        var c = document.createElement("span"); c.className = "chip";
        var dot = document.createElement("i"); dot.style.background = it[1];
        c.appendChild(dot); c.appendChild(document.createTextNode(it[0]));
        chips.appendChild(c);
      });
      box.appendChild(chips);
      $("skillBody").appendChild(box);
    });
  })();

  /* ---------- contact links ---------- */
  (function contact() {
    var IC = {
      linkedin: '<svg viewBox="0 0 24 24" fill="#0A66C2"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>',
      telegram: '<svg viewBox="0 0 24 24" fill="#26A5E4"><path d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z"/></svg>',
      email: '<svg viewBox="0 0 24 24"><path fill="#4285F4" d="M2 8.2V19a1 1 0 001 1h3V10.5z"/><path fill="#34A853" d="M22 8.2V19a1 1 0 01-1 1h-3V10.5z"/><path fill="#FBBC04" d="M18 4.9v5.6l4-2.3V6.3c0-1.5-1.7-2.4-2.9-1.5z"/><path fill="#EA4335" d="M6 10.5V4.9L12 9.4l6-4.5v5.6l-6 4.5z"/><path fill="#C5221F" d="M2 6.3v1.9l4 2.3V4.9L4.9 4.8C3.7 3.9 2 4.8 2 6.3z"/></svg>',
      github: '<svg viewBox="0 0 24 24" fill="#181616"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>'
    };

    var li = PROFILE.linkedin || "";
    var tg = (PROFILE.telegram || "").replace(/^https?:\/\/(t\.me\/)?/i, "").replace(/^@/, "");

    /* [label, text shown, link or "", icon] */
    var links = [
      ["LinkedIn", li ? li.replace(/^https?:\/\//i, "") : "linkedin.com/in/your-name", li ? (/^https?:/i.test(li) ? li : "https://" + li) : "", IC.linkedin],
      ["Telegram", tg ? "@" + tg : "@your-username", tg ? "https://t.me/" + tg : "", IC.telegram],
      ["Email", PROFILE.email || "your-name@gmail.com", PROFILE.email ? "mailto:" + PROFILE.email : "", IC.email],
      ["GitHub", "@" + PROFILE.username, "https://github.com/" + PROFILE.username, IC.github]
    ];

    links.forEach(function (l) {
      var a = document.createElement("a");
      if (l[2]) {
        a.href = l[2]; a.className = "on";
        if (!/^mailto/.test(l[2])) { a.target = "_blank"; a.rel = "noopener"; }
      }
      a.innerHTML = '<span class="ic">' + l[3] + '</span><span class="tx"><small></small><b></b></span>';
      a.querySelector("small").textContent = l[0];
      a.querySelector("b").textContent = l[1];
      $("ctaLinks").appendChild(a);
    });
  })();

  /* ---------- availability: timeline bar + weekly grid ---------- */
  (function timeline() {
    var s1 = $("seg1"), s2 = $("seg2");
    if (CROSS) {
      s1.style.left = pct(START); s1.style.width = (100 - START / 1440 * 100) + "%";
      s2.style.left = "0";        s2.style.width = pct(END);
    } else {
      s1.style.left = pct(START); s1.style.width = ((END - START) / 1440 * 100) + "%";
      s2.hidden = true;
    }
  })();

  /* returns 'f' (full), 'r' (right half), 'l' (left half) or '' for one hour cell.
     dayShift 0 = the day the session starts, 1 = the morning after it. */
  function covers(h, dayShift) {
    var a = h * 60, b = a + 60;
    function overlap(x, y) { return Math.max(0, Math.min(b, y) - Math.max(a, x)); }
    var mins = CROSS ? (dayShift === 0 ? overlap(START, 1440) : overlap(0, END))
                     : (dayShift === 0 ? overlap(START, END) : 0);
    if (mins >= 60) return "f";
    if (mins > 0) return CROSS ? (dayShift === 0 ? "r" : "l") : "r";
    return "";
  }

  (function weekGrid() {
    var wk = $("week"), today = addisNow().day;

    wk.appendChild(document.createElement("span"));                 /* corner cell */
    for (var h = 0; h < 24; h++) {                                  /* hour labels */
      var hl = document.createElement("span");
      hl.className = "h";
      hl.textContent = h % 6 === 0 ? (h === 0 ? "12a" : h === 12 ? "12p" : (h > 12 ? h - 12 : h) + (h < 12 ? "a" : "p")) : "";
      wk.appendChild(hl);
    }

    [1, 2, 3, 4, 5, 6, 0].forEach(function (d) {                    /* Mon ... Sun */
      var dl = document.createElement("span");
      dl.className = "d" + (d === today ? " today" : "");
      dl.textContent = DAYN[d];
      wk.appendChild(dl);

      var prev = (d + 6) % 7;
      for (var h2 = 0; h2 < 24; h2++) {
        var cls = "";
        if (DAYS.indexOf(d) > -1) cls = covers(h2, 0);
        if (!cls && CROSS && DAYS.indexOf(prev) > -1) cls = covers(h2, 1);
        var c = document.createElement("span");
        c.className = "c" + (cls ? " " + cls : "");
        wk.appendChild(c);
      }
    });
  })();

  /* ---------- live status + clock ---------- */
  (function liveStatus() {
    var chip = $("statusChip"), state = $("avState"), sub = $("avSub"), pill = $("livePill");

    function update() {
      var n = addisNow(), m = n.m;
      $("clock").textContent = pad(n.hh) + ":" + pad(n.mm);
      $("now").style.left = pct(m);

      var inWin, left;
      if (CROSS) { inWin = m >= START || m < END; left = m >= START ? 1440 - m + END : END - m; }
      else       { inWin = m >= START && m < END; left = END - m; }

      /* a session belongs to the day it started */
      var sessionDay = (CROSS && m < END) ? (n.day + 6) % 7 : n.day;
      var dayOk = DAYS.indexOf(sessionDay) > -1;

      if (inWin && dayOk) {
        chip.className = "status on"; chip.lastChild.textContent = "Available now";
        state.className = "av-state on"; state.textContent = "Available right now";
        sub.textContent = "Online until " + t12(END) + " EAT, about " + fmtDur(left) + " left.";
        pill.textContent = "Live"; pill.className = "pill live";
      } else {
        var wait = m < START ? START - m : 1440 - m + START;
        chip.className = "status off"; chip.lastChild.textContent = "Back at " + t12(START) + " EAT";
        state.className = "av-state off"; state.textContent = "Offline for now";
        sub.textContent = "Back at " + t12(START) + " EAT, in about " + fmtDur(wait) + ". Leave a message and I will reply then.";
        pill.textContent = "Away"; pill.className = "pill";
      }

      /* the visitor's own local time for my hours */
      try {
        var st = new Date(n.ymd + "T" + pad(HOURS.start[0]) + ":" + pad(HOURS.start[1]) + ":00" + HOURS.offset);
        var len = (CROSS ? 1440 - START + END : END - START) * 60000;
        var en = new Date(st.getTime() + len);
        var f = new Intl.DateTimeFormat(undefined, { hour: "numeric", minute: "2-digit" });
        $("yourTime").textContent = f.format(st) + " – " + f.format(en);
        var tz = new Intl.DateTimeFormat(undefined, { timeZoneName: "short" }).formatToParts(st).filter(function (p) { return p.type === "timeZoneName"; })[0];
        $("tzName").textContent = tz ? "(" + tz.value + ")" : "";
      } catch (e) { $("yourTime").textContent = "--"; }
    }

    update();
    setInterval(update, 30000);
  })();

  /* ---------- nav highlight on scroll ---------- */
  (function navHighlight() {
    if (!("IntersectionObserver" in window)) return;
    var map = {};
    Array.prototype.forEach.call(document.querySelectorAll(".top-nav a"), function (a) { map[a.getAttribute("href").slice(1)] = a; });
    var io = new IntersectionObserver(function (entries) {
      entries.forEach(function (e) {
        if (e.isIntersecting) Object.keys(map).forEach(function (k) { map[k].classList.toggle("on", k === e.target.id); });
      });
    }, { rootMargin: "-30% 0px -60% 0px" });
    Object.keys(map).forEach(function (id) { var s = $(id); if (s) io.observe(s); });
  })();
})();

</script>
</body>
</html>
