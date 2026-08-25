#
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>やりたいことリスト</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Zen+Kaku+Gothic+New:wght@400;500;700;900&family=Shippori+Mincho:wght@500;700&display=swap');

  :root{
    --sky-1:#0f1235;
    --sky-2:#1b1f52;
    --sky-3:#2a2f78;
    --gold:#f2c879;
    --gold-soft:#f2c87955;
    --cream:#f5f1e6;
    --cream-dim:#d9d4c4;
    --done:#7c8bd9;
    --dawn-1:#fff2d6;
    --dawn-2:#ffd98a;
    --dawn-3:#f6a35c;
  }

  *{box-sizing:border-box; -webkit-tap-highlight-color:transparent;}

  html,body{
    margin:0; padding:0; height:100%;
    font-family:'Zen Kaku Gothic New', sans-serif;
    background:
      radial-gradient(1px 1px at 20% 30%, #fff8 50%, transparent 51%),
      radial-gradient(1px 1px at 70% 20%, #fff6 50%, transparent 51%),
      radial-gradient(1.5px 1.5px at 40% 70%, #fffa 50%, transparent 51%),
      radial-gradient(1px 1px at 85% 60%, #fff7 50%, transparent 51%),
      radial-gradient(1px 1px at 10% 80%, #fff5 50%, transparent 51%),
      radial-gradient(1.5px 1.5px at 60% 45%, #fff9 50%, transparent 51%),
      radial-gradient(1px 1px at 90% 85%, #fff6 50%, transparent 51%),
      linear-gradient(160deg, var(--sky-1), var(--sky-2) 55%, var(--sky-3));
    color:var(--cream);
    min-height:100vh;
    transition: background 1.4s ease;
    overflow-x:hidden;
  }

  body.dawn{
    background: linear-gradient(160deg, var(--dawn-1), var(--dawn-2) 55%, var(--dawn-3));
    color:#4a2f12;
  }

  .wrap{
    max-width:480px;
    margin:0 auto;
    padding:36px 20px 60px;
    min-height:100vh;
    display:flex;
    flex-direction:column;
  }

  header{ margin-bottom:22px; }

  .eyebrow{
    font-size:12px;
    letter-spacing:.28em;
    color:var(--gold);
    font-weight:700;
    margin:0 0 6px;
    transition:color .8s ease;
  }
  body.dawn .eyebrow{ color:#a8631f; }

  h1{
    font-family:'Shippori Mincho', serif;
    font-size:30px;
    font-weight:700;
    margin:0 0 4px;
    letter-spacing:.03em;
  }

  .sub{
    font-size:13px;
    color:var(--cream-dim);
    margin:0;
  }
  body.dawn .sub{ color:#7a5a2e; }

  .counter{
    margin-top:18px;
    display:flex;
    align-items:baseline;
    gap:10px;
  }
  .counter .num{
    font-family:'Shippori Mincho', serif;
    font-size:42px;
    font-weight:700;
    color:var(--gold);
    line-height:1;
    transition:color .8s ease;
  }
  body.dawn .counter .num{ color:#c97a1f; }
  .counter .label{ font-size:12px; color:var(--cream-dim); }
  body.dawn .counter .label{ color:#7a5a2e; }

  .track{
    height:3px;
    border-radius:2px;
    background:#ffffff22;
    margin-top:14px;
    overflow:hidden;
  }
  body.dawn .track{ background:#ffffff55; }
  .track-fill{
    height:100%;
    width:0%;
    background:linear-gradient(90deg, var(--gold), #fff2c2);
    transition:width .5s cubic-bezier(.2,.8,.3,1);
  }

  form{
    display:flex;
    gap:8px;
    margin:26px 0 20px;
  }
  input[type=text]{
    flex:1;
    background:#ffffff12;
    border:1px solid #ffffff2a;
    border-radius:12px;
    padding:13px 14px;
    color:var(--cream);
    font-size:15px;
    font-family:inherit;
    outline:none;
    transition:border-color .2s;
  }
  body.dawn input[type=text]{
    background:#ffffff55;
    border:1px solid #00000022;
    color:#4a2f12;
  }
  input[type=text]::placeholder{ color:#ffffff77; }
  body.dawn input[type=text]::placeholder{ color:#7a5a2e88; }
  input[type=text]:focus{ border-color:var(--gold); }

  button.add{
    background:var(--gold);
    color:#1b1f52;
    border:none;
    border-radius:12px;
    padding:0 20px;
    font-weight:700;
    font-size:15px;
    cursor:pointer;
    font-family:inherit;
  }
  button.add:active{ transform:scale(.96); }

  ul.items{
    list-style:none;
    margin:0;
    padding:0;
    display:flex;
    flex-direction:column;
    gap:10px;
    flex:1;
  }

  li.item{
    display:flex;
    align-items:center;
    gap:12px;
    background:#ffffff0d;
    border:1px solid #ffffff1c;
    border-radius:14px;
    padding:14px 14px;
    animation:rise .35s ease;
  }
  body.dawn li.item{
    background:#ffffff55;
    border:1px solid #00000018;
  }

  @keyframes rise{
    from{ opacity:0; transform:translateY(8px); }
    to{ opacity:1; transform:translateY(0); }
  }

  .chk{
    width:24px; height:24px;
    min-width:24px;
    border-radius:50%;
    border:2px solid var(--gold-soft);
    display:flex; align-items:center; justify-content:center;
    cursor:pointer;
    transition:all .2s;
    font-size:13px;
    color:transparent;
  }
  body.dawn .chk{ border:2px solid #c97a1f88; }
  li.done .chk{
    background:var(--gold);
    border-color:var(--gold);
    color:#1b1f52;
  }

  .txt{
    flex:1;
    font-size:15px;
    line-height:1.4;
    word-break:break-word;
  }
  li.done .txt{
    text-decoration:line-through;
    color:var(--cream-dim);
    opacity:.7;
  }
  body.dawn li.done .txt{ color:#7a5a2e; }

  .del{
    background:none;
    border:none;
    color:#ffffff55;
    font-size:18px;
    cursor:pointer;
    padding:4px 6px;
    line-height:1;
  }
  body.dawn .del{ color:#00000044; }

  .empty{
    text-align:center;
    padding:60px 10px;
    color:var(--cream-dim);
    font-size:14px;
    line-height:1.8;
  }
  body.dawn .empty{ color:#7a5a2e; }
  .empty .big{
    font-size:34px;
    display:block;
    margin-bottom:10px;
  }

  .clear-bar{
    margin-top:22px;
    text-align:center;
  }
  .clear-btn{
    background:none;
    border:1px solid var(--gold-soft);
    color:var(--gold);
    padding:12px 22px;
    border-radius:999px;
    font-size:14px;
    font-weight:700;
    font-family:inherit;
    cursor:pointer;
    letter-spacing:.04em;
  }
  body.dawn .clear-btn{ border:1px solid #c97a1f; color:#a8631f; }
  .clear-btn:active{ transform:scale(.97); }

  /* celebration overlay */
  .celebrate{
    position:fixed; inset:0;
    display:none;
    align-items:center;
    justify-content:center;
    flex-direction:column;
    background:radial-gradient(circle at 50% 40%, #ffe9b0, #f6a35c 70%);
    z-index:50;
    text-align:center;
  }
  .celebrate.show{
    display:flex;
    animation:fadein .5s ease;
  }
  @keyframes fadein{ from{opacity:0;} to{opacity:1;} }

  .check-mark{
    font-size:96px;
    animation:pop .6s cubic-bezier(.3,1.6,.5,1);
  }
  @keyframes pop{
    0%{ transform:scale(0) rotate(-15deg); opacity:0; }
    60%{ transform:scale(1.15) rotate(4deg); opacity:1; }
    100%{ transform:scale(1) rotate(0); }
  }

  .celebrate h2{
    font-family:'Shippori Mincho', serif;
    font-size:24px;
    color:#4a2f12;
    margin:14px 0 4px;
  }
  .celebrate p{
    color:#7a5a2e;
    font-size:13px;
    margin:0 0 26px;
  }
  .celebrate button{
    background:#4a2f12;
    color:#fff2d6;
    border:none;
    padding:13px 30px;
    border-radius:999px;
    font-size:14px;
    font-weight:700;
    font-family:inherit;
    cursor:pointer;
  }

  .confetti{
    position:absolute;
    top:-10%;
    font-size:20px;
    animation:fall linear forwards;
  }
  @keyframes fall{
    to{ transform:translateY(115vh) rotate(360deg); opacity:.2; }
  }

  @media (prefers-reduced-motion: reduce){
    *{ animation-duration:.01ms !important; transition-duration:.01ms !important; }
  }
</style>
</head>
<body>

<div class="wrap">
  <header>
    <p class="eyebrow">WISH LIST · 夜空にひとつずつ</p>
    <h1>やりたいことリスト</h1>
    <p class="sub">思いついたことを星のように並べて、ひとつずつ叶えていく。</p>
    <div class="counter">
      <span class="num" id="doneCount">0</span>
      <span class="label">/ <span id="totalCount">0</span> 件 達成</span>
    </div>
    <div class="track"><div class="track-fill" id="trackFill"></div></div>
  </header>

  <form id="addForm">
    <input type="text" id="addInput" placeholder="やりたいことを入力…" maxlength="80" autocomplete="off">
    <button type="submit" class="add">追加</button>
  </form>

  <ul class="items" id="itemsList"></ul>
  <div class="empty" id="emptyState" style="display:none;">
    <span class="big">✨</span>
    まだ何もありません。<br>最初のひとつを書いてみましょう。
  </div>

  <div class="clear-bar" id="clearBar" style="display:none;">
    <button class="clear-btn" id="clearBtn">全部達成できた！リストをクリアする</button>
  </div>
</div>

<div class="celebrate" id="celebrate">
  <div class="check-mark">✅</div>
  <h2>ぜんぶ、やりきった。</h2>
  <p>リストがクリアされました</p>
  <button id="restartBtn">新しいリストを始める</button>
</div>

<script>
let items = [];
let loaded = false;

const itemsList = document.getElementById('itemsList');
const emptyState = document.getElementById('emptyState');
const clearBar = document.getElementById('clearBar');
const doneCount = document.getElementById('doneCount');
const totalCount = document.getElementById('totalCount');
const trackFill = document.getElementById('trackFill');
const celebrate = document.getElementById('celebrate');
const addForm = document.getElementById('addForm');
const addInput = document.getElementById('addInput');

async function saveItems(){
  try{
    await localStorage.set('todos', JSON.stringify(items));
  }catch(e){ console.error('save failed', e); }
}

async function loadItems(){
  try{
    const res = await window.storage.get('todos');
    if(res && res.value){ items = JSON.parse(res.value); }
  }catch(e){ /* no existing data */ }
  loaded = true;
  render();
}

function uid(){ return Math.random().toString(36).slice(2,9); }

function render(){
  itemsList.innerHTML = '';
  if(items.length === 0){
    emptyState.style.display = 'block';
    itemsList.style.display = 'none';
    clearBar.style.display = 'none';
  } else {
    emptyState.style.display = 'none';
    itemsList.style.display = 'flex';
    items.forEach(item => {
      const li = document.createElement('li');
      li.className = 'item' + (item.done ? ' done' : '');
      li.innerHTML = `
        <div class="chk" data-id="${item.id}">${item.done ? '✓' : ''}</div>
        <div class="txt">${escapeHtml(item.text)}</div>
        <button class="del" data-id="${item.id}">×</button>
      `;
      itemsList.appendChild(li);
    });
    const allDone = items.every(i => i.done);
    clearBar.style.display = allDone ? 'block' : 'none';
  }

  const done = items.filter(i => i.done).length;
  doneCount.textContent = done;
  totalCount.textContent = items.length;
  trackFill.style.width = items.length ? (done/items.length*100) + '%' : '0%';
}

function escapeHtml(str){
  const d = document.createElement('div');
  d.textContent = str;
  return d.innerHTML;
}

addForm.addEventListener('submit', async (e) => {
  e.preventDefault();
  const val = addInput.value.trim();
  if(!val) return;
  items.push({ id: uid(), text: val, done: false });
  addInput.value = '';
  render();
  saveItems();
});

itemsList.addEventListener('click', async (e) => {
  const chk = e.target.closest('.chk');
  const del = e.target.closest('.del');
  if(chk){
    const id = chk.dataset.id;
    const item = items.find(i => i.id === id);
    if(item) item.done = !item.done;
    render();
    await saveItems();
  } else if(del){
    const id = del.dataset.id;
    items = items.filter(i => i.id !== id);
    render();
    await saveItems();
  }
});

document.getElementById('clearBtn').addEventListener('click', async () => {
  items = [];
  await saveItems();
  triggerCelebration();
});

document.getElementById('restartBtn').addEventListener('click', () => {
  celebrate.classList.remove('show');
  document.body.classList.remove('dawn');
  document.querySelectorAll('.confetti').forEach(c => c.remove());
  render();
});

function triggerCelebration(){
  document.body.classList.add('dawn');
  celebrate.classList.add('show');
  spawnConfetti();
}

function spawnConfetti(){
  const emojis = ['✅','⭐','🎉','✨'];
  for(let i=0;i<24;i++){
    const el = document.createElement('div');
    el.className = 'confetti';
    el.textContent = emojis[Math.floor(Math.random()*emojis.length)];
    el.style.left = Math.random()*100 + 'vw';
    el.style.animationDuration = (2 + Math.random()*2) + 's';
    el.style.animationDelay = (Math.random()*0.6) + 's';
    celebrate.appendChild(el);
    setTimeout(() => el.remove(), 4500);
  }
}

loadItems();
</script>

</body>
</html>