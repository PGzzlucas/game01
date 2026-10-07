<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>AI Training Sim — 数据中心</title>
<style>
  :root {
    --bg: #0a0a0f;
    --glass: rgba(255,255,255,0.06);
    --glass-strong: rgba(255,255,255,0.1);
    --border: rgba(255,255,255,0.1);
    --text: #f5f5f7;
    --text-dim: rgba(235,235,245,0.6);
    --accent: #0a84ff;
    --accent2: #bf5af2;
    --green: #30d158;
    --red: #ff453a;
    --orange: #ff9f0a;
    --radius: 20px;
    --radius-sm: 14px;
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }
  html, body {
    background: var(--bg);
    color: var(--text);
    font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', 'Segoe UI', sans-serif;
    min-height: 100vh;
    -webkit-tap-highlight-color: transparent;
    overflow-x: hidden;
  }
  /* ===== Ambient Background Blobs ===== */
  body::before, body::after {
    content: ''; position: fixed; border-radius: 50%;
    filter: blur(100px); opacity: 0.35; z-index: 0; pointer-events: none;
  }
  body::before {
    width: 300px; height: 300px; background: var(--accent2);
    top: -80px; right: -60px; animation: drift1 20s ease-in-out infinite;
  }
  body::after {
    width: 250px; height: 250px; background: var(--accent);
    bottom: 100px; left: -80px; animation: drift2 25s ease-in-out infinite;
  }
  @keyframes drift1 {
    0%,100% { transform: translate(0,0) scale(1); }
    50% { transform: translate(-30px,40px) scale(1.2); }
  }
  @keyframes drift2 {
    0%,100% { transform: translate(0,0) scale(1); }
    50% { transform: translate(40px,-30px) scale(1.15); }
  }

  .app {
    max-width: 480px; margin: 0 auto; padding: 16px 16px 100px;
    position: relative; z-index: 1; transition: max-width 0.3s;
  }
  body.desktop .app { max-width: 1100px; }
  body.desktop .stats-row { grid-template-columns: 1fr 1fr; }
  body.desktop #shopList { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }
  body.desktop .shop-cat { grid-column: 1 / -1; }
  body.desktop #pageTM { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
  body.desktop #pageTrain { max-width: 600px; margin: 0 auto; }
  body.desktop .bottom-nav { max-width: 1100px; }

  /* ===== Header ===== */
  .header { text-align: center; padding: 20px 0 16px; animation: fadeInDown 0.5s ease; }
  .header h1 {
    font-size: 11px; font-weight: 600; letter-spacing: 3px;
    color: var(--text-dim); text-transform: uppercase; margin-bottom: 12px;
  }
  .flops-big {
    font-family: 'SF Pro Display', -apple-system, monospace;
    font-size: 40px; font-weight: 800; color: var(--text);
    line-height: 1.05; letter-spacing: -1px;
    background: linear-gradient(135deg, var(--accent) 0%, var(--accent2) 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .flops-label { font-size: 11px; color: var(--text-dim); margin-top: 6px; letter-spacing: 1px; }

  .progress-wrap { margin: 16px 0; }
  .progress-bar-bg {
    height: 10px; background: var(--glass); border-radius: 5px;
    overflow: hidden;
  }
  .progress-bar-fill {
    height: 100%; background: linear-gradient(90deg, var(--accent), var(--accent2));
    border-radius: 5px; width: 0%; transition: width 0.4s cubic-bezier(0.4,0,0.2,1);
    box-shadow: 0 0 12px rgba(10,132,255,0.5);
  }
  .progress-info {
    display: flex; justify-content: space-between;
    font-size: 11px; color: var(--text-dim); margin-top: 6px;
    font-family: 'SF Pro Display', monospace; font-weight: 500;
  }

  .stats-row { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 16px; }
  .stat-card {
    background: var(--glass); backdrop-filter: blur(20px) saturate(180%);
    -webkit-backdrop-filter: blur(20px) saturate(180%);
    border: 1px solid var(--border);
    border-radius: var(--radius-sm); padding: 14px; text-align: center;
    transition: transform 0.2s;
  }
  .stat-card:active { transform: scale(0.97); }
  .stat-value { font-family: 'SF Pro Display', monospace; font-size: 18px; font-weight: 700; }
  .stat-label { font-size: 10px; color: var(--text-dim); margin-top: 4px; text-transform: uppercase; letter-spacing: 1.2px; font-weight: 500; }

  /* ===== Pages ===== */
  .page { display: none; }
  .page.active { display: block; animation: pageIn 0.35s cubic-bezier(0.32,0.72,0,1); }
  @keyframes pageIn {
    from { opacity: 0; transform: translateY(12px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeInDown {
    from { opacity: 0; transform: translateY(-10px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ===== Train Page ===== */
  .train-btn {
    width: 100%; padding: 22px; background: linear-gradient(135deg, var(--accent), var(--accent2));
    color: #fff; border: none; border-radius: var(--radius); font-size: 20px; font-weight: 800;
    letter-spacing: 4px; cursor: pointer; margin-bottom: 14px;
    transition: transform 0.15s cubic-bezier(0.34,1.56,0.64,1), box-shadow 0.2s;
    box-shadow: 0 8px 32px rgba(10,132,255,0.35), inset 0 1px 0 rgba(255,255,255,0.2);
    user-select: none; touch-action: manipulation;
  }
  .train-btn:active { transform: scale(0.95); box-shadow: 0 4px 16px rgba(10,132,255,0.25); }
  .train-btn .sub { display: block; font-size: 10px; font-weight: 500; letter-spacing: 1px; opacity: 0.8; margin-top: 4px; }

  .terminal {
    background: rgba(0,0,0,0.4); backdrop-filter: blur(20px);
    border: 1px solid var(--border);
    border-radius: var(--radius-sm); overflow: hidden;
  }
  .terminal-header {
    display: flex; justify-content: space-between; align-items: center;
    padding: 10px 14px; border-bottom: 1px solid var(--border);
    font-size: 11px; color: var(--text-dim); font-family: monospace;
  }
  .terminal-dots span { display: inline-block; width: 8px; height: 8px; border-radius: 50%; margin-left: 4px; }
  .terminal-dots span:nth-child(1) { background: #ff5f56; }
  .terminal-dots span:nth-child(2) { background: #ffbd2e; }
  .terminal-dots span:nth-child(3) { background: #27c93f; }
  .terminal-body {
    height: 170px; overflow-y: auto; padding: 10px 14px;
    font-family: 'SF Mono', monospace;
    font-size: 11px; line-height: 1.7; color: var(--green);
  }
  .terminal-body .line { white-space: pre-wrap; word-break: break-all; animation: lineIn 0.2s ease; }
  @keyframes lineIn { from { opacity: 0; transform: translateX(-4px); } to { opacity: 1; transform: translateX(0); } }
  .terminal-body .line.warn { color: var(--orange); }
  .terminal-body .line.info { color: var(--accent); }
  .terminal-body .line.buy { color: var(--accent2); }
  .terminal-body::-webkit-scrollbar { width: 3px; }
  .terminal-body::-webkit-scrollbar-thumb { background: var(--border); border-radius: 2px; }

  /* ===== Task Manager Page ===== */
  .tm-section {
    background: var(--glass); backdrop-filter: blur(20px) saturate(180%);
    -webkit-backdrop-filter: blur(20px) saturate(180%);
    border: 1px solid var(--border);
    border-radius: var(--radius); padding: 16px; margin-bottom: 12px;
  }
  .tm-section h3 {
    font-size: 12px; font-weight: 600; letter-spacing: 0.5px;
    color: var(--text-dim); text-transform: uppercase; margin-bottom: 12px;
  }
  .tm-row { display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px; font-size: 13px; }
  .tm-row:last-child { margin-bottom: 0; }
  .tm-label { color: var(--text-dim); }
  .tm-val { font-family: monospace; font-weight: 600; }
  .tm-bar-bg {
    height: 8px; background: var(--glass-strong); border-radius: 4px; overflow: hidden; margin-top: 4px;
  }
  .tm-bar-fill { height: 100%; border-radius: 4px; transition: width 0.6s cubic-bezier(0.4,0,0.2,1); }
  .tm-bar-fill.green { background: linear-gradient(90deg, #30d158, #66d4cf); }
  .tm-bar-fill.amber { background: linear-gradient(90deg, #ff9f0a, #ffd60a); }
  .tm-bar-fill.red { background: linear-gradient(90deg, #ff453a, #ff6b6b); }
  .gpu-item {
    display: flex; justify-content: space-between; align-items: center;
    padding: 10px 12px; background: var(--glass-strong); border-radius: 12px; margin-bottom: 8px;
    font-size: 12px;
  }
  .gpu-item:last-child { margin-bottom: 0; }
  .gpu-name { font-weight: 600; }
  .gpu-stats { text-align: right; font-family: monospace; color: var(--text-dim); font-size: 10px; line-height: 1.5; }
  .gpu-temp { color: var(--orange); }
  .gpu-temp.hot { color: var(--red); }

  /* ===== Shop Page ===== */
  .shop-cat {
    font-size: 11px; color: var(--text-dim); text-transform: uppercase;
    letter-spacing: 1.5px; margin: 16px 0 8px; padding-left: 4px; font-weight: 600;
  }
  .shop-item {
    display: flex; justify-content: space-between; align-items: center;
    background: var(--glass); backdrop-filter: blur(20px) saturate(180%);
    -webkit-backdrop-filter: blur(20px) saturate(180%);
    border: 1px solid var(--border);
    border-radius: var(--radius-sm); padding: 12px 14px; margin-bottom: 8px;
    transition: all 0.2s;
  }
  .shop-item.affordable {
    border-color: rgba(10,132,255,0.4);
    background: rgba(10,132,255,0.08);
  }
  .shop-item.maxed { opacity: 0.45; }
  .shop-info { flex: 1; }
  .shop-name { font-size: 14px; font-weight: 600; }
  .shop-desc { font-size: 11px; color: var(--text-dim); margin-top: 2px; }
  .shop-own { font-size: 11px; color: var(--green); margin-top: 2px; font-family: monospace; }
  .shop-buy {
    margin-left: 10px; padding: 10px 14px;
    background: rgba(10,132,255,0.15); color: var(--accent);
    border: 1px solid rgba(10,132,255,0.3); border-radius: 12px;
    font-size: 11px; font-weight: 700; cursor: pointer; white-space: nowrap;
    font-family: monospace; min-width: 64px; min-height: 48px;
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    transition: all 0.15s;
  }
  .shop-buy:not(:disabled):active { transform: scale(0.93); background: rgba(10,132,255,0.3); }
  .shop-buy:disabled { opacity: 0.3; cursor: not-allowed; }
  .shop-buy .qty { font-size: 9px; opacity: 0.7; font-weight: 400; }

  /* ===== Bottom Nav ===== */
  .bottom-nav {
    position: fixed; bottom: 0; left: 0; right: 0;
    background: rgba(20,20,30,0.7); backdrop-filter: blur(30px) saturate(180%);
    -webkit-backdrop-filter: blur(30px) saturate(180%);
    border-top: 1px solid var(--border);
    display: flex; max-width: 480px; margin: 0 auto;
    padding-bottom: env(safe-area-inset-bottom);
    z-index: 100;
  }
  .nav-btn {
    flex: 1; padding: 10px 0; background: none; border: none;
    color: var(--text-dim); font-size: 10px; cursor: pointer;
    display: flex; flex-direction: column; align-items: center; gap: 4px;
    font-family: inherit; transition: color 0.2s;
  }
  .nav-btn.active { color: var(--accent); }
  .nav-btn svg { width: 24px; height: 24px; transition: transform 0.2s; }
  .nav-btn:active svg { transform: scale(0.85); }

  /* ===== Floating Numbers ===== */
  .float-num {
    position: fixed; font-family: monospace;
    font-size: 15px; font-weight: 700; color: var(--accent);
    pointer-events: none; animation: floatUp 0.9s ease-out forwards; z-index: 100;
    text-shadow: 0 0 10px rgba(10,132,255,0.5);
  }
  @keyframes floatUp {
    0% { opacity: 1; transform: translateY(0) scale(1); }
    100% { opacity: 0; transform: translateY(-70px) scale(1.3); }
  }

  /* ===== Modal ===== */
  .modal {
    position: fixed; inset: 0; background: rgba(0,0,0,0.6);
    backdrop-filter: blur(20px);
    display: flex; align-items: center; justify-content: center;
    z-index: 200; padding: 20px;
    animation: fadeIn 0.2s ease;
  }
  @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
  .modal.hidden { display: none; }
  .modal-content {
    background: rgba(40,40,55,0.85); backdrop-filter: blur(40px) saturate(180%);
    border: 1px solid var(--border);
    border-radius: 24px; padding: 28px 24px; text-align: center;
    max-width: 380px; width: 100%; max-height: 85vh; overflow-y: auto;
    box-shadow: 0 24px 64px rgba(0,0,0,0.4);
    animation: modalIn 0.3s cubic-bezier(0.34,1.56,0.64,1);
  }
  @keyframes modalIn {
    from { opacity: 0; transform: scale(0.9) translateY(20px); }
    to { opacity: 1; transform: scale(1) translateY(0); }
  }
  .modal-content h2 { font-size: 24px; background: linear-gradient(135deg, var(--accent), var(--accent2)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; margin-bottom: 12px; font-weight: 800; }
  .modal-content p { font-size: 14px; color: var(--text-dim); line-height: 1.6; margin-bottom: 18px; }
  .modal-stats { font-family: monospace; font-size: 12px; color: var(--text); margin-bottom: 20px; line-height: 1.9; }
  .modal-content button {
    padding: 14px 32px; background: linear-gradient(135deg, var(--accent), var(--accent2)); color: #fff;
    border: none; border-radius: 14px; font-size: 15px; font-weight: 700; cursor: pointer;
    transition: transform 0.15s;
  }
  .modal-content button:active { transform: scale(0.95); }
  .debug-btn {
    padding: 12px; background: rgba(10,132,255,0.15); color: var(--accent);
    border: 1px solid rgba(10,132,255,0.3); border-radius: 12px;
    font-size: 13px; font-weight: 600; cursor: pointer; transition: all 0.15s;
  }
  .debug-btn:active { transform: scale(0.95); background: rgba(10,132,255,0.3); }
  .modal input, .modal select {
    width: 100%; padding: 12px; margin-bottom: 8px;
    background: rgba(0,0,0,0.3); border: 1px solid var(--border);
    border-radius: 12px; color: var(--text); font-size: 13px; outline: none;
    box-sizing: border-box; font-family: inherit;
  }
</style>
</head>
<body>
<div class="app">
  <div class="header">
    <h1 id="titleEl">◆ Data Center Trainer</h1>
    <div class="flops-big" id="totalFLOPs">0.00</div>
    <div class="flops-label">总计算力 (FLOPs)</div>
  </div>

  <div class="progress-wrap">
    <div class="progress-bar-bg"><div class="progress-bar-fill" id="progressBar"></div></div>
    <div class="progress-info">
      <span id="progressPct">0.00%</span>
      <span id="progressTarget">目标: GPT-3.5</span>
    </div>
  </div>

  <div class="stats-row">
    <div class="stat-card">
      <div class="stat-value" id="clickPower">1</div>
      <div class="stat-label">每次点击</div>
    </div>
    <div class="stat-card">
      <div class="stat-value" id="autoPower">0/s</div>
      <div class="stat-label">自动算力</div>
    </div>
  </div>

  <!-- ===== Page: Train ===== -->
  <div class="page active" id="pageTrain">
    <button class="train-btn" id="trainBtn">
      TRAIN
      <span class="sub">执行一步训练迭代</span>
    </button>
    <div class="terminal">
      <div class="terminal-header">
        <span>training.log</span>
        <span class="terminal-dots"><span></span><span></span><span></span></span>
      </div>
      <div class="terminal-body" id="terminalBody"></div>
    </div>
  </div>

  <!-- ===== Page: Task Manager ===== -->
  <div class="page" id="pageTM">
    <div class="tm-section">
      <h3>系统资源</h3>
      <div class="tm-row">
        <span class="tm-label">CPU 使用率</span>
        <span class="tm-val" id="cpuVal">0%</span>
      </div>
      <div class="tm-bar-bg"><div class="tm-bar-fill green" id="cpuBar" style="width:0%"></div></div>
      <div class="tm-row" style="margin-top:10px;">
        <span class="tm-label">内存占用</span>
        <span class="tm-val" id="ramVal">0 GB</span>
      </div>
      <div class="tm-bar-bg"><div class="tm-bar-fill amber" id="ramBar" style="width:0%"></div></div>
      <div class="tm-row" style="margin-top:10px;">
        <span class="tm-label">总功耗</span>
        <span class="tm-val" id="powerVal">0 W</span>
      </div>
    </div>
    <div class="tm-section">
      <h3>GPU 状态 (<span id="gpuCount">0</span>)</h3>
      <div id="gpuList"><div style="color:var(--text-dim);font-size:11px;text-align:center;padding:10px;">还没有GPU，去商店买一块吧</div></div>
    </div>
  </div>

  <!-- ===== Page: Shop ===== -->
  <div class="page" id="pageShop">
    <div style="display:flex;gap:8px;margin-bottom:10px;">
      <button class="debug-btn" id="showAffordableBtn" style="flex:1;font-size:11px;padding:8px;">只看能买的</button>
      <button class="debug-btn" id="showAllBtn" style="flex:1;font-size:11px;padding:8px;opacity:0.5;">全部商品</button>
    </div>
    <div id="shopList"></div>
  </div>

  <!-- ===== Page: Settings ===== -->
  <div class="page" id="pageSettings">
    <div class="tm-section">
      <h3>显示模式</h3>
      <div style="display:flex;gap:8px;">
        <button class="debug-btn display-mode-btn" data-mode="auto" style="flex:1;">自动</button>
        <button class="debug-btn display-mode-btn" data-mode="mobile" style="flex:1;">手机版</button>
        <button class="debug-btn display-mode-btn" data-mode="desktop" style="flex:1;">电脑版</button>
      </div>
      <div style="font-size:11px;color:var(--text-dim);margin-top:8px;" id="modeStatus"></div>
    </div>
    <div class="tm-section">
      <h3>更新日志</h3>
      <div style="font-size:12px;line-height:1.8;color:var(--text-dim);">
        <div style="color:var(--accent);font-weight:600;margin-bottom:4px;">v2.7 — 2026.10.07</div>
        <div>· 修复无法通关的bug</div>
        <div>· 新增设置菜单</div>
        <div>· 自动识别手机/电脑并切换布局</div>
        <div>· 商品按价格排序</div>
        <div style="color:var(--accent);font-weight:600;margin:10px 0 4px;">v2.6 — 2026.10.07</div>
        <div>· 商店扩充到85个商品</div>
        <div>· 新增软件与数据类（31个，加点击收益）</div>
        <div>· 修复NaN显示bug</div>
        <div style="color:var(--accent);font-weight:600;margin:10px 0 4px;">v2.0 — 2026.10.07</div>
        <div>· 重写为数据中心模拟器</div>
        <div>· 三个页面：训练/任务管理器/商店</div>
      </div>
    </div>
  </div>
</div>

<!-- Bottom Nav -->
<nav class="bottom-nav">
  <button class="nav-btn active" data-page="pageTrain">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polygon points="5 3 19 12 5 21 5 3" fill="currentColor"/></svg>
    训练
  </button>
  <button class="nav-btn" data-page="pageTM">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="3" width="20" height="14" rx="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>
    任务管理器
  </button>
  <button class="nav-btn" data-page="pageShop">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"/></svg>
    商店
  </button>
  <button class="nav-btn" data-page="pageSettings">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-4 0v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06A1.65 1.65 0 0 0 4.6 15a1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1 0-4h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06A1.65 1.65 0 0 0 9 4.6a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 4 0v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06A1.65 1.65 0 0 0 19.4 9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 0 4h-.09a1.65 1.65 0 0 0-1.51 1z"/></svg>
    设置
  </button>
</nav>

<!-- Victory Modal -->
<div class="modal hidden" id="victoryModal">
  <div class="modal-content">
    <h2>训练完成</h2>
    <p>你的数据中心已达到目标算力！</p>
    <div class="modal-stats" id="victoryStats"></div>
    <button id="restartBtn">重新开始</button>
  </div>
</div>

<!-- Password Modal -->
<div class="modal hidden" id="passModal">
  <div class="modal-content">
    <h2 style="font-size:16px;">开发者验证</h2>
    <p>请输入4位密码</p>
    <input type="password" id="passInput" inputmode="numeric" maxlength="4"
      style="width:100%;padding:12px;font-size:24px;text-align:center;background:var(--bg);border:1px solid var(--border);border-radius:8px;color:var(--accent);font-family:monospace;letter-spacing:8px;outline:none;margin-bottom:8px;">
    <p id="passError" style="color:var(--red);font-size:11px;min-height:14px;"></p>
    <div style="display:flex;gap:8px;">
      <button id="passConfirm" style="flex:1;">确认</button>
      <button id="passCancel" style="flex:1;background:var(--surface-2);color:var(--text);border:1px solid var(--border);">取消</button>
    </div>
  </div>
</div>

<!-- Debug Modal -->
<div class="modal hidden" id="debugModal">
  <div class="modal-content" style="text-align:left;">
    <h2 style="font-size:16px;text-align:center;">◆ Debug Console</h2>
    <div class="modal-stats" style="text-align:center;" id="debugStats"></div>
    <div style="display:grid;grid-template-columns:1fr 1fr 1fr 1fr;gap:6px;margin-bottom:12px;">
      <button class="debug-btn" data-add="1e3">+1K</button>
      <button class="debug-btn" data-add="1e6">+1M</button>
      <button class="debug-btn" data-add="1e9">+1B</button>
      <button class="debug-btn" data-add="1e12">+1T</button>
    </div>
    <div style="background:var(--surface-2);border-radius:8px;padding:10px;margin-bottom:10px;">
      <div style="font-size:10px;color:var(--text-dim);margin-bottom:6px;">调整目标算力</div>
      <div style="display:flex;gap:6px;">
        <input type="number" id="targetInput" placeholder="如 1e15" style="flex:1;margin-bottom:0;">
        <button class="debug-btn" id="setTargetBtn" style="padding:8px 12px;">设置</button>
      </div>
      <div id="currentTarget" style="font-size:10px;color:var(--text-dim);margin-top:4px;font-family:monospace;"></div>
    </div>
    <div style="background:var(--surface-2);border-radius:8px;padding:10px;margin-bottom:10px;">
      <div style="font-size:10px;color:var(--text-dim);margin-bottom:6px;">商店添加商品</div>
      <input type="text" id="customName" placeholder="商品名（如：RTX 5090）">
      <select id="customCat">
        <option value="GPU 显卡">GPU 显卡</option>
        <option value="CPU 处理器">CPU 处理器</option>
        <option value="内存 RAM">内存 RAM</option>
        <option value="存储与基建">存储与基建</option>
      </select>
      <div style="display:flex;gap:6px;">
        <input type="number" id="customValue" placeholder="FLOPs/s" style="flex:1;">
        <input type="number" id="customCost" placeholder="成本" style="flex:1;">
      </div>
      <button class="debug-btn" id="addCustomBtn" style="width:100%;">+ 添加到商店</button>
    </div>
    <div style="display:flex;flex-direction:column;gap:6px;">
      <button class="debug-btn" id="unlockAllBtn" style="width:100%;">买空商店</button>
      <button class="debug-btn" id="winBtn" style="width:100%;">直接通关</button>
      <button class="debug-btn" id="closeDebugBtn" style="width:100%;background:var(--surface-2);color:var(--text);border:1px solid var(--border);">关闭</button>
    </div>
  </div>
</div>

<script>
// ===== State =====
let TARGET_FLOPS = 1e15;
let state = {
  totalFLOPs: 0,
  totalClicks: 0,
  owned: {},
  startTime: Date.now(),
  victoryShown: false
};

// ===== Shop Products =====
let PRODUCTS = [
  // ===== GPU 显卡（按价格排序） =====
  { id: 'g1', cat: 'GPU 显卡', name: 'RTX 3060', desc: '入门训练卡，12GB显存，适合跑小模型', cost: 50, flops: 1000, watt: 170 },
  { id: 'g2', cat: 'GPU 显卡', name: 'RTX 3070', desc: '平衡型游戏卡，8GB显存，推理够用', cost: 100, flops: 2000, watt: 220 },
  { id: 'g3', cat: 'GPU 显卡', name: 'RTX 3080', desc: '高性能推理卡，10GB显存', cost: 250, flops: 4000, watt: 320 },
  { id: 'g4', cat: 'GPU 显卡', name: 'RTX 3090', desc: '24GB大显存，个人入门微调首选', cost: 400, flops: 6000, watt: 350 },
  { id: 'g5', cat: 'GPU 显卡', name: 'RTX 4090', desc: '消费卡之王，24GB，训练小模型神器', cost: 800, flops: 12000, watt: 450 },
  { id: 'g19', cat: 'GPU 显卡', name: 'RTX 5090', desc: '下一代消费旗舰，32GB GDDR7', cost: 2000, flops: 30000, watt: 600 },
  { id: 'g6', cat: 'GPU 显卡', name: 'L40S', desc: 'NVIDIA推理专用卡，48GB显存', cost: 2000, flops: 25000, watt: 350 },
  { id: 'g7', cat: 'GPU 显卡', name: 'A100 40GB', desc: '数据中心经典，Ampere架构', cost: 4000, flops: 50000, watt: 400 },
  { id: 'g8', cat: 'GPU 显卡', name: 'A100 80GB', desc: '大显存版，训练7B-13B模型', cost: 6000, flops: 70000, watt: 400 },
  { id: 'g9', cat: 'GPU 显卡', name: 'H100 SXM', desc: 'Hopper架构主力，96GB HBM3', cost: 50000, flops: 500000, watt: 700 },
  { id: 'g10', cat: 'GPU 显卡', name: 'H100 NVL', desc: '长上下文专用，支持96GB统一显存', cost: 80000, flops: 650000, watt: 400 },
  { id: 'g11', cat: 'GPU 显卡', name: 'H200', desc: '最新HBM3e显存，带宽翻倍', cost: 150000, flops: 1000000, watt: 700 },
  { id: 'g12', cat: 'GPU 显卡', name: 'MI300X', desc: 'AMD旗舰，192GB显存，大模型训练', cost: 500000, flops: 4000000, watt: 750 },
  { id: 'g13', cat: 'GPU 显卡', name: 'MI325X', desc: '256GB显存，超长上下文', cost: 800000, flops: 6000000, watt: 800 },
  { id: 'g14', cat: 'GPU 显卡', name: 'TPU v5e', desc: 'Google推理芯片，T Pod部署', cost: 2000000, flops: 15000000, watt: 500 },
  { id: 'g15', cat: 'GPU 显卡', name: 'TPU v5p', desc: 'Google训练旗舰，浮点性能强', cost: 5000000, flops: 35000000, watt: 800 },
  { id: 'g16', cat: 'GPU 显卡', name: 'TPU v6 Trillium', desc: '最新TPU，性能比v5p高4.7倍', cost: 20000000, flops: 150000000, watt: 900 },
  { id: 'g20', cat: 'GPU 显卡', name: 'Rubin Ultra', desc: 'NVIDIA下一代机架级GPU', cost: 50000000, flops: 2000000000, watt: 1200 },
  { id: 'g17', cat: 'GPU 显卡', name: '量子处理器', desc: '量子比特计算，并行训练', cost: 100000000, flops: 500000000, watt: 1500 },
  { id: 'g21', cat: 'GPU 显卡', name: '神经拟态芯片', desc: '类脑计算，事件驱动推理', cost: 500000000, flops: 10000000000, watt: 2000 },
  { id: 'g18', cat: 'GPU 显卡', name: '轨道计算卫星', desc: '太空太阳能供电，零延迟星地互联', cost: 1000000000, flops: 3000000000, watt: 5000 },

  // ===== CPU 处理器（按价格排序） =====
  { id: 'c1', cat: 'CPU 处理器', name: 'Core i3-13100', desc: '入门桌面CPU，4核8线程', cost: 30, flops: 500, watt: 58 },
  { id: 'c2', cat: 'CPU 处理器', name: 'Core i5-13600K', desc: '主流开发机，14核20线程', cost: 100, flops: 2000, watt: 125 },
  { id: 'c3', cat: 'CPU 处理器', name: 'Core i7-13700K', desc: '高性能桌面，20核28线程', cost: 300, flops: 5000, watt: 253 },
  { id: 'c6', cat: 'CPU 处理器', name: 'Xeon Silver 4410', desc: '入门服务器CPU，20核', cost: 500, flops: 3000, watt: 185 },
  { id: 'c5', cat: 'CPU 处理器', name: 'Ryzen 9 7950X', desc: 'AMD 16核32线程，性价比高', cost: 800, flops: 10000, watt: 170 },
  { id: 'c4', cat: 'CPU 处理器', name: 'Core i9-14900K', desc: '消费级顶配，24核32线程', cost: 1000, flops: 12000, watt: 253 },
  { id: 'c7', cat: 'CPU 处理器', name: 'Xeon Gold 6448Y', desc: '主流服务器，32核，支持多路', cost: 3000, flops: 15000, watt: 270 },
  { id: 'c8', cat: 'CPU 处理器', name: 'EPYC 9354', desc: 'AMD 32核工作站处理器', cost: 5000, flops: 25000, watt: 280 },
  { id: 'c9', cat: 'CPU 处理器', name: 'Xeon Platinum 8480', desc: 'Intel顶级服务器，56核', cost: 10000, flops: 50000, watt: 350 },
  { id: 'c10', cat: 'CPU 处理器', name: 'EPYC 9654', desc: 'AMD 96核旗舰，多路训练节点', cost: 15000, flops: 120000, watt: 360 },
  { id: 'c11', cat: 'CPU 处理器', name: 'Threadripper 7960X', desc: '64核工作站，数据预处理利器', cost: 50000, flops: 300000, watt: 350 },
  { id: 'c12', cat: 'CPU 处理器', name: 'Threadripper Pro 7995WX', desc: '96核顶配，四路满血', cost: 150000, flops: 1000000, watt: 350 },

  // ===== 内存 RAM（按价格排序） =====
  { id: 'm1', cat: '内存 RAM', name: '16GB DDR5', desc: '入门容量，跑个小脚本', cost: 20, flops: 200, watt: 5 },
  { id: 'm2', cat: '内存 RAM', name: '32GB DDR5', desc: '开发机标配，跑7B模型量化', cost: 60, flops: 500, watt: 8 },
  { id: 'm3', cat: '内存 RAM', name: '64GB DDR5 ECC', desc: '工作站容量，支持微调', cost: 200, flops: 2000, watt: 12 },
  { id: 'm4', cat: '内存 RAM', name: '128GB DDR5 ECC', desc: '训练节点，加载大batch', cost: 600, flops: 6000, watt: 18 },
  { id: 'm5', cat: '内存 RAM', name: '256GB DDR5 ECC', desc: '大模型CPU推理', cost: 2000, flops: 20000, watt: 25 },
  { id: 'm6', cat: '内存 RAM', name: '512GB DDR5 全通道', desc: '多卡服务器共享内存', cost: 8000, flops: 60000, watt: 40 },
  { id: 'm7', cat: '内存 RAM', name: '2TB HBM3e', desc: '高带宽显存，近存计算', cost: 50000, flops: 300000, watt: 100 },
  { id: 'm8', cat: '内存 RAM', name: '8TB CXL 内存池', desc: '池化内存，跨节点共享', cost: 200000, flops: 1000000, watt: 200 },

  // ===== 存储与基建（按价格排序） =====
  { id: 's1', cat: '存储与基建', name: '2TB NVMe SSD', desc: '本地训练数据集缓存', cost: 100, flops: 300, watt: 7 },
  { id: 's2', cat: '存储与基建', name: '4TB NVMe SSD', desc: '高速数据集加载', cost: 250, flops: 800, watt: 8 },
  { id: 's3', cat: '存储与基建', name: '16TB SAS HDD', desc: '冷数据归档存储', cost: 500, flops: 1000, watt: 10 },
  { id: 's5', cat: '存储与基建', name: 'InfiniBand HDR 200G', desc: 'GPU卡间高速互联', cost: 5000, flops: 10000, watt: 30 },
  { id: 's8', cat: '存储与基建', name: '液冷散热系统', desc: '降低GPU温度，防止降频', cost: 5000, flops: 5000, watt: 500 },
  { id: 's9', cat: '存储与基建', name: '柴油发电机组', desc: '7x24不间断供电保障', cost: 20000, flops: 15000, watt: 1000 },
  { id: 's6', cat: '存储与基建', name: 'InfiniBand NDR 400G', desc: '万卡集群网络骨干', cost: 20000, flops: 40000, watt: 50 },
  { id: 's4', cat: '存储与基建', name: '全闪存阵列', desc: '并行存储，多GPU同时读数据', cost: 30000, flops: 80000, watt: 200 },
  { id: 's7', cat: '存储与基建', name: 'InfiniBand XDR 800G', desc: '超算级无损网络', cost: 100000, flops: 200000, watt: 80 },
  { id: 's10', cat: '存储与基建', name: '太阳能发电站', desc: '绿色算力，零边际电费', cost: 1000000, flops: 2000000, watt: 5000 },
  { id: 's11', cat: '存储与基建', name: '核聚变反应堆', desc: '近乎无限的清洁能源', cost: 10000000000, flops: 500000000, watt: 50000 },

  // ===== 软件与数据（按价格排序，全加点击收益） =====
  { id: 'sw9', cat: '软件与数据', name: '手写笔记工具', desc: '记录训练灵感，每次点击+50', cost: 20, clickBonus: 50, watt: 0 },
  { id: 'sw10', cat: '软件与数据', name: 'Jupyter Notebook', desc: '交互式实验环境，每次点击+200', cost: 50, clickBonus: 200, watt: 0 },
  { id: 'sw1', cat: '软件与数据', name: '数据预处理脚本', desc: '加速数据清洗，每次点击+500', cost: 100, clickBonus: 500, watt: 0 },
  { id: 'sw11', cat: '软件与数据', name: 'VS Code 插件包', desc: '代码补全和调试，每次点击+500', cost: 200, clickBonus: 500, watt: 0 },
  { id: 'sw12', cat: '软件与数据', name: 'Git 版本控制', desc: '管理实验代码版本，每次点击+1K', cost: 500, clickBonus: 1000, watt: 0 },
  { id: 'sw2', cat: '软件与数据', name: '高效数据采样器', desc: '重要性采样，每次点击+2K', cost: 1000, clickBonus: 2000, watt: 0 },
  { id: 'sw13', cat: '软件与数据', name: 'Docker 容器化', desc: '环境一键复现，每次点击+2K', cost: 2000, clickBonus: 2000, watt: 0 },
  { id: 'sw14', cat: '软件与数据', name: 'CI/CD 流水线', desc: '自动测试和部署，每次点击+5K', cost: 5000, clickBonus: 5000, watt: 0 },
  { id: 'sw3', cat: '软件与数据', name: '数据标注平台', desc: '人工标注提升质量，每次点击+8K', cost: 10000, clickBonus: 8000, watt: 0 },
  { id: 'sw15', cat: '软件与数据', name: '实验跟踪工具', desc: '记录每次实验指标，每次点击+10K', cost: 20000, clickBonus: 10000, watt: 0 },
  { id: 'sw16', cat: '软件与数据', name: '超参数自动搜索', desc: '自动调参，每次点击+20K', cost: 50000, clickBonus: 20000, watt: 0 },
  { id: 'sw4', cat: '软件与数据', name: 'BPE Tokenizer', desc: '更高效的分词，每次点击+30K', cost: 100000, clickBonus: 30000, watt: 0 },
  { id: 'sw17', cat: '软件与数据', name: '数据版本管理', desc: 'DVC管理数据集版本，每次点击+50K', cost: 200000, clickBonus: 50000, watt: 0 },
  { id: 'sw18', cat: '软件与数据', name: '自动标注流水线', desc: '弱标注自动清洗，每次点击+100K', cost: 500000, clickBonus: 100000, watt: 0 },
  { id: 'sw5', cat: '软件与数据', name: '课程学习调度', desc: '从易到难训练，每次点击+100K', cost: 1000000, clickBonus: 100000, watt: 0 },
  { id: 'sw19', cat: '软件与数据', name: '主动学习', desc: '选最有价值的样本标注，每次点击+200K', cost: 2000000, clickBonus: 200000, watt: 0 },
  { id: 'sw20', cat: '软件与数据', name: '课程学习 v2', desc: '难度自适应调度，每次点击+500K', cost: 5000000, clickBonus: 500000, watt: 0 },
  { id: 'sw6', cat: '软件与数据', name: '数据引擎', desc: '自动筛选高质量数据，每次点击+500K', cost: 10000000, clickBonus: 500000, watt: 0 },
  { id: 'sw21', cat: '软件与数据', name: '模型蒸馏', desc: '大模型教小模型，每次点击+1M', cost: 20000000, clickBonus: 1000000, watt: 0 },
  { id: 'sw22', cat: '软件与数据', name: '知识蒸馏', desc: '压缩模型同时保留能力，每次点击+2M', cost: 50000000, clickBonus: 2000000, watt: 0 },
  { id: 'sw7', cat: '软件与数据', name: '合成数据生成器', desc: '用小模型造训练数据，每次点击+2.5M', cost: 100000000, clickBonus: 2500000, watt: 0 },
  { id: 'sw23', cat: '软件与数据', name: '奖励模型训练', desc: '训练RLHF奖励模型，每次点击+5M', cost: 200000000, clickBonus: 5000000, watt: 0 },
  { id: 'sw24', cat: '软件与数据', name: '人类反馈对齐', desc: '收集人类偏好数据，每次点击+10M', cost: 500000000, clickBonus: 10000000, watt: 0 },
  { id: 'sw8', cat: '软件与数据', name: '世界模型数据', desc: '生成模拟环境训练数据，每次点击+10M', cost: 1000000000, clickBonus: 10000000, watt: 0 },
  { id: 'sw25', cat: '软件与数据', name: '思维链数据', desc: '逐步推理标注，每次点击+20M', cost: 2000000000, clickBonus: 20000000, watt: 0 },
  { id: 'sw26', cat: '软件与数据', name: '工具调用数据', desc: 'API调用轨迹训练，每次点击+50M', cost: 5000000000, clickBonus: 50000000, watt: 0 },
  { id: 'sw27', cat: '软件与数据', name: '多步推理数据', desc: '复杂任务分解训练，每次点击+100M', cost: 20000000000, clickBonus: 100000000, watt: 0 },
  { id: 'sw28', cat: '软件与数据', name: '自我对弈', desc: '模型和自己下棋进化，每次点击+500M', cost: 100000000000, clickBonus: 500000000, watt: 0 },
  { id: 'sw29', cat: '软件与数据', name: '递归自我改进', desc: '模型改进自己的训练数据，每次点击+1B', cost: 500000000000, clickBonus: 1000000000, watt: 0 },
  { id: 'sw30', cat: '软件与数据', name: '进化算法搜索', desc: '自动进化更好的模型结构，每次点击+3B', cost: 2000000000000, clickBonus: 3000000000, watt: 0 },
  { id: 'sw31', cat: '软件与数据', name: 'AGI 种子数据', desc: '通用智能的种子样本，每次点击+10B', cost: 10000000000000, clickBonus: 10000000000, watt: 0 },
];

// ===== Logs =====
const LOG_MSGS = [
  () => `Epoch ${rand(1,999)}/1000 | loss: ${(Math.random()*3+0.1).toFixed(4)} | lr: 1e-4`,
  () => `Step ${rand(1000,99999)} | grad_norm: ${(Math.random()*2).toFixed(3)}`,
  () => `Throughput: ${rand(10,500)*1000} tokens/s | GPU util: ${rand(80,99)}%`,
  () => `Loss spike at step ${rand(1000,99999)}, clipping gradients...`,
  () => `Checkpoint saved: step_${rand(100,999)}.pt`,
  () => `Eval MMLU: ${(Math.random()*0.5+0.1).toFixed(3)} | HellaSwag: ${(Math.random()*0.5+0.2).toFixed(3)}`,
  () => `GPU ${rand(0,15)} temp: ${rand(70,89)}°C`,
  () => `Tokenizer encoding ${rand(32,256)} sequences...`,
  () => `Data shard ${rand(0,999)} loaded, ${rand(80,100)}% used`,
  () => `NaN loss detected, skipping batch`,
  () => `Wandb run #${rand(1,999)} | wall clock: ${rand(1,120)}min`,
  () => `Distributed rank ${rand(0,15)} sync complete`,
];
function rand(a,b) { return Math.floor(Math.random()*(b-a+1))+a; }

// ===== Calculations =====
function getClickPower() {
  let base = 1;
  for (const p of PRODUCTS) {
    if (state.owned[p.id] && p.clickBonus) base += p.clickBonus;
  }
  return base;
}
function getAutoPower() {
  let total = 0;
  for (const p of PRODUCTS) {
    const n = state.owned[p.id] || 0;
    total += (p.flops || 0) * n;
  }
  return total;
}
function getCost(p) {
  const n = state.owned[p.id] || 0;
  return Math.floor(p.cost * Math.pow(1.5, n));
}
function getTotalWatt() {
  let w = 0;
  for (const p of PRODUCTS) {
    const n = state.owned[p.id] || 0;
    w += (p.watt || 0) * n;
  }
  return w;
}
function fmt(n) {
  if (n < 1000) return n.toFixed(n < 10 ? 2 : 0);
  const u = ['','K','M','B','T','Qa','Qi']; let i = 0;
  while (n >= 1000 && i < u.length-1) { n /= 1000; i++; }
  return n.toFixed(2) + u[i];
}

// ===== DOM =====
const el = {
  totalFLOPs: document.getElementById('totalFLOPs'),
  progressBar: document.getElementById('progressBar'),
  progressPct: document.getElementById('progressPct'),
  progressTarget: document.getElementById('progressTarget'),
  clickPower: document.getElementById('clickPower'),
  autoPower: document.getElementById('autoPower'),
  trainBtn: document.getElementById('trainBtn'),
  terminalBody: document.getElementById('terminalBody'),
  shopList: document.getElementById('shopList'),
  gpuList: document.getElementById('gpuList'),
  gpuCount: document.getElementById('gpuCount'),
  cpuVal: document.getElementById('cpuVal'),
  cpuBar: document.getElementById('cpuBar'),
  ramVal: document.getElementById('ramVal'),
  ramBar: document.getElementById('ramBar'),
  powerVal: document.getElementById('powerVal'),
  victoryModal: document.getElementById('victoryModal'),
  victoryStats: document.getElementById('victoryStats'),
  restartBtn: document.getElementById('restartBtn'),
  passModal: document.getElementById('passModal'),
  passInput: document.getElementById('passInput'),
  passError: document.getElementById('passError'),
  passConfirm: document.getElementById('passConfirm'),
  passCancel: document.getElementById('passCancel'),
  debugModal: document.getElementById('debugModal'),
  debugStats: document.getElementById('debugStats'),
  targetInput: document.getElementById('targetInput'),
  setTargetBtn: document.getElementById('setTargetBtn'),
  currentTarget: document.getElementById('currentTarget'),
  customName: document.getElementById('customName'),
  customCat: document.getElementById('customCat'),
  customValue: document.getElementById('customValue'),
  customCost: document.getElementById('customCost'),
  addCustomBtn: document.getElementById('addCustomBtn'),
  unlockAllBtn: document.getElementById('unlockAllBtn'),
  winBtn: document.getElementById('winBtn'),
  closeDebugBtn: document.getElementById('closeDebugBtn'),
  titleEl: document.getElementById('titleEl'),
};

// ===== Shop Render =====
let shopEls = {};
let showAffordableOnly = false;
function getMax(p) {
  if (p.max) return p.max;
  return p.cat === 'GPU 显卡' ? Infinity : 1;
}
function renderShop() {
  el.shopList.innerHTML = '';
  shopEls = {};
  let lastCat = '';
  for (const p of PRODUCTS) {
    const cost = getCost(p);
    const owned = state.owned[p.id] || 0;
    const max = getMax(p);
    const maxed = owned >= max;
    const affordable = state.totalFLOPs >= cost && !maxed;
    if (showAffordableOnly && !affordable) continue;
    if (p.cat !== lastCat) {
      const lbl = document.createElement('div');
      lbl.className = 'shop-cat';
      lbl.textContent = p.cat;
      el.shopList.appendChild(lbl);
      lastCat = p.cat;
    }
    const item = document.createElement('div');
    item.className = 'shop-item' + (maxed ? ' maxed' : '');
    const ownText = max === Infinity ? `已拥有 ×${owned}` : (maxed ? '已拥有' : '');
    item.innerHTML = `
      <div class="shop-info">
        <div class="shop-name">${p.name}</div>
        <div class="shop-desc">${p.desc || ''}</div>
        <div class="shop-desc" style="color:var(--accent);opacity:0.7;">${p.clickBonus ? '+'+fmt(p.clickBonus)+'/次点击' : '+'+fmt(p.flops)+'/s'} · ${p.watt||0}W${max !== Infinity ? ' · 限1件' : ''}</div>
        ${ownText ? `<div class="shop-own">${ownText}</div>` : ''}
      </div>`;
    const btn = document.createElement('button');
    btn.className = 'shop-buy';
    btn.onclick = () => buyProduct(p);
    item.appendChild(btn);
    el.shopList.appendChild(item);
    shopEls[p.id] = { item, btn };
  }
  refreshShop();
}
function refreshShop() {
  for (const p of PRODUCTS) {
    const r = shopEls[p.id]; if (!r) continue;
    const owned = state.owned[p.id] || 0;
    const max = getMax(p);
    const maxed = owned >= max;
    const cost = getCost(p);
    const aff = state.totalFLOPs >= cost && !maxed;
    r.item.classList.toggle('affordable', aff);
    r.item.classList.toggle('maxed', maxed);
    r.btn.disabled = !aff;
    if (maxed) {
      r.btn.innerHTML = `✓<span class="qty">已买</span>`;
    } else {
      r.btn.innerHTML = `${fmt(cost)}<span class="qty">买${max === Infinity ? ' ×' + (owned+1) : ''}</span>`;
    }
    const ownEl = r.item.querySelector('.shop-own');
    if (ownEl) {
      ownEl.textContent = max === Infinity ? `已拥有 ×${owned}` : '已拥有';
    }
  }
}

function buyProduct(p) {
  const cost = getCost(p);
  const owned = state.owned[p.id] || 0;
  if (state.totalFLOPs < cost || owned >= getMax(p)) return;
  state.totalFLOPs -= cost;
  state.owned[p.id] = owned + 1;
  const gain = p.clickBonus ? `+${fmt(p.clickBonus)}/点击` : `+${fmt(p.flops)}/s`;
  addLog(`[SHOP] 购入 ${p.name} ×${state.owned[p.id]} (${gain})`, 'buy');
  render(); renderShop(); renderTM();
}

// ===== Task Manager =====
function renderTM() {
  const gpus = PRODUCTS.filter(p => p.cat === 'GPU 显卡');
  let gpuTotal = 0;
  let gpuHtml = '';
  let gpuIdx = 0;
  for (const g of gpus) {
    const n = state.owned[g.id] || 0;
    for (let i = 0; i < n; i++) {
      gpuIdx++;
      gpuTotal++;
      const util = rand(75, 99);
      const temp = rand(65, 92);
      const memPct = rand(60, 98);
      gpuHtml += `<div class="gpu-item">
        <div>
          <div class="gpu-name">GPU ${gpuIdx}: ${g.name}</div>
          <div style="color:var(--text-dim);font-size:10px;margin-top:2px;">显存 ${memPct}% · ${fmt(g.flops)} TFLOPS</div>
        </div>
        <div class="gpu-stats">
          <div>利用率 ${util}%</div>
          <div class="gpu-temp${temp > 85 ? ' hot' : ''}">${temp}°C</div>
        </div>
      </div>`;
    }
  }
  el.gpuCount.textContent = gpuTotal;
  el.gpuList.innerHTML = gpuHtml || '<div style="color:var(--text-dim);font-size:11px;text-align:center;padding:10px;">还没有GPU，去商店买一块吧</div>';

  // CPU & RAM
  const auto = getAutoPower();
  const cpuPct = Math.min(99, 20 + Math.min(79, auto / 1000));
  const ramGB = Math.min(1024, Math.floor(2 + auto / 50));
  el.cpuVal.textContent = Math.round(cpuPct) + '%';
  el.cpuBar.style.width = cpuPct + '%';
  el.cpuBar.className = 'tm-bar-fill ' + (cpuPct > 85 ? 'red' : cpuPct > 60 ? 'amber' : 'green');
  el.ramVal.textContent = ramGB + ' GB';
  el.ramBar.style.width = Math.min(100, ramGB / 10) + '%';
  el.powerVal.textContent = fmt(getTotalWatt()) + ' W';
}

// ===== Terminal =====
function addLog(text, cls) {
  const line = document.createElement('div');
  line.className = 'line' + (cls ? ' ' + cls : '');
  line.textContent = text;
  el.terminalBody.appendChild(line);
  while (el.terminalBody.children.length > 50) el.terminalBody.removeChild(el.terminalBody.firstChild);
  el.terminalBody.scrollTop = el.terminalBody.scrollHeight;
}
function randomLog() {
  if (Math.random() < 0.4) return;
  addLog(LOG_MSGS[Math.floor(Math.random()*LOG_MSGS.length)]());
}

// ===== Render =====
function render() {
  el.totalFLOPs.textContent = fmt(state.totalFLOPs);
  const pct = Math.min(100, state.totalFLOPs / TARGET_FLOPS * 100);
  el.progressBar.style.width = pct + '%';
  el.progressPct.textContent = pct.toFixed(2) + '%';
  el.clickPower.textContent = fmt(getClickPower());
  el.autoPower.textContent = fmt(getAutoPower()) + '/s';
  refreshShop();
}

// ===== Train =====
function train(e) {
  const gain = getClickPower();
  state.totalFLOPs += gain;
  state.totalClicks++;
  render();
  if (e) {
    const rect = el.trainBtn.getBoundingClientRect();
    const s = document.createElement('span');
    s.className = 'float-num';
    s.textContent = '+' + fmt(gain);
    s.style.left = (e.clientX || rect.left + rect.width/2) + 'px';
    s.style.top = (e.clientY || rect.top) + 'px';
    document.body.appendChild(s);
    setTimeout(() => s.remove(), 800);
  }
  checkVictory();
}

function checkVictory() {
  if (state.totalFLOPs >= TARGET_FLOPS && !el.victoryModal.classList.contains('hidden')) return;
  if (state.totalFLOPS >= TARGET_FLOPS) {
    const s = Math.round((Date.now()-state.startTime)/1000);
    const m = Math.floor(s/60);
    el.victoryStats.innerHTML = `总算力: ${fmt(state.totalFLOPs)}<br>点击: ${state.totalClicks}<br>用时: ${m}分${s%60}秒<br>设备: ${Object.values(state.owned).reduce((a,b)=>a+b,0)}台`;
    el.victoryModal.classList.remove('hidden');
  }
}

// ===== Page Switching =====
document.querySelectorAll('.nav-btn').forEach(btn => {
  btn.onclick = () => {
    document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
    document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
    btn.classList.add('active');
    document.getElementById(btn.dataset.page).classList.add('active');
    if (btn.dataset.page === 'pageTM') renderTM();
  };
});

// ===== Game Loop =====
let lastT = Date.now(), logT = 0, tmT = 0;
function loop() {
  const now = Date.now();
  const dt = (now - lastT) / 1000;
  lastT = now;
  state.totalFLOPs += getAutoPower() * dt;
  logT += dt;
  if (logT > 1.5) { logT = 0; randomLog(); }
  tmT += dt;
  if (tmT > 2 && document.getElementById('pageTM').classList.contains('active')) { tmT = 0; renderTM(); }
  render();
  checkVictory();
  requestAnimationFrame(loop);
}

// ===== Debug Menu =====
let tClicks = 0, tTimer = null;
el.titleEl.addEventListener('click', () => {
  tClicks++; clearTimeout(tTimer);
  tTimer = setTimeout(() => tClicks = 0, 1500);
  if (tClicks >= 5) {
    tClicks = 0;
    el.passModal.classList.remove('hidden');
    el.passInput.value = ''; el.passError.textContent = '';
    setTimeout(() => el.passInput.focus(), 100);
  }
});
el.passCancel.onclick = () => el.passModal.classList.add('hidden');
el.passConfirm.onclick = () => {
  if (el.passInput.value === '0000') {
    el.passModal.classList.add('hidden');
    openDebug();
  } else { el.passError.textContent = '密码错误'; el.passInput.value=''; el.passInput.focus(); }
};
el.passInput.addEventListener('keydown', e => { if (e.key === 'Enter') el.passConfirm.onclick(); });

function openDebug() {
  el.debugModal.classList.remove('hidden');
  el.currentTarget.textContent = '当前目标: ' + fmt(TARGET_FLOPS);
  updateDebugStats();
}
function updateDebugStats() {
  el.debugStats.innerHTML = `FLOPs: ${fmt(state.totalFLOPs)}<br>自动: ${fmt(getAutoPower())}/s<br>设备: ${Object.values(state.owned).reduce((a,b)=>a+b,0)}`;
}
document.querySelectorAll('.debug-btn[data-add]').forEach(b => {
  b.onclick = () => {
    state.totalFLOPs += parseFloat(b.dataset.add);
    addLog(`[DEBUG] 注入 ${fmt(b.dataset.add)} FLOPs`, 'buy');
    render(); updateDebugStats(); checkVictory();
  };
});
el.setTargetBtn.onclick = () => {
  const v = parseFloat(el.targetInput.value);
  if (v > 0) { TARGET_FLOPS = v; el.currentTarget.textContent = '当前目标: ' + fmt(TARGET_FLOPS); render(); }
};
let customId = 100;
el.addCustomBtn.onclick = () => {
  const name = el.customName.value.trim();
  const cat = el.customCat.value;
  const val = parseFloat(el.customValue.value);
  const cost = parseFloat(el.customCost.value);
  if (!name || !val || !cost) return;
  PRODUCTS.push({ id: 'cust'+(customId++), cat, name, desc: '自定义设备', cost, flops: val, watt: 500 });
  addLog(`[DEBUG] 商店新增: ${name}`, 'buy');
  el.customName.value = ''; el.customValue.value = ''; el.customCost.value = '';
  renderShop(); updateDebugStats();
};
el.unlockAllBtn.onclick = () => {
  for (const p of PRODUCTS) state.owned[p.id] = 1;
  addLog('[DEBUG] 已买空商店', 'buy');
  render(); renderShop(); renderTM(); updateDebugStats();
};
el.winBtn.onclick = () => {
  state.totalFLOPs = TARGET_FLOPS;
  el.debugModal.classList.add('hidden');
  render(); checkVictory();
};
el.closeDebugBtn.onclick = () => el.debugModal.classList.add('hidden');

// ===== Restart =====
el.restartBtn.onclick = () => {
  state = { totalFLOPs: 0, totalClicks: 0, owned: {}, startTime: Date.now(), victoryShown: false };
  el.victoryModal.classList.add('hidden');
  el.terminalBody.innerHTML = '';
  addLog('Data Center Trainer 重启...', 'info');
  render(); renderShop(); renderTM();
};

// ===== Display Mode =====
let displayMode = 'auto';
function detectDevice() {
  const isMobile = /Android|iPhone|iPad|iPod|Mobile/i.test(navigator.userAgent) || window.innerWidth < 768;
  return isMobile ? 'mobile' : 'desktop';
}
function applyMode() {
  let m = displayMode;
  if (m === 'auto') m = detectDevice();
  document.body.classList.toggle('desktop', m === 'desktop');
  document.querySelectorAll('.display-mode-btn').forEach(b => {
    b.style.opacity = b.dataset.mode === displayMode ? '1' : '0.5';
  });
  const el2 = document.getElementById('modeStatus');
  if (el2) el2.textContent = displayMode === 'auto'
    ? `自动识别 → 当前是${m === 'desktop' ? '电脑' : '手机'}版布局`
    : `手动设置 → ${displayMode === 'desktop' ? '电脑版' : '手机版'}布局`;
}
document.querySelectorAll('.display-mode-btn').forEach(b => {
  b.onclick = () => { displayMode = b.dataset.mode; applyMode(); };
});
window.addEventListener('resize', () => { if (displayMode === 'auto') applyMode(); });

// ===== Shop Filter =====
const showAffordableBtn = document.getElementById('showAffordableBtn');
const showAllBtn = document.getElementById('showAllBtn');
showAffordableBtn.onclick = () => {
  showAffordableOnly = true;
  showAffordableBtn.style.opacity = '1';
  showAllBtn.style.opacity = '0.5';
  renderShop();
};
showAllBtn.onclick = () => {
  showAffordableOnly = false;
  showAllBtn.style.opacity = '1';
  showAffordableBtn.style.opacity = '0.5';
  renderShop();
};

// ===== Init =====
el.trainBtn.addEventListener('click', train);
addLog('Data Center Trainer v2.7 启动...', 'info');
addLog('初始化权重... 随机种子: 42', 'info');
addLog('开始训练循环', 'info');
render(); renderShop(); renderTM(); applyMode();
requestAnimationFrame(loop);
</script>
</body>
</html>
