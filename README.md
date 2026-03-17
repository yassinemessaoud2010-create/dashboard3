[dashboard-1.html](https://github.com/user-attachments/files/26068048/dashboard-1.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ahh</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
<style>
*{margin:0;padding:0;box-sizing:border-box;}
:root{
  --bg:#03080f;--bg2:#060e1c;--bg3:#0b1628;--bg4:#0f1e35;
  --card:#0d1a2e;--border:#132038;
  --accent:#1447d4;--accent2:#1c5aff;
  --txt:#d4e0f5;--txt2:#5a7aaa;--txt3:#2d4870;
  --green:#00e87a;--red:#ff3b5c;--yellow:#ffb800;--purple:#7c6bff;
  --sidebar:220px;
}
body{font-family:'Syne',sans-serif;background:var(--bg);color:var(--txt);display:flex;min-height:100vh;overflow-x:hidden;}
::-webkit-scrollbar{width:4px;}
::-webkit-scrollbar-track{background:transparent;}
::-webkit-scrollbar-thumb{background:var(--border);border-radius:4px;}
body::before{content:'';position:fixed;inset:0;background-image:repeating-linear-gradient(0deg,transparent,transparent 40px,rgba(255,255,255,0.012) 40px,rgba(255,255,255,0.012) 41px),repeating-linear-gradient(90deg,transparent,transparent 40px,rgba(255,255,255,0.012) 40px,rgba(255,255,255,0.012) 41px);pointer-events:none;z-index:0;}

/* SIDEBAR */
.sidebar{width:var(--sidebar);background:var(--bg2);border-right:1px solid var(--border);display:flex;flex-direction:column;position:fixed;top:0;left:0;height:100vh;z-index:100;overflow-y:auto;}
.logo{display:flex;align-items:center;gap:10px;padding:22px 16px 18px;border-bottom:1px solid var(--border);}
.logo-dot{width:32px;height:32px;background:var(--accent2);border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:15px;font-weight:800;color:#fff;box-shadow:0 0 18px rgba(28,90,255,0.4);flex-shrink:0;}
.logo-name{font-size:20px;font-weight:800;letter-spacing:-0.5px;color:#fff;}
.nav-section{padding:16px 8px 4px;}
.nav-label{font-size:9px;font-weight:700;color:var(--txt3);text-transform:uppercase;letter-spacing:1.5px;padding:0 8px 10px;}
.nav-item{display:flex;align-items:center;gap:9px;padding:8px 10px;border-radius:7px;cursor:pointer;color:var(--txt2);font-size:13px;font-weight:600;transition:all 0.15s;margin-bottom:1px;position:relative;user-select:none;}
.nav-item:hover{background:var(--bg4);color:var(--txt);}
.nav-item.active{background:rgba(28,90,255,0.12);color:var(--accent2);}
.nav-item.active::before{content:'';position:absolute;left:0;top:20%;bottom:20%;width:2px;background:var(--accent2);border-radius:2px;box-shadow:0 0 8px var(--accent2);}
.nav-item i{width:16px;text-align:center;font-size:12px;flex-shrink:0;}
.nav-badge{margin-left:auto;background:var(--red);color:#fff;font-size:9px;font-weight:800;padding:1px 5px;border-radius:20px;}
.sidebar-bot{margin-top:auto;padding:12px;border-top:1px solid var(--border);}
.bot-pill{display:flex;align-items:center;gap:8px;background:var(--bg3);border:1px solid var(--border);border-radius:8px;padding:9px 10px;cursor:pointer;transition:background 0.15s;}
.bot-pill:hover{background:var(--bg4);}
.bot-pill-icon{width:28px;height:28px;background:var(--accent2);border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:800;color:#fff;flex-shrink:0;}
.bot-pill-name{font-size:12px;font-weight:700;flex:1;}
.bot-pill-status{font-size:10px;color:var(--green);font-weight:600;display:flex;align-items:center;gap:3px;}
.bp-dot{width:5px;height:5px;background:var(--green);border-radius:50%;box-shadow:0 0 5px var(--green);}

/* MAIN */
.main{margin-left:var(--sidebar);flex:1;display:flex;flex-direction:column;min-height:100vh;position:relative;z-index:1;}

/* TOPBAR */
.topbar{background:var(--bg2);border-bottom:1px solid var(--border);padding:0 26px;height:56px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:50;backdrop-filter:blur(12px);}
.topbar-left{display:flex;align-items:center;gap:10px;}
.page-title{font-size:15px;font-weight:700;color:#fff;}
.page-crumb{font-size:12px;color:var(--txt3);font-weight:500;}
.topbar-sep{color:var(--txt3);font-size:12px;}
.topbar-right{display:flex;align-items:center;gap:10px;}
.tb-btn{width:34px;height:34px;background:var(--bg3);border:1px solid var(--border);border-radius:7px;display:flex;align-items:center;justify-content:center;cursor:pointer;color:var(--txt2);font-size:13px;transition:all 0.15s;position:relative;}
.tb-btn:hover{background:var(--bg4);color:var(--txt);}
.notif-dot{position:absolute;top:7px;right:7px;width:6px;height:6px;background:var(--red);border-radius:50%;border:1.5px solid var(--bg2);}
.status-pill{display:flex;align-items:center;gap:6px;background:rgba(0,232,122,0.07);border:1px solid rgba(0,232,122,0.15);border-radius:20px;padding:5px 12px;}
.status-pill-dot{width:6px;height:6px;background:var(--green);border-radius:50%;box-shadow:0 0 6px var(--green);animation:pulse 2s infinite;}
@keyframes pulse{0%,100%{opacity:1;}50%{opacity:0.5;}}
.status-pill span{font-size:11px;font-weight:700;color:var(--green);}

/* PAGES */
.page{display:none;padding:24px 26px;animation:fadeIn 0.2s ease;}
.page.active{display:block;}
@keyframes fadeIn{from{opacity:0;transform:translateY(4px);}to{opacity:1;transform:translateY(0);}}

/* STATS */
.stats-row{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-bottom:20px;}
.stat{background:var(--card);border:1px solid var(--border);border-radius:12px;padding:18px;display:flex;flex-direction:column;gap:10px;position:relative;overflow:hidden;transition:transform 0.15s,box-shadow 0.15s;}
.stat:hover{transform:translateY(-2px);box-shadow:0 8px 28px rgba(0,0,0,0.4);}
.stat-top{display:flex;align-items:center;justify-content:space-between;}
.stat-icon{width:36px;height:36px;border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:15px;}
.stat-change{font-size:10px;font-weight:700;padding:2px 7px;border-radius:20px;}
.stat-up{background:rgba(0,232,122,0.1);color:var(--green);}
.stat-val{font-size:26px;font-weight:800;color:#fff;letter-spacing:-0.5px;}
.stat-lbl{font-size:11px;color:var(--txt2);font-weight:600;margin-top:1px;}
.stat-bar{height:2px;background:var(--border);border-radius:2px;margin-top:4px;}
.stat-bar-fill{height:100%;border-radius:2px;background:var(--accent2);}

/* CARDS */
.card{background:var(--card);border:1px solid var(--border);border-radius:12px;overflow:hidden;margin-bottom:20px;}
.card-head{padding:16px 20px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;}
.card-title{font-size:13px;font-weight:700;color:#fff;}
.card-sub{font-size:11px;color:var(--txt2);margin-top:2px;}
.card-body{padding:18px 20px;}

/* GRIDS */
.g2{display:grid;grid-template-columns:1fr 1fr;gap:18px;}
.g3{display:grid;grid-template-columns:1.6fr 1fr;gap:18px;}

/* TOGGLE */
.toggle{width:36px;height:20px;background:var(--txt3);border-radius:10px;position:relative;cursor:pointer;transition:background 0.2s;flex-shrink:0;}
.toggle.on{background:var(--accent2);box-shadow:0 0 10px rgba(28,90,255,0.35);}
.toggle::after{content:'';position:absolute;width:14px;height:14px;background:#fff;border-radius:50%;top:3px;left:3px;transition:left 0.2s;box-shadow:0 1px 3px rgba(0,0,0,0.4);}
.toggle.on::after{left:19px;}

/* MODULE ITEMS */
.mod-item{display:flex;align-items:center;justify-content:space-between;padding:12px 20px;transition:background 0.13s;cursor:pointer;}
.mod-item:hover{background:var(--bg4);}
.mod-left{display:flex;align-items:center;gap:12px;}
.mod-icon{width:32px;height:32px;border-radius:7px;display:flex;align-items:center;justify-content:center;font-size:13px;}
.mod-name{font-size:13px;font-weight:700;}
.mod-desc{font-size:11px;color:var(--txt2);margin-top:1px;}

/* TAGS */
.tag{display:inline-block;padding:2px 8px;border-radius:5px;font-size:10px;font-weight:700;}
.tag-blue{background:rgba(28,90,255,0.15);color:#6fa3ff;}
.tag-green{background:rgba(0,232,122,0.1);color:var(--green);}
.tag-red{background:rgba(255,59,92,0.12);color:#ff6b83;}
.tag-purple{background:rgba(124,107,255,0.12);color:#a99aff;}
.tag-yellow{background:rgba(255,184,0,0.1);color:var(--yellow);}
.tag-gray{background:rgba(90,122,170,0.12);color:var(--txt2);}

/* ACTIVITY */
.act-item{display:flex;align-items:flex-start;gap:11px;padding:11px 0;border-bottom:1px solid rgba(19,32,56,0.8);}
.act-item:last-child{border-bottom:none;padding-bottom:0;}
.act-dot{width:7px;height:7px;border-radius:50%;margin-top:5px;flex-shrink:0;}
.act-text{font-size:12px;line-height:1.5;color:var(--txt2);}
.act-text b{color:var(--txt);}
.act-time{font-size:10px;color:var(--txt3);margin-top:2px;}

/* TABLE */
.tbl{width:100%;border-collapse:collapse;}
.tbl th{text-align:left;font-size:10px;font-weight:700;color:var(--txt3);text-transform:uppercase;letter-spacing:1px;padding:0 12px 10px;border-bottom:1px solid var(--border);}
.tbl td{padding:10px 12px;font-size:12px;border-bottom:1px solid rgba(19,32,56,0.5);transition:background 0.12s;}
.tbl tr:last-child td{border-bottom:none;}
.tbl tr:hover td{background:var(--bg4);}
.mono{font-family:'DM Mono',monospace;color:#7ab0ff;font-size:12px;}

/* BUTTONS */
.btn{padding:8px 16px;border-radius:7px;border:none;font-size:12px;font-weight:700;cursor:pointer;font-family:'Syne',sans-serif;transition:all 0.15s;display:inline-flex;align-items:center;gap:6px;}
.btn-primary{background:var(--accent2);color:#fff;}
.btn-primary:hover{background:#1a50e8;box-shadow:0 4px 16px rgba(28,90,255,0.35);}
.btn-ghost{background:transparent;border:1px solid var(--border);color:var(--txt2);}
.btn-ghost:hover{background:var(--bg4);color:var(--txt);}
.btn-danger{background:rgba(255,59,92,0.1);border:1px solid rgba(255,59,92,0.2);color:var(--red);}
.btn-danger:hover{background:rgba(255,59,92,0.18);}

/* STATUS ROWS */
.sr{display:flex;align-items:center;gap:8px;padding:9px 0;border-bottom:1px solid var(--border);}
.sr:last-child{border-bottom:none;padding-bottom:0;}
.sr-label{font-size:11px;color:var(--txt2);font-weight:600;width:120px;flex-shrink:0;}
.sr-val{font-size:12px;font-weight:700;}

/* INPUTS */
.inp{background:var(--bg3);border:1px solid var(--border);border-radius:7px;padding:9px 12px;color:var(--txt);font-size:12px;font-family:'Syne',sans-serif;outline:none;width:100%;transition:border 0.15s;}
.inp:focus{border-color:var(--accent2);}
.inp::placeholder{color:var(--txt3);}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px;}
.form-label{font-size:11px;font-weight:700;color:var(--txt2);margin-bottom:5px;display:block;}
textarea.inp{resize:vertical;min-height:80px;}
select.inp{cursor:pointer;}

/* TOKEN */
.token-wrap{background:var(--bg3);border:1px solid var(--border);border-radius:8px;padding:10px 14px;display:flex;align-items:center;gap:10px;}
.token-val{font-family:'DM Mono',monospace;font-size:11px;color:var(--txt2);flex:1;word-break:break-all;}
.token-btn{background:var(--bg4);border:1px solid var(--border);border-radius:6px;padding:4px 10px;font-size:10px;font-weight:700;color:var(--txt2);cursor:pointer;flex-shrink:0;font-family:'Syne',sans-serif;transition:all 0.15s;white-space:nowrap;}
.token-btn:hover{background:var(--border);color:var(--txt);}

/* BANNER */
.banner{background:linear-gradient(120deg,#080f22,#0d1a35);border:1px solid var(--border);border-radius:12px;padding:22px 24px;margin-bottom:20px;display:flex;align-items:center;justify-content:space-between;overflow:hidden;position:relative;}
.banner::after{content:'';position:absolute;right:-40px;top:-40px;width:180px;height:180px;background:radial-gradient(circle,rgba(28,90,255,0.15),transparent 65%);pointer-events:none;}
.banner-title{font-size:18px;font-weight:800;color:#fff;margin-bottom:4px;}
.banner-sub{font-size:12px;color:var(--txt2);}

/* SERVER ITEMS */
.server-item{display:flex;align-items:center;gap:12px;padding:12px 20px;transition:background 0.13s;cursor:pointer;}
.server-item:hover{background:var(--bg4);}
.server-icon{width:36px;height:36px;border-radius:8px;background:var(--accent);display:flex;align-items:center;justify-content:center;font-size:14px;font-weight:800;color:#fff;flex-shrink:0;}

/* LOG */
.log-item{display:flex;gap:12px;padding:10px 20px;border-bottom:1px solid rgba(19,32,56,0.5);font-size:12px;}
.log-item:last-child{border-bottom:none;}
.log-time{font-family:'DM Mono',monospace;font-size:10px;color:var(--txt3);width:70px;flex-shrink:0;margin-top:2px;}
.log-type{width:72px;flex-shrink:0;}
.log-msg{color:var(--txt2);flex:1;}
.log-msg b{color:var(--txt);}

/* CHART */
.bar-wrap{display:flex;align-items:flex-end;gap:3px;height:50px;}
.bar{flex:1;border-radius:3px 3px 0 0;background:var(--accent2);opacity:0.5;transition:opacity 0.15s;min-height:4px;}
.bar:hover{opacity:1;}
.bar-labels{display:flex;gap:3px;margin-top:3px;}
.bar-lbl{flex:1;font-size:9px;color:var(--txt3);text-align:center;}

/* SECTION HEADER */
.section-hd{display:flex;align-items:center;justify-content:space-between;margin-bottom:16px;}
.section-hd h2{font-size:16px;font-weight:800;color:#fff;}
.section-hd p{font-size:11px;color:var(--txt2);margin-top:2px;}

/* TOAST */
.toast{position:fixed;bottom:20px;right:20px;background:var(--bg3);border:1px solid var(--border);border-radius:10px;padding:12px 16px;font-size:12px;font-weight:600;display:flex;align-items:center;gap:8px;z-index:999;box-shadow:0 8px 30px rgba(0,0,0,0.5);transform:translateY(80px);opacity:0;transition:all 0.3s cubic-bezier(.34,1.56,.64,1);}
.toast.show{transform:translateY(0);opacity:1;}

/* LOADER */
.loader{display:flex;align-items:center;justify-content:center;padding:30px;gap:6px;}
.loader-dot{width:6px;height:6px;background:var(--accent2);border-radius:50%;animation:bounce 1.2s infinite;}
.loader-dot:nth-child(2){animation-delay:0.2s;}
.loader-dot:nth-child(3){animation-delay:0.4s;}
@keyframes bounce{0%,80%,100%{transform:scale(0.6);opacity:0.4;}40%{transform:scale(1);opacity:1;}}
</style>
</head>
<body>

<!-- SIDEBAR -->
<aside class="sidebar">
  <div class="logo">
    <div class="logo-dot">a</div>
    <span class="logo-name">ahh</span>
  </div>

  <div class="nav-section">
    <div class="nav-label">Overview</div>
    <div class="nav-item active" data-page="dashboard"><i class="fas fa-grip-vertical"></i> Dashboard</div>
    <div class="nav-item" data-page="analytics"><i class="fas fa-chart-line"></i> Analytics</div>
    <div class="nav-item" data-page="servers"><i class="fas fa-server"></i> Servers</div>
  </div>

  <div class="nav-section">
    <div class="nav-label">Moderation</div>
    <div class="nav-item" data-page="automod"><i class="fas fa-shield-halved"></i> Auto Mod</div>
    <div class="nav-item" data-page="infractions"><i class="fas fa-gavel"></i> Infractions <span class="nav-badge" id="infBadge">0</span></div>
    <div class="nav-item" data-page="logs"><i class="fas fa-scroll"></i> Logs</div>
  </div>

  <div class="nav-section">
    <div class="nav-label">Features</div>
    <div class="nav-item" data-page="leveling"><i class="fas fa-star"></i> Leveling</div>
    <div class="nav-item" data-page="music"><i class="fas fa-music"></i> Music</div>
    <div class="nav-item" data-page="tickets"><i class="fas fa-ticket"></i> Tickets</div>
    <div class="nav-item" data-page="welcome"><i class="fas fa-door-open"></i> Welcome</div>
    <div class="nav-item" data-page="commands"><i class="fas fa-terminal"></i> Commands</div>
  </div>

  <div class="nav-section">
    <div class="nav-label">Config</div>
    <div class="nav-item" data-page="settings"><i class="fas fa-sliders"></i> Settings</div>
    <div class="nav-item" data-page="token"><i class="fas fa-key"></i> Token &amp; API</div>
  </div>

  <div class="sidebar-bot">
    <div class="bot-pill">
      <div class="bot-pill-icon">a</div>
      <div>
        <div class="bot-pill-name">ahh</div>
        <div class="bot-pill-status"><span class="bp-dot"></span> online</div>
      </div>
    </div>
  </div>
</aside>

<!-- MAIN -->
<div class="main">
  <header class="topbar">
    <div class="topbar-left">
      <span class="page-crumb">ahh</span>
      <span class="topbar-sep">/</span>
      <span class="page-title" id="pageTitle">Dashboard</span>
    </div>
    <div class="topbar-right">
      <div class="status-pill"><span class="status-pill-dot"></span><span id="botPingLabel">— ms</span></div>
      <div class="tb-btn" onclick="fetchBotInfo()"><i class="fas fa-rotate-right"></i></div>
      <div class="tb-btn"><i class="fas fa-bell"></i><span class="notif-dot"></span></div>
    </div>
  </header>

  <!-- DASHBOARD -->
  <div class="page active" id="page-dashboard">
    <div class="banner">
      <div>
        <div class="banner-title">what's good — <span style="color:var(--accent2)">ahh</span></div>
        <div class="banner-sub" id="bannerSub">loading bot info...</div>
      </div>
      <div style="display:flex;gap:8px;position:relative;z-index:1;">
        <button class="btn btn-ghost" onclick="inviteBot()"><i class="fas fa-plus"></i> invite</button>
        <button class="btn btn-primary" onclick="fetchBotInfo()"><i class="fas fa-sync-alt"></i> refresh</button>
      </div>
    </div>
    <div class="stats-row">
      <div class="stat">
        <div class="stat-top"><div class="stat-icon" style="background:rgba(28,90,255,0.12);color:#6fa3ff"><i class="fas fa-server"></i></div><span class="stat-change stat-up" id="sc1">live</span></div>
        <div class="stat-val" id="sv1">—</div><div class="stat-lbl">servers</div>
        <div class="stat-bar"><div class="stat-bar-fill" style="width:60%"></div></div>
      </div>
      <div class="stat">
        <div class="stat-top"><div class="stat-icon" style="background:rgba(0,232,122,0.08);color:var(--green)"><i class="fas fa-users"></i></div><span class="stat-change stat-up" id="sc2">live</span></div>
        <div class="stat-val" id="sv2">—</div><div class="stat-lbl">users</div>
        <div class="stat-bar"><div class="stat-bar-fill" style="width:75%;background:var(--green)"></div></div>
      </div>
      <div class="stat">
        <div class="stat-top"><div class="stat-icon" style="background:rgba(124,107,255,0.1);color:var(--purple)"><i class="fas fa-bolt"></i></div><span class="stat-change stat-up" id="sc3">ms</span></div>
        <div class="stat-val" id="sv3">—</div><div class="stat-lbl">ping</div>
        <div class="stat-bar"><div class="stat-bar-fill" style="width:40%;background:var(--purple)"></div></div>
      </div>
      <div class="stat">
        <div class="stat-top"><div class="stat-icon" style="background:rgba(255,184,0,0.08);color:var(--yellow)"><i class="fas fa-circle-check"></i></div><span class="stat-change stat-up">live</span></div>
        <div class="stat-val" id="sv4">—</div><div class="stat-lbl">status</div>
        <div class="stat-bar"><div class="stat-bar-fill" style="width:90%;background:var(--yellow)"></div></div>
      </div>
    </div>
    <div class="g3">
      <div>
        <div class="card">
          <div class="card-head"><div><div class="card-title">modules</div><div class="card-sub">toggle features</div></div><button class="btn btn-ghost" style="font-size:11px;padding:5px 10px;" onclick="toast('Module settings saved','green')">save</button></div>
          <div class="mod-item"><div class="mod-left"><div class="mod-icon" style="background:rgba(28,90,255,0.12);color:#6fa3ff"><i class="fas fa-shield-halved"></i></div><div><div class="mod-name">Auto Moderation</div><div class="mod-desc">filters spam, links, slurs</div></div></div><div class="toggle on" onclick="this.classList.toggle('on')"></div></div>
          <div class="mod-item"><div class="mod-left"><div class="mod-icon" style="background:rgba(0,232,122,0.08);color:var(--green)"><i class="fas fa-star"></i></div><div><div class="mod-name">Leveling</div><div class="mod-desc">xp + rank cards</div></div></div><div class="toggle on" onclick="this.classList.toggle('on')"></div></div>
          <div class="mod-item"><div class="mod-left"><div class="mod-icon" style="background:rgba(124,107,255,0.1);color:var(--purple)"><i class="fas fa-music"></i></div><div><div class="mod-name">Music</div><div class="mod-desc">voice channel playback</div></div></div><div class="toggle" onclick="this.classList.toggle('on')"></div></div>
          <div class="mod-item"><div class="mod-left"><div class="mod-icon" style="background:rgba(255,184,0,0.08);color:var(--yellow)"><i class="fas fa-ticket"></i></div><div><div class="mod-name">Tickets</div><div class="mod-desc">support channel system</div></div></div><div class="toggle on" onclick="this.classList.toggle('on')"></div></div>
          <div class="mod-item"><div class="mod-left"><div class="mod-icon" style="background:rgba(255,59,92,0.08);color:var(--red)"><i class="fas fa-door-open"></i></div><div><div class="mod-name">Welcome</div><div class="mod-desc">greet new members</div></div></div><div class="toggle on" onclick="this.classList.toggle('on')"></div></div>
          <div class="mod-item"><div class="mod-left"><div class="mod-icon" style="background:rgba(28,90,255,0.1);color:#6fa3ff"><i class="fas fa-smile"></i></div><div><div class="mod-name">Reaction Roles</div><div class="mod-desc">self-assign via emoji</div></div></div><div class="toggle" onclick="this.classList.toggle('on')"></div></div>
        </div>
      </div>
      <div style="display:flex;flex-direction:column;gap:16px;">
        <div class="card">
          <div class="card-head"><div class="card-title">bot info</div><span class="tag tag-green">● live</span></div>
          <div class="card-body" style="padding-top:12px;padding-bottom:12px;">
            <div class="sr"><div class="sr-label">name</div><div class="sr-val" id="infoName">ahh</div></div>
            <div class="sr"><div class="sr-label">id</div><div class="sr-val"><span class="mono" id="infoId">—</span></div></div>
            <div class="sr"><div class="sr-label">tag</div><div class="sr-val" id="infoTag">—</div></div>
            <div class="sr"><div class="sr-label">verified</div><div class="sr-val" id="infoVerified">—</div></div>
          </div>
        </div>
        <div class="card">
          <div class="card-head"><div class="card-title">commands / 7d</div></div>
          <div class="card-body">
            <div class="bar-wrap">
              <div class="bar" style="height:35%"></div><div class="bar" style="height:55%"></div><div class="bar" style="height:42%"></div><div class="bar" style="height:78%"></div><div class="bar" style="height:62%"></div><div class="bar" style="height:88%"></div><div class="bar" style="height:70%"></div>
            </div>
            <div class="bar-labels"><div class="bar-lbl">mo</div><div class="bar-lbl">tu</div><div class="bar-lbl">we</div><div class="bar-lbl">th</div><div class="bar-lbl">fr</div><div class="bar-lbl">sa</div><div class="bar-lbl">su</div></div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- ANALYTICS -->
  <div class="page" id="page-analytics">
    <div class="section-hd"><div><h2>analytics</h2><p>usage stats and trends</p></div></div>
    <div class="stats-row">
      <div class="stat"><div class="stat-top"><div class="stat-icon" style="background:rgba(28,90,255,0.12);color:#6fa3ff"><i class="fas fa-terminal"></i></div><span class="stat-change stat-up">+12%</span></div><div class="stat-val">23,891</div><div class="stat-lbl">commands used</div><div class="stat-bar"><div class="stat-bar-fill" style="width:65%"></div></div></div>
      <div class="stat"><div class="stat-top"><div class="stat-icon" style="background:rgba(0,232,122,0.08);color:var(--green)"><i class="fas fa-message"></i></div><span class="stat-change stat-up">+8%</span></div><div class="stat-val">142k</div><div class="stat-lbl">messages seen</div><div class="stat-bar"><div class="stat-bar-fill" style="width:80%;background:var(--green)"></div></div></div>
      <div class="stat"><div class="stat-top"><div class="stat-icon" style="background:rgba(255,59,92,0.08);color:var(--red)"><i class="fas fa-ban"></i></div><span class="stat-change stat-up">47</span></div><div class="stat-val">47</div><div class="stat-lbl">bans issued</div><div class="stat-bar"><div class="stat-bar-fill" style="width:20%;background:var(--red)"></div></div></div>
      <div class="stat"><div class="stat-top"><div class="stat-icon" style="background:rgba(255,184,0,0.08);color:var(--yellow)"><i class="fas fa-ticket"></i></div><span class="stat-change stat-up">+5%</span></div><div class="stat-val">213</div><div class="stat-lbl">tickets opened</div><div class="stat-bar"><div class="stat-bar-fill" style="width:45%;background:var(--yellow)"></div></div></div>
    </div>
    <div class="card">
      <div class="card-head"><div class="card-title">top commands</div></div>
      <table class="tbl" style="margin:8px 0;">
        <thead><tr><th>command</th><th>uses</th><th>category</th><th>trend</th></tr></thead>
        <tbody>
          <tr><td><span class="mono">/ban</span></td><td>2,341</td><td><span class="tag tag-red">mod</span></td><td style="color:var(--green)">▲ 14%</td></tr>
          <tr><td><span class="mono">/play</span></td><td>1,872</td><td><span class="tag tag-purple">music</span></td><td style="color:var(--green)">▲ 9%</td></tr>
          <tr><td><span class="mono">/rank</span></td><td>1,654</td><td><span class="tag tag-blue">level</span></td><td style="color:var(--green)">▲ 6%</td></tr>
          <tr><td><span class="mono">/ticket</span></td><td>982</td><td><span class="tag tag-yellow">support</span></td><td style="color:var(--red)">▼ 2%</td></tr>
          <tr><td><span class="mono">/kick</span></td><td>741</td><td><span class="tag tag-red">mod</span></td><td style="color:var(--green)">▲ 1%</td></tr>
        </tbody>
      </table>
    </div>
  </div>

  <!-- SERVERS -->
  <div class="page" id="page-servers">
    <div class="section-hd"><div><h2>servers</h2><p>guilds your bot is in</p></div><button class="btn btn-primary" onclick="fetchGuilds()"><i class="fas fa-sync-alt"></i> fetch</button></div>
    <div class="card" id="guildsCard">
      <div style="padding:24px;text-align:center;color:var(--txt3);font-size:12px;">click "fetch" to load your servers from the Discord API</div>
    </div>
  </div>

  <!-- AUTO MOD -->
  <div class="page" id="page-automod">
    <div class="section-hd"><div><h2>auto moderation</h2><p>automated rule enforcement</p></div></div>
    <div class="g2">
      <div class="card">
        <div class="card-head"><div class="card-title">filters</div></div>
        <div class="mod-item"><div class="mod-left"><div class="mod-icon" style="background:rgba(255,59,92,0.1);color:var(--red)"><i class="fas fa-link"></i></div><div><div class="mod-name">Block Links</div><div class="mod-desc">delete messages with URLs</div></div></div><div class="toggle on" onclick="this.classList.toggle('on')"></div></div>
        <div class="mod-item"><div class="mod-left"><div class="mod-icon" style="background:rgba(255,184,0,0.08);color:var(--yellow)"><i class="fas fa-robot"></i></div><div><div class="mod-name">Anti Spam</div><div class="mod-desc">rate limit fast messages</div></div></div><div class="toggle on" onclick="this.classList.toggle('on')"></div></div>
        <div class="mod-item"><div class="mod-left"><div class="mod-icon" style="background:rgba(255,59,92,0.1);color:var(--red)"><i class="fas fa-comment-slash"></i></div><div><div class="mod-name">Bad Words</div><div class="mod-desc">custom word blacklist</div></div></div><div class="toggle on" onclick="this.classList.toggle('on')"></div></div>
        <div class="mod-item"><div class="mod-left"><div class="mod-icon" style="background:rgba(28,90,255,0.1);color:#6fa3ff"><i class="fas fa-at"></i></div><div><div class="mod-name">Block Mass Mentions</div><div class="mod-desc">3+ mentions triggers warn</div></div></div><div class="toggle" onclick="this.classList.toggle('on')"></div></div>
        <div class="mod-item"><div class="mod-left"><div class="mod-icon" style="background:rgba(124,107,255,0.1);color:var(--purple)"><i class="fas fa-font"></i></div><div><div class="mod-name">Caps Lock Filter</div><div class="mod-desc">mute for all-caps messages</div></div></div><div class="toggle" onclick="this.classList.toggle('on')"></div></div>
      </div>
      <div class="card">
        <div class="card-head"><div class="card-title">punishments</div></div>
        <div class="card-body">
          <label class="form-label">On Trigger Action</label>
          <select class="inp" style="margin-bottom:12px;"><option>Delete Message</option><option>Warn User</option><option>Timeout (10 min)</option><option>Kick</option><option>Ban</option></select>
          <label class="form-label">Log Channel</label>
          <input class="inp" placeholder="#mod-logs" style="margin-bottom:12px;">
          <label class="form-label">Exempt Roles</label>
          <input class="inp" placeholder="@Moderator, @Admin" style="margin-bottom:16px;">
          <button class="btn btn-primary" style="width:100%" onclick="toast('Auto mod saved','green')"><i class="fas fa-check"></i> save settings</button>
        </div>
      </div>
    </div>
  </div>

  <!-- INFRACTIONS -->
  <div class="page" id="page-infractions">
    <div class="section-hd"><div><h2>infractions</h2><p>issue and track moderation actions</p></div></div>
    <div class="card" style="margin-bottom:18px;">
      <div class="card-head"><div class="card-title">issue infraction</div></div>
      <div class="card-body">
        <div class="form-row">
          <div><label class="form-label">User ID / Username</label><input class="inp" id="infUser" placeholder="123456789 or User#0001"></div>
          <div><label class="form-label">Action</label><select class="inp" id="infAction"><option>warn</option><option>timeout</option><option>kick</option><option>ban</option></select></div>
        </div>
        <label class="form-label">Reason</label>
        <input class="inp" id="infReason" placeholder="reason for action..." style="margin-bottom:12px;">
        <button class="btn btn-primary" onclick="addInfraction()"><i class="fas fa-gavel"></i> issue</button>
      </div>
    </div>
    <div class="card">
      <div class="card-head"><div class="card-title">history</div><span class="tag tag-gray" id="infCount">0 records</span></div>
      <table class="tbl" id="infTable"><thead><tr><th>#</th><th>user</th><th>action</th><th>reason</th><th>time</th></tr></thead><tbody id="infBody"></tbody></table>
      <div style="padding:24px;text-align:center;color:var(--txt3);font-size:12px;" id="infEmpty">no infractions yet</div>
    </div>
  </div>

  <!-- LOGS -->
  <div class="page" id="page-logs">
    <div class="section-hd"><div><h2>logs</h2><p>live audit trail</p></div><button class="btn btn-ghost" onclick="clearLogs()"><i class="fas fa-trash"></i> clear</button></div>
    <div class="card">
      <div id="logsList">
        <div class="log-item"><div class="log-time">just now</div><div class="log-type"><span class="tag tag-green">START</span></div><div class="log-msg">bot <b>ahh</b> connected to Discord gateway</div></div>
        <div class="log-item"><div class="log-time">1m ago</div><div class="log-type"><span class="tag tag-blue">CMD</span></div><div class="log-msg"><b>User#1234</b> used <b>/rank</b> in #general</div></div>
        <div class="log-item"><div class="log-time">3m ago</div><div class="log-type"><span class="tag tag-red">MOD</span></div><div class="log-msg"><b>Mod#5678</b> banned <b>Spammer#0000</b></div></div>
        <div class="log-item"><div class="log-time">5m ago</div><div class="log-type"><span class="tag tag-yellow">WARN</span></div><div class="log-msg">auto-mod flagged a link in <b>#general</b></div></div>
        <div class="log-item"><div class="log-time">8m ago</div><div class="log-type"><span class="tag tag-purple">JOIN</span></div><div class="log-msg"><b>NewMember#9999</b> joined the server</div></div>
      </div>
    </div>
  </div>

  <!-- LEVELING -->
  <div class="page" id="page-leveling">
    <div class="section-hd"><div><h2>leveling</h2><p>xp and rank system</p></div></div>
    <div class="g2">
      <div class="card">
        <div class="card-head"><div class="card-title">settings</div></div>
        <div class="card-body">
          <label class="form-label">XP Per Message</label><input class="inp" value="15" style="margin-bottom:12px;">
          <label class="form-label">XP Cooldown (seconds)</label><input class="inp" value="60" style="margin-bottom:12px;">
          <label class="form-label">Level Up Message</label><input class="inp" value="gg {user}, you hit level {level} 🎉" style="margin-bottom:12px;">
          <label class="form-label">No XP Channels</label><input class="inp" placeholder="#spam, #bot-cmds" style="margin-bottom:16px;">
          <button class="btn btn-primary" onclick="toast('Leveling config saved','green')"><i class="fas fa-check"></i> save</button>
        </div>
      </div>
      <div class="card">
        <div class="card-head"><div class="card-title">top members</div></div>
        <table class="tbl"><thead><tr><th>rank</th><th>user</th><th>level</th><th>xp</th></tr></thead><tbody>
          <tr><td style="color:var(--yellow)">🥇</td><td>Alpha#0001</td><td><span class="tag tag-blue">42</span></td><td>88,200</td></tr>
          <tr><td style="color:#aaa">🥈</td><td>Beta#4321</td><td><span class="tag tag-blue">38</span></td><td>72,400</td></tr>
          <tr><td style="color:#cd7f32">🥉</td><td>Gamma#1337</td><td><span class="tag tag-blue">35</span></td><td>64,100</td></tr>
          <tr><td>4</td><td>Delta#9999</td><td><span class="tag tag-gray">29</span></td><td>51,300</td></tr>
          <tr><td>5</td><td>Epsilon#2020</td><td><span class="tag tag-gray">24</span></td><td>43,800</td></tr>
        </tbody></table>
      </div>
    </div>
  </div>

  <!-- MUSIC -->
  <div class="page" id="page-music">
    <div class="section-hd"><div><h2>music</h2><p>voice channel player</p></div></div>
    <div class="g2">
      <div class="card">
        <div class="card-head"><div class="card-title">now playing</div><span class="tag tag-gray">idle</span></div>
        <div class="card-body" style="text-align:center;padding:30px 20px;">
          <div style="width:70px;height:70px;background:var(--bg4);border-radius:50%;display:flex;align-items:center;justify-content:center;margin:0 auto 14px;border:2px solid var(--border);"><i class="fas fa-music" style="font-size:26px;color:var(--txt3)"></i></div>
          <div style="font-size:13px;font-weight:700;color:var(--txt2);margin-bottom:4px;">nothing playing</div>
          <div style="font-size:11px;color:var(--txt3)">use /play in a voice channel</div>
          <div style="display:flex;gap:10px;justify-content:center;margin-top:20px;">
            <button class="btn btn-ghost"><i class="fas fa-backward-step"></i></button>
            <button class="btn btn-primary" style="padding:8px 22px;"><i class="fas fa-play"></i></button>
            <button class="btn btn-ghost"><i class="fas fa-forward-step"></i></button>
          </div>
        </div>
      </div>
      <div class="card">
        <div class="card-head"><div class="card-title">settings</div></div>
        <div class="card-body">
          <label class="form-label">Default Volume</label>
          <input type="range" style="width:100%;margin-bottom:14px;accent-color:var(--accent2);" value="70">
          <label class="form-label">DJ Role</label><input class="inp" placeholder="@DJ" style="margin-bottom:14px;">
          <div class="mod-item" style="padding:0;margin-bottom:10px;"><div class="mod-name" style="font-size:12px;">24/7 Mode</div><div class="toggle" onclick="this.classList.toggle('on')"></div></div>
          <div class="mod-item" style="padding:0;"><div class="mod-name" style="font-size:12px;">Auto Queue</div><div class="toggle on" onclick="this.classList.toggle('on')"></div></div>
        </div>
      </div>
    </div>
  </div>

  <!-- TICKETS -->
  <div class="page" id="page-tickets">
    <div class="section-hd"><div><h2>tickets</h2><p>support channel system</p></div></div>
    <div class="g2">
      <div class="card">
        <div class="card-head"><div class="card-title">config</div></div>
        <div class="card-body">
          <label class="form-label">Support Category</label><input class="inp" placeholder="Tickets" style="margin-bottom:12px;">
          <label class="form-label">Staff Role</label><input class="inp" placeholder="@Support" style="margin-bottom:12px;">
          <label class="form-label">Transcript Channel</label><input class="inp" placeholder="#ticket-logs" style="margin-bottom:12px;">
          <label class="form-label">Welcome Message</label><textarea class="inp" style="margin-bottom:14px;">hey {user}, staff will be with you shortly.</textarea>
          <button class="btn btn-primary" onclick="toast('Ticket config saved','green')"><i class="fas fa-check"></i> save</button>
        </div>
      </div>
      <div class="card">
        <div class="card-head"><div class="card-title">open tickets</div><span class="tag tag-blue">3 open</span></div>
        <table class="tbl"><thead><tr><th>#</th><th>user</th><th>status</th><th>opened</th></tr></thead><tbody>
          <tr><td class="mono">#048</td><td>User#3456</td><td><span class="tag tag-yellow">open</span></td><td>2h ago</td></tr>
          <tr><td class="mono">#047</td><td>User#7890</td><td><span class="tag tag-blue">active</span></td><td>5h ago</td></tr>
          <tr><td class="mono">#046</td><td>User#1122</td><td><span class="tag tag-yellow">open</span></td><td>1d ago</td></tr>
          <tr><td class="mono">#045</td><td>User#3344</td><td><span class="tag tag-green">closed</span></td><td>2d ago</td></tr>
        </tbody></table>
      </div>
    </div>
  </div>

  <!-- WELCOME -->
  <div class="page" id="page-welcome">
    <div class="section-hd"><div><h2>welcome</h2><p>greet new members</p></div></div>
    <div class="g2">
      <div class="card">
        <div class="card-head"><div class="card-title">settings</div></div>
        <div class="card-body">
          <label class="form-label">Welcome Channel</label><input class="inp" placeholder="#welcome" style="margin-bottom:12px;">
          <label class="form-label">Message</label><textarea class="inp" style="margin-bottom:12px;">welcome to the server, {user}. you're member #{count}.</textarea>
          <label class="form-label">Auto Role on Join</label><input class="inp" placeholder="@Member" style="margin-bottom:12px;">
          <label class="form-label">Goodbye Channel</label><input class="inp" placeholder="#general" style="margin-bottom:16px;">
          <button class="btn btn-primary" onclick="toast('Welcome config saved','green')"><i class="fas fa-check"></i> save</button>
        </div>
      </div>
      <div class="card">
        <div class="card-head"><div class="card-title">preview</div></div>
        <div class="card-body">
          <div style="background:var(--bg3);border:1px solid var(--border);border-radius:8px;padding:14px;">
            <div style="display:flex;gap:10px;align-items:center;margin-bottom:8px;">
              <div style="width:32px;height:32px;background:var(--accent2);border-radius:50%;display:flex;align-items:center;justify-content:center;font-weight:800;font-size:13px;">a</div>
              <div><div style="font-size:13px;font-weight:700;">ahh <span style="font-size:10px;background:var(--accent2);padding:1px 5px;border-radius:3px;font-weight:700;">BOT</span></div><div style="font-size:10px;color:var(--txt3)">today at 12:00</div></div>
            </div>
            <div style="font-size:12px;color:var(--txt2);line-height:1.6;">welcome to the server, <span style="color:#6fa3ff">@NewUser</span>. you're member <span style="color:var(--green)">#1,249</span>.</div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- COMMANDS -->
  <div class="page" id="page-commands">
    <div class="section-hd"><div><h2>commands</h2><p>slash command manager</p></div><button class="btn btn-primary" onclick="toast('Commands synced with Discord','blue')"><i class="fas fa-sync-alt"></i> sync</button></div>
    <div class="card">
      <div class="card-head"><div class="card-title">all commands</div></div>
      <table class="tbl"><thead><tr><th>command</th><th>description</th><th>category</th><th>enabled</th></tr></thead><tbody>
        <tr><td><span class="mono">/ban</span></td><td style="color:var(--txt2)">ban a member</td><td><span class="tag tag-red">mod</span></td><td><div class="toggle on" onclick="this.classList.toggle('on')"></div></td></tr>
        <tr><td><span class="mono">/kick</span></td><td style="color:var(--txt2)">kick a member</td><td><span class="tag tag-red">mod</span></td><td><div class="toggle on" onclick="this.classList.toggle('on')"></div></td></tr>
        <tr><td><span class="mono">/mute</span></td><td style="color:var(--txt2)">timeout a member</td><td><span class="tag tag-red">mod</span></td><td><div class="toggle on" onclick="this.classList.toggle('on')"></div></td></tr>
        <tr><td><span class="mono">/warn</span></td><td style="color:var(--txt2)">issue a warning</td><td><span class="tag tag-red">mod</span></td><td><div class="toggle on" onclick="this.classList.toggle('on')"></div></td></tr>
        <tr><td><span class="mono">/rank</span></td><td style="color:var(--txt2)">view rank card</td><td><span class="tag tag-blue">level</span></td><td><div class="toggle on" onclick="this.classList.toggle('on')"></div></td></tr>
        <tr><td><span class="mono">/leaderboard</span></td><td style="color:var(--txt2)">top members by xp</td><td><span class="tag tag-blue">level</span></td><td><div class="toggle on" onclick="this.classList.toggle('on')"></div></td></tr>
        <tr><td><span class="mono">/play</span></td><td style="color:var(--txt2)">play a song</td><td><span class="tag tag-purple">music</span></td><td><div class="toggle" onclick="this.classList.toggle('on')"></div></td></tr>
        <tr><td><span class="mono">/skip</span></td><td style="color:var(--txt2)">skip current song</td><td><span class="tag tag-purple">music</span></td><td><div class="toggle" onclick="this.classList.toggle('on')"></div></td></tr>
        <tr><td><span class="mono">/ticket</span></td><td style="color:var(--txt2)">open a support ticket</td><td><span class="tag tag-yellow">support</span></td><td><div class="toggle on" onclick="this.classList.toggle('on')"></div></td></tr>
        <tr><td><span class="mono">/help</span></td><td style="color:var(--txt2)">list all commands</td><td><span class="tag tag-gray">general</span></td><td><div class="toggle on" onclick="this.classList.toggle('on')"></div></td></tr>
      </tbody></table>
    </div>
  </div>

  <!-- SETTINGS -->
  <div class="page" id="page-settings">
    <div class="section-hd"><div><h2>settings</h2><p>general bot configuration</p></div></div>
    <div class="g2">
      <div class="card">
        <div class="card-head"><div class="card-title">general</div></div>
        <div class="card-body">
          <label class="form-label">Bot Prefix</label><input class="inp" value="!" style="margin-bottom:12px;">
          <label class="form-label">Language</label><select class="inp" style="margin-bottom:12px;"><option>English</option><option>Spanish</option><option>French</option></select>
          <label class="form-label">Bot Nickname</label><input class="inp" value="ahh" style="margin-bottom:12px;">
          <label class="form-label">Status Message</label><input class="inp" value="watching your server" style="margin-bottom:16px;">
          <button class="btn btn-primary" onclick="toast('Settings saved','green')"><i class="fas fa-check"></i> save changes</button>
        </div>
      </div>
      <div class="card">
        <div class="card-head"><div class="card-title">permissions</div></div>
        <div>
          <div class="mod-item"><div class="mod-name" style="font-size:12px;">Admin bypass all filters</div><div class="toggle on" onclick="this.classList.toggle('on')"></div></div>
          <div class="mod-item"><div class="mod-name" style="font-size:12px;">Mod can issue bans</div><div class="toggle on" onclick="this.classList.toggle('on')"></div></div>
          <div class="mod-item"><div class="mod-name" style="font-size:12px;">Everyone can use /rank</div><div class="toggle on" onclick="this.classList.toggle('on')"></div></div>
          <div class="mod-item"><div class="mod-name" style="font-size:12px;">DM user on ban/kick</div><div class="toggle on" onclick="this.classList.toggle('on')"></div></div>
          <div class="mod-item"><div class="mod-name" style="font-size:12px;">Log all deleted messages</div><div class="toggle" onclick="this.classList.toggle('on')"></div></div>
        </div>
      </div>
    </div>
  </div>

  <!-- TOKEN & API -->
  <div class="page" id="page-token">
    <div class="section-hd"><div><h2>token &amp; api</h2><p>bot credentials and live info</p></div></div>
    <div class="card" style="margin-bottom:18px;">
      <div class="card-head"><div><div class="card-title">bot token</div><div class="card-sub">never share this with anyone</div></div><button class="btn btn-danger" onclick="toast('Reset at discord.com/developers','yellow')"><i class="fas fa-rotate-right"></i> regenerate</button></div>
      <div class="card-body">
        <div class="token-wrap" style="margin-bottom:10px;">
          <span class="token-val" id="tokenDisplay">••••••••••••••••••••••••••••••••••••••••••••••••</span>
          <button class="token-btn" id="revealBtn" onclick="revealToken()">reveal</button>
          <button class="token-btn" onclick="copyToken()">copy</button>
        </div>
        <div style="display:flex;align-items:center;gap:6px;font-size:11px;color:var(--yellow);"><i class="fas fa-triangle-exclamation"></i> this token grants full bot access. reset it if it was ever leaked.</div>
      </div>
    </div>
    <div class="card">
      <div class="card-head"><div class="card-title">live bot data</div><button class="btn btn-ghost" style="font-size:11px;padding:5px 10px;" onclick="fetchBotInfoToken()"><i class="fas fa-sync-alt"></i> fetch</button></div>
      <div class="card-body" id="tokenPageInfo"><div style="text-align:center;padding:20px;color:var(--txt3);font-size:12px;">click "fetch" to pull live data from the Discord API</div></div>
    </div>
  </div>

</div><!-- /main -->

<!-- TOAST -->
<div class="toast" id="toastEl"><i id="toastIcon" class="fas fa-check-circle"></i><span id="toastMsg">done</span></div>

<script>
const TOKEN = "MTQ4MzUwMDg1ODM0NzA5NDIwNw.GjLBE7.arIiw2B9S6NYNZ52XOR02G55EZAHKf09KSK2bM";
let tokenRevealed = false;
let infractions = [];
let infId = 1;
let toastTimer;
let botClientId = null;

// ── NAVIGATION ──
document.querySelectorAll('.nav-item[data-page]').forEach(el => {
  el.addEventListener('click', () => {
    document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
    document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
    el.classList.add('active');
    const pageEl = document.getElementById('page-' + el.dataset.page);
    if(pageEl) pageEl.classList.add('active');
    const label = el.textContent.trim().replace(/\d+$/, '').trim();
    document.getElementById('pageTitle').textContent = label;
    if(el.dataset.page === 'dashboard') fetchBotInfo();
    if(el.dataset.page === 'servers') fetchGuilds();
  });
});

// ── FETCH BOT INFO ──
async function fetchBotInfo() {
  try {
    const t0 = Date.now();
    const res = await fetch('https://discord.com/api/v10/users/@me', {
      headers: { Authorization: 'Bot ' + TOKEN }
    });
    const ping = Date.now() - t0;
    const data = await res.json();
    if(data.id) {
      botClientId = data.id;
      document.getElementById('infoName').textContent = data.username || 'ahh';
      document.getElementById('infoId').textContent = data.id;
      document.getElementById('infoTag').textContent = data.discriminator === '0' ? 'new format' : '#' + data.discriminator;
      document.getElementById('infoVerified').textContent = data.verified ? '✓ yes' : 'not verified';
      document.getElementById('bannerSub').textContent = 'bot id: ' + data.id + ' · online';
      document.getElementById('sv1').textContent = '—';
      document.getElementById('sv2').textContent = '—';
      document.getElementById('sv3').textContent = ping + 'ms';
      document.getElementById('sv4').textContent = 'online';
      document.getElementById('sc3').textContent = 'low';
      document.getElementById('botPingLabel').textContent = ping + ' ms';
      toast('bot info loaded ✓', 'green');
    } else {
      toast('API error: ' + (data.message || 'bad token'), 'red');
      document.getElementById('bannerSub').textContent = 'error: ' + (data.message || 'check token');
    }
  } catch(e) {
    toast('network error — CORS may block direct calls', 'red');
  }
}

// ── FETCH BOT INFO (token page) ──
async function fetchBotInfoToken() {
  document.getElementById('tokenPageInfo').innerHTML = '<div class="loader"><div class="loader-dot"></div><div class="loader-dot"></div><div class="loader-dot"></div></div>';
  try {
    const res = await fetch('https://discord.com/api/v10/users/@me', {
      headers: { Authorization: 'Bot ' + TOKEN }
    });
    const data = await res.json();
    if(data.id) {
      document.getElementById('tokenPageInfo').innerHTML = `
        <div class="sr"><div class="sr-label">username</div><div class="sr-val">${data.username}</div></div>
        <div class="sr"><div class="sr-label">id</div><div class="sr-val"><span class="mono">${data.id}</span></div></div>
        <div class="sr"><div class="sr-label">bot</div><div class="sr-val">${data.bot ? '✓ yes' : 'no'}</div></div>
        <div class="sr"><div class="sr-label">verified</div><div class="sr-val">${data.verified ? '✓ yes' : '—'}</div></div>
        <div class="sr"><div class="sr-label">public flags</div><div class="sr-val">${data.public_flags || 0}</div></div>
        <div class="sr"><div class="sr-label">mfa enabled</div><div class="sr-val">${data.mfa_enabled ? 'yes' : 'no'}</div></div>
      `;
      toast('live data fetched', 'green');
    } else {
      document.getElementById('tokenPageInfo').innerHTML = '<div style="color:var(--red);font-size:12px;padding:10px 0;">Error: ' + (data.message || 'invalid token') + '</div>';
    }
  } catch(e) {
    document.getElementById('tokenPageInfo').innerHTML = '<div style="color:var(--red);font-size:12px;padding:10px 0;">Network error — browser may block this due to CORS. Try running in a local environment.</div>';
  }
}

// ── FETCH GUILDS ──
async function fetchGuilds() {
  document.getElementById('guildsCard').innerHTML = '<div class="loader"><div class="loader-dot"></div><div class="loader-dot"></div><div class="loader-dot"></div></div>';
  try {
    const res = await fetch('https://discord.com/api/v10/users/@me/guilds', {
      headers: { Authorization: 'Bot ' + TOKEN }
    });
    const data = await res.json();
    if(Array.isArray(data) && data.length) {
      document.getElementById('sv1').textContent = data.length;
      document.getElementById('sc1').textContent = data.length + ' total';
      const html = data.slice(0, 30).map(g => `
        <div class="server-item">
          <div class="server-icon">${g.name.charAt(0).toUpperCase()}</div>
          <div style="flex:1;">
            <div style="font-size:13px;font-weight:700;">${g.name}</div>
            <div style="font-size:11px;color:var(--txt2);">id: ${g.id}${g.owner ? ' · <span style="color:var(--yellow)">owner</span>' : ''}</div>
          </div>
          <span class="tag tag-green">in</span>
        </div>
      `).join('');
      document.getElementById('guildsCard').innerHTML = html;
      toast(data.length + ' servers loaded', 'green');
    } else if(data.message) {
      document.getElementById('guildsCard').innerHTML = '<div style="padding:20px;color:var(--red);font-size:12px;">API error: ' + data.message + '</div>';
    } else {
      document.getElementById('guildsCard').innerHTML = '<div style="padding:20px;color:var(--txt2);font-size:12px;">no servers found</div>';
    }
  } catch(e) {
    document.getElementById('guildsCard').innerHTML = '<div style="padding:20px;color:var(--red);font-size:12px;">fetch failed — browser CORS may block this. try a local server.</div>';
  }
}

// ── TOKEN ──
function revealToken() {
  tokenRevealed = !tokenRevealed;
  document.getElementById('tokenDisplay').textContent = tokenRevealed ? TOKEN : '••••••••••••••••••••••••••••••••••••••••••••••••';
  document.getElementById('revealBtn').textContent = tokenRevealed ? 'hide' : 'reveal';
}

function copyToken() {
  navigator.clipboard.writeText(TOKEN).then(() => {
    toast('token copied to clipboard', 'green');
  }).catch(() => {
    toast('copy failed — try manually', 'red');
  });
}

// ── INFRACTIONS ──
function addInfraction() {
  const user = document.getElementById('infUser').value.trim();
  const action = document.getElementById('infAction').value;
  const reason = document.getElementById('infReason').value.trim() || 'no reason provided';
  if(!user) { toast('enter a user id or name', 'red'); return; }
  const now = new Date().toLocaleTimeString([], {hour:'2-digit',minute:'2-digit'});
  infractions.unshift({ id: infId++, user, action, reason, time: now });
  renderInfractions();
  document.getElementById('infUser').value = '';
  document.getElementById('infReason').value = '';
  toast(action + ' issued to ' + user, 'green');
}

function renderInfractions() {
  const tbody = document.getElementById('infBody');
  const empty = document.getElementById('infEmpty');
  const count = infractions.length;
  document.getElementById('infCount').textContent = count + ' record' + (count !== 1 ? 's' : '');
  document.getElementById('infBadge').textContent = count;
  if(count === 0) { tbody.innerHTML = ''; empty.style.display = 'block'; return; }
  empty.style.display = 'none';
  tbody.innerHTML = infractions.map(i => `
    <tr>
      <td class="mono">#${String(i.id).padStart(3,'0')}</td>
      <td>${i.user}</td>
      <td><span class="tag ${i.action==='ban'||i.action==='kick'?'tag-red':'tag-yellow'}">${i.action}</span></td>
      <td style="color:var(--txt2)">${i.reason}</td>
      <td style="color:var(--txt3);font-size:11px;">${i.time}</td>
    </tr>
  `).join('');
}

// ── LOGS ──
function clearLogs() {
  document.getElementById('logsList').innerHTML = '<div style="padding:24px;text-align:center;color:var(--txt3);font-size:12px;">logs cleared</div>';
  toast('logs cleared', 'green');
}

// ── INVITE ──
function inviteBot() {
  const id = botClientId || document.getElementById('infoId').textContent;
  if(id && id !== '—') {
    window.open('https://discord.com/oauth2/authorize?client_id=' + id + '&scope=bot+applications.commands&permissions=8', '_blank');
  } else {
    toast('fetch bot info first to get client id', 'yellow');
  }
}

// ── TOAST ──
function toast(msg, type = 'green') {
  const el = document.getElementById('toastEl');
  const icon = document.getElementById('toastIcon');
  document.getElementById('toastMsg').textContent = msg;
  const colors = { green: 'var(--green)', red: 'var(--red)', blue: 'var(--accent2)', yellow: 'var(--yellow)' };
  const icons = { green: 'fa-check-circle', red: 'fa-circle-xmark', blue: 'fa-circle-info', yellow: 'fa-triangle-exclamation' };
  icon.style.color = colors[type] || colors.green;
  icon.className = 'fas ' + (icons[type] || icons.green);
  el.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(() => el.classList.remove('show'), 3000);
}

// init
fetchBotInfo();
renderInfractions();
</script>
</body>
</html>
