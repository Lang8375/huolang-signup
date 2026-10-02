<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🐺 火狼狼人殺 報名系統</title>
  <style>
    :root {
      --bg-color: #0f172a;
      --card-bg: #1e293b;
      --card-border: #334155;
      --primary: #f97316;
      --primary-hover: #ea580c;
      --text-main: #f8fafc;
      --text-muted: #94a3b8;
      --danger: #ef4444;
      --danger-hover: #dc2626;
      --tag-bg: #374151;
      --accent: #eab308;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background-color: var(--bg-color);
      color: var(--text-main);
      padding: 20px 14px 60px;
      display: flex;
      justify-content: center;
    }

    .container {
      width: 100%;
      max-width: 580px;
      display: flex;
      flex-direction: column;
      gap: 16px;
    }

    /* 頂部卡片 */
    .card {
      background-color: var(--card-bg);
      border: 1px solid var(--card-border);
      border-radius: 12px;
      padding: 20px;
      box-shadow: 0 4px 16px rgba(0, 0, 0, 0.35);
    }

    .header-title {
      font-size: 1.6rem;
      font-weight: 800;
      color: #ffedd5;
      display: flex;
      align-items: center;
      gap: 8px;
      margin-bottom: 12px;
    }

    .info-list {
      display: flex;
      flex-direction: column;
      gap: 8px;
      margin-bottom: 16px;
      font-size: 0.95rem;
    }

    .info-item {
      display: flex;
      align-items: baseline;
      gap: 6px;
    }

    .info-item strong {
      color: #fdba74;
      white-space: nowrap;
    }

    .fee-badge {
      background: #7c2d12;
      color: #ffedd5;
      padding: 2px 8px;
      border-radius: 6px;
      font-weight: 600;
    }

    .rules-list {
      background-color: rgba(0, 0, 0, 0.2);
      border-radius: 8px;
      padding: 12px 14px;
      display: flex;
      flex-direction: column;
      gap: 6px;
      font-size: 0.88rem;
      color: #cbd5e1;
    }

    .rules-list span {
      color: var(--primary);
      margin-right: 6px;
    }

    /* 狀態提示卡 */
    .status-banner {
      background: #064e3b;
      border: 1px solid #059669;
      color: #a7f3d0;
      padding: 12px 16px;
      border-radius: 8px;
      font-size: 0.9rem;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    /* 表單區塊 */
    .form-group {
      display: flex;
      flex-direction: column;
      gap: 6px;
      margin-bottom: 14px;
    }

    label {
      font-size: 0.88rem;
      color: var(--text-muted);
      font-weight: 600;
    }

    input, select {
      background-color: #0f172a;
      border: 1px solid var(--card-border);
      color: #fff;
      padding: 10px 12px;
      border-radius: 8px;
      font-size: 1rem;
      outline: none;
      transition: border-color 0.2s;
    }

    input:focus, select:focus {
      border-color: var(--primary);
    }

    .btn-group {
      display: flex;
      gap: 10px;
      margin-top: 16px;
    }

    button {
      cursor: pointer;
      font-weight: 600;
      border-radius: 8px;
      border: none;
      padding: 12px;
      font-size: 0.95rem;
      transition: background-color 0.2s;
    }

    .btn-primary {
      background-color: var(--primary);
      color: #fff;
      flex: 1;
    }

    .btn-primary:hover {
      background-color: var(--primary-hover);
    }

    .btn-danger {
      background-color: var(--danger);
      color: #fff;
      padding: 12px 18px;
    }

    .btn-danger:hover {
      background-color: var(--danger-hover);
    }

    /* 名單區塊 */
    .list-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 12px;
      border-bottom: 1px solid var(--card-border);
      padding-bottom: 10px;
    }

    .counter-badge {
      font-weight: 700;
      font-size: 1.1rem;
      color: #fdba74;
    }

    .player-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    .player-item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: rgba(15, 23, 42, 0.7);
      padding: 10px 14px;
      border-radius: 8px;
      border: 1px solid rgba(255, 255, 255, 0.05);
    }

    .player-index {
      width: 26px;
      height: 26px;
      background: #334155;
      color: #cbd5e1;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.8rem;
      font-weight: 700;
      margin-right: 10px;
    }

    .player-info {
      display: flex;
      align-items: center;
      flex: 1;
    }

    .player-name {
      font-weight: 600;
      font-size: 0.95rem;
    }

    .player-self-tag {
      background: #0284c7;
      font-size: 0.7rem;
      padding: 2px 6px;
      border-radius: 4px;
      margin-left: 6px;
      color: #fff;
    }

    .player-meta {
      font-size: 0.8rem;
      color: var(--text-muted);
      display: flex;
      gap: 8px;
    }

    .status-tag {
      padding: 2px 6px;
      border-radius: 4px;
      font-size: 0.75rem;
    }

    .tag-active {
      background: #065f46;
      color: #6ee7b7;
    }

    .tag-wait {
      background: #854d0e;
      color: #fde047;
    }
  </style>
