<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>BFS/DFS Pathfinder</title>
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&display=swap" rel="stylesheet"/>
<style>
/* ─── CSS Variables (theme) ─── */
:root {
  --bg:        #0a0a12;
  --panel:     #12121e;
  --panel2:    #1a1a2e;
  --border:    #2a2a4a;
  --accent:    #00f5d4;
  --accent2:   #f72585;
  --accent3:   #7209b7;
  --text:      #e0e0ff;
  --text-dim:  #666688;
  --cell-free: #1a1a2e;
  --cell-wall: #0d0d18;
  --cell-vis:  #1a4a6a;
  --cell-path: #5a3a00;
  --cell-start:#004a30;
  --cell-end:  #4a0010;
  --cell-agent:#6a2000;
  --cell-alt:  #2a1a5a;
  --glow:      rgba(0,245,212,0.15);
  --cell-size: 54px;
  --anim-speed:80;
  --font-main: 'Share Tech Mono', monospace;
  --font-title:'Orbitron', monospace;
}

*{margin:0;padding:0;box-sizing:border-box;}

body{
  background:var(--bg);
  color:var(--text);
  font-family:var(--font-main);
  min-height:100vh;
  overflow-x:hidden;
}

/* Animated background grid */
body::before{
  content:'';
  position:fixed; inset:0;
  background-image:
    linear-gradient(rgba(0,245,212,.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,245,212,.03) 1px, transparent 1px);
  background-size:40px 40px;
  pointer-events:none;
  z-index:0;
}

/* ─── Layout ─── */
.app{ position:relative; z-index:1; display:flex; flex-direction:column; min-height:100vh; }

/* ─── Header ─── */
header{
  padding:18px 24px 14px;
  border-bottom:1px solid var(--border);
  background:linear-gradient(to right, var(--panel), transparent);
  display:flex; align-items:center; gap:16px; flex-wrap:wrap;
}
.logo{
  font-family:var(--font-title);
  font-size:20px; font-weight:900;
  background:linear-gradient(135deg, var(--accent), var(--accent2));
  -webkit-background-clip:text; -webkit-text-fill-color:transparent;
  letter-spacing:2px; white-space:nowrap;
}
.logo span{ font-size:11px; display:block; font-weight:400; letter-spacing:4px; opacity:.7; }

.btn-group{ display:flex; gap:8px; flex-wrap:wrap; }
.btn{
  padding:8px 16px; border:1px solid var(--border);
  background:var(--panel2); color:var(--text);
  font-family:var(--font-main); font-size:12px;
  cursor:pointer; border-radius:4px;
  transition:all .2s; white-space:nowrap;
  position:relative; overflow:hidden;
}
.btn::after{
  content:''; position:absolute; inset:0;
  background:var(--accent); opacity:0;
  transition:opacity .2s;
}
.btn:hover{ border-color:var(--accent); color:var(--accent); }
.btn:hover::after{ opacity:.05; }
.btn.primary{ border-color:var(--accent); color:var(--accent); }
.btn.primary:hover{ background:var(--accent); color:var(--bg); }
.btn.danger{ border-color:var(--accent2); color:var(--accent2); }
.btn.danger:hover{ background:var(--accent2); color:#fff; }
.btn:disabled{ opacity:.35; cursor:not-allowed; }

/* speed */
.speed-wrap{ display:flex; align-items:center; gap:8px; margin-left:auto; }
.speed-wrap label{ font-size:11px; color:var(--text-dim); }
input[type=range]{
  -webkit-appearance:none; width:100px; height:3px;
  background:var(--border); border-radius:2px; outline:none;
}
input[type=range]::-webkit-slider-thumb{
  -webkit-appearance:none; width:14px; height:14px;
  border-radius:50%; background:var(--accent); cursor:pointer;
  box-shadow:0 0 8px var(--accent);
}

/* ─── Status bar ─── */
#status{
  padding:8px 24px;
  font-size:12px; color:var(--accent);
  border-bottom:1px solid var(--border);
  background:var(--panel);
  min-height:32px;
  overflow:hidden; white-space:nowrap; text-overflow:ellipsis;
}
#status.error{ color:var(--accent2); }

/* ─── Main layout ─── */
.main{ display:flex; flex:1; gap:0; overflow:hidden; }

