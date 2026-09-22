# safeher
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SafeHer — Women's Safety Companion</title>
<style>
  :root{
    --bg:#14091f; --panel:#1f1230; --panel2:#2a1a40;
    --accent:#ff2d6f; --accent2:#a855f7;
    --text:#fdf4ff; --muted:#b8a5c9; --border:#3a2455;
    --safe:#22c55e; --warn:#f59e0b;
  }
  *{margin:0;padding:0;box-sizing:border-box;font-family:'Segoe UI',system-ui,-apple-system,sans-serif;}
  body{background:var(--bg);color:var(--text);line-height:1.6;-webkit-tap-highlight-color:transparent;}
  a{color:inherit;text-decoration:none;}

  /* HEADER */
  header{
    position:sticky;top:0;z-index:100;
    background:rgba(20,9,31,.92);backdrop-filter:blur(12px);
    border-bottom:1px solid var(--border);
    padding:.9rem 5%;display:flex;justify-content:space-between;align-items:center;
  }
  .logo{font-weight:800;font-size:1.25rem;display:flex;align-items:center;gap:.5rem;}
  .logo span{color:var(--accent);}
  .logo .dot{width:9px;height:9px;border-radius:50%;background:var(--accent);
    box-shadow:0 0 12px var(--accent);animation:pulse 2s infinite;}
  @keyframes pulse{0%,100%{opacity:1;}50%{opacity:.35;}}
  .header-sos{
    background:var(--accent);color:#fff;border:none;font-weight:700;
    padding:.5rem 1.1rem;border-radius:50px;cursor:pointer;font-size:.85rem;
    transition:transform .15s,background .2s;
  }
  .header-sos:hover{background:#e11d48;transform:scale(1.05);}

  /* HERO */
  .hero{padding:3rem 5% 2rem;text-align:center;
    background:radial-gradient(circle at 50% 0%,rgba(168,85,247,.18),transparent 60%);}
  .hero h1{font-size:clamp(1.7rem,5vw,2.6rem);font-weight:800;margin-bottom:.6rem;}
  .hero h1 span{background:linear-gradient(90deg,var(--accent),var(--accent2));
    -webkit-background-clip:text;background-clip:text;color:transparent;}
  .hero p{color:var(--muted);max-width:560px;margin:0 auto 2rem;font-size:.98rem;}

  /* SOS BUTTON */
  .sos-wrap{display:flex;flex-direction:column;align-items:center;gap:1rem;}
  .sos-btn{
    width:190px;height:190px;border-radius:50%;border:none;cursor:pointer;
    background:radial-gradient(circle at 35% 30%,#ff5c8a,var(--accent) 55%,#a3003a);
    color:#fff;font-weight:900;font-size:1.6rem;letter-spacing:.12em;
    display:flex;flex-direction:column;justify-content:center;align-items:center;gap:.2rem;
    box-shadow:0 0 0 0 rgba(255,45,111,.7),0 12px 40px rgba(255,45,111,.45);
    animation:sosPulse 2.4s infinite;transition:transform .12s;
  }
  .sos-btn:active{transform:scale(.94);}
  .sos-btn small{font-size:.62rem;font-weight:600;letter-spacing:.06em;opacity:.9;}
  @keyframes sosPulse{
    0%{box-shadow:0 0 0 0 rgba(255,45,111,.65),0 12px 40px rgba(255,45,111,.45);}
    70%{box-shadow:0 0 0 28px rgba(255,45,111,0),0 12px 40px rgba(255,45,111,.45);}
    100%{box-shadow:0 0 0 0 rgba(255,45,111,0),0 12px 40px rgba(255,45,111,.45);}
  }
  .sos-hint{color:var(--muted);font-size:.82rem;}

  /* SECTIONS */
  section{padding:2.5rem 5%;max-width:1100px;margin:0 auto;}
  .sec-title{font-size:1.35rem;font-weight:800;margin-bottom:.35rem;display:flex;align-items:center;gap:.55rem;}
  .sec-sub{color:var(--muted);font-size:.87rem;margin-bottom:1.4rem;}

  /* HELPLINE GRID */
  .helpline-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:.9rem;}
  .helpline{
    background:var(--panel);border:1px solid var(--border);border-radius:14px;
    padding:1rem;text-align:center;display:block;transition:.2s;
  }
  .helpline:hover{border-color:var(--accent);transform:translateY(-3px);background:var(--panel2);}
  .helpline .num{font-size:1.4rem;font-weight:800;color:var(--accent);}
  .helpline .name{font-size:.78rem;color:var(--muted);margin-top:.2rem;line-height:1.35;}

  /* TOOLS GRID */
  .tools{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:1rem;}
  .tool{
    background:var(--panel);border:1px solid var(--border);border-radius:16px;
    padding:1.4rem;display:flex;flex-direction:column;gap:.7rem;
  }
  .tool h3{font-size:1.02rem;font-weight:700;display:flex;align-items:center;gap:.5rem;}
  .tool p{color:var(--muted);font-size:.83rem;flex:1;}
  .btn{
    background:linear-gradient(135deg,var(--accent),var(--accent2));color:#fff;
    border:none;padding:.65rem 1rem;border-radius:10px;font-weight:700;
    font-size:.85rem;cursor:pointer;transition:.2s;
  }
  .btn:hover{filter:brightness(1.15);transform:translateY(-1px);}
  .btn:disabled{opacity:.45;cursor:not-allowed;transform:none;}
  .btn.ghost{background:transparent;border:1px solid var(--border);color:var(--text);}
  .btn.ghost:hover{border-color:var(--accent);background:rgba(255,45,111,.08);}
  .btn.danger{background:#dc2626;}

  /* CONTACTS */
  .contact-form{display:flex;gap:.6rem;flex-wrap:wrap;margin-bottom:1rem;}
  .contact-form input{
    flex:1;min-width:130px;background:var(--panel);border:1px solid var(--border);
    color:var(--text);padding:.7rem .9rem;border-radius:10px;font-size:.88rem;outline:none;
  }
  .contact-form input:focus{border-color:var(--accent);}
  .contact-list{display:flex;flex-direction:column;gap:.6rem;}
  .contact-row{
    background:var(--panel);border:1px solid var(--border);border-radius:12px;
    padding:.8rem 1rem;display:flex;justify-content:space-between;align-items:center;gap:.8rem;
  }
  .contact-row .info strong{display:block;font-size:.92rem;}
  .contact-row .info small{color:var(--muted);font-size:.78rem;}
  .contact-actions{display:flex;gap:.4rem;}
  .icon-btn{
    width:36px;height:36px;border-radius:9px;border:1px solid var(--border);
    background:var(--panel2);color:var(--text);cursor:pointer;font-size:.95rem;
    display:flex;align-items:center;justify-content:center;transition:.2s;
  }
  .icon-btn:hover{border-color:var(--accent);background:rgba(255,45,111,.12);}
  .empty{color:var(--muted);font-size:.85rem;text-align:center;padding:1.2rem;
    border:1px dashed var(--border);border-radius:12px;}

  /* TIPS */
  .tips{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:1rem;}
  .tip{
    background:var(--panel);border:1px solid var(--border);border-left:3px solid var(--accent2);
    border-radius:12px;padding:1.1rem;
  }
  .tip h4{font-size:.95rem;margin-bottom:.4rem;color:var(--accent2);}
  .tip p{font-size:.83rem;color:var(--muted);}

  /* LOCATION RESULT */
  .loc-box{background:var(--panel);border:1px solid var(--border);border-radius:14px;
    padding:1rem;margin-top:1rem;display:none;}
  .loc-box.show{display:block;}
  .loc-box code{display:block;background:#0d0517;padding:.6rem .8rem;border-radius:8px;
    font-size:.8rem;word-break:break-all;margin:.5rem 0;color:#7dd3fc;}
  .loc-actions{display:flex;gap:.5rem;flex-wrap:wrap;margin-top:.6rem;}
  iframe.map{width:100%;height:220px;border:0;border-radius:12px;margin-top:.7rem;}

  /* OVERLAYS */
  .overlay{
    position:fixed;inset:0;z-index:1000;display:none;
    justify-content:center;align-items:center;padding:1.5rem;
    background:rgba(10,4,18,.92);backdrop-filter:blur(8px);
  }
  .overlay.show{display:flex;}
  .overlay-card{
    background:var(--panel);border:1px solid var(--border);border-radius:20px;
    padding:2rem;max-width:400px;width:100%;text-align:center;
  }

  /* SOS COUNTDOWN */
  #sosOverlay .count{font-size:5rem;font-weight:900;color:var(--accent);
    line-height:1;animation:zoom .9s infinite;}
  @keyframes zoom{0%,100%{transform:scale(1);}50%{transform:scale(1.12);}}
  #sosOverlay h2{margin:.6rem 0 1.4rem;font-size:1.1rem;}

  /* ACTIVE ALERT */
  #alertOverlay .alert-icon{font-size:3rem;animation:shake .5s infinite;}
  @keyframes shake{0%,100%{transform:rotate(0);}25%{transform:rotate(-12deg);}75%{transform:rotate(12deg);}}
  #alertOverlay h2{color:var(--accent);margin:.8rem 0 .4rem;}
  #alertOverlay p{color:var(--muted);font-size:.88rem;margin-bottom:1.2rem;}

  /* FAKE CALL */
  #callOverlay{background:linear-gradient(160deg,#1a0b2e,#0d0517);}
  .caller-avatar{
    width:100px;height:100px;border-radius:50%;margin:0 auto 1rem;
    background:linear-gradient(135deg,var(--accent2),var(--accent));
    display:flex;align-items:center;justify-content:center;font-size:2.5rem;
    animation:ring 1.5s infinite;
  }
  @keyframes ring{0%,100%{transform:scale(1);}50%{transform:scale(1.07);}}
  .caller-name{font-size:1.5rem;font-weight:700;}
  .caller-sub{color:var(--muted);font-size:.85rem;margin-bottom:2.5rem;}
  .call-btns{display:flex;justify-content:center;gap:3rem;}
  .call-btn{
    width:64px;height:64px;border-radius:50%;border:none;cursor:pointer;
    font-size:1.5rem;display:flex;align-items:center;justify-content:center;
    transition:transform .15s;
  }
  .call-btn:active{transform:scale(.9);}
  .call-btn.accept{background:var(--safe);color:#fff;}
  .call-btn.decline{background:#dc2626;color:#fff;}

  /* FOOTER */
  footer{border-top:1px solid var(--border);padding:2rem 5%;margin-top:2rem;
    text-align:center;color:var(--muted);font-size:.8rem;}
  .disclaimer{
    background:rgba(245,158,11,.1);border:1px solid rgba(245,158,11,.35);
    border-radius:12px;padding:1rem;margin:1.5rem auto;max-width:800px;
    font-size:.8rem;color:#fcd34d;text-align:left;
  }

  /* TOAST */
  #toast{
    position:fixed;bottom:1.5rem;left:50%;transform:translateX(-50%) translateY(120%);
    background:var(--panel2);border:1px solid var(--accent);color:var(--text);
    padding:.75rem 1.3rem;border-radius:50px;font-size:.85rem;z-index:2000;
    transition:transform .3s;white-space:nowrap;max-width:90vw;overflow:hidden;
    text-overflow:ellipsis;
  }
  #toast.show{transform:translateX(-50%) translateY(0);}
</style>
</head>
<body>

<header>
  <div class="logo"><span class="dot"></span>Safe<span>Her</span></div>
  <button class="header-sos" onclick="startSOS()">🚨 SOS</button>
</header>

<!-- HERO -->
<div class="hero">
  <h1>Your safety, <span>one tap away</span></h1>
  <p>Emergency alerts, helplines, fake calls and location sharing — all in one place. Works offline once loaded.</p>
  <div class="sos-wrap">
    <button class="sos-btn" onclick="startSOS()">
      SOS
      <small>TAP TO ALERT</small>
    </button>
    <div class="sos-hint">Triggers siren + shares your live location</div>
  </div>
</div>

<!-- HELPLINES -->
<section>
  <div class="sec-title">📞 Emergency Helplines</div>
  <div class="sec-sub">Tap any number to call directly. Available 24/7 across India.</div>
  <div class="helpline-grid">
    <a class="helpline" href="tel:112"><div class="num">112</div><div class="name">National Emergency<br>(All services)</div></a>
    <a class="helpline" href="tel:1091"><div class="num">1091</div><div class="name">Women's Helpline<br>(Police)</div></a>
    <a class="helpline" href="tel:181"><div class="num">181</div><div class="name">Women Helpline<br>(Abuse / Distress)</div></a>
    <a class="helpline" href="tel:100"><div class="num">100</div><div class="name">Police</div></a>
    <a class="helpline" href="tel:102"><div class="num">102</div><div class="name">Ambulance</div></a>
    <a class="helpline" href="tel:1098"><div class="num">1098</div><div class="name">Child Helpline</div></a>
    <a class="helpline" href="tel:1930"><div class="num">1930</div><div class="name">Cyber Crime<br>Reporting</div></a>
    <a class="helpline" href="tel:1091"><div class="num">1090</div><div class="name">Women Power Line<br>(UP)</div></a>
  </div>
</section>

<!-- TOOLS -->
<section>
  <div class="sec-title">🛡️ Safety Tools</div>
  <div class="sec-sub">Practical tools you can use right now.</div>
  <div class="tools">

    <div class="tool">
      <h3>📍 Live Location</h3>
      <p>Get your exact coordinates and a Google Maps link you can instantly share with anyone.</p>
      <button class="btn" onclick="getLocation()">Get My Location</button>
      <button class="btn ghost" onclick="shareLocation()">Share Location</button>
    </div>

    <div class="tool">
      <h3>📱 Fake Call</h3>
      <p>Simulate an incoming call to escape uncomfortable or unsafe situations.</p>
      <button class="btn" onclick="openFakeCall()">Setup Fake Call</button>
    </div>

    <div class="tool">
      <h3>🔊 Loud Siren</h3>
      <p>Blast a high-volume alarm to attract attention and deter an attacker.</p>
      <button class="btn" id="sirenBtn" onclick="toggleSiren()">Start Siren</button>
    </div>

    <div class="tool">
      <h3>💬 Quick SMS Alert</h3>
      <p>Send a pre-written distress message with your location to a saved contact.</p>
      <button class="btn" onclick="quickSMS()">Send Alert SMS</button>
    </div>

  </div>

  <div class="loc-box" id="locBox">
    <strong>Your current location</strong>
    <code id="coordText">—</code>
    <div class="loc-actions">
      <button class="btn ghost" onclick="copyLocation()">📋 Copy Link</button>
      <a class="btn ghost" id="mapLink" target="_blank">🗺️ Open in Maps</a>
    </div>
    <iframe class="map" id="mapFrame" style="display:none"></iframe>
  </div>
</section>

<!-- CONTACTS -->
<section>
  <div class="sec-title">👥 Trusted Contacts</div>
  <div class="sec-sub">Saved privately in your browser only — never uploaded anywhere.</div>
  <div class="contact-form">
    <input type="text" id="cName" placeholder="Name (e.g. Mom)">
    <input type="tel" id="cPhone" placeholder="Phone (e.g. +919876543210)">
    <button class="btn" onclick="addContact()">Add</button>
  </div>
  <div class="contact-list" id="contactList"></div>
</section>

<!-- TIPS -->
<section>
  <div class="sec-title">💡 Safety Tips</div>
  <div class="sec-sub">Simple habits that make a real difference.</div>
  <div class="tips">
    <div class="tip"><h4>Share your live location</h4><p>Before a late-night commute or meeting a stranger, share your live location with a trusted person and set a check-in time.</p></div>
    <div class="tip"><h4>Trust your gut</h4><p>If a situation feels wrong, leave. You never need to justify your instinct to be polite.</p></div>
    <div class="tip"><h4>Keep your phone charged</h4><p>Carry a power bank. A dead phone means no SOS, no maps, no ride.</p></div>
    <div class="tip"><h4>Fake call escape</h4><p>If someone is making you uncomfortable, use the Fake Call tool to excuse yourself naturally.</p></div>
    <div class="tip"><h4>Verify cab details</h4><p>Match the number plate, driver photo and car model before getting in. Share the trip with someone.</p></div>
    <div class="tip"><h4>Walk with confidence</h4><p>Head up, phone away, aware of surroundings. Attackers target people who look distracted.</p></div>
    <div class="tip"><h4>Save emergency numbers</h4><p>Add 112 and 1091 as speed dials. In a crisis you won't have time to search.</p></div>
    <div class="tip"><h4>Report, don't stay silent</h4><p>Harassment is a crime. File an FIR at any police station — zero FIR means any station must accept it.</p></div>
  </div>

  <div class="disclaimer">
    ⚠️ <strong>Important:</strong> SafeHer is a personal safety aid, not a replacement for emergency services. Browser-based location and alerts depend on your device, permissions and network. In immediate danger, always call <strong>112</strong> directly. Add this page to your home screen for faster access.
  </div>
</section>

<footer>
  SafeHer — Built to keep you safer. Your data never leaves your device.
</footer>

<!-- ============ OVERLAYS ============ -->

<!-- SOS COUNTDOWN -->
<div class="overlay" id="sosOverlay">
  <div class="overlay-card">
    <div class="count" id="countNum">3</div>
    <h2>Triggering emergency alert…</h2>
    <button class="btn ghost" style="width:100%;padding:1rem;" onclick="cancelSOS()">CANCEL</button>
  </div>
</div>

<!-- ACTIVE ALERT -->
<div class="overlay" id="alertOverlay">
  <div class="overlay-card">
    <div class="alert-icon">🚨</div>
    <h2>SOS ACTIVATED</h2>
    <p id="alertMsg">Siren playing. Share your location immediately.</p>
    <div style="display:flex;flex-direction:column;gap:.6rem;">
      <a class="btn danger" href="tel:112" style="padding:.9rem;">📞 Call 112 Now</a>
      <button class="btn" onclick="shareLocation()">📍 Share My Location</button>
      <button class="btn ghost" onclick="stopSOS()">Stop Alert</button>
    </div>
  </div>
</div>

<!-- FAKE CALL SETUP -->
<div class="overlay" id="setupCallOverlay">
  <div class="overlay-card">
    <h2 style="margin-bottom:1rem;">Fake Call Setup</h2>
    <input id="fcName" placeholder="Caller name (e.g. Dad)"
      style="width:100%;background:var(--bg);border:1px solid var(--border);color:var(--text);
      padding:.8rem;border-radius:10px;margin-bottom:.7rem;outline:none;font-size:.9rem;">
    <input id="fcDelay" type="number" value="5" min="1" max="120"
      style="width:100%;background:var(--bg);border:1px solid var(--border);color:var(--text);
      padding:.8rem;border-radius:10px;margin-bottom:1rem;outline:none;font-size:.9rem;"
      placeholder="Delay in seconds">
    <button class="btn" style="width:100%;padding:.9rem;margin-bottom:.5rem;" onclick="scheduleFakeCall()">Schedule Call</button>
    <button class="btn ghost" style="width:100%;padding:.9rem;" onclick="closeOverlay('setupCallOverlay')">Cancel</button>
  </div>
</div>

<!-- INCOMING CALL -->
<div class="overlay" id="callOverlay">
  <div style="text-align:center;">
    <div class="caller-avatar">👤</div>
    <div class="caller-name" id="incomingName">Dad</div>
    <div class="caller-sub">Incoming call…</div>
    <div class="call-btns">
      <button class="call-btn decline" onclick="endFakeCall()">✕</button>
      <button class="call-btn accept" onclick="acceptFakeCall()">✓</button>
    </div>
  </div>
</div>

<!-- IN CALL -->
<div class="overlay" id="inCallOverlay">
  <div class="overlay-card">
    <div class="caller-avatar" style="animation:none;">👤</div>
    <div class="caller-name" id="activeName">Dad</div>
    <div class="caller-sub" id="callTimer">00:00</div>
    <div class="call-btns">
      <button class="call-btn decline" onclick="endFakeCall()">✕</button>
    </div>
  </div>
</div>

<div id="toast"></div>

<script>
/* ================= UTILITIES ================= */
const $ = id => document.getElementById(id);

function toast(msg){
  const t = $('toast');
  t.textContent = msg;
  t.classList.add('show');
  clearTimeout(t._timer);
  t._timer = setTimeout(()=>t.classList.remove('show'), 2600);
}
function openOverlay(id){ $(id).classList.add('show'); }
function closeOverlay(id){ $(id).classList.remove('show'); }

/* ================= AUDIO ENGINE ================= */
let ac = null;
function audio(){
  if(!ac) ac = new (window.AudioContext || window.webkitAudioContext)();
  if(ac.state === 'suspended') ac.resume();
  return ac;
}

/* --- SIREN --- */
let siren = null;
function startSiren(){
  if(siren) return;
  const ctx = audio();
  const osc = ctx.createOscillator();
  const gain = ctx.createGain();
  osc.type = 'sawtooth';
  gain.gain.setValueAtTime(0.0001, ctx.currentTime);
  gain.gain.exponentialRampToValueAtTime(0.22, ctx.currentTime + 0.15);
  osc.connect(gain).connect(ctx.destination);
  osc.frequency.setValueAtTime(650, ctx.currentTime);
  osc.start();

  const sweep = setInterval(() => {
    const t = ctx.currentTime;
    osc.frequency.linearRampToValueAtTime(1250, t + 0.45);
    osc.frequency.linearRampToValueAtTime(650, t + 0.9);
  }, 900);

  siren = { osc, gain, sweep };
  $('sirenBtn').textContent = 'Stop Siren';
  $('sirenBtn').classList.add('danger');
}
function stopSiren(){
  if(!siren) return;
  clearInterval(siren.sweep);
  try{
    siren.gain.gain.exponentialRampToValueAtTime(0.0001, ac.currentTime + 0.2);
    siren.osc.stop(ac.currentTime + 0.25);
  }catch(e){}
  siren = null;
  $('sirenBtn').textContent = 'Start Siren';
  $('sirenBtn').classList.remove('danger');
}
function toggleSiren(){ siren ? stopSiren() : startSiren(); }

/* --- RINGTONE for fake call --- */
let ringTimer = null, ringNodes = [];
function startRingtone(){
  const ctx = audio();
  ringNodes = [];
  c