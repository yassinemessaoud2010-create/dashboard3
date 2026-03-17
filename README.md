[dashboard.html](https://github.com/user-attachments/files/26067773/dashboard.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ahh Dashboard</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<style>
  :root {
    --bg-primary: #060d1f;
    --bg-secondary: #0a1628;
    --bg-card: #0e1d36;
    --bg-hover: #132240;
    --accent: #1a56db;
    --accent-light: #2563eb;
    --accent-glow: #3b82f6;
    --sidebar-width: 240px;
    --text-primary: #e8edf5;
    --text-secondary: #7a90b5;
    --text-muted: #4a607f;
    --border: #1a2d4f;
    --green: #22c55e;
    --red: #ef4444;
    --yellow: #f59e0b;
    --purple: #8b5cf6;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Nunito', sans-serif;
    background: var(--bg-primary);
    color: var(--text-primary);
    display: flex;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── SIDEBAR ── */
  .sidebar {
    width: var(--sidebar-width);
    background: var(--bg-secondary);
    border-right: 1px solid var(--border);
    display: flex;
    flex-direction: column;
    position: fixed;
    top: 0; left: 0;
    height: 100vh;
    z-index: 100;
    overflow-y: auto;
  }

  .sidebar-logo {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 20px 18px;
    border-bottom: 1px solid var(--border);
  }

  .bot-avatar {
    width: 38px; height: 38px;
    background: linear-gradient(135deg, var(--accent), var(--purple));
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 18px; font-weight: 800; color: #fff;
    box-shadow: 0 0 14px rgba(26,86,219,0.5);
    flex-shrink: 0;
  }

  .bot-name {
    font-size: 18px; font-weight: 800;
    background: linear-gradient(90deg, #60a5fa, #a78bfa);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    letter-spacing: 0.5px;
  }

  .sidebar-section {
    padding: 14px 10px 6px;
  }

  .sidebar-section-label {
    font-size: 10px; font-weight: 700;
    color: var(--text-muted);
    text-transform: uppercase;
    letter-spacing: 1.2px;
    padding: 0 8px 8px;
  }

  .nav-item {
    display: flex; align-items: center; gap: 10px;
    padding: 9px 12px;
    border-radius: 8px;
    cursor: pointer;
    color: var(--text-secondary);
    font-size: 13.5px; font-weight: 600;
    transition: all 0.18s;
    text-decoration: none;
  }

  .nav-item:hover { background: var(--bg-hover); color: var(--text-primary); }
  .nav-item.active { background: var(--accent); color: #fff; box-shadow: 0 2px 12px rgba(26,86,219,0.4); }

  .nav-item i { width: 18px; text-align: center; font-size: 14px; }

  .nav-badge {
    margin-left: auto;
    background: var(--red);
    color: #fff;
    font-size: 10px; font-weight: 700;
    padding: 1px 6px;
    border-radius: 10px;
  }

  .sidebar-server {
    margin-top: auto;
    padding: 14px;
    border-top: 1px solid var(--border);
  }

  .server-card {
    display: flex; align-items: center; gap: 10px;
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 10px 12px;
    cursor: pointer;
    transition: background 0.18s;
  }

  .server-card:hover { background: var(--bg-hover); }

  .server-icon {
    width: 34px; height: 34px;
    background: linear-gradient(135deg, #1a56db, #7c3aed);
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 14px; font-weight: 800; color: #fff;
    flex-shrink: 0;
  }

  .server-info { flex: 1; min-width: 0; }
  .server-name { font-size: 13px; font-weight: 700; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
  .server-status { font-size: 11px; color: var(--green); font-weight: 600; }

  /* ── MAIN ── */
  .main {
    margin-left: var(--sidebar-width);
    flex: 1;
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  /* ── TOPBAR ── */
  .topbar {
    background: var(--bg-secondary);
    border-bottom: 1px solid var(--border);
    padding: 0 28px;
    height: 60px;
    display: flex; align-items: center; justify-content: space-between;
    position: sticky; top: 0; z-index: 50;
  }

  .topbar-title { font-size: 17px; font-weight: 800; }

  .topbar-right { display: flex; align-items: center; gap: 14px; }

  .topbar-btn {
    width: 36px; height: 36px;
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    cursor: pointer; color: var(--text-secondary);
    transition: all 0.18s; font-size: 15px;
    position: relative;
  }

  .topbar-btn:hover { background: var(--bg-hover); color: var(--text-primary); }

  .notif-dot {
    position: absolute; top: 6px; right: 6px;
    width: 7px; height: 7px;
    background: var(--red); border-radius: 50%;
    border: 1.5px solid var(--bg-secondary);
  }

  .user-pill {
    display: flex; align-items: center; gap: 8px;
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 5px 12px 5px 5px;
    cursor: pointer; transition: background 0.18s;
  }

  .user-pill:hover { background: var(--bg-hover); }

  .user-avatar {
    width: 26px; height: 26px;
    background: linear-gradient(135deg, var(--accent), var(--purple));
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 11px; font-weight: 800; color: #fff;
  }

  .user-pill span { font-size: 13px; font-weight: 700; }

  /* ── CONTENT ── */
  .content {
    padding: 28px;
    flex: 1;
  }

  /* ── STATS ROW ── */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 16px;
    margin-bottom: 24px;
  }

  .stat-card {
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 20px;
    display: flex; align-items: center; gap: 14px;
    position: relative; overflow: hidden;
    transition: transform 0.18s, box-shadow 0.18s;
  }

  .stat-card:hover { transform: translateY(-2px); box-shadow: 0 8px 24px rgba(0,0,0,0.3); }

  .stat-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: var(--card-accent, var(--accent));
  }

  .stat-icon {
    width: 44px; height: 44px;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 18px; flex-shrink: 0;
    background: var(--icon-bg, rgba(26,86,219,0.15));
    color: var(--icon-color, var(--accent-glow));
  }

  .stat-label { font-size: 12px; color: var(--text-muted); font-weight: 600; margin-bottom: 4px; }
  .stat-value { font-size: 22px; font-weight: 800; }
  .stat-change { font-size: 11px; color: var(--green); font-weight: 600; margin-top: 2px; }

  /* ── GRID LAYOUT ── */
  .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-bottom: 24px; }
  .grid-3 { display: grid; grid-template-columns: 2fr 1fr; gap: 20px; margin-bottom: 24px; }

  /* ── CARDS ── */
  .card {
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: 14px;
    overflow: hidden;
  }

  .card-header {
    padding: 16px 20px;
    border-bottom: 1px solid var(--border);
    display: flex; align-items: center; justify-content: space-between;
  }

  .card-title { font-size: 14px; font-weight: 800; }
  .card-subtitle { font-size: 12px; color: var(--text-muted); margin-top: 2px; }

  .card-body { padding: 20px; }

  /* ── MODULE TOGGLE ── */
  .module-list { display: flex; flex-direction: column; gap: 2px; }

  .module-item {
    display: flex; align-items: center; justify-content: space-between;
    padding: 12px 20px;
    transition: background 0.15s; cursor: pointer;
    border-radius: 8px; margin: 1px 0;
  }

  .module-item:hover { background: var(--bg-hover); }

  .module-left { display: flex; align-items: center; gap: 12px; }

  .module-icon {
    width: 34px; height: 34px;
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 15px;
  }

  .module-name { font-size: 13px; font-weight: 700; }
  .module-desc { font-size: 11px; color: var(--text-muted); margin-top: 1px; }

  /* Toggle */
  .toggle {
    width: 40px; height: 22px;
    background: var(--text-muted);
    border-radius: 11px;
    position: relative; cursor: pointer;
    transition: background 0.2s; flex-shrink: 0;
  }

  .toggle.on { background: var(--accent); }

  .toggle::after {
    content: '';
    position: absolute;
    width: 16px; height: 16px;
    background: #fff;
    border-radius: 50%;
    top: 3px; left: 3px;
    transition: left 0.2s;
    box-shadow: 0 1px 4px rgba(0,0,0,0.3);
  }

  .toggle.on::after { left: 21px; }

  /* ── ACTIVITY ── */
  .activity-list { display: flex; flex-direction: column; gap: 0; }

  .activity-item {
    display: flex; align-items: flex-start; gap: 12px;
    padding: 12px 0;
    border-bottom: 1px solid var(--border);
  }

  .activity-item:last-child { border-bottom: none; }

  .activity-dot {
    width: 8px; height: 8px; border-radius: 50%;
    margin-top: 5px; flex-shrink: 0;
  }

  .activity-text { font-size: 13px; line-height: 1.5; }
  .activity-text strong { color: #93c5fd; }
  .activity-time { font-size: 11px; color: var(--text-muted); margin-top: 2px; }

  /* ── COMMAND TABLE ── */
  .cmd-table { width: 100%; border-collapse: collapse; }
  .cmd-table th {
    text-align: left; font-size: 11px; font-weight: 700;
    color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.8px;
    padding: 0 14px 10px; border-bottom: 1px solid var(--border);
  }

  .cmd-table td {
    padding: 11px 14px;
    font-size: 13px;
    border-bottom: 1px solid rgba(26,45,79,0.5);
  }

  .cmd-table tr:last-child td { border-bottom: none; }
  .cmd-table tr:hover td { background: var(--bg-hover); }

  .cmd-name { font-family: monospace; color: #93c5fd; font-weight: 700; font-size: 13px; }

  .tag {
    display: inline-block;
    padding: 2px 8px; border-radius: 6px;
    font-size: 11px; font-weight: 700;
  }

  .tag-blue { background: rgba(26,86,219,0.2); color: #60a5fa; }
  .tag-green { background: rgba(34,197,94,0.15); color: #4ade80; }
  .tag-red { background: rgba(239,68,68,0.15); color: #f87171; }
  .tag-purple { background: rgba(139,92,246,0.15); color: #a78bfa; }
  .tag-yellow { background: rgba(245,158,11,0.15); color: #fbbf24; }

  /* ── BOT STATUS ── */
  .status-row {
    display: flex; align-items: center; gap: 8px;
    padding: 10px 0; border-bottom: 1px solid var(--border);
  }
  .status-row:last-child { border-bottom: none; padding-bottom: 0; }
  .status-label { font-size: 12px; color: var(--text-muted); font-weight: 600; width: 110px; flex-shrink: 0; }
  .status-value { font-size: 13px; font-weight: 700; }
  .status-dot { width: 8px; height: 8px; border-radius: 50%; background: var(--green); box-shadow: 0 0 6px var(--green); }

  /* ── SEARCH BAR ── */
  .search-bar {
    display: flex; align-items: center; gap: 8px;
    background: var(--bg-primary);
    border: 1px solid var(--border);
    border-radius: 8px; padding: 8px 12px;
  }

  .search-bar input {
    background: none; border: none; outline: none;
    color: var(--text-primary); font-size: 13px; width: 100%;
    font-family: 'Nunito', sans-serif;
  }

  .search-bar input::placeholder { color: var(--text-muted); }

  /* ── MINI BAR CHART ── */
  .bar-chart { display: flex; align-items: flex-end; gap: 4px; height: 60px; padding-top: 8px; }
  .bar {
    flex: 1; border-radius: 4px 4px 0 0;
    background: var(--accent);
    opacity: 0.7;
    transition: opacity 0.2s;
    min-height: 4px;
  }
  .bar:hover { opacity: 1; }
  .bar-labels { display: flex; gap: 4px; margin-top: 4px; }
  .bar-label { flex: 1; font-size: 9px; color: var(--text-muted); text-align: center; }

  /* ── WELCOME BANNER ── */
  .welcome-banner {
    background: linear-gradient(135deg, #0e1d36, #1a2d4f);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 22px 26px;
    margin-bottom: 24px;
    display: flex; align-items: center; justify-content: space-between;
    overflow: hidden; position: relative;
  }

  .welcome-banner::after {
    content: '';
    position: absolute; right: -30px; top: -30px;
    width: 160px; height: 160px;
    background: radial-gradient(circle, rgba(26,86,219,0.25), transparent 70%);
    border-radius: 50%;
    pointer-events: none;
  }

  .welcome-title { font-size: 20px; font-weight: 800; margin-bottom: 4px; }
  .welcome-sub { font-size: 13px; color: var(--text-secondary); }

  .btn {
    padding: 9px 20px; border-radius: 8px; border: none;
    font-size: 13px; font-weight: 700; cursor: pointer;
    font-family: 'Nunito', sans-serif; transition: all 0.18s;
    display: inline-flex; align-items: center; gap: 7px;
  }

  .btn-primary { background: var(--accent); color: #fff; }
  .btn-primary:hover { background: var(--accent-light); box-shadow: 0 4px 14px rgba(26,86,219,0.4); }

  .btn-ghost {
    background: transparent;
    border: 1px solid var(--border);
    color: var(--text-secondary);
  }

  .btn-ghost:hover { background: var(--bg-hover); color: var(--text-primary); }

  /* ── TOKEN DISPLAY ── */
  .token-box {
    background: var(--bg-primary);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 10px 14px;
    font-family: monospace;
    font-size: 12px;
    color: var(--text-muted);
    word-break: break-all;
    display: flex; align-items: center; gap: 10px;
  }

  .token-text { flex: 1; }
  .token-copy {
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 4px 10px;
    font-size: 11px; font-weight: 700;
    color: var(--text-secondary);
    cursor: pointer; flex-shrink: 0;
    transition: background 0.15s;
    font-family: 'Nunito', sans-serif;
  }
  .token-copy:hover { background: var(--bg-hover); color: var(--text-primary); }

  /* scrollbar */
  ::-webkit-scrollbar { width: 5px; }
  ::-webkit-scrollbar-track { background: transparent; }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 4px; }
</style>
</head>
<body>

<!-- SIDEBAR -->
<aside class="sidebar">
  <div class="sidebar-logo">
    <div class="bot-avatar">A</div>
    <span class="bot-name">ahh</span>
  </div>

  <div class="sidebar-section">
    <div class="sidebar-section-label">General</div>
    <a class="nav-item active" href="#">
      <i class="fas fa-th-large"></i> Dashboard
    </a>
    <a class="nav-item" href="#">
      <i class="fas fa-chart-bar"></i> Analytics
    </a>
    <a class="nav-item" href="#">
      <i class="fas fa-server"></i> Servers
    </a>
  </div>

  <div class="sidebar-section">
    <div class="sidebar-section-label">Moderation</div>
    <a class="nav-item" href="#">
      <i class="fas fa-shield-alt"></i> Auto Mod
    </a>
    <a class="nav-item" href="#">
      <i class="fas fa-gavel"></i> Infractions
      <span class="nav-badge">3</span>
    </a>
    <a class="nav-item" href="#">
      <i class="fas fa-ban"></i> Bans &amp; Kicks
    </a>
    <a class="nav-item" href="#">
      <i class="fas fa-eye"></i> Logs
    </a>
  </div>

  <div class="sidebar-section">
    <div class="sidebar-section-label">Features</div>
    <a class="nav-item" href="#">
      <i class="fas fa-star"></i> Leveling
    </a>
    <a class="nav-item" href="#">
      <i class="fas fa-music"></i> Music
    </a>
    <a class="nav-item" href="#">
      <i class="fas fa-ticket-alt"></i> Tickets
    </a>
    <a class="nav-item" href="#">
      <i class="fas fa-tag"></i> Auto Roles
    </a>
    <a class="nav-item" href="#">
      <i class="fas fa-smile"></i> Reaction Roles
    </a>
    <a class="nav-item" href="#">
      <i class="fas fa-robot"></i> Commands
    </a>
  </div>

  <div class="sidebar-section">
    <div class="sidebar-section-label">Settings</div>
    <a class="nav-item" href="#">
      <i class="fas fa-cog"></i> Bot Settings
    </a>
    <a class="nav-item" href="#">
      <i class="fas fa-key"></i> Token &amp; API
    </a>
    <a class="nav-item" href="#">
      <i class="fas fa-users"></i> Permissions
    </a>
  </div>

  <div class="sidebar-server">
    <div class="server-card">
      <div class="server-icon">S</div>
      <div class="server-info">
        <div class="server-name">My Server</div>
        <div class="server-status">● Online</div>
      </div>
      <i class="fas fa-chevron-down" style="color:var(--text-muted);font-size:11px;"></i>
    </div>
  </div>
</aside>

<!-- MAIN -->
<div class="main">
  <!-- TOPBAR -->
  <header class="topbar">
    <div class="topbar-title">Dashboard Overview</div>
    <div class="topbar-right">
      <div class="topbar-btn"><i class="fas fa-search"></i></div>
      <div class="topbar-btn">
        <i class="fas fa-bell"></i>
        <span class="notif-dot"></span>
      </div>
      <div class="user-pill">
        <div class="user-avatar">A</div>
        <span>ahh#0001</span>
      </div>
    </div>
  </header>

  <!-- CONTENT -->
  <div class="content">

    <!-- Welcome Banner -->
    <div class="welcome-banner">
      <div>
        <div class="welcome-title">Welcome back to <span style="background:linear-gradient(90deg,#60a5fa,#a78bfa);-webkit-background-clip:text;-webkit-text-fill-color:transparent">ahh</span> 👋</div>
        <div class="welcome-sub">Your bot is online and running smoothly across all servers.</div>
      </div>
      <div style="display:flex;gap:10px;position:relative;z-index:1;">
        <button class="btn btn-ghost"><i class="fas fa-external-link-alt"></i> Invite Bot</button>
        <button class="btn btn-primary"><i class="fas fa-plus"></i> Add Server</button>
      </div>
    </div>

    <!-- Stats -->
    <div class="stats-grid">
      <div class="stat-card" style="--card-accent:#1a56db;">
        <div class="stat-icon" style="--icon-bg:rgba(26,86,219,0.15);--icon-color:#60a5fa;">
          <i class="fas fa-server"></i>
        </div>
        <div>
          <div class="stat-label">Total Servers</div>
          <div class="stat-value">1,248</div>
          <div class="stat-change">▲ 14 this week</div>
        </div>
      </div>
      <div class="stat-card" style="--card-accent:#22c55e;">
        <div class="stat-icon" style="--icon-bg:rgba(34,197,94,0.12);--icon-color:#4ade80;">
          <i class="fas fa-users"></i>
        </div>
        <div>
          <div class="stat-label">Total Members</div>
          <div class="stat-value">84,302</div>
          <div class="stat-change">▲ 632 this week</div>
        </div>
      </div>
      <div class="stat-card" style="--card-accent:#8b5cf6;">
        <div class="stat-icon" style="--icon-bg:rgba(139,92,246,0.12);--icon-color:#a78bfa;">
          <i class="fas fa-terminal"></i>
        </div>
        <div>
          <div class="stat-label">Commands Used</div>
          <div class="stat-value">23,891</div>
          <div class="stat-change">▲ 1.2k today</div>
        </div>
      </div>
      <div class="stat-card" style="--card-accent:#f59e0b;">
        <div class="stat-icon" style="--icon-bg:rgba(245,158,11,0.12);--icon-color:#fbbf24;">
          <i class="fas fa-bolt"></i>
        </div>
        <div>
          <div class="stat-label">Uptime</div>
          <div class="stat-value">99.8%</div>
          <div class="stat-change" style="color:var(--green);">● All systems go</div>
        </div>
      </div>
    </div>

    <!-- Row: Modules + Activity -->
    <div class="grid-3">

      <!-- Modules -->
      <div class="card">
        <div class="card-header">
          <div>
            <div class="card-title">Modules</div>
            <div class="card-subtitle">Toggle features for your server</div>
          </div>
          <button class="btn btn-ghost" style="padding:6px 12px;font-size:12px;">
            <i class="fas fa-cog"></i> Configure
          </button>
        </div>
        <div class="module-list">
          <div class="module-item">
            <div class="module-left">
              <div class="module-icon" style="background:rgba(26,86,219,0.15);color:#60a5fa"><i class="fas fa-shield-alt"></i></div>
              <div>
                <div class="module-name">Auto Moderation</div>
                <div class="module-desc">Filters spam, links, and bad words</div>
              </div>
            </div>
            <div class="toggle on" onclick="this.classList.toggle('on')"></div>
          </div>
          <div class="module-item">
            <div class="module-left">
              <div class="module-icon" style="background:rgba(34,197,94,0.12);color:#4ade80"><i class="fas fa-star"></i></div>
              <div>
                <div class="module-name">Leveling System</div>
                <div class="module-desc">XP rewards for activity</div>
              </div>
            </div>
            <div class="toggle on" onclick="this.classList.toggle('on')"></div>
          </div>
          <div class="module-item">
            <div class="module-left">
              <div class="module-icon" style="background:rgba(139,92,246,0.12);color:#a78bfa"><i class="fas fa-music"></i></div>
              <div>
                <div class="module-name">Music Player</div>
                <div class="module-desc">Play music in voice channels</div>
              </div>
            </div>
            <div class="toggle" onclick="this.classList.toggle('on')"></div>
          </div>
          <div class="module-item">
            <div class="module-left">
              <div class="module-icon" style="background:rgba(245,158,11,0.12);color:#fbbf24"><i class="fas fa-ticket-alt"></i></div>
              <div>
                <div class="module-name">Ticket System</div>
                <div class="module-desc">Support ticket channels</div>
              </div>
            </div>
            <div class="toggle on" onclick="this.classList.toggle('on')"></div>
          </div>
          <div class="module-item">
            <div class="module-left">
              <div class="module-icon" style="background:rgba(239,68,68,0.12);color:#f87171"><i class="fas fa-door-open"></i></div>
              <div>
                <div class="module-name">Welcome Messages</div>
                <div class="module-desc">Greet new members</div>
              </div>
            </div>
            <div class="toggle on" onclick="this.classList.toggle('on')"></div>
          </div>
          <div class="module-item">
            <div class="module-left">
              <div class="module-icon" style="background:rgba(26,86,219,0.12);color:#60a5fa"><i class="fas fa-smile"></i></div>
              <div>
                <div class="module-name">Reaction Roles</div>
                <div class="module-desc">Self-assign roles via reactions</div>
              </div>
            </div>
            <div class="toggle" onclick="this.classList.toggle('on')"></div>
          </div>
        </div>
      </div>

      <!-- Activity + Bot Status -->
      <div style="display:flex;flex-direction:column;gap:20px;">

        <!-- Bot Status -->
        <div class="card">
          <div class="card-header">
            <div class="card-title">Bot Status</div>
            <span class="tag tag-green">● Online</span>
          </div>
          <div class="card-body" style="padding-top:14px;padding-bottom:14px;">
            <div class="status-row">
              <div class="status-label">Bot Name</div>
              <div class="status-value">ahh</div>
            </div>
            <div class="status-row">
              <div class="status-label">Status</div>
              <div style="display:flex;align-items:center;gap:6px">
                <div class="status-dot"></div>
                <span class="status-value" style="color:var(--green)">Online</span>
              </div>
            </div>
            <div class="status-row">
              <div class="status-label">Ping</div>
              <div class="status-value">42 ms</div>
            </div>
            <div class="status-row">
              <div class="status-label">Library</div>
              <div class="status-value">discord.js v14</div>
            </div>
            <div class="status-row">
              <div class="status-label">Uptime</div>
              <div class="status-value">14d 6h 22m</div>
            </div>
          </div>
        </div>

        <!-- Command Usage Chart -->
        <div class="card">
          <div class="card-header">
            <div class="card-title">Commands (7d)</div>
          </div>
          <div class="card-body">
            <div class="bar-chart">
              <div class="bar" style="height:35%"></div>
              <div class="bar" style="height:55%"></div>
              <div class="bar" style="height:45%"></div>
              <div class="bar" style="height:80%"></div>
              <div class="bar" style="height:60%"></div>
              <div class="bar" style="height:90%"></div>
              <div class="bar" style="height:70%"></div>
            </div>
            <div class="bar-labels">
              <div class="bar-label">Mon</div>
              <div class="bar-label">Tue</div>
              <div class="bar-label">Wed</div>
              <div class="bar-label">Thu</div>
              <div class="bar-label">Fri</div>
              <div class="bar-label">Sat</div>
              <div class="bar-label">Sun</div>
            </div>
          </div>
        </div>

      </div>
    </div>

    <!-- Row: Commands + Recent Activity -->
    <div class="grid-2">

      <!-- Commands -->
      <div class="card">
        <div class="card-header">
          <div>
            <div class="card-title">Commands</div>
            <div class="card-subtitle">Most used slash commands</div>
          </div>
          <div class="search-bar" style="width:160px;">
            <i class="fas fa-search" style="color:var(--text-muted);font-size:12px;"></i>
            <input type="text" placeholder="Search...">
          </div>
        </div>
        <div style="padding:10px 6px;">
          <table class="cmd-table">
            <thead>
              <tr>
                <th>Command</th>
                <th>Category</th>
                <th>Uses</th>
                <th>Status</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td><span class="cmd-name">/ban</span></td>
                <td><span class="tag tag-red">Moderation</span></td>
                <td>2,341</td>
                <td><span class="tag tag-green">Active</span></td>
              </tr>
              <tr>
                <td><span class="cmd-name">/play</span></td>
                <td><span class="tag tag-purple">Music</span></td>
                <td>1,872</td>
                <td><span class="tag tag-green">Active</span></td>
              </tr>
              <tr>
                <td><span class="cmd-name">/rank</span></td>
                <td><span class="tag tag-blue">Leveling</span></td>
                <td>1,654</td>
                <td><span class="tag tag-green">Active</span></td>
              </tr>
              <tr>
                <td><span class="cmd-name">/ticket</span></td>
                <td><span class="tag tag-yellow">Support</span></td>
                <td>982</td>
                <td><span class="tag tag-green">Active</span></td>
              </tr>
              <tr>
                <td><span class="cmd-name">/kick</span></td>
                <td><span class="tag tag-red">Moderation</span></td>
                <td>741</td>
                <td><span class="tag tag-green">Active</span></td>
              </tr>
              <tr>
                <td><span class="cmd-name">/mute</span></td>
                <td><span class="tag tag-red">Moderation</span></td>
                <td>614</td>
                <td><span class="tag tag-green">Active</span></td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>

      <!-- Recent Activity -->
      <div class="card">
        <div class="card-header">
          <div class="card-title">Recent Activity</div>
          <button class="btn btn-ghost" style="padding:5px 12px;font-size:12px;">View All</button>
        </div>
        <div class="card-body">
          <div class="activity-list">
            <div class="activity-item">
              <div class="activity-dot" style="background:var(--red)"></div>
              <div>
                <div class="activity-text"><strong>User#1234</strong> was banned in <strong>My Server</strong></div>
                <div class="activity-time">2 minutes ago</div>
              </div>
            </div>
            <div class="activity-item">
              <div class="activity-dot" style="background:var(--green)"></div>
              <div>
                <div class="activity-text"><strong>NewUser#5678</strong> joined <strong>My Server</strong></div>
                <div class="activity-time">8 minutes ago</div>
              </div>
            </div>
            <div class="activity-item">
              <div class="activity-dot" style="background:var(--accent-glow)"></div>
              <div>
                <div class="activity-text"><strong>Mod#9012</strong> used <strong>/mute</strong> on someone</div>
                <div class="activity-time">15 minutes ago</div>
              </div>
            </div>
            <div class="activity-item">
              <div class="activity-dot" style="background:var(--yellow)"></div>
              <div>
                <div class="activity-text"><strong>Ticket #48</strong> was opened by <strong>User#3456</strong></div>
                <div class="activity-time">31 minutes ago</div>
              </div>
            </div>
            <div class="activity-item">
              <div class="activity-dot" style="background:var(--purple)"></div>
              <div>
                <div class="activity-text"><strong>User#7890</strong> reached <strong>Level 15</strong> 🎉</div>
                <div class="activity-time">1 hour ago</div>
              </div>
            </div>
            <div class="activity-item">
              <div class="activity-dot" style="background:var(--green)"></div>
              <div>
                <div class="activity-text">Auto-mod deleted a message with a <strong>blacklisted link</strong></div>
                <div class="activity-time">2 hours ago</div>
              </div>
            </div>
          </div>
        </div>
      </div>

    </div>

    <!-- Token Section -->
    <div class="card">
      <div class="card-header">
        <div>
          <div class="card-title"><i class="fas fa-key" style="color:var(--yellow);margin-right:7px;"></i>Bot Token</div>
          <div class="card-subtitle">Keep this secret — never share it publicly</div>
        </div>
        <button class="btn btn-ghost" style="padding:6px 14px;font-size:12px;color:var(--red);border-color:rgba(239,68,68,0.3);">
          <i class="fas fa-sync-alt"></i> Regenerate
        </button>
      </div>
      <div class="card-body">
        <div class="token-box">
          <span class="token-text" id="tokenText">••••••••••••••••••••••••••••••••••••••••••••</span>
          <button class="token-copy" onclick="toggleToken()">Reveal</button>
          <button class="token-copy" onclick="copyToken()">Copy</button>
        </div>
        <p style="font-size:11px;color:var(--text-muted);margin-top:10px;">
          <i class="fas fa-exclamation-triangle" style="color:var(--yellow);margin-right:4px;"></i>
          Your token grants full access to your bot. Reset it immediately if compromised.
        </p>
      </div>
    </div>

  </div>
</div>

<script>
  const realToken = "MTQ4MzUwMDg1ODM0NzA5NDIwNw.GjLBE7.arIiw2B9S6NYNZ52XOR02G55EZAHKf09KSK2bM";
  let revealed = false;

  function toggleToken() {
    revealed = !revealed;
    const el = document.getElementById('tokenText');
    el.textContent = revealed ? realToken : '••••••••••••••••••••••••••••••••••••••••••••';
    event.target.textContent = revealed ? 'Hide' : 'Reveal';
  }

  function copyToken() {
    navigator.clipboard.writeText(realToken).then(() => {
      const btn = event.target;
      btn.textContent = 'Copied!';
      btn.style.color = 'var(--green)';
      setTimeout(() => { btn.textContent = 'Copy'; btn.style.color = ''; }, 2000);
    });
  }
</script>

</body>
</html>