/* ─── Canvas area ─── */
.canvas-wrap{
  flex:1; overflow:auto; padding:24px;
  display:flex; flex-direction:column; align-items:center; gap:16px;
}
#grid-container{
  display:inline-grid;
  gap:2px;
  padding:16px;
  background:var(--panel);
  border:1px solid var(--border);
  border-radius:8px;
  box-shadow:0 0 40px var(--glow);
}
.cell{
  width:var(--cell-size); height:var(--cell-size);
  border-radius:3px;
  display:flex; align-items:center; justify-content:center;
  font-size:11px; font-weight:bold;
  cursor:pointer;
  transition:background .15s, box-shadow .15s, transform .1s;
  user-select:none;
  position:relative;
  border:1px solid rgba(255,255,255,.04);
}
.cell:hover{ transform:scale(1.08); z-index:2; }
.cell.free    { background:var(--cell-free); color:var(--text-dim); }
.cell.wall    { background:var(--cell-wall); color:#333; cursor:pointer; }
.cell.visited { background:var(--cell-vis);  color:var(--accent);
                box-shadow:inset 0 0 8px rgba(0,245,212,.25); }
.cell.path    { background:var(--cell-path); color:#fdcb6e;
                box-shadow:0 0 12px rgba(253,203,110,.4); }
.cell.start   { background:var(--cell-start); color:#00b894;
                box-shadow:0 0 16px rgba(0,184,148,.5); }
.cell.end     { background:var(--cell-end);   color:#e17055;
                box-shadow:0 0 16px rgba(225,112,85,.5); }
.cell.agent   { background:var(--cell-agent); color:#e17055;
                box-shadow:0 0 20px rgba(225,112,85,.7);
                transform:scale(1.15); z-index:5; }
.cell.alt     { background:var(--cell-alt);  color:#a29bfe; }

.cell .cell-label{ font-size:9px; opacity:.5; position:absolute; bottom:2px; right:4px; }

/* Coord labels */
.coord-row, .coord-col{
  display:flex; align-items:center; justify-content:center;
  font-size:9px; color:var(--text-dim);
  width:var(--cell-size);
}

/* Mode indicator */
.mode-bar{
  display:flex; gap:8px; align-items:center;
  flex-wrap:wrap; font-size:11px;
}
.mode-item{
  padding:5px 12px; border-radius:3px; border:1px solid var(--border);
  cursor:pointer; transition:all .2s;
  background:var(--panel2);
}
.mode-item.active{ border-color:var(--accent); color:var(--accent); background:rgba(0,245,212,.08); }

/* ─── Sidebar ─── */
.sidebar{
  width:280px; min-width:240px;
  border-left:1px solid var(--border);
  background:var(--panel);
  display:flex; flex-direction:column;
  overflow:hidden;
}
.tab-bar{
  display:flex; border-bottom:1px solid var(--border);
}
.tab{
  flex:1; padding:10px 4px; text-align:center;
  font-size:11px; cursor:pointer; color:var(--text-dim);
  border-bottom:2px solid transparent;
  transition:all .2s;
}
.tab.active{ color:var(--accent); border-bottom-color:var(--accent); }
.tab-content{ display:none; flex:1; flex-direction:column; overflow:hidden; }
.tab-content.active{ display:flex; }

/* Results */
#result-box{
  flex:1; overflow-y:auto; padding:12px;
  font-size:11px; line-height:1.8;
  color:var(--text-dim);
}
#result-box .hi{ color:var(--accent); }
#result-box .hi2{ color:var(--accent2); }
#result-box .hi3{ color:#fdcb6e; }

/* ─── Customize panel ─── */
.customize{
  padding:12px; overflow-y:auto; flex:1;
  display:flex; flex-direction:column; gap:12px;
}
.cust-group{ border:1px solid var(--border); border-radius:6px; padding:10px; }
.cust-title{ font-size:10px; color:var(--accent); letter-spacing:2px; margin-bottom:8px; }
.cust-row{ display:flex; align-items:center; gap:8px; margin-bottom:6px; font-size:11px; }
.cust-row label{ flex:1; color:var(--text-dim); }
input[type=color]{
  width:36px; height:24px; border:none; background:none;
  cursor:pointer; border-radius:3px; padding:1px;
}
input[type=number]{
  width:52px; background:var(--panel2); border:1px solid var(--border);
  color:var(--text); padding:3px 6px; font-family:var(--font-main);
  font-size:11px; border-radius:3px; outline:none;
}
select{
  background:var(--panel2); border:1px solid var(--border);
  color:var(--text); padding:4px 8px; font-family:var(--font-main);
  font-size:11px; border-radius:3px; outline:none; cursor:pointer;
}
.theme-grid{ display:grid; grid-template-columns:1fr 1fr; gap:6px; }
.theme-btn{
  padding:6px; border-radius:4px; cursor:pointer; text-align:center;
  font-size:10px; border:1px solid transparent; transition:all .2s;
}
.theme-btn:hover{ border-color:var(--accent); }

/* Grid size */
.grid-size-row{ display:flex; align-items:center; gap:6px; font-size:11px; }
.grid-size-row label{ color:var(--text-dim); width:50px; }

/* ─── Scrollbar ─── */
::-webkit-scrollbar{ width:5px; height:5px; }
::-webkit-scrollbar-track{ background:var(--panel); }
::-webkit-scrollbar-thumb{ background:var(--border); border-radius:3px; }
::-webkit-scrollbar-thumb:hover{ background:var(--accent3); }

/* ─── Pulse animation ─── */
@keyframes pulse{ 0%,100%{opacity:1} 50%{opacity:.5} }
@keyframes pop{ 0%{transform:scale(0.5)} 60%{transform:scale(1.2)} 100%{transform:scale(1)} }
.cell.just-visited{ animation:pop .25s ease; }
.cell.agent{ animation:pulse .6s ease infinite; }

/* ─── Toast ─── */
#toast{
  position:fixed; bottom:24px; left:50%; transform:translateX(-50%) translateY(80px);
  background:var(--panel2); border:1px solid var(--accent);
  color:var(--accent); padding:10px 24px; border-radius:6px;
  font-size:13px; z-index:999;
  transition:transform .3s; pointer-events:none;
  box-shadow:0 0 20px var(--glow);
}
#toast.show{ transform:translateX(-50%) translateY(0); }
</style>
</head>
<body>
<div class="app">

