<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Planificateur de Cycle — CRMEF Inezgane · EPS</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=Literata:ital,wght@0,300;0,400;0,500;1,300&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
:root {
  --navy:       #0B1F35;
  --blue:       #1A4A7A;
  --blue-mid:   #2563A8;
  --accent:     #E8621A;
  --accent2:    #F5893E;
  --gold:       #C9A227;
  --green:      #1E7A4A;
  --teal:       #1A7A6E;
  --purple:     #5E3A8A;
  --light:      #F2F5F9;
  --mid:        #D4DDE8;
  --muted:      #4A6278;   /* ← contraste amélioré : était #7A8FA6 */
  --muted-lt:   #7A8FA6;   /* version claire pour fonds sombres */
  --text:       #0F1E2D;
  --white:      #FFFFFF;
  --card-r:     14px;
  --trans:      0.22s cubic-bezier(.4,0,.2,1);
}
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body {
  font-family: 'Literata', Georgia, serif;
  background: var(--light);
  color: var(--text);
  min-height: 100vh;
  overflow-x: hidden;
}

/* ══ HEADER ══ */
.site-header {
  background: var(--navy); color: white;
  padding: 0 32px;
  display: flex; align-items: stretch;
  height: 64px;
  border-bottom: 3px solid var(--accent);
  position: sticky; top: 0; z-index: 100;
  box-shadow: 0 4px 24px rgba(11,31,53,0.4);
}
.header-brand {
  display: flex; align-items: center; gap: 14px;
  border-right: 1px solid rgba(255,255,255,0.1);
  padding-right: 20px; margin-right: 20px;
}
.brand-logo {
  width: 40px; height: 40px; background: var(--accent);
  border-radius: 10px;
  display: flex; align-items: center; justify-content: center;
  font-family: 'Syne', sans-serif;
  font-weight: 800; font-size: 15px; color: white;
  letter-spacing: -0.5px; flex-shrink: 0;
}
.brand-text h1 {
  font-family: 'Syne', sans-serif;
  font-size: 14px; font-weight: 700;
  letter-spacing: 0.02em; line-height: 1.2;
}
.brand-text p {
  font-size: 10px; color: rgba(255,255,255,0.55);
  font-family: 'DM Mono', monospace; margin-top: 1px;
}
.header-nav { display: flex; align-items: center; gap: 4px; flex: 1; }
.hnav-btn {
  padding: 6px 14px; border: none; background: none;
  color: rgba(255,255,255,0.65);
  font-family: 'DM Mono', monospace; font-size: 11px;
  cursor: pointer; border-radius: 6px;
  transition: all var(--trans);
}
.hnav-btn:hover, .hnav-btn.active { background: rgba(255,255,255,0.1); color: white; }
.hnav-btn.active { color: var(--accent2); }
.header-actions { display: flex; align-items: center; gap: 8px; margin-left: auto; }
.hbtn {
  padding: 7px 16px; border-radius: 7px; border: none;
  font-family: 'Syne', sans-serif; font-size: 12px; font-weight: 600;
  cursor: pointer; transition: all var(--trans);
}
.hbtn-ghost { background: rgba(255,255,255,0.08); color: rgba(255,255,255,0.8); }
.hbtn-ghost:hover { background: rgba(255,255,255,0.15); color: white; }
.hbtn-accent { background: var(--accent); color: white; }
.hbtn-accent:hover { background: var(--accent2); transform: translateY(-1px); }

/* ══ VIEWS ══ */
.view { display: none; }
.view.active { display: block; animation: viewIn 0.3s ease; }
@keyframes viewIn { from { opacity:0; transform:translateY(12px); } to { opacity:1; transform:none; } }

/* ══ HERO ══ */
.hero {
  background: linear-gradient(135deg, var(--navy) 0%, var(--blue) 60%, #1A3A5A 100%);
  color: white; padding: 52px 32px 48px;
  position: relative; overflow: hidden;
}
.hero::before {
  content: ''; position: absolute; inset: 0;
  background: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none'%3E%3Cg fill='%23ffffff' fill-opacity='0.03'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
}
.hero-inner { max-width: 960px; margin: 0 auto; position: relative; }
.hero-tag {
  display: inline-flex; align-items: center; gap: 6px;
  background: rgba(255,255,255,0.1); border: 1px solid rgba(255,255,255,0.2);
  padding: 4px 12px; border-radius: 20px;
  font-family: 'DM Mono', monospace; font-size: 11px;
  color: rgba(255,255,255,0.85); margin-bottom: 16px;
}
.hero-tag span { color: var(--accent2); }
.hero h2 {
  font-family: 'Syne', sans-serif;
  font-size: clamp(26px, 4vw, 38px); font-weight: 800; line-height: 1.15;
  margin-bottom: 12px;
}
.hero h2 em { color: var(--accent2); font-style: normal; }
.hero p {
  font-size: 15px; color: rgba(255,255,255,0.8);
  max-width: 520px; line-height: 1.7; margin-bottom: 24px;
}
.hero-stats { display: flex; gap: 28px; flex-wrap: wrap; }
.hero-stat { display: flex; flex-direction: column; }
.hero-stat .num {
  font-family: 'Syne', sans-serif; font-size: 28px; font-weight: 800;
  color: var(--accent2); line-height: 1;
}
.hero-stat .lbl {
  font-size: 11px; color: rgba(255,255,255,0.65);
  font-family: 'DM Mono', monospace; margin-top: 2px;
  text-transform: uppercase; letter-spacing: 0.06em;
}

/* ══ FAMILLES ══ */
.familles-section { max-width: 960px; margin: 0 auto; padding: 36px 20px 60px; }
.section-label {
  font-family: 'DM Mono', monospace; font-size: 11px; color: var(--muted);
  text-transform: uppercase; letter-spacing: 0.1em;
  margin-bottom: 20px; display: flex; align-items: center; gap: 10px;
}
.section-label::after { content: ''; flex: 1; height: 1px; background: var(--mid); }
.familles-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 20px; }
@media(max-width:680px){ .familles-grid { grid-template-columns: 1fr; } }

