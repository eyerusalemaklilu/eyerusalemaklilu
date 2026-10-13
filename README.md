<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Eyerusalem Aklilu – Website Developer</title>
<meta name="description" content="Website developer building pages and web applications, from the first layout to launch.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@500;700&family=Plus+Jakarta+Sans:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#0b100d; --bg2:#16221b; --card:#111a15; --line:#223128;
    --text:#e8efe9; --muted:#93a39a; --amber:#f6a900; --green:#3ddc84; --blue:#6ea8ff; --purple:#a259ff;
    --sans:'Plus Jakarta Sans','Segoe UI',Helvetica,Arial,sans-serif;
    --mono:'JetBrains Mono','SFMono-Regular',Consolas,'Liberation Mono',Menlo,monospace;
  }
  *{box-sizing:border-box}
  html{-webkit-text-size-adjust:100%}
  body{margin:0;background:var(--bg);color:var(--text);font-family:var(--sans);line-height:1.4}
  .page{max-width:900px;margin:0 auto;padding:24px 16px 56px;display:flex;flex-direction:column;gap:20px}
  svg{display:block}
  .label{font-size:13px;font-weight:600;color:var(--muted);margin:12px 0 -8px 2px}
  .fade{opacity:0;animation:fade .45s forwards;animation-delay:var(--d,0s)}
  @keyframes fade{to{opacity:1}}

  /* ---------- HERO ---------- */
  .hero{position:relative;overflow:hidden;border:2px solid var(--line);border-radius:24px;
    background:radial-gradient(circle at 90% 5%,rgba(246,169,0,.22),transparent 60%),
               radial-gradient(circle at 5% 95%,rgba(47,122,88,.35),transparent 60%),
               linear-gradient(135deg,#0b100d,#16221b);
    padding:40px 36px;display:flex;align-items:center;gap:36px}
  .hero::after{content:"</>";position:absolute;right:24px;bottom:-18px;font:700 clamp(70px,16vw,120px)/1 var(--mono);color:var(--amber);opacity:.07;pointer-events:none}
  .wave{position:relative;flex:0 0 auto;width:150px;height:150px;display:grid;place-items:center}
  .wave svg{width:110px;height:auto;position:relative;z-index:1}
  .ring{position:absolute;inset:0;margin:auto;width:116px;height:116px;border:2px solid var(--amber);border-radius:50%;opacity:0;animation:ring 2.6s infinite}
  .ring.r2{animation-delay:1.3s}
  @keyframes ring{0%{transform:scale(1);opacity:.38}100%{transform:scale(1.8);opacity:0}}
  .hero-text{min-width:0;position:relative;z-index:1}
  .hi{font:500 19px var(--mono);color:var(--amber);margin:0 0 6px}
  .name{margin:0;font:700 clamp(22px,6.4vw,50px)/1.15 var(--mono);color:var(--text);white-space:nowrap}
  .typed{display:inline-block;overflow:hidden;vertical-align:bottom;width:0;border-right:.08em solid var(--amber);
    animation:type 9s steps(17,end) infinite,blink 1s steps(1) infinite}
  @keyframes type{0%,5.5%{width:0}25%,71%{width:17ch}90%,100%{width:0}}
  @keyframes blink{50%{border-right-color:transparent}}
  .role{font-size:26px;font-weight:800;margin:14px 0 4px}
  .tag{font-size:16px;color:var(--muted);margin:0}

  /* ---------- PROJECTS ---------- */
  .stats{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}
  .stat{position:relative;background:var(--card);border:2px solid var(--line);border-radius:18px;padding:22px 24px 20px 30px;overflow:hidden}
  .stat::before{content:"";position:absolute;left:1px;top:26px;bottom:26px;width:5px;border-radius:3px;background:var(--c)}
  .stat .ic{position:absolute;right:18px;top:22px}
  .stat .num{font-size:64px;font-weight:800;line-height:1;color:var(--c)}
  .stat b{display:block;font-size:15px;margin-top:14px}
  .stat span{font-size:12.5px;color:var(--muted)}
  .about{position:relative;background:linear-gradient(90deg,rgba(246,169,0,.12),rgba(246,169,0,0) 60%),var(--bg2);
    border:2px solid var(--line);border-radius:18px;padding:28px 32px;display:flex;align-items:center;gap:28px}
  .about .code{font:700 46px var(--mono);color:var(--amber);flex:0 0 auto}
  .about h2{margin:0 0 8px;font-size:26px;font-weight:800}
  .about p{margin:0 0 14px;color:var(--muted);font-size:15px}
  .chips{display:flex;flex-wrap:wrap;gap:10px}
  .chip{background:var(--bg2);border:1.5px solid var(--line);border-radius:999px;padding:5px 16px;font-size:13px;font-weight:600}

  /* ---------- SKILLS ---------- */
  .tools{display:grid;grid-template-columns:repeat(5,1fr);gap:16px}
  .tool{background:var(--card);border:2px solid var(--line);border-radius:18px;padding:22px 8px 16px;text-align:center}
  .tool svg{width:48px;height:48px;margin:0 auto 14px}
  .tool b{font-size:15px;font-weight:700}
  .does{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}
  .do{position:relative;background:var(--card);border:2px solid var(--line);border-radius:18px;padding:24px 24px 24px 28px}
  .do::before{content:"";position:absolute;left:1px;top:26px;bottom:26px;width:5px;border-radius:3px;background:var(--c)}
  .do svg{width:36px;height:36px;margin-bottom:16px}
  .do b{display:block;font-size:15px;font-weight:800;margin-bottom:6px}
  .do span{font-size:12.5px;color:var(--muted)}

  /* ---------- AVAILABILITY ---------- */
  .card{background:var(--card);border:2px solid var(--line);border-radius:18px;padding:20px}
  .sec-title{font-size:28px;font-weight:800;margin:20px 0 0}
  .sub{margin:0;color:var(--muted);font-size:15px}
  .legend{display:flex;flex-wrap:wrap;gap:8px 16px;margin:0 0 14px;font-size:13px;color:var(--muted)}
  .legend i{display:inline-block;width:14px;height:14px;border-radius:4px;margin-right:6px;vertical-align:-2px}
  #av-chart svg{width:100%;height:auto}
  .notes{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
  .note{background:var(--card);border:2px solid var(--line);border-left:5px solid var(--purple);border-radius:14px;padding:14px 16px;font-size:13.5px;color:var(--muted)}
  .note b{display:block;color:var(--text);font-size:15px;margin-bottom:4px}
  .form h3{margin:0 0 4px;font-size:20px;font-weight:800}
  .form p{margin:0 0 16px;color:var(--muted);font-size:14px}
  .grid{display:grid;grid-template-columns:1fr 1fr;gap:14px}
  .grid .full{grid-column:1/-1}
  label{display:block;font-size:12.5px;font-weight:600;color:var(--muted);margin-bottom:6px}
  input,select,textarea{width:100%;background:#0b120e;color:var(--text);border:2px solid var(--line);border-radius:12px;padding:12px 13px;font:inherit;font-size:16px;outline:none}
  input:focus,select:focus,textarea:focus{border-color:var(--purple)}
  textarea{min-height:110px;resize:vertical}
  button{margin-top:16px;background:var(--purple);color:#fff;border:0;border-radius:12px;padding:13px 26px;font:inherit;font-weight:800;font-size:15px;cursor:pointer}
  button:hover{filter:brightness(1.1)}
  .msg{margin-top:12px;font-size:13.5px;color:#c9a3ff;min-height:20px}

  /* ---------- TABLET ---------- */
  @media (max-width:760px){
    .stats{grid-template-columns:1fr}
    .stat{padding:18px 20px 16px 28px}
    .stat .num{font-size:52px}
    .does{grid-template-columns:1fr}
    .tools{grid-template-columns:repeat(3,1fr)}
    .notes{grid-template-columns:1fr}
    .about{flex-direction:column;align-items:flex-start;gap:12px;padding:24px 22px}
    .about .code{font-size:38px}
    .about h2{font-size:22px}
  }
  /* ---------- PHONE ---------- */
  @media (max-width:560px){
    .page{padding:14px 12px 40px;gap:16px}
    .hero{flex-direction:column;text-align:center;padding:28px 18px;gap:6px}
    .wave{width:120px;height:120px}.wave svg{width:84px}.ring{width:92px;height:92px}
    .hi{font-size:16px}
    .role{font-size:21px;margin-top:10px}
    .tag{font-size:14px}
    .name{display:flex;justify-content:center}
    .grid{grid-template-columns:1fr}
    .sec-title{font-size:23px}
    .card{padding:14px}
    .chips{gap:8px}
  }
  @media (max-width:400px){
    .tools{grid-template-columns:repeat(2,1fr)}
    .tool:last-child{grid-column:1/-1}
  }
  @media (prefers-reduced-motion:reduce){
    *{animation-duration:.01ms!important;animation-iteration-count:1!important}
    .typed{width:17ch}
  }
</style>
</head>
<body>
<main class="page">

  <!-- ================= HERO ================= -->
  <section class="hero" aria-label="Introduction">
    <div class="wave">
      <span class="ring"></span><span class="ring r2"></span>
      <svg viewBox="0 0 110 130" aria-hidden="true">
        <defs><linearGradient id="skin" gradientUnits="userSpaceOnUse" x1="0" y1="0" x2="0" y2="125"><stop offset="0" stop-color="#ffd978"/><stop offset="1" stop-color="#f6a900"/></linearGradient></defs>
        <g>
          <animateTransform attributeName="transform" type="rotate" dur="2.6s" repeatCount="indefinite" keyTimes="0;0.1;0.2;0.3;0.4;0.5;0.6;1" values="0 55 122;16 55 122;-9 55 122;14 55 122;-7 55 122;10 55 122;0 55 122;0 55 122"/>
          <rect x="4" y="68" width="18" height="50" rx="9" fill="url(#skin)" transform="rotate(-36 22 108)"/>
          <rect x="20" y="52" width="70" height="70" rx="22" fill="url(#skin)"/>
          <rect x="22" y="14" width="15" height="70" rx="7.5" fill="url(#skin)"/>
          <rect x="39" y="3" width="15" height="80" rx="7.5" fill="url(#skin)"/>
          <rect x="56" y="9" width="15" height="74" rx="7.5" fill="url(#skin)"/>
          <rect x="73" y="24" width="15" height="60" rx="7.5" fill="url(#skin)"/>
          <path d="M38.5 40v34M55.5 40v34M72.5 46v28" stroke="#b97a00" stroke-opacity=".25" stroke-width="1.5" stroke-linecap="round"/>
        </g>
      </svg>
    </div>
    <div class="hero-text">
      <p class="hi">Hi there, I'm</p>
      <h1 class="name"><span class="typed">Eyerusalem Aklilu</span></h1>
      <p class="role">Website developer</p>
      <p class="tag">I build pages and web applications, from the first layout to launch.</p>
    </div>
  </section>

  <!-- ================= PROJECTS ================= -->
  <section class="stats" aria-label="Projects">
    <div class="stat" style="--c:var(--green)">
      <svg class="ic" width="24" height="24" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10" fill="none" stroke="#3ddc84" stroke-width="2"/><path d="M7 12.5l3.2 3.2L17 9" fill="none" stroke="#3ddc84" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"/></svg>
      <div class="num count" data-to="6" data-delay="400">0</div>
      <b>Projects completed</b><span>Websites and web applications</span>
    </div>
    <div class="stat" style="--c:var(--amber)">
      <svg class="ic" width="24" height="24" viewBox="0 0 24 24"><path d="M13 2L4 14h7l-1 8 9-12h-7z" fill="#f6a900"/></svg>
      <div class="num count" data-to="1" data-delay="800">0</div>
      <b>Automation built</b><span>Slack and Jira task tracker</span>
    </div>
    <div class="stat" style="--c:var(--blue)">
      <svg class="ic" width="24" height="24" viewBox="0 0 24 24"><circle cx="12" cy="12" r="9" fill="none" stroke="#223128" stroke-width="3"/><path d="M12 3a9 9 0 019 9" fill="none" stroke="#6ea8ff" stroke-width="3" stroke-linecap="round"><animateTransform attributeName="transform" type="rotate" values="0 12 12;360 12 12" dur="1.6s" repeatCount="indefinite"/></path></svg>
      <div class="num count" data-to="1" data-delay="1100">0</div>
      <b>In progress</b><span>Currently building</span>
    </div>
  </section>

  <section class="about">
    <div class="code">&lt;/&gt;</div>
    <div>
      <h2>I'm a website developer</h2>
      <p>I design and build pages and web applications, and connect them to the tools your team uses.</p>
      <div class="chips"><span class="chip">Pages</span><span class="chip">Web apps</span><span class="chip">Automation</span></div>
    </div>
  </section>

  <!-- ================= SKILLS ================= -->
  <div class="label">Tools and platforms</div>
  <section class="tools" aria-label="Tools and platforms">
    <div class="tool fade" style="--d:.15s">
      <svg viewBox="0 0 24 24"><rect x="2" y="2" width="20" height="20" rx="2" fill="#F7DF1E"/><text x="21" y="20" text-anchor="end" font-family="Plus Jakarta Sans,Segoe UI,Arial,sans-serif" font-size="10.5" font-weight="800" fill="#1a1a1a">JS</text></svg>
      <b>JavaScript</b></div>
    <div class="tool fade" style="--d:.27s">
      <svg viewBox="0 0 24 24"><path d="M3 2l1.8 19.2L12 23l7.2-1.8L21 2z" fill="#E34F26"/><path d="M12 3.6v18l5.9-1.6L19.4 3.6z" fill="#EF652A"/><text x="12" y="17" text-anchor="middle" font-family="Plus Jakarta Sans,Segoe UI,Arial,sans-serif" font-size="12.5" font-weight="800" fill="#fff">5</text></svg>
      <b>HTML</b></div>
    <div class="tool fade" style="--d:.39s">
      <svg viewBox="0 0 24 24"><path d="M3 2l1.8 19.2L12 23l7.2-1.8L21 2z" fill="#1572B6"/><path d="M12 3.6v18l5.9-1.6L19.4 3.6z" fill="#33A9DC"/><text x="12" y="17" text-anchor="middle" font-family="Plus Jakarta Sans,Segoe UI,Arial,sans-serif" font-size="12.5" font-weight="800" fill="#fff">3</text></svg>
      <b>CSS</b></div>
    <div class="tool fade" style="--d:.51s">
      <svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10.5" fill="#21759B"/><circle cx="12" cy="12" r="8.6" fill="none" stroke="#fff" stroke-width=".9" opacity=".55"/><text x="12" y="17" text-anchor="middle" font-family="Georgia,'Times New Roman',serif" font-size="14" font-weight="700" fill="#fff">W</text></svg>
      <b>WordPress</b></div>
    <div class="tool fade" style="--d:.63s">
      <svg viewBox="0 0 24 24"><rect x="1.5" y="1.5" width="21" height="21" rx="6" fill="#4353FF"/><polyline points="5.2,8.6 8.4,16 12,10 15.6,16 18.8,8.6" fill="none" stroke="#fff" stroke-width="2.3" stroke-linecap="round" stroke-linejoin="round"/></svg>
      <b>Webflow</b></div>
    <div class="tool fade" style="--d:.75s">
      <svg viewBox="0 0 24 24"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12" fill="#e8efe9"/></svg>
      <b>GitHub</b></div>
  </section>

  <div class="label">What I do</div>
  <section class="does" aria-label="What I do">
    <div class="do fade" style="--c:#a259ff;--d:1.1s">
      <svg viewBox="0 0 36 36"><g transform="scale(1.5)"><rect x="5" y="6.5" width="14" height="11" rx="1" fill="none" stroke="#a259ff" stroke-width="1.8"/><g fill="#a259ff"><rect x="3" y="4.5" width="4" height="4" rx="1"/><rect x="17" y="4.5" width="4" height="4" rx="1"/><rect x="3" y="15.5" width="4" height="4" rx="1"/><rect x="17" y="15.5" width="4" height="4" rx="1"/></g></g></svg>
      <b>UI/UX</b><span>Clear layouts and flows that are easy to scan and use.</span></div>
    <div class="do fade" style="--c:#f6a900;--d:1.3s">
      <svg viewBox="0 0 36 36"><g transform="scale(1.5)"><rect x="2.5" y="4" width="19" height="16" rx="2.5" fill="none" stroke="#f6a900" stroke-width="1.8"/><path d="M2.5 9h19" stroke="#f6a900" stroke-width="1.8"/><path d="M9.5 12.5l-2.2 2.3 2.2 2.3M14.5 12.5l2.2 2.3-2.2 2.3" fill="none" stroke="#f6a900" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/></g></svg>
      <b>Web design and development</b><span>Pages and web applications, from first layout to launch.</span></div>
    <div class="do fade" style="--c:#3ddc84;--d:1.5s">
      <svg viewBox="0 0 36 36"><g transform="scale(1.5)"><rect x="3" y="3.5" width="18" height="5" rx="1.5" fill="#3ddc84"/><rect x="3" y="11" width="8" height="9.5" rx="1.5" fill="none" stroke="#3ddc84" stroke-width="1.8"/><rect x="13.5" y="11" width="7.5" height="4" rx="1.5" fill="none" stroke="#3ddc84" stroke-width="1.8"/><rect x="13.5" y="17" width="7.5" height="3.5" rx="1.5" fill="none" stroke="#3ddc84" stroke-width="1.8"/></g></svg>
      <b>Content organization</b><span>Structuring pages so information is easy to find.</span></div>
  </section>

  <!-- ================= AVAILABILITY ================= -->
  <section id="availability" aria-label="Availability" style="display:flex;flex-direction:column;gap:16px">
    <h2 class="sec-title">My Availability</h2>
    <p class="sub">Times are shown in East Africa Time (EAT, UTC+3). Purple bars show when I'm available.</p>

    <div class="card">
      <div class="legend">
        <span><i style="background:#a259ff"></i>Freelance jobs</span>
        <span><i style="background:#d9bcff"></i>Remote / full-time / contract</span>
      </div>
      <div id="av-chart" role="img" aria-label="Weekly availability schedule"></div>
    </div>

    <div class="notes" id="av-notes"></div>

    <div class="card form">
      <h3>Need a different time?</h3>
      <p>Tell me what works for you and I'll confirm by email.</p>
      <form id="av-form" novalidate>
        <div class="grid">
          <div><label for="av-name">Your name</label><input id="av-name" autocomplete="name" required></div>
          <div><label for="av-email">Your email</label><input id="av-email" type="email" autocomplete="email" required></div>
          <div class="full"><label for="av-title">Your title / project title (used as the email subject)</label>
            <input id="av-title" placeholder="e.g. Marketing Manager – Website redesign" required></div>
          <div><label for="av-type">Job type</label>
            <select id="av-type"><option>Freelance job</option><option>Remote job</option><option>Full-time job</option><option>Contract work</option></select></div>
          <div><label for="av-time">Your preferred day &amp; time</label><input id="av-time" placeholder="e.g. Wednesday 9:00 AM (your timezone)"></div>
          <div class="full"><label for="av-details">Details</label><textarea id="av-details" placeholder="Tell me about the work..."></textarea></div>
        </div>
        <button type="submit">Send</button>
        <div class="msg" id="av-msg" role="status"></div>
      </form>
    </div>
  </section>

</main>

<script>
/* ---- counters (0 → N, same stepped feel as before) ---- */
document.querySelectorAll('.count').forEach(function(el){
  var to=+el.dataset.to,d=+el.dataset.delay,n=0;
  setTimeout(function(){
    var t=setInterval(function(){n++;el.textContent=n;if(n>=to)clearInterval(t);},120);
  },d);
});

/* ---- availability ---- */
(function(){
  /* ===== EDIT YOUR HOURS HERE (24h "HH:MM"; end earlier than start = after midnight) ===== */
  var FREELANCE = {start:'13:00', end:'01:00'};   // Mon–Sat
  var REMOTE    = {start:'16:30', end:'01:30'};   // Mon–Sat, also full-time & contract
  var SUNDAY    = {start:'09:30', end:'13:00'};   // Sunday (all job types)
  var DAYS = ['Mon','Tue','Wed','Thu','Fri','Sat','Sun'];
  /* ======================================================================================= */

  function m(t){var p=t.split(':');return (+p[0])*60+(+p[1]);}
  function span(o){var s=m(o.start),e=m(o.end);if(e<=s)e+=1440;return [s,e];}
  function fmt(mins){var h=Math.floor(mins/60)%24,mm=mins%60,ap=h>=12?'PM':'AM',h12=h%12||12;
    return h12+(mm?':'+(mm<10?'0':'')+mm:':00')+' '+ap;}
  function range(o){var s=span(o);return fmt(s[0])+' – '+fmt(s[1]);}

  var box=document.getElementById('av-chart');
  var F="font-family=\"'Plus Jakarta Sans','Segoe UI',Helvetica,Arial,sans-serif\"";

  function draw(){
    var W=Math.max(box.clientWidth,240);
    var small=W<520;
    var AX0=540,AX1=1560,step=small?240:120;
    var L=small?38:62,R=W-(small?8:10),rowH=small?44:46,top=30,fs=small?10.5:11;
    var H=top+DAYS.length*rowH+8,sc=(R-L)/(AX1-AX0);
    function x(v){return L+(v-AX0)*sc;}
    var s='<svg viewBox="0 0 '+W+' '+H+'" width="'+W+'" height="'+H+'" xmlns="http://www.w3.org/2000/svg">';
    for(var t=AX0;t<=AX1;t+=step){
      s+='<line x1="'+x(t)+'" y1="'+(top-6)+'" x2="'+x(t)+'" y2="'+(H-6)+'" stroke="#223128" stroke-width="1.5"/>';
      var anchor=t===AX0?'start':(t+step>AX1?'end':'middle');
      s+='<text x="'+x(t)+'" y="14" text-anchor="'+anchor+'" '+F+' font-size="'+fs+'" fill="#93a39a">'+fmt(t).replace(':00','')+'</text>';
    }
    function bar(o,y,h,fill){
      var a=span(o),x0=x(Math.max(a[0],AX0)),x1=x(Math.min(a[1],AX1));
      return '<rect x="'+x0+'" y="'+y+'" width="'+(x1-x0)+'" height="'+h+'" rx="'+(h/2)+'" fill="'+fill+'"/>';
    }
    DAYS.forEach(function(d,i){
      var y=top+i*rowH;
      s+='<text x="2" y="'+(y+27)+'" '+F+' font-size="'+(small?12.5:14)+'" font-weight="800" fill="#e8efe9">'+d+'</text>';
      if(d==='Sun'){
        s+=bar(SUNDAY,y+8,26,'#a259ff');
        var a=span(SUNDAY),lbl=small?'Open':'All job types · '+range(SUNDAY);
        s+='<text x="'+(x(a[0])+12)+'" y="'+(y+25)+'" '+F+' font-size="'+(small?11:12)+'" font-weight="700" fill="#fff">'+lbl+'</text>';
      }else{
        s+=bar(FREELANCE,y+4,17,'#a259ff');
        s+=bar(REMOTE,y+24,17,'#d9bcff');
      }
    });
    box.innerHTML=s+'</svg>';
  }
  draw();
  var rt;window.addEventListener('resize',function(){clearTimeout(rt);rt=setTimeout(draw,120);});

  document.getElementById('av-notes').innerHTML=
    '<div class="note"><b>Freelance jobs</b>Mon–Sat · '+range(FREELANCE)+'</div>'+
    '<div class="note"><b>Remote, full-time &amp; contract</b>Mon–Sat · '+range(REMOTE)+'</div>'+
    '<div class="note"><b>Sunday</b>'+range(SUNDAY)+'</div>';

  function to(){return ['aklilueyerusalem05','gmail.com'].join('@');}

  document.getElementById('av-form').addEventListener('submit',function(e){
    e.preventDefault();
    var g=function(id){return document.getElementById(id).value.trim();};
    var name=g('av-name'),mail=g('av-email'),title=g('av-title'),type=document.getElementById('av-type').value,
        time=g('av-time'),details=g('av-details'),msg=document.getElementById('av-msg');
    if(!name||!mail||!title){msg.textContent='Please fill in your name, email and title.';return;}
    if(!/^\S+@\S+\.\S+$/.test(mail)){msg.textContent='Please enter a valid email address.';return;}
    var subject='[GitHub] Availability request – '+title;
    var body='Hello,\n\nI would like to confirm your availability.\n\n'+
      'Source: GitHub portfolio – availability form\n------------------------------------------\n'+
      'Name: '+name+'\nEmail: '+mail+'\nTitle / Project: '+title+'\nJob type: '+type+'\n'+
      'Preferred day & time: '+(time||'Not specified')+'\n\nDetails:\n'+(details||'—')+
      '\n\n------------------------------------------\nPlease confirm if this time works.\n\nThank you,\n'+name;
    window.location.href='mailto:'+to()+'?subject='+encodeURIComponent(subject)+'&body='+encodeURIComponent(body);
    msg.textContent='Opening your email app with the message ready — press send there to confirm.';
  });
})();
</script>
</body>
</html>