<!-- ─── Header ─── -->
<header>
  <div class="logo">PATHFINDER<span>BFS / DFS ENGINE v2</span></div>
  <div class="btn-group">
    <button class="btn primary" onclick="runBFS()">▶ Chạy BFS</button>
    <button class="btn" onclick="runDFS()">🌲 Đếm DFS</button>
    <button class="btn" onclick="runMove()">🚀 Di chuyển</button>
    <button class="btn danger" onclick="stopAnim()">⏹ Dừng</button>
    <button class="btn" onclick="resetView()">↺ Reset</button>
  </div>
  <div class="speed-wrap">
    <label>TỐC ĐỘ</label>
    <input type="range" id="speedSlider" min="20" max="500" value="80"
           oninput="animSpeed=parseInt(this.value)"/>
    <span id="speedVal" style="font-size:11px;color:var(--accent);">80ms</span>
  </div>
</header>

<!-- ─── Status ─── -->
<div id="status">Chào mừng! Hãy nhấn ▶ Chạy BFS để bắt đầu với lưới mẫu.</div>

<!-- ─── Main ─── -->
<div class="main">

  <!-- Canvas area -->
  <div class="canvas-wrap">

    <!-- Mode bar -->
    <div class="mode-bar">
      <span style="color:var(--text-dim);font-size:11px;">CHẾ ĐỘ:</span>
      <div class="mode-item active" id="m-toggle" onclick="setMode('toggle')">✏ Toggle 0↔1</div>
      <div class="mode-item" id="m-start"  onclick="setMode('start')">🟢 Đặt điểm A</div>
      <div class="mode-item" id="m-end"    onclick="setMode('end')">🔴 Đặt điểm B</div>
      <div class="mode-item" id="m-erase"  onclick="setMode('erase')">🗑 Xóa tường</div>
    </div>

    <!-- Grid -->
    <div id="grid-container"></div>

    <!-- Info row -->
    <div style="display:flex;gap:16px;font-size:11px;color:var(--text-dim);flex-wrap:wrap;justify-content:center;">
      <span>A = <b id="info-start" style="color:#00b894">-</b></span>
      <span>B = <b id="info-end"   style="color:#e17055">-</b></span>
      <span>Lưới: <b id="info-size" style="color:var(--accent)">-</b></span>
      <span>BFS bước: <b id="info-bsteps" style="color:#fdcb6e">-</b></span>
      <span>DFS đường: <b id="info-dpaths" style="color:#a29bfe">-</b></span>
    </div>
  </div>

  <!-- Sidebar -->
  <div class="sidebar">
    <div class="tab-bar">
      <div class="tab active" onclick="switchTab('results')">📊 Kết quả</div>
      <div class="tab" onclick="switchTab('grid')">⚙ Lưới</div>
      <div class="tab" onclick="switchTab('theme')">🎨 Giao diện</div>
    </div>

    <!-- Tab: Results -->
    <div id="tab-results" class="tab-content active">
      <div id="result-box"><span style="color:var(--text-dim)">Chưa có kết quả...</span></div>
    </div>

    <!-- Tab: Grid settings -->
    <div id="tab-grid" class="tab-content">
      <div class="customize">
        <div class="cust-group">
          <div class="cust-title">KÍCH THƯỚC LƯỚI</div>
          <div class="grid-size-row">
            <label>Hàng:</label>
            <input type="number" id="inp-rows" value="6" min="2" max="20"/>
          </div>
          <div class="grid-size-row" style="margin-top:6px;">
            <label>Cột:</label>
            <input type="number" id="inp-cols" value="6" min="2" max="20"/>
          </div>
          <div style="margin-top:8px;display:flex;gap:6px;">
            <button class="btn" style="flex:1" onclick="rebuildGrid()">✓ Áp dụng</button>
            <button class="btn" onclick="loadSample()">📋 Lưới mẫu</button>
          </div>
        </div>

        <div class="cust-group">
          <div class="cust-title">KÍCH THƯỚC Ô</div>
          <div class="cust-row">
            <label>Px/ô:</label>
            <input type="range" id="cellSizeSlider" min="30" max="90" value="54"
                   style="flex:1" oninput="setCellSize(this.value)"/>
            <span id="cellSizeVal" style="font-size:11px;color:var(--accent)">54</span>
          </div>
        </div>

        <div class="cust-group">
          <div class="cust-title">RANDOM MAZE</div>
          <div class="cust-row">
            <label>Mật độ tường:</label>
            <input type="range" id="densitySlider" min="0" max="70" value="30" style="flex:1"/>
            <span id="densityVal" style="font-size:11px;color:var(--accent)">30%</span>
          </div>
          <button class="btn" style="width:100%;margin-top:4px" onclick="generateRandom()">🎲 Tạo ngẫu nhiên</button>
        </div>

        <div class="cust-group">
          <div class="cust-title">XUẤT / NHẬP</div>
          <button class="btn" style="width:100%;margin-bottom:6px" onclick="exportGrid()">💾 Xuất JSON</button>
          <button class="btn" style="width:100%" onclick="document.getElementById('importInput').click()">📂 Nhập JSON</button>
          <input type="file" id="importInput" accept=".json" style="display:none" onchange="importGrid(event)"/>
        </div>
      </div>
    </div>

    <!-- Tab: Theme -->
    <div id="tab-theme" class="tab-content">
      <div class="customize">

        <div class="cust-group">
          <div class="cust-title">THEMES CÓ SẴN</div>
          <div class="theme-grid" id="theme-presets"></div>
        </div>

        <div class="cust-group">
          <div class="cust-title">MÀU NỀN & BẢNG</div>
          <div class="cust-row"><label>Nền tổng</label>
            <input type="color" value="#0a0a12" oninput="setVar('--bg',this.value)"/></div>
          <div class="cust-row"><label>Panel</label>
            <input type="color" value="#12121e" oninput="setVar('--panel',this.value)"/></div>
          <div class="cust-row"><label>Accent chính</label>
            <input type="color" value="#00f5d4" oninput="setVar('--accent',this.value)"/></div>
          <div class="cust-row"><label>Accent phụ</label>
            <input type="color" value="#f72585" oninput="setVar('--accent2',this.value)"/></div>
        </div>

        <div class="cust-group">
          <div class="cust-title">MÀU Ô LƯỚI</div>
          <div class="cust-row"><label>Ô trống</label>
            <input type="color" value="#1a1a2e" oninput="setVar('--cell-free',this.value)"/></div>
          <div class="cust-row"><label>Tường</label>
            <input type="color" value="#0d0d18" oninput="setVar('--cell-wall',this.value)"/></div>
          <div class="cust-row"><label>Đã duyệt BFS</label>
            <input type="color" value="#1a4a6a" oninput="setVar('--cell-vis',this.value)"/></div>
          <div class="cust-row"><label>Đường ngắn nhất</label>
            <input type="color" value="#5a3a00" oninput="setVar('--cell-path',this.value)"/></div>
          <div class="cust-row"><label>Điểm A</label>
            <input type="color" value="#004a30" oninput="setVar('--cell-start',this.value)"/></div>
          <div class="cust-row"><label>Điểm B</label>
            <input type="color" value="#4a0010" oninput="setVar('--cell-end',this.value)"/></div>
          <div class="cust-row"><label>Agent</label>
            <input type="color" value="#6a2000" oninput="setVar('--cell-agent',this.value)"/></div>
          <div class="cust-row"><label>DFS (đường khác)</label>
            <input type="color" value="#2a1a5a" oninput="setVar('--cell-alt',this.value)"/></div>
        </div>

        <div class="cust-group">
          <div class="cust-title">FONT</div>
          <div class="cust-row">
            <label>Font chính</label>
            <select onchange="setVar('--font-main',this.value)">
              <option value="'Share Tech Mono',monospace">Share Tech Mono</option>
              <option value="'Courier New',monospace">Courier New</option>
              <option value="'Consolas',monospace">Consolas</option>
              <option value="'Georgia',serif">Georgia</option>
              <option value="'Trebuchet MS',sans-serif">Trebuchet MS</option>
            </select>
          </div>
        </div>
      </div>
    </div>
  </div><!-- /sidebar -->
