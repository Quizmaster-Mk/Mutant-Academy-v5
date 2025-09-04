<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Mutant Academy — Danger Room (V2.2)</title>
<style>
:root{
  --bg:#03060b; --card:#081426; --muted:#9fb0bd; --accent:#6ee7b7; --accent2:#7cc1ff;
  --danger:#ff6b6b; --gold:#ffd166; --text:#e9fbf6;
}
*{box-sizing:border-box}
html,body{height:100%}
body{
  margin:0;font-family:Inter,system-ui,Segoe UI,Arial;background:
  radial-gradient(1000px 500px at 10% 10%, rgba(110,231,183,0.03), transparent 6%),
  radial-gradient(700px 350px at 90% 90%, rgba(124,193,255,0.02), transparent 6%),
  linear-gradient(180deg,var(--bg),#00111a 60%);
  color:var(--text); display:flex; align-items:flex-start; justify-content:center; padding:18px;
  transition:background .25s ease;
}
.app{
  width:100%; max-width:800px; background:linear-gradient(180deg, rgba(255,255,255,0.012), rgba(255,255,255,0.008));
  border:1px solid rgba(255,255,255,0.04); border-radius:14px; padding:14px; box-shadow:0 18px 50px rgba(0,0,0,0.6);
  overflow:hidden;
}
.header{display:flex;justify-content:space-between;align-items:center}
.title{display:flex;gap:12px;align-items:center}
.logo{width:56px;height:56px;border-radius:12px;background:linear-gradient(135deg,var(--accent),var(--accent2));display:flex;align-items:center;justify-content:center;font-weight:900;color:#02121a;font-size:20px}
.h1{font-size:18px;margin:0}
.hint{color:var(--muted);font-size:13px}

.grid{display:grid;grid-template-columns:1fr 360px;gap:12px;margin-top:12px}
@media(max-width:900px){ .grid{grid-template-columns:1fr} .rightCol{order:2} }

.card{background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.006)); border-radius:10px;padding:12px;border:1px solid rgba(255,255,255,0.03)}
.powerList{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.btn{background:#081021;border:1px solid rgba(255,255,255,0.04);color:var(--text);padding:10px;border-radius:8px;font-weight:700;cursor:pointer}
.btn:disabled{opacity:.5;cursor:not-allowed}
.row{display:flex;gap:8px;align-items:center}
.col{flex:1}
.stat{font-size:13px;color:var(--muted)}
.avatar{width:78px;height:78px;border-radius:12px;background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));display:flex;align-items:center;justify-content:center;font-size:38px;transition:transform .24s ease}
.hpbar{height:12px;background:#071219;border-radius:8px;overflow:hidden;border:1px solid rgba(255,255,255,0.03)}
.fill{height:100%;transition:width .35s linear, background .3s linear;background:linear-gradient(90deg,#46d0b9,#1aa08c)}
.fill.enemy{background:linear-gradient(90deg,#ff7b7b,#ff4d4d)}
.log{height:260px;overflow:auto;padding:8px;background:linear-gradient(180deg, rgba(255,255,255,0.01), transparent);border-radius:8px;font-size:13px;color:var(--muted)}
.controls{display:flex;gap:8px;flex-wrap:wrap;margin-top:8px}
.small{font-size:13px;color:var(--muted)}
.note{font-size:12px;color:var(--muted);margin-top:8px}
.floating{position:fixed;pointer-events:none;font-weight:900;text-shadow:0 8px 24px rgba(0,0,0,.6);animation:floatUp 900ms ease-out forwards}
@keyframes floatUp{from{opacity:1;transform:translate(-50%,0) scale(1)}to{opacity:0;transform:translate(-50%,-60px) scale(1.02)}}
.badge{display:inline-block;padding:6px 10px;border-radius:999px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,255,255,0.03);font-size:13px}
.footer{display:flex;justify-content:space-between;align-items:center;margin-top:12px}
.endTitle{font-size:18px;margin:0}
.center{display:flex;justify-content:center;align-items:center}
.hidden{display:none}
.actionBtn{flex:1;padding:10px;border-radius:8px;background:#08121a;border:1px solid rgba(255,255,255,0.04);cursor:pointer}
.actionBtn:disabled{opacity:.45;cursor:not-allowed}
.placeSmall{font-size:12px;color:var(--muted);margin-top:6px}

/* attack animation */
.attackAnim{position:fixed;padding:8px 10px;border-radius:8px;background:rgba(255,255,255,0.03);font-weight:900;z-index:9999;transform:translate(-50%,-50%);transition:transform .45s cubic-bezier(.2,.9,.2,1),opacity .45s}
@keyframes shake {
  0%{ transform: translateX(0) }
  25%{ transform: translateX(-6px) }
  50%{ transform: translateX(6px) }
  75%{ transform: translateX(-3px) }
  100%{ transform: translateX(0) }
}
.shake{animation:shake .45s linear}

/* glow on big hit */
.glow{
  box-shadow: 0 0 18px rgba(255,120,120,0.18), inset 0 0 12px rgba(255,255,255,0.02);
  transition: box-shadow .25s ease;
}

/* puzzle visuals */
.puzzleBox{display:flex;gap:12px;align-items:center}
.puzzleCard{background:rgba(255,255,255,0.02);padding:10px;border-radius:10px;border:1px solid rgba(255,255,255,0.03)}
.choiceBtn{display:flex;align-items:center;gap:8px;padding:10px;border-radius:8px;background:#081026;border:1px solid rgba(255,255,255,0.03);cursor:pointer}
.choiceIcon{font-size:20px;width:36px;height:36px;border-radius:8px;background:rgba(255,255,255,0.02);display:flex;align-items:center;justify-content:center}
.choiceBtn.correct{outline:2px solid rgba(102,244,178,0.18)}
.choiceBtn.wrong{outline:2px solid rgba(255,120,120,0.12);opacity:0.85}
.fadeIn{animation:fadeIn .28s ease}
@keyframes fadeIn{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}
</style>
</head>
<body>
<div class="app" role="application" aria-label="Mutant Academy Danger Room v2.2">
  <div class="header">
    <div class="title">
      <div class="logo">MA</div>
      <div>
        <h1 class="h1">Mutant Academy — Danger Room</h1>
        <div class="hint">V2.2 — puzzles visuels, récupération PV entre épreuves, pouvoir utilisable 2×.</div>
      </div>
    </div>
    <div class="badge">v2.2 — équilibrage & puzzle</div>
  </div>

  <div class="grid">
    <!-- LEFT: main flow -->
    <div>
      <div class="card" id="startCard">
        <div style="display:flex;justify-content:space-between;align-items:center">
          <div>
            <div class="small">1 • Choisis ton pouvoir</div>
            <div style="margin-top:8px" class="small">Chaque pouvoir est <b>usage unique</b>, utilisable <b>2 fois</b> (entraînement + final).</div>
          </div>
          <div class="badge" id="chosenBadge">Aucun</div>
        </div>

        <div style="margin-top:10px" class="powerList" id="powerList"></div>

        <hr style="border:none;border-top:1px solid rgba(255,255,255,0.03);margin:12px 0">

        <div style="display:flex;gap:8px;align-items:center">
          <div class="small">2 • Choisis la difficulté</div>
          <select id="difficultySelect" class="badge" style="margin-left:auto">
            <option value="facile">😃 Facile</option>
            <option value="normal" selected>😐 Normal</option>
            <option value="difficile">😈 Difficile</option>
          </select>
        </div>

        <div style="margin-top:12px" class="controls">
          <button id="btnStart" class="btn" disabled>▶️ Démarrer la session</button>
          <button id="btnHelp" class="btn" onclick="showHelp()">❔ Aide</button>
        </div>
        <div class="note">Nouvelle mécanique : après chaque épreuve, tu récupères <b>+8 PV</b> (jusqu'au max).</div>
      </div>

      <div id="gameCard" class="card hidden" style="margin-top:12px">
        <div style="display:flex;justify-content:space-between;align-items:center">
          <div>
            <div class="small">Épreuve</div>
            <div id="stageTitle" style="font-weight:800;margin-top:6px">—</div>
          </div>
          <div class="badge" id="sessionBadge">Score: 0</div>
        </div>

        <div id="challengeArea" style="margin-top:12px"></div>

        <div id="actionArea" style="margin-top:12px" class="controls"></div>

        <div style="margin-top:12px" class="small">Historique</div>
        <div id="log" class="log" aria-live="polite"></div>
      </div>

      <div id="endCard" class="card hidden" style="margin-top:12px;text-align:center">
        <h2 id="endTitle" class="endTitle">—</h2>
        <p id="endText" class="small"></p>
        <div style="margin-top:10px"><button class="btn" onclick="location.reload()">🔁 Rejouer</button></div>
      </div>
    </div>

    <!-- RIGHT: player & enemy -->
    <div class="rightCol">
      <div class="card">
        <div style="display:flex;gap:8px;align-items:center">
          <div>
            <div class="avatar" id="playerAvatar">🦸</div>
          </div>
          <div style="flex:1">
            <div style="display:flex;justify-content:space-between;align-items:center">
              <div><strong id="playerName">Élève</strong></div>
              <div class="stat">PV: <span id="playerPV">0</span>/<span id="playerMax">0</span></div>
            </div>
            <div class="hpbar" style="margin-top:8px"><div id="playerFill" class="fill" style="width:100%"></div></div>
            <div class="placeSmall" id="powerNote">Pouvoir: — (2 usages restants)</div>
          </div>
        </div>
      </div>

      <div id="enemyCard" class="card hidden" style="margin-top:12px">
        <div style="display:flex;gap:8px;align-items:center">
          <div class="avatar" id="enemyAvatar">🤖</div>
          <div style="flex:1">
            <div style="display:flex;justify-content:space-between;align-items:center">
              <div><strong id="enemyName">Ennemi</strong></div>
              <div class="stat">PV: <span id="enemyPV">0</span>/<span id="enemyMax">0</span></div>
            </div>
            <div class="hpbar" style="margin-top:8px"><div id="enemyFill" class="fill enemy" style="width:0%"></div></div>
            <div class="placeSmall" id="enemyNote">—</div>
          </div>
        </div>
      </div>

      <div class="card" style="margin-top:12px">
        <div class="small">Raccourcis</div>
        <div style="margin-top:8px;display:flex;gap:8px">
          <button class="btn" id="btnUsePower" disabled>✨ Utiliser pouvoir</button>
          <button class="btn" id="btnStatus" onclick="showStatus()">📋 Statut</button>
        </div>
        <div class="note" style="margin-top:8px">Rappel : le pouvoir est utilisable <b>2 fois</b> (1× en entraînement, 1× en final).</div>
      </div>
    </div>
  </div>

</div>

<script>
/* ================= Data ================= */
const POWERS = {
  telekinesis:{id:'telekinesis',name:'Télékinésie',emoji:'🧠',desc:'Augmente l’esquive ennemie (30%) pendant 1 tour',uses:2},
  claws:{id:'claws',name:'Griffes',emoji:'🗡️',desc:'Prochaine attaque inflige +8 dégâts (utilisable 2×)',uses:2},
  speed:{id:'speed',name:'Vitesse',emoji:'⚡',desc:'Donne 1 action supplémentaire ce tour (utilisable 2×)',uses:2},
  ice:{id:'ice',name:'Glace',emoji:'❄️',desc:'Gèle l’ennemi 1 tour (utilisable 2×)',uses:2},
  pyro:{id:'pyro',name:'Pyro',emoji:'🔥',desc:'Applique brûlure (2 tours, 3 dégâts/turn) (utilisable 2×)',uses:2}
};

const VILLAINS = [
  {id:'magneto',name:'Magneto',emoji:'🧲',pv:36,dmg:[3,7],note:'Réduit l’efficacité des armes (aléa)'},
  {id:'mystique',name:'Mystique',emoji:'🌀',pv:28,dmg:[2,6],note:'Peut imiter une action aléatoire'},
  {id:'sentinel',name:'sentinel',emoji:'🤖',pv:44,dmg:[4,9],note:'Attaques lourdes mais lentes'}
];

/* ================= State ================= */
let state = {
  difficulty:'normal',
  chosenPower:null,
  powerUsesLeft:2, // global: two uses total
  player:{pv:0,max:0,avatar:'🦸',name:'Novice',powerAvailable:true,clawsBoost:false,extraAction:false,evade:0},
  enemy:null,
  score:0,
  stage:0,
  challenges:[],
  _rescue:null,
  _quiz:null
};

/* ================= Elements ================= */
const powerListEl = document.getElementById('powerList');
const btnStart = document.getElementById('btnStart');
const difficultySelect = document.getElementById('difficultySelect');
const chosenBadge = document.getElementById('chosenBadge');
const sessionBadge = document.getElementById('sessionBadge');
const challengeArea = document.getElementById('challengeArea');
const actionArea = document.getElementById('actionArea');
const logEl = document.getElementById('log');
const playerAvatar = document.getElementById('playerAvatar');
const enemyCard = document.getElementById('enemyCard');

/* ================= Helpers (UI & animation) ================= */
function log(msg){
  const d=document.createElement('div'); d.className='small fadeIn'; d.innerHTML=msg; logEl.appendChild(d); logEl.scrollTop=logEl.scrollHeight;
}
function spawnFloatingOver(el,txt,color='white'){
  if(!el) return;
  const r = el.getBoundingClientRect();
  const f = document.createElement('div'); f.className='floating'; f.textContent=txt; f.style.left=(r.left+r.width/2)+'px'; f.style.top=(r.top+8)+'px'; f.style.color=color;
  document.body.appendChild(f); setTimeout(()=>f.remove(),900);
}
function animateAttack(fromEl,toEl,icon,cb){
  if(!fromEl || !toEl){ if(cb) cb(); return; }
  const r1 = fromEl.getBoundingClientRect();
  const r2 = toEl.getBoundingClientRect();
  const anim = document.createElement('div'); anim.className='attackAnim'; anim.textContent = icon; anim.style.left = (r1.left + r1.width/2)+'px'; anim.style.top = (r1.top + r1.height/2)+'px';
  anim.style.opacity = 1; anim.style.transform = 'translate(-50%,-50%) scale(1.0)';
  document.body.appendChild(anim);
  requestAnimationFrame(()=>{
    anim.style.transform = `translate(${r2.left + r2.width/2 - (r1.left + r1.width/2)}px, ${r2.top + r2.height/2 - (r1.top + r1.height/2)}px) scale(1.0)`;
    anim.style.opacity = 0.95;
  });
  setTimeout(()=>{
    toEl.classList.add('glow'); setTimeout(()=>toEl.classList.remove('glow'),220);
    anim.remove(); if(cb) cb();
  },420);
}
function screenShake(){
  const app = document.querySelector('.app');
  app.classList.add('shake');
  setTimeout(()=>app.classList.remove('shake'),420);
}

/* ================= UI update functions ================= */
function updatePlayerUI(){
  document.getElementById('playerPV').textContent = state.player.pv;
  document.getElementById('playerMax').textContent = state.player.max;
  document.getElementById('playerFill').style.width = Math.max(0,(state.player.pv/state.player.max*100))+'%';
  playerAvatar.textContent = state.player.avatar;
  document.getElementById('chosenBadge').textContent = state.chosenPower ? (state.chosenPower.emoji+' '+state.chosenPower.name) : 'Aucun';
  document.getElementById('powerNote').textContent = state.chosenPower ? `${state.chosenPower.desc} — usages restants: ${state.powerUsesLeft}` : 'Pouvoir: —';
  sessionBadge.textContent = 'Score: '+state.score;
  document.getElementById('btnUsePower').disabled = !(state.player.powerAvailable && state.powerUsesLeft>0);
}
function updateEnemyUI(){
  if(!state.enemy) { enemyCard.classList.add('hidden'); return; }
  enemyCard.classList.remove('hidden');
  document.getElementById('enemyName').textContent = state.enemy.emoji+' '+state.enemy.name;
  document.getElementById('enemyPV').textContent = state.enemy.pv;
  document.getElementById('enemyMax').textContent = state.enemy.max;
  document.getElementById('enemyFill').style.width = Math.max(0,(state.enemy.pv/state.enemy.max*100))+'%';
  document.getElementById('enemyNote').textContent = state.enemy.note || '';
  document.getElementById('enemyAvatar').textContent = state.enemy.emoji;
}

/* ================= Build power buttons ================= */
function buildPowerButtons(){
  powerListEl.innerHTML='';
  Object.values(POWERS).forEach(p=>{
    const btn = document.createElement('button');
    btn.className='btn';
    btn.innerHTML = `<div style="text-align:left"><strong>${p.emoji} ${p.name}</strong><div class="small" style="margin-top:6px">${p.desc}</div></div>`;
    btn.onclick = ()=>selectPower(p.id, btn);
    powerListEl.appendChild(btn);
  });
}
buildPowerButtons();

/* ================= Selection & start ================= */
function selectPower(id, btn){
  state.chosenPower = POWERS[id];
  state.player.avatar = state.chosenPower.emoji;
  // reset uses left to the default (2)
  state.powerUsesLeft = state.chosenPower.uses;
  state.player.powerAvailable = true;
  Array.from(powerListEl.children).forEach(b=>b.style.opacity=.45);
  btn.style.opacity=1;
  btnStart.disabled = false;
  updatePlayerUI();
  log(`✨ Pouvoir choisi : ${state.chosenPower.name} — usages : ${state.powerUsesLeft}`);
}
btnStart.onclick = ()=>{
  if(!state.chosenPower) return alert('Choisis un pouvoir avant de démarrer.');
  state.difficulty = difficultySelect.value;
  beginSession();
};

/* ================= Session flow ================= */
function beginSession(){
  const basePV = state.difficulty==='facile'?48:(state.difficulty==='difficile'?32:40);
  state.player.pv = basePV; state.player.max = basePV;
  state.score = 0; state.stage = 0; state.challenges = [];
  const pool = ['combat','rescue','puzzle'];
  for(let i=0;i<3;i++) state.challenges.push(pool[Math.floor(Math.random()*pool.length)]);
  state.player.clawsBoost = false; state.player.extraAction=false; state.player.evade=0;
  state.player.powerAvailable = (state.powerUsesLeft>0);
  state.chosenPower.usage = false;
  document.getElementById('startCard').classList.add('hidden');
  document.getElementById('gameCard').classList.remove('hidden');
  logEl.innerHTML=''; log('🔰 Session débutée — Danger Room active');
  nextChallenge();
  updatePlayerUI(); updateEnemyUI();
}

/* ================= Challenge dispatcher ================= */
function nextChallenge(){
  // if stage >=3, final
  if(state.stage < 3){
    const ch = state.challenges[state.stage];
    document.getElementById('stageTitle').textContent = `Entraînement — épreuve ${state.stage+1}/3 : ${capitalize(ch)}`;
    if(ch === 'combat') startTrainingCombat();
    else if(ch === 'rescue') startTrainingRescue();
    else startTrainingPuzzle();
  } else {
    prepareFinal();
  }
}

/* ================= Training Combat (balanced) ================= */
function startTrainingCombat(){
  // make first combats slightly easier: lower dmg and pv depending on difficulty
  const botPV = state.difficulty==='facile'?12:(state.difficulty==='difficile'?16:14);
  const botDmg = state.difficulty==='difficile'? [3,6]:[2,4];
  state.enemy = {name:'Robot d’entraînement',emoji:'🤖',pv:botPV,max:botPV,dmg:botDmg,note:'Bot — IA d’entraînement',frozen:false,burn:0};
  updateEnemyUI(); log('🤖 Épreuve Combat : neutralise le robot.');
  renderCombat(true);
}

/* ================= Training Rescue ================= */
function startTrainingRescue(){
  state.enemy = null; updateEnemyUI();
  const correct = Math.floor(Math.random()*3)+1;
  state._rescue = {correct};
  challengeArea.innerHTML = `<div class="small puzzleBox"><div class="puzzleCard"><strong>🚪 Sauvetage</strong><div class="small" style="margin-top:6px">Un otage est caché derrière 1 des 3 portes. Choisis une porte.</div></div></div>`;
  actionArea.innerHTML = '';
  for(let i=1;i<=3;i++){
    const b = document.createElement('button'); b.className='actionBtn'; b.textContent='Porte '+i; b.onclick = ()=>resolveRescue(i);
    actionArea.appendChild(b);
  }
  log('🚪 Épreuve Sauvetage : choisis la bonne porte.');
}

/* ================= Training Puzzle (visuel & icons) ================= */
const QUIZZES = {
  facile:[
    {q:'Quelle tactique est la meilleure pour esquiver rapidement ?',choices:[{t:'Attaque directe',i:'⚔️'},{t:'Esquive latérale',i:'↩️'},{t:'Crier',i:'🗣️'}],a:1},
  ],
  normal:[
    {q:'Quelle option neutralise au mieux plusieurs cibles ?',choices:[{t:'Fuir',i:'🏃'},{t:'Zone d\'effet',i:'💥'},{t:'Attaque précise',i:'🎯'}],a:1},
    {q:'Lors d’une embuscade, quelle est la priorité ?',choices:[{t:'Frapper fort',i:'💥'},{t:'Analyser',i:'🔎'},{t:'Se cacher',i:'🕳️'}],a:1}
  ],
  difficile:[
    {q:'Comment contrer un ennemi blindé efficacement ?',choices:[{t:'Attaquer source énergie',i:'🔌'},{t:'Coup aléatoire',i:'❓'},{t:'Reculer',i:'⬅️'}],a:0},
    {q:'Quel mouvement réduit les chances d’être touché par tirs automatiques ?',choices:[{t:'Rester immobile',i:'🧍'},{t:'Se couvrir puis bouger',i:'🛡️'},{t:'Crier',i:'🗣️'}],a:1}
  ]
};
function startTrainingPuzzle(){
  const pool = state.difficulty==='facile'?QUIZZES.facile:(state.difficulty==='difficile'?QUIZZES.difficile:QUIZZES.normal);
  const q = pool[Math.floor(Math.random()*pool.length)];
  state._quiz = q;
  // render puzzle visually
  challengeArea.innerHTML = `<div class="puzzleCard"><strong>❓ Question</strong><div class="small" style="margin-top:8px">${q.q}</div></div>`;
  actionArea.innerHTML = '';
  q.choices.forEach((c,i)=>{
    const b = document.createElement('div'); b.className='choiceBtn fadeIn'; b.onclick = ()=>resolveQuiz(i,b);
    b.innerHTML = `<div class="choiceIcon">${c.i}</div><div style="text-align:left"><div style="font-weight:700">${c.t}</div></div>`;
    actionArea.appendChild(b);
  });
  log('🧠 Épreuve Stratégie : choisis la meilleure réponse (visuel).');
}

/* ================= Resolvers for Rescue & Puzzle ================= */
function resolveRescue(choice){
  actionArea.innerHTML='';
  if(choice === state._rescue.correct){
    log('🟢 Sauvetage réussi — otage sécurisé.');
    spawnFloatingOver(playerAvatar,'+10','lightgreen'); state.score += 10;
  } else {
    log('🔴 Mauvaise porte — simulation piège : légère blessure.');
    spawnFloatingOver(playerAvatar,'-6','red'); state.player.pv -= 6; state.score -= 2; if(state.player.pv<0) state.player.pv=0; updatePlayerUI();
  }
  // after each challenge: heal +8 (cap at max)
  setTimeout(()=>{ postChallengeHeal(); },600);
}

/* Puzzle resolver */
function resolveQuiz(choiceIdx, el){
  // visual feedback
  const q = state._quiz;
  const children = Array.from(actionArea.children);
  children.forEach((c,idx)=>{ c.classList.remove('correct','wrong'); if(idx===choiceIdx) c.classList.add('fadeIn'); });
  if(choiceIdx === q.a){
    el.classList.add('correct');
    log('🟢 Bonne réponse — tactique efficace.');
    state.score += 6;
  } else {
    el.classList.add('wrong');
    log('🔴 Mauvaise réponse — légère fatigue.');
    state.player.pv -= 4; if(state.player.pv<0) state.player.pv=0; state.score -= 1; updatePlayerUI();
  }
  // disable further clicks
  Array.from(actionArea.children).forEach(b=>b.onclick=null);
  // heal after brief pause
  setTimeout(()=>{ postChallengeHeal(); },700);
}

/* ========== Combat rendering & logic (shared) ========== */
function renderCombat(isTraining){
  updatePlayerUI(); updateEnemyUI();
  challengeArea.innerHTML = `<div class="small"><b>${state.enemy.emoji} ${state.enemy.name}</b></div><div class="small" id="enemyPVtxt">PV: ${state.enemy.pv}/${state.enemy.max}</div>`;
  actionArea.innerHTML = '';
  const a1 = document.createElement('button'); a1.className='actionBtn'; a1.textContent='⚔️ Coup léger (2-4)'; a1.onclick = ()=>playerAttack('light');
  const a2 = document.createElement('button'); a2.className='actionBtn'; a2.textContent='💥 Coup fort (4-7)'; a2.onclick = ()=>playerAttack('heavy');
  const a3 = document.createElement('button'); a3.className='actionBtn'; a3.textContent='🛡️ Défendre (réduit dégâts)'; a3.onclick = ()=>playerDefend();
  actionArea.appendChild(a1); actionArea.appendChild(a2); actionArea.appendChild(a3);
  const useBtn = document.getElementById('btnUsePower');
  useBtn.disabled = !(state.player.powerAvailable && state.powerUsesLeft>0);
  useBtn.onclick = ()=>{ usePower(); document.getElementById('btnUsePower').disabled=true; };
}

/* Player actions with animations */
function playerAttack(kind){
  let dmg = kind==='light'? rand(2,4): rand(4,7);
  if(state.player.clawsBoost){ dmg += 8; state.player.clawsBoost=false; log('🗡️ Griffes : attaque renforcée (+8)'); }
  if(state.enemy && Math.random()<0.08 && state.difficulty==='difficile'){ dmg = Math.max(0,dmg-2); log('🔰 Résilience adverse réduit les dégâts.'); }
  if(state.enemy){
    animateAttack(document.getElementById('playerAvatar'), document.getElementById('enemyFill'), state.player.avatar, ()=>{
      state.enemy.pv -= dmg; if(state.enemy.pv<0) state.enemy.pv=0;
      updateEnemyUI();
      log(`🦸 Tu infliges ${dmg} PV à ${state.enemy.name}`);
      spawnFloatingOver(document.getElementById('enemyFill'),`-${dmg}`,'#ffcccc');
      if(dmg>=10) screenShake();
      if(state.enemy.name.includes('Robot')) state.score += 2;
      if(state.player.extraAction){
        state.player.extraAction = false; log('🔁 Action supplémentaire utilisée (pas de riposte immédiate).'); updatePlayerUI(); return;
      }
      setTimeout(()=>enemyReact(),420);
    });
  } else {
    log('ℹ️ Pas d’ennemi présent.');
  }
}

/* defend */
function playerDefend(){
  state.player.evade = Math.min(0.6, (state.player.evade||0) + 0.25);
  log('🛡️ Tu te protèges — prochaine attaque réduite.');
  setTimeout(()=>enemyReact(),300);
}

/* use power (2 uses) */
function usePower(){
  if(!(state.player.powerAvailable && state.powerUsesLeft>0 && state.chosenPower)) return;
  const p = state.chosenPower;
  log(`✨ Tu actives ${p.emoji} ${p.name} — ${p.desc}`);
  animateAttack(document.getElementById('playerAvatar'), state.enemy ? document.getElementById('enemyFill') : document.getElementById('playerFill'), p.emoji, ()=>{
    if(p.id==='telekinesis'){ state.player.evade += 0.3; log('🔮 Télékinésie : evade +30% pour une attaque ennemie.'); }
    else if(p.id==='claws'){ state.player.clawsBoost = true; log('🗡️ Griffes activées : prochaine attaque +8.'); }
    else if(p.id==='speed'){ state.player.extraAction = true; log('⚡ Vitesse : action supplémentaire disponible.'); }
    else if(p.id==='ice'){ if(state.enemy){ state.enemy.frozen = true; log('❄️ Glace : l’ennemi sera gelé une fois.'); } }
    else if(p.id==='pyro'){ if(state.enemy){ state.enemy.burn = 2; log('🔥 Pyro : brûlure 2 tours infligée.'); } }
    state.powerUsesLeft--; state.player.powerAvailable = (state.powerUsesLeft>0);
    updatePlayerUI();
    // if not extraAction, enemy reacts
    if(!state.player.extraAction) setTimeout(()=>enemyReact(),420);
  });
}

/* enemy react */
function enemyReact(){
  if(!state.enemy){
    // no enemy -> finish
    log('ℹ️ Aucun ennemi — épreuve terminée.');
    state.stage++; setTimeout(()=>postChallengeHeal(),550);
    return;
  }
  if(state.enemy.frozen){
    log(`❄️ ${state.enemy.name} est gelé et rate son action !`);
    state.enemy.frozen = false;
    if(state.enemy.burn && state.enemy.burn>0){ state.enemy.pv -= 3; state.enemy.burn--; log(`🔥 Brûlure : ${state.enemy.name} subit 3 PV`); spawnFloatingOver(document.getElementById('enemyFill'),'-3','#ffb86b'); updateEnemyUI(); }
    checkCombatEnd(); return;
  }
  const dmgBase = rand(state.enemy.dmg[0], state.enemy.dmg[1]);
  const evade = state.player.evade || 0;
  const reduced = Math.round(dmgBase * evade);
  const final = Math.max(0, dmgBase - reduced);
  animateAttack(document.getElementById('enemyAvatar'), document.getElementById('playerFill'), state.enemy.emoji, ()=>{
    state.player.pv -= final; if(state.player.pv<0) state.player.pv=0;
    log(`💥 ${state.enemy.name} riposte : ${final} PV infligés.`);
    spawnFloatingOver(document.getElementById('playerFill'),`-${final}`,'#ff9aa2');
    state.player.evade = 0;
    if(state.enemy.burn && state.enemy.burn>0){ state.enemy.pv -= 3; state.enemy.burn--; log(`🔥 Brûlure : ${state.enemy.name} subit 3 PV`); spawnFloatingOver(document.getElementById('enemyFill'),'-3','#ffb86b'); updateEnemyUI(); }
    updatePlayerUI(); checkCombatEnd();
    if(final >= 7) screenShake();
  });
}

/* check combat end */
function checkCombatEnd(){
  if(state.enemy && state.enemy.pv <= 0){
    log(`🏁 ${state.enemy.name} neutralisé !`);
    state.score += (state.enemy.name.includes('Robot')? 8 : 20);
    state.enemy = null; updateEnemyUI();
    state.stage++; setTimeout(()=>postChallengeHeal(),700);
    return;
  }
  if(state.player.pv <= 0){
    log('💀 Tu es K.O. — session interrompue.');
    conclude(false);
  }
}

/* post-challenge heal (recover +8 PV bounded) */
function postChallengeHeal(){
  const before = state.player.pv;
  const heal = 8;
  state.player.pv = Math.min(state.player.max, state.player.pv + heal);
  updatePlayerUI();
  log(`💚 Récupération : +${state.player.pv - before} PV (auto-recharge entre épreuves).`);
  // continue to next challenge or final
  if(state.stage < 3) nextChallenge();
  else prepareFinal();
}

/* prepare final boss */
function prepareFinal(){
  document.getElementById('stageTitle').textContent = 'Combat final — Simulateur';
  const v = VILLAINS[Math.floor(Math.random()*VILLAINS.length)];
  const mul = state.difficulty==='difficile'?1.1:(state.difficulty==='facile'?0.9:1);
  state.enemy = {name:v.name,emoji:v.emoji,pv:Math.round(v.pv * mul),max:Math.round(v.pv * mul),dmg:v.dmg,note:v.note,frozen:false,burn:0};
  log(`⚠️ Combat final : ${v.name} simulé — ${v.note}`);
  // Allow one final power usage if a use remains (powerUsesLeft may be 1 or 2)
  state.player.powerAvailable = state.powerUsesLeft>0;
  updatePlayerUI();
  renderCombat(false);
}

/* conclude final */
function conclude(victory){
  document.getElementById('gameCard').classList.add('hidden');
  document.getElementById('endCard').classList.remove('hidden');
  let title='', text='';
  if(!victory){
    title='💥 Simulation échouée';
    text=`Tu as été dépassé par le simulateur. Score final : ${state.score}. Recommence l'entraînement.`;
  } else {
    if(state.score >= 70){ title='🏆 Admis avec mention'; text=`Excellent — tu rejoins les X-Men comme membre prometteur.<br>Score: ${state.score}`; }
    else if(state.score >= 45){ title='✅ Admis à l’Académie'; text=`Bon travail — admis pour formation avancée.<br>Score: ${state.score}`; }
    else if(state.score >= 25){ title='⚠️ Admis en formation'; text=`Tu as réussi mais tu dois t’entraîner davantage.<br>Score: ${state.score}`; }
    else { title='🔰 En formation (recalé temporaire)'; text=`Tu n’as pas atteint le niveau requis — réessaie.<br>Score: ${state.score}`; }
  }
  document.getElementById('endTitle').textContent = title;
  document.getElementById('endText').innerHTML = text;
}

/* utility functions */
function rand(min,max){ return Math.floor(Math.random()*(max-min+1))+min; }
function capitalize(s){ return s.charAt(0).toUpperCase()+s.slice(1); }
function showHelp(){ alert('Mutant Academy — Danger Room (V2.2)\\n\\n• Choisis un pouvoir (2 usages au total).\\n• Passe 3 épreuves (combat, sauvetage, puzzle).\\n• Tu récupères +8 PV entre épreuves.\\n• Utilise ton pouvoir stratégiquement (2 usages).'); }
function showStatus(){ alert(`PV: ${state.player.pv}/${state.player.max}\\nScore: ${state.score}\\nPouvoir: ${state.chosenPower?state.chosenPower.name:'—'}\\nUsages restants: ${state.powerUsesLeft}`); }

/* init hooks */
document.getElementById('btnUsePower').onclick = ()=>{ usePower(); document.getElementById('btnUsePower').disabled = true; };
updatePlayerUI(); updateEnemyUI();
log('ℹ️ Chargement prêt — choisis ton pouvoir pour commencer.');
</script>
</body>
</html>