</head>
<body>

  <div class="container">
    <!-- 主揪資訊板 -->
    <div class="card">
      <h1 class="header-title">🐺 火狼狼人殺</h1>
      <div class="info-list">
        <div class="info-item">
          <strong>📍 地點：</strong>
          <span>台中市北屯區天津路三段57號</span>
        </div>
        <div class="info-item">
          <strong>💰 費用：</strong>
          <span class="fee-badge">入場費 $200 打到破桌</span>
        </div>
      </div>
      <div class="rules-list">
        <p><span>◆</span> 禁止情緒激動、脾氣大的人</p>
        <p><span>◆</span> 禁止任何不禮貌行為</p>
        <p><span>◆</span> 臨時無法參加/延後請告知主揪</p>
        <p><span>◆</span> 請包容每一位玩家勿隨意批評</p>
        <p><span>◆</span> 開心最重要</p>
      </div>
    </div>

    <!-- 已報名狀態提示 (JS 動態切換) -->
    <div id="registeredBanner" class="status-banner" style="display: none;">
      💡 您已報名此場次，可直接在下方更新到場時間或取消報名。
    </div>

    <!-- 報名 / 修改表單 -->
    <div class="card">
      <form id="signupForm">
        <div class="form-group">
          <label for="userName">玩家暱稱</label>
          <input type="text" id="userName" placeholder="請輸入暱稱" required>
        </div>

        <div class="form-group">
          <label for="arriveTime">預計到場時間</label>
          <select id="arriveTime" required>
            <option value="準時開桌 (19:30)">準時開桌 (19:30)</option>
            <option value="20:00 前後">20:00 前後</option>
            <option value="20:30 前後">20:30 前後</option>
            <option value="晚到 (請備註時間)">晚到 (請備註時間)</option>
          </select>
        </div>

        <div class="form-group">
          <label for="userRemark">備註（選填）</label>
          <input type="text" id="userRemark" placeholder="如：+1朋友、幾點需離開等">
        </div>

        <div class="btn-group">
          <button type="submit" id="submitBtn" class="btn-primary">立即報名</button>
          <button type="button" id="cancelBtn" class="btn-danger" style="display: none;">取消報名</button>
        </div>
      </form>
    </div>

    <!-- 報名清單區 -->
    <div class="card">
      <div class="list-header">
        <h3>當前報名名單</h3>
        <span class="counter-badge">
          玩家：<span id="playerCount">0</span> / 12 人
        </span>
      </div>
      <ul id="playerList" class="player-list">
        <!-- 名單由 JS 渲染 -->
      </ul>
    </div>
  </div>

  <script>
    // 預設示範名單
    const DEFAULT_PLAYERS = [
      { id: '1', name: '阿廷 (主揪)', time: '準時開桌 (19:30)', remark: '主揪位' },
      { id: '2', name: '小黑', time: '準時開桌 (19:30)', remark: '' },
      { id: '3', name: 'Ray', time: '20:00 前後', remark: '下班趕過來' }
    ];

    // 初始化 LocalStorage 資料
    let players = JSON.parse(localStorage.getItem('huolang_players')) || DEFAULT_PLAYERS;
    let myRegistration = JSON.parse(localStorage.getItem('huolang_my_reg')) || null;

    const signupForm = document.getElementById('signupForm');
    const userNameInput = document.getElementById('userName');
    const arriveTimeInput = document.getElementById('arriveTime');
    const userRemarkInput = document.getElementById('userRemark');
    const submitBtn = document.getElementById('submitBtn');
    const cancelBtn = document.getElementById('cancelBtn');
    const registeredBanner = document.getElementById('registeredBanner');
    const playerList = document.getElementById('playerList');
    const playerCount = document.getElementById('playerCount');

    // 儲存並渲染
    function saveAndRender() {
      localStorage.setItem('huolang_players', JSON.stringify(players));
      localStorage.setItem('huolang_my_reg', JSON.stringify(myRegistration));
      renderList();
      checkUserStatus();
    }

    // 檢查使用者報名狀態
    function checkUserStatus() {
      if (myRegistration) {
        registeredBanner.style.display = 'flex';
        userNameInput.value = myRegistration.name;
        userNameInput.disabled = true; // 鎖定名稱
        arriveTimeInput.value = myRegistration.time;
        userRemarkInput.value = myRegistration.remark || '';
        submitBtn.textContent = '更新報名資訊';
        cancelBtn.style.display = 'block';
      } else {
        registeredBanner.style.display = 'none';
        userNameInput.disabled = false;
        userNameInput.value = '';
        arriveTimeInput.value = '準時開桌 (19:30)';
        userRemarkInput.value = '';
        submitBtn.textContent = '立即報名';
        cancelBtn.style.display = 'none';
      }
    }

    // 渲染名單列表
    function renderList() {
      playerList.innerHTML = '';
      playerCount.textContent = players.length;

      players.forEach((p, idx) => {
        const li = document.createElement('li');
        li.className = 'player-item';

        const isSelf = myRegistration && p.id === myRegistration.id;
        const isWaiting = idx >= 12;

        li.innerHTML = `
          <div class="player-info">
            <span class="player-index">${idx + 1}</span>
            <span class="player-name">${p.name}</span>
            ${isSelf ? '<span class="player-self-tag">您</span>' : ''}
          </div>
          <div class="player-meta">
            <span>${p.time}</span>
            <span class="status-tag ${isWaiting ? 'tag-wait' : 'tag-active'}">
              ${isWaiting ? '候補' : '正取'}
            </span>
          </div>
        `;
        playerList.appendChild(li);
      });
    }

    // 表單送出（報名或更新）
    signupForm.addEventListener('submit', (e) => {
      e.preventDefault();
      const name = userNameInput.value.trim();
      const time = arriveTimeInput.value;
      const remark = userRemarkInput.value.trim();

      if (!name) return;

      if (myRegistration) {
        // 更新現有資料
        const target = players.find(p => p.id === myRegistration.id);
        if (target) {
          target.time = time;
          target.remark = remark;
        }
        myRegistration.time = time;
        myRegistration.remark = remark;
      } else {
        // 新增報名
        const newEntry = {
          id: 'user_' + Date.now(),
          name: name,
          time: time,
          remark: remark
        };
        players.push(newEntry);
        myRegistration = newEntry;
      }

      saveAndRender();
    });

    // 取消報名
    cancelBtn.addEventListener('click', () => {
      if (!myRegistration) return;
      if (confirm('確定要取消報名嗎？')) {
        players = players.filter(p => p.id !== myRegistration.id);
        myRegistration = null;
        saveAndRender();
      }
    });

    // 初次載入
    saveAndRender();
  </script>
</body>
</html>