</div><!-- /main -->
</div><!-- /app -->

<div id="toast"></div>

<script>
/* ═══════════════════════════════════════
   STATE
═══════════════════════════════════════ */
let ROWS=6, COLS=6;
let gridData=[], startCell=null, endCell=null;
let bfsPath=[], bfsLog=[], allPaths=[];
let animId=null, animPhase='idle', animSpeed=80;
let mode='toggle';
let mouseDown=false;

const DIRS=[[-1,0],[1,0],[0,-1],[0,1]];

/* ═══════════════════════════════════════
   SAMPLE GRID
═══════════════════════════════════════ */
const SAMPLE=[
  [0,1,0,0,0,0],
  [0,1,0,1,1,0],
  [0,0,0,1,0,0],
  [1,1,0,0,0,1],
  [0,0,1,1,0,0],
  [0,0,0,0,0,0],
];

function loadSample(){
  ROWS=6; COLS=6;
  document.getElementById('inp-rows').value=6;
  document.getElementById('inp-cols').value=6;
  gridData=SAMPLE.map(r=>[...r]);
  startCell=[0,0]; endCell=[5,5];
  bfsPath=[]; bfsLog=[]; allPaths=[];
  buildDOM(); updateInfoBar();
  setStatus('Đã tải lưới mẫu 6×6. Nhấn ▶ Chạy BFS để bắt đầu!');
}

