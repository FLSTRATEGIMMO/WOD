<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="theme-color" content="#0D0D1A">
<title>WOD BOOK — Niveau ÉLITE</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400;600;700;800;900&family=Barlow:wght@300;400;500;600&display=swap" rel="stylesheet">

<style>
:root {
  --dark:    #0D0D1A;
  --mid:     #16213E;
  --card:    #1A1A2E;
  --border:  #2A2A45;
  --accent1: #E94560;
  --accent2: #0F3460;
  --accent3: #533483;
  --gold:    #F5A623;
  --green:   #27AE60;
  --white:   #F0F0F5;
  --muted:   #8888AA;
  --font-head: 'Barlow Condensed', sans-serif;
  --font-body: 'Barlow', sans-serif;
}

* { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }

body {
  background: var(--dark);
  color: var(--white);
  font-family: var(--font-body);
  min-height: 100vh;
  overscroll-behavior: none;
}

/* ── TOP BAR ── */
.topbar {
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  background: rgba(13,13,26,0.95);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--border);
  height: 56px;
  display: flex; align-items: center; justify-content: space-between;
  padding: 0 16px;
}
.topbar-logo {
  font-family: var(--font-head);
  font-size: 20px; font-weight: 900; letter-spacing: 2px;
  color: var(--white);
}
.topbar-logo span { color: var(--accent1); }
.topbar-sync {
  display: flex; align-items: center; gap: 8px;
  font-size: 12px; color: var(--muted);
}
.sync-dot {
  width: 8px; height: 8px; border-radius: 50%;
  background: var(--muted);
  transition: background .3s;
}
.sync-dot.ok { background: var(--green); }
.sync-dot.saving { background: var(--gold); animation: pulse .6s infinite; }

@keyframes pulse { 0%,100%{opacity:1} 50%{opacity:.4} }

/* ── NAV TABS ── */
.nav-tabs {
  position: fixed; bottom: 0; left: 0; right: 0; z-index: 100;
  background: rgba(13,13,26,0.97);
  border-top: 1px solid var(--border);
  display: flex;
}
.nav-tab {
  flex: 1; display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  padding: 8px 4px 10px;
  cursor: pointer; border: none; background: none;
  color: var(--muted); font-family: var(--font-head);
  font-size: 10px; font-weight: 700; letter-spacing: 1px;
  text-transform: uppercase; gap: 4px;
  transition: color .2s;
}
.nav-tab.active { color: var(--accent1); }
.nav-tab svg { width: 20px; height: 20px; }
.nav-tab-bar {
  position: absolute; top: 0; left: 10%; right: 10%; height: 2px;
  background: var(--accent1); border-radius: 0 0 2px 2px;
  transform: scaleX(0); transition: transform .25s;
}
.nav-tab.active .nav-tab-bar { transform: scaleX(1); }

/* ── MAIN CONTENT ── */
.main {
  padding: 72px 0 80px;
  min-height: 100vh;
}

/* ── SCREENS ── */
.screen { display: none; }
.screen.active { display: block; }

/* ── HERO / DASHBOARD ── */
.hero {
  background: linear-gradient(135deg, var(--mid) 0%, var(--dark) 100%);
  padding: 20px 16px 24px;
  border-bottom: 1px solid var(--border);
}
.hero-greeting {
  font-size: 13px; color: var(--muted); margin-bottom: 4px;
  font-weight: 500; text-transform: uppercase; letter-spacing: 1px;
}
.hero-title {
  font-family: var(--font-head);
  font-size: 32px; font-weight: 900; line-height: 1;
  color: var(--white);
}
.hero-title span { color: var(--accent1); }