.famille-card {
  background: var(--white); border-radius: var(--card-r);
  border: 1px solid var(--mid); overflow: hidden;
  transition: all var(--trans); cursor: pointer;
}
.famille-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 12px 36px rgba(11,31,53,0.12);
  border-color: transparent;
}
.famille-header {
  padding: 20px 22px 16px;
  position: relative; overflow: hidden;
}
.famille-header::before {
  content: ''; position: absolute; top: 0; right: -20px;
  width: 120px; height: 120px; border-radius: 50%; opacity: 0.08;
}
.fc-athletisme .famille-header { background: linear-gradient(135deg, #0B1F35, #1A4A7A); }
.fc-athletisme .famille-header::before { background: var(--accent); }
.fc-gymnique .famille-header { background: linear-gradient(135deg, #1E1A35, #5E3A8A); }
.fc-gymnique .famille-header::before { background: #A06AE8; }
.fc-renvoi .famille-header { background: linear-gradient(135deg, #0B2A2A, #1A7A6E); }
.fc-renvoi .famille-header::before { background: #4AE8D8; }
.fc-demarquage .famille-header { background: linear-gradient(135deg, #1A2A0B, #2A6A1A); }
.fc-demarquage .famille-header::before { background: #6AE84A; }

.famille-icon { font-size: 32px; margin-bottom: 10px; display: block; }
.famille-title {
  font-family: 'Syne', sans-serif; font-size: 17px; font-weight: 700;
  color: white; margin-bottom: 4px;
}
.famille-sub {
  font-size: 11px; color: rgba(255,255,255,0.7);
  font-family: 'DM Mono', monospace;
}
.famille-count {
  position: absolute; top: 16px; right: 16px;
  background: rgba(255,255,255,0.15); color: white;
  font-family: 'Syne', sans-serif; font-size: 12px; font-weight: 700;
  padding: 3px 10px; border-radius: 20px;
}
.aps-list { padding: 14px 18px; }
.aps-item {
  display: flex; align-items: center; justify-content: space-between;
  padding: 9px 10px; border-radius: 8px; margin-bottom: 4px;
  transition: background var(--trans);
}
.aps-item:hover { background: var(--light); }
.aps-item-left { display: flex; align-items: center; gap: 10px; }
.aps-dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; }
.dot-ready { background: var(--green); box-shadow: 0 0 0 3px rgba(30,122,74,0.2); }
.dot-locked { background: var(--mid); }
.dot-active { background: var(--accent); box-shadow: 0 0 0 3px rgba(232,98,26,0.2); }
.aps-name { font-size: 13px; font-weight: 500; color: var(--text); }
.aps-name.locked { color: var(--muted); }
.aps-badge {
  font-family: 'DM Mono', monospace; font-size: 10px;
  padding: 2px 8px; border-radius: 20px;
}
.badge-ready { background: rgba(30,122,74,0.1); color: var(--green); }
.badge-locked { background: var(--light); color: var(--muted); }
.badge-active { background: rgba(232,98,26,0.12); color: var(--accent); font-weight: 600; }
.famille-footer {
  padding: 12px 18px; border-top: 1px solid var(--mid);
  display: flex; align-items: center; justify-content: space-between;
}
.famille-progress { display: flex; align-items: center; gap: 8px; }
.progress-bar { width: 80px; height: 4px; background: var(--mid); border-radius: 2px; overflow: hidden; }
.progress-fill { height: 100%; border-radius: 2px; transition: width 0.5s ease; }
.pf-athletisme { background: var(--accent); }
.pf-gymnique { background: var(--purple); }
.pf-renvoi { background: var(--teal); }
.pf-demarquage { background: var(--green); }
.prog-text { font-size: 11px; color: var(--muted); font-family: 'DM Mono', monospace; }
.famille-open-btn {
  font-family: 'Syne', sans-serif; font-size: 12px; font-weight: 600;
  color: var(--blue-mid); background: none; border: none; cursor: pointer;
  display: flex; align-items: center; gap: 4px;
  transition: gap var(--trans);
}
.famille-open-btn:hover { gap: 8px; }

/* ══ APS SELECTION ══ */
.aps-sel-wrap { max-width: 960px; margin: 0 auto; padding: 28px 20px 60px; }
.aps-sel-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; max-width: 640px; }
@media(max-width:500px){ .aps-sel-grid { grid-template-columns: 1fr; } }
.aps-sel-card {
  background: var(--white); border-radius: var(--card-r);
  border: 2px solid var(--accent); overflow: hidden;
  cursor: pointer; transition: all var(--trans);
  box-shadow: 0 2px 8px rgba(232,98,26,0.1);
}
.aps-sel-card:hover { transform: translateY(-3px); box-shadow: 0 10px 28px rgba(232,98,26,0.2); }
.aps-sel-h {
  background: linear-gradient(135deg, #0B1F35, #1A4A7A);
  padding: 18px 20px; border-bottom: 2px solid var(--accent);
}
.aps-sel-icon { font-size: 28px; margin-bottom: 8px; display: block; }
.aps-sel-title {
  font-family: 'Syne', sans-serif; font-weight: 800; font-size: 16px;
  color: white; margin-bottom: 3px;
}
.aps-sel-sub { font-size: 11px; color: rgba(255,255,255,0.6); font-family: 'DM Mono', monospace; }
.aps-sel-foot {
  padding: 12px 20px;
  display: flex; align-items: center; justify-content: space-between;
}
.aps-sel-badge {
  font-size: 11px; font-weight: 700; color: var(--green);
  background: rgba(30,122,74,0.1); padding: 3px 9px;
  border-radius: 20px; font-family: 'DM Mono', monospace;
}
.aps-sel-go {
  font-family: 'Syne', sans-serif; font-weight: 700;
  font-size: 12px; color: var(--blue-mid);
  background: none; border: none; cursor: pointer;
}

/* ══ APS DETAIL ══ */
.aps-view-wrap { max-width: 960px; margin: 0 auto; padding: 28px 20px 60px; }
.breadcrumb {
  display: flex; align-items: center; gap: 8px;
  font-family: 'DM Mono', monospace; font-size: 11px; color: var(--muted);
  margin-bottom: 20px;
}
.breadcrumb a { color: var(--blue-mid); text-decoration: none; cursor: pointer; }
.breadcrumb a:hover { text-decoration: underline; }
.breadcrumb span { color: var(--mid); }
.aps-hero {
  display: flex; align-items: flex-start; justify-content: space-between;
  gap: 20px; padding-bottom: 24px;
  border-bottom: 1px solid var(--mid); margin-bottom: 28px; flex-wrap: wrap;
}
.aps-hero-left { flex: 1; }
.aps-famille-chip {
  display: inline-flex; align-items: center; gap: 6px;
  padding: 4px 12px; border-radius: 20px;
  font-family: 'DM Mono', monospace; font-size: 11px; margin-bottom: 10px;
  background: rgba(26,74,122,0.1); color: var(--blue);
}
.aps-hero h2 {
  font-family: 'Syne', sans-serif; font-size: 28px; font-weight: 800;
  color: var(--navy); margin-bottom: 6px;
}
.aps-hero p { font-size: 14px; color: var(--muted); line-height: 1.6; max-width: 480px; }
.aps-hero-actions { display: flex; flex-direction: column; gap: 8px; align-items: flex-end; }
.btn-launch {
  padding: 12px 24px; border-radius: 10px;
  background: var(--accent); color: white; border: none;
  font-family: 'Syne', sans-serif; font-size: 14px; font-weight: 700;
  cursor: pointer; transition: all var(--trans);
  display: flex; align-items: center; gap: 8px;
}
.btn-launch:hover { background: var(--accent2); transform: translateY(-2px); box-shadow: 0 8px 24px rgba(232,98,26,0.35); }
.btn-outline {
  padding: 10px 20px; border-radius: 10px;
  background: white; color: var(--navy);
  border: 1px solid var(--mid);
  font-family: 'Syne', sans-serif; font-size: 13px; font-weight: 600;
  cursor: pointer; transition: all var(--trans);
}
.btn-outline:hover { border-color: var(--blue-mid); color: var(--blue-mid); }

.niveaux-grid {
  display: grid; grid-template-columns: repeat(3, 1fr); gap: 14px; margin-bottom: 28px;
}
@media(max-width:600px){ .niveaux-grid { grid-template-columns: 1fr; } }
.niveau-mini-card {
  background: white; border-radius: 10px;
  border: 1px solid var(--mid); padding: 16px;
  position: relative; overflow: hidden; transition: all var(--trans);
}
.niveau-mini-card:hover { box-shadow: 0 6px 20px rgba(11,31,53,0.1); }
.niveau-mini-card::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px; }
.nmc-1::before { background: var(--navy); }
.nmc-2::before { background: var(--blue-mid); }
.nmc-3::before { background: var(--accent); }
.nmc-badge {
  font-family: 'DM Mono', monospace; font-size: 10px;
  text-transform: uppercase; letter-spacing: 0.08em;
  margin-bottom: 6px; display: block;
}
.nmc-1 .nmc-badge { color: var(--navy); }
.nmc-2 .nmc-badge { color: var(--blue-mid); }
.nmc-3 .nmc-badge { color: var(--accent); }
.nmc-title { font-family: 'Syne', sans-serif; font-size: 13px; font-weight: 700; color: var(--navy); margin-bottom: 4px; }
.nmc-phrase {
  font-size: 11px; color: var(--muted); font-style: italic; line-height: 1.4;
  border-left: 2px solid var(--mid); padding-left: 8px; margin: 8px 0;
}

/* ══ PLANIFICATEUR ══ */
.planner-wrap { max-width: 960px; margin: 0 auto; padding: 0 20px 60px; }
.stepper-bar {
  background: white; border-radius: 12px; border: 1px solid var(--mid);
  display: flex; overflow: hidden; margin-bottom: 24px;
}
.step-tab {
  flex: 1; padding: 14px 12px;
  display: flex; align-items: center; gap: 8px;
  background: none; border: none; cursor: pointer;
  font-family: 'DM Mono', monospace; font-size: 11px;
  color: var(--muted); transition: all var(--trans);
  border-bottom: 3px solid transparent; justify-content: center;
}
.step-tab:not(:last-child) { border-right: 1px solid var(--mid); }
.step-tab.active { color: var(--navy); border-bottom-color: var(--accent); background: #FAFBFC; }
.step-tab.done { color: var(--green); border-bottom-color: var(--green); }
.step-tab-num {
  width: 22px; height: 22px; border-radius: 50%;
  background: var(--mid); color: var(--muted);
  display: flex; align-items: center; justify-content: center;
  font-size: 11px; font-weight: 700; flex-shrink: 0; transition: all var(--trans);
}
.step-tab.active .step-tab-num { background: var(--accent); color: white; }
.step-tab.done .step-tab-num { background: var(--green); color: white; }
.step-tab-label { text-align: left; line-height: 1.3; display: none; }
@media(min-width:500px){ .step-tab-label { display: block; } }

.sub-panel { display: none; }
.sub-panel.active { display: block; animation: viewIn 0.25s ease; }

.sp-title {
  font-family: 'Syne', sans-serif; font-size: 20px; font-weight: 800;
  color: var(--navy); margin-bottom: 4px;
}
.sp-desc { font-size: 13px; color: var(--muted); margin-bottom: 18px; font-family: 'Literata', serif; }

/* Conduites */
.niveau-section-label { display: flex; align-items: center; gap: 10px; margin: 20px 0 12px; }
.nsl-pill {
  font-family: 'Syne', sans-serif; font-size: 12px; font-weight: 700;
  padding: 3px 12px; border-radius: 20px; white-space: nowrap;
}
.nsl-1 { background: var(--navy); color: white; }
.nsl-2 { background: var(--blue-mid); color: white; }
.nsl-3 { background: var(--accent); color: white; }
.nsl-line { flex: 1; height: 1px; background: var(--mid); }
.nsl-sub { font-size: 11px; color: var(--muted); font-style: italic; }

.conduite-card {
  background: white; border-radius: 10px; border: 2px solid var(--mid);
  padding: 14px 16px; margin-bottom: 10px;
  display: flex; gap: 14px; align-items: flex-start;
  cursor: pointer; transition: all var(--trans);
}
.conduite-card:hover { border-color: var(--blue-mid); }
.conduite-card.sel { border-color: var(--green); background: rgba(30,122,74,0.04); }
.conduite-card.rej { border-color: #D05030; background: rgba(208,80,48,0.04); opacity:0.7; }
.cc-check {
  width: 24px; height: 24px; border-radius: 7px;
  border: 2px solid var(--mid); background: white;
  display: flex; align-items: center; justify-content: center;
  font-size: 13px; flex-shrink: 0; margin-top: 2px;
  transition: all var(--trans);
}
.conduite-card.sel .cc-check { background: var(--green); border-color: var(--green); color: white; }
.conduite-card.rej .cc-check { background: #D05030; border-color: #D05030; color: white; }
.cc-body strong {
  font-size: 13px; font-family: 'Syne', sans-serif;
  color: var(--navy); display: block; margin-bottom: 4px;
}
.cc-body p { font-size: 12px; color: var(--muted); line-height: 1.5; }
.cc-hyp {
  margin-top: 6px; padding: 5px 10px;
  background: var(--light); border-radius: 6px;
  font-size: 11px; color: var(--blue-mid);
  font-family: 'DM Mono', monospace; display: inline-block;
}
.ot-banner {
  background: linear-gradient(135deg, var(--navy), var(--blue));
  color: white; border-radius: 8px;
  padding: 12px 16px; font-size: 12px; line-height: 1.6;
  margin: 12px 0 20px; display: flex; gap: 10px; align-items: flex-start;
}
.ot-label {
  font-family: 'DM Mono', monospace; font-size: 10px;
  color: var(--accent2); white-space: nowrap; padding-top: 1px;
}

/* OE */
.oe-cards-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
@media(max-width:580px){ .oe-cards-grid { grid-template-columns: 1fr; } }
.oe-mini {
  background: white; border-radius: 10px; border: 1px solid var(--mid);
  padding: 14px; position: relative; overflow: hidden; transition: all var(--trans);
}
.oe-mini:hover { box-shadow: 0 4px 16px rgba(11,31,53,0.08); }
.oe-mini::before { content: ''; position: absolute; left: 0; top: 0; bottom: 0; width: 3px; }
.oep1::before { background: var(--accent); }
.oep2::before { background: var(--blue-mid); }
.oep3::before { background: var(--mid); }
.oe-mini-tag {
  font-family: 'DM Mono', monospace; font-size: 10px;
  text-transform: uppercase; letter-spacing: 0.06em;
  padding: 2px 8px; border-radius: 20px; display: inline-block; margin-bottom: 6px;
}
.oep1 .oe-mini-tag { background: rgba(232,98,26,0.1); color: var(--accent); }
.oep2 .oe-mini-tag { background: rgba(37,99,168,0.1); color: var(--blue-mid); }
.oep3 .oe-mini-tag { background: var(--light); color: var(--muted); }
.oe-mini-title { font-family: 'Syne', sans-serif; font-size: 13px; font-weight: 700; color: var(--navy); margin-bottom: 6px; }
.oe-mini-desc { font-size: 12px; color: var(--muted); line-height: 1.5; margin-bottom: 10px; }
.toggle-row { display: flex; align-items: center; gap: 8px; cursor: pointer; }
.tog {
  width: 36px; height: 20px; border-radius: 10px;
  background: var(--mid); position: relative;
  transition: background var(--trans); flex-shrink: 0;
}
.tog::after {
  content: ''; position: absolute;
  width: 16px; height: 16px; border-radius: 50%; background: white;
  top: 2px; left: 2px; transition: transform var(--trans);
  box-shadow: 0 1px 3px rgba(0,0,0,0.2);
}
.tog.on { background: var(--green); }
.tog.on::after { transform: translateX(16px); }
.tog-lbl { font-size: 12px; color: var(--muted); font-family: 'DM Mono', monospace; }
.tog.on + .tog-lbl { color: var(--green); font-weight: 500; }

/* Objectifs */
.cfg-bar {
  background: white; border-radius: 10px; border: 1px solid var(--mid);
  padding: 14px 18px; margin-bottom: 22px;
  display: flex; gap: 16px; flex-wrap: wrap; align-items: center;
}
.cfg-field { display: flex; flex-direction: column; gap: 3px; }
.cfg-label {
  font-family: 'DM Mono', monospace; font-size: 10px;
  text-transform: uppercase; letter-spacing: 0.08em; color: var(--muted);
}
.cfg-input {
  border: 1px solid var(--mid); border-radius: 6px;
  padding: 6px 10px; font-size: 12px; color: var(--navy);
  font-family: 'DM Mono', monospace; background: var(--light);
  transition: border var(--trans);
}
.cfg-input:focus { outline: none; border-color: var(--blue-mid); background: white; }

/* ── Volume horaire curseur ── */
.vol-block {
  background: var(--light);
  border: 1.5px solid var(--mid);
  border-radius: 11px;
  padding: 18px 20px 14px;
  margin: 16px 0 20px;
}
.vol-top { display: flex; justify-content: space-between; align-items: flex-end; margin-bottom: 12px; }
.vol-label { font-family: 'Syne', sans-serif; font-size: 12px; font-weight: 700; letter-spacing: .05em; text-transform: uppercase; color: var(--muted); }
.vol-val-wrap { display: flex; align-items: baseline; gap: 5px; }
.vol-num { font-family: 'Syne', sans-serif; font-size: 30px; font-weight: 800; color: var(--accent); line-height: 1; }
.vol-unit { font-family: 'DM Mono', monospace; font-size: 11px; color: var(--muted); }
.vol-slider-row { padding: 0 2px; }
.vol-slider-row input[type=range] {
  width: 100%; -webkit-appearance: none; height: 6px; border-radius: 4px;
  background: linear-gradient(to right, var(--accent) 0%, var(--accent) var(--vpct,50%), var(--mid) var(--vpct,50%));
  outline: none; cursor: pointer;
}
.vol-slider-row input[type=range]::-webkit-slider-thumb {
  -webkit-appearance: none; width: 22px; height: 22px; border-radius: 50%;
  background: var(--accent); border: 3px solid white;
  box-shadow: 0 2px 8px rgba(232,98,26,.35); cursor: pointer;
}
.vol-ticks { display: flex; justify-content: space-between; font-family: 'DM Mono', monospace; font-size: 10px; color: var(--muted); padding: 4px 2px 0; }
.vol-conseil {
  background: #FFF7F2; border-left: 3px solid var(--accent); border-radius: 0 7px 7px 0;
  padding: 10px 14px; font-size: 12px; color: var(--navy); margin: 12px 0 10px;
  font-style: italic; line-height: 1.55;
}
.vol-bar { display: flex; border-radius: 7px; overflow: hidden; height: 36px; margin-bottom: 8px; }
.vb-seg { display: flex; align-items: center; justify-content: center; font-family: 'Syne', sans-serif; font-size: 11px; font-weight: 700; color: white; transition: flex .35s cubic-bezier(.4,0,.2,1); white-space: nowrap; overflow: hidden; gap: 3px; }
.vb-seg small { font-weight: 400; font-size: 9px; opacity: .8; }
.vb-1 { background: var(--blue); }
.vb-2 { background: var(--accent); }
.vb-3 { background: #16A34A; }
.vol-legend { display: flex; gap: 14px; }
.vleg { font-family: 'DM Mono', monospace; font-size: 10px; }
.vleg-1 { color: var(--blue); }
.vleg-2 { color: var(--accent); }
.vleg-3 { color: #16A34A; }

/* Objectif inactif */
.obj-entry.inactive { opacity: .35; filter: grayscale(.5); pointer-events: none; }
.obj-entry.inactive .obj-entry-title { color: var(--muted); }

.phase-header { display: flex; align-items: center; gap: 10px; margin: 22px 0 12px; }
.phase-dot { width: 12px; height: 12px; border-radius: 3px; flex-shrink: 0; }
.ph-a { background: var(--navy); }
.ph-b { background: var(--blue-mid); }
.ph-c { background: var(--accent); }
.phase-name { font-family: 'Syne', sans-serif; font-size: 14px; font-weight: 800; color: var(--navy); }
.phase-line { flex: 1; height: 1px; background: var(--mid); }
.phase-seances { font-family: 'DM Mono', monospace; font-size: 11px; color: var(--muted); }

.obj-entry {
  background: white; border-radius: 10px; border: 1px solid var(--mid);
  margin-bottom: 12px; overflow: hidden; transition: all var(--trans);
}
.obj-entry:hover { box-shadow: 0 4px 16px rgba(11,31,53,0.08); }
.obj-entry-head {
  padding: 12px 16px; display: flex; align-items: center; gap: 12px;
  border-bottom: 1px solid var(--mid);
}
.obj-circle {
  width: 30px; height: 30px; border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-family: 'Syne', sans-serif; font-weight: 800; font-size: 13px;
  color: white; flex-shrink: 0;
}
.oc-a { background: var(--navy); }
.oc-b { background: var(--blue-mid); }
.oc-c { background: var(--accent); }
.obj-entry-title { font-family: 'Syne', sans-serif; font-size: 13px; font-weight: 700; color: var(--navy); flex: 1; }
.obj-entry-meta {
  display: flex; align-items: center; gap: 8px;
  font-family: 'DM Mono', monospace; font-size: 11px; color: var(--muted);
}
.obj-entry-meta input {
  width: 36px; border: 1px solid var(--mid); border-radius: 4px;
  padding: 2px 4px; text-align: center;
  font-family: 'DM Mono', monospace; font-size: 11px; color: var(--navy);
}
.obj-body { padding: 12px 16px; }
.obj-ta {
  width: 100%; border: 1px solid var(--mid); border-radius: 7px;
  padding: 10px 12px; font-size: 12px; font-family: 'Literata', serif;
  color: var(--text); background: var(--light); resize: vertical; min-height: 72px;
  line-height: 1.6; transition: border var(--trans);
}
.obj-ta:focus { outline: none; border-color: var(--blue-mid); background: white; }
.obj-chips { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 8px; }
.obj-chip {
  font-family: 'DM Mono', monospace; font-size: 10px;
  padding: 3px 9px; border-radius: 20px; cursor: pointer;
  background: var(--light); border: 1px solid var(--mid); color: var(--muted);
  transition: all var(--trans); user-select: none;
}
.obj-chip.on { background: var(--navy); color: white; border-color: var(--navy); }
.obj-chip.on.sit { background: var(--blue-mid); border-color: var(--blue-mid); }
.obj-chip.on.ev { background: var(--accent); border-color: var(--accent); }

/* Résumé */
.resume-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; margin-bottom: 20px; }
@media(max-width:580px){ .resume-grid { grid-template-columns: 1fr; } }
.r-card { background: white; border-radius: 10px; border: 1px solid var(--mid); overflow: hidden; }
.r-card-full { grid-column: 1 / -1; }
.r-card-h {
  padding: 12px 16px; font-family: 'Syne', sans-serif;
  font-size: 13px; font-weight: 700; color: white;
  background: var(--navy); display: flex; align-items: center; gap: 6px;
}
.r-card-body { padding: 14px 16px; }
.r-row { display: flex; justify-content: space-between; padding: 7px 0; border-bottom: 1px dashed var(--mid); font-size: 12px; }
.r-row:last-child { border: none; }
.r-lbl { color: var(--muted); }
.r-val { font-weight: 600; color: var(--navy); font-family: 'DM Mono', monospace; }
.cycle-bar { display: flex; gap: 3px; border-radius: 8px; overflow: hidden; margin: 14px 0; height: 36px; }
.cb-seg {
  display: flex; align-items: center; justify-content: center;
  font-family: 'Syne', sans-serif; font-size: 11px; font-weight: 700; color: white;
  transition: flex var(--trans); flex-direction: column; gap: 1px;
}
.cb-a { background: var(--navy); }
.cb-b { background: var(--blue-mid); }
.cb-c { background: var(--accent); }
.cb-seg small { font-size: 9px; font-weight: 400; opacity: 0.8; }

/* Nav */
.planner-nav {
  display: flex; justify-content: space-between; align-items: center;
  padding-top: 20px; margin-top: 24px; border-top: 1px solid var(--mid);
}
.btn-nav {
  padding: 10px 22px; border-radius: 8px; border: none;
  font-family: 'Syne', sans-serif; font-size: 13px; font-weight: 700;
  cursor: pointer; transition: all var(--trans);
  display: flex; align-items: center; gap: 8px;
}
.btn-prev { background: white; color: var(--navy); border: 1px solid var(--mid); }
.btn-prev:hover { border-color: var(--blue-mid); color: var(--blue-mid); }
.btn-next { background: var(--accent); color: white; }
.btn-next:hover { background: var(--accent2); transform: translateY(-1px); box-shadow: 0 6px 18px rgba(232,98,26,0.3); }
.btn-next:disabled { opacity: .4; cursor: not-allowed; transform: none; box-shadow: none; }
.btn-finish { background: var(--green); color: white; }
.btn-finish:hover { background: #18623C; }
.btn-print-r { background: var(--navy); color: white; }
.nav-hint { font-family: 'DM Mono', monospace; font-size: 11px; color: var(--muted); }
.nav-hint.ok { color: var(--green); }

/* Footer */
footer {
  background: var(--navy); color: rgba(255,255,255,0.6);
  padding: 20px 32px; font-size: 11px;
  font-family: 'DM Mono', monospace;
  display: flex; justify-content: space-between; align-items: center;
  flex-wrap: wrap; gap: 8px;
}
footer a { color: var(--accent2); text-decoration: none; }

@media print {
  .site-header, .stepper-bar, .planner-nav, footer { display: none !important; }
  body { background: white; }
  .planner-wrap { padding: 0; }
  .sub-panel { display: block !important; }
  .r-card { break-inside: avoid; }
  .r-card-h, .cb-seg { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
}
</style>
</head>
<body>

<!-- ══ HEADER ══ -->
<header class="site-header">
  <div class="header-brand">
    <div class="brand-logo">EPS</div>
    <div class="brand-text">
      <h1>Planificateur de Cycle</h1>
      <p>CRMEF Inezgane · Section EPS</p>
    </div>
  </div>
  <nav class="header-nav">
    <button class="hnav-btn active" id="nb-home" onclick="showView('home')">Accueil</button>
    <button class="hnav-btn" id="nb-ath" onclick="showView('aps-sel')">Athlétisme</button>
    <button class="hnav-btn" id="nb-relais" onclick="showView('aps-relais')">C. Relais</button>
    <button class="hnav-btn" id="nb-sl" onclick="showView('aps-sl')">S. Longueur</button>
    <button class="hnav-btn" id="nb-sprint" onclick="showView('aps-sprint')">C. Sprint</button>
    <button class="hnav-btn" id="nb-plan" onclick="launchPlan('relais')">Planifier</button>
  </nav>
  <div class="header-actions">
    <button class="hbtn hbtn-ghost" onclick="window.print()">🖨 Imprimer</button>
    <button class="hbtn hbtn-accent" onclick="launchPlan('relais')">+ Nouveau cycle</button>
  </div>
</header>

<!-- ══════════════════════════════════════
     VIEW : HOME
══════════════════════════════════════ -->
<div class="view active" id="view-home">
  <div class="hero">
    <div class="hero-inner">
      <div class="hero-tag">🎓 <span>CRMEF Inezgane</span> · Outil Didactique EPS · 2025/2026</div>
      <h2>Planifiez vos cycles<br>d'apprentissage <em>en EPS</em></h2>
      <p>Un outil structuré pour accompagner les enseignants dans la planification didactique à partir des conduites typiques, des objets d'enseignement et des objectifs progressifs.</p>
      <div class="hero-stats">
        <div class="hero-stat"><span class="num">4</span><span class="lbl">Familles</span></div>
        <div class="hero-stat"><span class="num">14</span><span class="lbl">Activités</span></div>
        <div class="hero-stat"><span class="num">7</span><span class="lbl">Disponibles ✅</span></div>
        <div class="hero-stat"><span class="num">4</span><span class="lbl">Étapes guidées</span></div>
      </div>
    </div>
  </div>

  <div class="familles-section">
    <div class="section-label">Choisir une famille d'APS</div>
    <div class="familles-grid">

      <!-- ATHLÉTISME -->
      <div class="famille-card fc-athletisme" onclick="showView('aps-sel')">
        <div class="famille-header">
          <span class="famille-count">7 APS</span>
          <span class="famille-icon">🏃</span>
          <div class="famille-title">Athlétisme</div>
          <div class="famille-sub">Courses · Sauts · Lancers</div>
        </div>
        <div class="aps-list">
          <div class="aps-item"><div class="aps-item-left"><div class="aps-dot dot-ready"></div><span class="aps-name">Course de Relais</span></div><span class="aps-badge badge-ready">✓ Disponible</span></div>
          <div class="aps-item"><div class="aps-item-left"><div class="aps-dot dot-ready"></div><span class="aps-name">Saut en Longueur</span></div><span class="aps-badge badge-ready">✓ Disponible</span></div>
          <div class="aps-item"><div class="aps-item-left"><div class="aps-dot dot-ready"></div><span class="aps-name">Course de Sprint</span></div><span class="aps-badge badge-ready">✓ Disponible</span></div>
          <div class="aps-item"><div class="aps-item-left"><div class="aps-dot dot-ready"></div><span class="aps-name">Course de Durée</span></div><span class="aps-badge badge-ready">✓ Disponible</span></div>
          <div class="aps-item"><div class="aps-item-left"><div class="aps-dot dot-active"></div><span class="aps-name">Course de Haies</span></div><span class="aps-badge badge-active">✓ Disponible</span></div>
        </div>
        <div class="famille-footer">
          <div class="famille-progress">
            <div class="progress-bar"><div class="progress-fill pf-athletisme" style="width:71%"></div></div>
            <span class="prog-text">5 / 7</span>
          </div>
          <button class="famille-open-btn">Explorer →</button>
        </div>
      </div>

      <!-- GYMNIQUE -->
      <div class="famille-card fc-gymnique" onclick="showLocked()">
        <div class="famille-header">
          <span class="famille-count">2 APS</span>
          <span class="famille-icon">🤸</span>
          <div class="famille-title">Activités Gymniques & Artistiques</div>
          <div class="famille-sub">Gym au sol · Acrogym</div>
        </div>
        <div class="aps-list">
          <div class="aps-item"><div class="aps-item-left"><div class="aps-dot dot-locked"></div><span class="aps-name locked">Gymnastique au Sol</span></div><span class="aps-badge badge-locked">À venir</span></div>
          <div class="aps-item"><div class="aps-item-left"><div class="aps-dot dot-locked"></div><span class="aps-name locked">Acrogym</span></div><span class="aps-badge badge-locked">À venir</span></div>
        </div>
        <div class="famille-footer">
          <div class="famille-progress">
            <div class="progress-bar"><div class="progress-fill pf-gymnique" style="width:0%"></div></div>
            <span class="prog-text">0 / 2</span>
          </div>
          <button class="famille-open-btn">Explorer →</button>
        </div>
      </div>

      <!-- RENVOI -->
      <div class="famille-card fc-renvoi" onclick="showView('aps-sel-renvoi')">
        <div class="famille-header">
          <span class="famille-count">2 APS</span>
          <span class="famille-icon">🏐</span>
          <div class="famille-title">Sports Collectifs de Renvoi</div>
          <div class="famille-sub">Volleyball · Badminton</div>
        </div>
        <div class="aps-list">
          <div class="aps-item"><div class="aps-item-left"><div class="aps-dot dot-ready"></div><span class="aps-name">Volleyball</span></div><span class="aps-badge badge-ready">✓ Disponible</span></div>
          <div class="aps-item"><div class="aps-item-left"><div class="aps-dot dot-locked"></div><span class="aps-name locked">Badminton</span></div><span class="aps-badge badge-locked">À venir</span></div>
        </div>
        <div class="famille-footer">
          <div class="famille-progress">
            <div class="progress-bar"><div class="progress-fill pf-renvoi" style="width:50%"></div></div>
            <span class="prog-text">1 / 2</span>
          </div>
          <button class="famille-open-btn">Explorer →</button>
        </div>
      </div>

      <!-- DÉMARQUAGE -->
      <div class="famille-card fc-demarquage" onclick="showView('aps-sel-demarquage')">
        <div class="famille-header">
          <span class="famille-count">3 APS</span>
          <span class="famille-icon">🤝</span>
          <div class="famille-title">Sports Collectifs de Démarquage</div>
          <div class="famille-sub">Basketball · Handball · Football</div>
        </div>
        <div class="aps-list">
          <div class="aps-item"><div class="aps-item-left"><div class="aps-dot dot-ready"></div><span class="aps-name">Basketball</span></div><span class="aps-badge badge-ready">✓ Disponible</span></div>
          <div class="aps-item"><div class="aps-item-left"><div class="aps-dot dot-locked"></div><span class="aps-name locked">Handball</span></div><span class="aps-badge badge-locked">À venir</span></div>
          <div class="aps-item"><div class="aps-item-left"><div class="aps-dot dot-locked"></div><span class="aps-name locked">Football</span></div><span class="aps-badge badge-locked">À venir</span></div>
        </div>
        <div class="famille-footer">
          <div class="famille-progress">
            <div class="progress-bar"><div class="progress-fill pf-demarquage" style="width:33%"></div></div>
            <span class="prog-text">1 / 3</span>
          </div>
          <button class="famille-open-btn">Explorer →</button>
        </div>
      </div>

    </div>
  </div>
</div>

<!-- ══════════════════════════════════════
     VIEW : SÉLECTION APS ATHLÉTISME
══════════════════════════════════════ -->
<div class="view" id="view-aps-sel">
  <div class="aps-sel-wrap">
    <div class="breadcrumb">
      <a onclick="showView('home')">⌂ Accueil</a>
      <span>›</span> 🏃 Athlétisme
    </div>
    <div class="sp-title">Athlétisme</div>
    <div class="sp-desc">Choisissez une activité disponible pour commencer la planification.</div>
    <div class="aps-sel-grid">
      <div class="aps-sel-card" onclick="showView('aps-relais')">
        <div class="aps-sel-h">
          <span class="aps-sel-icon">🏃</span>
          <div class="aps-sel-title">Course de Relais</div>
          <div class="aps-sel-sub">Courses · 4×50m</div>
        </div>
        <div class="aps-sel-foot">
          <span class="aps-sel-badge">✓ Disponible</span>
          <button class="aps-sel-go">Ouvrir →</button>
        </div>
      </div>
      <div class="aps-sel-card" onclick="showView('aps-sl')">
        <div class="aps-sel-h">
          <span class="aps-sel-icon">🦘</span>
          <div class="aps-sel-title">Saut en Longueur</div>
          <div class="aps-sel-sub">Sauts · Élan & Impulsion</div>
        </div>
        <div class="aps-sel-foot">
          <span class="aps-sel-badge">✓ Disponible</span>
          <button class="aps-sel-go">Ouvrir →</button>
        </div>
      </div>
      <div class="aps-sel-card" onclick="showView('aps-sprint')">
        <div class="aps-sel-h">
          <span class="aps-sel-icon">⚡</span>
          <div class="aps-sel-title">Course de Sprint</div>
          <div class="aps-sel-sub">Courses · 50m – 100m</div>
        </div>
        <div class="aps-sel-foot">
          <span class="aps-sel-badge">✓ Disponible</span>
          <button class="aps-sel-go">Ouvrir →</button>
        </div>
      </div>
      <div class="aps-sel-card" onclick="showView('aps-duree')">
        <div class="aps-sel-h">
          <span class="aps-sel-icon">🫀</span>
          <div class="aps-sel-title">Course de Durée</div>
          <div class="aps-sel-sub">Courses · Endurance · % VMA</div>
        </div>
        <div class="aps-sel-foot">
          <span class="aps-sel-badge">✓ Disponible</span>
          <button class="aps-sel-go">Ouvrir →</button>
        </div>
      </div>
      <div class="aps-sel-card" onclick="showView('aps-haies')">
        <div class="aps-sel-h">
          <span class="aps-sel-icon">🚧</span>
          <div class="aps-sel-title">Course de Haies</div>
          <div class="aps-sel-sub">Courses · 60m haies</div>
        </div>
        <div class="aps-sel-foot">
          <span class="aps-sel-badge">✓ Disponible</span>
          <button class="aps-sel-go">Ouvrir →</button>
        </div>
      </div>
    </div><!-- /aps-sel-grid -->
  </div><!-- /aps-sel-wrap -->
</div><!-- /view-aps-sel -->

<!-- ══════════════════════════════════════
     VIEW : APS COURSE DE RELAIS
══════════════════════════════════════ -->
<div class="view" id="view-aps-relais">
  <div class="aps-view-wrap">
    <div class="breadcrumb">
      <a onclick="showView('home')">⌂ Accueil</a> <span>›</span>
      <a onclick="showView('aps-sel')">Athlétisme</a> <span>›</span>
      Course de Relais
    </div>
    <div class="aps-hero">
      <div class="aps-hero-left">
        <div class="aps-famille-chip">🏃 Athlétisme · Courses</div>
        <h2>Course de Relais</h2>
        <p>Planifier un cycle 4×50m à partir des conduites typiques observées, des objets d'enseignement prioritaires et de 6 objectifs progressifs.</p>
      </div>
      <div class="aps-hero-actions">
        <button class="btn-launch" onclick="launchPlan('relais')">▶ Lancer la planification</button>
        <button class="btn-outline" onclick="showView('aps-sel')">← Retour Athlétisme</button>
      </div>
    </div>
    <div class="niveaux-grid">
      <div class="niveau-mini-card nmc-1">
        <span class="nmc-badge">Niveau 1</span>
        <div class="nmc-title">Relais discontinu</div>
        <div class="nmc-phrase">« Le témoin s'arrête et repart »</div>
      </div>
      <div class="niveau-mini-card nmc-2">
        <span class="nmc-badge">Niveau 2</span>
        <div class="nmc-title">Relais continu</div>
        <div class="nmc-phrase">« Le témoin ralentit franchement »</div>
      </div>
      <div class="niveau-mini-card nmc-3">
        <span class="nmc-badge">Niveau 3</span>
        <div class="nmc-title">Relais coordonné</div>
        <div class="nmc-phrase">« Le témoin décélère »</div>
      </div>
    </div>
    <div style="text-align:center">
      <button class="btn-launch" onclick="launchPlan('relais')">▶ Commencer la planification</button>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════
     VIEW : APS SAUT EN LONGUEUR
══════════════════════════════════════ -->
<div class="view" id="view-aps-sl">
  <div class="aps-view-wrap">
    <div class="breadcrumb">
      <a onclick="showView('home')">⌂ Accueil</a> <span>›</span>
      <a onclick="showView('aps-sel')">Athlétisme</a> <span>›</span>
      Saut en Longueur
    </div>
    <div class="aps-hero">
      <div class="aps-hero-left">
        <div class="aps-famille-chip">🏃 Athlétisme · Sauts</div>
        <h2>Saut en Longueur</h2>
        <p>Planifier un cycle à partir des conduites typiques et des objets d'enseignement selon Bouargane (CRMEF Inezgane, 2015/2016).</p>
      </div>
      <div class="aps-hero-actions">
        <button class="btn-launch" onclick="launchPlan('sl')">▶ Lancer la planification</button>
        <button class="btn-outline" onclick="showView('aps-sel')">← Retour Athlétisme</button>
      </div>
    </div>
    <div class="niveaux-grid">
      <div class="niveau-mini-card nmc-1">
        <span class="nmc-badge">Niveau 1</span>
        <div class="nmc-title">Le sauteur prudent</div>
        <div class="nmc-phrase">« Il cherche l'impulsion et a peur de la réception »</div>
      </div>
      <div class="niveau-mini-card nmc-2">
        <span class="nmc-badge">Niveau 2</span>
        <div class="nmc-title">Le sauteur percuteur</div>
        <div class="nmc-phrase">« Freinage important durant l'appel »</div>
      </div>
      <div class="niveau-mini-card nmc-3">
        <span class="nmc-badge">Niveau 3</span>
        <div class="nmc-title">Le coureur-sauteur</div>
        <div class="nmc-phrase">« Augmenter la trajectoire et s'équilibrer »</div>
      </div>
    </div>
    <div style="text-align:center">
      <button class="btn-launch" onclick="launchPlan('sl')">▶ Commencer la planification</button>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════
     VIEW : APS COURSE DE SPRINT
══════════════════════════════════════ -->
<div class="view" id="view-aps-sprint">
  <div class="aps-view-wrap">
    <div class="breadcrumb">
      <a onclick="showView('home')">⌂ Accueil</a> <span>›</span>
      <a onclick="showView('aps-sel')">Athlétisme</a> <span>›</span>
      Course de Sprint
    </div>
    <div class="aps-hero">
      <div class="aps-hero-left">
        <div class="aps-famille-chip">🏃 Athlétisme · Courses de vitesse</div>
        <h2>Course de Sprint</h2>
        <p>Planifier un cycle 50-100m à partir des conduites typiques enrichies (recherche didactique INSEP / EPS), des objets d'enseignement et de 6 objectifs progressifs.</p>
      </div>
      <div class="aps-hero-actions">
        <button class="btn-launch" onclick="launchPlan('sprint')">▶ Lancer la planification</button>
        <button class="btn-outline" onclick="showView('aps-sel')">← Retour Athlétisme</button>
      </div>
    </div>
    <div class="niveaux-grid">
      <div class="niveau-mini-card nmc-1">
        <span class="nmc-badge">Niveau 1</span>
        <div class="nmc-title">Le coureur spontané</div>
        <div class="nmc-phrase">« Courir vite c'est répéter le plus vite possible ses foulées habituelles »</div>
      </div>
      <div class="niveau-mini-card nmc-2">
        <span class="nmc-badge">Niveau 2</span>
        <div class="nmc-title">Le sprinteur précipité</div>
        <div class="nmc-phrase">« Courir vite c'est accélérer vite — mais le corps se redresse trop tôt »</div>
      </div>
      <div class="niveau-mini-card nmc-3">
        <span class="nmc-badge">Niveau 3</span>
        <div class="nmc-title">Le coureur-sprinteur</div>
        <div class="nmc-phrase">« Accélération progressive — gestion des ressources en fin de course à construire »</div>
      </div>
    </div>
    <div style="text-align:center">
      <button class="btn-launch" onclick="launchPlan('sprint')">▶ Commencer la planification</button>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════
     VIEW : APS COURSE DE HAIES
══════════════════════════════════════ -->
<div class="view" id="view-aps-haies">
  <div class="aps-view-wrap">
    <div class="breadcrumb">
      <a onclick="showView('home')">⌂ Accueil</a> <span>›</span>
      <a onclick="showView('aps-sel')">Athlétisme</a> <span>›</span>
      Course de Haies
    </div>
    <div class="aps-hero">
      <div class="aps-hero-left">
        <div class="aps-famille-chip">🏃 Athlétisme · Courses combinées</div>
        <h2>Course de Haies</h2>
        <p>Planifier un cycle 60m haies à partir des conduites typiques (Lamotte V., 2002), des objets d'enseignement structurés et de 6 objectifs progressifs articulant intégration du franchissement, organisation de la trajectoire et reprise de course active.</p>
      </div>
      <div class="aps-hero-actions">
        <button class="btn-launch" onclick="launchPlan('haies')">▶ Lancer la planification</button>
        <button class="btn-outline" onclick="showView('aps-sel')">← Retour Athlétisme</button>
      </div>
    </div>
    <div class="niveaux-grid">
      <div class="niveau-mini-card nmc-1">
        <span class="nmc-badge">Niveau 1</span>
        <div class="nmc-title">Le sauteur de haies</div>
        <div class="nmc-phrase">« Franchissement très aérien — course en accordéon »</div>
      </div>
      <div class="niveau-mini-card nmc-2">
        <span class="nmc-badge">Niveau 2</span>
        <div class="nmc-title">Le planeur</div>
        <div class="nmc-phrase">« 4 appuis non rythmés — franchissement encore haut — l'élève plane »</div>
      </div>
      <div class="niveau-mini-card nmc-3">
        <span class="nmc-badge">Niveau 3</span>
        <div class="nmc-title">Le coureur-hurdleur</div>
        <div class="nmc-phrase">« Course continue — reprise de course lente après la haie »</div>
      </div>
    </div>
    <div style="text-align:center">
      <button class="btn-launch" onclick="launchPlan('haies')">▶ Commencer la planification</button>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════
     VIEW : APS COURSE DE DURÉE
══════════════════════════════════════ -->
<div class="view" id="view-aps-duree">
  <div class="aps-view-wrap">
    <div class="breadcrumb">
      <a onclick="showView('home')">⌂ Accueil</a> <span>›</span>
      <a onclick="showView('aps-sel')">Athlétisme</a> <span>›</span>
      Course de Durée
    </div>
    <div class="aps-hero">
      <div class="aps-hero-left">
        <div class="aps-famille-chip">🏃 Athlétisme · Courses d'endurance</div>
        <h2>Course de Durée</h2>
        <p>Planifier un cycle à partir des conduites typiques enrichies (Bergé 2000, Cazorla 2014), des OE structurés et de 6 objectifs progressifs articulant régularité d'allure, puissance aérobie et projet de performance.</p>
      </div>
      <div class="aps-hero-actions">
        <button class="btn-launch" onclick="launchPlan('duree')">▶ Lancer la planification</button>
        <button class="btn-outline" onclick="showView('aps-sel')">← Retour Athlétisme</button>
      </div>
    </div>
    <div class="niveaux-grid">
      <div class="niveau-mini-card nmc-1">
        <span class="nmc-badge">Niveau 1</span>
        <div class="nmc-title">Le coureur spontané</div>
        <div class="nmc-phrase">« Courir vite = partir fort — absence d'allure régulée »</div>
      </div>
      <div class="niveau-mini-card nmc-2">
        <span class="nmc-badge">Niveau 2</span>
        <div class="nmc-title">Le régulier insuffisant</div>
        <div class="nmc-phrase">« Régularité construite — mais % VMA insuffisant pour performer »</div>
      </div>
      <div class="niveau-mini-card nmc-3">
        <span class="nmc-badge">Niveau 3</span>
        <div class="nmc-title">Le coureur-stratège</div>
        <div class="nmc-phrase">« Projet de course construit — gestion de la confrontation à optimiser »</div>
      </div>
    </div>
    <div style="text-align:center">
      <button class="btn-launch" onclick="launchPlan('duree')">▶ Commencer la planification</button>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════
     VIEW : SÉLECTION APS DÉMARQUAGE
══════════════════════════════════════ -->
<div class="view" id="view-aps-sel-demarquage">
  <div class="aps-sel-wrap">
    <div class="breadcrumb">
      <a onclick="showView('home')">⌂ Accueil</a>
      <span>›</span> 🤝 Sports Collectifs de Démarquage
    </div>
    <div class="sp-title">Sports Collectifs de Démarquage</div>
    <div class="sp-desc">Choisissez une activité disponible pour commencer la planification.</div>
    <div class="aps-sel-grid">
      <div class="aps-sel-card" onclick="showView('aps-basketball')">
        <div class="aps-sel-h">
          <span class="aps-sel-icon">🏀</span>
          <div class="aps-sel-title">Basketball</div>
          <div class="aps-sel-sub">Sports co · 3×3 – 4×4</div>
        </div>
        <div class="aps-sel-foot">
          <span class="aps-sel-badge">✓ Disponible</span>
          <button class="aps-sel-go">Ouvrir →</button>
        </div>
      </div>
      <div class="aps-sel-card" style="opacity:.45;pointer-events:none">
        <div class="aps-sel-h">
          <span class="aps-sel-icon">🤾</span>
          <div class="aps-sel-title">Handball</div>
          <div class="aps-sel-sub">Sports co · À venir</div>
        </div>
        <div class="aps-sel-foot">
          <span class="aps-sel-badge" style="background:var(--mid);color:var(--muted)">À venir</span>
          <button class="aps-sel-go" disabled>Bientôt →</button>
        </div>
      </div>
      <div class="aps-sel-card" style="opacity:.45;pointer-events:none">
        <div class="aps-sel-h">
          <span class="aps-sel-icon">⚽</span>
          <div class="aps-sel-title">Football</div>
          <div class="aps-sel-sub">Sports co · À venir</div>
        </div>
        <div class="aps-sel-foot">
          <span class="aps-sel-badge" style="background:var(--mid);color:var(--muted)">À venir</span>
          <button class="aps-sel-go" disabled>Bientôt →</button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════
     VIEW : APS BASKETBALL
══════════════════════════════════════ -->
<div class="view" id="view-aps-basketball">
  <div class="aps-view-wrap">
    <div class="breadcrumb">
      <a onclick="showView('home')">⌂ Accueil</a> <span>›</span>
      <a onclick="showView('aps-sel-demarquage')">Sports Collectifs de Démarquage</a> <span>›</span>
      Basketball
    </div>
    <div class="aps-hero">
      <div class="aps-hero-left">
        <div class="aps-famille-chip">🤝 Sports Collectifs de Démarquage</div>
        <h2>Basketball</h2>
        <p>Planifier un cycle 3×3 – 4×4 à partir des conduites typiques enrichies, des objets d'enseignement et de 6 objectifs progressifs articulant dimensions offensive et défensive.</p>
      </div>
      <div class="aps-hero-actions">
        <button class="btn-launch" onclick="launchPlan('basketball')">▶ Lancer la planification</button>
        <button class="btn-outline" onclick="showView('aps-sel-demarquage')">← Retour</button>
      </div>
    </div>
    <div class="niveaux-grid">
      <div class="niveau-mini-card nmc-1">
        <span class="nmc-badge">Niveau 1</span>
        <div class="nmc-title">La grappe</div>
        <div class="nmc-phrase">« Le ballon m'appartient — je dois l'avoir pour jouer »</div>
      </div>
      <div class="niveau-mini-card nmc-2">
        <span class="nmc-badge">Niveau 2</span>
        <div class="nmc-title">Le gagne-terrain</div>
        <div class="nmc-phrase">« Je dois aller le plus près possible du panier avant de tirer »</div>
      </div>
      <div class="niveau-mini-card nmc-3">
        <span class="nmc-badge">Niveau 3</span>
        <div class="nmc-title">L'attaque stéréotypée</div>
        <div class="nmc-phrase">« Je connais mon jeu — mais la défense le connaît aussi »</div>
      </div>
    </div>
    <div style="text-align:center">
      <button class="btn-launch" onclick="launchPlan('basketball')">▶ Commencer la planification</button>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════
     VIEW : SÉLECTION APS RENVOI
══════════════════════════════════════ -->
<div class="view" id="view-aps-sel-renvoi">
  <div class="aps-sel-wrap">
    <div class="breadcrumb">
      <a onclick="showView('home')">⌂ Accueil</a>
      <span>›</span> 🏐 Sports Collectifs de Renvoi
    </div>
    <div class="sp-title">Sports Collectifs de Renvoi</div>
    <div class="sp-desc">Choisissez une activité disponible pour commencer la planification.</div>
    <div class="aps-sel-grid">
      <div class="aps-sel-card" onclick="showView('aps-volleyball')">
        <div class="aps-sel-h">
          <span class="aps-sel-icon">🏐</span>
          <div class="aps-sel-title">Volleyball</div>
          <div class="aps-sel-sub">Renvoi · 4×4 – 6×6</div>
        </div>
        <div class="aps-sel-foot">
          <span class="aps-sel-badge">✓ Disponible</span>
          <button class="aps-sel-go">Ouvrir →</button>
        </div>
      </div>
      <div class="aps-sel-card" style="opacity:.45;pointer-events:none">
        <div class="aps-sel-h">
          <span class="aps-sel-icon">🏸</span>
          <div class="aps-sel-title">Badminton</div>
          <div class="aps-sel-sub">Renvoi · À venir</div>
        </div>
        <div class="aps-sel-foot">
          <span class="aps-sel-badge" style="background:var(--mid);color:var(--muted)">À venir</span>
          <button class="aps-sel-go" disabled>Bientôt →</button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════
     VIEW : APS VOLLEYBALL
══════════════════════════════════════ -->
<div class="view" id="view-aps-volleyball">
  <div class="aps-view-wrap">
    <div class="breadcrumb">
      <a onclick="showView('home')">⌂ Accueil</a> <span>›</span>
      <a onclick="showView('aps-sel-renvoi')">Sports Collectifs de Renvoi</a> <span>›</span>
      Volleyball
    </div>
    <div class="aps-hero">
      <div class="aps-hero-left">
        <div class="aps-famille-chip">🏐 Sports Collectifs de Renvoi</div>
        <h2>Volleyball</h2>
        <p>Planifier un cycle 4×4 à partir des conduites typiques synthétisées (Lagrange, Thevenot, Choffin & Vidalie), des objets d'enseignement et de 6 objectifs progressifs articulant renvoi, relais et attaque construite.</p>
      </div>
      <div class="aps-hero-actions">
        <button class="btn-launch" onclick="launchPlan('volleyball')">▶ Lancer la planification</button>
        <button class="btn-outline" onclick="showView('aps-sel-renvoi')">← Retour</button>
      </div>
    </div>
    <div class="niveaux-grid">
      <div class="niveau-mini-card nmc-1">
        <span class="nmc-badge">Niveau 1</span>
        <div class="nmc-title">Le sauveur</div>
        <div class="nmc-phrase">« L'adversaire c'est la balle — je dois l'empêcher de tomber »</div>
      </div>
      <div class="niveau-mini-card nmc-2">
        <span class="nmc-badge">Niveau 2</span>
        <div class="nmc-title">Le renvoyeur</div>
        <div class="nmc-phrase">« Nous gagnons si nous renvoyons la balle de l'autre côté du filet »</div>
      </div>
      <div class="niveau-mini-card nmc-3">
        <span class="nmc-badge">Niveau 3</span>
        <div class="nmc-title">Le constructeur</div>
        <div class="nmc-phrase">« Nous gagnons si nous mettons l'adversaire dans l'impossibilité de renvoyer »</div>
      </div>
    </div>
    <div style="text-align:center">
      <button class="btn-launch" onclick="launchPlan('volleyball')">▶ Commencer la planification</button>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════
     VIEW : PLANIFICATEUR
══════════════════════════════════════ -->
<div class="view" id="view-plan">
  <div class="planner-wrap">

    <div class="breadcrumb" style="padding-top:24px">
      <a onclick="showView('home')">⌂ Accueil</a> <span>›</span>
      <a id="bc-aps-link" onclick="backToAps()">Course de Relais</a> <span>›</span>
      <span id="bc-plan-cur" style="color:var(--text)">Planification</span>
    </div>

    <div class="stepper-bar">
      <button class="step-tab active" id="stab1" onclick="showStep(1)">
        <div class="step-tab-num">1</div>
        <div class="step-tab-label">Conduites<br>typiques</div>
      </button>
      <button class="step-tab" id="stab2" onclick="showStep(2)">
        <div class="step-tab-num">2</div>
        <div class="step-tab-label">Objets<br>d'enseignement</div>
      </button>
      <button class="step-tab" id="stab3" onclick="showStep(3)">
        <div class="step-tab-num">3</div>
        <div class="step-tab-label">6 Objectifs<br>progressifs</div>
      </button>
      <button class="step-tab" id="stab4" onclick="showStep(4)">
        <div class="step-tab-num">4</div>
        <div class="step-tab-label">Résumé<br>imprimable</div>
      </button>
    </div>

    <!-- ── ÉTAPE 1 : Conduites ── -->
    <div class="sub-panel active" id="sp1">
      <div class="sp-title" id="sp1-title">Conduites Typiques — Course de Relais</div>
      <div class="sp-desc">Cliquez pour valider ✓ ou rejeter ✕ les conduites observées dans votre groupe.</div>
      <div id="conduites-content"><!-- généré par JS --></div>
      <div class="planner-nav">
        <div class="nav-hint" id="hint1">⚠️ Sélectionnez au moins 2 conduites</div>
        <button class="btn-nav btn-next" id="btnNext1" onclick="showStep(2)" disabled>Objets d'enseignement →</button>
      </div>
    </div>

    <!-- ── ÉTAPE 2 : OE ── -->
    <div class="sub-panel" id="sp2">
      <div class="sp-title">Objets d'Enseignement Prioritaires</div>
      <div class="sp-desc">Les objets issus de vos conduites validées sont présélectionnés. Activez ou désactivez.</div>
      <div class="oe-cards-grid" id="oe-grid"></div>
      <div class="planner-nav">
        <button class="btn-nav btn-prev" onclick="showStep(1)">← Retour</button>
        <button class="btn-nav btn-next" onclick="showStep(3)">Planifier les objectifs →</button>
      </div>
    </div>

    <!-- ── ÉTAPE 3 : Objectifs ── -->
    <div class="sub-panel" id="sp3">
      <div class="sp-title" id="sp3-title">6 Objectifs Progressifs — Course de Relais</div>
      <div class="sp-desc">Indiquez le volume horaire disponible — l'outil adapte les objectifs retenus et leur répartition selon la logique de progression.</div>
      <div class="cfg-bar">
        <div class="cfg-field"><label class="cfg-label">Classe</label><input class="cfg-input" id="cfg-classe" type="text" placeholder="Ex: 2BAC EPS A" style="width:150px"></div>
        <div class="cfg-field"><label class="cfg-label">Durée</label><select class="cfg-input" id="cfg-dur"><option>60 min</option><option selected>90 min</option><option>120 min</option></select></div>
        <div class="cfg-field"><label class="cfg-label">Niveau départ</label><select class="cfg-input" id="cfg-niv"><option>Niveau 1</option><option selected>Niveau 2</option><option>Niveau 3</option></select></div>
      </div>

      <!-- Curseur volume horaire -->
      <div class="vol-block">
        <div class="vol-top">
          <div class="vol-label">Volume horaire disponible</div>
          <div class="vol-val-wrap">
            <span class="vol-num" id="vol-num">10</span>
            <span class="vol-unit">séances</span>
          </div>
        </div>
        <div class="vol-slider-row">
          <input type="range" id="vol-slider" min="6" max="12" step="2" value="10" oninput="onVolChange(this.value)">
        </div>
        <div class="vol-ticks">
          <span>6</span><span>8</span><span>10</span><span>12</span>
        </div>
        <div class="vol-conseil" id="vol-conseil"></div>
        <div class="vol-bar" id="vol-bar">
          <div class="vb-seg vb-1" id="vol-seg-1"></div>
          <div class="vb-seg vb-2" id="vol-seg-2"></div>
          <div class="vb-seg vb-3" id="vol-seg-3"></div>
        </div>
        <div class="vol-legend">
          <span class="vleg vleg-1">■ Phase 1</span>
          <span class="vleg vleg-2">■ Phase 2</span>
          <span class="vleg vleg-3">■ Phase 3</span>
        </div>
      </div>
      <div id="objectifs-content"><!-- généré par JS --></div>
      <div class="planner-nav">
        <button class="btn-nav btn-prev" onclick="showStep(2)">← Retour</button>
        <button class="btn-nav btn-next" onclick="buildResume();showStep(4)">Voir le résumé →</button>
      </div>
    </div>

    <!-- ── ÉTAPE 4 : Résumé ── -->
    <div class="sub-panel" id="sp4">
      <div class="sp-title" id="sp4-title">Résumé — Course de Relais</div>
      <div class="sp-desc">Vue d'ensemble du cycle planifié — prêt pour impression ou export PDF.</div>

      <div class="resume-grid">
        <div class="r-card">
          <div class="r-card-h">📋 Informations générales</div>
          <div class="r-card-body">
            <div class="r-row"><span class="r-lbl">Classe / Groupe</span><span class="r-val" id="r-classe">—</span></div>
            <div class="r-row"><span class="r-lbl">APS</span><span class="r-val" id="r-aps">Course de Relais</span></div>
            <div class="r-row"><span class="r-lbl">Famille</span><span class="r-val">Athlétisme</span></div>
            <div class="r-row"><span class="r-lbl">Niveau de départ</span><span class="r-val" id="r-niv">—</span></div>
            <div class="r-row"><span class="r-lbl">Total séances</span><span class="r-val" id="r-total">—</span></div>
            <div class="r-row"><span class="r-lbl">Durée / séance</span><span class="r-val" id="r-dur">—</span></div>
          </div>
        </div>
        <div class="r-card">
          <div class="r-card-h">📊 Bilan sélection</div>
          <div class="r-card-body">
            <div class="r-row"><span class="r-lbl">Conduites validées</span><span class="r-val" id="r-ct">—</span></div>
            <div class="r-row"><span class="r-lbl">Objets d'ens. activés</span><span class="r-val" id="r-oe">—</span></div>
            <div class="r-row"><span class="r-lbl" id="lbl-pA">Phase 1 (séances)</span><span class="r-val" id="r-pA">4</span></div>
            <div class="r-row"><span class="r-lbl" id="lbl-pB">Phase 2 (séances)</span><span class="r-val" id="r-pB">4</span></div>
            <div class="r-row"><span class="r-lbl" id="lbl-pC">Phase 3 (séances)</span><span class="r-val" id="r-pC">4</span></div>
          </div>
        </div>
        <div class="r-card r-card-full">
          <div class="r-card-h">📊 Répartition du cycle</div>
          <div class="r-card-body">
            <div class="cycle-bar">
              <div class="cb-seg cb-a" id="cba" style="flex:4">4<small>Phase A</small></div>
              <div class="cb-seg cb-b" id="cbb" style="flex:4">4<small>Phase B</small></div>
              <div class="cb-seg cb-c" id="cbc" style="flex:4">4<small>Phase C</small></div>
            </div>
            <div id="obj-summary"></div>
          </div>
        </div>
        <div class="r-card r-card-full">
          <div class="r-card-h">🎯 Compétences visées (synthèse)</div>
          <div class="r-card-body" id="r-competences" style="font-size:13px;line-height:1.9;color:var(--text)"></div>
        </div>
      </div>

      <div class="planner-nav">
        <button class="btn-nav btn-prev" onclick="showStep(3)">← Modifier</button>
        <div style="display:flex;gap:8px">
          <button class="btn-nav btn-print-r" onclick="window.print()">🖨️ Imprimer</button>
          <button class="btn-nav btn-finish" onclick="exportCycle()">💾 Exporter</button>
        </div>
      </div>
    </div>

  </div>
</div>

<!-- ══ FOOTER ══ -->
<footer>
  <span>CRMEF Inezgane · Section EPS · Planificateur de Cycle d'Apprentissage · 2025/2026</span>
  <span><a href="mailto:a.bouargane@crmefsm.ac.ma">a.bouargane@crmefsm.ac.ma</a></span>
</footer>

<script>
// ══════════ DATA ══════════
const DATA = {
  relais: {
    nom: 'Course de Relais',
    apsView: 'aps-relais',
    phases: {
      A: 'Phase 1 — Construire la continuité du déplacement',
      B: 'Phase 2 — Organiser la zone de transmission',
      C: 'Phase 3 — Affiner la technique de passage'
    },
    conduites: [
      { niv:1, phrase:'Relais discontinu', items:[
        { id:'c1', titre:'Centration sur la prise de bâton', desc:'Le donneur et le receveur focalisés sur la façon de transmettre le bâton plutôt que sur la continuité du déplacement.', hyp:"L'arrivée du partenaire organise l'action" },
        { id:'c2', titre:"Prise à l'arrêt — receveur face au donneur", desc:"La prise de témoin se fait à l'arrêt, le receveur attend d'avoir le bâton en main pour partir.", hyp:"Centration visuelle sur le témoin et la main" },
        { id:'c3', titre:'Percussions et freinages brutaux', desc:"Les relayeurs se percutent, le donneur est obligé de freiner pour éviter le receveur.", hyp:"Absence de coordination spatiale et temporelle" },
      ], ot:"Réaliser un relais 4×50m en transmettant le témoin <strong>en déplacement</strong> dans une zone imposée." },
      { niv:2, phrase:'Relais continu', items:[
        { id:'c4', titre:'Donneur ralentit main tendue longtemps à l\'avance', desc:"Le donneur ralentit à l'approche du receveur, main tendue vers l'avant, longtemps avant leur rencontre.", hyp:"Centrés sur la prise de témoin et l'équilibre en course" },
        { id:'c5', titre:'Receveur part tôt mais ralentit en regardant en arrière', desc:"Le receveur part trop tôt, ralentit et contrôle visuellement toute la transmission.", hyp:"Centration sur la transmission et son moment" },
        { id:'c6', titre:'Transmission sur course lente et regardée', desc:"Les partenaires effectuent la transmission lentement et visuellement.", hyp:"Centration sur les prises de témoin sur une transmission lente" },
      ], ot:"Relais 4×50m en <strong>ajustant les vitesses</strong> et utilisant l'élan autorisé dans la zone réglementaire." },
      { niv:3, phrase:'Relais coordonné', items:[
        { id:'c7', titre:'Donneur à vitesse max — receveur part trop tôt', desc:"Le donneur garde sa vitesse maximale. Le receveur part légèrement trop tôt.", hyp:"Difficulté d'ajuster la vitesse de déplacement" },
        { id:'c8', titre:'Donneur ralentit — receveur parti tard à vitesse max', desc:"Le donneur ralentit pour que le receveur, parti trop tard, soit à vitesse maximale avant la transmission.", hyp:"Centrés sur leur vitesse lors de la transmission" },
      ], ot:"Relais 4×50m avec <strong>technique de transmission efficace</strong> grâce à un repérage et code de communication stabilisé." },
    ],
    oe: [
      { id:'oe1', p:'oep1', tag:'PRIORITAIRE', titre:'Continuité du déplacement', desc:"Maintenir la vitesse de course jusqu'à la transmission. Le donneur ne doit pas freiner.", linked:['c1','c2','c3'] },
      { id:'oe2', p:'oep1', tag:'PRIORITAIRE', titre:"Posture de départ & prise d'info vers l'arrière", desc:"Adopter une posture permettant de prendre des informations vers l'arrière tout en s'élançant.", linked:['c1','c2'] },
      { id:'oe3', p:'oep1', tag:'PRIORITAIRE', titre:'Signal et repère de départ', desc:"Identifier le moment propice pour déclencher le départ du receveur grâce à une marque au sol.", linked:['c4','c5','c6'] },
      { id:'oe4', p:'oep2', tag:'SECONDAIRE', titre:'Dissociation segmentaire', desc:"Conserver la dissociation entre le bras libre et le bras receveur pendant la transmission.", linked:['c5','c6'] },
      { id:'oe5', p:'oep2', tag:'SECONDAIRE', titre:'Attente dynamique du receveur', desc:"Automatiser une attitude d'attente « dynamique » pour réagir dès l'arrivée du donneur.", linked:['c7','c8'] },
      { id:'oe6', p:'oep3', tag:'COMPLÉMENTAIRE', titre:'Affinage technique de la transmission', desc:"Préciser et confirmer les marques, construire et affiner le moment et la technique de transmission.", linked:['c7','c8'] },
    ],
    objectifs: [
      { oe:'oe1', phase:'A', titre:'Découverte & Sécurité de la transmission', ta:"Construire la transmission du témoin en sécurité.\n• Comprendre le rôle de donneur / receveur\n• Adopter une posture de départ avec prise d'info vers l'arrière\n• Situation : relais statique puis en marche (zone 10m)", chips:['Découverte','Situation-problème'] },
      { oe:'oe2', phase:'A', titre:'Continuité du déplacement lors de la transmission', ta:"Maintenir la vitesse de course jusqu'à la transmission.\n• Conserver l'allure à l'approche du receveur\n• Construire la zone de transmission (zone délimitée)\n• Situation : jeu des éponges / relais en couloir", chips:['Continuité','Situation-problème'] },
      { oe:'oe3', phase:'B', titre:"Signal & Repère de départ (marque au sol)", ta:"Identifier le moment propice pour déclencher le départ du receveur.\n• Utiliser des marques au sol pour optimiser le départ\n• Réaliser un départ debout en position optimale\n• Situation : relais avec marque ajustable + chrono", chips:['Signal-marque','Situation-problème','Évaluation'] },
      { oe:'oe4', phase:'B', titre:'Dissociation segmentaire bras libre / bras receveur', ta:"Conserver la dissociation entre le bras libre et le bras receveur.\n• Maintenir la course lors de la réception\n• Réagir rapidement au signal visuel\n• Situation : slalom + transmission / jeu des chronomètres", chips:['Dissociation','Situation-problème'] },
      { oe:'oe5', phase:'C', titre:"Automatisation de l'attente dynamique", ta:"Automatiser l'attitude d'attente « dynamique ».\n• Stabiliser l'ordre des relayeurs et le moment de transmission\n• Placer et fixer sa main au signal\n• Situation : compétition interne 4×50m chronométrée", chips:['Automatisation','Compétition','Évaluation'] },
      { oe:'oe6', phase:'C', titre:'Performance optimale & Évaluation sommative', ta:"Réaliser la meilleure performance en relais 4×50m.\n• Préciser et confirmer les marques\n• Affiner le moment de transmission\n• Évaluation : relais officiel + grille technique + chrono", chips:['Performance','Éval. sommative'] },
    ],
    competences: [
      { niv:'Niv. 1 → 2', txt:"Transmettre et recevoir le témoin <em>en déplacement, dans une zone imposée</em>." },
      { niv:'Niv. 2 → 3', txt:"Ajuster les vitesses du donneur et du receveur en utilisant l'élan autorisé." },
      { niv:'Niv. 3', txt:"Assurer la meilleure coordination des vitesses pour une transmission efficiente." },
    ]
  },
  sl: {
    nom: 'Saut en Longueur',
    apsView: 'aps-sl',
    phases: {
      A: "Phase 1 — Identifier l'appel et enchaîner l'élan",
      B: 'Phase 2 — Construire l\'impulsion vers le haut',
      C: 'Phase 3 — Coordonner et optimiser la performance'
    },
    conduites: [
      { niv:1, phrase:'Le sauteur prudent', items:[
        { id:'sl1', titre:"Course d'élan saccadée et aléatoire", desc:"Le sauteur accélère, ralentit et repart. Élan imprécis et changeant — soit très long, soit très court.", hyp:"Il cherche l'impulsion et a peur de la réception" },
        { id:'sl2', titre:'Impulsion discrète et très brève (piétinement)', desc:"Il piétine à l'approche de la planche, l'impulsion est discrète. Il cherche tout de suite la réception.", hyp:"Centration sur la réception plutôt que l'impulsion" },
        { id:'sl3', titre:'Réception catastrophique — corps projeté', desc:"Réception sur un pied ou pieds décalés. Le corps est projeté sans contrôle.", hyp:"Pas d'anticipation de la chute équilibrée" },
      ], ot:"Enchaîner une course d'élan <strong>progressive, sans rupture</strong> au moment de l'impulsion, pour franchir une distance matérialisée." },
      { niv:2, phrase:'Le sauteur percuteur', items:[
        { id:'sl4', titre:"Difficulté de transit course → saut à la dernière foulée", desc:"Course d'élan correcte et accélérée, mais difficulté à transiter d'un appui de course à un appui de saut.", hyp:"Freinage important durant l'appel" },
        { id:'sl5', titre:"Appel « frappé » et en force — affaissement", desc:"L'appel est frappé violemment, avec affaissement sur la jambe d'appel et blocage partiel.", hyp:"Blocage partiel lors de l'impulsion" },
        { id:'sl6', titre:"Réception groupée ou en déséquilibre arrière", desc:"Réception groupée sur les deux pieds ou en déséquilibre vers l'arrière — perte de distance.", hyp:"Absence d'utilisation des membres libres" },
      ], ot:"Stabiliser une course d'élan accélérée pour se projeter à l'impulsion <strong>vers le haut et vers l'avant</strong> plus loin dans la zone de réception." },
      { niv:3, phrase:'Le coureur-sauteur', items:[
        { id:'sl7', titre:"Course accélérée mais appel imprécis", desc:"La course d'élan est accélérée mais met à l'épreuve la précision de l'appel — pose du pied plat.", hyp:"Tension entre vitesse d'élan et précision de l'appel" },
        { id:'sl8', titre:"Suspension passive — réception sans projection des jambes", desc:"La suspension est une phase passive. La chute ne permet pas une projection des jambes vers l'avant.", hyp:"Augmenter la trajectoire et s'équilibrer en suspension" },
      ], ot:"Après une course d'élan étalonnée et précise, se projeter en <strong>orientant activement les segments libres en suspension</strong> pour augmenter la performance." },
    ],
    oe: [
      { id:'sl-oe1', p:'oep1', tag:'PRIORITAIRE', titre:"Identification & stabilisation du pied d'appel", desc:"Stabiliser le pied d'appel dominant et l'enchaîner sans rupture avec la course.", linked:['sl1','sl2','sl3'] },
      { id:'sl-oe2', p:'oep1', tag:'PRIORITAIRE', titre:"Continuité de l'élan & accélération progressive", desc:"Construire une course d'élan progressive et accélérée sans rupture à l'approche de la planche.", linked:['sl1','sl2'] },
      { id:'sl-oe3', p:'oep1', tag:'PRIORITAIRE', titre:"Rythme des 2 dernières foulées & élan étalonné", desc:"Structurer l'espace d'élan à partir d'un nombre régulier d'appuis et stabiliser le rythme final.", linked:['sl4','sl5'] },
      { id:'sl-oe4', p:'oep2', tag:'SECONDAIRE', titre:"Impulsion vers le haut — gainage & jambe libre", desc:"Se grandir à l'impulsion, rester gainé, utiliser dynamiquement la jambe libre.", linked:['sl4','sl5','sl6'] },
      { id:'sl-oe5', p:'oep2', tag:'SECONDAIRE', titre:"Coordination propulsive en suspension", desc:"Coordonner les actions propulsives de la jambe d'appel avec l'action des segments libres.", linked:['sl7','sl8'] },
      { id:'sl-oe6', p:'oep3', tag:'COMPLÉMENTAIRE', titre:"Chute équilibrée — projection des pieds vers l'avant", desc:"Réaliser une réception équilibrée en projetant les pieds vers l'avant dans le sable.", linked:['sl7','sl8'] },
    ],
    objectifs: [
      { oe:'sl-oe1', phase:'A', titre:"Identification du pied d'appel & continuité de l'élan", ta:"Enchaîner sans ralentir une course et un saut en posant le pied d'appel dans une zone déterminée.\n• Identifier et stabiliser le pied d'appel dominant\n• Mettre en relation la performance et la vitesse d'élan\n• Situation : sauts sur lattes / marques de couleur (zone 1m)", chips:['Découverte','Situation-problème'] },
      { oe:'sl-oe2', phase:'A', titre:"Distance d'élan performante & accélération progressive", ta:"Déterminer la distance d'élan performante et s'élancer de façon progressive.\n• Construire et stabiliser la distance d'élan\n• Franchir une distance matérialisée sans rupture\n• Situation : élan variable 5-7-9-11 appuis + chrono", chips:['Élan','Situation-problème'] },
      { oe:'sl-oe3', phase:'B', titre:"Structuration du rythme des 2 dernières foulées", ta:"Structurer l'espace d'élan à partir d'un nombre régulier d'appuis.\n• Élan précis : bon pied, au bon moment (11-13-15-17 appuis)\n• Stabiliser le rythme des 2 dernières foulées\n• Situation : élan étalonné + repères au sol colorés", chips:['Rythme-élan','Situation-problème','Évaluation'] },
      { oe:'sl-oe4', phase:'B', titre:"Impulsion vers le haut — gainage & action jambe libre", ta:"Se grandir à l'impulsion et utiliser les membres libres.\n• Se grandir à l'impulsion (rester gainé)\n• Action dynamique de la jambe libre vers le haut\n• Situation : saut en contre-haut / haie basse à franchir", chips:['Impulsion','Situation-problème'] },
      { oe:'sl-oe5', phase:'C', titre:"Coordination propulsive jambe d'appel + segments libres", ta:"Coordonner les actions propulsives de la jambe d'appel avec les segments libres.\n• Attitude de course haute lors des 2 dernières foulées\n• Coordonner bras et jambe libre à l'impulsion\n• Situation : saut groupé / saut tendu avec repère hauteur", chips:['Coordination','Situation-problème','Évaluation'] },
      { oe:'sl-oe6', phase:'C', titre:"Chute équilibrée — projection des pieds vers l'avant", ta:"Réaliser une chute équilibrée en projetant les pieds plus loin dans le sable.\n• Stabiliser la course d'élan étalonnée et précise\n• Projeter les pieds vers l'avant lors de la réception\n• Évaluation : saut officiel + mesure + grille technique", chips:['Réception','Éval. sommative'] },
    ],
    competences: [
      { niv:'Niv. 1 → 2', txt:"Enchaîner une course d'élan progressive sans rupture à l'impulsion. Identifier et stabiliser le pied d'appel." },
      { niv:'Niv. 2 → 3', txt:"Stabiliser une course d'élan accélérée (nombre régulier d'appuis) et se projeter vers le haut et vers l'avant. Utiliser la jambe libre et les bras." },
      { niv:'Niv. 3', txt:"Après une course d'élan étalonnée et précise, coordonner les actions propulsives en suspension. Réaliser une chute équilibrée en projetant les pieds vers l'avant." },
    ]
  },

  sprint: {
    nom: 'Course de Sprint',
    apsView: 'aps-sprint',
    phases: {
      A: "Phase 1 — Organiser le départ et courir en ligne",
      B: 'Phase 2 — Construire l\'accélération progressive',
      C: 'Phase 3 — Optimiser la vitesse sur la distance'
    },
    conduites: [
      { niv:1, phrase:'Le coureur spontané', items:[
        { id:'sp1', titre:"Regard vers le starter — mise en action vers le haut", desc:"L'élève porte son regard vers le starter et s'élance vers le haut. Il ne produit pas de déséquilibre vers l'avant.", hyp:"Recherche d'équilibre : peur de tomber vers l'avant" },
        { id:'sp2', titre:"Foulée non structurée — appuis hors de l'axe", desc:"Courir vite = répéter rapidement ses foulées habituelles. Attitude crispée, appuis en dehors de l'axe de course.", hyp:"Pas de différenciation entre foulée de jogging et foulée de sprint" },
        { id:'sp3', titre:"Ralentissement ou arrêt avant la ligne d'arrivée", desc:"L'élève ralentit nettement ou s'arrête avant d'avoir franchi la ligne. Souvent attiré vers le couloir voisin.", hyp:"Absence de maintien de l'effort — course non rectiligne" },
      ], ot:"Prendre un départ debout <strong>organisé vers l'avant</strong> avec une coordination bras-jambes efficace, et courir en ligne droite <strong>sans ralentir brutalement</strong> avant la ligne d'arrivée." },
      { niv:2, phrase:'Le sprinteur précipité', items:[
        { id:'sp4', titre:"Redressement du tronc très précoce (avant 20m)", desc:"L'élève amorce le déséquilibre vers l'avant mais se redresse trop tôt, dès les 5-8 premiers appuis.", hyp:"Départ associé à la mise en action : se redresse avant d'être en vitesse" },
        { id:'sp5', titre:"Vélocité précoce — syncinésies d'équilibration", desc:"Course en fréquence lors des 30 premiers mètres avec mouvements parasites réactionnels (syncinésies bras/tronc). Poussée incomplète sans extension totale de la jambe.", hyp:"Rapport fréquence/amplitude non optimisé" },
        { id:'sp6', titre:"Crispation généralisée — dégradation rapide de la vélocité", desc:"Attitude crispée, difficulté de stabilisation du cycle de jambe antérieur. La tension musculaire globale freine la segmentation.", hyp:"Absence de relâchement sélectif en conservation" },
      ], ot:"Prendre un départ accroupi et réaliser une <strong>mise en action rectiligne et progressive</strong>. Adopter un rapport fréquence-amplitude optimal en fonction des différentes phases de la course." },
      { niv:3, phrase:'Le coureur-sprinteur', items:[
        { id:'sp7', titre:"Relèvement progressif efficace — alignement en construction", desc:"Mise en action progressive dans l'axe. L'alignement pied-bassin-épaule est en cours de stabilisation entre 20 et 40m.", hyp:"Rapport fréquence/amplitude légèrement insuffisant en fin de poussée" },
        { id:'sp8', titre:"Dégradation en fin de course (60-100m)", desc:"La vitesse se dégrade aux 30 derniers mètres par épuisement de la filière anaérobie alactique (créatine-phosphate). L'action des bras est fonctionnelle mais non encore optimale.", hyp:"Lutte active contre la décélération à construire" },
      ], ot:"Prendre ses marques de départ et adopter une <strong>mise en action progressive dans l'axe</strong>. Adopter une attitude dynamique et répartir ses ressources sur la distance pour <strong>retarder la dégradation de la vitesse</strong>." },
    ],
    oe: [
      { id:'sp-oe1', p:'oep1', tag:'PRIORITAIRE', titre:"Départ organisé vers l'avant — réaction au signal & coordination bras-jambes", desc:"Produire un déséquilibre vers l'avant par engagement progressif. Réagir au signal auditif.", linked:['sp1','sp2','sp3'] },
      { id:'sp-oe2', p:'oep1', tag:'PRIORITAIRE', titre:"Courir en ligne droite sans ralentir — maintien de l'effort au-delà de l'arrivée", desc:"Poser les pieds dans l'axe de course et prolonger l'effort 5m après la ligne d'arrivée.", linked:['sp2','sp3'] },
      { id:'sp-oe3', p:'oep1', tag:'PRIORITAIRE', titre:"Départ accroupi — mise en action rectiligne & progressive (redressement progressif)", desc:"Rythme des appuis les 20 premiers mètres. Construire le relèvement progressif du tronc.", linked:['sp4','sp5'] },
      { id:'sp-oe4', p:'oep2', tag:'SECONDAIRE', titre:"Rapport fréquence/amplitude optimal — alignement pied-bassin-épaule", desc:"Extension complète de la jambe d'appui (poussée arrière-bas). Temps de contact réduit — griffe active du sol.", linked:['sp5','sp6'] },
      { id:'sp-oe5', p:'oep2', tag:'SECONDAIRE', titre:"Relâchement sélectif & conservation de la vitesse — 30 derniers mètres", desc:"Retarder la dégradation par relâchement musculaire sélectif (visage, épaules). Filière anaérobie alactique.", linked:['sp7','sp8'] },
      { id:'sp-oe6', p:'oep3', tag:'COMPLÉMENTAIRE', titre:"Performance optimale & distribution des ressources sur la distance totale", desc:"Attitude dynamique sur toute la course. Accélérer par relevé progressif et alignement pied-bassin-épaule.", linked:['sp7','sp8'] },
    ],
    objectifs: [
      { oe:'sp-oe1', phase:'A', titre:"Départ organisé vers l'avant — coordination bras-jambes", ta:"Prendre un départ debout avec déséquilibre vers l'avant.\n• Reconnaître les commandements (à vos marques / prêts / signal)\n• Produire un déséquilibre par engagement progressif du corps\n• Situation : départ debout avec contrastes (talons levés / genoux fléchis) — 3 essais sur 20m\n• Critère : distance aux 10 premiers appuis ≥ repère au sol", chips:['Découverte','Situation-problème'] },
      { oe:'sp-oe2', phase:'A', titre:"Course rectiligne sans ralentir — maintien de l'effort", ta:"Courir en ligne droite sans ralentir ou s'arrêter brutalement.\n• Coordination bras-jambes dans l'axe de course\n• Prolonger l'effort 5m après la ligne\n• Situation : sprint 30m + plot de freinage 5m après l'arrivée\n• Critère : pas de ralentissement perceptible aux 10 derniers mètres", chips:['Axe de course','Situation-problème'] },
      { oe:'sp-oe3', phase:'B', titre:"Départ accroupi — redressement progressif & mise en action dans l'axe", ta:"Réaliser une mise en action rectiligne et progressive depuis un départ accroupi.\n• Rythme des appuis les 20 premiers mètres\n• Relèvement progressif du tronc — nouvel équilibre fréquence/amplitude\n• Situation : marques au sol tous les 2 appuis (0-20m)\n• Starting-block si disponible", chips:['Départ accroupi','Situation-problème','Évaluation'] },
      { oe:'sp-oe4', phase:'B', titre:"Rapport fréquence/amplitude optimal — alignement pied-bassin-épaule", ta:"Construire un rapport fréquence/amplitude favorable.\n• Extension complète de la jambe d'appui (poussée arrière-bas)\n• Griffe active du sol sur avant-pied — temps de contact réduit\n• Situation : haies basses (50cm) sur 30m / contraste sprint 20m vs 40m\n• Critère : alignement pied-bassin-épaule visible entre 20 et 50m", chips:['Fréquence-amplitude','Situation-problème'] },
      { oe:'sp-oe5', phase:'C', titre:"Relâchement sélectif & conservation de la vitesse", ta:"Retarder la dégradation de la vitesse sur les 30 derniers mètres.\n• Relâchement musculaire sélectif (visage, épaules, mâchoire)\n• 4 × 60m avec chrono aux 30m et 60m — calculer indice de conservation\n• Critère de réussite : écart V30 / V60 < 0,3s\n• Travail spécifique filière anaérobie alactique (< 8s, récupération complète)", chips:['Relâchement','Évaluation'] },
      { oe:'sp-oe6', phase:'C', titre:"Performance optimale & évaluation sommative", ta:"Réaliser la meilleure performance sur 50 ou 100m.\n• Attitude dynamique sur toute la course (départ → franchissement ligne)\n• Relevé progressif, alignement pied-bassin-épaule, action des bras\n• Évaluation : sprint officiel 50 ou 100m + grille technique\n• Indicateur : performance + régularité sur 3 essais", chips:['Performance','Éval. sommative'] },
    ],
    competences: [
      { niv:'Niv. 1 → 2', txt:"Prendre un départ debout organisé vers l'avant avec coordination bras-jambes efficace, et courir en ligne droite sans ralentir brutalement avant l'arrivée." },
      { niv:'Niv. 2 → 3', txt:"Réaliser un départ accroupi avec mise en action progressive et rectiligne. Construire un rapport fréquence/amplitude favorable par relèvement progressif du tronc." },
      { niv:'Niv. 3', txt:"Réaliser la meilleure performance sur 50-100m : mise en action dans l'axe, rapport fréquence/amplitude optimal, relâchement sélectif pour retarder la dégradation de la vitesse." },
    ]
  },

  basketball: {
    nom: 'Basketball',
    apsView: 'aps-basketball',
    phases: {
      A: 'Phase 1 — Différencier les rôles et progresser vers la cible',
      B: 'Phase 2 — Construire un jeu collectif organisé',
      C: 'Phase 3 — Développer un jeu varié et adapté à la défense'
    },
    conduites: [
      { niv:1, phrase:'La grappe', items:[
        { id:'bb1', titre:"Regroupement autour du ballon — jeu en paquet", desc:"Tous les joueurs (attaquants ET défenseurs) convergent vers le ballon. L'équipe se déplace en bloc au gré des mouvements hasardeux de la balle.", hyp:"Le joueur cherche à avoir le ballon plutôt qu'à marquer — centration sur l'objet, pas sur la cible." },
        { id:'bb2', titre:"Indifférenciation attaquant / défenseur", desc:"Il n'y a que celui qui a la balle et tous les autres qui cherchent à l'avoir. Aucune distinction de rôles ni de camp.", hyp:"Absence de représentation du jeu collectif — chaque joueur agit comme s'il était seul avec le ballon." },
        { id:'bb3', titre:"Déplacements hasardeux sans intention tactique", desc:"Les trajectoires sont erratiques, sans recherche de position favorable. Le joueur ne regarde pas la cible avant d'avoir le ballon.", hyp:"Pas de prise d'information préalable — réaction au ballon plutôt qu'anticipation du jeu." },
      ], ot:"Progresser collectivement vers la cible en <strong>différenciant les rôles</strong> de porteur et non-porteur de balle, et reconnaître la cible à atteindre." },
      { niv:2, phrase:'Le gagne-terrain', items:[
        { id:'bb4', titre:"Jeu en couloir central — progression rectiligne", desc:"L'intention est de progresser vers le panier, mais le jeu est concentré dans le couloir central. Les couloirs latéraux sont ignorés.", hyp:"Le joueur identifie la cible mais ne conçoit pas encore l'espace latéral comme ressource — le chemin le plus court semble le meilleur." },
        { id:'bb5', titre:"Jeu précipité — tir dès l'entrée en zone", desc:"Dès que la balle arrive en zone de marque, le tir est systématique quelle que soit la position. Pas d'attente d'une meilleure opportunité.", hyp:"Seule intention : progresser vers la cible — la notion de position favorable de tir n'est pas encore construite." },
        { id:'bb6', titre:"NPB passifs — jeu individuel du porteur", desc:"Chaque non-porteur agit comme s'il était seul avec le porteur. Pas de démarquage actif, pas d'appels de balle coordonnés.", hyp:"Absence de lecture collective — le NPB attend la balle sans se créer d'espace ni proposer de solution au porteur." },
      ], ot:"Assurer des montées de balle vers l'espace de marque en organisant des <strong>relations porteur / non-porteurs en appui et en soutien</strong>, et choisir entre défense sur porteur et défense sur non-porteur." },
      { niv:3, phrase:"L'attaque stéréotypée", items:[
        { id:'bb7', titre:"Jeu rapide stéréotypé — attaque prévisible", desc:"Les attaquants privilégient systématiquement le jeu rapide. Les actions sont prévisibles et facilement contestées par une défense organisée.", hyp:"Les joueurs ont automatisé un schéma simple mais manquent de solutions alternatives pour déjouer une défense placée." },
        { id:'bb8', titre:"Difficultés de relation intérieur / extérieur", desc:"En attaque placée, difficultés à créer des relations entre joueurs intérieurs (raquette) et extérieurs (périphérie), côté ballon et côté opposé.", hyp:"Absence de lecture défensive pour varier les solutions — le joueur répète sa solution habituelle sans analyser le placement adverse." },
        { id:'bb9', titre:"Duels 1c1 non exploités collectivement", desc:"Des duels 1 contre 1 apparaissent mais les partenaires ne créent pas de situations favorables pour exploiter le déséquilibre provoqué.", hyp:"Le joueur ne connecte pas le duel individuel à l'organisation collective — la lecture du déséquilibre créé n'est pas partagée." },
      ], ot:"Construire un jeu offensif <strong>varié et adapté à la défense</strong> par des combinaisons intérieur / extérieur, et exploiter les duels 1c1 dans une organisation collective." },
    ],
    oe: [
      { id:'bb-oe1', p:'oep1', tag:'PRIORITAIRE', titre:"Différenciation des rôles PB / NPB et progression vers la cible", desc:"Construire la distinction porteur / non-porteur. Identifier et viser la cible adverse dès la possession de balle.", linked:['bb1','bb2','bb3'] },
      { id:'bb-oe2', p:'oep1', tag:'PRIORITAIRE', titre:"Prise d'information préalable à l'action", desc:"Lever la tête avant de recevoir la balle pour voir partenaires et adversaires. Décider avant de recevoir : passer, dribbler ou tirer.", linked:['bb2','bb3'] },
      { id:'bb-oe3', p:'oep1', tag:'PRIORITAIRE', titre:"Organisation offensive — appui et soutien du porteur", desc:"NPB en appui (devant, en avance) et en soutien (derrière, en retrait). Élargir l'espace de jeu par les couloirs latéraux.", linked:['bb4','bb5','bb6'] },
      { id:'bb-oe4', p:'oep2', tag:'SECONDAIRE', titre:"Choix défensifs — porteur ou non-porteur libre", desc:"Choisir entre harceler le porteur pour gêner la passe ou couvrir un NPB libre pour l'empêcher de recevoir.", linked:['bb5','bb6'] },
      { id:'bb-oe5', p:'oep2', tag:'SECONDAIRE', titre:"Jeu intérieur / extérieur — combinaisons et déséquilibres", desc:"Créer et exploiter des déséquilibres défensifs par des combinaisons entre joueurs intérieurs (raquette) et extérieurs (périphérie).", linked:['bb7','bb8','bb9'] },
      { id:'bb-oe6', p:'oep3', tag:'COMPLÉMENTAIRE', titre:"Adaptation au contexte défensif — contre-attaque ou attaque placée", desc:"Lire rapidement le contexte après récupération et choisir entre jeu rapide (contre-attaque) ou jeu placé (attaque organisée).", linked:['bb7','bb8','bb9'] },
    ],
    objectifs: [
      { oe:'bb-oe1', phase:'A', titre:"Identifier la cible et différencier les rôles PB / NPB", ta:"Reconnaître la cible adverse et s'orienter vers elle dès la possession de balle.\n• Identifier clairement la cible à atteindre (panier adverse)\n• Distinguer son rôle : PB (progresser, protéger) vs NPB (se démarquer, soutenir)\n• Situation : 2×2 sur demi-terrain — comptabiliser tirs tentés vs passes réalisées", chips:['Découverte','Situation-problème'] },
      { oe:'bb-oe2', phase:'A', titre:"Prendre des informations avant et pendant la possession", ta:"Développer la prise d'information préalable à l'action.\n• Lever la tête avant de recevoir la balle — voir partenaires et adversaires\n• Décider avant de recevoir : passer, dribbler ou tirer\n• Situation : 3×3 avec temps de possession limité (5 secondes)", chips:['Prise d\'info','Situation-problème'] },
      { oe:'bb-oe3', phase:'B', titre:"Organiser les déplacements en appui et soutien", ta:"Créer des solutions au porteur par des déplacements coordonnés des NPB.\n• NPB en appui devant (relai offensif) et en soutien derrière (sécurité)\n• Utiliser les couloirs latéraux pour élargir l'espace de jeu\n• Situation : 3×3 avec bonus si passe vers un joueur en mouvement", chips:['Jeu collectif','Situation-problème','Évaluation'] },
      { oe:'bb-oe4', phase:'B', titre:"Construire les comportements défensifs collectifs", ta:"Développer une défense organisée sur porteur et non-porteurs.\n• Monter sur le porteur pour gêner la progression et la passe\n• Couvrir un NPB libre — couper les lignes de passe\n• Situation : 3×3 défensif — comptabiliser interceptions + reconquêtes", chips:['Défense','Situation-problème','Évaluation'] },
      { oe:'bb-oe5', phase:'C', titre:"Créer des déséquilibres par le jeu intérieur / extérieur", ta:"Exploiter les espaces créés par les combinaisons intérieur / extérieur.\n• Passe en profondeur vers un joueur coupant dans la raquette\n• Duel 1c1 exploité collectivement — partenaires prêts au rebond\n• Situation : 4×4 avec bonus si tir précédé d'une combinaison int./ext.", chips:['Combinaisons','Situation-problème','Évaluation'] },
      { oe:'bb-oe6', phase:'C', titre:"Adapter le jeu au contexte défensif — contre-attaque ou attaque placée", ta:"Lire rapidement la défense après récupération et choisir la bonne solution.\n• Défense non replacée → jeu rapide (contre-attaque, surnombre)\n• Défense replacée → attaque placée avec circulation intérieur/extérieur\n• Évaluation : match 4×4 complet avec grille d'observation collective", chips:['Lecture défense','Éval. sommative'] },
    ],
    competences: [
      { niv:'Niv. 1 → 2', txt:"Reconnaître la cible adverse et progresser vers elle en différenciant les rôles de porteur et non-porteur de balle. Prendre des informations avant de recevoir la balle." },
      { niv:'Niv. 2 → 3', txt:"Assurer des montées de balle organisées avec NPB en appui et en soutien. Élargir l'espace de jeu par les couloirs latéraux. Choisir entre défense sur porteur ou couverture d'un NPB libre." },
      { niv:'Niv. 3', txt:"Construire un jeu offensif varié adapté à la défense : combinaisons intérieur/extérieur, exploitation des duels 1c1, choix entre contre-attaque et attaque placée selon le contexte défensif." },
    ]
  },

  volleyball: {
    nom: 'Volleyball',
    apsView: 'aps-volleyball',
    phases: {
      A: 'Phase 1 — Construire le renvoi régulier et orienté vers la cible',
      B: 'Phase 2 — Organiser le jeu en relais et différencier les rôles',
      C: 'Phase 3 — Construire l\'attaque en 3 touches et mettre l\'adversaire en difficulté'
    },
    conduites: [
      { niv:1, phrase:'Le sauveur', items:[
        { id:'ct-vb1', titre:"Frappes explosives et inadaptées — l'adversaire c'est la balle", desc:"L'élève frappe la balle de façon explosive pour l'empêcher de tomber. Le geste est réactif, souvent à une main, sans maîtrise de la force ni de la direction. La peur de la balle est présente.", hyp:"L'intention qui prime est de frapper, pas de renvoyer. La balle est vécue comme l'unique adversaire — le camp adverse n'existe pas encore comme cible." },
        { id:'ct-vb2', titre:"Peu de mobilité — pas de lecture de trajectoire", desc:"L'élève reste statique, attend que la balle arrive sur lui. Lecture de trajectoire tardive ou absente — le joueur réagit après l'arrivée de la balle, pas avant.", hyp:"Centration optimale sur la balle : toute l'attention est focalisée sur l'objet, ce qui empêche toute anticipation du déplacement et toute prise d'information sur l'espace." },
        { id:'ct-vb3', titre:"Absence de coopération — notion de rôle inexistante", desc:"Les joueurs sont côte à côte sans relation. Chacun joue pour lui-même. Pas de communication, pas d'organisation. La notion de réceptionneur / non-réceptionneur n'est pas construite.", hyp:"La centration sur la balle rend la notion de rôle inexistante — le partenaire n'existe pas encore comme ressource. Les interventions sur la balle sont individuelles et maladroites." },
      ], ot:"Frapper la balle <strong>sans appréhension</strong>, se déplacer pour aller à sa rencontre, et l'orienter vers la cible adverse — <strong>passer du jeu de sauvegarde au renvoi orienté</strong>." },
      { niv:2, phrase:'Le renvoyeur', items:[
        { id:'ct-vb4', titre:"Renvoi direct systématique — jeu similaire au tennis", desc:"L'intention est de renvoyer la balle directement dans le camp adverse dès la première touche. Pas de conservation ni de relais. Le jeu ressemble à du tennis : renvoi immédiat dès contact.", hyp:"Le joueur différencie maintenant l'espace adverse mais conçoit encore le volleyball comme un jeu de renvoi direct — la construction du jeu en plusieurs touches n'est pas encore représentée." },
        { id:'ct-vb5', titre:"NPB joueur de soutien passif — pas de relais organisé", desc:"Le non-porteur de balle n'intervient qu'en cas de faute du porteur. Il se contente d'empêcher la balle de tomber dans le camp, sans anticiper ni se déplacer vers une position favorable.", hyp:"Le NPB n'a pas encore construit son rôle de relais. Il est « joueur soutien » (réactif) et non « joueur relais » (proactif). La coopération reste ponctuelle et non intentionnelle." },
        { id:'ct-vb6', titre:"Grappe dynamique près du filet — espace non différencié", desc:"Les joueurs se concentrent dynamiquement près du filet. L'espace arrière est délaissé. Aucune distinction entre zone de défense et zone d'attaque. Aucune situation favorable de marque n'apparaît.", hyp:"Le filet est l'objectif immédiat mais les zones du terrain n'ont pas encore de valeur différenciée. L'espace est vécu comme global et non structuré en zone arrière / zone avant." },
      ], ot:"Passer du renvoi direct au <strong>renvoi construit avec relais</strong> : systématiser le renvoi haut vers la zone avant, construire le rôle de joueur relais, différencier l'espace défensif et offensif." },
      { niv:3, phrase:'Le constructeur', items:[
        { id:'ct-vb7', titre:"Dispositif étagé construit mais attaques peu variées", desc:"Les joueurs adoptent un dispositif arrières / avants et utilisent des relais. Le jeu se construit en 2-3 touches. Mais les attaques restent stéréotypées et prévisibles — l'adversaire n'est pas mis en difficulté.", hyp:"Le relais est construit mais la lecture du dispositif défensif adverse est absente. Le joueur attaque là où il peut, pas là où l'adversaire n'est pas." },
        { id:'ct-vb8', titre:"Relations avants / arrières difficiles — avants dos au filet", desc:"Les arrières envoient la balle vers l'avant mais les avants sont dos au filet pour attaquer. Les relations entre la zone arrière et la zone avant restent difficiles, notamment sur balle haute.", hyp:"Construction incomplète du rôle de passeur — l'avant ne sait pas encore s'orienter face au jeu pour transmettre la balle vers le côté libre tout en permettant une attaque efficace." },
        { id:'ct-vb9', titre:"Peu d'échanges suite au risque de perte de balle — maîtrise imparfaite", desc:"Encore peu d'échanges longs : le risque de perte de balle freine l'engagement dans des combinaisons. La maîtrise des frappes (manchette, passe haute) n'est pas encore automatisée.", hyp:"L'incertitude sur la réussite technique inhibe la prise de risque tactique — le joueur préfère le renvoi direct à la construction sur 3 touches quand la situation devient incertaine." },
      ], ot:"Construire une <strong>attaque coordonnée en 3 touches</strong> (réception → relais passeur → attaque) pour mettre l'adversaire dans l'impossibilité de renvoyer — balle au fond, balle tendue, balle là où l'adversaire n'est pas." },
    ],
    oe: [
      { id:'vb-oe1', p:'oep1', tag:'PRIORITAIRE', titre:"Déplacement anticipé et frappe maîtrisée", desc:"Se déplacer pour se placer sous la balle avant son arrivée. Doser l'énergie transmise — frapper sans appréhension avec force et direction contrôlées. Dépasser la peur de la balle.", linked:['ct-vb1','ct-vb2','ct-vb3'] },
      { id:'vb-oe2', p:'oep1', tag:'PRIORITAIRE', titre:"Orientation du renvoi vers la cible adverse", desc:"Renvoyer la balle vers l'espace arrière adverse et non vers le filet. Construire la représentation de la cible — différencier 'défendre son camp' de 'attaquer le camp adverse'.", linked:['ct-vb1','ct-vb4','ct-vb6'] },
      { id:'vb-oe3', p:'oep1', tag:'PRIORITAIRE', titre:"Différenciation des rôles R / NR — construction du relais", desc:"Différencier le rôle de réceptionneur (R) qui intervient sur la balle et le non-réceptionneur (NR) qui se déplace en position de relais. Passer du joueur soutien passif au joueur relais proactif.", linked:['ct-vb3','ct-vb4','ct-vb5','ct-vb6'] },
      { id:'vb-oe4', p:'oep2', tag:'SECONDAIRE', titre:"Construction du dispositif étagé — zone arrière / zone avant", desc:"Occuper et différencier la zone arrière (défense, réception) et la zone avant (attaque, relais). Systématiser le renvoi haut et lent vers la zone avant pour donner du temps aux partenaires.", linked:['ct-vb5','ct-vb6','ct-vb7'] },
      { id:'vb-oe5', p:'oep2', tag:'SECONDAIRE', titre:"Construction du rôle de passeur — relais en zone avant", desc:"Le joueur arrière envoie une balle haute orientée vers le passeur (zone avant). Le passeur s'oriente face au jeu pour transmettre la balle vers l'attaquant libre.", linked:['ct-vb7','ct-vb8'] },
      { id:'vb-oe6', p:'oep3', tag:'COMPLÉMENTAIRE', titre:"Attaque en 3 touches — lire et mettre en difficulté", desc:"Construire et enchaîner la séquence réception → passe passeur → attaque. Lire le dispositif défensif adverse pour choisir où attaquer (fond de terrain, zone libre, balle tendue).", linked:['ct-vb8','ct-vb9'] },
    ],
    objectifs: [
      { oe:'vb-oe1', phase:'A', titre:"Frapper la balle et se déplacer pour aller à sa rencontre", ta:"Construire le déplacement anticipé et la frappe maîtrisée.\n• Se placer sous la balle avant son arrivée — anticiper la trajectoire\n• Doser la force de frappe : balle haute et lente (pas explosive)\n• Situation de référence : 2×2 terrain réduit (4,5m×7m) — ratio balles touchées / balles non touchées", chips:['Découverte','Situation-problème'] },
      { oe:'vb-oe2', phase:'A', titre:"Orienter le renvoi vers la cible adverse — fond du terrain", ta:"Passer du renvoi hasardeux au renvoi orienté vers la cible.\n• Identifier et viser la zone arrière adverse (pas le filet)\n• Transformer la représentation : de 'empêcher de tomber' à 'attaquer la cible'\n• Situation : zones cibles matérialisées au sol — bonus si balle dans la zone arrière adverse", chips:['Cible','Situation-problème'] },
      { oe:'vb-oe3', phase:'B', titre:"Construire le relais — différencier R et NR, passer au joueur relais", ta:"Organiser la coopération offensive entre partenaires.\n• R annonce verbalement son intention d'intervenir\n• NR anticipe et se déplace vers une position de relais proactive\n• Situation : 3×3 — point bonus si la balle est touchée par 2 joueurs avant renvoi\n• Critère de réalisation observable : NR en déplacement avant l'arrivée de la balle", chips:['Relais','Situation-problème','Évaluation'] },
      { oe:'vb-oe4', phase:'B', titre:"Construire le dispositif étagé — différencier zone défensive et offensive", ta:"Différencier l'occupation de l'espace défensif et offensif.\n• Arrières : déplacement vers la balle + renvoi haut vers la zone avant\n• Avants : placement face au jeu + orientation vers l'espace libre adverse\n• Situation : 3×3 avec zones matérialisées — grille d'observation placement avant/arrière", chips:['Espace','Situation-problème','Évaluation'] },
      { oe:'vb-oe5', phase:'C', titre:"Construire l'enchaînement en 3 touches — réception → passe → attaque", ta:"Enchaîner les 3 rôles de jeu : réceptionneur, passeur, attaquant.\n• Réception haute orientée vers le passeur en zone avant\n• Passeur face au jeu — passe vers l'attaquant en position favorable\n• Situation : 4×4 — point bonus si renvoi construit en 3 touches dans la zone arrière adverse", chips:['3 touches','Situation-problème','Évaluation'] },
      { oe:'vb-oe6', phase:'C', titre:"Lire le dispositif défensif adverse et attaquer l'espace libre", ta:"Développer la lecture du jeu adverse pour varier et efficacité les attaques.\n• Observer le placement défensif adverse avant d'attaquer\n• Choisir entre : attaque fond de terrain / balle tendue près du filet / zone libre latérale\n• Évaluation sommative : match 4×4 — grille observables + schéma topographique des impacts (Deconinck & Fontaine, 2002)", chips:['Lecture','Éval. sommative'] },
    ],
    competences: [
      { niv:'Niv. 1 → 2', txt:"Se déplacer pour frapper la balle sans appréhension. Maîtriser la force et la direction du renvoi pour l'orienter vers la cible adverse. Signaler verbalement son intention d'intervenir et organiser un relais simple avec ses partenaires." },
      { niv:'Niv. 2 → 3', txt:"Différencier le rôle de réceptionneur et de non-réceptionneur. Construire un dispositif étagé zone arrière / zone avant. Systématiser le renvoi haut et orienté vers le passeur en zone avant pour préparer l'attaque." },
      { niv:'Niv. 3', txt:"Construire une attaque coordonnée en 3 touches (réception → passe passeur → attaque). Lire le dispositif défensif adverse pour attaquer l'espace libre — fond de terrain, zone latérale, balle tendue près du filet." },
    ]
  },

  // ══════════════════════════════════════════════════════════════
  // COURSE DE DURÉE
  // Réf. : Bergé F. (2000) · Cazorla G. (2014) · Swain (1994)
  // ══════════════════════════════════════════════════════════════
  duree: {
    nom: 'Course de Durée',
    apsView: 'aps-duree',
    phases: {
      A: 'Phase 1 — Construire la régularité et les repères d\'allure',
      B: 'Phase 2 — Exploiter la puissance aérobie et progresser en performance',
      C: 'Phase 3 — Construire le projet de course et gérer la confrontation'
    },
    conduites: [
      { niv:1, phrase:'Le coureur spontané', items:[
        { id:'cd1', titre:'Départ trop rapide → essoufflement et abandon', desc:"L'élève part à une intensité maximale et s'essouffle rapidement. Il abandonne ou marche dès la 2ᵉ minute.", hyp:"Courir vite = courir fort — absence de notion d'allure régulée" },
        { id:'cd2', titre:'Allure irrégulière entrecoupée de marche', desc:"L'élève alterne des phases de course rapide et de marche sans aucun repère temporel ou spatial.", hyp:"Absence de repères internes (sensations) et externes (temps/espace)" },
        { id:'cd3', titre:'Absence de repères pour réguler l\'intensité', desc:"L'élève ne dispose d'aucun indicateur (VMA, FC, temps de passage) pour ajuster son effort à la durée prévue.", hyp:"L'élève ignore sa VMA et ne sait pas la mettre en relation avec l'allure" },
      ], ot:"Courir <strong>sans s'arrêter</strong> sur la durée prévue, à une allure continue et régulière, en utilisant des repères sonores et visuels pour maintenir l'intensité." },
      { niv:2, phrase:'Le régulier insuffisant', items:[
        { id:'cd4', titre:'Allure régulière mais % VMA insuffisant', desc:"L'élève court régulièrement mais à une intensité trop faible (< 65 % VMA). Il n'exploite pas sa puissance aérobie.", hyp:"Régularité acquise mais relation allure-performance non construite" },
        { id:'cd5', titre:'Incapacité à différencier les allures selon l\'intensité visée', desc:"L'élève ne sait pas moduler son allure selon l'objectif (continu, intermittent, cadence). Il court toujours à la même vitesse perçue.", hyp:"Absence de lien entre % VMA, FC et effort ressenti" },
        { id:'cd6', titre:'Projet de performance non construit', desc:"L'élève ne peut pas annoncer de projet de vitesse ni contrôler l'écart entre projet et réalisation.", hyp:"Connaissances sur le % VMA et la gestion de l'allure non intégrées" },
      ], ot:"Réaliser la meilleure performance sur la distance/durée prévue à une vitesse <strong>proche de son allure de référence % VMA</strong>, en maîtrisant une allure assez régulière." },
      { niv:3, phrase:'Le coureur-stratège', items:[
        { id:'cd7', titre:'Course régulière proche du % VMA — projet non optimisé', desc:"L'élève court régulièrement et proche de son % VMA de référence, mais ne prépare pas de projet de course précis ni de stratégie pour améliorer sa performance.", hyp:"Relation allure-performance construite mais planification autonome absente" },
        { id:'cd8', titre:'Incapacité à réagir aux changements de rythme adverses', desc:"L'élève est déstabilisé par les variations d'allure imposées par un adversaire lors de la confrontation collective.", hyp:"Gestion de l'effort en confrontation : priorité à la réaction sur la planification" },
      ], ot:"Réaliser la meilleure performance en <strong>confrontation collective</strong>, en conservant l'allure de référence % VMA assez régulièrement et le plus longtemps possible grâce à un projet de course préparé." },
    ],
    oe: [
      { id:'cd-oe1', p:'oep1', tag:'PRIORITAIRE', titre:'Régulation de l\'allure par les repères externes (balises, signaux sonores)', desc:"Utiliser des repères spatiaux et temporels (balises, signaux sonores, temps de passage) pour courir longtemps à allure régulière.", linked:['cd1','cd2','cd3'] },
      { id:'cd-oe2', p:'oep1', tag:'PRIORITAIRE', titre:'Construction et contrôle du projet d\'allure (% VMA)', desc:"Établir sa VMA par le test Léger-Mercier. Déterminer les allures cibles en % VMA. Utiliser les tableaux de temps de passage.", linked:['cd2','cd3'] },
      { id:'cd-oe3', p:'oep1', tag:'PRIORITAIRE', titre:'Relation allure-performance — augmenter progressivement le % VMA', desc:"Comprendre et mettre en pratique la relation entre % VMA, durée d'effort supportable et performance.", linked:['cd4','cd5'] },
      { id:'cd-oe4', p:'oep2', tag:'SECONDAIRE', titre:'Intégration des formes d\'entraînement (continu, intermittent, cadence)', desc:"Distinguer et utiliser continu, intermittent long-long, intermittent court-court et cadence rythmée pour développer la puissance aérobie.", linked:['cd5','cd6'] },
      { id:'cd-oe5', p:'oep2', tag:'SECONDAIRE', titre:'Projet de course : prévoir et réaliser à ± 0,5 km/h', desc:"Construire un projet de performance : annoncer une vitesse cible en % VMA, courir, et analyser l'écart projet-réalisation.", linked:['cd6','cd7'] },
      { id:'cd-oe6', p:'oep3', tag:'COMPLÉMENTAIRE', titre:'Gestion de la confrontation et adaptation tactique en course', desc:"Réagir aux changements de rythme adverses. Maintenir le projet de course malgré la pression collective (course fantôme, opposition directe).", linked:['cd7','cd8'] },
    ],
    objectifs: [
      { oe:'cd-oe1', phase:'A', titre:'Courir sans s\'arrêter — allure continue avec repères externes', ta:"Construire la continuité du déplacement à allure régulière grâce aux repères sonores et visuels.\n• Déterminer sa VMA par le test de 6 min (Léger-Mercier)\n• Courir en continu 12 min à 65–70 % VMA avec repères sonores (coup de sifflet / 30'')\n• Utiliser balises et temps de passage pour réguler l'allure\n• Rôles : coureur + chronométreur/observateur (binôme)\n• Critère : aucun arrêt sur la durée prévue", chips:['Test VMA','Régularité','Situation-problème'] },
      { oe:'cd-oe2', phase:'A', titre:'Ajuster l\'allure à la distance/durée — tableau % VMA', ta:"Utiliser sa VMA pour calculer les allures cibles et contrôler l'effort.\n• Construire le tableau personnel d'allures (60 / 70 / 80 / 85 % VMA)\n• Calculer la distance théorique à couvrir selon % VMA et durée\n• Comparer distance réalisée vs distance théorique\n• Continu 15–18 min à 70 % VMA\n• Critère : écart < 5 % entre distance visée et distance réalisée", chips:['% VMA','Tableau allures','Évaluation'] },
      { oe:'cd-oe3', phase:'B', titre:'Augmenter le % VMA en maintenant la régularité (continu avec rythme)', ta:"Exploiter la puissance aérobie longue pour progresser en performance.\n• Fartlek / continu avec rythme : 6–12–18 min à 75–85 % VMA\n• Intermittent long-long : (2'–3') × 1,5–3 km à 85–95 % VMA, récup 1'30–2'\n• Annoncer un projet de vitesse avant chaque séquence\n• Critère : tenir l'allure cible sur ≥ 80 % de la durée, écart ≤ 1 km/h", chips:['Puissance aérobie','Intermittent','Situation-problème','Évaluation'] },
      { oe:'cd-oe4', phase:'B', titre:'Utiliser l\'intermittent court-court pour développer la puissance maximale aérobie', ta:"Solliciter le VO₂max par le travail intermittent court-court à haute intensité.\n• Intermittent court-court : 30''/30'' × 10–15 rép. à 95–110 % VMA\n• Alterner avec cadence rythmée : (1'–3') × (1,5–3 × dist. course)\n• Identifier les sensations à chaque zone d'intensité (80 / 95 / 110 % VMA)\n• Critère : compléter la série sans réduire la distance par répétition de > 10 %", chips:['Intermittent ct-ct','VO₂max','Sensations'] },
      { oe:'cd-oe5', phase:'C', titre:'Projet de course — annoncer, réaliser, analyser (± 0,5 km/h)', ta:"Construire et valider un projet de performance individuel sur la durée cible.\n• Annoncer un % VMA cible et la distance correspondante\n• Courir la séquence et relever la distance réelle\n• Analyser l'écart : expliquer les ajustements à apporter\n• Fiche de suivi individuelle : VMA · allure cible · réalisation · commentaire\n• Critère de réussite : réalisation à ± 0,5 km/h du projet sur 3 séquences consécutives", chips:['Projet performance','Auto-évaluation','Évaluation'] },
      { oe:'cd-oe6', phase:'C', titre:'Gestion de la confrontation — course fantôme et évaluation sommative', ta:"Réaliser la meilleure performance en opposition collective en conservant l'allure de référence.\n• Course en mode fantôme : départ décalé (handicap individualisé) → arrivée commune\n• S'entraîner à maintenir le projet de course face aux variations de rythme adverses\n• Évaluation sommative : performance + grille technique (régularité, projet annoncé, écart)\n• Bilan de cycle : évolution VMA séance 1 → séance finale\n• Critère : maintenir l'allure de référence sur ≥ 85 % de la durée en confrontation", chips:['Course fantôme','Confrontation','Éval. sommative'] },
    ],
    competences: [
      { niv:'Niv. 1 → 2', txt:"Courir sans s'arrêter sur la durée prévue, à une allure continue et régulière ≥ 85 % VMA, en utilisant des repères externes (balises, signaux sonores, temps de passage) pour maintenir l'intensité." },
      { niv:'Niv. 2 → 3', txt:"Exploiter la puissance aérobie pour réaliser la meilleure performance à l'allure de référence % VMA. Utiliser le travail intermittent et la cadence pour augmenter progressivement le % VMA." },
      { niv:'Niv. 3', txt:"Construire un projet de course personnalisé (% VMA cible, distance annoncée) et le réaliser à ± 0,5 km/h. Gérer la confrontation collective en conservant l'allure de référence malgré les variations imposées." },
    ]
  },

  // ══════════════════════════════════════════════════════════════
  // COURSE DE HAIES
  // Réf. : Lamotte V. (2002) · Dhellemmes R. (1995)
  // Revue EPS n°293 — « Contenus : un exemple en course de haies »
  // ══════════════════════════════════════════════════════════════
  haies: {
    nom: 'Course de Haies',
    apsView: 'aps-haies',
    phases: {
      A: 'Phase 1 — Intégrer le franchissement dans la course',
      B: 'Phase 2 — Organiser le franchissement et la trajectoire',
      C: 'Phase 3 — Organiser la reprise de course après la haie'
    },
    conduites: [
      { niv:1, phrase:'Le sauteur de haies', items:[
        { id:'ch1', titre:'Franchissement très aérien — course en accordéon', desc:"L'élève piétine avant la haie et marque un temps d'arrêt après. Le parcours est une addition de franchissements sans continuité de course.", hyp:"La haie est vécue comme un obstacle à éviter impérativement — passage sécuritaire très haut qui induit un piétinement avant et un affaissement à la réception" },
        { id:'ch2', titre:'Impulsion proche de la haie — réception en double appui', desc:"L'élève s'impulse très près de la haie et réceptionne les deux pieds en même temps, ce qui stoppe sa course.", hyp:"Centration sur l'obstacle : peur de chuter — recherche d'équilibre au détriment de la continuité" },
        { id:'ch3', titre:'Saut très haut — jambe arrière en crochet sous la haie', desc:"L'élève passe la jambe arrière en dessous de la haie (crochet) avec les bras écartés pour s'équilibrer.", hyp:"Absence de représentation du franchissement rasant — la haie est contournée verticalement" },
      ], ot:"Courir <strong>sans s'arrêter</strong> entre les haies, franchir en intégrant la haie comme une cible à franchir (et non un obstacle à éviter), en adoptant un rythme régulier (4 ou 6 appuis inter-obstacles)." },
      { niv:2, phrase:'Le planeur', items:[
        { id:'ch4', titre:'Course en 4 appuis non rythmée (1-2, 3-4) — franchissement encore haut', desc:"L'élève court en 4 appuis entre les haies mais sans rythme régulier (1-2, pause, 3-4). Le franchissement reste haut — l'élève « plane ».", hyp:"La continuité de course est assurée, mais l'élève n'organise pas sa trajectoire par rapport à l'obstacle — il n'a pas compris l'intérêt de franchir en descendant" },
        { id:'ch5', titre:'Impulsion et réception à égale distance de la haie (1/2 — 1/2)', desc:"L'élève s'impulse et réceptionne à égale distance de l'obstacle. La jambe arrière passe sur le côté mais traîne derrière.", hyp:"Inutilité de la trajectoire : l'élève continue de sauter plutôt que de courir sur la haie — rapport 2/3–1/3 non construit" },
        { id:'ch6', titre:'Franchissement déséquilibré — bras équilibrateurs écartés', desc:"Le franchissement est encore déséquilibré. L'élève utilise les bras écartés pour maintenir l'équilibre au lieu de les fixer le long du tronc.", hyp:"Organisation de la trajectoire non maîtrisée — les bras compensent un déséquilibre structural du franchissement" },
      ], ot:"Franchir la haie en phase <strong>descendante</strong> avec une impulsion loin de l'obstacle (rapport 2/3–1/3). Attaquer par le genou avec engagement des épaules vers l'avant. Organiser une réception en appuis décalés." },
      { niv:3, phrase:'Le coureur-hurdleur', items:[
        { id:'ch7', titre:'Course continue — reprise de course lente après la haie', desc:"L'élève court de façon continue mais marque une impression de non vélocité sur les deux appuis après la haie. Temps « mort » après le franchissement.", hyp:"Le franchissement est conçu comme une résultante des actions précédentes et non comme l'origine potentielle des actions suivantes (reprise de course)" },
        { id:'ch8', titre:'Centre de gravité en arrière lors de la reprise de course', desc:"L'élève attaque par le genou à 2/3 avant la haie et réceptionne à 1/3 après, mais son centre de gravité est souvent en arrière lors de la reprise de course. Attente passive du sol au-dessus de l'obstacle.", hyp:"Pas de lien franchissement-course : l'action des segments pendant la trajectoire ne prépare pas encore la reprise active d'accélération" },
      ], ot:"Mobiliser activement les segments pendant le franchissement pour <strong>accélérer dès la reprise de course</strong>. Rabattre la jambe d'attaque, retourner rapidement la jambe d'esquive, regarder la haie suivante (et non la zone de réception)." },
    ],
    oe: [
      { id:'ch-oe1', p:'oep1', tag:'PRIORITAIRE', titre:'Rythme régulier inter-obstacles et intégration du franchissement dans la course', desc:"Adopter un rythme régulier (4 ou 6 appuis) entre les haies. Considérer la haie comme une cible à franchir en course et non un obstacle à éviter.", linked:['ch1','ch2','ch3'] },
      { id:'ch-oe2', p:'oep1', tag:'PRIORITAIRE', titre:'Réglage départ–1ère haie et gestion du rapport amplitude/fréquence', desc:"Choisir le pied de devant pour attaquer la 1ère haie du bon pied. Gérer le rapport amplitude/fréquence pour prendre une impulsion loin de l'obstacle.", linked:['ch1','ch2'] },
      { id:'ch-oe3', p:'oep1', tag:'PRIORITAIRE', titre:'Franchissement rasant — passage latéral de la jambe arrière', desc:"Franchir des obstacles inférieurs à l'enfourchure sans élévation importante du centre de gravité. Effectuer un passage latéral de la jambe arrière.", linked:['ch3','ch4'] },
      { id:'ch-oe4', p:'oep2', tag:'SECONDAIRE', titre:'Organisation de la trajectoire — rapport 2/3 avant / 1/3 après la haie', desc:"Organiser le rapport amplitude/fréquence pour s'impulser loin de l'obstacle (2/3 avant) et franchir en phase descendante. Établir un rapport entre l'angle de décollage et le point haut de la trajectoire.", linked:['ch4','ch5','ch6'] },
      { id:'ch-oe5', p:'oep2', tag:'SECONDAIRE', titre:'Équilibre du franchissement — attaque genou, épaules avant, bras fixés', desc:"Attaquer par le genou avec engagement des épaules vers l'avant. Fixer les bras à côté du tronc. Retourner la jambe d'esquive vers l'avant pour une réception en appuis décalés.", linked:['ch5','ch6'] },
      { id:'ch-oe6', p:'oep3', tag:'COMPLÉMENTAIRE', titre:'Anticipation de la reprise de course — mobilisation active des segments', desc:"Rabattre la jambe d'attaque vers le sol dès le passage de la jambe d'esquive. Retourner rapidement la jambe d'esquive vers l'avant. Regarder la haie suivante (et non la zone de réception).", linked:['ch7','ch8'] },
    ],
    objectifs: [
      { oe:'ch-oe1', phase:'A', titre:'Rythme régulier et intégration de la haie dans la course', ta:"Construire la continuité de course en traitant la haie comme une cible à franchir.\n• Réglage départ–1ère haie : choisir le bon pied d'attaque\n• Adopter un rythme régulier 4 ou 6 appuis entre les obstacles\n• Situation : franchir des lattes au sol (0 cm) puis obstacles bas (30–40 cm)\n• Contrainte : imposer un nombre d'appuis entre les obstacles\n• Critère : aucun piétinement ni arrêt entre les haies", chips:['Rythme','Situation-problème'] },
      { oe:'ch-oe2', phase:'A', titre:'Réglage départ–1ère haie — impulsion loin de l\'obstacle', ta:"Apprendre à régler la distance départ–1ère haie et à gérer l'amplitude pour s'impulser loin.\n• Exercice de réglage : marquer le pied d'attaque et ajuster les appuis\n• Varier l'inter-haies (6 / 8 / 10 appuis) pour construire le rapport amplitude/fréquence\n• Situation : franchissement d'un obstacle sur 20m avec couloir\n• Critère : impulsion à ≥ 1,5m de l'obstacle (repère au sol)", chips:['Réglage','Amplitude-fréquence','Situation-problème'] },
      { oe:'ch-oe3', phase:'B', titre:'Franchissement rasant — trajectoire descendante et jambe d\'esquive latérale', ta:"Construire un franchissement en phase descendante avec passage latéral de la jambe arrière.\n• Contraste : franchir des obstacles à hauteur croissante (40–60–76 cm)\n• Situation : marque au sol 2/3 avant la haie pour l'impulsion\n• Observer : point haut de la trajectoire au-dessus de la haie (et non avant)\n• Critère : jambe arrière rasante — aucune élévation excessive du CDG", chips:['Trajectoire','Rasant','Évaluation'] },
      { oe:'ch-oe4', phase:'B', titre:'Organisation du franchissement — rapport 2/3–1/3 et équilibre dans la trajectoire', ta:"Organiser la trajectoire par rapport à l'obstacle : 2/3 avant / 1/3 après.\n• Établir le rapport entre l'angle de décollage et le point haut\n• Attaquer par le genou avec engagement des épaules vers l'avant\n• Fixer les bras à côté du tronc (contre les équilibrateurs latéraux)\n• Situation : haies officielles 60m avec analyse vidéo ou observateur\n• Critère : réception en appuis décalés — bras non écartés", chips:['Organisation','2/3–1/3','Situation-problème'] },
      { oe:'ch-oe5', phase:'C', titre:'Reprise de course active — mobilisation des segments pendant la trajectoire', ta:"Anticiper la reprise de course en mobilisant activement les segments pendant le franchissement.\n• Rabattre la jambe d'attaque vers le sol dès le passage de la jambe d'esquive\n• Retourner rapidement la jambe d'esquive vers l'avant\n• Regarder la haie suivante dès la réception (et non la zone de pose)\n• Contre-action des membres supérieurs à la rotation d'impulsion\n• Critère : temps inter-haies constant — pas de ralentissement perceptible après chaque haie", chips:['Reprise de course','Anticipation','Évaluation'] },
      { oe:'ch-oe6', phase:'C', titre:'Performance globale et gestion de la course inter-obstacles', ta:"Réaliser la meilleure performance sur 60m haies en maintenant la continuité de course.\n• Gérer le rapport amplitude-fréquence en cas d'incident (haie touchée)\n• Situation : compétition 60m haies officielle avec chronométrage\n• Évaluation : chrono + observables techniques (rythme, impulsion, reprise)\n• Bilan individuel : comparer performance séance 1 et séance finale\n• Critère : progression chronométrique + rythme 4 appuis stabilisé sur l'ensemble du parcours", chips:['Performance','Éval. sommative'] },
    ],
    competences: [
      { niv:'Niv. 1 → 2', txt:"Courir sans s'arrêter entre les haies en adoptant un rythme régulier (4 ou 6 appuis). Intégrer le franchissement dans la course en traitant la haie comme une cible à franchir en phase descendante et non comme un obstacle à sauter." },
      { niv:'Niv. 2 → 3', txt:"Organiser la trajectoire de franchissement selon le rapport 2/3–1/3. Attaquer par le genou avec engagement des épaules vers l'avant. Réceptionner en appuis décalés pour préparer la reprise de course." },
      { niv:'Niv. 3', txt:"Mobiliser activement les segments pendant le franchissement pour accélérer dès la reprise de course. Maintenir la continuité et la vélocité sur l'ensemble du parcours (60m haies) malgré les incidents éventuels." },
    ]
  }
};

// ══════════ STATE ══════════
let currentAps = 'relais';
const selected = new Set();
const activeOE = new Set();

// ══════════ VIEWS ══════════
function showView(v) {
  document.querySelectorAll('.view').forEach(el => el.classList.remove('active'));
  document.getElementById('view-' + v).classList.add('active');
  document.querySelectorAll('.hnav-btn').forEach(b => b.classList.remove('active'));
  const map = { home:'nb-home', 'aps-sel':'nb-ath', 'aps-relais':'nb-relais', 'aps-sl':'nb-sl', 'aps-sprint':'nb-sprint', 'aps-sel-demarquage':'nb-home', 'aps-basketball':'nb-home', 'aps-sel-renvoi':'nb-home', 'aps-volleyball':'nb-home', plan:'nb-plan' };
  if (map[v]) document.getElementById(map[v]).classList.add('active');
  window.scrollTo({top:0, behavior:'smooth'});
}

function showLocked() {
  alert('Cette famille sera disponible dès le chargement de son contenu. Revenez bientôt !');
}

function backToAps() {
  showView(DATA[currentAps].apsView);
}

// ══════════ LAUNCH ══════════
function launchPlan(aps) {
  currentAps = aps;
  currentVol = 10;
  selected.clear(); activeOE.clear();
  const d = DATA[aps];
  document.getElementById('bc-aps-link').textContent = d.nom;
  document.getElementById('sp1-title').textContent = `Conduites Typiques — ${d.nom}`;
  document.getElementById('sp3-title').textContent = `Objectifs Progressifs — ${d.nom}`;
  document.getElementById('sp4-title').textContent = `Résumé — ${d.nom}`;
  document.getElementById('r-aps').textContent = d.nom;
  buildConduites();
  showView('plan');
  showStep(1);
  // init curseur volume
  const sl = document.getElementById('vol-slider');
  if(sl){ sl.value = 10; initVol(); }
}

// ══════════ STEPS ══════════
function showStep(n) {
  document.querySelectorAll('.sub-panel').forEach((p,i) => p.classList.toggle('active', i===n-1));
  document.querySelectorAll('.step-tab').forEach((t,i) => {
    t.classList.remove('active','done');
    if (i===n-1) t.classList.add('active');
    else if (i<n-1) t.classList.add('done');
  });
  if (n===2) buildOE();
  if (n===3) { buildObjectifs(); initVol(); }
  if (n===4) buildResume();
  window.scrollTo({top:0, behavior:'smooth'});
}

// ══════════ CONDUITES ══════════
function buildConduites() {
  const d = DATA[currentAps];
  let html = '';
  d.conduites.forEach(niv => {
    html += `<div class="niveau-section-label">
      <span class="nsl-pill nsl-${niv.niv}">Niveau ${niv.niv}</span>
      <div class="nsl-line"></div>
      <span class="nsl-sub">${niv.phrase}</span>
    </div>`;
    niv.items.forEach(c => {
      html += `<div class="conduite-card" onclick="toggleCC(this,'${c.id}')" id="${c.id}">
        <div class="cc-check"></div>
        <div class="cc-body">
          <strong>${c.titre}</strong>
          <p>${c.desc}</p>
          <span class="cc-hyp">↳ ${c.hyp}</span>
        </div>
      </div>`;
    });
    html += `<div class="ot-banner"><span class="ot-label">OT Étape ${niv.niv}</span><span>${niv.ot}</span></div>`;
  });
  document.getElementById('conduites-content').innerHTML = html;
  updateHint();
}

function toggleCC(el, id) {
  if (el.classList.contains('sel')) {
    el.classList.replace('sel','rej');
    el.querySelector('.cc-check').textContent = '✕';
    selected.delete(id);
  } else if (el.classList.contains('rej')) {
    el.classList.remove('rej');
    el.querySelector('.cc-check').textContent = '';
    selected.delete(id);
  } else {
    el.classList.add('sel');
    el.querySelector('.cc-check').textContent = '✓';
    selected.add(id);
  }
  updateHint();
}

function updateHint() {
  const n = selected.size, ok = n >= 2;
  const hint = document.getElementById('hint1');
  const btn  = document.getElementById('btnNext1');
  hint.textContent = ok ? `✅ ${n} conduite(s) validée(s)` : '⚠️ Sélectionnez au moins 2 conduites';
  hint.className = 'nav-hint' + (ok ? ' ok' : '');
  btn.disabled = !ok;
}

// ══════════ OE ══════════
function buildOE() {
  const grid = document.getElementById('oe-grid');
  grid.innerHTML = '';
  DATA[currentAps].oe.forEach(oe => {
    const rel = oe.linked.some(c => selected.has(c));
    if (rel && !activeOE.has(oe.id)) activeOE.add(oe.id);
    const on = activeOE.has(oe.id);
    grid.innerHTML += `<div class="oe-mini ${oe.p}">
      <div class="oe-mini-tag">${oe.tag}</div>
      ${rel ? '<div style="font-size:10px;color:var(--green);margin-bottom:4px;font-family:\'DM Mono\',monospace">● Issu de vos conduites</div>' : ''}
      <div class="oe-mini-title">${oe.titre}</div>
      <div class="oe-mini-desc">${oe.desc}</div>
      <label class="toggle-row" onclick="toggleOE('${oe.id}')">
        <div class="tog ${on?'on':''}" id="tog-${oe.id}"></div>
        <span class="tog-lbl" id="togl-${oe.id}">${on?'Activé':'Désactivé'}</span>
      </label>
    </div>`;
  });
}

function toggleOE(id) {
  setTimeout(()=>{
    const tog = document.getElementById('tog-'+id);
    const lbl = document.getElementById('togl-'+id);
    if (activeOE.has(id)) { activeOE.delete(id); tog.classList.remove('on'); lbl.textContent='Désactivé'; }
    else { activeOE.add(id); tog.classList.add('on'); lbl.textContent='Activé'; }
  },10);
}

// ══════════ OBJECTIFS ══════════
const phColors = { A:'var(--navy)', B:'var(--blue-mid)', C:'var(--accent)' };
const phNames  = () => DATA[currentAps].phases;
const phDots   = { A:'ph-a', B:'ph-b', C:'ph-c' };
const ocCls    = { A:'oc-a', B:'oc-b', C:'oc-c' };

// ══════════ VOLUME — filtre par tag OE ══════════
// Seuils : ≤6h → PRIORITAIRES seuls | ≤8h → +SECONDAIRES | ≥10h → tous
let currentVol = 10;

function tagsAutorises(vol) {
  if (vol <= 6)  return ['PRIORITAIRE'];
  if (vol <= 8)  return ['PRIORITAIRE','SECONDAIRE'];
  return ['PRIORITAIRE','SECONDAIRE','COMPLÉMENTAIRE'];
}

function getTagOE(oeId) {
  const oe = DATA[currentAps].oe.find(o => o.id === oeId);
  return oe ? oe.tag : '';
}

// Répartition horaire — règle didactique
// Poids par rang : Ph1→2 (Construction) · Ph2→3 (Consolidation) · Ph3→2 (Transfert)
// Temps_phase = poids × nb_obj_dans_phase → normalisé au volume total
// Garde-fou : minimum 2 séances par objectif
function seancesDist(retenus, total) {
  if (!retenus.length) return [];
  const phases  = [...new Set(retenus.map(o => o.phase))]; // ordre d'apparition = rang réel
  const poids   = {};
  if (phases[0]) poids[phases[0]] = 2;
  if (phases[1]) poids[phases[1]] = 3;
  if (phases[2]) poids[phases[2]] = 2;

  const count    = {};
  phases.forEach(p => count[p] = retenus.filter(o => o.phase === p).length);

  const raw      = {};
  phases.forEach(p => raw[p] = poids[p] * count[p]);
  const totalRaw = Object.values(raw).reduce((s,v) => s+v, 0);

  // Séances par phase — garantir min 2 par objectif
  const seaPhase = {};
  phases.forEach(p => {
    seaPhase[p] = Math.max(count[p] * 2, Math.round(raw[p] / totalRaw * total));
  });

  // Ajuster si le total alloué dépasse le volume (à cause du min)
  let allocated = Object.values(seaPhase).reduce((s,v) => s+v, 0);
  if (allocated > total) {
    const central = phases[Math.min(1, phases.length-1)];
    seaPhase[central] = Math.max(count[central]*2, seaPhase[central] - (allocated - total));
    allocated = Object.values(seaPhase).reduce((s,v) => s+v, 0);
  }

  // Absorber l'écart d'arrondi dans la phase centrale
  const diff    = total - Object.values(seaPhase).reduce((s,v) => s+v, 0);
  const central = phases[Math.min(1, phases.length-1)];
  seaPhase[central] += diff;

  // Séances par objectif individuel
  return retenus.map(obj =>
    Math.max(2, Math.round(seaPhase[obj.phase] / count[obj.phase]))
  );
}

// Numérotation dynamique des phases : Phase 1, Phase 2 (…3 si présente)
// Le nom didactique vient de DATA[aps].phases mais re-numéroté selon le rang réel
function labelPhase(phCode, phasesPresentes) {
  const rang = phasesPresentes.indexOf(phCode) + 1;
  const nom = DATA[currentAps].phases[phCode];
  // Remplacer "Phase 1/2/3 —" par le rang dynamique
  return nom.replace(/^Phase [123]/, `Phase ${rang}`);
}

function conseilVol(vol, nbPhases, nbObj) {
  const tags = tagsAutorises(vol);
  if (vol <= 6)  return `Cycle court (${vol} séances) · OE prioritaires uniquement · ${nbObj} objectif(s) · ${nbPhases} phase(s)`;
  if (vol <= 8)  return `Cycle réduit (${vol} séances) · OE prioritaires + secondaires · ${nbObj} objectif(s) · ${nbPhases} phase(s)`;
  return `Cycle standard (${vol} séances) · Tous les OE activés · ${nbObj} objectif(s) · ${nbPhases} phase(s)`;
}

function onVolChange(v) {
  v = parseInt(v);
  currentVol = v;
  const pct = ((v-6)/(12-6))*100;
  document.getElementById('vol-slider').style.setProperty('--vpct', pct+'%');
  document.getElementById('vol-num').textContent = v;
  buildObjectifs(); // conseil mis à jour dans buildObjectifs
}

function initVol() { onVolChange(currentVol); }

// ══════════ OBJECTIFS — moteur refactorisé ══════════
function buildObjectifs() {
  const objs   = DATA[currentAps].objectifs;
  const tags   = tagsAutorises(currentVol);

  // Filtre : OE actif ET tag autorisé par le volume
  const retenus = objs.filter(obj =>
    activeOE.has(obj.oe) && tags.includes(getTagOE(obj.oe))
  );

  // Mise à jour barre conseil volume
  const phasesPresentes = [...new Set(retenus.map(o => o.phase))];
  document.getElementById('vol-conseil').textContent =
    conseilVol(currentVol, phasesPresentes.length, retenus.length);

  // Mise à jour barre visuelle volume
  const distSea = seancesDist(retenus, currentVol);
  const seaByPhase = {};
  phasesPresentes.forEach(p => {
    seaByPhase[p] = retenus.reduce((s, o, i) => o.phase===p ? s+distSea[i] : s, 0);
  });
  const phCodes = ['A','B','C'];
  phCodes.forEach((p, idx) => {
    const seg = document.getElementById(`vol-seg-${idx+1}`);
    const val = seaByPhase[p] || 0;
    const rang = phasesPresentes.indexOf(p) + 1;
    seg.style.flex = val || 0.001;
    seg.innerHTML  = val > 0 ? `<span>${val}h</span><small> Ph.${rang}</small>` : '';
  });

  // Bandeau 2 phases
  let bandeauHtml = '';
  if (phasesPresentes.length === 2) {
    bandeauHtml = `<div style="background:#FFF3CD;border:1px solid #F5C518;border-radius:8px;padding:10px 14px;
      font-family:'DM Mono',monospace;font-size:11px;color:#7A5800;margin-bottom:16px;display:flex;gap:8px;align-items:center">
      <span style="font-size:16px">⚠️</span>
      <span>Cycle à <strong>2 phases</strong> — La phase 3 n'est pas accessible avec les conduites sélectionnées.
      Sélectionnez des conduites de niveau supérieur pour débloquer la 3ᵉ phase.</span>
    </div>`;
  } else if (phasesPresentes.length === 1) {
    bandeauHtml = `<div style="background:#FFE5E5;border:1px solid #E87070;border-radius:8px;padding:10px 14px;
      font-family:'DM Mono',monospace;font-size:11px;color:#7A1A1A;margin-bottom:16px;display:flex;gap:8px;align-items:center">
      <span style="font-size:16px">⚠️</span>
      <span>Cycle à <strong>1 seule phase</strong> — Revenez à l'étape 1 et sélectionnez des conduites
      supplémentaires, ou activez davantage d'OE à l'étape 2.</span>
    </div>`;
  }

  if (retenus.length === 0) {
    document.getElementById('objectifs-content').innerHTML =
      `<div style="padding:32px;text-align:center;font-family:'DM Mono',monospace;color:var(--muted);font-size:13px">
        ⚠️ Aucun objectif disponible.<br><br>
        Retournez à l'étape 2 et activez au moins un Objet d'Enseignement.
      </div>`;
    return;
  }

  let html = bandeauHtml;
  let lastPhase = ''; let num = 0;

  retenus.forEach((obj, idx) => {
    num++;
    const seances = distSea[idx];
    if (obj.phase !== lastPhase) {
      lastPhase = obj.phase;
      const nbInPhase = retenus.filter(o => o.phase === lastPhase).length;
      const phLabel   = labelPhase(obj.phase, phasesPresentes);
      html += `<div class="phase-header">
        <div class="phase-dot ${phDots[obj.phase]}"></div>
        <span class="phase-name" style="color:${phColors[obj.phase]}">${phLabel}</span>
        <div class="phase-line"></div>
        <span class="phase-seances">${nbInPhase} obj. retenu${nbInPhase>1?'s':''}</span>
      </div>`;
    }
    const chips = obj.chips.map(c => {
      const cls = c.includes('Éval') ? 'on ev'
                : (c.includes('prob')||c.includes('Situation')||c.includes('Comp')) ? 'on sit'
                : 'on';
      return `<span class="obj-chip ${cls}">${c}</span>`;
    }).join('');
    html += `<div class="obj-entry" data-phase="${obj.phase}">
      <div class="obj-entry-head">
        <div class="obj-circle ${ocCls[obj.phase]}">${num}</div>
        <div class="obj-entry-title">${obj.titre}</div>
        <div class="obj-entry-meta">Séances : <input type="number" class="si" value="${seances}" min="1" max="8"></div>
      </div>
      <div class="obj-body">
        <textarea class="obj-ta">${obj.ta}</textarea>
        <div class="obj-chips">${chips}</div>
      </div>
    </div>`;
  });
  document.getElementById('objectifs-content').innerHTML = html;
}

// ══════════ RÉSUMÉ ══════════
function buildResume() {
  document.getElementById('r-classe').textContent = document.getElementById('cfg-classe').value || '—';
  document.getElementById('r-niv').textContent    = document.getElementById('cfg-niv').value;
  document.getElementById('r-total').textContent  = currentVol + ' séances';
  document.getElementById('r-dur').textContent    = document.getElementById('cfg-dur').value;
  document.getElementById('r-ct').textContent     = selected.size + ' validée(s)';
  document.getElementById('r-oe').textContent     = activeOE.size + ' activé(s)';

  // Même filtre que buildObjectifs
  const tags    = tagsAutorises(currentVol);
  const retenus = DATA[currentAps].objectifs.filter(obj =>
    activeOE.has(obj.oe) && tags.includes(getTagOE(obj.oe))
  );

  const phasesPresentes = [...new Set(retenus.map(o => o.phase))];
  const distSea = seancesDist(retenus, currentVol);

  // Lire les séances depuis les inputs de l'étape 3 (si disponibles)
  const inputs = [...document.querySelectorAll('.si')];
  const vals = inputs.length > 0
    ? inputs.map(i => parseInt(i.value)||0)
    : distSea;

  // Séances par phase (nommées dynamiquement)
  const seaByPhase = {};
  phasesPresentes.forEach(p => {
    seaByPhase[p] = retenus.reduce((s, o, i) => o.phase===p ? s+(vals[i]||0) : s, 0);
  });
  const ph = phNames();

  // Afficher les 3 lignes de phase en renommant selon rang réel
  ['A','B','C'].forEach((p, idx) => {
    const rang  = phasesPresentes.indexOf(p) + 1;
    const sea   = seaByPhase[p] || 0;
    const label = rang > 0 ? labelPhase(p, phasesPresentes) : ph[p];
    document.getElementById(`r-p${p}`).textContent   = sea;
    document.getElementById(`lbl-p${p}`).textContent = label + ' (séances)';
    const seg = document.getElementById(['cba','cbb','cbc'][idx]);
    seg.style.flex = sea || 0.001;
    seg.innerHTML  = `${sea}<small>${label}</small>`;
  });

  // Barre vol résumé
  ['A','B','C'].forEach((p, idx) => {
    const sea  = seaByPhase[p] || 0;
    const rang = phasesPresentes.indexOf(p) + 1;
    const seg  = document.getElementById(`vol-seg-${idx+1}`);
    seg.style.flex = sea || 0.001;
    seg.innerHTML  = sea > 0 ? `<span>${sea}h</span><small> Ph.${rang>0?rang:idx+1}</small>` : '';
  });

  // Récap objectifs
  document.getElementById('obj-summary').innerHTML = retenus.length === 0
    ? `<div style="color:var(--muted);font-size:12px;font-style:italic;padding:8px 0">Aucun objectif retenu.</div>`
    : retenus.map((o, i) => `
      <div style="display:flex;justify-content:space-between;padding:7px 0;border-bottom:1px dashed var(--mid);font-size:12px">
        <span style="display:flex;align-items:center;gap:8px;color:var(--text)">
          <span style="width:20px;height:20px;border-radius:50%;background:${phColors[o.phase]};color:white;
            display:inline-flex;align-items:center;justify-content:center;font-size:10px;font-weight:800;flex-shrink:0">${i+1}</span>
          ${o.titre}
        </span>
        <span style="font-family:'DM Mono',monospace;font-size:11px;color:var(--muted)">${vals[i]||0} sé.</span>
      </div>`).join('');

  document.getElementById('r-competences').innerHTML = DATA[currentAps].competences.map(c =>
    `<strong>${c.niv} :</strong> ${c.txt}<br>`).join('');
}

// ══════════ EXPORT ══════════
function exportCycle() {
  const blob = new Blob([document.documentElement.outerHTML], {type:'text/html'});
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = 'cycle_' + currentAps + '_' + (document.getElementById('cfg-classe').value||'classe').replace(/\s+/g,'_') + '.html';
  a.click();
}
</script>
</body>
</html>