/* ═══════════════════════════════════════
   BUILD DOM GRID
═══════════════════════════════════════ */
function buildDOM(){
  stopAnim();
  const gc=document.getElementById('grid-container');
  gc.style.gridTemplateColumns=`repeat(${COLS}, var(--cell-size))`;
  gc.innerHTML='';
  for(let r=0;r<ROWS;r++){
    for(let c=0;c<COLS;c++){
      const el=document.createElement('div');
      el.id=`c${r}_${c}`;
      el.className='cell';
      el.dataset.r=r; el.dataset.c=c;
      el.addEventListener('mousedown',e=>{mouseDown=true;onCellClick(r,c,e);});
      el.addEventListener('mouseenter',e=>{ if(mouseDown) onCellDrag(r,c);});
      const lbl=document.createElement('span');
      lbl.className='cell-label';
      lbl.textContent=`${r},${c}`;
      el.appendChild(lbl);
      gc.appendChild(el);
    }
  }
  document.addEventListener('mouseup',()=>mouseDown=false);
  redrawAll();
}

function rebuildGrid(){
  ROWS=Math.max(2,Math.min(20,parseInt(document.getElementById('inp-rows').value)||6));
  COLS=Math.max(2,Math.min(20,parseInt(document.getElementById('inp-cols').value)||6));
  gridData=Array.from({length:ROWS},()=>new Array(COLS).fill(0));
  startCell=null; endCell=null;
  bfsPath=[]; bfsLog=[]; allPaths=[];
  buildDOM(); updateInfoBar();
  setStatus(`Lưới ${ROWS}×${COLS} mới. Nhấn 🎲 để tạo ngẫu nhiên hoặc vẽ tường.`);
}

/* ═══════════════════════════════════════
   CELL INTERACTIONS
═══════════════════════════════════════ */
function setMode(m){
  mode=m;
  document.querySelectorAll('.mode-item').forEach(el=>el.classList.remove('active'));
  document.getElementById(`m-${m}`)?.classList.add('active');
}

function onCellClick(r,c,e){
  e.preventDefault();
  applyMode(r,c);
}
function onCellDrag(r,c){
  if(mode==='toggle'||mode==='erase') applyMode(r,c);
}

function applyMode(r,c){
  if(mode==='toggle'){
    if(sameCell([r,c],startCell)||sameCell([r,c],endCell)) return;
    gridData[r][c]^=1; redrawCell(r,c);
  } else if(mode==='erase'){
    if(sameCell([r,c],startCell)||sameCell([r,c],endCell)) return;
    gridData[r][c]=0; redrawCell(r,c);
  } else if(mode==='start'){
    if(gridData[r][c]===1){ toast('Ô tường! Chọn ô trống.'); return; }
    const old=startCell; startCell=[r,c];
    if(old) redrawCell(old[0],old[1]);
    redrawCell(r,c); updateInfoBar();
  } else if(mode==='end'){
    if(gridData[r][c]===1){ toast('Ô tường! Chọn ô trống.'); return; }
    const old=endCell; endCell=[r,c];
    if(old) redrawCell(old[0],old[1]);
    redrawCell(r,c); updateInfoBar();
  }
}

/* ═══════════════════════════════════════
   DRAW
═══════════════════════════════════════ */
const visitedSet=new Set(), pathSet=new Set(), altSet=new Set();
let agentCell=null;

function redrawAll(){
  visitedSet.clear(); pathSet.clear(); altSet.clear(); agentCell=null;
  bfsLog.forEach(c=>visitedSet.add(key(c)));
  bfsPath.forEach(c=>pathSet.add(key(c)));
  allPaths.forEach(p=>p.forEach(c=>altSet.add(key(c))));
  for(let r=0;r<ROWS;r++) for(let c=0;c<COLS;c++) redrawCell(r,c);
}

function redrawCell(r,c,forceAgent){
  const el=document.getElementById(`c${r}_${c}`);
  if(!el) return;
  const k=key([r,c]);
  const isStart=sameCell([r,c],startCell);
  const isEnd  =sameCell([r,c],endCell);
  const isAgent=forceAgent||sameCell([r,c],agentCell);

  el.className='cell';
  let txt='';
  if(isStart)        { el.classList.add('start');   txt='A'; }
  else if(isEnd)     { el.classList.add('end');     txt='B'; }
  else if(isAgent)   { el.classList.add('agent');   txt='●'; }
  else if(pathSet.has(k))    { el.classList.add('path');    txt='·'; }
  else if(visitedSet.has(k)) { el.classList.add('visited'); txt='·'; }
  else if(altSet.has(k))     { el.classList.add('alt');     txt='·'; }
  else if(gridData[r][c]===1){ el.classList.add('wall');    txt='▪'; }
  else                       { el.classList.add('free');    txt=''; }

  // keep coord label
  el.innerHTML=`${txt}<span class="cell-label">${r},${c}</span>`;
}

function key(c){ return c[0]*1000+c[1]; }
function sameCell(a,b){ return a&&b&&a[0]===b[0]&&a[1]===b[1]; }

