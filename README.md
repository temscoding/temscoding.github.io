# temscoding.github.io
<!DOCTYPE html>
<html lang="en-GB">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="theme-color" content="#f6f1e7">
<title>Pause · A calm space for students</title>
<style>
:root{
  --cream:#f6f1e7; --card:#fffdf8; --sage:#9caf88; --sage-d:#5f7a55; --sage-l:#e3ebd9;
  --ink:#2f3330; --muted:#6a7068; --line:#e6e0d1; --alert:#9b4a3c;
  --shadow:0 2px 4px rgba(47,51,48,.04),0 8px 24px rgba(47,51,48,.07);
  --serif:Georgia,"Iowan Old Style","Palatino Linotype",serif;
  --sans:system-ui,-apple-system,"Segoe UI",Roboto,Helvetica,Arial,sans-serif;
}
*{box-sizing:border-box;margin:0}
html{-webkit-text-size-adjust:100%}
body{background:var(--cream);color:var(--ink);font:16px/1.55 var(--sans);padding:env(safe-area-inset-top) 0 env(safe-area-inset-bottom)}
main{max-width:480px;margin:0 auto;padding:28px 16px 48px;display:flex;flex-direction:column;gap:16px}
header{padding:8px 6px 8px}
header h1{font:400 34px/1.15 var(--serif);letter-spacing:-.01em}
header p{color:var(--muted);margin-top:6px}
.card{background:var(--card);border-radius:24px;padding:22px;box-shadow:var(--shadow)}
h2{font:600 17px/1.3 var(--sans);margin-bottom:4px}
.sub{color:var(--muted);font-size:14px;margin-bottom:16px}
button,summary,a.link{font:inherit;-webkit-tap-highlight-color:transparent}
button{cursor:pointer;border:0;min-height:52px;padding:0 22px;border-radius:999px;background:var(--sage-d);color:#fff;font-weight:600;transition:background .2s,transform .15s}
button:active{transform:scale(.97)}
button.ghost{background:var(--sage-l);color:var(--sage-d)}
button:hover{background:#4f6746} button.ghost:hover{background:#d6e2c9}
:focus-visible{outline:3px solid var(--sage-d);outline-offset:3px}
.full{width:100%}

/* Affirmation */
.affirm{background:var(--sage-l)}
#affirmText{font:400 25px/1.35 var(--serif);min-height:5.4em;display:flex;align-items:center;transition:opacity .35s}
#affirmText.fade{opacity:0}
.affirm button{margin-top:14px}

/* Breathing */
.stage{display:grid;place-items:center;height:240px;margin:6px 0 14px}
.ring{grid-area:1/1;width:210px;height:210px;border-radius:50%;border:2px dashed var(--sage)}
#orb{grid-area:1/1;width:210px;height:210px;border-radius:50%;background:radial-gradient(circle at 35% 30%,#c9d8b8,var(--sage));transform:scale(.6);display:grid;place-items:center;transition:transform 4s ease-in-out}
#orbLabel{grid-area:1/1;text-align:center;color:var(--ink);font-weight:600;pointer-events:none}
#orbLabel b{display:block;font:400 34px/1.1 var(--serif)}
.bar{height:6px;border-radius:6px;background:var(--sage-l);overflow:hidden;margin-bottom:16px}
.bar i{display:block;height:100%;width:0;background:var(--sage-d);transition:width 1s linear}

/* Mood */
.moods{display:grid;grid-template-columns:repeat(5,1fr);gap:6px;margin-bottom:18px}
.mood{min-height:72px;padding:6px 0;border-radius:18px;background:var(--cream);color:var(--ink);display:flex;flex-direction:column;align-items:center;justify-content:center;gap:2px;font-size:11px;font-weight:500;border:2px solid transparent}
.mood:hover{background:var(--sage-l)}
.mood span{font-size:26px;line-height:1}
.mood[aria-pressed="true"]{background:var(--sage-l);border-color:var(--sage-d)}
.prompt{font:italic 400 18px/1.4 var(--serif);margin-bottom:10px}
textarea{width:100%;min-height:120px;resize:vertical;padding:14px;border-radius:18px;border:1.5px solid var(--line);background:#fff;font:16px/1.5 var(--sans);color:var(--ink);margin-bottom:12px}
textarea:focus{outline:none;border-color:var(--sage-d);box-shadow:0 0 0 3px var(--sage-l)}
#msg{min-height:1.5em;font-size:14px;color:var(--sage-d);margin-top:8px;text-align:center}
#msg.err{color:var(--alert)}
details{margin-top:14px;border-top:1px solid var(--line);padding-top:4px}
summary{min-height:52px;display:flex;align-items:center;justify-content:space-between;cursor:pointer;font-weight:600;list-style:none}
summary::-webkit-details-marker{display:none}
summary::after{content:"";width:9px;height:9px;border-right:2px solid var(--muted);border-bottom:2px solid var(--muted);transform:rotate(45deg);transition:transform .25s;margin-right:4px}
details[open] summary::after{transform:rotate(-135deg)}
.entry{padding:12px 0;border-bottom:1px solid var(--line)}
.entry:last-of-type{border-bottom:0}
.entry .meta{font-size:13px;color:var(--muted);display:flex;justify-content:space-between;gap:8px}
.entry p{margin-top:4px;white-space:pre-wrap;overflow-wrap:anywhere}
.entry .pq{font-size:13px;font-style:italic;color:var(--muted);margin-top:4px}
.empty{color:var(--muted);padding:8px 0 12px}
.small{min-height:44px;font-size:14px;margin-top:10px}

/* Playlist */
.player{border-radius:16px;overflow:hidden;background:var(--sage-l)}
.player iframe{display:block;width:100%;height:152px;border:0}

/* Support */
.help{display:flex;flex-direction:column;gap:10px}
.help a{display:flex;flex-direction:column;gap:2px;min-height:60px;justify-content:center;padding:12px 16px;border-radius:18px;background:var(--cream);color:var(--ink);text-decoration:none;transition:background .2s}
.help a:hover{background:var(--sage-l)}
.help strong{font-weight:600}
.help span{font-size:14px;color:var(--muted)}
.help .num{color:var(--sage-d);font-weight:600}
.urgent{margin-top:14px;font-size:14px;color:var(--muted)}
.urgent a{color:var(--alert);font-weight:600}
footer{text-align:center;color:var(--muted);font-size:13px;padding:6px 12px}

@media (prefers-reduced-motion:reduce){
  #orb,.bar i,#affirmText,summary::after{transition-duration:.01s!important}
}
</style>
</head>
<body>
<main>
  <header>
    <h1 id="greeting">Take a moment.</h1>
    <p>You’re here, and that’s a good first step.</p>
  </header>

  <!-- Affirmation -->
  <section class="card affirm" aria-labelledby="h-aff">
    <h2 id="h-aff">Today’s affirmation</h2>
    <p id="affirmText" aria-live="polite"></p>
    <button id="affirmBtn" class="full">New affirmation</button>
  </section>

  <!-- Breathing -->
  <section class="card" aria-labelledby="h-br">
    <h2 id="h-br">One-minute breathing</h2>
    <p class="sub">In for 4, hold for 4, out for 4. Five rounds.</p>
    <div class="stage">
      <div class="ring" aria-hidden="true"></div>
      <div id="orb" aria-hidden="true"></div>
      <div id="orbLabel" role="status" aria-live="polite"><b>Ready</b><span id="orbSub">Tap start when you are</span></div>
    </div>
    <div class="bar" aria-hidden="true"><i id="bar"></i></div>
    <button id="breathBtn" class="full">Start</button>
  </section>

  <!-- Mood + journal -->
  <section class="card" aria-labelledby="h-mood">
    <h2 id="h-mood">How are you feeling?</h2>
    <p class="sub">Pick the one that’s closest. There’s no wrong answer.</p>
    <div class="moods" id="moods" role="group" aria-label="Mood"></div>
    <p class="prompt" id="prompt"></p>
    <label for="note" class="sr" style="position:absolute;left:-9999px">Your thoughts</label>
    <textarea id="note" placeholder="Write as much or as little as you like…"></textarea>
    <button id="saveBtn" class="full">Save entry</button>
    <p id="msg" role="status" aria-live="polite"></p>
    <details id="hist">
      <summary>Past check-ins <span id="count" style="font-weight:400;color:var(--muted);margin-left:auto;margin-right:12px"></span></summary>
      <div id="list"></div>
      <button id="clearBtn" class="ghost small" hidden>Clear all entries</button>
    </details>
    <p class="sub" style="margin:12px 0 0;font-size:13px">Entries stay on this device only. They’re never sent anywhere.</p>
  </section>

  <!-- Playlist -->
  <section class="card" aria-labelledby="h-pl">
    <h2 id="h-pl">Calm and focus playlist</h2>
    <p class="sub">Soft lo-fi for studying or winding down.</p>
    <div class="player">
      <!-- To use your own playlist: swap the ID after /playlist/ to change playlist -->
      <iframe title="Spotify lo-fi playlist" loading="lazy"
        src="https://open.spotify.com/embed/playlist/0vvXsWCC9xrXsKd4FyS8kM?utm_source=generator&theme=0"
        allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"></iframe>
    </div>
  </section>

  <!-- UK support -->
  <section class="card" aria-labelledby="h-help">
    <h2 id="h-help">Need to talk to someone?</h2>
    <p class="sub">Free, confidential UK support. Tap to call, text or visit.</p>
    <div class="help">
      <a href="tel:08001111"><strong>Childline</strong><span>Under 19s, any worry. Call <span class="num">0800 1111</span></span></a>
      <a href="sms:85258"><strong>Shout</strong><span>24/7 text support. Text <span class="num">SHOUT</span> to <span class="num">85258</span></span></a>
      <a href="https://www.youngminds.org.uk/young-person/" target="_blank" rel="noopener"><strong>YoungMinds</strong><span>Advice and the YoungMinds Textline: text <span class="num">YM</span> to <span class="num">85258</span></span></a>
      <a href="tel:116123"><strong>Samaritans</strong><span>Listening, day or night. Call <span class="num">116 123</span></span></a>
    </div>
    <p class="urgent">In immediate danger or at risk of harm? Call <a href="tel:999">999</a>.</p>
  </section>

  <footer>Not a substitute for professional help. Be kind to yourself today.</footer>
</main>

<script>
(function(){
  "use strict";
  var $ = function(id){return document.getElementById(id)};

  /* Safe storage */
  var store = {
    get:function(k){try{return JSON.parse(localStorage.getItem(k))}catch(e){return null}},
    set:function(k,v){try{localStorage.setItem(k,JSON.stringify(v));return true}catch(e){return false}}
  };

  /* Greeting */
  var h = new Date().getHours();
  $("greeting").textContent = h<12 ? "Good morning." : h<18 ? "Good afternoon." : "Good evening.";

  /* Affirmations */
  var affirmations = [
    "You are allowed to take things one step at a time.",
    "Your worth is not measured by your grades.",
    "It’s okay to ask for help. That takes strength.",
    "You have handled hard days before, and you can handle this one.",
    "Rest is productive. You’re allowed to recharge.",
    "Progress counts, even when it’s small.",
    "You don’t have to have everything figured out yet.",
    "Mistakes are how learning happens. You’re learning.",
    "You belong here, exactly as you are.",
    "Your feelings are valid, even the messy ones.",
    "You can do hard things, one breath at a time.",
    "Comparing yourself to others won’t help you grow. Focus on your own path.",
    "You are more than your to-do list.",
    "Today, ‘good enough’ is enough.",
    "It’s okay to say no to protect your energy.",
    "You’ve already come further than you think.",
    "Being kind to yourself is part of the work.",
    "Bad days don’t cancel out your effort.",
    "You are allowed to change your mind and grow.",
    "Your best looks different every day, and that’s fine.",
    "Small breaks help you do your best work.",
    "You are not behind. You’re on your own timeline.",
    "You deserve the same patience you give your friends.",
    "This feeling is temporary. It will pass."
  ];
  var aIdx = (function(){var d=new Date();return (d.getFullYear()*366+Math.floor((d-new Date(d.getFullYear(),0,0))/864e5))%affirmations.length})();
  var aEl = $("affirmText");
  aEl.textContent = affirmations[aIdx];
  $("affirmBtn").addEventListener("click", function(){
    var n; do { n = Math.floor(Math.random()*affirmations.length); } while(n===aIdx);
    aIdx = n;
    aEl.classList.add("fade");
    setTimeout(function(){aEl.textContent = affirmations[aIdx]; aEl.classList.remove("fade")}, 300);
  });

  /* Breathing: 4-4-4 for 60 seconds */
  var orb=$("orb"), lab=$("orbLabel").firstElementChild, sub=$("orbSub"), bar=$("bar"), bBtn=$("breathBtn");
  var TOTAL=60, t=0, timer=null, running=false;
  var phases=[{n:"Breathe in",s:1},{n:"Hold",s:null},{n:"Breathe out",s:.6}];
  function setPhase(p, secs){
    if(phases[p].s!==null){
      orb.style.transition="transform "+secs+"s ease-in-out";
      orb.style.transform="scale("+phases[p].s+")";
    }
  }
  function render(){
    var p=Math.floor((t%12)/4), left=4-(t%4);
    lab.textContent=left; sub.textContent=phases[p].n;
    bar.style.width=(t/TOTAL*100)+"%";
  }
  function tick(){
    t++;
    if(t>=TOTAL){ finish(); return; }
    if(t%4===0) setPhase(Math.floor((t%12)/4),4);
    render();
  }
  function finish(){
    clearInterval(timer); running=false; t=0;
    bar.style.width="100%";
    orb.style.transition="transform 4s ease-in-out"; orb.style.transform="scale(.6)";
    lab.textContent="Well done"; sub.textContent="Notice how you feel now";
    bBtn.textContent="Start again"; bBtn.className="full";
  }
  function start(){
    running=true; bBtn.textContent="Pause"; bBtn.className="full ghost";
    if(t===0){bar.style.transition="none";bar.style.width="0";void bar.offsetWidth;bar.style.transition="";}
    setPhase(Math.floor((t%12)/4), 4-(t%4));
    render();
    timer=setInterval(tick,1000);
  }
  function pause(){
    running=false; clearInterval(timer);
    var m=getComputedStyle(orb).transform; orb.style.transition="none"; orb.style.transform=m;
    sub.textContent="Paused"; bBtn.textContent="Resume"; bBtn.className="full";
  }
  bBtn.addEventListener("click", function(){ running ? pause() : start(); });

  /* Mood + journal */
  var moods=[["😊","Great"],["🙂","Okay"],["😟","Stressed"],["😣","Overwhelmed"],["😴","Tired"]];
  var prompts=[
    "What’s one thing that went okay today?",
    "What’s taking up the most space in your head right now?",
    "Who or what made you feel supported this week?",
    "What’s one small thing you could do to look after yourself today?",
    "What are you proud of, however small?",
    "What would you tell a friend who felt the way you do now?",
    "What’s something you’re looking forward to?",
    "What do you need more of right now? Less of?",
    "Describe a moment today when you felt calm."
  ];
  var pIdx=Math.floor(Date.now()/864e5)%prompts.length;
  $("prompt").textContent=prompts[pIdx];
  var selected=null, mWrap=$("moods");
  moods.forEach(function(m){
    var b=document.createElement("button");
    b.type="button"; b.className="mood"; b.setAttribute("aria-pressed","false");
    b.setAttribute("aria-label",m[1]);
    var e=document.createElement("span"); e.textContent=m[0]; e.setAttribute("aria-hidden","true");
    b.appendChild(e); b.appendChild(document.createTextNode(m[1]));
    b.addEventListener("click",function(){
      selected=m;
      Array.prototype.forEach.call(mWrap.children,function(c){c.setAttribute("aria-pressed",c===b?"true":"false")});
    });
    mWrap.appendChild(b);
  });

  var KEY="pause.checkins.v1", msg=$("msg");
  function say(t,err){msg.textContent=t;msg.className=err?"err":""}
  function load(){var d=store.get(KEY);return Array.isArray(d)?d:[]}
  function renderList(){
    var d=load(), list=$("list"); list.textContent="";
    $("count").textContent=d.length?d.length:"";
    $("clearBtn").hidden=!d.length;
    if(!d.length){var p=document.createElement("p");p.className="empty";p.textContent="No check-ins yet. Your first one will show up here.";list.appendChild(p);return}
    d.forEach(function(en){
      var row=document.createElement("div"); row.className="entry";
      var meta=document.createElement("div"); meta.className="meta";
      var l=document.createElement("span"); l.textContent=en.emoji+" "+en.mood;
      var r=document.createElement("span"); r.textContent=new Date(en.ts).toLocaleString("en-GB",{day:"numeric",month:"short",hour:"2-digit",minute:"2-digit"});
      meta.appendChild(l); meta.appendChild(r); row.appendChild(meta);
      if(en.note){var q=document.createElement("div");q.className="pq";q.textContent=en.prompt;row.appendChild(q);var n=document.createElement("p");n.textContent=en.note;row.appendChild(n)}
      list.appendChild(row);
    });
  }
  $("saveBtn").addEventListener("click",function(){
    var note=$("note").value.trim();
    if(!selected){say("Pick a mood first so we can log it.",true);return}
    var d=load();
    d.unshift({ts:Date.now(),emoji:selected[0],mood:selected[1],prompt:prompts[pIdx],note:note});
    if(store.set(KEY,d.slice(0,200))){
      say("Saved. Well done for checking in.");
      $("note").value=""; selected=null;
      Array.prototype.forEach.call(mWrap.children,function(c){c.setAttribute("aria-pressed","false")});
      renderList();
    } else { say("Couldn’t save. Your browser may be blocking storage (e.g. private mode).",true); }
  });
  $("clearBtn").addEventListener("click",function(){
    if(confirm("Delete all saved check-ins from this device?")){store.set(KEY,[]);renderList();say("")}
  });
  renderList();
})();
</script>
</body>
</html>
