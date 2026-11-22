<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Wordfinders</title>
<link href="https://fonts.googleapis.com/css2?family=Lilita+One&family=Manrope:wght@400;600&display=swap" rel="stylesheet">
<style>
:root{--bg:#02030a;--blue:#142c7a;--blue2:#081646;--gold:#ff7ab8;--ink:#fff4fa;--mut:#c4b4e0;--line:rgba(255,122,184,.4);
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
*{box-sizing:border-box}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;min-height:100vh;color:var(--ink);font:400 16px/1.5 Manrope,system-ui,sans-serif;
background:radial-gradient(70% 50% at 0% 12%,rgba(255,122,184,.3),transparent 70%),radial-gradient(60% 45% at 100% 100%,rgba(255,122,184,.18),transparent 70%),radial-gradient(120% 90% at 10% 0%,var(--blue) 0%,var(--blue2) 35%,var(--bg) 80%),var(--bg);background-attachment:fixed}
.laurel{position:fixed;left:2vw;top:8vh;height:84vh;width:auto;opacity:.85;pointer-events:none;z-index:0;transform:rotate(-6deg);filter:drop-shadow(0 0 8px rgba(255,190,110,.45))}
main{position:relative;z-index:1;max-width:720px;margin:0 auto;padding:28px 20px 60px}
.head{background:rgba(4,6,13,.7);border:1px solid var(--line);border-radius:14px;padding:16px 20px;margin-bottom:20px;backdrop-filter:blur(3px)}
h1{font:400 50px/1 "Lilita One",system-ui,sans-serif;margin:0 0 6px;color:#ffd1e6;text-shadow:0 2px 0 #c2307a,0 4px 14px rgba(0,0,0,.6);letter-spacing:1px}
.sub{color:var(--mut);margin:0}
nav{display:flex;gap:8px;margin-bottom:20px;border-bottom:1px solid var(--line)}
nav button{flex:1;background:none;border:0;color:var(--mut);font:400 19px "Lilita One",system-ui,sans-serif;padding:12px 4px;cursor:pointer;border-bottom:2px solid transparent;margin-bottom:-1px}
nav button[aria-selected=true]{color:var(--gold);border-color:var(--gold)}
button:focus-visible,input:focus-visible,select:focus-visible{outline:2px solid var(--gold);outline-offset:2px}
section{display:none}section.on{display:block}
.panel{background:rgba(4,6,13,.5);border:1px solid var(--line);border-radius:12px;padding:18px;backdrop-filter:blur(1px)}
label{display:block;font-size:13px;color:var(--mut);margin:0 0 4px}
input,select{width:100%;background:#050914;color:var(--ink);border:1px solid rgba(154,167,204,.35);border-radius:6px;padding:10px 12px;font:inherit}
.row{display:flex;gap:10px;flex-wrap:wrap;align-items:end;margin-bottom:12px}.row>div{flex:1;min-width:130px}
.btn{background:var(--gold);color:#14100a;border:0;border-radius:6px;padding:11px 18px;font:400 17px "Lilita One",system-ui,sans-serif;cursor:pointer}
.btn.ghost{background:none;color:var(--gold);border:1px solid var(--line)}
.bar{display:flex;justify-content:space-between;align-items:center;margin:14px 0}
#grid{display:grid;gap:4px;margin:10px 0;background:rgba(2,3,10,.75);padding:8px;border-radius:12px}
#grid button{aspect-ratio:1;background:#050914;border:1px solid rgba(154,167,204,.25);color:var(--ink);font:400 clamp(15px,4.5vw,24px) "Lilita One",system-ui,sans-serif;border-radius:6px;cursor:pointer;padding:0}
#grid button.sel{background:var(--blue);border-color:var(--gold)}
#grid button.found{background:var(--gold);color:#14100a;border-color:var(--gold)}
.words{display:flex;flex-wrap:wrap;gap:8px;margin:0;padding:0;list-style:none}
.words li{background:#0a1030;border:1.5px solid #ff7ab8;color:#fff;border-radius:20px;padding:4px 14px;font-size:15px;font-weight:600}
.words{background:rgba(2,3,10,.85);border:1px solid var(--line);border-radius:12px;padding:12px}
.words li.done{background:var(--gold);color:#14100a;text-decoration:line-through}
ul.list{list-style:none;margin:12px 0 0;padding:0}
ul.list li{display:flex;justify-content:space-between;gap:10px;align-items:center;padding:10px 0;border-top:1px solid rgba(154,167,204,.2)}
ul.list li small{color:var(--mut)}
ul.list li button{background:none;border:0;color:var(--mut);cursor:pointer;font-size:14px}
audio{width:100%;margin-top:14px}
.hint{color:var(--mut);font-size:13px;margin:10px 0 0}
#alert{position:fixed;inset:auto 16px calc(16px + env(safe-area-inset-bottom,0px)) 16px;z-index:5;max-width:520px;margin:0 auto;background:var(--gold);color:#14100a;border-radius:10px;padding:16px 18px;display:none;box-shadow:0 10px 40px rgba(0,0,0,.6)}
#alert b{font:400 24px "Lilita One",system-ui,sans-serif;display:block}
#alert button{margin-top:8px;background:#14100a;color:var(--gold);border:0;border-radius:6px;padding:8px 14px;font:600 14px Manrope,sans-serif;cursor:pointer}
@media (max-width:600px){.laurel{left:-40px;opacity:.7}h1{font-size:40px}}
</style>
</head>
<body>
<svg class="laurel" viewBox="-30 -50 250 580" fill="none" stroke="#f2c46d" stroke-width="2.2" stroke-linecap="round" aria-hidden="true">
<path d="M150 508C96 440 60 330 66 210C70 130 100 60 140 14"/>
<g id="lf"><path d="M70 440c-26-6-44-28-48-52 24 4 44 22 48 52z"/><path d="M70 440c-20-12-34-26-44-48"/></g>
<use href="#lf" transform="translate(-6 -64) rotate(4 70 440)"/>
<use href="#lf" transform="translate(-12 -128) rotate(8 70 440)"/>
<use href="#lf" transform="translate(-14 -192) rotate(10 70 440)"/>
<use href="#lf" transform="translate(-10 -256) rotate(14 70 440)"/>
<use href="#lf" transform="translate(90 100) rotate(15) scale(.75) translate(-70 -440)"/>
<use href="#lf" transform="translate(112 54) rotate(20) scale(.6) translate(-70 -440)"/>
<use href="#lf" transform="translate(138 18) rotate(40) scale(.5) translate(-70 -440)"/>
<g id="rf"><path d="M78 420c26 0 50-16 58-40-26-2-52 12-58 40z"/><path d="M78 420c22-6 40-20 54-36"/></g>
<use href="#rf" transform="translate(-8 -70) rotate(-2 78 420)"/>
<use href="#rf" transform="translate(-14 -140) rotate(-4 78 420)"/>
<use href="#rf" transform="translate(-14 -210) rotate(-6 78 420)"/>
<use href="#rf" transform="translate(100 104) rotate(-8) scale(.8) translate(-78 -420)"/>
<use href="#rf" transform="translate(114 52) rotate(-8) scale(.65) translate(-78 -420)"/>
<use href="#rf" transform="translate(132 24) rotate(-10) scale(.5) translate(-78 -420)"/>
</svg>

<main>
<div class="head"><h1>Wordfinders</h1>
<p class="sub">Play, listen, and never miss what’s next.</p></div>
<nav role="tablist">
<button role="tab" aria-selected="true" data-t="game">Word race</button>
<button role="tab" aria-selected="false" data-t="pod">Podcasts</button>
<button role="tab" aria-selected="false" data-t="rem">Reminders</button>
</nav>

<section id="game" class="on"><div class="panel">
<div class="row"><div><label for="name">Your name</label><input id="name" maxlength="16"></div>
<div><label for="room">Room code</label><input id="room" maxlength="12" value="LAUREL"></div>
<button class="btn" id="start">Start game</button></div>
<div class="bar"><span id="timer">0:00</span><span id="count"></span></div>
<ul class="words" id="words"></ul>
<div id="grid"></div>
<p class="hint">Tap the first and last letter of a food word. Everyone with the same room code gets the same grid.</p>
<div id="win" style="display:none"><p id="winmsg"></p><button class="btn ghost" id="share">Share result</button></div>
</div></section>

<section id="pod"><div class="panel">
<div class="row"><div><label for="purl">Audio link (.mp3 or direct episode file)</label><input id="purl" placeholder="https://…/episode.mp3"></div></div>
<div class="row"><div><label for="ptitle">Title (optional)</label><input id="ptitle"></div><button class="btn" id="padd">Add link</button></div>
<div class="row"><div><label for="pfile">Or pick an audio file from this device</label><input id="pfile" type="file" accept="audio/*"></div></div>
<audio id="player" controls></audio>
<ul class="list" id="plist"></ul>
<p class="hint">Spotify and Apple Podcasts links can’t play here. Use the episode’s direct audio or RSS file link instead.</p>
</div></section>

<section id="rem"><div class="panel">
<div class="row"><div><label for="ics">Import your calendar (.ics file)</label><input id="ics" type="file" accept=".ics,text/calendar"></div>
<div><label for="lead">Remind me</label><select id="lead"><option value="5">5 min before</option><option value="10" selected>10 min before</option><option value="15">15 min before</option><option value="30">30 min before</option></select></div></div>
<div class="row"><div><label for="etitle">Add one event</label><input id="etitle" placeholder="Dentist"></div>
<div><label for="edate">When</label><input id="edate" type="datetime-local"></div><button class="btn" id="eadd">Add event</button></div>
<button class="btn ghost" id="notif">Turn on phone alerts</button>
<ul class="list" id="elist"></ul>
<p class="hint">Keep this page open and it will alert you with a banner, a chime, and a notification, even while you’re busy in another tab.</p>
</div></section>
</main>
<div id="alert" role="alert"><b id="atitle"></b><span id="atime"></span><br><button id="aok">Got it</button></div>

<script>
const $=s=>document.querySelector(s),$$=s=>[...document.querySelectorAll(s)];
const st={get(k,d){try{const v=localStorage.getItem(k);return v?JSON.parse(v):d}catch(e){return d}},set(k,v){try{localStorage.setItem(k,JSON.stringify(v))}catch(e){}}};
$$('nav button').forEach(b=>b.onclick=()=>{$$('nav button').forEach(x=>x.setAttribute('aria-selected',x===b));$$('section').forEach(s=>s.classList.toggle('on',s.id===b.dataset.t))});

/* Word race */
const FOOD=['MANGO','BREAD','PASTA','OLIVE','LEMON','HONEY','PEACH','CURRY','SALAD','TACOS','RICE','BEANS','PIZZA','GRAPE','SUSHI','CREAM','STEAK','PLUM','BERRY','FIGS','PEAR','SOUP','CAKE','CORN'];
const N=10,DIRS=[[1,0],[0,1],[1,1]];let G,placed,found,t0,tick,sel;
const hash=s=>{let h=1779033703;for(const c of s.toUpperCase()){h=Math.imul(h^c.charCodeAt(0),3432918353);h=h<<13|h>>>19}return h>>>0};
const rng=a=>()=>{a|=0;a=a+0x6D2B79F5|0;let t=Math.imul(a^a>>>15,1|a);t=t+Math.imul(t^t>>>7,61|t)^t;return((t^t>>>14)>>>0)/4294967296};
function build(code){const r=rng(hash(code));const pool=[...FOOD].sort(()=>r()-.5).filter(w=>w.length<=N).slice(0,8);
 G=Array.from({length:N},()=>Array(N).fill(''));placed=[];
 for(const w of pool){for(let k=0;k<200;k++){const[d0,d1]=DIRS[Math.floor(r()*3)],x=Math.floor(r()*N),y=Math.floor(r()*N);
  const ex=x+d0*(w.length-1),ey=y+d1*(w.length-1);if(ex>=N||ey>=N)continue;
  let ok=true;for(let i=0;i<w.length;i++){const c=G[y+d1*i][x+d0*i];if(c&&c!==w[i])ok=false}
  if(!ok)continue;for(let i=0;i<w.length;i++)G[y+d1*i][x+d0*i]=w[i];placed.push({w,x,y,d0,d1});break}}
 const L='ABCDEFGHIJKLMNOPRSTUY';for(let y=0;y<N;y++)for(let x=0;x<N;x++)if(!G[y][x])G[y][x]=L[Math.floor(r()*L.length)]}
function draw(){const g=$('#grid');g.style.gridTemplateColumns=`repeat(${N},1fr)`;g.innerHTML='';
 for(let y=0;y<N;y++)for(let x=0;x<N;x++){const b=document.createElement('button');b.textContent=G[y][x];b.dataset.k=x+','+y;b.setAttribute('aria-label',G[y][x]);b.onclick=()=>pick(x,y);g.append(b)}
 $('#words').innerHTML=placed.map(p=>`<li id="w-${p.w}">${p.w}</li>`).join('');upd()}
const cell=(x,y)=>$(`#grid [data-k="${x},${y}"]`);
function pick(x,y){if(!placed)return;if(!sel){sel=[x,y];cell(x,y).classList.add('sel');return}
 const[sx,sy]=sel;cell(sx,sy).classList.remove('sel');sel=null;
 const dx=Math.sign(x-sx),dy=Math.sign(y-sy),len=Math.max(Math.abs(x-sx),Math.abs(y-sy))+1;
 if((x-sx!==0&&y-sy!==0&&Math.abs(x-sx)!==Math.abs(y-sy)))return;
 const cs=[];for(let i=0;i<len;i++)cs.push([sx+dx*i,sy+dy*i]);const s=cs.map(c=>G[c[1]][c[0]]).join('');
 const p=placed.find(p=>!found.has(p.w)&&(p.w===s||p.w===[...s].reverse().join('')));
 if(p){found.add(p.w);cs.forEach(c=>cell(c[0],c[1]).classList.add('found'));$('#w-'+p.w).classList.add('done');upd();if(found.size===placed.length)end()}}
const upd=()=>$('#count').textContent=`${found?found.size:0} of ${placed?placed.length:0} found`;
function fmt(s){return Math.floor(s/60)+':'+String(s%60).padStart(2,'0')}
function end(){clearInterval(tick);const s=Math.round((Date.now()-t0)/1000);$('#win').style.display='block';
 $('#winmsg').textContent=`${$('#name').value||'You'} found all ${placed.length} words in ${fmt(s)}.`}
$('#start').onclick=()=>{const c=($('#room').value||'LAUREL').trim();st.set('name',$('#name').value);build(c);found=new Set();sel=null;draw();$('#win').style.display='none';
 clearInterval(tick);t0=Date.now();$('#timer').textContent='0:00';tick=setInterval(()=>$('#timer').textContent=fmt(Math.round((Date.now()-t0)/1000)),500)};
$('#share').onclick=async()=>{const m=`${$('#winmsg').textContent} Room ${$('#room').value}. Beat me!`;try{if(navigator.share)await navigator.share({text:m});else{await navigator.clipboard.writeText(m);$('#share').textContent='Copied'}}catch(e){}};
$('#name').value=st.get('name','');

/* Podcasts */
let pods=st.get('pods',[]),objUrl=null;
function rp(){$('#plist').innerHTML=pods.map((p,i)=>`<li><span>${p.t}<br><small>${p.u.slice(0,48)}</small></span><span><button data-p="${i}">Play</button><button data-d="${i}">Remove</button></span></li>`).join('')||'<li><small>No episodes yet. Add a link or a file above.</small></li>'}
$('#plist').onclick=e=>{const b=e.target.closest('button');if(!b)return;if(b.dataset.p!==undefined){const p=pods[b.dataset.p];$('#player').src=p.u;$('#player').play().catch(()=>{})}
 if(b.dataset.d!==undefined){pods.splice(b.dataset.d,1);st.set('pods',pods);rp()}};
$('#padd').onclick=()=>{const u=$('#purl').value.trim();if(!/^https?:\/\//.test(u))return;pods.push({u,t:$('#ptitle').value.trim()||'Episode '+(pods.length+1)});st.set('pods',pods);$('#purl').value='';$('#ptitle').value='';rp()};
$('#pfile').onchange=e=>{const f=e.target.files[0];if(!f)return;if(objUrl)URL.revokeObjectURL(objUrl);objUrl=URL.createObjectURL(f);$('#player').src=objUrl;$('#player').play().catch(()=>{})};
rp();

/* Reminders */
let evs=st.get('evs',[]);$('#lead').value=st.get('lead','10');
const save=()=>{evs=evs.filter(e=>e.s>Date.now()-3600e3).sort((a,b)=>a.s-b.s);st.set('evs',evs);re()};
function re(){$('#elist').innerHTML=evs.map((e,i)=>`<li><span>${e.t}<br><small>${new Date(e.s).toLocaleString([], {weekday:'short',month:'short',day:'numeric',hour:'numeric',minute:'2-digit'})}</small></span><button data-x="${i}">Remove</button></li>`).join('')||'<li><small>No upcoming events. Import a calendar or add one above.</small></li>'}
$('#elist').onclick=e=>{const b=e.target.closest('button');if(b){evs.splice(b.dataset.x,1);save()}};
$('#lead').onchange=()=>st.set('lead',$('#lead').value);
$('#eadd').onclick=()=>{const t=$('#etitle').value.trim()||'Event',d=$('#edate').value;if(!d)return;evs.push({t,s:new Date(d).getTime(),n:0});$('#etitle').value='';save()};
function parseICS(txt){const out=[];txt=txt.replace(/\r?\n[ \t]/g,'');
 for(const blk of txt.split('BEGIN:VEVENT').slice(1)){const sum=(blk.match(/\nSUMMARY[^:]*:(.*)/)||[])[1]||'Event',m=blk.match(/\nDTSTART([^:]*):(\d{4})(\d{2})(\d{2})(?:T(\d{2})(\d{2})(\d{2})?(Z)?)?/);if(!m)continue;
  const[,,Y,Mo,D,h='09',mi='00',,z]=m;const s=z?Date.UTC(+Y,Mo-1,+D,+h,+mi):new Date(+Y,Mo-1,+D,+h,+mi).getTime();
  out.push({t:sum.trim().replace(/\\,/g,','),s,n:0})}return out}
$('#ics').onchange=async e=>{const f=e.target.files[0];if(!f)return;const add=parseICS(await f.text()).filter(x=>x.s>Date.now());
 for(const a of add)if(!evs.some(o=>o.s===a.s&&o.t===a.t))evs.push(a);save()};
$('#notif').onclick=async()=>{try{const r=await Notification.requestPermission();$('#notif').textContent=r==='granted'?'Phone alerts on':'Alerts blocked in browser settings'}catch(e){$('#notif').textContent='Alerts not supported here'}};
function chime(){try{const c=new (window.AudioContext||window.webkitAudioContext)();[880,1175,1480].forEach((f,i)=>{const o=c.createOscillator(),g=c.createGain();o.frequency.value=f;o.connect(g);g.connect(c.destination);const t=c.currentTime+i*.22;g.gain.setValueAtTime(.2,t);g.gain.exponentialRampToValueAtTime(.001,t+.4);o.start(t);o.stop(t+.45)})}catch(e){}}
function fire(e){const mins=Math.max(0,Math.round((e.s-Date.now())/60000));$('#atitle').textContent=e.t;$('#atime').textContent=mins<=0?'Starting now':`Starts in ${mins} min`;$('#alert').style.display='block';chime();
 try{if(Notification.permission==='granted')new Notification(e.t,{body:mins<=0?'Starting now':`Starts in ${mins} min`})}catch(x){}if(navigator.vibrate)navigator.vibrate([200,100,200])}
$('#aok').onclick=()=>$('#alert').style.display='none';
setInterval(()=>{const lead=+$('#lead').value*60000,now=Date.now();let ch=false;for(const e of evs){if(!e.n&&now>=e.s-lead&&now<e.s+60000){e.n=1;ch=true;fire(e)}}if(ch)st.set('evs',evs)},10000);
re();$('#start').click();
</script>
</body>
</html>