/* ═══════════════════════════════════════
   BFS
═══════════════════════════════════════ */
function bfsAlgo(grid,start,end){
  const rows=grid.length, cols=grid[0].length;
  const queue=[start], visited=new Set([key(start)]);
  const parent=new Map([[key(start),null]]);
  const log=[start];
  while(queue.length){
    const curr=queue.shift();
    if(sameCell(curr,end)) break;
    for(const [dr,dc] of DIRS){
      const nxt=[curr[0]+dr,curr[1]+dc];
      const k=key(nxt);
      if(nxt[0]>=0&&nxt[0]<rows&&nxt[1]>=0&&nxt[1]<cols
         &&grid[nxt[0]][nxt[1]]===0&&!visited.has(k)){
        visited.add(k); parent.set(k,curr);
        queue.push(nxt); log.push(nxt);
      }
    }
  }
  if(!parent.has(key(end))) return {path:null,log};
  const path=[]; let node=end;
  while(node){ path.push(node); const pk=key(node); node=parent.get(pk); }
  path.reverse(); return {path,log};
}

function runBFS(){
  if(!checkReady()) return;
  stopAnim();
  visitedSet.clear(); pathSet.clear(); altSet.clear(); agentCell=null;
  bfsLog=[]; bfsPath=[];
  redrawAll();
  logClear();

  const t0=performance.now();
  const res=bfsAlgo(gridData,startCell,endCell);
  const dt=(performance.now()-t0).toFixed(2);
  bfsLog=res.log; bfsPath=res.path||[];

  if(bfsPath.length){
    log(`<span class="hi">✅ BFS tìm thấy đường!</span>`);
    log(`   Số bước: <span class="hi3">${bfsPath.length-1}</span>`);
    log(`   Ô đã duyệt: <span class="hi">${bfsLog.length}</span>`);
    log(`   Thời gian: <span class="hi">${dt} ms</span>`);
    log(`\n<span class="hi">📍 Đường đi:</span>`);
    bfsPath.forEach((p,i)=>log(`   ${i}: (${p[0]},${p[1]})`));
    document.getElementById('info-bsteps').textContent=bfsPath.length-1;
  } else {
    log(`<span class="hi2">❌ Không tìm thấy đường đi!</span>`);
    document.getElementById('info-bsteps').textContent='—';
  }

  animPhase='bfs'; animStep=0; tickBFS();
}

let animStep=0;
function tickBFS(){
  if(animPhase!=='bfs') return;
  if(animStep<bfsLog.length){
    const c=bfsLog[animStep];
    visitedSet.add(key(c));
    redrawCell(c[0],c[1]);
    setStatus(`🔍 BFS duyệt (${c[0]},${c[1]}) — [${animStep+1}/${bfsLog.length}]`);
    animStep++; animId=setTimeout(tickBFS,animSpeed);
  } else {
    animPhase='showpath'; animStep=0; tickPath();
  }
}
function tickPath(){
  if(animPhase!=='showpath') return;
  if(!bfsPath.length){
    setStatus('❌ Không có đường từ A đến B!','error'); animPhase='idle'; return;
  }
  if(animStep<=bfsPath.length){
    bfsPath.slice(0,animStep).forEach(c=>{ pathSet.add(key(c)); redrawCell(c[0],c[1]); });
    setStatus(`✨ Hiển thị đường ngắn nhất... [${animStep}/${bfsPath.length}]`);
    animStep++; animId=setTimeout(tickPath,animSpeed);
  } else {
    setStatus(`✅ BFS hoàn tất! Đường ngắn nhất: ${bfsPath.length-1} bước — Nhấn 🌲 DFS hoặc 🚀 Di chuyển`);
    animPhase='idle';
  }
}

/* ═══════════════════════════════════════
   DFS
═══════════════════════════════════════ */
function dfsAlgo(grid,start,end){
  const rows=grid.length,cols=grid[0].length;
  const results=[], visited=new Set();
  function dfs(node,path){
    if(sameCell(node,end)){ results.push([...path]); return; }
    visited.add(key(node));
    for(const [dr,dc] of DIRS){
      const nxt=[node[0]+dr,node[1]+dc];
      if(nxt[0]>=0&&nxt[0]<rows&&nxt[1]>=0&&nxt[1]<cols
         &&grid[nxt[0]][nxt[1]]===0&&!visited.has(key(nxt))){
        path.push(nxt); dfs(nxt,path); path.pop();
      }
    }
    visited.delete(key(node));
  }
  dfs(start,[start]); return results;
}

function runDFS(){
  if(!checkReady()) return;
  stopAnim();
  setStatus('⏳ DFS đang đếm tất cả đường... có thể lâu với lưới lớn.');
  logClear();
  log(`<span class="hi">⏳ Đang chạy DFS...</span>`);

  setTimeout(()=>{
    const t0=performance.now();
    allPaths=dfsAlgo(gridData,startCell,endCell);
    const dt=(performance.now()-t0).toFixed(2);

    altSet.clear();
    allPaths.forEach(p=>p.forEach(c=>altSet.add(key(c))));
    redrawAll();

    log(`<span class="hi">🌲 DFS hoàn tất!</span>`);
    log(`   Tổng đường đi: <span class="hi2">${allPaths.length}</span>`);
    log(`   Thời gian: <span class="hi">${dt} ms</span>`);
    if(allPaths.length){
      log(`\n<span class="hi">📋 Danh sách:</span>`);
      allPaths.forEach((p,i)=>{
        log(`\n  <span class="hi3">[${i+1}]</span> <span class="hi">${p.length-1} bước</span>`);
        log(`   `+p.map(c=>`(${c[0]},${c[1]})`).join(' → '));
      });
    }

    document.getElementById('info-dpaths').textContent=allPaths.length;
    setStatus(`🌲 DFS: Tìm thấy ${allPaths.length} đường đi (tím=đường khác, vàng=ngắn nhất BFS)`);
    animPhase='idle';
  }, 30);
}