.stats-row {
  display: grid; grid-template-columns: repeat(4, 1fr); gap: 8px;
  padding: 16px;
}
.stat-card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 10px 8px;
  text-align: center;
}
.stat-num {
  font-family: var(--font-head);
  font-size: 26px; font-weight: 900; line-height: 1;
}
.stat-num.red { color: var(--accent1); }
.stat-num.blue { color: #4FC3F7; }
.stat-num.purple { color: #B39DDB; }
.stat-num.gold { color: var(--gold); }
.stat-label { font-size: 9px; color: var(--muted); text-transform: uppercase; letter-spacing: .5px; margin-top: 2px; }

/* ── FILTERS / SEARCH ── */
.filters {
  padding: 12px 16px;
  display: flex; gap: 8px; flex-wrap: wrap;
}
.filter-btn {
  padding: 6px 14px;
  border-radius: 20px;
  border: 1px solid var(--border);
  background: var(--card);
  color: var(--muted);
  font-family: var(--font-head);
  font-size: 12px; font-weight: 700; letter-spacing: 1px;
  cursor: pointer; transition: all .2s;
  text-transform: uppercase;
}
.filter-btn.active { border-color: var(--accent1); color: var(--accent1); background: rgba(233,69,96,.1); }
.filter-btn.haut.active { border-color: var(--accent1); color: var(--accent1); background: rgba(233,69,96,.1); }
.filter-btn.bas.active { border-color: #4FC3F7; color: #4FC3F7; background: rgba(79,195,247,.1); }
.filter-btn.complet.active { border-color: #B39DDB; color: #B39DDB; background: rgba(179,157,219,.1); }
.filter-btn.challenge.active { border-color: var(--gold); color: var(--gold); background: rgba(245,166,35,.1); }

.search-bar {
  padding: 0 16px 12px;
}
.search-input {
  width: 100%; background: var(--card);
  border: 1px solid var(--border); border-radius: 10px;
  padding: 10px 16px; color: var(--white);
  font-family: var(--font-body); font-size: 14px;
  outline: none;
}
.search-input::placeholder { color: var(--muted); }
.search-input:focus { border-color: var(--accent1); }

/* ── WOD LIST ── */
.wod-list { padding: 0 16px; display: flex; flex-direction: column; gap: 8px; }

.wod-card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 12px;
  overflow: hidden;
  cursor: pointer;
  transition: transform .15s, border-color .15s;
  position: relative;
}
.wod-card:active { transform: scale(.98); }
.wod-card.done { border-color: rgba(39,174,96,.3); }
.wod-card.done::after {
  content: '✓';
  position: absolute; top: 10px; right: 12px;
  color: var(--green); font-size: 16px; font-weight: 700;
}

.wod-card-header {
  display: flex; align-items: center; gap: 0;
}
.wod-num {
  background: var(--accent1);
  font-family: var(--font-head); font-size: 13px; font-weight: 800;
  color: white; padding: 8px 12px; white-space: nowrap;
  letter-spacing: 1px;
}
.wod-num.bas { background: var(--accent2); }
.wod-num.complet { background: var(--accent3); }
.wod-num.challenge { background: var(--gold); color: var(--dark); }
.wod-type-badge {
  background: var(--mid); padding: 8px 10px;
  font-size: 9px; font-weight: 700; color: var(--muted);
  text-transform: uppercase; letter-spacing: 1px;
  flex: 1;
}
.wod-card-body { padding: 10px 14px 12px; }
.wod-name {
  font-family: var(--font-head); font-size: 20px; font-weight: 900;
  letter-spacing: 1px; line-height: 1.1; margin-bottom: 3px;
}
.wod-format {
  font-size: 11px; color: var(--muted); margin-bottom: 6px;
}
.wod-preview {
  font-size: 11.5px; color: #9999BB; line-height: 1.5;
}

/* ── WOD DETAIL MODAL ── */
.modal-overlay {
  display: none; position: fixed; inset: 0; z-index: 200;
  background: rgba(0,0,0,.7); backdrop-filter: blur(4px);
}
.modal-overlay.open { display: flex; align-items: flex-end; }
@media(min-width:600px) { .modal-overlay.open { align-items: center; justify-content: center; } }

.modal {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 20px 20px 0 0;
  width: 100%; max-height: 90vh; overflow-y: auto;
  padding: 0 0 32px;
  animation: slideUp .25s ease;
}
@media(min-width:600px) {
  .modal { border-radius: 16px; max-width: 480px; max-height: 80vh; }
}
@keyframes slideUp { from { transform: translateY(100%); } to { transform: translateY(0); } }

.modal-handle {
  width: 36px; height: 4px; background: var(--border);
  border-radius: 2px; margin: 12px auto 0;
}
.modal-header {
  padding: 16px 16px 12px;
  border-bottom: 1px solid var(--border);
}
.modal-badge {
  display: flex; gap: 0; margin-bottom: 10px; border-radius: 8px; overflow: hidden;
}
.modal-badge-num {
  background: var(--accent1); color: white;
  font-family: var(--font-head); font-size: 13px; font-weight: 800;
  padding: 6px 14px; letter-spacing: 1px;
}
.modal-badge-num.bas { background: var(--accent2); }
.modal-badge-num.complet { background: var(--accent3); }
.modal-badge-num.challenge { background: var(--gold); color: var(--dark); }
.modal-badge-type {
  background: var(--mid); flex: 1;
  font-size: 9px; font-weight: 700; color: var(--muted);
  text-transform: uppercase; letter-spacing: 1px;
  display: flex; align-items: center; padding: 0 12px;
}
.modal-name {
  font-family: var(--font-head); font-size: 28px; font-weight: 900;
  letter-spacing: 2px; line-height: 1;
}
.modal-format {
  margin-top: 6px;
  background: rgba(233,69,96,.12); border: 1px solid rgba(233,69,96,.3);
  border-radius: 6px; padding: 6px 12px;
  font-size: 12px; font-weight: 600; color: var(--accent1);
  display: inline-block;
}
.modal-format.bas { background: rgba(79,195,247,.08); border-color: rgba(79,195,247,.3); color: #4FC3F7; }
.modal-format.complet { background: rgba(179,157,219,.08); border-color: rgba(179,157,219,.3); color: #B39DDB; }
.modal-format.challenge { background: rgba(245,166,35,.1); border-color: rgba(245,166,35,.3); color: var(--gold); }

.modal-body { padding: 16px; }
.modal-section-title {
  font-family: var(--font-head); font-size: 11px; font-weight: 700;
  letter-spacing: 2px; color: var(--muted); text-transform: uppercase;
  margin-bottom: 10px;
}
.exercise-list { display: flex; flex-direction: column; gap: 6px; margin-bottom: 16px; }
.exercise-item {
  display: flex; align-items: baseline; gap: 10px;
  background: rgba(255,255,255,.03); border-radius: 8px;
  padding: 8px 12px; border-left: 2px solid var(--accent1);
  font-size: 13.5px; line-height: 1.4;
}
.exercise-item.bas { border-color: #4FC3F7; }
.exercise-item.complet { border-color: #B39DDB; }
.exercise-item.challenge { border-color: var(--gold); }
.exercise-bullet {
  font-size: 8px; color: var(--muted); flex-shrink: 0; margin-top: 2px;
}
.note-box {
  background: rgba(245,166,35,.08); border: 1px solid rgba(245,166,35,.25);
  border-radius: 8px; padding: 10px 14px;
  font-size: 12px; color: var(--gold); margin-bottom: 16px;
  display: flex; gap: 8px; align-items: flex-start;
}

/* ── LOG FORM ── */
.log-form {
  background: rgba(255,255,255,.03);
  border: 1px solid var(--border);
  border-radius: 12px; padding: 16px; margin: 0 16px;
}
.log-title {
  font-family: var(--font-head); font-size: 14px; font-weight: 700;
  letter-spacing: 1px; color: var(--white); margin-bottom: 14px;
  display: flex; align-items: center; gap: 8px;
}
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 10px; }
.form-field { display: flex; flex-direction: column; gap: 5px; }
.form-field.full { grid-column: 1 / -1; }
.form-label { font-size: 10px; color: var(--muted); text-transform: uppercase; letter-spacing: 1px; font-weight: 600; }
.form-input, .form-select, .form-textarea {
  background: var(--dark); border: 1px solid var(--border);
  border-radius: 8px; padding: 9px 12px;
  color: var(--white); font-family: var(--font-body); font-size: 13px;
  outline: none; transition: border-color .2s;
  -webkit-appearance: none;
}
.form-input:focus, .form-select:focus, .form-textarea:focus { border-color: var(--accent1); }
.form-select option { background: var(--dark); }
.form-textarea { resize: none; height: 60px; }

.btn-save {
  width: 100%; padding: 14px;
  background: var(--accent1); border: none; border-radius: 10px;
  color: white; font-family: var(--font-head); font-size: 16px;
  font-weight: 800; letter-spacing: 2px; cursor: pointer;
  transition: opacity .2s; text-transform: uppercase; margin-top: 4px;
}
.btn-save:active { opacity: .8; }
.btn-save.saved { background: var(--green); }

/* ── LOGBOOK / HISTORY ── */
.log-entries { padding: 0 16px; display: flex; flex-direction: column; gap: 10px; }
.log-entry {
  background: var(--card); border: 1px solid var(--border);
  border-radius: 12px; padding: 14px 16px;
  display: flex; justify-content: space-between; align-items: flex-start;
}
.log-entry-left { flex: 1; }
.log-entry-name {
  font-family: var(--font-head); font-size: 18px; font-weight: 800;
  letter-spacing: 1px; margin-bottom: 3px;
}
.log-entry-meta { font-size: 11px; color: var(--muted); margin-bottom: 4px; }
.log-entry-note { font-size: 11.5px; color: #9999BB; font-style: italic; }
.log-entry-right { text-align: right; flex-shrink: 0; }
.log-entry-score {
  font-family: var(--font-head); font-size: 22px; font-weight: 900;
  color: var(--accent1); line-height: 1;
}
.log-entry-date { font-size: 10px; color: var(--muted); margin-top: 2px; }
.log-entry-type-dot {
  width: 8px; height: 8px; border-radius: 50%;
  display: inline-block; margin-right: 4px;
}

/* ── CHALLENGES SCREEN ── */
.challenge-grid { padding: 0 16px; display: flex; flex-direction: column; gap: 10px; }
.challenge-card {
  background: var(--card); border: 1px solid var(--border);
  border-radius: 12px; overflow: hidden; cursor: pointer;
  transition: transform .15s; position: relative;
}
.challenge-card:active { transform: scale(.98); }
.challenge-card.done { border-color: rgba(39,174,96,.4); }
.challenge-header {
  display: flex; align-items: center;
  background: var(--gold); padding: 8px 14px; gap: 10px;
}
.challenge-num {
  font-family: var(--font-head); font-size: 13px; font-weight: 900;
  color: var(--dark); letter-spacing: 1px;
}
.challenge-stars { font-size: 11px; margin-left: auto; }
.challenge-body { padding: 10px 14px 14px; }
.challenge-name {
  font-family: var(--font-head); font-size: 20px; font-weight: 900;
  letter-spacing: 1px; margin-bottom: 3px;
}
.challenge-desc { font-size: 11px; color: var(--muted); margin-bottom: 8px; }
.challenge-score-row {
  display: flex; gap: 8px; align-items: center;
}
.challenge-best {
  font-family: var(--font-head); font-size: 18px; font-weight: 800;
  color: var(--gold);
}
.challenge-done-badge {
  background: rgba(39,174,96,.15); border: 1px solid rgba(39,174,96,.4);
  color: var(--green); font-size: 10px; font-weight: 700;
  padding: 3px 8px; border-radius: 20px; letter-spacing: 1px;
}

/* ── PROGRESS SCREEN ── */
.progress-wrap { padding: 0 16px; }
.progress-section { margin-bottom: 24px; }
.progress-section-title {
  font-family: var(--font-head); font-size: 14px; font-weight: 800;
  letter-spacing: 2px; text-transform: uppercase; color: var(--muted);
  margin-bottom: 12px; padding-bottom: 8px;
  border-bottom: 1px solid var(--border);
}
.progress-bar-wrap { margin-bottom: 10px; }
.progress-bar-label {
  display: flex; justify-content: space-between;
  font-size: 12px; margin-bottom: 5px;
}
.progress-bar-label span:first-child { color: var(--white); font-weight: 500; }
.progress-bar-label span:last-child { color: var(--muted); }
.progress-bar-bg {
  background: var(--border); border-radius: 4px; height: 6px; overflow: hidden;
}
.progress-bar-fill {
  height: 100%; border-radius: 4px; transition: width 1s ease;
}
.fill-red { background: var(--accent1); }
.fill-blue { background: #4FC3F7; }
.fill-purple { background: #B39DDB; }
.fill-gold { background: var(--gold); }

.recent-list { display: flex; flex-direction: column; gap: 8px; }
.recent-item {
  background: var(--card); border: 1px solid var(--border);
  border-radius: 10px; padding: 10px 14px;
  display: flex; justify-content: space-between; align-items: center;
}
.recent-item-name {
  font-family: var(--font-head); font-size: 16px; font-weight: 800;
  letter-spacing: 1px;
}
.recent-item-meta { font-size: 10px; color: var(--muted); }
.recent-item-score {
  font-family: var(--font-head); font-size: 18px; font-weight: 900;
  color: var(--accent1);
}

/* ── USER SETUP ── */
.setup-screen {
  display: none; position: fixed; inset: 0; z-index: 300;
  background: var(--dark);
  align-items: center; justify-content: center; flex-direction: column;
  padding: 24px;
}
.setup-screen.active { display: flex; }
.setup-logo {
  font-family: var(--font-head); font-size: 40px; font-weight: 900;
  letter-spacing: 4px; margin-bottom: 8px;
}
.setup-logo span { color: var(--accent1); }
.setup-sub { color: var(--muted); margin-bottom: 32px; font-size: 14px; text-align: center; }
.setup-input {
  width: 100%; max-width: 320px;
  background: var(--card); border: 1px solid var(--border);
  border-radius: 10px; padding: 14px 16px;
  color: var(--white); font-family: var(--font-body); font-size: 16px;
  outline: none; margin-bottom: 12px;
}
.setup-input:focus { border-color: var(--accent1); }
.setup-btn {
  width: 100%; max-width: 320px; padding: 14px;
  background: var(--accent1); border: none; border-radius: 10px;
  color: white; font-family: var(--font-head); font-size: 18px;
  font-weight: 900; letter-spacing: 2px; cursor: pointer;
}
.setup-hint { font-size: 11px; color: var(--muted); margin-top: 16px; text-align: center; max-width: 280px; }

/* ── EMPTY STATE ── */
.empty-state {
  text-align: center; padding: 40px 20px;
  color: var(--muted);
}
.empty-state-icon { font-size: 40px; margin-bottom: 12px; }
.empty-state-text { font-size: 14px; }

/* ── TOAST ── */
.toast {
  position: fixed; bottom: 90px; left: 50%; transform: translateX(-50%) translateY(20px);
  background: var(--green); color: white;
  padding: 10px 20px; border-radius: 20px;
  font-family: var(--font-head); font-size: 14px; font-weight: 700; letter-spacing: 1px;
  opacity: 0; transition: all .3s; z-index: 500; white-space: nowrap;
}
.toast.show { opacity: 1; transform: translateX(-50%) translateY(0); }

/* ── MODAL CLOSE ── */
.modal-close-btn {
  position: absolute; top: 14px; right: 14px;
  background: var(--border); border: none; border-radius: 50%;
  width: 32px; height: 32px; cursor: pointer; color: var(--muted);
  display: flex; align-items: center; justify-content: center;
  font-size: 18px;
}
.modal-close-btn:active { background: var(--accent1); color: white; }

/* ── SCROLLBAR ── */
::-webkit-scrollbar { width: 4px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb { background: var(--border); border-radius: 2px; }

/* ── SECTION HEADER ── */
.section-header {
  padding: 12px 16px 8px;
  display: flex; align-items: center; justify-content: space-between;
}
.section-title {
  font-family: var(--font-head); font-size: 13px; font-weight: 800;
  letter-spacing: 2px; text-transform: uppercase; color: var(--muted);
}
.section-count {
  font-family: var(--font-head); font-size: 13px; font-weight: 700;
  color: var(--accent1);
}

/* Responsive */
@media(min-width: 600px) {
  .stats-row { grid-template-columns: repeat(4, 1fr); }
  .wod-list, .challenge-grid, .log-entries, .progress-wrap { max-width: 600px; margin: 0 auto; }
  .filters, .search-bar, .section-header { max-width: 600px; margin: 0 auto; }
}
</style>
</head>

<body>

<!-- SETUP SCREEN -->
<div class="setup-screen active" id="setupScreen">
  <div class="setup-logo">WOD<span>BOOK</span></div>
  <p class="setup-sub">Entrez votre nom pour synchroniser vos performances entre tous vos appareils</p>
  <input class="setup-input" id="setupName" type="text" placeholder="Votre prénom (ex: Fabrice)" maxlength="30" autocomplete="off">
  <input class="setup-input" id="setupCode" type="text" placeholder="Code d'équipe (optionnel)" maxlength="20" autocomplete="off" style="margin-top:0">
  <button class="setup-btn" onclick="startApp()">COMMENCER →</button>
  <p class="setup-hint">Utilisez le même prénom + code sur tous vos appareils pour synchroniser automatiquement.</p>
</div>

<!-- TOP BAR -->
<div class="topbar">
  <div class="topbar-logo">WOD<span>BOOK</span></div>
  <div class="topbar-sync">
    <div class="sync-dot" id="syncDot"></div>
    <span id="syncLabel">–</span>
  </div>
</div>

<!-- MAIN -->
<div class="main">

  <!-- SCREEN: WODs -->
  <div class="screen active" id="screen-wods">
    <div class="hero">
      <div class="hero-greeting" id="heroGreeting">Niveau ÉLITE !</div>
      <div class="hero-title">WOD <span>BOOK</span></div>
    </div>
    <div class="stats-row">
      <div class="stat-card">
        <div class="stat-num red" id="statTotal">0</div>
        <div class="stat-label">Faits</div>
      </div>
      <div class="stat-card">
        <div class="stat-num blue" id="statHaut">0/50</div>
        <div class="stat-label">Haut</div>
      </div>
      <div class="stat-card">
        <div class="stat-num purple" id="statBas">0/50</div>
        <div class="stat-label">Bas</div>
      </div>
      <div class="stat-card">
        <div class="stat-num gold" id="statComplet">0/50</div>
        <div class="stat-label">Complet</div>
      </div>
    </div>
    <div class="filters">
      <button class="filter-btn active" onclick="setFilter('all', this)">Tous</button>
      <button class="filter-btn haut" onclick="setFilter('haut', this)">Haut</button>
      <button class="filter-btn bas" onclick="setFilter('bas', this)">Bas</button>
      <button class="filter-btn complet" onclick="setFilter('complet', this)">Complet</button>
      <button class="filter-btn" onclick="setFilter('done', this)">✓ Faits</button>
      <button class="filter-btn" onclick="setFilter('todo', this)">À faire</button>
    </div>
    <div class="search-bar">
      <input class="search-input" id="searchInput" placeholder="🔍  Rechercher un WOD..." oninput="renderWods()">
    </div>
    <div class="section-header">
      <div class="section-title">WODs</div>
      <div class="section-count" id="wodCount"></div>
    </div>
    <div class="wod-list" id="wodList"></div>
    <div style="height:16px"></div>
  </div>

  <!-- SCREEN: Challenges -->
  <div class="screen" id="screen-challenges">
    <div class="hero">
      <div class="hero-greeting">Tests de sélection · Records</div>
      <div class="hero-title">CHAL<span>LENGES</span></div>
    </div>
    <div class="stats-row">
      <div class="stat-card" style="grid-column:span 2">
        <div class="stat-num gold" id="statChallDone">0</div>
        <div class="stat-label">Challenges complétés</div>
      </div>
      <div class="stat-card" style="grid-column:span 2">
        <div class="stat-num red" id="statChallLeft">0</div>
        <div class="stat-label">Restants</div>
      </div>
    </div>
    <div class="section-header">
      <div class="section-title">50 Challenges</div>
    </div>
    <div class="challenge-grid" id="challengeGrid"></div>
    <div style="height:16px"></div>
  </div>

  <!-- SCREEN: Logbook -->
  <div class="screen" id="screen-log">
    <div class="hero">
      <div class="hero-greeting">Historique de vos performances</div>
      <div class="hero-title">LOG<span>BOOK</span></div>
    </div>
    <div class="section-header">
      <div class="section-title">Dernières entrées</div>
      <div class="section-count" id="logCount"></div>
    </div>
    <div class="log-entries" id="logEntries"></div>
    <div class="empty-state" id="logEmpty" style="display:none">
      <div class="empty-state-icon">📋</div>
      <div class="empty-state-text">Aucun entraînement enregistré.<br>Faites votre premier WOD !</div>
    </div>
    <div style="height:16px"></div>
  </div>

  <!-- SCREEN: Progress -->
  <div class="screen" id="screen-progress">
    <div class="hero">
      <div class="hero-greeting">Votre évolution</div>
      <div class="hero-title">PRO<span>GRÈS</span></div>
    </div>
    <div class="progress-wrap" id="progressWrap">
      <div style="height:16px"></div>
      <div class="progress-section">
        <div class="progress-section-title">Complétion par catégorie</div>
        <div class="progress-bar-wrap">
          <div class="progress-bar-label"><span>Haut du corps</span><span id="pctHaut">0%</span></div>
          <div class="progress-bar-bg"><div class="progress-bar-fill fill-red" id="barHaut" style="width:0%"></div></div>
        </div>
        <div class="progress-bar-wrap">
          <div class="progress-bar-label"><span>Bas du corps</span><span id="pctBas">0%</span></div>
          <div class="progress-bar-bg"><div class="progress-bar-fill fill-blue" id="barBas" style="width:0%"></div></div>
        </div>
        <div class="progress-bar-wrap">
          <div class="progress-bar-label"><span>Corps complet</span><span id="pctComplet">0%</span></div>
          <div class="progress-bar-bg"><div class="progress-bar-fill fill-purple" id="barComplet" style="width:0%"></div></div>
        </div>
        <div class="progress-bar-wrap">
          <div class="progress-bar-label"><span>Challenges</span><span id="pctChall">0%</span></div>
          <div class="progress-bar-bg"><div class="progress-bar-fill fill-gold" id="barChall" style="width:0%"></div></div>
        </div>
      </div>
      <div class="progress-section">
        <div class="progress-section-title">5 derniers entraînements</div>
        <div class="recent-list" id="recentList"></div>
      </div>
    </div>
  </div>

</div>

<!-- NAV TABS -->
<nav class="nav-tabs">
  <button class="nav-tab active" onclick="goTo('wods', this)">
    <div class="nav-tab-bar"></div>
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/><rect x="3" y="14" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/></svg>
    WODs
  </button>
  <button class="nav-tab" onclick="goTo('challenges', this)">
    <div class="nav-tab-bar"></div>
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polygon points="12,2 15.09,8.26 22,9.27 17,14.14 18.18,21.02 12,17.77 5.82,21.02 7,14.14 2,9.27 8.91,8.26"/></svg>
    Défis
  </button>
  <button class="nav-tab" onclick="goTo('log', this)">
    <div class="nav-tab-bar"></div>
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/></svg>
    Logbook
  </button>
  <button class="nav-tab" onclick="goTo('progress', this)">
    <div class="nav-tab-bar"></div>
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
    Progrès
  </button>
</nav>

<!-- WOD DETAIL MODAL -->
<div class="modal-overlay" id="modalOverlay" onclick="closeModal(event)">
  <div class="modal" id="modal">
    <button class="modal-close-btn" onclick="closeModalDirect()">×</button>
    <div class="modal-handle"></div>
    <div class="modal-header">
      <div class="modal-badge">
        <div class="modal-badge-num" id="mBadgeNum">WOD #001</div>
        <div class="modal-badge-type" id="mBadgeType">HAUT DU CORPS</div>
      </div>
      <div class="modal-name" id="mName">ALPHA</div>
      <div class="modal-format" id="mFormat">5 rounds</div>
    </div>
    <div class="modal-body">
      <div class="modal-section-title">EXERCICES</div>
      <div class="exercise-list" id="mExercises"></div>
      <div class="note-box" id="mNote" style="display:none">
        <span>⚡</span><span id="mNoteText"></span>
      </div>
    </div>

    <!-- LOG FORM -->
    <div class="log-form">
      <div class="log-title">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--gold)" stroke-width="2"><path d="M12 2v20M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6"/></svg>
        Enregistrer ma performance
      </div>
      <div class="form-row">
        <div class="form-field">
          <label class="form-label">Date</label>
          <input class="form-input" type="date" id="logDate">
        </div>
        <div class="form-field">
          <label class="form-label">Temps</label>
          <input class="form-input" type="text" id="logTime" placeholder="ex: 22:45">
        </div>
      </div>
      <div class="form-row">
        <div class="form-field">
          <label class="form-label">Rounds / Score</label>
          <input class="form-input" type="text" id="logScore" placeholder="ex: 8 rounds">
        </div>
        <div class="form-field">
          <label class="form-label">Ressenti</label>
          <select class="form-select" id="logFeeling">
            <option value="😤">😤 Dans le dur</option>
            <option value="💪" selected>💪 Bon</option>
            <option value="🔥">🔥 On fire</option>
            <option value="🏆">🏆 Record</option>
          </select>
        </div>
      </div>
      <div class="form-row">
        <div class="form-field full">
          <label class="form-label">Note personnelle</label>
          <textarea class="form-textarea" id="logNote" placeholder="Observations, conditions, sensations..."></textarea>
        </div>
      </div>
      <button class="btn-save" id="saveBtn" onclick="saveLog()">ENREGISTRER ✓</button>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script>
// ── DATA: ALL WODs ─────────────────────────────────────────────────────────────
const WODS = [
  // ── HAUT DU CORPS ÉLITE (1-50) ─────────────────────────────────────────────
  {id:1,num:"WOD #001",type:"haut",name:"ALPHA",format:"7 rounds — SANS RIR",exercises:["30 pompes claquées","20 dips lestés (10 kg)","15 tractions prise large","15 pompes diamant","20 élévations latérales KB","10 muscle-ups"],note:"Aucun repos entre les exercices du round"},
  {id:2,num:"WOD #002",type:"haut",name:"BRAVO",format:"AMRAP 30 min",exercises:["12 tractions prise large","20 pompes archer","15 dips lestés","10 muscle-ups (anneaux)","25 pompes sautées claquées","8 tractions L-sit"],note:"Objectif élite : >12 rounds"},
  {id:3,num:"WOD #003",type:"haut",name:"CHARLIE",format:"6 rounds — RIR 30 s MAX",exercises:["20 tractions supination","30 pompes claquées","20 dips parallèles lestés","15 pompes large + 15 serrées (enchaîné)","45 s gainage dorsal actif"],note:"RIR 30 s strict — chronométré"},
  {id:4,num:"WOD #004",type:"haut",name:"DELTA",format:"TABATA 10 rounds (20 s / 5 s)",exercises:["Pompes araignée","Tractions isométriques 5 s maintien","Dips lestés","Pompes pieds surélevés sur chaise","Muscle-ups négatifs lents"],note:"Repos réduit à 5 s — niveau sélection"},
  {id:5,num:"WOD #005",type:"haut",name:"ECHO",format:"5 rounds — SANS RIR",exercises:["Max pompes en 90 s","30 s repos","Max tractions en 90 s","30 s repos","Max dips en 90 s","30 s repos"],note:"Objectif : maintenir >85% sur tous les rounds"},
  {id:6,num:"WOD #006",type:"haut",name:"FOXTROT",format:"8 rounds — RIR 30 s",exercises:["20 pompes sautées claquées","15 tractions prise neutre","15 pompes isométriques (5 s bas)","20 abdos toes to bar","10 muscle-ups"],note:"Si RIR dépassé : 5 pompes pénalité"},
  {id:7,num:"WOD #007",type:"haut",name:"GOLF",format:"For time — 30-20-15-9",exercises:["Pompes claquées (30-20-15-9)","Tractions (30-20-15-9)","Dips lestés (30-20-15-9)","Muscle-ups (10-8-5-3)"],note:"Objectif élite < 12 min"},
  {id:8,num:"WOD #008",type:"haut",name:"HOTEL",format:"7 rounds — RIR 30 s",exercises:["15 tractions prise large","15 tractions prise serrée","30 pompes alternées sur médecine-ball","20 dips lestés","8 muscle-ups"],note:"Objectif élite : 7 rounds < 25 min"},
  {id:9,num:"WOD #009",type:"haut",name:"INDIA",format:"30 min non-stop — cadence imposée",exercises:["Toutes les 90 s : 10 tractions + 15 pompes claquées + 12 dips","Entre les rounds : 20 abdos toes to bar"],note:"Aucun repos autorisé entre exercices du bloc"},
  {id:10,num:"WOD #010",type:"haut",name:"JULIET",format:"Pyramide 1→15→1 — SANS pause",exercises:["Pompes (x reps)","Tractions (x reps)","Dips lestés (x reps)","Muscle-ups (x reps ÷2)"],note:"Total = 450 reps. Objectif < 20 min"},
  {id:11,num:"WOD #011",type:"haut",name:"KILO",format:"6 rounds — RIR 30 s",exercises:["20 pompes instabilité swiss ball","15 tirages horizontaux TRX","15 pompes araignée","10 tractions L-sit","8 muscle-ups sur anneaux"],note:"Objectif : aucun échec technique"},
  {id:12,num:"WOD #012",type:"haut",name:"LIMA",format:"EMOM 30 min (alterner A/B/C)",exercises:["Minute A : 12 tractions + 6 muscle-ups","Minute B : 20 pompes claquées + 12 dips lestés","Minute C : 8 tractions L-sit + 10 dips ring"],note:"Si raté : double pénalité au tour suivant"},
  {id:13,num:"WOD #013",type:"haut",name:"MIKE",format:"5 rounds — RIR 90 s",exercises:["Max pompes en 90 s","Max tractions en 90 s","Max dips lestés en 90 s"],note:"Objectif élite : >50 pompes / >25 tractions / >30 dips par round"},
  {id:14,num:"WOD #014",type:"haut",name:"NOVEMBER",format:"For time — STRICT",exercises:["200 pompes","100 tractions","150 dips lestés","50 muscle-ups"],note:"Aucun repos imposé. Objectif élite < 25 min"},
  {id:15,num:"WOD #015",type:"haut",name:"OSCAR",format:"7 rounds — RIR 30 s",exercises:["15 pompes spartiates","12 tractions pliométriques","20 dips lents (5 s descente)","15 pompes prise inversée","8 muscle-ups"],note:"Descente contrôlée OBLIGATOIRE"},
  {id:16,num:"WOD #016",type:"haut",name:"PAPA",format:"AMRAP 25 min",exercises:["8 tractions","15 pompes diamant","12 dips lestés","20 élévations frontales KB","6 muscle-ups"],note:"Objectif élite : >14 rounds"},
  {id:17,num:"WOD #017",type:"haut",name:"QUEBEC",format:"6 rounds — SANS RIR",exercises:["30 pompes → 15 pieds hauts → 15 pieds bas (enchaîné sans arrêt)","15 tractions barre fixe","20 dips lestés"],note:"Zéro pause entre exercices du round"},
  {id:18,num:"WOD #018",type:"haut",name:"ROMEO",format:"8 rounds — RIR 30 s",exercises:["20 pompes sautées claquées","12 tractions australiennes lestées","10 muscle-ups","25 pompes normales"],note:"Porter un sac 10 kg pour les tractions"},
  {id:19,num:"WOD #019",type:"haut",name:"SIERRA",format:"TABATA x 6 exercices (5 min récup entre)",exercises:["Pompes claquées","Tractions","Dips lestés","Pompes araignée","Muscle-ups","Pompes pieds surélevés"],note:"20 s effort MAX / 5 s repos — niveau sélection"},
  {id:20,num:"WOD #020",type:"haut",name:"TANGO",format:"For time",exercises:["15-14-13-12-11-10-9-8-7-6-5-4-3-2-1 tractions","Même ladder pompes claquées x2","Muscle-ups (1 toutes les 3 séries de tractions)"],note:"Total 120 tractions + 240 pompes. Objectif < 20 min"},
  {id:21,num:"WOD #021",type:"haut",name:"UNIFORM",format:"7 rounds — SANS RIR",exercises:["20 pompes + 12 tractions + 10 dips lestés (enchaîné)","45 s gainage actif","15 pompes pieds surélevés"],note:"Chronométrer le temps total"},
  {id:22,num:"WOD #022",type:"haut",name:"VICTOR",format:"AMRAP 35 min",exercises:["6 tractions lentes (5 s montée / 5 s descente)","12 dips lents (5 s)","20 pompes normales","25 pompes sautées claquées","8 muscle-ups"],note:"Objectif élite : >14 rounds"},
  {id:23,num:"WOD #023",type:"haut",name:"WHISKEY",format:"5 rounds — RIR 60 s",exercises:["Max tractions strict en 2 min","Max pompes claquées en 2 min","Max dips lestés en 2 min"],note:"Objectif cumulé : >300 reps en 5 rounds"},
  {id:24,num:"WOD #024",type:"haut",name:"X-RAY",format:"For time",exercises:["8 rounds : 20 pompes + 8 tractions","Puis 8 rounds : 12 dips lestés + 10 muscle-ups"],note:"Objectif élite < 20 min"},
  {id:25,num:"WOD #025",type:"haut",name:"YANKEE",format:"7 rounds — RIR 30 s",exercises:["15 tractions prise large + 8 prise serrée (enchaîné)","25 pompes claquées","20 dips lestés (sac 10 kg)","5 muscle-ups"],note:"Gilet lesté 10 kg conseillé"},
  {id:26,num:"WOD #026",type:"haut",name:"ZULU",format:"EMOM 40 min",exercises:["Min 1 : 12 tractions","Min 2 : 20 pompes claquées","Min 3 : 12 dips lestés + 6 muscle-ups","Min 4 : 10 tractions L-sit","Min 5 : 15 pompes araignée"],note:"Si raté : 10 pompes pénalité hors temps"},
  {id:27,num:"WOD #027",type:"haut",name:"AJAX",format:"6 rounds — RIR 30 s",exercises:["12 tractions (KB 12 kg entre genoux)","25 pompes decline (pieds sur chaise)","20 dips lestés parallèles","45 s front hold bras tendus à 90°","8 muscle-ups"],note:"Niveau sélection force"},
  {id:28,num:"WOD #028",type:"haut",name:"BEAR",format:"8 rounds — SANS RIR",exercises:["15 pompes + 8 tractions + 12 dips lestés + 5 muscle-ups (enchaîné)"],note:"Aucun repos dans le round. Chronométrer"},
  {id:29,num:"WOD #029",type:"haut",name:"COBRA",format:"AMRAP 25 min",exercises:["10 tractions lentes (5 s montée / 5 s descente)","15 dips lents","20 pompes normales","8 muscle-ups"],note:"Objectif élite : >10 rounds"},
  {id:30,num:"WOD #030",type:"haut",name:"DRAGON",format:"For time — 15 rounds",exercises:["8 tractions + 15 pompes + 20 dips + 5 muscle-ups"],note:"Objectif élite < 20 min"},
  {id:31,num:"WOD #031",type:"haut",name:"EAGLE",format:"7 rounds — RIR 30 s",exercises:["20 pompes prise étroite","15 tractions prise large","12 tractions prise neutre","15 pompes prise écartée max amplitude","8 muscle-ups"],note:"Volume total : 700+ reps"},
  {id:32,num:"WOD #032",type:"haut",name:"FALCON",format:"TABATA (5 s repos) puis 6 rounds",exercises:["TABATA ultra-court : pompes claquées (20 s / 5 s)","Rounds sans RIR : 12 tractions + 15 dips lestés + 10 muscle-ups"],note:"Transition directe TABATA → rounds"},
  {id:33,num:"WOD #033",type:"haut",name:"GHOST",format:"6 rounds — RIR 90 s",exercises:["Max tractions strict (forme parfaite)","Max pompes à un bras (alterné)","Max dips lestés 15 kg"],note:"Carnet obligatoire : progression semaine/semaine"},
  {id:34,num:"WOD #034",type:"haut",name:"HAWK",format:"For time",exercises:["250 pompes","120 dips lestés","80 tractions","20 muscle-ups"],note:"Petits sets max 10. Objectif élite < 25 min"},
  {id:35,num:"WOD #035",type:"haut",name:"IRON",format:"7 rounds — RIR 30 s",exercises:["20 pompes pieds surélevés + 15 pompes normales (enchaîné sans arrêt)","10 tractions lentes (5 s)","15 dips lestés + 8 dips ring"],note:"Volume total par round : 53 reps"},
  {id:36,num:"WOD #036",type:"haut",name:"JAGUAR",format:"EMOM 35 min",exercises:["Min 1 : 15 pompes diamant","Min 2 : 10 tractions + 6 muscle-ups","Min 3 : 20 dips lestés","Min 4 : 12 pompes araignée","Min 5 : 8 tractions L-sit + 5 muscle-ups rings","Min 6 : repos (30 s max)","Min 7 : répéter"],note:"Si raté : recommencer la minute"},
  {id:37,num:"WOD #037",type:"haut",name:"KNIGHT",format:"5 rounds — RIR 30 s",exercises:["35 pompes + 25 pompes écartées + 20 pompes serrées (SANS pause)","12 tractions + 8 tractions L-sit","8 muscle-ups rings"],note:"155 reps haut du corps par round"},
  {id:38,num:"WOD #038",type:"haut",name:"LION",format:"For time — 30-25-20-15-10-5",exercises:["Pompes claquées (ladder)","Tractions (même ladder)","Muscle-ups (ladder ÷4)"],note:"Total 105 tractions + 210 pompes. Objectif < 18 min"},
  {id:39,num:"WOD #039",type:"haut",name:"MAMBA",format:"8 rounds — SANS RIR",exercises:["10 tractions + 15 pompes claquées + 8 muscle-ups (enchaîné — chrono)"],note:"Objectif élite : 8 rounds < 16 min"},
  {id:40,num:"WOD #040",type:"haut",name:"NINJA",format:"AMRAP 30 min",exercises:["12 pompes pieds surélevés","10 tractions + 6 tractions L-sit","20 dips lestés","12 pompes araignée","6 muscle-ups rings"],note:"Objectif élite : >12 rounds"},
  {id:41,num:"WOD #041",type:"haut",name:"OWL",format:"7 rounds — RIR 30 s",exercises:["25 pompes claquées + 15 isométriques 5 s (enchaîné)","15 tractions prise supination","20 dips lents (5 s descente)","8 muscle-ups"],note:"Qualité de mouvement prioritaire"},
  {id:42,num:"WOD #042",type:"haut",name:"PANTHER",format:"For time — 8 rounds",exercises:["15 tractions + 20 dips lestés + 25 pompes + 10 muscle-ups"],note:"Objectif élite < 20 min"},
  {id:43,num:"WOD #043",type:"haut",name:"RAPTOR",format:"TABATA 20 s / 5 s — 8 exercices",exercises:["Pompes claquées","Tractions","Dips lestés","Pompes araignée","Muscle-ups négatifs","Pompes normales","Tractions L-sit","Dips ring"],note:"5 s de repos seulement — sélection"},
  {id:44,num:"WOD #044",type:"haut",name:"SAVAGE",format:"6 rounds — RIR 30 s",exercises:["20 tractions australiennes lestées","25 pompes à un bras (alterné)","15 dips lestés 15 kg","12 tractions prise large lentes (5 s)","8 muscle-ups"],note:"Niveau sélection commando"},
  {id:45,num:"WOD #045",type:"haut",name:"TITAN",format:"For time",exercises:["15 rounds : 5 muscle-ups + 8 tractions + 15 pompes claquées + 30 dips"],note:"Total : 75 muscle-ups + 120 tractions + 225 pompes. Objectif < 30 min"},
  {id:46,num:"WOD #046",type:"haut",name:"ULTRA",format:"7 rounds — RIR 30 s",exercises:["20 pompes spartiates","12 tractions pliométriques","15 dips lestés + 6 dips ring","10 tractions lentes","8 muscle-ups"],note:"Porter gilet lesté 10 kg"},
  {id:47,num:"WOD #047",type:"haut",name:"VIPER",format:"AMRAP 30 min",exercises:["8 muscle-ups","12 tractions prise large","25 pompes claquées","20 dips lestés","8 tractions L-sit"],note:"Objectif élite : >14 rounds complets"},
  {id:48,num:"WOD #048",type:"haut",name:"WOLF",format:"8 rounds — SANS RIR",exercises:["20 pompes + 10 tractions + 12 dips lestés + 5 muscle-ups (enchaîné)"],note:"Chronométrer. Objectif < 20 min"},
  {id:49,num:"WOD #049",type:"haut",name:"XENON",format:"For time — Élite Angie",exercises:["75 tractions","75 dips lestés","150 pompes claquées","50 muscle-ups"],note:"Finir chaque exercice avant de passer. Objectif < 25 min"},
  {id:50,num:"WOD #050",type:"haut",name:"ZEUS",format:"EMOM 40 min",exercises:["Min 1 : 10 tractions","Min 2 : 20 pompes claquées","Min 3 : 12 dips lestés + 6 muscle-ups","Min 4 : 8 tractions L-sit","Min 5 : 15 pompes araignée","Min 6 : 5 muscle-ups rings","Min 7 : 10 dips ring","Min 8 : repos (30 s)"],note:"400+ reps en 40 min. Niveau sélection"},

  // ── BAS DU CORPS ÉLITE (51-100) ─────────────────────────────────────────────
  {id:51,num:"WOD #051",type:"bas",name:"ALPHA-B",format:"7 rounds — SANS RIR",exercises:["30 squats sautés","20 fentes sautées alternées","15 squats bulgares lestés/jambe","12 pistol squats","45 s wall sit lestée (sac 10 kg)","10 squat jumps profonds"],note:"Aucun repos entre les exercices"},
  {id:52,num:"WOD #052",type:"bas",name:"BRAVO-B",format:"AMRAP 30 min",exercises:["20 squats","12 box jumps hauteur max","15 fentes latérales lestées","12 squat jumps","25 montées de genoux sautées","8 pistol squats"],note:"Objectif élite : >14 rounds"},
  {id:53,num:"WOD #053",type:"bas",name:"CHARLIE-B",format:"6 rounds — RIR 30 s",exercises:["15 squats bulgares lestés/jambe","25 fentes sautées","20 pontés fessiers lestés","12 squat jumps (atterrissage 3 s)","45 s gainage latéral"],note:"Charge : sac 15 kg minimum"},
  {id:54,num:"WOD #054",type:"bas",name:"DELTA-B",format:"TABATA 10 rounds (20 s / 5 s)",exercises:["Squats sautés MAX","Fentes sautées alternées MAX","Box jumps MAX","Mountain climbers rapides","Squat sumo sautés"],note:"5 s repos seulement — explosivité totale"},
  {id:55,num:"WOD #055",type:"bas",name:"ECHO-B",format:"5 rounds — SANS RIR",exercises:["Max squats en 90 s","30 s repos","Max fentes sautées en 90 s","30 s repos","Max squat jumps en 90 s","30 s repos"],note:"Objectif élite : >60 squats / >40 fentes / >30 squat jumps"},
  {id:56,num:"WOD #056",type:"bas",name:"FOXTROT-B",format:"For time — 30-20-15-9",exercises:["Squat jumps profonds","Fentes avant alternées lestées","Box jumps hauteur max"],note:"Objectif élite < 10 min"},
  {id:57,num:"WOD #057",type:"bas",name:"GOLF-B",format:"7 rounds — SANS RIR",exercises:["20 squats + 15 pulsés + 10 sautés (sans arrêt)","15 fentes bulgares lestées/jambe","45 s wall sit lesté"],note:"Charge minimale : sac 10 kg"},
  {id:58,num:"WOD #058",type:"bas",name:"HOTEL-B",format:"8 rounds — RIR 30 s",exercises:["25 squats","15 box jumps hauteur max","20 fentes sautées","12 squat sumo lestés"],note:"Objectif élite : 8 rounds < 20 min"},
  {id:59,num:"WOD #059",type:"bas",name:"INDIA-B",format:"EMOM 30 min (A/B alternés)",exercises:["Minute A : 15 squat jumps + 12 box jumps","Minute B : 15 fentes/jambe + 25 montées genoux sautées"],note:"Maintenir la cadence jusqu'au bout"},
  {id:60,num:"WOD #060",type:"bas",name:"JULIET-B",format:"Pyramide 1→15→1 SANS pause",exercises:["Squat jumps (x reps)","Fentes sautées (x2)","Box jumps (x reps)"],note:"Total 225 squat jumps + 450 fentes + 225 box jumps"},
  {id:61,num:"WOD #061",type:"bas",name:"KILO-B",format:"6 rounds — RIR 30 s",exercises:["20 sumo squats lestés","15 squat sur une jambe (libre)/jambe","25 fentes marchées lestées","20 pontés fessiers unilatéraux/jambe"],note:"Charge : sac 15 kg ou KB 20 kg"},
  {id:62,num:"WOD #062",type:"bas",name:"LIMA-B",format:"AMRAP 25 min",exercises:["12 squat jumps","12 fentes bulgares lestées/jambe","15 step-ups hauts lestés/jambe","25 squats sautés"],note:"Objectif élite : >12 rounds"},
  {id:63,num:"WOD #063",type:"bas",name:"MIKE-B",format:"5 rounds — RIR 60 s",exercises:["Max squats sautés en 2 min","Max fentes sautées en 2 min","Max box jumps en 2 min"],note:"Objectif cumulé élite : >500 reps en 5 rounds"},
  {id:64,num:"WOD #064",type:"bas",name:"NOVEMBER-B",format:"For time",exercises:["200 squats","100 fentes avant alternées lestées","100 fentes latérales","50 squat jumps","25 pistol squats"],note:"Objectif élite < 20 min"},
  {id:65,num:"WOD #065",type:"bas",name:"OSCAR-B",format:"7 rounds — RIR 30 s",exercises:["15 squats bulgares lestés/jambe (3 s descente)","12 squat sautés lents (4 s descente)","20 pontés fessiers glissés lestés","25 step-ups genou haut lestés"],note:"Volume extrême — jambes de feu"},
  {id:66,num:"WOD #066",type:"bas",name:"PAPA-B",format:"6 rounds — RIR 30 s",exercises:["25 fentes marchées lestées","20 squats sautés","15 squat sumo lents lestés","10 pistol squats libres/jambe"],note:"Pistol squats : forme parfaite obligatoire"},
  {id:67,num:"WOD #067",type:"bas",name:"QUEBEC-B",format:"7 rounds — SANS RIR",exercises:["20 squats + 15 pulsés + 10 sautés (enchaîné)","15 fentes latérales/côté lestées","12 box jumps"],note:"Zéro arrêt dans le round"},
  {id:68,num:"WOD #068",type:"bas",name:"ROMEO-B",format:"AMRAP 30 min",exercises:["12 squat jumps profonds","15 fentes bulgares lestées/jambe","20 box jumps","25 squat sumo sautés"],note:"Objectif élite : >12 rounds"},
  {id:69,num:"WOD #069",type:"bas",name:"SIERRA-B",format:"8 rounds — RIR 30 s",exercises:["12 pistol squats (6/jambe)","20 fentes sautées lestées","15 squat jumps","25 montées de genoux sautées"],note:"Charge sac 10 kg pour les fentes"},
  {id:70,num:"WOD #070",type:"bas",name:"TANGO-B",format:"For time — 15 rounds",exercises:["8 squat jumps + 8 box jumps + 8 fentes/jambe"],note:"240 reps total. Objectif élite < 15 min"},
  {id:71,num:"WOD #071",type:"bas",name:"UNIFORM-B",format:"7 rounds — RIR 30 s",exercises:["25 squats","20 fentes marchées lestées","12 box jumps hauteur max","45 s wall sit lesté"],note:"Porter gilet lesté 10 kg"},
  {id:72,num:"WOD #072",type:"bas",name:"VICTOR-B",format:"EMOM 35 min",exercises:["Min 1 : 20 squats sautés","Min 2 : 15 fentes bulgares lestées/jambe","Min 3 : 12 box jumps","Min 4 : 25 step-ups lestés","Min 5 : 15 squat sumo sautés","Min 6 : repos (30 s)","Min 7 : répéter"],note:"Si raté : recommencer la minute"},
  {id:73,num:"WOD #073",type:"bas",name:"WHISKEY-B",format:"5 rounds — RIR 60 s",exercises:["Max fentes sautées en 2 min","Max box jumps en 2 min","Max squats sautés en 2 min"],note:"Objectif élite : >500 reps cumulés"},
  {id:74,num:"WOD #074",type:"bas",name:"X-RAY-B",format:"For time",exercises:["50 squat jumps","30 box jumps hauteur max","40 fentes bulgares lestées (20/jambe)","25 pistol squats (libre)","40 step-ups hauts lestés"],note:"Objectif élite < 15 min"},
  {id:75,num:"WOD #075",type:"bas",name:"YANKEE-B",format:"7 rounds — RIR 30 s",exercises:["15 squat sumo pulsés lestés","20 fentes latérales glissées lestées","12 squat sautés claqués","25 montées de genoux sautées"],note:"Charge 10 kg minimum tout le long"},
  {id:76,num:"WOD #076",type:"bas",name:"ZULU-B",format:"TABATA 6 exercices (5 s repos)",exercises:["Squats sautés","Fentes sautées lestées","Box jumps","Mountain climbers","Squat sumo sauté","Pistol squats alternés"],note:"5 s repos seulement — aucune concession"},
  {id:77,num:"WOD #077",type:"bas",name:"AJAX-B",format:"6 rounds — RIR 30 s",exercises:["30 fentes marchées lestées + 15 sautées (enchaîné)","20 pontés fessiers lestés + 12 unilatéraux/jambe","15 box jumps hauteur max"],note:"Charge : sac 15 kg ou KB"},
  {id:78,num:"WOD #078",type:"bas",name:"BEAR-B",format:"8 rounds — SANS RIR",exercises:["20 squats + 12 pulsés + 8 sautés (sans arrêt)"],note:"Chronométrer. Gilet lesté 10 kg"},
  {id:79,num:"WOD #079",type:"bas",name:"COBRA-B",format:"AMRAP 30 min",exercises:["12 squat jumps","15 fentes avant lestées/jambe","20 step-ups hauts lestés/jambe","25 squats sumo sautés"],note:"Objectif élite : >12 rounds"},
  {id:80,num:"WOD #080",type:"bas",name:"DRAGON-B",format:"For time — 8 rounds",exercises:["12 pistol squats + 20 box jumps + 25 fentes sautées lestées + 35 squats"],note:"Objectif élite < 20 min"},
  {id:81,num:"WOD #081",type:"bas",name:"EAGLE-B",format:"7 rounds — RIR 30 s",exercises:["15 squat bulgares lestés (4 s descente)/jambe","20 squats sautés","12 squat sumo lestés 20 kg","25 fentes marchées lestées"],note:"Force + explosivité : combo élite"},
  {id:82,num:"WOD #082",type:"bas",name:"FALCON-B",format:"TABATA (5 s repos) puis 6 rounds",exercises:["TABATA : squat jumps (20 s / 5 s)","Rounds sans RIR : 12 fentes bulgares lestées + 15 box jumps + 20 squat sumo sautés"],note:"Transition directe TABATA → rounds"},
  {id:83,num:"WOD #083",type:"bas",name:"GHOST-B",format:"6 rounds — RIR 90 s",exercises:["Max squat jumps en 2 min (gilet lesté)","Max pistol squats en 2 min","Max fentes sautées lestées en 2 min"],note:"Objectif élite : >300 reps cumulés par round"},
  {id:84,num:"WOD #084",type:"bas",name:"HAWK-B",format:"For time",exercises:["300 squats lestés","150 fentes alternées lestées","75 squat jumps","25 pistol squats"],note:"Objectif élite < 20 min"},
  {id:85,num:"WOD #085",type:"bas",name:"IRON-B",format:"7 rounds — RIR 30 s",exercises:["20 box jumps + 12 step-down lestés (enchaîné)","15 squat bulgares lestés/jambe","25 squats sumo pulsés lestés"],note:"Gilet lesté 10 kg ou sac"},
  {id:86,num:"WOD #086",type:"bas",name:"JAGUAR-B",format:"EMOM 35 min",exercises:["Min 1 : 20 squat jumps","Min 2 : 15 box jumps","Min 3 : 12 pistol squats","Min 4 : 25 fentes marchées lestées","Min 5 : repos (30 s)"],note:"Charge progressive : +2 kg chaque semaine"},
  {id:87,num:"WOD #087",type:"bas",name:"KNIGHT-B",format:"5 rounds — SANS RIR",exercises:["40 fentes sautées lestées + 25 squat jumps + 15 box jumps hauteur max (sans repos)"],note:"80 reps par round minimum — chrono"},
  {id:88,num:"WOD #088",type:"bas",name:"LION-B",format:"For time — 30-20-15-9",exercises:["Fentes sautées lestées","Squat jumps","Box jumps hauteur max"],note:"Objectif élite < 12 min"},
  {id:89,num:"WOD #089",type:"bas",name:"MAMBA-B",format:"8 rounds — SANS RIR",exercises:["12 squat bulgares lestés/jambe + 20 squat sautés + 10 box jumps (enchaîné)"],note:"Objectif élite : 8 rounds < 20 min"},
  {id:90,num:"WOD #090",type:"bas",name:"NINJA-B",format:"AMRAP 30 min",exercises:["10 pistol squats (5/jambe)","15 fentes bulgares lestées/jambe","12 box jumps hauteur max","25 squats sautés lestés"],note:"Objectif élite : >12 rounds"},
  {id:91,num:"WOD #091",type:"bas",name:"OWL-B",format:"7 rounds — RIR 30 s",exercises:["25 squats sautés lestés","15 squat sumo lestés 20 kg","12 pistol squats","20 fentes latérales lestées/côté"],note:"Charge : gilet 10 kg ou sac 15 kg"},
  {id:92,num:"WOD #092",type:"bas",name:"PANTHER-B",format:"For time — 8 rounds",exercises:["20 box jumps + 15 fentes bulgares lestées/jambe + 25 squats sautés + 12 pistol squats"],note:"Objectif élite < 20 min"},
  {id:93,num:"WOD #093",type:"bas",name:"RAPTOR-B",format:"TABATA 6 exercices (5 s repos)",exercises:["Squat jumps MAX","Fentes sautées lestées MAX","Box jumps MAX","Mountain climbers MAX","Squat sumo sauté MAX","Pistol squats alternés MAX"],note:"Intensité maximale — 5 s de repos seulement"},
  {id:94,num:"WOD #094",type:"bas",name:"SAVAGE-B",format:"6 rounds — RIR 30 s",exercises:["20 squats bulgares lestés/jambe","25 fentes marchées lestées","15 box jumps profonds","12 pistol squats libres"],note:"Charge 15 kg minimum — niveau sélection"},
  {id:95,num:"WOD #095",type:"bas",name:"TITAN-B",format:"For time",exercises:["15 rounds : 6 pistol squats/jambe + 12 box jumps + 20 squat sautés lestés"],note:"Objectif élite < 25 min"},
  {id:96,num:"WOD #096",type:"bas",name:"ULTRA-B",format:"7 rounds — RIR 30 s",exercises:["20 fentes sautées lestées + 12 squat jumps + 8 box jumps hauts (enchaîné)"],note:"Charge : gilet 10 kg ou sac"},
  {id:97,num:"WOD #097",type:"bas",name:"VIPER-B",format:"AMRAP 30 min",exercises:["12 box jumps hauteur max","15 squat bulgares lestés/jambe","20 squats sautés","25 fentes marchées lestées"],note:"Objectif élite : >12 rounds"},
  {id:98,num:"WOD #098",type:"bas",name:"WOLF-B",format:"8 rounds — SANS RIR",exercises:["20 squats + 12 sautés + 10 box jumps + 6 pistol squats (enchaîné)"],note:"Chronométrer total. Gilet lesté"},
  {id:99,num:"WOD #099",type:"bas",name:"XENON-B",format:"For time",exercises:["75 box jumps","150 fentes alternées lestées","75 squat jumps","150 squats lestés","25 pistol squats"],note:"Objectif élite < 20 min"},
  {id:100,num:"WOD #100",type:"bas",name:"ZEUS-B",format:"EMOM 40 min",exercises:["Min 1 : 15 box jumps","Min 2 : 20 squat sautés lestés","Min 3 : 12 pistol squats","Min 4 : 25 fentes lestées","Min 5 : 15 squat bulgares lestés/jambe","Min 6 : repos (30 s)","Min 7 : 12 squat sumo sautés","Min 8 : repos (30 s)"],note:"400+ reps en 40 min. Niveau sélection"},

  // ── CORPS COMPLET ÉLITE (101-150) ───────────────────────────────────────────
  {id:101,num:"WOD #101",type:"complet",name:"ALPHA-C",format:"7 rounds — SANS RIR",exercises:["15 burpees sautés claqués","20 pompes","25 squats lestés","12 tractions","20 fentes sautées","25 abdos toes to bar"],note:"Aucun repos inter-exercices"},
  {id:102,num:"WOD #102",type:"complet",name:"BRAVO-C",format:"AMRAP 35 min",exercises:["8 burpee-tractions pliométriques","12 pompes claquées","20 squat jumps lestés","25 abdos toes to bar","30 box jumps","8 muscle-ups"],note:"Objectif élite : >12 rounds"},
  {id:103,num:"WOD #103",type:"complet",name:"CHARLIE-C",format:"6 rounds — RIR 30 s",exercises:["15 clean and jerk KB 20 kg","20 pompes araignée","15 squat-press lestés","12 tractions","25 fentes marchées lestées","20 abdos chandelles"],note:"Volume total : 100+ reps/round"},
  {id:104,num:"WOD #104",type:"complet",name:"DELTA-C",format:"TABATA 6 exercices (5 s repos)",exercises:["Burpees MAX","Pompes claquées MAX","Squat jumps MAX","Tractions MAX","Mountain climbers MAX","Muscle-ups MAX"],note:"5 s repos seulement — élite sélection"},
  {id:105,num:"WOD #105",type:"complet",name:"ECHO-C",format:"5 rounds — SANS RIR",exercises:["Max burpees en 2 min","30 s repos","Max tractions en 90 s","30 s repos","Max fentes sautées lestées en 2 min","30 s repos"],note:"Objectif élite : >20 burpees / >15 tractions / >30 fentes"},
  {id:106,num:"WOD #106",type:"complet",name:"FOXTROT-C",format:"For time — 30-20-15-9",exercises:["Burpee-tractions","Squat jumps lestés","Dips lestés","Muscle-ups"],note:"Objectif élite < 12 min"},
  {id:107,num:"WOD #107",type:"complet",name:"GOLF-C",format:"8 rounds — RIR 30 s",exercises:["12 burpees","20 pompes","15 box jumps","12 tractions","45 s gainage latéral/côté","8 muscle-ups"],note:"Objectif élite : 8 rounds < 25 min"},
  {id:108,num:"WOD #108",type:"complet",name:"HOTEL-C",format:"7 rounds — RIR 30 s",exercises:["10 muscle-ups","20 squat jumps lestés","25 pompes claquées","15 fentes bulgares lestées/jambe"],note:"Niveau sélection forces spéciales"},
  {id:109,num:"WOD #109",type:"complet",name:"INDIA-C",format:"EMOM 30 min",exercises:["Min 1 : 8 burpee-tractions","Min 2 : 15 squat jumps + 12 pompes","Min 3 : 15 fentes + 10 tractions","Min 4 : 20 abdos + 12 dips lestés","Min 5 : 5 muscle-ups + 10 squat jumps"],note:"Si raté : 10 burpees pénalité"},
  {id:110,num:"WOD #110",type:"complet",name:"JULIET-C",format:"Pyramide 1→10→1 SANS pause",exercises:["Burpees (x reps)","Tractions (x reps)","Squat jumps lestés (x reps)","Pompes claquées (x reps)","Muscle-ups (x reps ÷2)"],note:"Total 100 reps de chaque. Objectif < 20 min"},
  {id:111,num:"WOD #111",type:"complet",name:"KILO-C",format:"6 rounds — RIR 30 s",exercises:["15 KB swing américain 24 kg","12 KB goblet squat 24 kg","10 KB snatch/bras","12 pompes sur KB","20 abdos crunch KB"],note:"KB 24 kg minimum — niveau confirmé élite"},
  {id:112,num:"WOD #112",type:"complet",name:"LIMA-C",format:"AMRAP 30 min",exercises:["10 burpee box jump","12 tractions prise large","20 squat sautés lestés","15 dips lestés","25 fentes marchées lestées","8 muscle-ups"],note:"Objectif élite : >10 rounds"},
  {id:113,num:"WOD #113",type:"complet",name:"MIKE-C",format:"For time",exercises:["15 rounds : 12 pompes + 12 squats lestés + 12 abdos crunch"],note:"216 reps par exercice. Objectif < 15 min"},
  {id:114,num:"WOD #114",type:"complet",name:"NOVEMBER-C",format:"7 rounds — RIR 30 s",exercises:["20 pompes pieds surélevés","12 squat-tractions enchainés","20 box jumps","15 abdos toes to bar","12 dips lestés","8 muscle-ups"],note:"Volume extrême — 87 reps/round"},
  {id:115,num:"WOD #115",type:"complet",name:"OSCAR-C",format:"8 rounds — RIR 30 s",exercises:["12 burpees claqués","15 tractions prise neutre","20 squat sumo sautés lestés","25 pompes normales","45 s gainage dorsal actif"],note:"Objectif élite : 8 rounds < 22 min"},
  {id:116,num:"WOD #116",type:"complet",name:"PAPA-C",format:"For time",exercises:["75 burpees","75 tractions","150 squats lestés","75 dips lestés","75 pompes claquées","25 muscle-ups"],note:"Objectif élite < 30 min"},
  {id:117,num:"WOD #117",type:"complet",name:"QUEBEC-C",format:"7 rounds — SANS RIR",exercises:["20 pompes + 12 squat jumps lestés + 10 tractions + 8 burpees + 6 muscle-ups (enchaîné)"],note:"56 reps/round — zéro pause"},
  {id:118,num:"WOD #118",type:"complet",name:"ROMEO-C",format:"AMRAP 30 min",exercises:["8 muscle-ups","12 squat jumps lestés","15 pompes araignée","20 fentes sautées lestées","25 abdos toes to bar"],note:"Objectif élite : >12 rounds"},
  {id:119,num:"WOD #119",type:"complet",name:"SIERRA-C",format:"7 rounds — RIR 30 s",exercises:["15 tirages dos TRX lestés","20 fentes bulgares lestées/jambe","12 pompes claquées + 8 diamant","10 squat-traction barre basse lestée","8 muscle-ups"],note:"Porter gilet lesté 10 kg"},
  {id:120,num:"WOD #120",type:"complet",name:"TANGO-C",format:"EMOM 35 min",exercises:["Min 1 : 10 burpee-tractions","Min 2 : 20 squat jumps lestés","Min 3 : 15 pompes claquées","Min 4 : 12 tractions","Min 5 : 20 abdos + 12 fentes/jambe","Min 6 : 6 muscle-ups","Min 7 : repos (30 s)"],note:"Cadence elite — aucune minute ratée"},
  {id:121,num:"WOD #121",type:"complet",name:"UNIFORM-C",format:"For time",exercises:["8 rounds : 6 tractions + 12 pompes + 20 squats lestés","Puis 8 rounds : 12 burpees + 12 box jumps + 12 dips lestés"],note:"Objectif élite < 20 min"},
  {id:122,num:"WOD #122",type:"complet",name:"VICTOR-C",format:"6 rounds — RIR 30 s",exercises:["20 squat-press lestés 15 kg","15 tractions","20 pompes pieds surélevés","12 squat jumps","25 abdos croisés lestés"],note:"Volume + charge = niveau sélection"},
  {id:123,num:"WOD #123",type:"complet",name:"WHISKEY-C",format:"5 rounds — RIR 60 s",exercises:["Max burpees en 2 min","Max tractions en 90 s","Max squat jumps lestés en 2 min","Max pompes claquées en 90 s"],note:"Objectif élite : >400 reps cumulés"},
  {id:124,num:"WOD #124",type:"complet",name:"X-RAY-C",format:"AMRAP 30 min",exercises:["6 burpee-tractions pliométriques","12 dips lestés","20 squats bulgares lestés","25 pompes claquées","8 muscle-ups"],note:"Objectif élite : >12 rounds"},
  {id:125,num:"WOD #125",type:"complet",name:"YANKEE-C",format:"7 rounds — SANS RIR",exercises:["12 burpees","12 tractions","12 fentes sautées lestées/jambe","12 pompes araignée","12 squat jumps lestés","12 abdos toes to bar","6 muscle-ups"],note:"84 reps/round — zéro pause"},
  {id:126,num:"WOD #126",type:"complet",name:"ZULU-C",format:"For time",exercises:["200 pompes claquées","150 squat jumps lestés","100 tractions","75 box jumps","50 burpee-tractions","25 muscle-ups"],note:"Objectif élite < 35 min"},
  {id:127,num:"WOD #127",type:"complet",name:"AJAX-C",format:"6 rounds — RIR 30 s",exercises:["12 KB swing 24 kg","12 squat-press KB 20 kg","10 KB snatch/bras","10 burpees sur KB","20 abdos crunch lestés"],note:"KB lourd — niveau élite"},
  {id:128,num:"WOD #128",type:"complet",name:"BEAR-C",format:"8 rounds — SANS RIR",exercises:["20 pompes + 12 squat jumps lestés + 10 tractions + 8 burpees + 6 muscle-ups (enchaîné)"],note:"56 reps/round — chronométrer"},
  {id:129,num:"WOD #129",type:"complet",name:"COBRA-C",format:"AMRAP 35 min",exercises:["10 muscle-ups","15 fentes bulgares lestées/jambe","20 pompes claquées","25 squats sautés lestés","30 abdos toes to bar"],note:"Objectif élite : >10 rounds"},
  {id:130,num:"WOD #130",type:"complet",name:"DRAGON-C",format:"For time — 8 rounds",exercises:["12 burpee box jumps + 12 tractions + 20 fentes lestées + 20 pompes + 25 squats lestés"],note:"Objectif élite < 20 min"},
  {id:131,num:"WOD #131",type:"complet",name:"EAGLE-C",format:"7 rounds — RIR 30 s",exercises:["15 squat-tirages barre basse lestés","20 pompes pieds surélevés","12 squat jumps lestés","10 tractions lentes (5 s)","25 abdos croisés lestés","6 muscle-ups"],note:"Force + endurance : 88 reps/round"},
  {id:132,num:"WOD #132",type:"complet",name:"FALCON-C",format:"EMOM 40 min",exercises:["Min 1 : 8 burpee-tractions","Min 2 : 15 squat jumps lestés","Min 3 : 12 dips lestés + 6 muscle-ups","Min 4 : 20 pompes araignée","Min 5 : 12 box jumps + 12 fentes lestées","Min 6 : 8 muscle-ups rings","Min 7 : 15 squat sautés","Min 8 : repos (30 s)"],note:"Si raté : 10 burpees pénalité hors EMOM"},
  {id:133,num:"WOD #133",type:"complet",name:"GHOST-C",format:"6 rounds — RIR 60 s",exercises:["Max burpees en 2 min","Max tractions en 90 s","Max squat jumps lestés en 2 min","Max pompes claquées en 90 s"],note:"Objectif élite total : >500 reps sur 6 rounds"},
  {id:134,num:"WOD #134",type:"complet",name:"HAWK-C",format:"For time",exercises:["150 burpees","150 tractions","150 squat jumps lestés","150 dips lestés","150 pompes claquées","50 muscle-ups"],note:"Objectif élite < 45 min — niveau légende"},
  {id:135,num:"WOD #135",type:"complet",name:"IRON-C",format:"7 rounds — SANS RIR",exercises:["15 pompes + 12 squat bulgares lestés/jambe + 10 tractions + 8 burpees + 25 abdos (enchaîné)"],note:"70 reps/round — zéro pause"},
  {id:136,num:"WOD #136",type:"complet",name:"JAGUAR-C",format:"TABATA 8 exercices (5 s repos)",exercises:["Burpees","Tractions","Squat jumps lestés","Pompes","Box jumps","Dips lestés","Muscle-ups","Mountain climbers"],note:"5 s repos — 8 exercices de suite — élite"},
  {id:137,num:"WOD #137",type:"complet",name:"KNIGHT-C",format:"5 rounds — RIR 30 s",exercises:["25 pompes + 25 squats lestés + 25 abdos + 20 tractions + 20 fentes + 12 burpees + 8 muscle-ups (SANS pause)"],note:"135 reps/round — niveau sélection"],
  {id:138,num:"WOD #138",type:"complet",name:"LION-C",format:"For time — ladder 15→1",exercises:["Burpees + tractions + squat jumps lestés + pompes (décroissants simultanément)"],note:"Total 120 de chaque. Objectif < 20 min"},
  {id:139,num:"WOD #139",type:"complet",name:"MAMBA-C",format:"8 rounds — SANS RIR",exercises:["10 burpee-tractions + 15 squat jumps lestés + 20 pompes + 12 dips lestés + 6 muscle-ups (enchaîné)"],note:"63 reps/round. Objectif : 8 rounds < 20 min"},
  {id:140,num:"WOD #140",type:"complet",name:"NINJA-C",format:"AMRAP 30 min",exercises:["8 muscle-ups","12 fentes sautées lestées/jambe","15 pompes araignée","20 abdos toes to bar","10 squat jumps lestés"],note:"Objectif élite : >12 rounds"},
  {id:141,num:"WOD #141",type:"complet",name:"OWL-C",format:"7 rounds — SANS RIR",exercises:["25 pompes + 20 squats lestés + 12 burpees + 10 tractions + 6 muscle-ups (enchaîné)"],note:"73 reps/round — chronométrer"},
  {id:142,num:"WOD #142",type:"complet",name:"PANTHER-C",format:"For time",exercises:["15 rounds : 6 tractions + 12 pompes + 20 squats lestés + 25 abdos + 6 muscle-ups"],note:"Objectif élite < 25 min"},
  {id:143,num:"WOD #143",type:"complet",name:"RAPTOR-C",format:"EMOM 35 min",exercises:["Min 1 : 10 burpees","Min 2 : 15 pompes claquées","Min 3 : 12 tractions","Min 4 : 20 squat jumps lestés","Min 5 : 12 dips lestés","Min 6 : 20 fentes sautées lestées","Min 7 : repos (30 s)"],note:"Si raté : 8 burpees pénalité"},
  {id:144,num:"WOD #144",type:"complet",name:"SAVAGE-C",format:"6 rounds — RIR 30 s",exercises:["20 KB swing 24 kg","12 squat-press KB 20 kg","10 KB snatch/bras","12 tractions","20 fentes sautées lestées","8 muscle-ups"],note:"Niveau élite KB + poids corps"},
  {id:145,num:"WOD #145",type:"complet",name:"TITAN-C",format:"For time",exercises:["8 rounds : 12 burpee-tractions + 20 box jumps + 25 pompes + 25 squats sautés lestés + 8 muscle-ups"],note:"Objectif élite < 25 min"},
  {id:146,num:"WOD #146",type:"complet",name:"ULTRA-C",format:"7 rounds — SANS RIR",exercises:["12 burpees claqués + 15 tractions + 20 squat jumps lestés + 25 pompes + 8 muscle-ups (enchaîné)"],note:"80 reps/round — zéro concession"},
  {id:147,num:"WOD #147",type:"complet",name:"VIPER-C",format:"AMRAP 30 min",exercises:["10 muscle-ups","20 fentes bulgares lestées/jambe","15 pompes claquées","25 squats sautés lestés","12 tractions"],note:"Objectif élite : >12 rounds"},
  {id:148,num:"WOD #148",type:"complet",name:"WOLF-C",format:"8 rounds — SANS RIR",exercises:["20 burpees + 15 tractions + 20 pompes + 12 squat jumps lestés + 25 abdos (enchaîné)"],note:"92 reps/round. Objectif : 8 rounds < 25 min"},
  {id:149,num:"WOD #149",type:"complet",name:"XENON-C",format:"For time",exercises:["150 burpees","150 tractions","150 fentes lestées","150 pompes claquées","150 squat jumps lestés","50 muscle-ups"],note:"Objectif élite < 50 min — testez vos limites"],
  {id:150,num:"WOD #150",type:"complet",name:"ZEUS-C",format:"EMOM 45 min",exercises:["Min 1 : 6 burpee-tractions","Min 2 : 12 pompes claquées","Min 3 : 15 squat jumps lestés","Min 4 : 10 tractions","Min 5 : 12 dips lestés","Min 6 : 20 fentes sautées lestées","Min 7 : 8 muscle-ups","Min 8 : 20 abdos toes to bar","Min 9 : repos (30 s)"],note:"500+ reps en 45 min. Niveau ULTIME"},
];


const CHALLENGES = [
  {id:"c1",name:"300 WARRIOR ÉLITE",desc:"Version élite du 300 — avec charge",target:"30 tractions · 60 box jumps hauts · 60 pompes claquées · 60 fentes lestées (30/jambe) · 30 tractions · 60 pompes · 60 abdos toes to bar · 60 squats lestés",tip:"Objectif élite < 18 min. Porter gilet 10 kg"},
  {id:"c2",name:"MURPH LESTÉ",desc:"Le classique des forces spéciales — AVEC gilet",target:"1 mile run (gilet 10 kg) · 100 tractions · 200 pompes · 300 squats · 1 mile run (gilet)",tip:"Objectif élite < 35 min avec gilet 10 kg"},
  {id:"c3",name:"CINDY ÉLITE",desc:"AMRAP 30 min — version longue",target:"5 tractions · 10 pompes claquées · 15 squat jumps (répéter)",tip:"Objectif élite : >30 rounds en 30 min"},
  {id:"c4",name:"FRAN ÉLITE",desc:"For time — 30-20-10",target:"Tractions · Pompes claquées · Muscle-ups",tip:"Objectif élite < 6 min"},
  {id:"c5",name:"ANGIE ÉLITE",desc:"For time — version lestée",target:"100 tractions · 100 dips lestés · 100 pompes claquées · 100 abdos toes to bar · 50 muscle-ups",tip:"Objectif élite < 20 min"},
  {id:"c6",name:"BARBARA ÉLITE",desc:"5 rounds — RIR 2 min strict",target:"25 tractions · 40 pompes claquées · 50 abdos toes to bar · 60 squats lestés",tip:"Objectif élite < 8 min/round"},
  {id:"c7",name:"CHELSEA ÉLITE",desc:"EMOM 40 min — version augmentée",target:"6 tractions · 12 pompes claquées · 20 squat jumps (toutes les minutes)",tip:"Si tu rates une minute : tu arrêtes et tu notes le round"},
  {id:"c8",name:"LE CENTURION ÉLITE",desc:"100 burpee-tractions + finisher",target:"100 burpee-tractions · immédiatement 50 dips · 50 pompes claquées",tip:"Objectif élite < 18 min — aucune pause"},
  {id:"c9",name:"LE PLONGEOIR ÉLITE",desc:"Ladder décroissante lestée",target:"60-50-40-30-20-10 : pompes claquées · squat jumps lestés · abdos toes to bar · box jumps",tip:"Objectif élite < 20 min"},
  {id:"c10",name:"L'ESCALIER ÉLITE",desc:"Ladder 1→25 tractions — avec poids",target:"1 traction lestée, 2 tractions lestées... jusqu'à 25",tip:"Total 325 tractions lestées. Objectif élite < 35 min"},
  {id:"c11",name:"LE GRIMPEUR ÉLITE",desc:"Ladder 1→12 lestée",target:"1→12 de burpees + tractions + pompes + squat jumps lestés",tip:"Total 78 reps de chaque. Gilet 10 kg. Objectif < 20 min"},
  {id:"c12",name:"THOR ÉLITE",desc:"8 rounds pour temps",target:"15 tractions · 20 pompes sautées claquées · 25 squat jumps lestés · 30 abdos toes to bar · 35 squats lestés",tip:"RIR 30 s MAX. Objectif élite < 25 min"},
  {id:"c13",name:"HÉRACLÈS ÉLITE",desc:"5 rounds effort maximal absolu",target:"Max tractions strict · 30 s repos · max pompes claquées · 30 s repos · max dips lestés",tip:"Objectif élite total : >500 reps sur 5 rounds"},
  {id:"c14",name:"L'AMAZONE ÉLITE",desc:"AMRAP 45 min lestée",target:"12 burpees · 20 tractions · 25 pompes claquées · 30 squats sautés lestés",tip:"Objectif élite : >12 rounds complets"},
  {id:"c15",name:"LE TITAN ÉLITE",desc:"For time — opération terrain simulée",target:"2 km run · 75 tractions · 150 pompes · 200 squats lestés · 2 km run",tip:"Objectif élite < 30 min — gilet 10 kg"},
  {id:"c16",name:"SPARTAN 50",desc:"50 min AMRAP style spartan race",target:"40 burpees · 40 tractions · 40 box jumps hauts · 40 pompes claquées · 40 fentes sautées lestées",tip:"Objectif élite : >8 rounds complets"},
  {id:"c17",name:"COMMANDO ÉLITE",desc:"For time — solo niveau sélection",target:"75 burpees · 75 tractions · 150 pompes claquées · 150 squats lestés · 75 dips lestés · 75 box jumps hauts · 25 muscle-ups",tip:"Objectif élite < 40 min"},
  {id:"c18",name:"RAGNARÖK ÉLITE",desc:"EMOM 50 min — ultime des EMOM",target:"Min 1 : 10 tractions · Min 2 : 15 pompes claquées · Min 3 : 12 squat jumps lestés · Min 4 : 10 burpees · Min 5 : 6 muscle-ups",tip:"Si raté : 15 burpees pénalité hors temps"},
  {id:"c19",name:"TRIPLE TROUBLE",desc:"15 rounds pour temps",target:"10 tractions + 20 pompes claquées + 15 squat jumps lestés (x15 rounds)",tip:"Total 150 tractions / 300 pompes / 225 squat jumps. Objectif < 18 min"},
  {id:"c20",name:"IRONMAN BODY ÉLITE",desc:"Épreuve totale lestée",target:"150 pompes claquées · 75 tractions · 150 squat jumps lestés · 75 dips lestés · 150 abdos toes to bar · 75 box jumps · 25 muscle-ups",tip:"Objectif élite < 35 min"},
  {id:"c21",name:"LE SPHINX ÉLITE",desc:"Pyramid 15→1 lestée",target:"15-14-13...1 de tractions + pompes claquées + squat jumps lestés + dips lestés + muscle-ups (÷3)",tip:"Repos = reps suivantes en secondes"},
  {id:"c22",name:"POSEIDON ÉLITE",desc:"8 rounds pour temps",target:"15 burpee-tractions · 20 pompes pieds surélevés · 25 squats bulgares lestés · 30 abdos toes to bar",tip:"RIR 30 s MAX. Objectif élite < 30 min"},
  {id:"c23",name:"ACHILLE ÉLITE",desc:"Test de force-endurance absolu",target:"Max tractions strict · 3 min repos · max dips lestés · 3 min repos · max pompes à un bras",tip:"Objectif élite : >30 tractions / >25 dips lestés / >15 pompes un bras"},
  {id:"c24",name:"LE BERSERKER ÉLITE",desc:"45 min non-stop",target:"Toutes les 90 s : 8 burpees + 8 tractions + 12 pompes claquées + 12 squat jumps lestés",tip:"Aucun repos autorisé entre exercices du bloc"},
  {id:"c25",name:"LÉGION ÉLITE",desc:"For time — solo",target:"500 tractions · 1000 pompes claquées · 1500 squats lestés",tip:"Solo objectif élite : < 60 min. Se divise librement"},
  {id:"c26",name:"RAVEN ÉLITE",desc:"AMRAP 30 min",target:"5 muscle-ups · 8 dips lestés · 12 tractions · 15 pompes claquées · 20 squat jumps lestés",tip:"Objectif élite : >12 rounds"},
  {id:"c27",name:"OLYMPE ÉLITE",desc:"For time — 8 rounds",target:"20 tractions + 25 pompes claquées + 30 squats sautés lestés + 35 abdos toes to bar + 8 muscle-ups",tip:"RIR 30 s MAX. Objectif élite < 25 min"},
  {id:"c28",name:"LA TEMPÊTE ÉLITE",desc:"30 min non-stop lestée",target:"Max rounds : 10 burpees · 10 tractions · 10 pompes claquées · 10 squat jumps lestés · 5 muscle-ups",tip:"Gilet 10 kg. Objectif élite : >12 rounds"},
  {id:"c29",name:"NIRVANA ÉLITE",desc:"Progression par paliers lestée",target:"6 rounds : 100% · 90% · 80% · 80% · 90% · 100% des reps (avec charge)",tip:"Gestion effort + charge = intelligence élite"},
  {id:"c30",name:"KRONOS ÉLITE",desc:"EMOM 60 min — le boss absolu",target:"Min 1-5 : 6 tractions · 12 pompes · 10 squat jumps lestés · 8 burpees · 5 muscle-ups / Min 6 : repos (30 s)",tip:"Si raté : double pénalité. Aucune concession"},
  {id:"c31",name:"LE VOLCAN ÉLITE",desc:"15 rounds for time",target:"6 burpees · 12 tractions · 20 pompes claquées · 25 squats lestés · 6 muscle-ups",tip:"Chaque round < 90 s. Total < 22 min"},
  {id:"c32",name:"BATMAN ÉLITE",desc:"AMRAP 20 min puis 8 rounds",target:"AMRAP : 6 tractions + 12 pompes claquées + 6 muscle-ups / Rounds : 12 squat jumps lestés + 10 dips lestés",tip:"Score AMRAP + temps 8 rounds"},
  {id:"c33",name:"LE SOLDAT ÉLITE",desc:"Challenge hebdomadaire intensifié",target:"Lun : 150 pompes · Mar : 100 tractions · Mer : 150 squats lestés · Jeu : 100 abdos toes to bar · Ven : 75 burpees · Sam : 50 muscle-ups",tip:"Chaque jour en moins de 15 min"},
  {id:"c34",name:"ULTRAVIOLET ÉLITE",desc:"Challenge mensuel élite",target:"1500 pompes claquées · 750 tractions · 1500 squats lestés · 750 dips lestés · 250 muscle-ups",tip:"Se divise librement. Chrono total sur le mois"},
  {id:"c35",name:"DÉTROIT D'ACIER ÉLITE",desc:"Compétition interne hebdomadaire",target:"Max tractions + max pompes claquées + max squat jumps lestés + max dips lestés (3 min par exercice, 60 s repos)",tip:"Score hebdomadaire. Battre le record chaque semaine"},
  {id:"c36",name:"ALPHA TEAM ÉLITE",desc:"For time — équipe de 3 gilets lestés",target:"400 burpees · 400 tractions · 400 pompes claquées · 400 box jumps hauts · 100 muscle-ups",tip:"Gilet 10 kg chacun. Relais libre. Objectif < 35 min"},
  {id:"c37",name:"ZODIAC ÉLITE",desc:"12 exercices — AMRAP 15 min",target:"1 min 15 s de chaque : pompes claquées · tractions · burpees · squats lestés · dips lestés · abdos toes to bar · box jumps · fentes lestées · mountain climbers · gainage lestée · squat jumps · muscle-ups",tip:"Score = reps totales. Élite : >800 reps"},
  {id:"c38",name:"L'HYDRE ÉLITE",desc:"12 rounds — version lestée",target:"Round 1 : 12 tractions. Round 2 : +12 pompes. Round 3 : +12 squats lestés... jusqu'à R12",tip:"Chaque round ajoute 12 reps d'un exercice. Objectif : finir"},
  {id:"c39",name:"APOCALYPSE ÉLITE",desc:"For time — version sans pitié",target:"75 burpees · 150 pompes claquées · 75 tractions · 150 squat jumps lestés · 75 dips lestés · 150 abdos toes to bar · 25 muscle-ups",tip:"Objectif élite < 30 min"},
  {id:"c40",name:"GOLIATH ÉLITE",desc:"7 rounds en pyramide lestée",target:"R1:6+6+6 · R2:12+12+12 · R3:18+18+18 · R4:20+20+20 · R5:18+18+18 · R6:12+12+12 · R7:6+6+6 (tractions-pompes claquées-squats lestés)",tip:"Objectif élite < 35 min"},
  {id:"c41",name:"MINOTAURE ÉLITE",desc:"AMRAP 40 min lestée",target:"12 burpees · 12 tractions · 12 dips lestés · 12 squat jumps lestés · 12 pompes araignée · 6 muscle-ups",tip:"Objectif élite : >10 rounds complets"},
  {id:"c42",name:"FEU ET GLACE ÉLITE",desc:"Alternance haute intensité",target:"15 rounds : 45 s max burpees lestés · 15 s repos · 45 s max tractions · 15 s repos",tip:"Score = reps totales. Gilet 10 kg. Élite : >600 reps"},
  {id:"c43",name:"CERBÈRE ÉLITE",desc:"5 rounds 4 objectifs",target:"R1-5 : max tractions strict · max pompes claquées · max squat jumps lestés · max burpees (2 min par exercice, 30 s repos)",tip:"Score = total des 4 sur 5 rounds. Objectif élite : >1000 reps"},
  {id:"c44",name:"EXCALIBUR ÉLITE",desc:"Épreuve de sélection lestée",target:"3 km run (gilet 10 kg) · 75 tractions · 150 pompes claquées · 200 squats lestés · 75 dips lestés · 3 km run (gilet)",tip:"Objectif élite < 35 min"},
  {id:"c45",name:"RAGNAR ÉLITE",desc:"EMOM 60 min",target:"Min 1 : 6 burpees · Min 2 : 12 tractions · Min 3 : 20 pompes claquées · Min 4 : 25 squats lestés · Min 5 : 6 muscle-ups · Min 6 : repos (30 s)",tip:"Si raté : 8 burpees pénalité. 60 min SANS fléchir"},
  {id:"c46",name:"PHÉNIX ÉLITE",desc:"For time — renaissance lestée",target:"5x : 60 pompes claquées puis 30 tractions puis 10 muscle-ups (enchaîner les 5 blocs)",tip:"Chaque bloc = même performance ou mieux. Gilet 10 kg"},
  {id:"c47",name:"GLADIATEUR ÉLITE",desc:"8 rounds — arène",target:"45 s max pompes claquées · 15 s repos · 45 s max tractions · 15 s repos · 45 s max squat jumps lestés · 15 s repos · 45 s max burpees · 2 min repos",tip:"Score = reps totales sur 8 rounds. Élite : >1200 reps"},
  {id:"c48",name:"NEMESIS ÉLITE",desc:"Course + WOD intensifié",target:"0-10 min : max tractions+pompes+muscle-ups · 10 min : 2 km run gilet · 20-30 min : max squat jumps+dips+burpees · 30 min : 2 km run gilet",tip:"Score = reps + km courus. Niveau forces spéciales"},
  {id:"c49",name:"L'HYDRE NOIRE ÉLITE",desc:"Version ultime — 20 rounds",target:"Round 1 : 6 burpees. Round 2 : +6 pompes. Round 3 : +6 tractions... (ajouter un exercice tous les 2 rounds, avec charge)",tip:"Score = rounds complétés avec charge. Niveau légende"},
  {id:"c50",name:"ZEUS FINAL ÉLITE",desc:"Le boss absolu — all-in lestée",target:"15 rounds : 12 burpees + 12 tractions + 12 pompes claquées + 12 squat jumps lestés + 12 dips lestés + 6 muscle-ups (aucun repos)",tip:"Gilet 10 kg. Objectif élite < 35 min. Niveau LÉGENDE"},
];


// ── STATE ─────────────────────────────────────────────────────────────────────
let userName = '';
let teamCode = '';
let storageKey = '';
let logs = {}; // { wodId: [{date, time, score, feeling, note, ts}] }
let challengeLogs = {}; // { challengeId: {date, score, note, done} }
let currentFilter = 'all';
let currentWodId = null;

// ── STORAGE (localStorage + cross-device via shared key) ──────────────────────
function getKey(suffix) { return `wodb_${storageKey}_${suffix}`; }

function loadData() {
  try {
    const l = localStorage.getItem(getKey('logs'));
    if (l) logs = JSON.parse(l);
    const c = localStorage.getItem(getKey('challenge_logs'));
    if (c) challengeLogs = JSON.parse(c);
  } catch(e) {}
}

function saveData() {
  try {
    localStorage.setItem(getKey('logs'), JSON.stringify(logs));
    localStorage.setItem(getKey('challenge_logs'), JSON.stringify(challengeLogs));
    setSyncStatus('ok', 'Sauvegardé');
  } catch(e) {
    setSyncStatus('error', 'Erreur');
  }
}

function setSyncStatus(state, label) {
  const dot = document.getElementById('syncDot');
  const lbl = document.getElementById('syncLabel');
  dot.className = 'sync-dot ' + (state === 'ok' ? 'ok' : state === 'saving' ? 'saving' : '');
  lbl.textContent = label;
}

// ── SETUP ─────────────────────────────────────────────────────────────────────
function startApp() {
  const name = document.getElementById('setupName').value.trim();
  const code = document.getElementById('setupCode').value.trim().toUpperCase();
  if (!name) { document.getElementById('setupName').focus(); return; }
  userName = name;
  teamCode = code;
  storageKey = (name + '_' + code).toLowerCase().replace(/[^a-z0-9]/g,'_');
  localStorage.setItem('wodb_user', JSON.stringify({name, code}));
  document.getElementById('setupScreen').classList.remove('active');
  initApp();
}

function checkUser() {
  const saved = localStorage.getItem('wodb_user');
  if (saved) {
    try {
      const u = JSON.parse(saved);
      userName = u.name; teamCode = u.code || '';
      storageKey = (u.name + '_' + (u.code||'')).toLowerCase().replace(/[^a-z0-9]/g,'_');
      document.getElementById('setupScreen').classList.remove('active');
      initApp();
    } catch(e) {}
  }
}

function initApp() {
  loadData();
  const h = new Date().getHours();
  const greet = h < 12 ? 'Bonjour' : h < 18 ? 'Bonne séance' : 'Bonsoir';
  document.getElementById('heroGreeting').textContent = `${greet}, ${userName} — NIVEAU ÉLITE !`;
  // Set today's date in form
  document.getElementById('logDate').value = new Date().toISOString().split('T')[0];
  updateStats();
  renderWods();
  renderChallenges();
  renderLog();
  renderProgress();
  setSyncStatus('ok', 'Synchronisé');
}

// ── STATS ─────────────────────────────────────────────────────────────────────
function isDone(wodId) { return logs[wodId] && logs[wodId].length > 0; }
function isChallDone(cid) { return challengeLogs[cid] && challengeLogs[cid].done; }

function updateStats() {
  const hautDone = WODS.filter(w => w.type === 'haut' && isDone(w.id)).length;
  const basDone  = WODS.filter(w => w.type === 'bas'  && isDone(w.id)).length;
  const compDone = WODS.filter(w => w.type === 'complet' && isDone(w.id)).length;
  const challDone = CHALLENGES.filter(c => isChallDone(c.id)).length;
  const total = hautDone + basDone + compDone + challDone;

  document.getElementById('statTotal').textContent = total;
  document.getElementById('statHaut').textContent = `${hautDone}/50`;
  document.getElementById('statBas').textContent = `${basDone}/50`;
  document.getElementById('statComplet').textContent = `${compDone}/50`;
  document.getElementById('statChallDone').textContent = challDone;
  document.getElementById('statChallLeft').textContent = 50 - challDone;

  // Progress bars
  const pct = (n, total) => Math.round(n / total * 100);
  const set = (id, bar, n, t) => {
    const p = pct(n, t);
    document.getElementById(id).textContent = p + '%';
    document.getElementById(bar).style.width = p + '%';
  };
  set('pctHaut', 'barHaut', hautDone, 50);
  set('pctBas', 'barBas', basDone, 50);
  set('pctComplet', 'barComplet', compDone, 50);
  set('pctChall', 'barChall', challDone, 50);
}

// ── FILTER ────────────────────────────────────────────────────────────────────
function setFilter(f, btn) {
  currentFilter = f;
  document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  renderWods();
}

// ── RENDER WODS ───────────────────────────────────────────────────────────────
function renderWods() {
  const search = document.getElementById('searchInput').value.toLowerCase();
  let list = WODS.filter(w => {
    if (currentFilter === 'haut') return w.type === 'haut';
    if (currentFilter === 'bas')  return w.type === 'bas';
    if (currentFilter === 'complet') return w.type === 'complet';
    if (currentFilter === 'done') return isDone(w.id);
    if (currentFilter === 'todo') return !isDone(w.id);
    return true;
  }).filter(w => {
    if (!search) return true;
    return w.name.toLowerCase().includes(search) ||
           w.format.toLowerCase().includes(search) ||
           w.exercises.some(e => e.toLowerCase().includes(search));
  });

  document.getElementById('wodCount').textContent = list.length + ' WODs';

  const typeClass = { haut: '', bas: 'bas', complet: 'complet' };
  const html = list.map(w => {
    const tc = typeClass[w.type] || '';
    const typeName = { haut: 'HAUT DU CORPS', bas: 'BAS DU CORPS', complet: 'CORPS COMPLET' }[w.type];
    const done = isDone(w.id);
    const bestLog = done ? logs[w.id][logs[w.id].length - 1] : null;
    const preview = w.exercises.slice(0, 2).join(' · ') + (w.exercises.length > 2 ? '...' : '');
    return `<div class="wod-card ${done?'done':''}" onclick="openWod(${w.id})">
      <div class="wod-card-header">
        <div class="wod-num ${tc}">${w.num}</div>
        <div class="wod-type-badge">${typeName}${done ? ' &nbsp;·&nbsp; <span style="color:var(--green)">'+logs[w.id].length+' fois</span>' : ''}</div>
      </div>
      <div class="wod-card-body">
        <div class="wod-name">${w.name}</div>
        <div class="wod-format">${w.format}</div>
        <div class="wod-preview">${preview}</div>
        ${bestLog && bestLog.score ? `<div style="font-size:11px;color:var(--gold);margin-top:4px">Meilleur : ${bestLog.score}</div>` : ''}
      </div>
    </div>`;
  }).join('');

  document.getElementById('wodList').innerHTML = html || `<div class="empty-state"><div class="empty-state-icon">🔍</div><div class="empty-state-text">Aucun WOD trouvé</div></div>`;
}

// ── OPEN WOD MODAL ────────────────────────────────────────────────────────────
function openWod(id) {
  const w = WODS.find(x => x.id === id);
  if (!w) return;
  currentWodId = id;

  const tc = { haut: '', bas: 'bas', complet: 'complet' }[w.type] || '';
  const typeName = { haut: 'HAUT DU CORPS', bas: 'BAS DU CORPS', complet: 'CORPS COMPLET' }[w.type];

  document.getElementById('mBadgeNum').textContent = w.num;
  document.getElementById('mBadgeNum').className = 'modal-badge-num ' + tc;
  document.getElementById('mBadgeType').textContent = typeName;
  document.getElementById('mName').textContent = w.name;
  document.getElementById('mFormat').textContent = w.format;
  document.getElementById('mFormat').className = 'modal-format ' + tc;

  document.getElementById('mExercises').innerHTML = w.exercises.map(e =>
    `<div class="exercise-item ${tc}"><span class="exercise-bullet">▸</span>${e}</div>`
  ).join('');

  const noteBox = document.getElementById('mNote');
  if (w.note) {
    noteBox.style.display = 'flex';
    document.getElementById('mNoteText').textContent = w.note;
  } else {
    noteBox.style.display = 'none';
  }

  // Pre-fill last log if exists
  document.getElementById('logDate').value = new Date().toISOString().split('T')[0];
  document.getElementById('logTime').value = '';
  document.getElementById('logScore').value = '';
  document.getElementById('logFeeling').value = '💪';
  document.getElementById('logNote').value = '';

  const saveBtn = document.getElementById('saveBtn');
  saveBtn.textContent = 'ENREGISTRER ✓';
  saveBtn.className = 'btn-save';

  document.getElementById('modalOverlay').classList.add('open');
  document.body.style.overflow = 'hidden';
}

function closeModal(e) {
  if (e.target === document.getElementById('modalOverlay')) closeModalDirect();
}
function closeModalDirect() {
  document.getElementById('modalOverlay').classList.remove('open');
  document.body.style.overflow = '';
}

// ── SAVE LOG ─────────────────────────────────────────────────────────────────
function saveLog() {
  if (!currentWodId) return;
  const date    = document.getElementById('logDate').value;
  const time    = document.getElementById('logTime').value.trim();
  const score   = document.getElementById('logScore').value.trim();
  const feeling = document.getElementById('logFeeling').value;
  const note    = document.getElementById('logNote').value.trim();

  if (!date) { showToast('Indiquez une date !'); return; }

  const entry = { date, time, score, feeling, note, ts: Date.now() };
  if (!logs[currentWodId]) logs[currentWodId] = [];
  logs[currentWodId].push(entry);

  saveData();
  updateStats();
  renderWods();
  renderLog();
  renderProgress();

  const btn = document.getElementById('saveBtn');
  btn.textContent = '✓ ENREGISTRÉ !';
  btn.className = 'btn-save saved';
  showToast('Performance enregistrée ! 💪');

  setTimeout(closeModalDirect, 800);
}

// ── RENDER CHALLENGES ─────────────────────────────────────────────────────────
function renderChallenges() {
  const html = CHALLENGES.map((c, i) => {
    const done = isChallDone(c.id);
    const cl = challengeLogs[c.id];
    return `<div class="challenge-card ${done?'done':''}" onclick="openChallenge('${c.id}')">
      <div class="challenge-header">
        <div class="challenge-num">CHALLENGE #${String(i+1).padStart(2,'0')}</div>
        <div class="challenge-stars">★★★★★</div>
      </div>
      <div class="challenge-body">
        <div class="challenge-name">${c.name}</div>
        <div class="challenge-desc">${c.desc}</div>
        <div class="challenge-score-row">
          ${cl && cl.score ? `<div class="challenge-best">${cl.score}</div>` : ''}
          ${done ? '<div class="challenge-done-badge">COMPLÉTÉ</div>' : ''}
        </div>
      </div>
    </div>`;
  }).join('');
  document.getElementById('challengeGrid').innerHTML = html;
}

function openChallenge(cid) {
  const c = CHALLENGES.find(x => x.id === cid);
  if (!c) return;

  // Reuse modal but in challenge mode
  currentWodId = 'challenge_' + cid;

  document.getElementById('mBadgeNum').textContent = 'CHALLENGE';
  document.getElementById('mBadgeNum').className = 'modal-badge-num challenge';
  document.getElementById('mBadgeType').textContent = '★★★★★ ÉLITE';
  document.getElementById('mName').textContent = c.name;
  document.getElementById('mFormat').textContent = c.desc;
  document.getElementById('mFormat').className = 'modal-format challenge';

  document.getElementById('mExercises').innerHTML = c.target.split(' · ').map(e =>
    `<div class="exercise-item challenge"><span class="exercise-bullet">→</span>${e}</div>`
  ).join('');

  const noteBox = document.getElementById('mNote');
  noteBox.style.display = 'flex';
  document.getElementById('mNoteText').textContent = c.tip;

  document.getElementById('logDate').value = new Date().toISOString().split('T')[0];
  document.getElementById('logTime').value = '';
  document.getElementById('logScore').value = '';
  document.getElementById('logFeeling').value = '💪';
  document.getElementById('logNote').value = '';

  const saveBtn = document.getElementById('saveBtn');
  saveBtn.textContent = 'VALIDER LE CHALLENGE ✓';
  saveBtn.className = 'btn-save';
  saveBtn.style.background = 'var(--gold)';

  document.getElementById('modalOverlay').classList.add('open');
  document.body.style.overflow = 'hidden';
}

// Override saveLog to handle challenges
const _origSaveLog = saveLog;
window.saveLog = function() {
  if (currentWodId && String(currentWodId).startsWith('challenge_')) {
    const cid = currentWodId.replace('challenge_', '');
    const date    = document.getElementById('logDate').value;
    const time    = document.getElementById('logTime').value.trim();
    const score   = document.getElementById('logScore').value.trim();
    const feeling = document.getElementById('logFeeling').value;
    const note    = document.getElementById('logNote').value.trim();
    if (!date) { showToast('Indiquez une date !'); return; }
    challengeLogs[cid] = { date, time, score, feeling, note, done: true, ts: Date.now() };
    document.getElementById('saveBtn').style.background = '';
    saveData();
    updateStats();
    renderChallenges();
    renderLog();
    renderProgress();
    showToast('Challenge validé ! 🏆');
    setTimeout(closeModalDirect, 800);
  } else {
    _origSaveLog();
  }
};

// ── RENDER LOG ────────────────────────────────────────────────────────────────
function renderLog() {
  const allEntries = [];

  Object.entries(logs).forEach(([id, entries]) => {
    const wod = WODS.find(w => w.id == id);
    if (!wod) return;
    entries.forEach(e => allEntries.push({ ...e, name: wod.name, type: wod.type, num: wod.num }));
  });

  Object.entries(challengeLogs).forEach(([id, e]) => {
    const c = CHALLENGES.find(x => x.id === id);
    if (!c) return;
    allEntries.push({ ...e, name: c.name, type: 'challenge', num: 'CHALLENGE' });
  });

  allEntries.sort((a, b) => b.ts - a.ts);

  document.getElementById('logCount').textContent = allEntries.length + ' entrées';

  if (allEntries.length === 0) {
    document.getElementById('logEmpty').style.display = 'block';
    document.getElementById('logEntries').innerHTML = '';
    return;
  }
  document.getElementById('logEmpty').style.display = 'none';

  const typeColor = { haut: 'var(--accent1)', bas: '#4FC3F7', complet: '#B39DDB', challenge: 'var(--gold)' };

  document.getElementById('logEntries').innerHTML = allEntries.map(e => `
    <div class="log-entry">
      <div class="log-entry-left">
        <div class="log-entry-name">
          <span class="log-entry-type-dot" style="background:${typeColor[e.type]||'var(--accent1)'}"></span>
          ${e.name}
        </div>
        <div class="log-entry-meta">${e.num} · ${e.feeling || ''}</div>
        ${e.note ? `<div class="log-entry-note">${e.note}</div>` : ''}
      </div>
      <div class="log-entry-right">
        <div class="log-entry-score">${e.score || e.time || '–'}</div>
        <div class="log-entry-date">${formatDate(e.date)}</div>
        ${e.time && e.score ? `<div style="font-size:10px;color:var(--muted)">${e.time}</div>` : ''}
      </div>
    </div>
  `).join('');

  // Recent 5 for progress
  const recent5 = allEntries.slice(0, 5);
  document.getElementById('recentList').innerHTML = recent5.map(e => `
    <div class="recent-item">
      <div>
        <div class="recent-item-name">${e.name}</div>
        <div class="recent-item-meta">${formatDate(e.date)} · ${e.feeling || ''}</div>
      </div>
      <div class="recent-item-score">${e.score || e.time || '–'}</div>
    </div>
  `).join('') || '<div style="color:var(--muted);font-size:12px;text-align:center;padding:12px">Aucun entraînement encore</div>';
}

function renderProgress() {
  updateStats();
  renderLog();
}

function formatDate(d) {
  if (!d) return '';
  const [y, m, day] = d.split('-');
  return `${day}/${m}/${y}`;
}

// ── NAV ───────────────────────────────────────────────────────────────────────
function goTo(screen, btn) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('.nav-tab').forEach(b => b.classList.remove('active'));
  document.getElementById('screen-' + screen).classList.add('active');
  btn.classList.add('active');
  window.scrollTo(0, 0);
}

// ── TOAST ─────────────────────────────────────────────────────────────────────
function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 2200);
}

// ── INIT ──────────────────────────────────────────────────────────────────────
checkUser();
</script>
</body>
</html>