/* ═══════════════════════════════════════
   MOVE ANIMATION
═══════════════════════════════════════ */
function runMove(){
  if(!bfsPath.length){ toast('Hãy chạy BFS trước!'); return; }
  stopAnim();
  animPhase='move'; animStep=0; tickMove();
}
function tickMove(){
  if(animPhase!=='move') return;
  if(animStep<bfsPath.length){
    const prev=agentCell;
    agentCell=bfsPath[animStep];
    if(prev) redrawCell(prev[0],prev[1]);
    redrawCell(agentCell[0],agentCell[1],true);
    setStatus(`🚀 Agent di chuyển... bước ${animStep}/${bfsPath.length-1} → (${agentCell[0]},${agentCell[1]})`);
    animStep++; animId=setTimeout(tickMove,animSpeed+40);
  } else {
    agentCell=null; redrawAll();
    setStatus(`🏁 Đến đích! Đường: ${bfsPath.length-1} bước | DFS: ${allPaths.length} đường`);
    animPhase='idle';
  }
}

/* ═══════════════════════════════════════
   CONTROLS
═══════════════════════════════════════ */
function stopAnim(){
  if(animId) clearTimeout(animId);
  animId=null; animPhase='idle';
}
function resetView(){
  stopAnim(); bfsPath=[]; bfsLog=[];
  visitedSet.clear(); pathSet.clear(); altSet.clear(); agentCell=null;
  redrawAll();
  setStatus('↺ Đã reset. BFS và DFS đã xóa.');
}
function checkReady(){
  if(!startCell||!endCell){ toast('Hãy đặt điểm A và B trước (tab ⚙ Lưới > chế độ)'); return false; }
  if(sameCell(startCell,endCell)){ toast('A và B không được trùng nhau!'); return false; }
  return true;
}
function updateInfoBar(){
  document.getElementById('info-start').textContent=startCell?`(${startCell[0]},${startCell[1]})`:'-';
  document.getElementById('info-end').textContent  =endCell  ?`(${endCell[0]},${endCell[1]})`:'-';
  document.getElementById('info-size').textContent =`${ROWS}×${COLS}`;
}

/* ═══════════════════════════════════════
   RANDOM MAZE
═══════════════════════════════════════ */
function generateRandom(){
  const density=parseInt(document.getElementById('densitySlider').value)/100;
  gridData=Array.from({length:ROWS},()=>
    Array.from({length:COLS},()=>Math.random()<density?1:0));
  // Ensure start/end are clear
  if(startCell) gridData[startCell[0]][startCell[1]]=0;
  if(endCell)   gridData[endCell[0]][endCell[1]]=0;
  bfsPath=[]; bfsLog=[]; allPaths=[];
  visitedSet.clear(); pathSet.clear(); altSet.clear();
  redrawAll();
  setStatus(`🎲 Random maze ${ROWS}×${COLS} (${(density*100).toFixed(0)}% tường)`);
}
document.getElementById('densitySlider').oninput=function(){
  document.getElementById('densityVal').textContent=this.value+'%';
};

/* ═══════════════════════════════════════
   CELL SIZE
═══════════════════════════════════════ */
function setCellSize(v){
  document.documentElement.style.setProperty('--cell-size',v+'px');
  document.getElementById('cellSizeVal').textContent=v;
}

/* ═══════════════════════════════════════
   SPEED
═══════════════════════════════════════ */
document.getElementById('speedSlider').oninput=function(){
  animSpeed=parseInt(this.value);
  document.getElementById('speedVal').textContent=this.value+'ms';
};

/* ═══════════════════════════════════════
   EXPORT / IMPORT
═══════════════════════════════════════ */
function exportGrid(){
  const data=JSON.stringify({rows:ROWS,cols:COLS,grid:gridData,start:startCell,end:endCell},null,2);
  const a=document.createElement('a');
  a.href='data:application/json,'+encodeURIComponent(data);
  a.download='grid.json'; a.click();
  toast('Đã xuất grid.json!');
}
function importGrid(e){
  const f=e.target.files[0]; if(!f) return;
  const r=new FileReader();
  r.onload=ev=>{
    try{
      const d=JSON.parse(ev.target.result);
      ROWS=d.rows; COLS=d.cols; gridData=d.grid;
      startCell=d.start; endCell=d.end;
      document.getElementById('inp-rows').value=ROWS;
      document.getElementById('inp-cols').value=COLS;
      bfsPath=[]; bfsLog=[]; allPaths=[];
      buildDOM(); updateInfoBar();
      toast('Đã nhập lưới thành công!');
    } catch(err){ toast('File JSON không hợp lệ!'); }
  };
  r.readAsText(f);
}

/* ═══════════════════════════════════════
   THEME CUSTOMIZATION
═══════════════════════════════════════ */
function setVar(name,val){
  document.documentElement.style.setProperty(name,val);
}

const THEMES={
  'Cyber Neon':{
    '--bg':'#0a0a12','--panel':'#12121e','--panel2':'#1a1a2e',
    '--accent':'#00f5d4','--accent2':'#f72585','--border':'#2a2a4a',
    '--cell-free':'#1a1a2e','--cell-wall':'#0d0d18',
    '--cell-vis':'#1a4a6a','--cell-path':'#5a3a00',
    '--cell-start':'#004a30','--cell-end':'#4a0010',
    '--cell-agent':'#6a2000','--cell-alt':'#2a1a5a',
  },
  'Forest':{
    '--bg':'#0d1a0d','--panel':'#122012','--panel2':'#1a2e1a',
    '--accent':'#7ec850','--accent2':'#e8a020','--border':'#2a3a2a',
    '--cell-free':'#1a2e1a','--cell-wall':'#0a120a',
    '--cell-vis':'#1a3a1a','--cell-path':'#3a3000',
    '--cell-start':'#003a10','--cell-end':'#3a1a00',
    '--cell-agent':'#5a2800','--cell-alt':'#1a3010',
  },
  'Ocean':{
    '--bg':'#000d1a','--panel':'#001225','--panel2':'#001830',
    '--accent':'#00cfff','--accent2':'#ff6b35','--border':'#002a40',
    '--cell-free':'#001830','--cell-wall':'#000a14',
    '--cell-vis':'#003a50','--cell-path':'#403000',
    '--cell-start':'#004040','--cell-end':'#400020',
    '--cell-agent':'#602010','--cell-alt':'#201050',
  },
  'Lava':{
    '--bg':'#120000','--panel':'#1e0000','--panel2':'#2a0000',
    '--accent':'#ff4500','--accent2':'#ffd700','--border':'#3a1000',
    '--cell-free':'#1e0800','--cell-wall':'#0a0000',
    '--cell-vis':'#3a1000','--cell-path':'#3a2000',
    '--cell-start':'#003a00','--cell-end':'#3a0000',
    '--cell-agent':'#5a0000','--cell-alt':'#1a0a30',
  },
  'Arctic':{
    '--bg':'#e8f0f5','--panel':'#d0dde8','--panel2':'#c0ccd8',
    '--accent':'#0070cc','--accent2':'#cc4400','--border':'#b0bcc8',
    '--cell-free':'#ddeef8','--cell-wall':'#7090a8',
    '--cell-vis':'#a0d0f0','--cell-path':'#f0e060',
    '--cell-start':'#a0f0c0','--cell-end':'#f0a0a0',
    '--cell-agent':'#f07040','--cell-alt':'#d0b0f0',
    '--text':'#102030','--text-dim':'#506070',
  },
  'Sakura':{
    '--bg':'#1a0a12','--panel':'#250d1a','--panel2':'#2e1020',
    '--accent':'#ff9ec4','--accent2':'#ffce7a','--border':'#3a1a28',
    '--cell-free':'#2e1020','--cell-wall':'#0e0008',
    '--cell-vis':'#3a102a','--cell-path':'#3a2800',
    '--cell-start':'#002a1a','--cell-end':'#2a0010',
    '--cell-agent':'#4a1000','--cell-alt':'#201040',
  },
};

// Build theme preset buttons
function buildThemePresets(){
  const container=document.getElementById('theme-presets');
  Object.entries(THEMES).forEach(([name,vars])=>{
    const btn=document.createElement('div');
    btn.className='theme-btn';
    btn.style.background=vars['--panel']||'#111';
    btn.style.color=vars['--accent']||'#fff';
    btn.style.border=`1px solid ${vars['--accent']||'#444'}`;
    btn.textContent=name;
    btn.onclick=()=>applyTheme(vars,name);
    container.appendChild(btn);
  });
}
function applyTheme(vars,name){
  Object.entries(vars).forEach(([k,v])=>setVar(k,v));
  toast(`Theme: ${name}`);
}

/* ═══════════════════════════════════════
   TABS
═══════════════════════════════════════ */
function switchTab(name){
  document.querySelectorAll('.tab').forEach((t,i)=>{
    const names=['results','grid','theme'];
    t.classList.toggle('active',names[i]===name);
  });
  document.querySelectorAll('.tab-content').forEach(el=>{
    el.classList.toggle('active',el.id===`tab-${name}`);
  });
}

/* ═══════════════════════════════════════
   UI HELPERS
═══════════════════════════════════════ */
function setStatus(msg,cls=''){
  const el=document.getElementById('status');
  el.textContent=msg; el.className=cls;
}
function log(html){
  const el=document.getElementById('result-box');
  el.innerHTML+=html+'<br>';
  el.scrollTop=el.scrollHeight;
}
function logClear(){
  document.getElementById('result-box').innerHTML='';
}
let toastTimer;
function toast(msg){
  const el=document.getElementById('toast');
  el.textContent=msg; el.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer=setTimeout(()=>el.classList.remove('show'),2500);
}

/* ═══════════════════════════════════════
   INIT
═══════════════════════════════════════ */
buildThemePresets();
loadSample();
updateInfoBar();
</script>
</body>
</html>
