<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>聖約經緯：經與史的永恆對局</title>
<style>
/* ============ 聖約經緯 · 聖殿至聖所與羊皮古卷美學 ============ */
* { margin: 0; padding: 0; box-sizing: border-box; }
:root {
  --bg: #0d0a08; --bg2: #16110c; --panel: #201710; --panel2: #19110b;
  --line: #4f3d24; --text: #f3ebd8; --dim: #aa9778; --accent: #dfba64;
  --water: #143852; --water2: #0d2538; --beach: #c7b07b; --plain: #4e633d;
  --forest: #2b4227; --city: #8c7d66; --ruin: #5e4e3b; --mtn: #544b41;
  --sand: #ab9563; --snow: #d2dc84; --ice: #7ab2cb; --desert: #b89354; --mine: #5e3c28;
  --marsh: #3c4f39; --trench: #634f37; --reef: #216373; --rail: #9c8454;
  --house: #73533c; --port: #254b63; --airfield: #68532e; --road: #a48c5a;
  --void: #060812; --light: #d2b45a;
  --playerc: #245743; --playerc2: #3a8266; --aic: #4d2328; --aic2: #75373f;
  --danger: #d44848; --good: #54b26a; --faith: #6bd4ee;
}
html, body { height: 100%; }
body {
  background: radial-gradient(circle at 50% 15%, #20170f, var(--bg) 80%);
  color: var(--text);
  font-family: "Noto Serif TC", "Songti TC", "PMingLiU", "PingFang TC", "Microsoft JhengHei", serif;
  overflow-y: auto;
}
.hidden { display: none !important; }
.screen { height: 100vh; display: flex; flex-direction: column; }

/* ---------- 古卷按鈕風格 ---------- */
.btn {
  background: linear-gradient(135deg, #e6c272, #b88f30);
  color: #140d04; border: 1px solid #ffde94; padding: 8px 16px;
  font-size: 14.5px; font-weight: 800; border-radius: 5px; cursor: pointer;
  font-family: inherit; letter-spacing: 1.5px; transition: all .15s;
  box-shadow: 0 2px 8px rgba(0,0,0,.5);
}
.btn:hover { filter: brightness(1.1); transform: translateY(-1px); }
.btn:active { transform: scale(.97); }
.btn.ghost {
  background: rgba(32, 23, 16, 0.85); color: var(--text); border: 1px solid var(--line);
  font-weight: 600; letter-spacing: 0.8px; box-shadow: none;
}
.btn.ghost:hover { border-color: var(--accent); color: var(--accent); background: rgba(223,186,100,.1); }
.btn.sm { padding: 5px 11px; font-size: 12.5px; }
.btn.big { padding: 13px 36px; font-size: 18px; letter-spacing: 2.5px; }
.btn:disabled { opacity: .4; cursor: not-allowed; transform: none; }

/* ============ 畫面一：聖地全景沙盤 ============ */
#map-header {
  display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px;
  padding: 12px 24px 10px; border-bottom: 2px solid var(--line);
  background: linear-gradient(180deg, rgba(22,17,12,.98), rgba(13,10,8,.92));
}
#map-header h1 {
  font-size: 26px; letter-spacing: 5px; color: var(--accent);
  text-shadow: 0 0 18px rgba(223,186,100,.4);
  display: flex; align-items: center; gap: 10px;
}
.subtitle { color: var(--dim); font-size: 12px; letter-spacing: 2px; margin-top: 3px; }
.ver { color: #ffe180; font-weight: 700; }
.hdr-right { display: flex; gap: 7px; align-items: center; flex-wrap: wrap; }
#map-main { flex: 1; display: flex; min-height: 0; }
#map-wrap {
  flex: 1; position: relative; display: flex; align-items: center; justify-content: center;
  padding: 8px; background: radial-gradient(circle at 50% 50%, #121e2c, #060b14 90%);
}
#worldmap { width: 100%; height: 100%; max-height: calc(100vh - 120px); border: 1px solid var(--line); border-radius: 6px; }
#map-hint {
  position: absolute; bottom: 14px; left: 50%; transform: translateX(-50%);
  color: #f3ebd8; font-size: 12px; letter-spacing: 1.5px;
  background: rgba(20,15,10,.92); padding: 6px 18px; border-radius: 20px; border: 1px solid var(--accent);
  pointer-events: none; white-space: nowrap;
}

/* 聖卷篇章右側欄 */
#battle-list {
  width: 385px; flex-shrink: 0; min-height: 0; display: flex; flex-direction: column;
  border-left: 2px solid var(--line); background: linear-gradient(180deg, #18110b, #0f0b07);
}
.bl-head {
  padding: 12px 14px 9px; color: var(--accent); font-size: 15.5px; font-weight: 800; letter-spacing: 2.5px;
  border-bottom: 1px solid var(--line); display: flex; flex-direction: column; gap: 3px;
}
.bl-head small { color: var(--dim); font-size: 11.5px; font-weight: 400; letter-spacing: 0.8px; }
.bl-filter-wrap {
  padding: 8px 10px; border-bottom: 1px solid var(--line); background: rgba(0,0,0,.25);
  display: flex; flex-direction: column; gap: 6px;
}
.bl-search-input {
  width: 100%; background: var(--bg2); color: var(--text); border: 1px solid var(--line);
  border-radius: 4px; padding: 6px 10px; font-size: 12.5px; font-family: inherit; outline: none;
}
.bl-search-input:focus { border-color: var(--accent); }
.bl-theater-tabs { display: flex; flex-wrap: wrap; gap: 4px; }
.bl-tab {
  background: var(--panel2); color: var(--dim); border: 1px solid var(--line);
  border-radius: 3px; padding: 3px 7px; font-size: 11px; font-family: inherit; cursor: pointer; transition: all .14s;
}
.bl-tab:hover { color: var(--text); border-color: var(--accent); }
.bl-tab.active {
  background: var(--accent); color: #140d04; border-color: var(--accent); font-weight: 800;
}
#battle-list-items { overflow-y: auto; padding: 8px; display: flex; flex-direction: column; gap: 6px; min-height: 0; flex: 1; }
.bl-item {
  display: flex; align-items: center; gap: 9px; text-align: left; cursor: pointer;
  background: var(--panel2); border: 1px solid var(--line); border-radius: 6px;
  padding: 8px 10px; color: var(--text); font-family: inherit; transition: all .13s;
}
.bl-item:hover, .bl-item.bl-lit {
  border-color: var(--accent); transform: translateX(3px);
  background: linear-gradient(90deg, rgba(223,186,100,.15), var(--panel));
}
.bl-idx { font-size: 13px; font-weight: 900; color: var(--accent); width: 30px; flex-shrink: 0; }
.bl-main { flex: 1; min-width: 0; display: flex; flex-direction: column; gap: 2px; }
.bl-name { font-size: 13.5px; font-weight: 700; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.bl-meta { font-size: 11px; color: var(--dim); white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.bl-kind { color: #ffe180; font-style: normal; }
.bl-stars { font-size: 10px; color: #dfba64; flex-shrink: 0; }
.handcrafted-tag {
  display: inline-block; background: rgba(223,186,100,.22); color: #ffe59e;
  border: 1px solid #dfba64; border-radius: 3px; padding: 0 4px; font-size: 9.5px; margin-left: 4px;
}

/* 地圖光點與懸停經文卡 */
.pin { cursor: pointer; }
.pin .pin-dot { fill: var(--accent); filter: url(#pinGlow); transition: transform .15s, fill .15s; transform-origin: center; transform-box: fill-box; }
.pin .pin-ring { fill: none; stroke: var(--accent); stroke-width: 1.6; opacity: .85; transform-origin: center; transform-box: fill-box; animation: pulse 2.4s ease-out infinite; }
@keyframes pulse { 0% { transform: scale(.5); opacity: 1; } 100% { transform: scale(2.4); opacity: 0; } }
.pin:hover .pin-dot, .pin.lit .pin-dot { transform: scale(1.8); fill: #fff4d1 !important; stroke: #dfba64; stroke-width: 1.5px; }
.pin.th-pentateuch .pin-dot { fill: #f09e42; } .pin.th-pentateuch .pin-ring { stroke: #f09e42; }
.pin.th-joshua .pin-dot     { fill: #e65c72; } .pin.th-joshua .pin-ring     { stroke: #e65c72; }
.pin.th-kingdom .pin-dot    { fill: #dfba64; } .pin.th-kingdom .pin-ring    { stroke: #dfba64; }
.pin.th-prophets .pin-dot   { fill: #b87fed; } .pin.th-prophets .pin-ring   { stroke: #b87fed; }
.pin.th-gospels .pin-dot    { fill: #52bfe6; } .pin.th-gospels .pin-ring    { stroke: #52bfe6; }
.pin.th-acts .pin-dot       { fill: #4ac27b; } .pin.th-acts .pin-ring       { stroke: #4ac27b; }
.pin.won-pin .pin-dot       { fill: #54b26a !important; }
#map-top-bar {
  position: absolute; top: 12px; left: 14px; right: 14px;
  display: flex; flex-wrap: wrap; justify-content: space-between; align-items: center; gap: 8px;
  pointer-events: none; z-index: 15;
}
.map-legend-pills, .map-ctrl-btns {
  display: flex; flex-wrap: wrap; align-items: center; gap: 6px;
  background: rgba(18, 13, 8, 0.9); border: 1px solid var(--line); border-radius: 20px;
  padding: 5px 12px; backdrop-filter: blur(6px); pointer-events: auto; font-size: 11.5px; color: var(--dim);
}
.map-legend-item {
  display: inline-flex; align-items: center; gap: 5px; color: var(--text); font-size: 11.5px;
  cursor: pointer; padding: 2px 7px; border-radius: 12px; transition: background .14s;
}
.map-legend-item:hover { background: rgba(223,186,100,.15); }
.map-legend-dot { width: 8px; height: 8px; border-radius: 50%; display: inline-block; box-shadow: 0 0 6px currentColor; }
.map-mini-btn {
  background: rgba(255,255,255,.05); color: var(--text); border: 1px solid var(--line);
  border-radius: 14px; padding: 3px 9px; font-size: 11.5px; font-family: inherit; cursor: pointer;
}
.map-mini-btn:hover, .map-mini-btn.active { border-color: var(--accent); color: var(--accent); background: rgba(223,186,100,.15); }
#map-hover-card {
  position: absolute; pointer-events: none; z-index: 30;
  background: linear-gradient(145deg, rgba(28, 20, 12, 0.98), rgba(14, 10, 7, 0.98));
  border: 1.5px solid var(--accent); border-radius: 8px; padding: 10px 13px;
  min-width: 270px; max-width: 350px; box-shadow: 0 10px 28px rgba(0,0,0,.8);
  opacity: 0; transform: translateY(4px); transition: opacity .14s, transform .14s;
}
#map-hover-card.visible { opacity: 1; transform: translateY(0); }

/* ============ 畫面二：聖經經文與神學導讀 ============ */
#brief-header {
  padding: 12px 24px; border-bottom: 1px solid var(--line);
  display: flex; justify-content: space-between; align-items: center; background: var(--bg2);
}
#brief-body { flex: 1; overflow-y: auto; padding: 22px 30px 44px; }
#brief-title-row { display: flex; align-items: baseline; gap: 14px; flex-wrap: wrap; margin-bottom: 6px; }
#brief-title-row h2 { font-size: 28px; letter-spacing: 2.5px; color: var(--accent); }
#brief-title-row .en { color: var(--dim); font-size: 13.5px; letter-spacing: 1.5px; }
.brief-meta { color: var(--dim); font-size: 13.5px; margin-bottom: 16px; letter-spacing: 1px; }
.brief-cols { display: grid; grid-template-columns: 1.15fr .85fr; gap: 22px; max-width: 1220px; }
@media (max-width: 920px) { .brief-cols { grid-template-columns: 1fr; } }
.brief-card {
  background: linear-gradient(160deg, rgba(36,26,17,.95), rgba(22,16,10,.96));
  border: 1px solid var(--line); border-radius: 8px; padding: 16px 20px; margin-bottom: 16px;
  box-shadow: 0 6px 20px rgba(0,0,0,.4);
}
.brief-card h3 {
  color: var(--accent); font-size: 15px; letter-spacing: 2px; margin-bottom: 10px;
  border-bottom: 1px dashed var(--line); padding-bottom: 7px;
}
.brief-card p { font-size: 14.5px; line-height: 1.9; white-space: pre-line; color: var(--text); }
.scripture-quote-banner {
  background: linear-gradient(135deg, rgba(223,186,100,.15), rgba(52,38,20,.8));
  border-left: 4px solid var(--accent); border-radius: 6px;
  padding: 13px 16px; margin-bottom: 16px; color: #fff6de; font-size: 15px; line-height: 1.8;
}
.scripture-quote-banner small { display: block; color: var(--accent); font-weight: 700; margin-top: 4px; text-align: right; }
.ai-pick, .loadout-pick { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-top: 8px; }
.ai-card, .loadout-card {
  border: 1.5px solid var(--line); border-radius: 7px; padding: 11px; cursor: pointer;
  background: var(--panel2); transition: all .15s;
}
.ai-card:hover, .loadout-card:hover { border-color: var(--accent); }
.ai-card.selected, .loadout-card.selected {
  border-color: var(--accent); background: rgba(223,186,100,.15);
  box-shadow: 0 0 14px rgba(223,186,100,.22);
}
.ai-card .ai-name, .loadout-card .lc-title { font-size: 15px; font-weight: 800; color: var(--accent); }
.ai-card .ai-stars { font-size: 12px; margin: 2px 0 6px; color: #dfba64; }
.ai-card .ai-desc, .loadout-card .lc-desc { font-size: 12px; line-height: 1.55; color: var(--dim); }

/* 迷你預覽棋盤 */
.mini-preview-wrap { display: flex; flex-direction: column; align-items: center; gap: 8px; margin-top: 6px; }
.mini-board-grid { display: grid; border: 2px solid var(--line); border-radius: 5px; overflow: hidden; }
.mini-cell { width: 22px; height: 22px; display: flex; align-items: center; justify-content: center; position: relative; border: 0.5px solid rgba(255,255,255,.06); }
.mini-cell .mini-unit { width: 17px; height: 17px; border-radius: 50%; display: flex; align-items: center; justify-content: center; }
.mini-cell .mini-unit.player { background: var(--playerc); color: #fff; border: 1px solid #75d4a9; }
.mini-cell .mini-unit.ai { background: var(--aic); color: #ffd2d2; border: 1px solid #e87b7b; }
.mini-cell .mini-unit svg { width: 12px; height: 12px; fill: currentColor; }

/* ============ 畫面三：棋局對弈界面 ============ */
#game-top {
  display: flex; align-items: center; gap: 14px; padding: 8px 18px;
  border-bottom: 2px solid var(--line); background: var(--bg2); min-height: 52px; flex-wrap: wrap;
}
#game-title { font-size: 16px; font-weight: 800; letter-spacing: 1.5px; color: var(--accent); }
#turn-box { flex: 1; text-align: center; font-size: 14px; letter-spacing: 1.2px; }
#turn-indicator.you { color: var(--good); font-weight: 800; }
#turn-indicator.foe { color: var(--danger); font-weight: 800; }
#thinking { color: var(--dim); font-size: 13px; }
.top-btns { display: flex; gap: 6px; flex-wrap: wrap; }
#game-main { flex: 1; display: flex; gap: 14px; padding: 10px 16px; overflow: hidden; }
#board-area { flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 5px; min-width: 0; }

/* 聖曆七日與安息日橫幅 */
#sabbath-bar {
  width: 100%; max-width: 760px;
  background: linear-gradient(90deg, rgba(30,22,13,.95), rgba(52,38,20,.95), rgba(30,22,13,.95));
  border: 1px solid var(--accent); border-radius: 5px; padding: 5px 12px;
  display: flex; flex-wrap: wrap; justify-content: space-between; align-items: center; gap: 8px;
  font-size: 12px; box-shadow: 0 2px 10px rgba(0,0,0,.45);
}
#sabbath-bar.is-sabbath {
  background: linear-gradient(90deg, rgba(35,62,92,.95), rgba(70,52,122,.95), rgba(35,62,92,.95));
  border-color: #6bd4ee; box-shadow: 0 0 16px rgba(107,212,238,.4);
}
.army-banner { font-size: 12.5px; letter-spacing: 1px; color: var(--dim); display: flex; gap: 10px; align-items: center; }
.army-banner b { color: var(--text); }
.army-banner .lost { display: inline-flex; gap: 2px; align-items: center; }
.army-banner .lost svg { width: 16px; height: 16px; opacity: .75; }
#board-with-labels { display: grid; grid-template-columns: 20px auto; grid-template-rows: auto 20px; }
#row-labels { display: flex; flex-direction: column; }
#row-labels span, #col-labels span { display: flex; align-items: center; justify-content: center; color: var(--dim); font-size: 11px; }
#col-labels { grid-column: 2; display: flex; }
#board {
  display: grid; border: 3px solid var(--accent); border-radius: 5px; overflow: hidden;
  box-shadow: 0 10px 42px rgba(0,0,0,.75), 0 0 20px rgba(223,186,100,.15); grid-column: 2;
}
.cell { position: relative; width: var(--sq, 58px); height: var(--sq, 58px); cursor: default; border: 0.5px solid rgba(255,255,255,.05); }
.cell.t-w  { background: linear-gradient(160deg, var(--water), var(--water2)); }
.cell.t-b  { background: var(--beach); }
.cell.t-p  { background: var(--plain); }
.cell.t-f  { background: var(--forest); }
.cell.t-c  { background: var(--city); }
.cell.t-u  { background: var(--ruin); }
.cell.t-m  { background: var(--mtn); }
.cell.t-s  { background: var(--sand); }
.cell.t-sn { background: linear-gradient(160deg, var(--snow), #98a4ae); }
.cell.t-ic { background: linear-gradient(160deg, var(--ice), #548da9); }
.cell.t-ds { background: var(--desert); }
.cell.t-mn { background: repeating-linear-gradient(45deg, var(--mine), var(--mine) 6px, #3d251a 6px, #3d251a 12px); }
.cell.t-mr { background: linear-gradient(160deg, var(--marsh), #273824); }
.cell.t-tr { background: repeating-linear-gradient(0deg, var(--trench), var(--trench) 5px, #4a3a25 5px, #4a3a25 10px); }
.cell.t-rf { background: radial-gradient(circle at 50% 50%, #359898, var(--reef) 75%); }
.cell.t-rl { background: repeating-linear-gradient(90deg, var(--plain), var(--plain) 7px, #6e5a36 7px, #6e5a36 10px); }
.cell.t-hs { background: linear-gradient(145deg, var(--house), #4f3624); }
.cell.t-pt { background: linear-gradient(160deg, var(--port), #173247); }
.cell.t-af { background: radial-gradient(circle at 50% 50%, #8a6a2c, var(--airfield)); }
.cell.t-rd { background: linear-gradient(90deg, #7a653f 0%, var(--road) 50%, #7a653f 100%); }
.cell.t-vd { background: radial-gradient(circle at 50% 50%, #12152e, #04050a 85%); }
.cell.t-lt { background: radial-gradient(circle at 50% 50%, #ffe991, #b58d2a 85%); }

/* 地標紋理裝飾 */
.cell .deco { position: absolute; inset: 0; pointer-events: none; display: flex; align-items: center; justify-content: center; font-size: calc(var(--sq,58px)*.40); opacity: .82; }
.cell.t-f .deco::before  { content: "🫒"; }
.cell.t-m .deco::before  { content: "⛰️"; }
.cell.t-c .deco::before  { content: "🏛️"; font-size: calc(var(--sq,58px)*.36); opacity: .65; }
.cell.t-u .deco::before  { content: "🪨"; font-size: calc(var(--sq,58px)*.34); opacity: .55; }
.cell.t-s .deco::before  { content: "🌴"; font-size: calc(var(--sq,58px)*.36); opacity: .75; }
.cell.t-w .deco::before  { content: "〰"; color: rgba(255,255,255,.18); font-size: calc(var(--sq,58px)*.48); }
.cell.t-mn .deco::before { content: "🌵"; font-size: calc(var(--sq,58px)*.34); opacity: .75; }
.cell.t-ic .deco::before { content: "💎"; font-size: calc(var(--sq,58px)*.30); opacity: .55; }
.cell.t-sn .deco::before { content: "❅"; color: rgba(255,255,255,.45); font-size: calc(var(--sq,58px)*.32); }
.cell.t-mr .deco::before { content: "🌿"; font-size: calc(var(--sq,58px)*.34); opacity: .65; }
.cell.t-tr .deco::before { content: "🧱"; font-size: calc(var(--sq,58px)*.32); opacity: .60; }
.cell.t-rf .deco::before { content: "🐚"; font-size: calc(var(--sq,58px)*.32); opacity: .65; }
.cell.t-rl .deco::before { content: "👣"; font-size: calc(var(--sq,58px)*.30); opacity: .50; }
.cell.t-hs .deco::before { content: "🏺"; font-size: calc(var(--sq,58px)*.34); opacity: .70; }
.cell.t-pt .deco::before { content: "⛵"; font-size: calc(var(--sq,58px)*.36); opacity: .72; }
.cell.t-af .deco::before { content: "🔥"; font-size: calc(var(--sq,58px)*.36); opacity: .78; }
.cell.t-rd .deco::before { content: "📜"; font-size: calc(var(--sq,58px)*.28); opacity: .42; }
.cell.t-vd .deco::before { content: "🌌"; font-size: calc(var(--sq,58px)*.36); opacity: .55; }
.cell.t-lt .deco::before { content: "✨"; font-size: calc(var(--sq,58px)*.38); opacity: .88; }
.cell.zone-evac { box-shadow: inset 0 0 0 2.5px rgba(84,178,106,.9); }
.cell.zone-evac .deco::before { content: "🌈"; font-size: calc(var(--sq,58px)*.40); opacity: .85; }
.cell.zone-bunker .mark, .cell.zone-flag .mark { position: absolute; top: 1px; left: 2px; font-size: calc(var(--sq,58px)*.28); z-index: 2; }
.cell.lastmove { box-shadow: inset 0 0 0 2.5px rgba(223,186,100,.65); }
.cell.sel { box-shadow: inset 0 0 0 3px #fff2b2; z-index: 3; }
.cell.legal { cursor: pointer; }
.cell.legal::after {
  content: ""; position: absolute; left: 50%; top: 50%; width: 26%; height: 26%;
  transform: translate(-50%,-50%); border-radius: 50%; background: rgba(84,178,106,.75); z-index: 2;
}
.cell.legalcap { cursor: pointer; }
.cell.legalcap::after {
  content: ""; position: absolute; inset: 6%; border-radius: 50%;
  border: 3.5px solid rgba(223,186,100,.92); z-index: 2;
}
.cell.enemy-threat::after {
  content: ""; position: absolute; inset: 2px; border: 1.5px dashed rgba(212, 72, 72, 0.72);
  background: radial-gradient(circle, rgba(212, 72, 72, 0.22) 0%, transparent 75%); pointer-events: none; z-index: 2;
}
.cell.hint-from { box-shadow: inset 0 0 0 3px #dfba64, 0 0 14px #dfba64 !important; }
.cell.hint-to   { box-shadow: inset 0 0 0 3px #54b26a, 0 0 16px #54b26a !important; }

/* 棋子（聖約綠玉 vs 對手暗紅） */
.piece {
  position: absolute; inset: 7%; border-radius: 50%; z-index: 3;
  display: flex; align-items: center; justify-content: center; transition: transform .12s;
}
.piece.player {
  background: radial-gradient(circle at 35% 30%, var(--playerc2), var(--playerc) 65%, #143325);
  border: 2px solid #dfba64; box-shadow: 0 2px 7px rgba(0,0,0,.6); color: #fff8e6;
}
.piece.ai {
  background: radial-gradient(circle at 35% 30%, var(--aic2), var(--aic) 65%, #291215);
  border: 2px solid #e87b7b; box-shadow: 0 2px 7px rgba(0,0,0,.6); color: #ffe8e8;
}
.piece.is-hero {
  box-shadow: 0 0 0 2px #ffe484, 0 0 14px rgba(255, 228, 132, 0.85), 0 3px 8px rgba(0,0,0,.7) !important;
}
.piece.is-foe-boss {
  box-shadow: 0 0 0 2px #e87b7b, 0 0 14px rgba(232, 123, 123, 0.85), 0 3px 8px rgba(0,0,0,.7) !important;
}
.picon { width: 76%; height: 76%; fill: currentColor; }
.piece.movable { cursor: pointer; }
.hero-tag {
  position: absolute; bottom: -5px; left: 50%; transform: translateX(-50%);
  background: linear-gradient(135deg, #38240a, #1a1103); color: #ffe59e;
  border: 1px solid #dfba64; border-radius: 3px; padding: 0 4px; font-size: 9px; font-weight: 900;
  white-space: nowrap; z-index: 6; pointer-events: none;
}
.piece.ai .hero-tag { background: linear-gradient(135deg, #3d0d12, #1f0407); color: #ffb8c0; border-color: #e87b7b; }
.piece .vet-star { position: absolute; top: -3px; right: -3px; font-size: 11px; pointer-events: none; }
.piece .entrench-badge { position: absolute; bottom: -3px; right: -3px; font-size: 10px; pointer-events: none; }

/* ---------- 右側屬靈控制台 ---------- */
#side-panel { width: 345px; display: flex; flex-direction: column; gap: 10px; overflow-y: auto; padding-right: 3px; }
@media (max-width: 1080px) { #side-panel { width: 285px; } }
.panel-card { background: var(--panel2); border: 1px solid var(--line); border-radius: 7px; padding: 11px 13px; }
.panel-card.grow { flex: 1; min-height: 110px; display: flex; flex-direction: column; }
.card-title {
  color: var(--accent); font-size: 13px; letter-spacing: 1.5px; font-weight: 800;
  border-bottom: 1px dashed var(--line); padding-bottom: 5px; margin-bottom: 8px;
}

/* 信心神蹟祈禱面板 */
.faith-meter-wrap {
  background: rgba(0,0,0,.35); border: 1px solid rgba(107,212,238,.4); border-radius: 5px;
  padding: 6px 9px; margin-bottom: 8px;
}
.faith-bar-bg { width: 100%; height: 7px; background: rgba(255,255,255,.1); border-radius: 99px; overflow: hidden; margin-top: 4px; }
.faith-bar-fill { height: 100%; background: linear-gradient(90deg, #e6c272, #6bd4ee); transition: width .25s; }
.miracle-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 5px; margin-bottom: 6px; }
.miracle-btn {
  background: linear-gradient(145deg, rgba(223,186,100,.15), rgba(20,35,52,.85));
  border: 1px solid rgba(223,186,100,.55); border-radius: 5px; padding: 6px 4px;
  color: var(--text); font-family: inherit; font-size: 11px; cursor: pointer; text-align: center; transition: all .14s;
}
.miracle-btn:hover:not(:disabled) { border-color: #6bd4ee; transform: translateY(-1px); box-shadow: 0 3px 10px rgba(107,212,238,.25); }
.miracle-btn:disabled { opacity: 0.38; cursor: not-allowed; filter: grayscale(0.7); }
.miracle-btn b { display: block; color: #ffe180; font-size: 11.5px; }
.miracle-btn small { color: #6bd4ee; font-size: 10px; }
.tactical-tools-row { display: grid; grid-template-columns: repeat(4, 1fr); gap: 4px; margin-top: 4px; }
.tac-tool-btn {
  background: var(--panel); color: var(--text); border: 1px solid var(--line);
  border-radius: 4px; padding: 5px 3px; font-size: 11px; font-family: inherit; cursor: pointer;
}
.tac-tool-btn:hover:not(:disabled), .tac-tool-btn.active { border-color: var(--accent); color: var(--accent); }
#obj-text { font-size: 12.5px; line-height: 1.65; color: var(--text); margin-bottom: 7px; white-space: pre-line; }
#obj-progress { font-size: 12.5px; line-height: 1.85; }
#obj-progress .pg-row { display: flex; justify-content: space-between; gap: 8px; }
#obj-progress b.good { color: var(--good); } #obj-progress b.bad { color: var(--danger); } #obj-progress b.acc { color: var(--accent); }
#terrain-legend { display: flex; flex-wrap: wrap; gap: 5px 10px; font-size: 11.5px; color: var(--dim); }
.tl-item { display: flex; align-items: center; gap: 4px; }
.tl-swatch { width: 13px; height: 13px; border-radius: 3px; border: 1px solid rgba(255,255,255,.25); }
.fl-side { margin-bottom: 7px; }
.fl-side .fl-name { color: var(--dim); margin-bottom: 3px; font-size: 11.5px; }
.fl-units { display: flex; flex-wrap: wrap; gap: 3px; align-items: center; }
.fl-units svg { width: 19px; height: 19px; fill: currentColor; }
.fl-player svg { color: #75d4a9; } .fl-ai svg { color: #e87b7b; }
#battle-log { flex: 1; overflow-y: auto; font-size: 12px; line-height: 1.55; display: flex; flex-direction: column; gap: 3px; }
#battle-log .lg { padding: 3px 6px; border-radius: 3px; background: rgba(255,255,255,.03); color: var(--dim); }
#battle-log .lg.cap { color: #ffe59e; background: rgba(223,186,100,.15); }
#battle-log .lg.good { color: #b4f0c2; background: rgba(84,178,106,.15); }

/* ---------- 彈窗與查經問答卡 ---------- */
#modal-overlay {
  position: fixed; inset: 0; background: rgba(6,4,2,.85); z-index: 60;
  display: flex; align-items: center; justify-content: center; backdrop-filter: blur(4px);
}
#modal-box {
  background: linear-gradient(160deg, #221810, #140e09); border: 1.5px solid var(--accent);
  border-radius: 10px; max-width: 680px; width: calc(100% - 36px); max-height: 86vh;
  overflow-y: auto; padding: 26px 30px; box-shadow: 0 18px 60px rgba(0,0,0,.85);
}
#modal-box.wide { max-width: 920px; }
#modal-content h2 { color: var(--accent); font-size: 24px; letter-spacing: 2px; margin-bottom: 10px; }
#modal-content h3 { color: var(--accent); font-size: 16px; margin: 14px 0 6px; }
#modal-content p { font-size: 14px; line-height: 1.85; color: var(--text); margin-bottom: 8px; white-space: pre-line; }
#modal-btns { display: flex; gap: 10px; justify-content: center; margin-top: 18px; flex-wrap: wrap; }
.result-big { font-size: 40px; text-align: center; letter-spacing: 6px; margin: 6px 0 12px; font-weight: 900; }
.result-big.win { color: var(--good); text-shadow: 0 0 28px rgba(84,178,106,.6); }
.result-big.lose { color: var(--danger); }
.codex-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
@media (max-width: 720px) { .codex-grid { grid-template-columns: 1fr; } }
.codex-item { display: flex; gap: 11px; border: 1px solid var(--line); border-radius: 7px; padding: 10px 12px; background: var(--panel2); }
.codex-item .ci-icon {
  width: 46px; height: 46px; border-radius: 50%; flex-shrink: 0;
  display: flex; align-items: center; justify-content: center;
  background: radial-gradient(circle at 35% 30%, var(--playerc2), var(--playerc)); color: #fff8e6; border: 2px solid var(--accent);
}
.codex-item .ci-icon svg { width: 30px; height: 30px; fill: currentColor; }
.codex-item .ci-name { font-weight: 800; font-size: 14.5px; color: var(--accent); }
.codex-item .ci-chess { color: #ffe180; font-size: 11.5px; margin-bottom: 4px; }
.codex-item .ci-desc { color: var(--dim); font-size: 12px; line-height: 1.55; }
.quiz-opt-btn {
  display: block; width: 100%; text-align: left; padding: 10px 14px; margin: 7px 0;
  background: var(--panel2); border: 1px solid var(--line); border-radius: 6px;
  color: var(--text); font-family: inherit; font-size: 14px; cursor: pointer; transition: all .15s;
}
.quiz-opt-btn:hover { border-color: var(--accent); background: rgba(223,186,100,.15); }

/* 雲彩見證人館徽章 */
.cmd-rank-pill {
  display: inline-flex; align-items: center; gap: 8px;
  background: linear-gradient(135deg, rgba(223,186,100,.2), rgba(110,82,30,.3));
  border: 1px solid var(--accent); border-radius: 5px; padding: 5px 11px; font-size: 12.5px; cursor: pointer;
}
.medals-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(205px, 1fr)); gap: 9px; max-height: 310px; overflow-y: auto; }
.medal-card {
  background: rgba(0,0,0,.3); border: 1px solid var(--line); border-radius: 6px; padding: 9px 11px;
  display: flex; gap: 9px; opacity: 0.45; filter: grayscale(0.85);
}
.medal-card.unlocked { opacity: 1; filter: none; border-color: var(--accent); background: rgba(223,186,100,.12); }
.medal-icon { font-size: 24px; }
.hero-skill-btn {
  width: 100%; padding: 6px 9px; margin-top: 5px;
  background: linear-gradient(135deg, rgba(223,186,100,.25), rgba(110,74,20,.35));
  border: 1px solid #dfba64; border-radius: 4px; color: #ffe59e; font-size: 11.5px; font-weight: 800;
  cursor: pointer; font-family: inherit; display: flex; justify-content: space-between; align-items: center;
}
.hero-skill-btn:disabled { opacity: 0.4; cursor: not-allowed; }

/* 聖地主題色彩環境 */
body.theme-bible-cosmos { --bg:#03050e; --bg2:#060918; --panel:#0d122e; --panel2:#080b20; --line:#3d467a; --accent:#ffd76a; --plain:#0d142b; --water:#050d22; }
body.theme-bible-eden   { --bg:#05120d; --bg2:#081812; --panel:#0d241c; --panel2:#081a13; --line:#25543d; --accent:#e8c166; --plain:#2b5437; --forest:#173824; }
body.theme-bible-flood  { --bg:#030b14; --bg2:#051120; --panel:#0a1e35; --panel2:#061426; --line:#21486c; --accent:#6bd4ee; --water:#0a3556; }
body.theme-bible-egypt  { --bg:#140d07; --bg2:#1c120a; --panel:#28190d; --panel2:#1f130a; --line:#54371d; --accent:#e0aa3d; --plain:#78643e; --desert:#9e7f45; }
body.theme-bible-redsea { --bg:#05121f; --bg2:#08192b; --panel:#0d2640; --panel2:#081b2e; --line:#225278; --accent:#dfba64; --water:#0c436d; --beach:#b59e6d; }
body.theme-bible-sinai  { --bg:#170a06; --bg2:#210d08; --panel:#2e150c; --panel2:#210f08; --line:#5c2d1b; --accent:#f09e42; --plain:#6b462c; --mtn:#3d1d12; }
body.theme-bible-canaan { --bg:#0e130c; --bg2:#131a10; --panel:#1b2617; --panel2:#131d10; --line:#364d2e; --accent:#d4aa52; --plain:#52633d; }
body.theme-bible-jerusalem { --bg:#120f08; --bg2:#1a150b; --panel:#261f10; --panel2:#1c170b; --line:#544424; --accent:#dfba64; --city:#998869; }
body.theme-bible-galilee   { --bg:#06121c; --bg2:#091926; --panel:#0f2638; --panel2:#0a1c2b; --line:#244f70; --accent:#6bd4ee; --water:#13527b; }
body.theme-bible-passion   { --bg:#0e0a14; --bg2:#140e1c; --panel:#1e142b; --panel2:#140f21; --line:#40305c; --accent:#e8be63; --plain:#423b4e; }
body.theme-bible-mission   { --bg:#08101a; --bg2:#0c1726; --panel:#112236; --panel2:#0c1928; --line:#27486c; --accent:#dfba64; }
body.theme-bible-newjerusalem { --bg:#060412; --bg2:#0c0821; --panel:#140e2e; --panel2:#0e0921; --line:#4e3894; --accent:#ffe484; --city:#b8972e; --water:#196aa0; }
@media (max-width: 980px) {
  #map-main { flex-direction: column; }
  #battle-list { width: 100%; border-left: none; border-top: 2px solid var(--line); max-height: 42vh; }
}
</style>
</head>
<body class="theme-map">

<!-- ============ 畫面一：聖地全景沙盤 ============ -->
<div id="screen-map" class="screen">
  <header id="map-header">
    <div class="hdr-left">
      <h1>📜 聖約經緯：經與史的永恆對局</h1>
      <div class="subtitle">聖經策略戰棋 <span class="ver">｜36 位聖經領袖 · 120 關地圖與陣型 · 庇哩亞查經版</span></div>
    </div>
    <div class="hdr-right">
      <div class="cmd-rank-pill" id="btn-honors-map" title="檢視雲彩見證人榜與聖經聖物紀念章"></div>
      <button class="btn ghost sm" id="btn-audio-toggle">🔊 聖所音律：開</button>
      <button class="btn ghost sm" id="btn-heroes-map">👑 36位聖經人物錄</button>
      <button class="btn ghost sm" id="btn-codex-map">🛡️ 屬靈軍裝圖鑑</button>
      <button class="btn ghost sm" id="btn-saves-map">💾 聖卷書籤</button>
      <button class="btn ghost sm" id="btn-help-map">❔ 玩法與神學指南</button>
    </div>
  </header>

  <div id="map-main">
    <div id="map-wrap">
      <div id="map-top-bar">
        <div class="map-legend-pills">
          <span style="color:var(--accent);font-weight:800">聖史分期：</span>
          <span class="map-legend-item" data-th="all"><i class="map-legend-dot" style="background:#fff"></i>全卷(120)</span>
          <span class="map-legend-item" data-th="pentateuch"><i class="map-legend-dot" style="background:#f09e42"></i>摩西五經</span>
          <span class="map-legend-item" data-th="joshua"><i class="map-legend-dot" style="background:#e65c72"></i>迦南士師</span>
          <span class="map-legend-item" data-th="kingdom"><i class="map-legend-dot" style="background:#dfba64"></i>大衛列王</span>
          <span class="map-legend-item" data-th="prophets"><i class="map-legend-dot" style="background:#b87fed"></i>先知歸回</span>
          <span class="map-legend-item" data-th="gospels"><i class="map-legend-dot" style="background:#52bfe6"></i>四福音書</span>
          <span class="map-legend-item" data-th="acts"><i class="map-legend-dot" style="background:#4ac27b"></i>使徒啟示錄</span>
        </div>
        <div class="map-ctrl-btns">
          <button class="map-mini-btn" id="btn-zoom-canaan">🏔️ 聚焦迦南應許地</button>
          <button class="map-mini-btn" id="btn-zoom-all">🌍 全景聖經地圖</button>
        </div>
      </div>

      <svg id="worldmap" viewBox="0 0 1000 520" preserveAspectRatio="xMidYMid meet">
        <defs>
          <radialGradient id="ocean" cx="50%" cy="40%" r="80%">
            <stop offset="0%" stop-color="#142c44"/>
            <stop offset="100%" stop-color="#071220"/>
          </radialGradient>
          <filter id="pinGlow"><feGaussianBlur stdDeviation="3" result="b"/>
            <feMerge><feMergeNode in="b"/><feMergeNode in="SourceGraphic"/></feMerge>
          </filter>
        </defs>
        <rect x="0" y="0" width="1000" height="520" fill="url(#ocean)"/>
        <g stroke="#382c1b" stroke-width="0.6" opacity="0.45" id="gridlines"></g>
        <g id="land">
          <path d="M 10,20 L 420,20 L 445,65 L 405,115 L 440,145 L 725,135 L 980,85 L 990,510 L 580,510 L 535,415 L 505,455 L 435,510 L 10,510 L 10,365 L 480,375 L 555,345 L 595,245 L 590,175 L 415,175 L 385,135 L 335,178 L 285,155 L 265,95 L 185,145 L 145,120 L 175,75 L 95,45 Z"
                fill="#2b2117" stroke="#7a623d" stroke-width="1.8"/>
          <path d="M 15,95 L 145,120 L 185,145 L 265,95 L 285,155 L 335,178 L 385,135 L 415,175 L 590,175 L 595,255 L 555,345 L 480,375 L 15,365 Z"
                fill="url(#ocean)" stroke="#4e7392" stroke-width="1.5"/>
          <path d="M 525,212 L 568,204 L 572,222 L 528,228 Z" fill="#362c1e" stroke="#8c734b" stroke-width="1.2"/>
          <path d="M 335,215 L 398,212 L 402,224 L 338,226 Z" fill="#362c1e" stroke="#8c734b" stroke-width="1.2"/>
          <circle cx="404" cy="174" r="5.5" fill="#4f3e26" stroke="#dfba64" stroke-width="1.4"/>
          <circle cx="118" cy="242" r="5.5" fill="#4f3e26" stroke="#dfba64" stroke-width="1.4"/>
          <path d="M 545,385 L 578,435 L 612,388 L 622,395 L 592,455 L 635,515 L 565,515 L 558,452 L 532,395 Z"
                fill="#123a54" stroke="#4c92b8" stroke-width="1.5"/>
          <path d="M 525,515 Q 532,455 535,405 L 505,368 M 535,405 L 552,368 M 535,405 L 528,368"
                fill="none" stroke="#3d92c2" stroke-width="3.2" opacity="0.82"/>
          <ellipse cx="655" cy="312" rx="7" ry="10" fill="#3292c2" stroke="#7bbdeb" stroke-width="1.2"/>
          <path d="M 655,292 L 655,362" fill="none" stroke="#3fa2d4" stroke-width="2.8"/>
          <ellipse cx="655" cy="378" rx="8.5" ry="18" fill="#20638a" stroke="#68b4e0" stroke-width="1.2"/>
          <path d="M 760,85 Q 815,185 865,265 Q 915,325 965,375" fill="none" stroke="#3892c2" stroke-width="3.0" opacity="0.78"/>
          <path d="M 825,80 Q 868,175 905,255 Q 938,315 965,375" fill="none" stroke="#4aa2d4" stroke-width="2.8" opacity="0.78"/>
          <polyline points="670,210 550,218 445,155 342,92 325,185 118,242 68,85"
                    fill="none" stroke="rgba(223,186,100,0.45)" stroke-width="1.8" stroke-dasharray="5 5"/>
          <polyline points="535,388 552,412 585,438 612,382 655,348"
                    fill="none" stroke="rgba(223,135,90,0.55)" stroke-width="1.8" stroke-dasharray="4 4"/>
          <g fill="rgba(243, 235, 216, 0.62)" font-size="12.5" font-weight="700" letter-spacing="2" pointer-events="none">
            <text x="515" y="395" text-anchor="end">【埃及 · 歌珊與尼羅河】</text>
            <text x="585" y="468" text-anchor="middle" fill="#f09e42">【西乃曠野 · 何烈聖山】</text>
            <text x="642" y="348" text-anchor="end" fill="#ffe180">【錫安聖城 · 耶路撒冷】</text>
            <text x="668" y="308" text-anchor="start" fill="#8cbcf5">【加利利海 · 迦百農】</text>
            <text x="685" y="205" text-anchor="start">【安提阿 · 大馬士革】</text>
            <text x="868" y="65" text-anchor="middle">【亞拉臘山 · 方舟停泊處】</text>
            <text x="875" y="195" text-anchor="middle">【亞述 · 尼尼微大城】</text>
            <text x="895" y="295" text-anchor="middle">【兩河流域 · 吾珥與巴比倫】</text>
            <text x="935" y="342" text-anchor="middle">【波斯 · 書珊城】</text>
            <text x="455" y="135" text-anchor="middle">【小亞細亞 · 啟示錄七教會】</text>
            <text x="340" y="78" text-anchor="middle">【馬其頓 · 腓立比】</text>
            <text x="315" y="198" text-anchor="end">【亞該亞 · 雅典與哥林多】</text>
            <text x="404" y="192" text-anchor="middle" fill="#dfba64" font-size="11">【拔摩海島】</text>
            <text x="75" y="72" text-anchor="middle" fill="#dfba64">【義大利 · 羅馬】</text>
            <text x="275" y="285" text-anchor="middle" fill="rgba(145,195,230,0.45)" font-size="13.5" letter-spacing="5">～～ 滄 海（使 徒 保 羅 遠 洋 宣 教 航 路）～～</text>
          </g>
        </g>
        <g id="pins"></g>
      </svg>
      <div id="map-hover-card"></div>
      <div id="map-hint">點擊聖地星芒光點，或從右側「聖經 120 篇章一覽」查閱每關專屬經文領袖與歷史對手</div>
    </div>

    <aside id="battle-list">
      <div class="bl-head">
        <span>📜 聖經 120 篇章總覽</span>
        <small>聖史戰局</small>
      </div>
      <div class="bl-filter-wrap">
        <input type="text" id="bl-search" class="bl-search-input" placeholder="🔍 檢索篇章、經文、領袖或對手（如：耶和華、歌利亞、救恩）…">
        <div class="bl-theater-tabs" id="bl-tabs">
          <button class="bl-tab active" data-th="all">全卷(120)</button>
          <button class="bl-tab" data-th="pentateuch">五經(20)</button>
          <button class="bl-tab" data-th="joshua">士師(15)</button>
          <button class="bl-tab" data-th="kingdom">列王(15)</button>
          <button class="bl-tab" data-th="prophets">先知(10)</button>
          <button class="bl-tab" data-th="gospels">福音(30)</button>
          <button class="bl-tab" data-th="acts">使徒啟示(30)</button>
        </div>
      </div>
      <div id="battle-list-items"></div>
    </aside>
  </div>
</div>

<!-- ============ 畫面二：經文與神學導讀 ============ -->
<div id="screen-brief" class="screen hidden">
  <header id="brief-header">
    <button class="btn ghost" id="btn-brief-back">← 返回全景聖史地圖</button>
    <div style="color:var(--accent);font-weight:800;letter-spacing:1.5px">🕯️ 聖經經文考釋與戰術陣型佈署</div>
  </header>
  <div id="brief-body"></div>
</div>

<!-- ============ 畫面三：棋局對弈 ============ -->
<div id="screen-game" class="screen hidden">
  <div id="game-top">
    <button class="btn ghost sm" id="btn-game-back">🗺 聖史地圖</button>
    <div id="game-title"></div>
    <div id="turn-box">
      <span id="turn-indicator"></span>
      <span id="thinking" class="hidden">天軍與歷史推演中…</span>
    </div>
    <div class="top-btns">
      <button class="btn ghost sm" id="btn-quiz-game">📖 庇哩亞問答(+信心)</button>
      <button class="btn ghost sm" id="btn-audio-game">🔊 音律：開</button>
      <button class="btn ghost sm" id="btn-scripture-game">📜 本章經文</button>
      <button class="btn ghost sm" id="btn-codex-game">🛡️ 聖物圖鑑</button>
      <button class="btn ghost sm" id="btn-saves-game">💾 聖卷書籤</button>
      <button class="btn ghost sm" id="btn-restart">↻ 重新部署</button>
    </div>
  </div>
  <div id="game-main">
    <div id="board-area">
      <div id="sabbath-bar"></div>
      <div id="ai-banner" class="army-banner"></div>
      <div id="board-with-labels">
        <div id="row-labels"></div>
        <div id="board"></div>
        <div id="col-labels"></div>
      </div>
      <div id="player-banner" class="army-banner"></div>
    </div>
    <div id="side-panel">
      <!-- 信心神蹟祈禱面板 -->
      <div class="panel-card" id="miracle-card">
        <div class="card-title" style="display:flex;justify-content:space-between;align-items:center">
          <span>✨ 信心祈禱 · 屬靈神蹟介入</span>
          <span id="faith-badge" style="color:var(--faith);font-size:12px">信心 4 / 10</span>
        </div>
        <div class="faith-meter-wrap">
          <div style="display:flex;justify-content:space-between;font-size:11px;color:var(--dim)">
            <span>築壇(a)、查經問答或安息日可累積信心</span>
            <span id="faith-status-txt" style="color:#ffe180">可懇求神蹟</span>
          </div>
          <div class="faith-bar-bg"><div class="faith-bar-fill" id="faith-bar-fill" style="width:40%"></div></div>
        </div>
        <div class="miracle-grid">
          <button class="miracle-btn" id="btn-miracle-manna" title="出埃及記 16:14 / 五餅二魚：賜予全場同行者恩典神聖護盾">
            <b>🍞 嗎哪與五餅二魚</b><small>3 點信心 (全員護盾)</small>
          </button>
          <button class="miracle-btn" id="btn-miracle-waters" title="出埃及記 14:21：將水域與沼澤化為乾地走廊">
            <b>🌊 分開紅海／約旦河</b><small>4 點信心 (開闢水路)</small>
          </button>
          <button class="miracle-btn" id="btn-miracle-shofar" title="約書亞記 6:20：吹起羊角號震平敵陣城牆與荊棘">
            <b>📯 耶利哥吹角塌牆</b><small>5 點信心 (震平城牆)</small>
          </button>
          <button class="miracle-btn" id="btn-miracle-gibeon" title="約書亞記 10:12：日頭停在基遍！我方連續行動兩回合">
            <b>☀️ 亞雅崙日頭停留</b><small>7 點信心 (連續行動)</small>
          </button>
        </div>
        <div class="tactical-tools-row">
          <button class="tac-tool-btn" id="btn-tac-undo">↩ 悔棋</button>
          <button class="tac-tool-btn" id="btn-tac-threat">👁 警戒網</button>
          <button class="tac-tool-btn" id="btn-tac-hint">💡 默想</button>
          <button class="tac-tool-btn" id="btn-tac-quiz">📖 問答</button>
        </div>
      </div>

      <!-- 選中同行者與領袖卡 -->
      <div class="panel-card" id="sel-card">
        <div class="card-title" style="display:flex;justify-content:space-between;align-items:center">
          <span>🕊️ 聖約使者與領袖恩賜</span>
          <span id="sel-coord-badge" style="font-size:11px;color:var(--accent);font-weight:400">點擊棋盤棋子</span>
        </div>
        <div id="sel-box" style="font-size:12px;color:var(--dim);line-height:1.5">點擊棋盤上我方領袖或對手主將，可檢視其正統聖經背景與主動恩賜。</div>
      </div>

      <div class="panel-card" id="obj-card">
        <div class="card-title">🎯 本章勝負準則與經文目標</div>
        <div id="obj-text"></div>
        <div id="obj-progress"></div>
      </div>
      <div class="panel-card" id="terrain-card">
        <div class="card-title">⛰️ 聖地地貌情報</div>
        <div id="terrain-legend"></div>
      </div>
      <div class="panel-card" id="forces-card">
        <div class="card-title">🛡️ 聖史對陣陣容</div>
        <div id="forces-lists"></div>
      </div>
      <div class="panel-card grow" id="log-card">
        <div class="card-title">🕯️ 聖約見證日誌</div>
        <div id="battle-log"></div>
      </div>
    </div>
  </div>
</div>

<!-- ============ 彈窗 ============ -->
<div id="modal-overlay" class="hidden">
  <div id="modal-box">
    <div id="modal-content"></div>
    <div id="modal-btns"></div>
  </div>
</div>

<script>
"use strict";

/* ============ 0. 純 Web Audio API 聖所音律合成器 ============ */
const BiblicalAudio = {
  ctx: null,
  enabled: true,
  init() {
    if (!this.ctx) {
      const AC = window.AudioContext || window.webkitAudioContext;
      if (AC) this.ctx = new AC();
    }
    if (this.ctx && this.ctx.state === "suspended") this.ctx.resume();
  },
  toggle() {
    this.enabled = !this.enabled;
    const txt = this.enabled ? "🔊 聖所音律：開" : "🔇 聖所音律：關";
    const txtSm = this.enabled ? "🔊 音律：開" : "🔇 音律：關";
    const b1 = document.getElementById("btn-audio-toggle");
    const b2 = document.getElementById("btn-audio-game");
    if (b1) b1.textContent = txt;
    if (b2) b2.textContent = txtSm;
    if (this.enabled) this.playHarpChord([440, 554.37, 659.25]);
  },
  playHarpNote(freq = 440, dur = 0.65, delay = 0, vol = 0.14) {
    if (!this.enabled) return;
    this.init();
    if (!this.ctx) return;
    const t0 = this.ctx.currentTime + delay;
    const osc = this.ctx.createOscillator();
    const osc2 = this.ctx.createOscillator();
    const gain = this.ctx.createGain();
    osc.type = "triangle";
    osc2.type = "sine";
    osc.frequency.setValueAtTime(freq, t0);
    osc2.frequency.setValueAtTime(freq * 2, t0);
    gain.gain.setValueAtTime(0.001, t0);
    gain.gain.linearRampToValueAtTime(vol, t0 + 0.02);
    gain.gain.exponentialRampToValueAtTime(0.0008, t0 + dur);
    osc.connect(gain); osc2.connect(gain); gain.connect(this.ctx.destination);
    osc.start(t0); osc2.start(t0);
    osc.stop(t0 + dur); osc2.stop(t0 + dur);
  },
  playHarpChord(notes = [293.66, 369.99, 440, 587.33], step = 0.08) {
    notes.forEach((f, idx) => this.playHarpNote(f, 1.1, idx * step, 0.13));
  },
  playShofar() {
    if (!this.enabled) return;
    this.init();
    if (!this.ctx) return;
    const now = this.ctx.currentTime;
    const osc = this.ctx.createOscillator();
    const filter = this.ctx.createBiquadFilter();
    const gain = this.ctx.createGain();
    osc.type = "sawtooth";
    osc.frequency.setValueAtTime(285, now);
    osc.frequency.linearRampToValueAtTime(293.66, now + 0.18);
    osc.frequency.exponentialRampToValueAtTime(440, now + 0.55);
    osc.frequency.setValueAtTime(440, now + 1.25);
    osc.frequency.linearRampToValueAtTime(415, now + 1.55);
    filter.type = "lowpass";
    filter.frequency.setValueAtTime(950, now);
    filter.Q.setValueAtTime(4.5, now);
    gain.gain.setValueAtTime(0.001, now);
    gain.gain.linearRampToValueAtTime(0.24, now + 0.15);
    gain.gain.setValueAtTime(0.22, now + 1.15);
    gain.gain.exponentialRampToValueAtTime(0.001, now + 1.6);
    osc.connect(filter); filter.connect(gain); gain.connect(this.ctx.destination);
    osc.start(now); osc.stop(now + 1.65);
  },
  playSeaWaves(dur = 1.4) {
    if (!this.enabled) return;
    this.init();
    if (!this.ctx) return;
    const now = this.ctx.currentTime;
    const bufferSize = this.ctx.sampleRate * dur;
    const buffer = this.ctx.createBuffer(1, bufferSize, this.ctx.sampleRate);
    const data = buffer.getChannelData(0);
    for (let i = 0; i < bufferSize; i++) data[i] = Math.random() * 2 - 1;
    const noise = this.ctx.createBufferSource();
    noise.buffer = buffer;
    const filter = this.ctx.createBiquadFilter();
    filter.type = "bandpass";
    filter.frequency.setValueAtTime(260, now);
    filter.frequency.exponentialRampToValueAtTime(780, now + dur * 0.5);
    filter.frequency.exponentialRampToValueAtTime(220, now + dur);
    filter.Q.setValueAtTime(1.8, now);
    const gain = this.ctx.createGain();
    gain.gain.setValueAtTime(0.001, now);
    gain.gain.linearRampToValueAtTime(0.22, now + dur * 0.35);
    gain.gain.exponentialRampToValueAtTime(0.001, now + dur);
    noise.connect(filter); filter.connect(gain); gain.connect(this.ctx.destination);
    noise.start(now); noise.stop(now + dur);
  },
  playMiracleChime() {
    this.playHarpChord([523.25, 659.25, 783.99, 1046.5, 1318.5], 0.09);
  }
};

/* ============ 1. 22 種純聖經正統器物與異象 SVG 圖示 ============ */
const ICON_SVG = {
  hq: `<rect x="6" y="16" width="20" height="9" rx="1.5"/>
     <line x1="3" y1="21" x2="29" y2="21" stroke="currentColor" stroke-width="2.2"/>
     <path d="M7 16 c0 -6 5 -9 9 -4 c4 -5 9 -2 9 4 z"/>
     <circle cx="16" cy="8" r="2.5"/>`,
  flagship: `<path d="M3 20 h26 l-3.5 7 h-19 z"/>
     <rect x="6" y="13" width="20" height="7" rx="1"/>
     <path d="M4 13 l12 -6 l12 6 z"/>
     <path d="M7 7 a11 9 0 0 1 18 0" fill="none" stroke="currentColor" stroke-width="1.8"/>`,
  infantry: `<circle cx="14.5" cy="8.5" r="4"/>
     <path d="M8.5 27 l2.2 -11.5 q3.8 -2.5 7.6 0 l2.2 11.5 z"/>
     <path d="M23 5 a3.5 3.5 0 1 1 -3.2 4.8" fill="none" stroke="currentColor" stroke-width="2.2"/>
     <line x1="23" y1="8.5" x2="23" y2="27" stroke="currentColor" stroke-width="2.2"/>`,
  commando: `<path d="M5 23 q9 1 15 -11 l3.5 2.5 q-7 13 -17 12.5 z"/>
     <path d="M20 12 l5 -4 l2 3 l-4.5 3.5 z"/>
     <path d="M9 11 c0 -4 3 -6 4 -8 c1 2 4 4 4 8 a4 4 0 0 1 -8 0 z"/>`,
  fighter: `<path d="M16 9 c4 -6 12 -4 13 3 c-3.5 2 -6.5 2.5 -9.5 2.5 l5 7.5 l-8.5 -3 l-8.5 3 l5 -7.5 c-3 0 -6 -0.5 -9.5 -2.5 c1 -7 9 -9 13 -3 z"/>
     <circle cx="16" cy="7" r="2.4"/>`,
  bomber: `<path d="M16 2 c5.5 6 8.5 11.5 5 18 c-1.5 3 -5 4.5 -5 4.5 s-3.5 -1.5 -5 -4.5 c-3.5 -6.5 -0.5 -12 5 -18 z"/>
     <path d="M16 9 c2.5 3 3.5 6.5 0 10.5 c-3.5 -4 -2.5 -7.5 0 -10.5 z" fill="rgba(0,0,0,.35)"/>
     <rect x="8" y="25" width="16" height="3.5" rx="1.5"/>`,
  tank: `<path d="M7 5 h18 v11.5 c0 6.5 -9 10.5 -9 10.5 s-9 -4 -9 -10.5 z"/>
     <line x1="16" y1="8" x2="16" y2="23" stroke="rgba(0,0,0,.48)" stroke-width="2.6"/>
     <line x1="10" y1="13.5" x2="22" y2="13.5" stroke="rgba(0,0,0,.48)" stroke-width="2.6"/>`,
  td: `<polygon points="16,2 19,20 13,20"/>
     <rect x="9" y="20" width="14" height="3" rx="1.2"/>
     <rect x="14.2" y="23" width="3.6" height="5" rx="1"/>
     <circle cx="16" cy="29" r="1.8"/>`,
  artillery: `<path d="M8 6 v17 a3 3 0 0 0 3 3 h11 v-3 h-9 v-15 c4 0 8 2 10 7 l2.5 -1.5 c-2.5 -6.5 -7.5 -9.5 -17.5 -7.5 z"/>
     <line x1="13" y1="8" x2="13" y2="23" stroke="currentColor" stroke-width="1.5"/>
     <line x1="16.5" y1="9" x2="16.5" y2="23" stroke="currentColor" stroke-width="1.5"/>
     <line x1="20" y1="11" x2="20" y2="23" stroke="currentColor" stroke-width="1.5"/>`,
  engineer: `<polygon points="16,3 24,13 16,17 8,13"/>
     <rect x="14.5" y="17" width="3" height="4"/>
     <rect x="6" y="21" width="9" height="5.5" rx="1"/>
     <rect x="17" y="21" width="9" height="5.5" rx="1"/>`,
  kamikaze: `<circle cx="16" cy="15" r="4.2"/>
     <path d="M16 11 c-4 -7 -11 -7 -12 -2 c3 2 6 3 9 4 z"/>
     <path d="M16 11 c4 -7 11 -7 12 -2 c-3 2 -6 3 -9 4 z"/>
     <path d="M16 19 c-5 5 -11 6 -12 2 c3 -2 6 -2 9 -3 z"/>
     <path d="M16 19 c5 5 11 6 12 2 c-3 -2 -6 -2 -9 -3 z"/>`,
  partisan: `<line x1="16" y1="3" x2="16" y2="28" stroke="currentColor" stroke-width="2.6"/>
     <line x1="10" y1="9" x2="22" y2="9" stroke="currentColor" stroke-width="2.6"/>
     <path d="M9 24 q7 -5 14 0 l2 4 h-18 z"/>`,
  mortar: `<path d="M6 17 l2 -3 v3 h16 v-3 l2 3 v10 h-20 z"/>
     <path d="M13 13 c-2 -3 2 -5 0 -9 M19 13 c-2 -3 2 -5 0 -9" fill="none" stroke="currentColor" stroke-width="2.2"/>`,
  katyusha: `<path d="M5 24 l18 -18 l3 3 l-18 18 z"/>
     <path d="M27 24 l-18 -18 l-3 3 l18 18 z"/>
     <circle cx="16" cy="6" r="2.6"/>`,
  armoredtrain: `<path d="M5 19 c0 -6 5 -10 11 -10 h8 l2 5 l-4 2 v3 z"/>
     <circle cx="11" cy="22" r="5" stroke="currentColor" stroke-width="2.2" fill="rgba(0,0,0,.4)"/>
     <circle cx="22" cy="22" r="5" stroke="currentColor" stroke-width="2.2" fill="rgba(0,0,0,.4)"/>
     <path d="M9 9 c2 -4 6 -5 9 -2" fill="none" stroke="currentColor" stroke-width="2"/>`,
  sub: `<path d="M3 17 q11 -9 21 -2 l5 -4 l-1.5 6 l1.5 6 l-5 -4 q-10 7 -21 -2 z"/>
     <circle cx="10.5" cy="15.5" r="1.8" fill="rgba(0,0,0,.55)"/>`,
  destroyer: `<path d="M4 21 h24 l-4 6 h-16 z"/>
     <path d="M15 5 v15 M15 6 l9 11 h-9 z"/>`,
  cruiser: `<path d="M3 21 h26 l-3.5 6 h-19 z"/>
     <path d="M12 6 v14 M12 6 l8 11 h-8 z"/>
     <path d="M21 9 v11 M21 9 l5 8 h-5 z"/>`,
  battleship: `<path d="M2 21 h28 l-4 7 h-20 z"/>
     <path d="M9 6 v14 M9 7 l7 10 h-7 z"/>
     <path d="M19 5 v15 M19 6 l8 11 h-8 z"/>`,
  carrier: `<path d="M2 21 h28 l-3.5 6.5 h-21 z"/>
     <path d="M16 4 v16 M16 5 l10 11 h-20 z"/>`,
  mtb: `<path d="M4 18 q12 10 24 0 l-3 7 h-18 z"/>
     <path d="M8 18 a8 7 0 0 1 16 0 z"/>`,
  transport: `<path d="M3 20 h26 l-4 7 h-18 z"/>
     <circle cx="10.5" cy="16.5" r="3"/><circle cx="16" cy="15.5" r="3.4"/><circle cx="21.5" cy="16.5" r="3"/>`,
};

const PIECE_DEFS = {
  hq:         { name: "至聖所核心／聖約會幕", chess: "王 (King)·聖約核心", move: "king",   domain: "land",  vehicle: false, value: 100000, isKing: true,
    desc: "我方為聖史領袖與聖約見證會幕，敵方為該章節的具名歷史強敵或幽暗權勢核心。每次八方移動一格。" },
  flagship:   { name: "立約方舟／使徒主船", chess: "王 (King)·水上主帥", move: "king", domain: "water", vehicle: false, value: 100000, isKing: true,
    desc: "水上篇章的歌斐木方舟或使徒宣教主船核心，每次航行一格。" },
  infantry:   { name: "信心門徒／聖約子民", chess: "兵 (Pawn)·憑信前行", move: "pawn",   domain: "land",  vehicle: false, value: 100,
    desc: "「我們行事為人是憑著信心，不是憑著眼見」（林後 5:7）。直線前行，斜向光照化解。抵達終點線可蒙恩晉升！" },
  commando:   { name: "基甸勇士／族長近衛", chess: "馬 (Knight)·跨越奇兵", move: "knight", domain: "land",  vehicle: false, value: 310,
    desc: "「三百人吹角，打破瓶子，左手拿著火把」（士 7:20）。走「日」字跨越一切山嶺與城牆障礙。" },
  fighter:    { name: "天使信使／報佳音者", chess: "象 (Bishop)·佳美腳蹤", move: "bishop", domain: "air",   vehicle: false, value: 330,
    desc: "「那報佳音、傳平安、報好信、傳救恩的，他的腳登山何等佳美！」（賽 52:7）。沿斜線任意距離跨越山海與混沌深淵。" },
  bomber:     { name: "雲柱火柱／榮耀晨光", chess: "車 (Rook)·聖別光照",  move: "rook",   domain: "air",   vehicle: false, value: 490,
    desc: "「日間耶和華在雲柱中領他們的路；夜間在火柱中光照他們」（出 13:21）。沿直線任意距離跨越山川，驅散一切幽暗攔阻。" },
  tank:       { name: "信德藤牌衛隊／重盾方陣", chess: "車 (Rook)·堅固推進",  move: "rook",   domain: "land",  vehicle: true,  value: 500,
    desc: "「拿著信德當作藤牌，可以滅盡那惡者一切的火箭」（弗 6:16）；在敵方則代表法老鐵車營陣。沿直線任意距離推進。" },
  td:         { name: "聖靈寶劍真道／王權銅戟", chess: "后 (Queen)·全向威能", move: "queen",  domain: "land",  vehicle: true,  value: 680,
    desc: "我方為「神的道是活潑的，比一切兩刃的劍更快」（來 4:12）；敵方則代表歌利亞巨戟與帝國精銳。直線與斜線任意推進！" },
  artillery:  { name: "大衛機弦詩琴／十絃瑟", chess: "象 (Bishop)·遠程甩石", move: "bishop", domain: "land", vehicle: true, value: 380,
    desc: "取自大衛在以拉谷挑選五顆光滑溪石的機弦與十絃瑟（撒上 17:40），沿斜線遠程推進並擊退強敵。" },
  engineer:   { name: "尼希米巧匠／修垣工匠", chess: "王 (King)·築壇除荊", move: "king",   domain: "land",  vehicle: false, value: 270, ignoreMine: true,
    desc: "「修造城牆的，都一手做工，一手拿兵器」（尼 4:17）。八方移動一格，可清除曠野荊棘網羅(x)與攀登聖山。" },
  kamikaze:   { name: "撒拉弗聖壇炭／基路伯火劍", chess: "后 (Queen)·天火潔淨", move: "queen",  domain: "air",   vehicle: false, value: 620,
    desc: "《創世記》3:24 四面轉動發火焰的劍與《以賽亞書》6:6 六翼撒拉弗紅炭，沿直線與斜線跨越一切地形！" },
  partisan:   { name: "曠野開路先鋒／拿細耳人", chess: "馬 (Knight)·修直主路", move: "knight", domain: "land",  vehicle: false, value: 340, ignoreMine: true,
    desc: "「在曠野有人聲喊著說：預備主的道，修直祂的路！」（太 3:3）。走「日」字跨越障礙，自由通過荊棘與高山。" },
  mortar:     { name: "守望代求祭壇", chess: "象 (Bishop)·登高代求", move: "bishop", domain: "land",  vehicle: false, allowMtn: true, value: 360,
    desc: "「願我的禱告如香陳列在你面前」（詩 141:2）。沿斜線移動與光照，可登上西乃高山(m)與橄欖林(f)守望。" },
  katyusha:   { name: "利未讚美詩班／銀號隊", chess: "車 (Rook)·頌讚前鋒",  move: "rook",   domain: "land",  vehicle: true,  value: 520,
    desc: "約沙法王設立走在軍前歌頌耶和華的利未詩班與祭司銀號（代下 20:21），沿直線推進震退強敵。" },
  armoredtrain:{ name: "多坍火車火馬", chess: "后 (Queen)·天軍圍繞", move: "queen",  domain: "land",  vehicle: true,  value: 650,
    desc: "以利沙祈求開少年人眼目所見「滿山有火車火馬圍繞以利沙」（王下 6:17），沿直線與斜線馳騁。" },
  sub:        { name: "約拿深海大魚／深淵海怪", chess: "象 (Bishop)·深海潛行", move: "bishop", domain: "water", vehicle: false, value: 300, noAir: true, waterOnly: true,
    desc: "「耶和華安排一條大魚吞了約拿，約拿在魚腹中禱告」（拿 1:17-2:1）。沿斜線在水域深處潛行任意距離。" },
  destroyer:  { name: "約旦河護航舟", chess: "車 (Rook)·水面護航",  move: "rook",   domain: "water", vehicle: false, value: 400,
    desc: "沿直線航行江河與海域任意距離，為水陸同行者提供遠程策應。" },
  cruiser:    { name: "加利利福音船", chess: "象 (Bishop)·湖面傳道", move: "bishop", domain: "water", vehicle: false, value: 440,
    desc: "航行於加利利海的福音船，沿斜線巡航水域並向岸邊傳講天國真理。" },
  battleship: { name: "保羅遠洋大帆船", chess: "后 (Queen)·跨海宣教", move: "queen",  domain: "water", vehicle: false, value: 850,
    desc: "如使徒保羅三次宣教旅程與前往羅馬所乘的亞歷山大遠洋帆船（徒 27:6），直線與斜線任意航行。" },
  carrier:    { name: "得人漁船／深水下網船", chess: "車 (Rook)·深水撒網", move: "rook",   domain: "water", vehicle: false, value: 550, noShore: true,
    desc: "「把船開到水深之處，下網打魚……從今以後你要得人了」（路 5:4,10）。沿直線航行任意距離。" },
  mtb:        { name: "尼羅河蒲草箱舟", chess: "馬 (Knight)·蘆葦神蹟", move: "knight", domain: "water", vehicle: false, noShore: true, value: 340,
    desc: "如保護嬰孩摩西的蒲草箱（出 2:3），走「日」字在水域與蘆葦淺灘(r)間靈活穿行。" },
  transport:  { name: "五餅二魚供應船／嗎哪輜重", chess: "王 (King)·恩典供應",  move: "king",   domain: "water", vehicle: false, value: 350, noAttack: true,
    desc: "滿載五餅二魚與愛心供應的船隻或營隊（太 14:19），每回合移動一格，受全軍嚴密保護。" },
};

const DOMAIN_NAME = { land: "同行步履", water: "水路恩典", air: "屬天異象" };

function pieceIcon(type, cls) {
  return `<svg viewBox="0 0 32 32" class="picon ${cls || ""}">${ICON_SVG[type] || ICON_SVG.infantry}</svg>`;
}

/* ============ 2. 聖地地形定義 ============ */
const TERRAIN = {
  "v": { name: "太初空虛混沌深淵", void: true, noGround: true },
  "L": { name: "神說要有光·太初真光", land: true, water: true },
  "~": { name: "太初淵水／紅海／加利利海", water: true },
  "b": { name: "紅海乾地走廊／約旦河淺灘", land: true, water: true },
  ".": { name: "迦南青草牧場", land: true },
  "f": { name: "伊甸生命樹／客西馬尼橄欖林", land: true, noVehicle: true },
  "c": { name: "聖經城邑與會堂", land: true },
  "u": { name: "待修荒涼城垣", land: true, noVehicle: true },
  "m": { name: "西乃與錫安聖山", land: true, infOnly: true },
  "s": { name: "以琳十二水泉綠洲", land: true },
  "w": { name: "黑門山雪嶺", land: true },
  "i": { name: "寶座前水晶玻璃海", land: true, water: true },
  "d": { name: "猶太與巴蘭曠野", land: true },
  "x": { name: "曠野荊棘試探網羅", land: true, noGround: true },
  "B": { name: "敵方堅固營壘／王權要塞", land: true, marker: "bunker" },
  "F": { name: "應許立石標竿(以便以謝)", land: true, water: true, marker: "flag" },
  "g": { name: "基順河谷泥沼", land: true, noVehicle: true },
  "t": { name: "耶利哥／尼希米守望石牆", land: true, noVehicle: true },
  "r": { name: "尼羅河蘆葦淺水灘", water: true, land: true, infOnly: true },
  "l": { name: "錫安上行朝聖路", land: true },
  "h": { name: "伯大尼與馬可樓房舍", land: true, noVehicle: true },
  "p": { name: "迦百農與約帕古漁港", land: true, water: true },
  "a": { name: "伯特利築壇獻祭所(查經點)", land: true },
  "=": { name: "以馬忤斯與羅馬大道", land: true },
  "H": { name: "至聖所會幕避難所", land: true, water: true, marker: "bunker" },
};

const TERR_COLOR = {
  "v": "var(--void)", "L": "var(--light)",
  "~": "var(--water)", "b": "var(--beach)", ".": "var(--plain)", "f": "var(--forest)",
  "c": "var(--city)", "u": "var(--ruin)", "m": "var(--mtn)", "s": "var(--sand)",
  "w": "var(--snow)", "i": "var(--ice)", "d": "var(--desert)", "x": "var(--mine)",
  "B": "var(--city)", "F": "var(--city)", "g": "var(--marsh)", "t": "var(--trench)",
  "r": "var(--reef)", "l": "var(--rail)", "h": "var(--house)", "p": "var(--port)",
  "a": "var(--airfield)", "=": "var(--road)", "H": "var(--city)"
};

const TERR_CLASS = {
  "v": "t-vd", "L": "t-lt",
  "~": "t-w", "b": "t-b", ".": "t-p", "f": "t-f", "c": "t-c", "u": "t-u",
  "m": "t-m", "s": "t-s", "w": "t-sn", "i": "t-ic", "d": "t-ds", "x": "t-mn",
  "B": "t-c zone-bunker", "F": "t-c zone-flag", "g": "t-mr", "t": "t-tr",
  "r": "t-rf", "l": "t-rl", "h": "t-hs", "p": "t-pt", "a": "t-af", "=": "t-rd", "H": "t-c zone-bunker"
};

function P(type, r, c, heroId) { return { type, r, c, heroId }; }

/* ============ 3. 完整 36 位聖經核心領袖與專屬主動神蹟恩賜 ============ */
const BIBLICAL_HEROES = {
  yahweh: {
    id: "yahweh", name: "耶和華（神的靈）", title: "創造天地萬物的自有永有者", ref: "創世記 1:2-3",
    quote: "「地是空虛混沌，淵面黑暗；神的靈運行在水面上. 神說：要有光，就有了光。」",
    skillName: "✨ 神說：要有光",
    skillDesc: "將全場阻礙通行的「太初空虛混沌深淵(v)」與幽暗網羅(x)瞬間化為「✨ 太初真光大道(L)」，並呼召 2 隊雲柱晨光！",
    cast(st, hero) {
      BiblicalAudio.playMiracleChime();
      const rows = st.battle.terrain.map(r => r.split(""));
      let lit = 0;
      for (let r = 0; r < st.rows; r++) for (let c = 0; c < st.cols; c++) {
        if (rows[r][c] === "v" || rows[r][c] === "x") { rows[r][c] = "L"; lit++; }
      }
      st.battle.terrain = rows.map(r => r.join(""));
      let sp = 0;
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc] && sp < 2) {
          st.board[nr][nc] = { type: "bomber", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          sp++;
        }
      }
      st.faith = 10;
      buildBoard();
      return `✨ 神說：「要有光！」就有了光！${lit} 處混沌深淵化為太初真光，神看光是好的，把光暗分開了！`;
    }
  },
  adam: {
    id: "adam", name: "亞當與夏娃", title: "伊甸園的修理看守者", ref: "創世記 2:15",
    quote: "「耶和華神將那人安置在伊甸園，使他修理，看守。」",
    skillName: "🌳 伊甸生命樹果子",
    skillDesc: "全體我方看守者披戴恩典神聖護盾，並恢復 +3 點信心。",
    cast(st) {
      BiblicalAudio.playHarpChord([329.63, 440, 554.37], 0.08);
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      st.faith = Math.min(10, st.faith + 3);
      return `🌳 伊甸四河滋潤園子！全體看守者領受生命樹庇蔭與恩典神聖護盾！`;
    }
  },
  noah: {
    id: "noah", name: "挪亞 (Noah)", title: "與神同行的義人 · 方舟建造者", ref: "創世記 6:22",
    quote: "「挪亞就這樣行. 凡神所吩咐他的，他都照樣行了。」",
    skillName: "🕊️ 放鴿銜回橄欖葉",
    skillDesc: "呼召 2 隻「天使信使(fighter)」跨越洪水深淵偵察並清除周圍暗礁(r)，全船隊獲得護盾。",
    cast(st, hero) {
      BiblicalAudio.playSeaWaves(1.2);
      const rows = st.battle.terrain.map(r => r.split(""));
      for (let r = 0; r < st.rows; r++) for (let c = 0; c < st.cols; c++) if (rows[r][c] === "r") rows[r][c] = "~";
      st.battle.terrain = rows.map(r => r.join(""));
      let sp = 0;
      for (const [dr, dc] of [[-1,-1],[-1,1],[0,-1],[0,1]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc] && sp < 2) {
          st.board[nr][nc] = { type: "fighter", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          sp++;
        }
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      buildBoard();
      return `🕊️ 白鴿嘴裡叼著新擰下來的橄欖葉飛回方舟！暗礁消退，彩虹之約護庇全船！`;
    }
  },
  abraham: {
    id: "abraham", name: "亞伯拉罕 (Abraham)", title: "信心之父 · 神的朋友", ref: "創世記 15:6",
    quote: "「亞伯蘭信耶和華，耶和華就以此為他的義。」",
    skillName: "🔥 摩利亞山築壇仰望",
    skillDesc: "將所在格化為伯特利築壇處(a)，立即獲得 +4 點信心並為全軍披戴護盾。",
    cast(st, hero) {
      BiblicalAudio.playHarpChord([329.63, 440, 554.37, 659.25], 0.08);
      const rows = st.battle.terrain.map(r => r.split(""));
      rows[hero.r][hero.c] = "a";
      st.battle.terrain = rows.map(r => r.join(""));
      st.faith = Math.min(10, (st.faith || 0) + 4);
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      buildBoard();
      return `🔥 亞伯拉罕築壇求告耶和華以勒！信心大幅提升 +4，全體蒙受祝福！`;
    }
  },
  jacob: {
    id: "jacob", name: "雅各 / 以色列 (Jacob)", title: "與神與人較力得勝的族長", ref: "創世記 28:17",
    quote: "「這不是別的，乃是神的殿，也是天的門！」",
    skillName: "🪜 伯特利天梯使者",
    skillDesc: "天梯展開，神的使者上去下來！在雅各身旁呼召 2 隊「撒拉弗聖壇炭(kamikaze)」或天使助陣。",
    cast(st, hero) {
      BiblicalAudio.playMiracleChime();
      let sp = 0;
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc] && sp < 2) {
          st.board[nr][nc] = { type: sp === 0 ? "kamikaze" : "fighter", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          sp++;
        }
      }
      return `🪜 伯特利天梯向天敞開！神的使者上去下來，降臨戰場護衛以色列！`;
    }
  },
  joseph: {
    id: "joseph", name: "約瑟 (Joseph)", title: "枝子探出牆外 · 解夢宰相", ref: "創世記 50:20",
    quote: "「從前你們的意思是要害我，但神的意思原是好的，要保全許多人的性命。」",
    skillName: "🌾 七個豐年開倉賑糧",
    skillDesc: "全體我方同行者披戴恩典神聖護盾，並直接將信心值補滿至 10 點！",
    cast(st) {
      BiblicalAudio.playMiracleChime();
      st.faith = 10;
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      return `🌾 約瑟打開埃及積蓄倉賑濟萬民！全隊獲得恩典神聖護盾，信心值直接滿溢至 10 點！`;
    }
  },
  moses: {
    id: "moses", name: "摩西 (Moses)", title: "神人 · 領百姓出埃及的先知", ref: "出埃及記 14:16",
    quote: "「不要懼怕，只管站穩！看耶和華今天向你們所要施行的救恩。」",
    skillName: "🌊 舉杖分水為乾地",
    skillDesc: "將摩西周圍 3 格內的水域(~)化為可通行的紅海乾地走廊(b)，並賜予全體信心行者護盾。",
    cast(st, hero) {
      BiblicalAudio.playSeaWaves(1.6);
      let conv = 0;
      const rows = st.battle.terrain.map(r => r.split(""));
      for (let dr = -3; dr <= 3; dr++) for (let dc = -3; dc <= 3; dc++) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && rows[nr][nc] === "~" && !st.board[nr][nc]) {
          rows[nr][nc] = "b"; conv++;
        }
      }
      st.battle.terrain = rows.map(r => r.join(""));
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      buildBoard();
      return `🌊 摩西向海伸杖！大東風吹起，${conv} 處深水立起成壘化為乾地走廊，百姓全體披戴恩典神聖護盾！`;
    }
  },
  joshua: {
    id: "joshua", name: "約書亞 (Joshua)", title: "嫩的兒子 · 耶和華軍隊的元帥", ref: "約書亞記 1:9",
    quote: "「你當剛強壯膽！不要懼怕，也不要驚惶；因為你無論往哪裡去，耶和華你的神必與你同在。」",
    skillName: "📯 繞城吹角塌牆",
    skillDesc: "吹響羊角號清除棋盤上所有荒涼廢墟(u)、守望石牆(t)與荊棘(x)，並讓全軍獲得剛強護盾。",
    cast(st) {
      BiblicalAudio.playShofar();
      const rows = st.battle.terrain.map(r => r.split(""));
      for (let r = 0; r < st.rows; r++) for (let c = 0; c < st.cols; c++) {
        if (rows[r][c] === "u" || rows[r][c] === "x" || rows[r][c] === "t") rows[r][c] = ".";
      }
      st.battle.terrain = rows.map(r => r.join(""));
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      buildBoard();
      return `📯 約書亞吩咐祭司吹響羊角號！耶利哥城牆與荊棘瞬間塌陷為坦途，全軍剛強壯膽！`;
    }
  },
  caleb: {
    id: "caleb", name: "迦勒 (Caleb)", title: "專一跟從耶和華的老將", ref: "約書亞記 14:12",
    quote: "「求你將耶和華那日應許我的這山地給我！現在我還是強壯，像摩西打發我去的那天一樣。」",
    skillName: "⛰️ 攻取希伯崙山地",
    skillDesc: "將全場崎嶇高山(m)化為可通行的朝聖大道(=)，並將身旁 1 名門徒晉升為信德藤牌衛隊！",
    cast(st) {
      BiblicalAudio.playShofar();
      const rows = st.battle.terrain.map(r => r.split(""));
      for (let r = 0; r < st.rows; r++) for (let c = 0; c < st.cols; c++) if (rows[r][c] === "m") rows[r][c] = "=";
      st.battle.terrain = rows.map(r => r.join(""));
      const pawns = piecesOf(st, "player").filter(p => p.type === "infantry");
      if (pawns[0]) { pawns[0].type = "tank"; pawns[0].entrenched = true; }
      buildBoard();
      return `⛰️ 八十五歲的迦勒老當益壯！希伯崙山地化為坦途，前鋒晉升為重盾方陣！`;
    }
  },
  deborah: {
    id: "deborah", name: "底波拉與巴拉 (Deborah)", title: "棕樹下審判以色列的女士師", ref: "士師記 5:20",
    quote: "「星宿從天上爭戰，從其軌道與西西拉爭戰；基順古河把敵人沖沒！」",
    skillName: "🌟 星宿爭戰基順漲水",
    skillDesc: "基順河暴漲沖沒敵軍鐵車！隨機擊退 1 隊敵方重裝戰車(tank/td)，並為全軍加持護盾。",
    cast(st) {
      BiblicalAudio.playSeaWaves(1.3);
      const foes = piecesOf(st, "ai").filter(p => !PIECE_DEFS[p.type].isKing && PIECE_DEFS[p.type].vehicle);
      if (foes[0]) {
        st.board[foes[0].r][foes[0].c] = null;
        st.captured.player.push(foes[0].type);
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      return `🌟 星宿從軌道爭戰！基順古河暴漲沖沒西西拉的鐵車，全軍士氣大振！`;
    }
  },
  gideon: {
    id: "gideon", name: "基甸 (Gideon)", title: "大能的勇士 · 三百角號破米甸", ref: "士師記 7:20",
    quote: "「耶和華和基甸的刀！」",
    skillName: "🔥 打破瓦瓶舉火把",
    skillDesc: "在基甸周圍空格呼召 2 名「基甸勇士(commando)」加入戰局，並獲得 +2 點信心。",
    cast(st, hero) {
      BiblicalAudio.playShofar();
      let spawned = 0;
      for (const [dr, dc] of [[-1,-1],[-1,1],[1,-1],[1,1],[-1,0],[1,0],[0,-1],[0,1]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc] && canStand(PIECE_DEFS.commando, terrAt(st, nr, nc))) {
          st.board[nr][nc] = { type: "commando", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          if (++spawned >= 2) break;
        }
      }
      st.faith = Math.min(10, (st.faith || 0) + 2);
      return `🔥 三百勇士打破瓦瓶高舉火把！${spawned} 隊基甸勇士響應呼召現身助陣！`;
    }
  },
  jephthah: {
    id: "jephthah", name: "耶弗他 (Jephthah)", title: "基列大能的勇士 · 米斯巴守望士師", ref: "士師記 11:29",
    quote: "「耶和華的靈降在耶弗他身上，他就經過基列和瑪拿西，來到亞捫人那裡。」",
    skillName: "⚔️ 基列米斯巴盟約衝鋒",
    skillDesc: "呼召 1 隊「信德藤牌衛隊(tank)」助陣，並為全軍披戴護盾。",
    cast(st, hero) {
      BiblicalAudio.playShofar();
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc] && canStand(PIECE_DEFS.tank, terrAt(st, nr, nc))) {
          st.board[nr][nc] = { type: "tank", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          break;
        }
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      return `⚔️ 耶和華的靈降在耶弗他身上！基列精兵列陣衝鋒，全軍披戴護盾！`;
    }
  },
  samson: {
    id: "samson", name: "參孫 (Samson)", title: "拿細耳人 · 隱鶴泉力士", ref: "士師記 15:18",
    quote: "「主耶和華啊，求你眷念我！神啊，求你賜我這一次的力量！」",
    skillName: "🏛️ 撼動非利士神廟雙柱",
    skillDesc: "震毀敵方主帥周圍的堅固石牆(t/u)，並直接震退距離參孫最近的一名非王敵軍！",
    cast(st, hero) {
      BiblicalAudio.playShofar();
      const foes = piecesOf(st, "ai").filter(p => !PIECE_DEFS[p.type].isKing)
        .sort((a, b) => (Math.abs(a.r - hero.r) + Math.abs(a.c - hero.c)) - (Math.abs(b.r - hero.r) + Math.abs(b.c - hero.c)));
      if (foes[0]) {
        st.board[foes[0].r][foes[0].c] = null;
        st.captured.player.push(foes[0].type);
      }
      hero.entrenched = true;
      return `🏛️ 耶和華的靈大大感動參孫！一擊粉碎近身強敵並獲得隱鶴泉恩典神聖護盾！`;
    }
  },
  ruth: {
    id: "ruth", name: "路得與波阿斯 (Ruth)", title: "投靠神翅膀下的摩押賢婦", ref: "路得記 1:16",
    quote: "「你的國就是我的國，你的神就是我的神。」",
    skillName: "🌾 伯利恆麥田滿得賞賜",
    skillDesc: "波阿斯吩咐僕人故意留下一把麥穗！全軍獲得護盾並恢復 +4 點信心。",
    cast(st) {
      BiblicalAudio.playHarpChord([349.23, 440, 523.25, 698.46], 0.08);
      st.faith = Math.min(10, st.faith + 4);
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      return `🌾 伯利恆麥田豐收！全體同行者投靠在耶和華以色列神的翅膀下，滿得護盾與信心！`;
    }
  },
  samuel: {
    id: "samuel", name: "撒母耳 (Samuel)", title: "立起以便以謝石的先知與士師", ref: "撒母耳記上 7:12",
    quote: "「到如今耶和華都幫助我們（以便以謝）！」",
    skillName: "🪨 米斯巴雷聲驚亂敵營",
    skillDesc: "撒母耳獻燔祭禱告，耶和華大發雷聲驚亂非利士人！凍結敵軍一回合（連續行動兩回合）！",
    cast(st) {
      BiblicalAudio.playMiracleChime();
      st.extraTurnPending = true;
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      return `🪨 撒母耳立起以便以謝石！耶和華大發雷聲驚亂敵營，我方獲得連續行動兩回合！`;
    }
  },
  jonathan: {
    id: "jonathan", name: "約拿單 (Jonathan)", title: "掃羅長子 · 密抹崖信心勇士", ref: "撒母耳記上 14:6",
    quote: "「或者耶和華為我們施展能力；因為耶和華使人得勝，不在乎人多人少！」",
    skillName: "🧗 密抹雙崖攀岩奇襲",
    skillDesc: "在約拿單身旁呼召 2 名可跨越山崖的「拿細耳勇士(partisan)」，並使全軍披戴護盾。",
    cast(st, hero) {
      BiblicalAudio.playShofar();
      let sp = 0;
      for (const [dr, dc] of [[-1,-1],[-1,1],[0,-1],[0,1],[-1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc] && sp < 2) {
          st.board[nr][nc] = { type: "partisan", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          sp++;
        }
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      return `🧗 約拿單與拿兵器少年人攀上密抹陡崖！非利士防線大亂，奇兵現身助陣！`;
    }
  },
  david: {
    id: "david", name: "大衛 (David)", title: "合神心意的牧者與君王", ref: "撒母耳記上 17:45",
    quote: "「你來攻擊我，是靠著刀槍和銅戟；我來攻擊你，是靠著萬軍之耶和華的名！」",
    skillName: "🪨 以拉谷五顆溪石",
    skillDesc: "直接遠程擊倒棋盤上價值最高的一名敵方非王核心重裝單位（如歌利亞巨戟或重盾）。",
    cast(st) {
      BiblicalAudio.playHarpChord([293.66, 440, 587.33, 880], 0.06);
      const enemies = piecesOf(st, "ai").filter(p => !PIECE_DEFS[p.type].isKing)
        .sort((a, b) => PIECE_DEFS[b.type].value - PIECE_DEFS[a.type].value);
      if (!enemies.length) return "🪨 場上已無敵方巨人目標！";
      const target = enemies[0];
      st.board[target.r][target.c] = null;
      st.captured.player.push(target.type);
      return `🪨 大衛用機弦甩出光滑溪石！在 ${coordName(st, target.r, target.c)} 一擊擊倒敵方最強的「${PIECE_DEFS[target.type].name}」！`;
    }
  },
  solomon: {
    id: "solomon", name: "所羅門王 (Solomon)", title: "建造耶路撒冷第一聖殿的智慧王", ref: "列王紀上 8:11",
    quote: "「甚至祭司不能站立供職，因為耶和華的榮光充滿了殿。」",
    skillName: "☁️ 聖殿獻殿榮雲充滿",
    skillDesc: "榮雲充滿全場！呼召 1 隊「利未讚美詩班(katyusha)」並使全軍披戴護盾、信心 +3。",
    cast(st, hero) {
      BiblicalAudio.playMiracleChime();
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc]) {
          st.board[nr][nc] = { type: "katyusha", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          break;
        }
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      st.faith = Math.min(10, st.faith + 3);
      return `☁️ 所羅門向天舉手祈禱！耶和華的榮雲充滿聖殿，利未詩班吹號助陣！`;
    }
  },
  elijah: {
    id: "elijah", name: "以利亞 (Elijah)", title: "提斯比人 · 迦密山求火先知", ref: "列王紀上 18:38",
    quote: "「耶和華是神！耶和華是神！」",
    skillName: "🔥 迦密山天火降臨",
    skillDesc: "在以利亞前方呼召一隊「雲柱火柱(bomber)」與一隊「多坍火車火馬(armoredtrain)」護衛。",
    cast(st, hero) {
      BiblicalAudio.playMiracleChime();
      const types = ["bomber", "armoredtrain"];
      let idx = 0;
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0],[-1,-1],[-1,1]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc] && idx < types.length) {
          const t = types[idx];
          if (canStand(PIECE_DEFS[t], terrAt(st, nr, nc))) {
            st.board[nr][nc] = { type: t, side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
            idx++;
          }
        }
      }
      return `🔥 耶和華降下天火燒盡燔祭與溝水！雲柱火柱與火車火馬降臨戰場！`;
    }
  },
  elisha: {
    id: "elisha", name: "以利沙 (Elisha)", title: "承接加倍感動的神人先知", ref: "列王紀下 6:17",
    quote: "「不要懼怕！與我們同在的，比與他們同在的更多。」",
    skillName: "🐎 開少年眼見滿山火馬",
    skillDesc: "開眼看見滿山火車火馬圍繞！呼召 1 隊「多坍火車火馬(armoredtrain)」並點亮全場敵軍警戒網。",
    cast(st, hero) {
      BiblicalAudio.playMiracleChime();
      st.showThreat = true;
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc]) {
          st.board[nr][nc] = { type: "armoredtrain", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          break;
        }
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      return `🐎 耶和華開少年人的眼目，見滿山有火車火馬圍繞以利沙！`;
    }
  },
  jehoshaphat: {
    id: "jehoshaphat", name: "約沙法王 (Jehoshaphat)", title: "設立利未詩班讚美退敵的猶大王", ref: "歷代志下 20:21",
    quote: "「當稱謝耶和華，因祂的慈愛永遠長存！」",
    skillName: "🎵 讚美詩班派伏兵退敵",
    skillDesc: "眾人方唱歌讚美時，耶和華派伏兵擊退聯軍！呼召 1 隊「利未讚美詩班(katyusha)」並擊退 1 名敵方前鋒！",
    cast(st, hero) {
      BiblicalAudio.playHarpChord([392, 493.88, 587.33, 783.99], 0.07);
      const foes = piecesOf(st, "ai").filter(p => !PIECE_DEFS[p.type].isKing);
      if (foes[0]) {
        st.board[foes[0].r][foes[0].c] = null;
        st.captured.player.push(foes[0].type);
      }
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc]) {
          st.board[nr][nc] = { type: "katyusha", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          break;
        }
      }
      return `🎵 約沙法設立詩班走在軍前歌頌神！敵軍自相擊殺，利未詩班列陣推進！`;
    }
  },
  hezekiah: {
    id: "hezekiah", name: "希西家王 (Hezekiah)", title: "在聖殿將書信鋪在神面前的猶大王", ref: "列王紀下 19:14",
    quote: "「希西家在耶和華面前展開那信，禱告說：坐在二基路伯上耶和華以色列的神啊，唯有你是天下萬國的神！」",
    skillName: "👼 耶和華使者夜間護城",
    skillDesc: "耶和華的使者夜間出去擊退亞述圍城大軍！直接削弱並擊退 1 名敵方前鋒重裝單位。",
    cast(st) {
      BiblicalAudio.playMiracleChime();
      const foes = piecesOf(st, "ai").filter(p => !PIECE_DEFS[p.type].isKing)
        .sort((a, b) => b.r - a.r);
      if (foes[0]) {
        st.board[foes[0].r][foes[0].c] = null;
        st.captured.player.push(foes[0].type);
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      return `👼 希西家流淚禱告蒙應允！耶和華的使者夜間出營擊退亞述前鋒，保護錫安城！`;
    }
  },
  isaiah: {
    id: "isaiah", name: "先知以賽亞 (Isaiah)", title: "見主高高坐在寶座上的先知", ref: "以賽亞書 6:8",
    quote: "「我又聽見主的聲音說：我可以差遣誰呢？誰肯為我們去呢？我說：我在這裡，請差遣我！」",
    skillName: "🔥 撒拉弗聖壇紅炭潔淨",
    skillDesc: "呼召 1 隊「撒拉弗聖壇炭(kamikaze)」降臨，並賜予全軍護盾。",
    cast(st, hero) {
      BiblicalAudio.playMiracleChime();
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc]) {
          st.board[nr][nc] = { type: "kamikaze", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          break;
        }
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      return `🔥 撒拉弗用火剪從壇上取下紅炭沾以賽亞的口！罪孽除掉，撒拉弗天軍隨行出征！`;
    }
  },
  jeremiah: {
    id: "jeremiah", name: "先知耶利米 (Jeremiah)", title: "流淚的先知 · 賜平安意念的守望者", ref: "耶利米書 29:11",
    quote: "「耶和華說：我知道我向你們所懷的意念是賜平安的意念，不是降災禍的意念，要叫你們末後有指望。」",
    skillName: "📜 巴比倫平安書信盼望",
    skillDesc: "賜予全體被擄百姓恩典神聖護盾，並立即恢復 +4 點信心值。",
    cast(st) {
      BiblicalAudio.playHarpChord([349.23, 440, 523.25, 659.25], 0.08);
      st.faith = Math.min(10, st.faith + 4);
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      return `📜 耶利米寄信安慰巴比倫被擄百姓！全隊重燃末後的指望，獲得護盾與 +4 信心！`;
    }
  },
  ezekiel: {
    id: "ezekiel", name: "先知以西結 (Ezekiel)", title: "迦巴魯河邊見天開異象與枯骨復生的先知", ref: "以西結書 37:10",
    quote: "「氣息就進入骸骨，骸骨便活了，並且站起來，成為極大的軍隊！」",
    skillName: "🌬️ 四方氣息吹入枯骨成軍",
    skillDesc: "從四圍呼召氣息！在場上空格召喚 2 名剛強的「信德藤牌衛隊(tank)」或「基甸勇士(commando)」站起來成為極大軍隊！",
    cast(st, hero) {
      BiblicalAudio.playMiracleChime();
      let sp = 0;
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0],[-1,-1],[-1,1]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc] && sp < 2) {
          const t = sp === 0 ? "tank" : "commando";
          if (canStand(PIECE_DEFS[t], terrAt(st, nr, nc))) {
            st.board[nr][nc] = { type: t, side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
            sp++;
          }
        }
      }
      return `🌬️ 以西結遵命發預言！氣息進入平原枯骨，${sp} 隊大軍站起來披戴護盾投入爭戰！`;
    }
  },
  daniel: {
    id: "daniel", name: "但以理 (Daniel)", title: "一日三次面向耶路撒冷禱告的先知", ref: "但以理書 6:22",
    quote: "「我的神差遣使者，封住獅子的口，叫獅子不傷我！」",
    skillName: "🦁 封住獅口與烈火第四人",
    skillDesc: "神差遣使者封住敵軍攻勢！我方全體獲得恩典神聖護盾，並凍結敵軍一回合（連續行動兩回合）！",
    cast(st) {
      BiblicalAudio.playMiracleChime();
      st.extraTurnPending = true;
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      return `🦁 神差遣使者封住獅子的口！敵軍被震懾無法攻擊，我方獲得連續行動兩回合！`;
    }
  },
  jonah: {
    id: "jonah", name: "先知約拿 (Jonah)", title: "深海魚腹禱告與尼尼微傳道者", ref: "約拿書 2:9",
    quote: "「但我必用感謝的聲音獻祭與你。我所許的願，我必償還。救恩出於耶和華！」",
    skillName: "🐋 大魚吐在旱地傳道",
    skillDesc: "呼召「約拿深海大魚(sub)」助陣，並為全體船隊披戴護盾。",
    cast(st, hero) {
      BiblicalAudio.playSeaWaves(1.4);
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc] && TERRAIN[terrAt(st, nr, nc)]?.water) {
          st.board[nr][nc] = { type: "sub", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          break;
        }
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      return `🐋 救恩出於耶和華！深海大魚聽命護航，全船隊平安蒙保守！`;
    }
  },
  ezra: {
    id: "ezra", name: "文士以斯拉 (Ezra)", title: "立定心志考究遵行耶和華律法的祭司文士", ref: "以斯拉記 7:10",
    quote: "「以斯拉定志考究遵行耶和華的律法，又將律例典章教訓以色列人。」",
    skillName: "📖 水門前宣讀律法書",
    skillDesc: "宣讀律法使百姓大大喜樂！全軍獲得護盾、信心 +3，並將 1 名門徒晉升為「聖靈寶劍真道(td)」！",
    cast(st) {
      BiblicalAudio.playMiracleChime();
      const pawns = piecesOf(st, "player").filter(p => p.type === "infantry");
      if (pawns[0]) { pawns[0].type = "td"; pawns[0].entrenched = true; }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      st.faith = Math.min(10, st.faith + 3);
      return `📖 以斯拉站在木台上宣讀律法書！因靠耶和華而得的喜樂成為百姓的力量！`;
    }
  },
  esther: {
    id: "esther", name: "以斯帖王后 (Esther)", title: "書珊城為本族禁食請命的王后", ref: "以斯帖記 4:14",
    quote: "「焉知妳得了王后的位分，不是為現今的機會嗎？我若死就死吧！」",
    skillName: "👑 金杖伸出轉危為安",
    skillDesc: "亞哈隨魯王向以斯帖伸出金杖！全體猶大百姓披戴恩典神聖護盾，並將 1 名門徒直接晉升為聖靈寶劍！",
    cast(st) {
      BiblicalAudio.playMiracleChime();
      const pawns = piecesOf(st, "player").filter(p => p.type === "infantry");
      if (pawns[0]) { pawns[0].type = "td"; pawns[0].entrenched = true; }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      st.faith = Math.min(10, st.faith + 3);
      return `👑 王向以斯帖伸出金杖！哈曼的計謀敗露，全體百姓轉悲為喜披戴護盾！`;
    }
  },
  nehemiah: {
    id: "nehemiah", name: "尼希米 (Nehemiah)", title: "五十二日重修耶路撒冷城垣的省長", ref: "尼希米記 2:20",
    quote: "「天上的神必使我們亨通。我們作祂僕人的，要起來建造！」",
    skillName: "🧱 一手做工一手拿兵器",
    skillDesc: "將場上的荒涼廢墟(u)修築為堅固守望石牆(t)，並讓全體我方同行者披戴護盾。",
    cast(st) {
      BiblicalAudio.playShofar();
      const rows = st.battle.terrain.map(r => r.split(""));
      for (let r = 0; r < st.rows; r++) for (let c = 0; c < st.cols; c++) {
        if (rows[r][c] === "u") rows[r][c] = "t";
      }
      st.battle.terrain = rows.map(r => r.join(""));
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      buildBoard();
      return `🧱 尼希米率眾起來建造！荒涼城垣重修為守望石牆，全隊披戴堅固神聖護盾！`;
    }
  },
  malachi: {
    id: "malachi", name: "先知瑪拉基 (Malachi)", title: "舊約最後一位預言公義日頭的先知", ref: "瑪拉基書 4:2",
    quote: "「但向你們敬畏我名的人，必有公義的日頭出現，其光線有醫治之能！」",
    skillName: "🌅 公義日頭醫治之光",
    skillDesc: "呼召「雲柱火柱(bomber)」降臨，將場上荊棘(x)化為真光(L)，並賜全軍護盾。",
    cast(st, hero) {
      BiblicalAudio.playMiracleChime();
      const rows = st.battle.terrain.map(r => r.split(""));
      for (let r = 0; r < st.rows; r++) for (let c = 0; c < st.cols; c++) if (rows[r][c] === "x") rows[r][c] = "L";
      st.battle.terrain = rows.map(r => r.join(""));
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc]) {
          st.board[nr][nc] = { type: "bomber", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          break;
        }
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      buildBoard();
      return `🌅 公義的日頭出現，其光線有醫治之能！百姓出來跳躍如圈裡的肥犢！`;
    }
  },
  jesus: {
    id: "jesus", name: "主耶穌基督 (Jesus Christ)", title: "神的兒子 · 道路、真理、生命", ref: "約翰福音 14:6",
    quote: "「我就是道路、真理、生命……在世上你們有苦難，但你們可以放心，我已經勝了世界！」",
    skillName: "✝️ 平靜風浪與復活大能",
    skillDesc: "斥責風浪「住了吧！靜了吧！」清除全場荊棘網羅(x)與暗礁(r)，全體門徒披戴護盾、信心補滿並晉升 1 名門徒！",
    cast(st) {
      BiblicalAudio.playMiracleChime();
      const rows = st.battle.terrain.map(r => r.split(""));
      for (let r = 0; r < st.rows; r++) for (let c = 0; c < st.cols; c++) {
        if (rows[r][c] === "x") rows[r][c] = ".";
        if (rows[r][c] === "r") rows[r][c] = "~";
      }
      st.battle.terrain = rows.map(r => r.join(""));
      const pawns = piecesOf(st, "player").filter(p => p.type === "infantry");
      if (pawns[0]) { pawns[0].type = "td"; pawns[0].entrenched = true; }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      st.faith = 10;
      buildBoard();
      return `✝️ 主耶穌彰顯復活與平靜風浪的大能！全場攔阻化為坦途，門徒剛強得勝、信心滿溢！`;
    }
  },
  johnbaptist: {
    id: "johnbaptist", name: "施洗約翰 (John the Baptist)", title: "曠野的呼聲 · 為主預備道路的先鋒", ref: "約翰福音 1:29",
    quote: "「看哪，神的羔羊，除去世人罪孽的！祂必興旺，我必衰微。」",
    skillName: "🦗 預備主的道修直祂的路",
    skillDesc: "將全場曠野荊棘(x)與荒垣(u)修直為朝聖大道(=)，並呼召 1 名「拿細耳勇士(partisan)」助陣。",
    cast(st, hero) {
      BiblicalAudio.playHarpChord([392, 493.88, 587.33], 0.07);
      const rows = st.battle.terrain.map(r => r.split(""));
      for (let r = 0; r < st.rows; r++) for (let c = 0; c < st.cols; c++) {
        if (rows[r][c] === "x" || rows[r][c] === "u") rows[r][c] = "=";
      }
      st.battle.terrain = rows.map(r => r.join(""));
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc]) {
          st.board[nr][nc] = { type: "partisan", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          break;
        }
      }
      buildBoard();
      return `🦗 曠野人聲喊著說：預備主的道，修直祂的路！一切高低不平處皆化為平坦大道！`;
    }
  },
  peter: {
    id: "peter", name: "使徒彼得 (Apostle Peter)", title: "得人漁夫 · 五旬節教會柱石", ref: "使徒行傳 2:38",
    quote: "「金銀我都沒有，只把我所有的給你：我奉拿撒勒人耶穌基督的名，叫你起來行走！」",
    skillName: "🕊️ 五旬節聖靈充滿",
    skillDesc: "將場上最多 2 名「信心門徒(infantry)」直接就地蒙恩晉升為「信德藤牌衛隊」或「天使信使」！",
    cast(st) {
      BiblicalAudio.playMiracleChime();
      const pawns = piecesOf(st, "player").filter(p => p.type === "infantry");
      let count = 0;
      for (const p of pawns.slice(0, 2)) {
        p.type = canStand(PIECE_DEFS.tank, terrAt(st, p.r, p.c)) ? "tank" : "fighter";
        p.entrenched = true;
        count++;
      }
      st.faith = Math.min(10, (st.faith || 0) + 2);
      return `🕊️ 五旬節聖靈如火舌降臨！${count} 名信心門徒剛強站立，直接晉升為屬靈精兵！`;
    }
  },
  stephen: {
    id: "stephen", name: "司提反 (Stephen)", title: "滿得恩惠能力 · 定睛望天見主榮耀的執事", ref: "使徒行傳 7:55",
    quote: "「但司提反被聖靈充滿，定睛望天，看見神的榮耀，又看見耶穌站在神的右邊！」",
    skillName: "✨ 天開見人子站在神右邊",
    skillDesc: "天門敞開！呼召 1 隊「撒拉弗聖壇炭(kamikaze)」降臨，全軍披戴護盾並獲得 +3 信心。",
    cast(st, hero) {
      BiblicalAudio.playMiracleChime();
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc]) {
          st.board[nr][nc] = { type: "kamikaze", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          break;
        }
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      st.faith = Math.min(10, st.faith + 3);
      return `✨ 司提反面貌好像天使的面貌！天門敞開，榮耀天軍降臨護衛見證人！`;
    }
  },
  philip: {
    id: "philip", name: "傳福音者腓利 (Philip)", title: "迦薩曠野路貼近車走解開以賽亞書的執事", ref: "使徒行傳 8:35",
    quote: "「腓利就開口從這經上起，對他傳講耶穌。」",
    skillName: "💧 曠野活水受洗歡喜",
    skillDesc: "呼召 1 隻「天使信使(fighter)」跨越曠野，並讓全軍披戴恩典神聖護盾、信心 +3。",
    cast(st, hero) {
      BiblicalAudio.playHarpChord([440, 554.37, 659.25, 880], 0.07);
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc]) {
          st.board[nr][nc] = { type: "fighter", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          break;
        }
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      st.faith = Math.min(10, st.faith + 3);
      return `💧 看哪，這裡有水！太監受洗後歡歡喜喜地走路，福音傳遍曠野與外邦！`;
    }
  },
  paul: {
    id: "paul", name: "使徒保羅 (Apostle Paul)", title: "外邦人的使徒 · 真道守望者", ref: "提摩太後書 4:7",
    quote: "「那美好的仗我已經打過了，當跑的路我已經跑盡了，所信的道我已經守住了。」",
    skillName: "⚔️ 神的全副軍裝",
    skillDesc: "在保羅身旁呼召一隊「聖靈寶劍真道(td)」，並讓全體我方單位披戴恩典神聖護盾。",
    cast(st, hero) {
      BiblicalAudio.playMiracleChime();
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0],[-1,-1],[-1,1]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc] && canStand(PIECE_DEFS.td, terrAt(st, nr, nc))) {
          st.board[nr][nc] = { type: "td", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          break;
        }
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      return `⚔️ 保羅宣講以弗所書真道！聖靈寶劍降臨，全隊穿戴神的全副軍裝！`;
    }
  },
  john: {
    id: "john", name: "使徒約翰 (Apostle John)", title: "主所愛的門徒 · 拔摩島啟示先見", ref: "啟示錄 21:4",
    quote: "「神要擦去他們一切的眼淚；不再有死亡，也不再有悲哀、哭號、疼痛。」",
    skillName: "🌈 新耶路撒冷榮光",
    skillDesc: "呼召一隊「撒拉弗聖壇炭(kamikaze)」降臨，並直接獲得 +3 點信心與全軍護盾。",
    cast(st, hero) {
      BiblicalAudio.playMiracleChime();
      for (const [dr, dc] of [[-1,0],[0,-1],[0,1],[1,0]]) {
        const nr = hero.r + dr, nc = hero.c + dc;
        if (inBounds(st, nr, nc) && !st.board[nr][nc]) {
          st.board[nr][nc] = { type: "kamikaze", side: "player", r: nr, c: nc, startR: nr, startC: nc, entrenched: true };
          break;
        }
      }
      for (const p of piecesOf(st, "player")) p.entrenched = true;
      st.faith = Math.min(10, (st.faith || 0) + 3);
      return `🌈 拔摩島天門打開！撒拉弗榮光降臨，信心倍增並全軍披戴恩典神聖護盾！`;
    }
  }
};

/* ============ 4. 聖曆七日創造與安息日律動 + 雲彩見證人最高榮譽徽章 ============ */
const CREATION_DAYS = [
  { day: 1, name: "第一日 · 神說要有光", ref: "創 1:3", desc: "真光普照，視野清明，全場試探警戒一目了然。" },
  { day: 2, name: "第二日 · 諸水之間有空氣", ref: "創 1:6", desc: "天窗敞開，天軍信使與雲柱火柱翱翔無阻。" },
  { day: 3, name: "第三日 · 青草與結果子的樹", ref: "創 1:11", desc: "迦南青草地與橄欖林充滿生機，同行者得享飽足。" },
  { day: 4, name: "第四日 · 光體管理晝夜節令", ref: "創 1:14", desc: "星宿指引方向，夜間守望的代求祭壇大有能力。" },
  { day: 5, name: "第五日 · 水中滋生魚類與飛鳥", ref: "創 1:20", desc: "加利利海與滄海風平浪靜，水路航行蒙受保守。" },
  { day: 6, name: "第六日 · 照神形象造人與託付", ref: "創 1:26", desc: "信心門徒剛強行事，預備迎接明日聖安息日！" },
  { day: 7, name: "🕯️ 第七日 · 聖安息日 (Sabbath)", ref: "創 2:3", desc: "神賜福給第七日定為聖日！全隊自動恢復 +2 信心，且駐守會幕/逃城/築壇處的同行者自動披戴恩典神聖護盾！" }
];

const BIBLICAL_RANKS = [
  { min: 0,   title: "🌱 慕道朝聖行者", badge: "🕯️" },
  { min: 3,   title: "⛺ 會幕守望利未人", badge: "📯" },
  { min: 10,  title: "🛡️ 迦南剛強士師", badge: "⚔️" },
  { min: 25,  title: "👑 大衛詩琴勇士", badge: "🪕" },
  { min: 50,  title: "🔥 先知學校守望者", badge: "📜" },
  { min: 85,  title: "🕊️ 使徒宣教柱石", badge: "⛵" },
  { min: 120, title: "🏛️ 榮耀寶座前的雲彩見證人（全卷 120 篇大圓滿）", badge: "👑" }
];

const BIBLICAL_MEDALS = [
  { id: "m_light",    icon: "✨", name: "起初神創造天地", desc: "在《創世記 1:1》以耶和華（神的靈）分開光暗得勝", check: s => s.wonIds.includes(1) },
  { id: "m_ark",      icon: "🌈", name: "歌斐木彩虹之約", desc: "與挪亞一同完成方舟洪水立約篇章(#3)", check: s => s.wonIds.includes(3) || s.wonIds.length >= 2 },
  { id: "m_redsea",   icon: "🌊", name: "紅海乾地救恩", desc: "擊潰法老鐵車完成《過紅海如行乾地》(#13)", check: s => s.wonIds.includes(13) || s.wonIds.length >= 5 },
  { id: "m_jericho",  icon: "📯", name: "耶利哥七日吹角", desc: "攻克雙層城牆《繞行七日吹角攻克耶利哥》(#22)", check: s => s.miraclesUsed >= 1 || s.wonIds.includes(22) },
  { id: "m_david",    icon: "🪨", name: "以拉谷五顆溪石", desc: "擊倒巨人歌利亞(#38)或累積 10 勝", check: s => s.wonIds.includes(38) || s.wonIds.length >= 10 },
  { id: "m_elijah",   icon: "🔥", name: "迦密山天火見證", desc: "施放任意聖經領袖主動恩賜擊敗巴力先知", check: s => s.heroSkillsUsed >= 1 },
  { id: "m_quiz",     icon: "📖", name: "庇哩亞查考聖經", desc: "在對局中答對至少 3 題庇哩亞經文問答", check: s => (s.quizCorrect || 0) >= 3 },
  { id: "m_galilee",  icon: "⛵", name: "平靜加利利風浪", desc: "與主耶穌一同完成任意四福音神蹟篇章", check: s => s.wonIds.some(id => id >= 61 && id <= 90) },
  { id: "m_paul",     icon: "📜", name: "那美好的仗已經打過", desc: "完成任意使徒行傳或啟示錄篇章", check: s => s.wonIds.some(id => id >= 91) },
  { id: "m_cloud12",  icon: "🏛️", name: "十二支派與十二使徒", desc: "累計完成 12 篇以上聖約棋局", check: s => s.wonIds.length >= 12 },
  { id: "m_ultimate_cloud", icon: "👑", name: "希伯來書的雲彩見證人（大圓滿）", desc: "成功通關第 120 篇《新耶路撒冷》，跑盡當跑的路，守住所信的道！", check: s => s.wonIds.includes(120) }

];
















/* ============ 5. 聖經 120 篇完整目錄 ============ */
// 欄位格式：[篇號, 聖史分期, 經文依憑, 篇名, 希伯來/希臘/拉丁原文或英文譯名, 地圖X, 地圖Y, 勝負體系, 領袖代碼, 聖地氛圍, 聖言金句, 歷史對敵]
const CHAPTER_CATALOG = [
  // 一、摩西五經 · 創世與立約之始 (1-20)
  [1,  "pentateuch", "創世記 1:1-5",     "太初神說要有光與混沌分明", "Fiat Lux",                885, 275, "annihilate", "yahweh",  "theme-bible-cosmos", "神說：「要有光」，就有了光。神看光是好的，就把光暗分開了。", "🌌 淵面黑暗與空虛混沌"],
  [2,  "pentateuch", "創世記 2:8-3:15",  "伊甸聖園修理看守與古蛇試誘","Paradisus Edensis",      895, 285, "defend",     "adam",    "theme-bible-eden",   "耶和華神將那人安置在伊甸園，使他修理，看守。", "🐍 古蛇之詭計與試誘權勢"],
  [3,  "pentateuch", "創世記 6:14-8:1",  "歌斐木方舟與彩虹永約",     "Arca Noe",                868, 72,  "evacuate",   "noah",    "theme-bible-flood",  "我把虹放在雲彩中，這就可作我與地立約的記號了。", "🌊 裂開之深淵大洪水"],
  [4,  "pentateuch", "創世記 12:1-8",    "亞伯蘭蒙召出迦勒底吾珥",   "Vocatio Abrahami",        892, 302, "breakthrough","abraham","theme-bible-canaan", "你要離開本地、本族、父家，往我所要指示你的地去。", "🗿 迦勒底吾珥月神偶像營壘"],
  [5,  "pentateuch", "創世記 14:14-20",  "亞伯蘭率家丁夜襲救羅得",   "Liberatio Lot",           662, 290, "annihilate", "abraham", "theme-bible-canaan", "至高的神把敵人交在你手裡，是應當稱頌的！", "👑 基大老瑪四王聯軍"],
  [6,  "pentateuch", "創世記 22:1-14",   "摩利亞山獻祭與耶和華以勒", "Jehovah-Jireh",           645, 348, "capture",    "abraham", "theme-bible-jerusalem","在耶和華的山上必有預備。", "🔥 摩利亞山順服大試驗"],
  [7,  "pentateuch", "創世記 28:10-22",  "伯特利天梯與天使往來",     "Scala Jacob",             648, 338, "capture",    "jacob",   "theme-bible-canaan", "這不是別的，乃是神的殿，也是天的門。", "🌑 路斯荒野之孤寂與驚懼"],
  [8,  "pentateuch", "創世記 32:22-30",  "雅博渡口毗努伊勒較力之福", "Lucta ad Jabbok",         665, 335, "defend",     "jacob",   "theme-bible-canaan", "你的名不要再叫雅各，要叫以色列；因為你與神與人較力，都得了勝。", "⚔️ 西珥地四百壯丁前鋒"],
  [9,  "pentateuch", "創世記 41:38-57",  "約瑟宰相治理埃及七豐年",   "Josephus Gubernator",     522, 392, "defend",     "joseph",  "theme-bible-egypt",  "神的意思原是好的，要保全許多人的性命。", "🥀 席捲全地之七年大饑荒"],
  [10, "pentateuch", "出埃及記 2:1-10",  "尼羅河蘆葦蒲草箱之拯救",   "Moyses in Flumine",       532, 382, "evacuate",   "moses",   "theme-bible-egypt",  "她給孩子起名叫摩西，意思說：因我把他從水裡拉出來。", "🐊 尼羅河法老巡察水軍"],
  [11, "pentateuch", "出埃及記 3:1-14",  "何烈山荊棘烈焰神聖召命",   "Rubus Ardens",            582, 462, "capture",    "moses",   "theme-bible-sinai",  "我是自有永有的。當把你腳上的鞋脫下來，因為你所站之地是聖地。", "🏜️ 米甸曠野督工哨網"],
  [12, "pentateuch", "出埃及記 12:1-28", "逾越節羔羊之血立約門楣",   "Primus Pascha",           535, 395, "defend",     "moses",   "theme-bible-egypt",  "我一見這血，就越過你們去，災殃必不臨到你們身上。", "👑 歌珊埃及心硬之法老"],
  [13, "pentateuch", "出埃及記 14:15-31","伸杖分紅海巨浸如行乾地",   "Transitus Maris Rubri",   565, 422, "breakthrough","moses",  "theme-bible-redsea", "摩西向海伸杖，耶和華便用大東風，使海水一夜退去，水便分開。", "🛞 法老特選六百鐵車精銳"],
  [14, "pentateuch", "出埃及記 16:11-35","汛曠野天降嗎哪與以琳泉",   "Manna de Caelo",          575, 442, "defend",     "moses",   "theme-bible-sinai",  "這就是耶和華給你們吃的食物。", "🌵 汛曠野之困乏與怨言試探"],
  [15, "pentateuch", "出埃及記 17:8-16", "利非訂山巔舉手亞倫戶珥扶翼","Victoria in Rephidim",   580, 452, "annihilate", "moses",   "theme-bible-sinai",  "摩西何時舉手，以色列人就得勝；亞倫與戶珥扶著他的手。", "🗡️ 亞瑪力劫掠首領大軍"],
  [16, "pentateuch", "出埃及記 19-20章", "西乃聖山十誡法版與盟約",   "Lex in Monte Sinai",      588, 468, "capture",    "moses",   "theme-bible-sinai",  "如今你們若實在聽從我的話，遵守我的約，就要在萬民中作屬我的子民。", "🐂 山下拜金牛犢悖逆營壘"],
  [17, "pentateuch", "出埃及記 40:1-38", "至聖會幕立起與耶和華榮光", "Tabernaculum Gloriae",    592, 455, "defend",     "moses",   "theme-bible-sinai",  "當時雲彩遮蓋會幕，耶和華的榮光就充滿了帳幕。", "🌪️ 西乃大荒漠狂風與外敵"],
  [18, "pentateuch", "民數記 13:17-33",  "迦勒專一跟從窺探迦南應許", "Exploratio Chanaan",      638, 368, "capture",    "caleb",   "theme-bible-canaan", "我們立刻上去得那地吧！我們足能得勝。", "🗿 希伯崙亞衲族偉人後裔"],
  [19, "pentateuch", "民數記 21:4-9",    "曠野仰望高舉銅蛇瞻仰存活", "Serpens Aeneus",         618, 412, "defend",     "moses",   "theme-bible-sinai",  "凡被咬的，一望這銅蛇，就活了。", "🐍 以東邊境之火蛇肆虐"],
  [20, "pentateuch", "申命記 34:1-9",    "尼波山巔遙望美地權柄交付", "Conspectus de Monte Nebo",665, 355, "capture",    "joshua",  "theme-bible-canaan", "嫩的兒子約書亞，因為摩西曾按手在他頭上，就被智慧的靈充滿。", "👑 亞摩利王西宏與巴珊王噩"],

  // 二、迦南征服與士師秉政 (21-35)
  [21, "joshua", "約書亞記 3:14-17", "抬約櫃踏約旦河水立起成壘", "Transitus Jordanis",      656, 342, "breakthrough","joshua",  "theme-bible-redsea", "抬約櫃的祭司腳一入水，那從上往下流的水便停住立起成壘。", "🌊 漲滿兩岸之約旦河激流"],
  [22, "joshua", "約書亞記 6:1-20",  "圍城七日吹號呼喊耶利哥塌陷","Moenia Hierichuntis",    651, 345, "capture",    "joshua",  "theme-bible-canaan", "百姓聽見角聲，便大聲呼喊，城牆就塌陷，百姓便上去進城。", "🧱 耶利哥堅固雙層城防守軍"],
  [23, "joshua", "約書亞記 8:1-29",  "艾城誘敵西側伏兵短槍大捷", "Insidiae ad Ai",          647, 342, "annihilate", "joshua",  "theme-bible-canaan", "約書亞伸手中的短槍指著城，伏兵就從原處急忙起來奪城。", "👑 艾城王追擊軍之合圍"],
  [24, "joshua", "約書亞記 10:12-14","亞雅崙谷日頭停留基遍止息", "Sol in Gibeon",          644, 346, "annihilate", "joshua",  "theme-bible-canaan", "日頭啊，你要停在基遍！月亮啊，你要止在亞雅崙谷！", "👑 亞摩利五王聯軍大陣"],
  [25, "joshua", "約書亞記 11:1-15", "米倫水邊突襲北方鐵車聯軍", "Aquae Merom",            655, 298, "annihilate", "joshua",  "theme-bible-canaan", "明日我必將他們交付以色列人；你要砍斷他們馬的蹄筋，用火焚燒他們的車輛。", "🛞 夏瑣王耶賓北方戰車大軍"],
  [26, "joshua", "約書亞記 14:6-14", "八十五歲迦勒得希伯崙山地", "Hereditas Caleb",         644, 362, "capture",    "caleb",   "theme-bible-canaan", "求你將耶和華那日應許我的這山地給我！", "🗿 亞衲族三巨子之盤踞要塞"],
  [27, "joshua", "約書亞記 24:14-27","示劍大橡樹下立石至於我和我家","Foedus in Sichem",      649, 328, "defend",     "joshua",  "theme-bible-canaan", "至於我和我家，我們必定事奉耶和華。", "🗿 迦南殘餘偶像風俗之惑"],
  [28, "joshua", "士師記 4:4-23",    "底波拉與巴拉他泊山俯衝大捷","Victoria Deborae",       652, 315, "annihilate", "deborah", "theme-bible-canaan", "今日就是耶和華將西西拉交在你手的日子。耶和華豈不在你前頭行嗎？", "🛞 西西拉九百輛鐵車精銳"],
  [29, "joshua", "士師記 5:19-21",   "星宿軌道爭戰基順古河暴漲", "Torrens Cison",          642, 312, "annihilate", "deborah", "theme-bible-canaan", "星宿從天上爭戰，從其軌道與西西拉爭戰；基順古河把敵人沖沒。", "⚔️ 夏羅設外邦鐵車主力"],
  [30, "joshua", "士師記 6:11-24",   "俄弗拉酒醡旁耶和華沙龍顯現","Jehovah-Shalom",         648, 324, "defend",     "gideon",  "theme-bible-canaan", "大能的勇士啊，耶和華與你同在！", "🐪 米甸亞瑪力掠地駱駝軍"],
  [31, "joshua", "士師記 7:1-22",    "基甸三百勇士角號火把夜襲", "Trecenti Viri Gedeonis",  652, 320, "annihilate", "gideon",  "theme-bible-canaan", "三百人就吹角，打破瓶子，左手拿著火把，右手拿著角，喊叫說：耶和華和基甸的刀！", "👑 米甸二王十三萬聯軍大營"],
  [32, "joshua", "士師記 11:29-33",  "耶弗他基列米斯巴破亞捫人", "Victoria Jephthae",      665, 330, "defend",     "jephthah","theme-bible-canaan", "耶和華的靈降在耶弗他身上。", "⚔️ 犯界侵伐之亞捫聯軍"],
  [33, "joshua", "士師記 15:14-19",  "參孫利希隱鶴泉湧流得力",   "Fons En-Hakkore",         636, 352, "annihilate", "samson",  "theme-bible-canaan", "神就使利希的窪處裂開，有水從其中湧出來，參孫喝了精神復原。", "🛡️ 非利士千人精甲部隊"],
  [34, "joshua", "路得記 2:1-16",    "伯利恆麥田拾穗與至近親恩典","Ager Boaz",              645, 353, "defend",     "ruth",    "theme-bible-canaan", "你來投靠耶和華以色列神的翅膀下，願你滿得祂的賞賜。", "🥀 士師荒年之窘迫與窮乏"],
  [35, "joshua", "撒母耳記上 7:7-12","米斯巴雷聲震散仇敵立以便以謝","Lapis Auxilii",        642, 344, "capture",    "samuel",  "theme-bible-canaan", "到如今耶和華都幫助我們（以便以謝）！", "⚔️ 犯境進擊之非利士全軍"],

  // 三、大衛王朝與王國興衰 (36-50)
  [36, "kingdom", "撒母耳記上 14:6-15","約拿單攀密抹隘口憑信克敵", "Jonathan in Michmash",  648, 344, "annihilate", "jonathan","theme-bible-canaan", "因為耶和華使人得勝，不在乎人多人少。", "🛡️ 密抹隘口非利士防線重營"],
  [37, "kingdom", "撒母耳記上 16:1-13","伯利恆受膏牧童大衛內心鑒察","Unctio Davidis",       646, 354, "defend",     "david",   "theme-bible-canaan", "耶和華不像人看人：人是看外貌；耶和華是看內心。", "🦁 曠野吞噬羊群之猛獅惡熊"],
  [38, "kingdom", "撒母耳記上 17:38-51","以拉谷五顆溪石機弦破歌利亞","David et Goliath",     638, 351, "annihilate", "david",   "theme-bible-canaan", "爭戰的勝敗全在乎耶和華。祂必將你們交在我們手裡。", "🗡️ 迦特巨人歌利亞與重裝持盾者"],
  [39, "kingdom", "撒母耳記上 22:1-5", "亞杜蘭洞窮乏困迫四百勇士", "Spelunca Adullam",       639, 355, "defend",     "david",   "theme-bible-canaan", "凡受窘迫的、欠債的、心裡苦惱的都聚集到大衛那裡；大衛就作他們的頭目。", "⚔️ 掃羅三千搜捕精卒"],
  [40, "kingdom", "撒母耳記上 24:1-15","隱基底野羊磐石深洞存憐憫", "Refugium En-Gedi",      651, 365, "defend",     "david",   "theme-bible-canaan", "願耶和華在你我中間判斷，斷定是非，並且救我脫離你的手。", "👑 荒野逼索之王廷鐵衛"],
  [41, "kingdom", "撒母耳記下 5:6-10", "攻取錫安堅壘定名大衛之城", "Arx Zion",               646, 348, "capture",    "david",   "theme-bible-jerusalem","大衛日見強盛，因為耶和華萬軍之神與他同在。", "🧱 耶布斯人錫安山高牆要塞"],
  [42, "kingdom", "撒母耳記下 6:12-19","歡呼吹號迎約櫃入耶路撒冷", "Adventus Arcae",         645, 349, "evacuate",   "david",   "theme-bible-jerusalem","大衛和以色列的全家歡呼吹角，將耶和華的約櫃抬上來。", "⚔️ 利乏音谷攔截之非利士重兵"],
  [43, "kingdom", "列王紀上 8:1-21",   "所羅門聖殿奉獻榮雲充溢聖所","Templum Salomonis",     647, 348, "defend",     "solomon", "theme-bible-jerusalem","祭司從聖所出來的時候，有雲充滿耶和華的殿。", "🌑 周遭列國窺伺與離棄真道之勢"],
  [44, "kingdom", "列王紀上 17:1-16",  "基立溪烏鴉供養與撒勒法罈麵","Torrens Cherith",       658, 336, "defend",     "elijah",  "theme-bible-canaan", "罈內的麵必不減少，瓶裡的油必不缺短，直到耶和華使雨降在地上的日子。", "☀️ 三年六月遍地枯竭之旱災"],
  [45, "kingdom", "列王紀上 18:20-39", "迦密山天火降臨焚燒燔祭溝水","Ignis in Carmelo",      638, 310, "annihilate", "elijah",  "theme-bible-sinai",  "耶和華是神！耶和華是神！", "🐂 巴力亞舍拉四百五十假先知"],
  [46, "kingdom", "列王紀上 19:8-18",  "何烈山洞微小聲音與七千義士","Vox Tenuis",            588, 466, "defend",     "elijah",  "theme-bible-sinai",  "火後有微小安靜的聲音……我在以色列人中為自己留下七千人。", "👑 耶洗別追索性命之通緝令"],
  [47, "kingdom", "列王紀下 2:1-14",   "約旦河外旋風火車乘風升天", "Currus Igneus",          656, 344, "breakthrough","elisha",  "theme-bible-redsea", "忽有火車火馬將二人隔開，以利亞就乘旋風升天去了。", "🌊 阻斷去路之湍急約旦河"],
  [48, "kingdom", "列王紀下 6:8-23",   "多坍滿山火車火馬護衛先知", "Montes Igniti Dothan",   647, 322, "defend",     "elisha",  "theme-bible-canaan", "不要懼怕！與我們同在的，比與他們同在的更多。", "🐎 圍困多坍之亞蘭王車騎大軍"],
  [49, "kingdom", "歷代志下 20:1-25",  "約沙法王聖殿伏地詩班讚美破敵","Cantores Josaphat",    648, 358, "annihilate", "jehoshaphat","theme-bible-jerusalem","眾人方唱歌讚美的時候，耶和華就派伏兵擊殺敵軍。", "⚔️ 摩押亞捫西珥山三國聯軍"],
  [50, "kingdom", "列王紀下 19:14-35", "希西家展書禱告使者夜滅亞述","Oratio Ezechiae",       646, 349, "defend",     "hezekiah","theme-bible-jerusalem","耶和華的使者出去，在亞述營中殺了十八萬五千人。", "👑 亞述王西拿基立十八萬大軍"],

  // 四、先知默示與被擄歸回 (51-60)
  [51, "prophets", "以賽亞書 6:1-8",   "至高寶座撒拉弗紅炭沾唇蒙差","Sanctus et Carbo",      646, 347, "capture",    "isaiah",  "theme-bible-jerusalem","我在這裡，請差遣我！", "🌑 嘴唇不潔與蒙脂油之暗世"],
  [52, "prophets", "耶利米書 29:10-14","迦巴魯河畔向被擄民賜平安意念","Consilia Pacis",       892, 292, "defend",     "jeremiah","theme-bible-egypt",  "我知道我向你們所懷的意念是賜平安的意念，不是降災禍的意念，要叫你們末後有指望。", "🏛️ 巴比倫假先知與絕望泥淖"],
  [53, "prophets", "以西結書 37:1-14", "平原枯骨遵命預言氣息成大軍","Vallis Ossium Aridorum",888, 282, "annihilate", "ezekiel", "theme-bible-canaan", "氣息就進入骸骨，骸骨便活了，並且站起來，成為極大的軍隊。", "💀 死蔭幽谷極其乾枯之骨骸"],
  [54, "prophets", "但以理書 3:16-28", "杜拉平原烈火窯中神子同行", "Fornax Ignis Ardentis",  895, 296, "defend",     "daniel",  "theme-bible-sinai",  "看哪，我見有四個人，並沒有捆綁，在火中遊行，第四個的相貌好像神子。", "🔥 尼布甲尼撒王七倍烈火窯"],
  [55, "prophets", "但以理書 6:10-23", "但以理三時向殿祈禱封住獅口","Daniel in Lacu Leonum", 898, 298, "defend",     "daniel",  "theme-bible-jerusalem","我的神差遣使者，封住獅子的口，叫獅子不傷我。", "🦁 瑪代波斯奸佞禁令與飢獅"],
  [56, "prophets", "約拿書 1-3章",     "深淵大魚魚腹禱告救恩出於耶和華","Jonas in Profundo",    875, 198, "evacuate",   "jonah",   "theme-bible-flood",  "救恩出於耶和華！", "🌪️ 他施航道洶湧狂風巨濤"],
  [57, "prophets", "以斯拉記 1-3章",   "古列諭旨重返聖城立原有祭壇","Reditus et Altare",     646, 348, "capture",    "ezra",    "theme-bible-jerusalem","他們彼此唱和，讚美稱謝耶和華說：祂本為善，祂向以色列人永發慈愛！", "🪨 阻撓修造之河西敵對勢力"],
  [58, "prophets", "以斯帖記 4:13-17", "書珊王宮死就死吧現今之機會","Esther pro Populo",     935, 345, "defend",     "esther",  "theme-bible-jerusalem","焉知妳得了王后的位分，不是為現今的機會嗎？", "🗡️ 亞甲族哈曼之滅族諭旨"],
  [59, "prophets", "尼希米記 4:6-23",  "五十二日修垣一手作工一手兵器","Aedificantes Portas",  645, 350, "defend",     "nehemiah","theme-bible-jerusalem","修造城牆的，扛抬材料的，都一手做工，一手拿兵器。", "⚔️ 參巴拉多比雅擾害同盟"],
  [60, "prophets", "瑪拉基書 4:1-6",   "公義日頭興起光線有醫治之能","Sol Justitiae",         647, 351, "capture",    "malachi", "theme-bible-jerusalem","但向你們敬畏我名的人，必有公義的日頭出現，其光線有醫治之能。", "🌑 兩約間四百年沉寂暗夜"],

  // 五、四福音書 · 救恩成就 (61-90)
  [61, "gospels", "路加福音 2:8-20",   "伯利恆客店晨星顯現天軍讚美", "Nativitas Domini",       645, 354, "capture",    "jesus",       "theme-bible-cosmos",   "在至高之處榮耀歸與神！在地上平安歸與祂所喜悅的人！", "👑 希律王與暗夜封鎖"],
  [62, "gospels", "馬太福音 2:1-12",   "東方博士隨星朝拜開寶盒奉獻", "Adoratio Magorum",      646, 355, "evacuate",   "jesus",       "theme-bible-jerusalem","他們看見那星，就大大地歡喜。", "🗡️ 希律王之追查暗哨"],
  [63, "gospels", "馬太福音 3:1-17",   "約旦河受洗天開聖靈如鴿降臨", "Baptisma Christi",      656, 343, "capture",    "johnbaptist", "theme-bible-redsea",   "這是我的愛子，我所喜悅的。", "🐍 毒蛇種類假善傳統"],
  [64, "gospels", "馬太福音 4:1-11",   "猶太曠野禁食四十日勝三試探", "Tentatio in Deserto",   651, 348, "annihilate", "jesus",       "theme-bible-sinai",    "經上記著說：人活著，不是單靠食物，乃是靠神口裡所出的一切話。", "🏜️ 曠野試誘者撒但"],
  [65, "gospels", "路加福音 5:1-11",   "革尼撒勒湖水深之處撒網得人", "Duc in Altum",          655, 312, "capture",    "jesus",       "theme-bible-galilee",  "不要怕！從今以後，你要得人了。", "🌊 整夜勞碌空無之水"],
  [66, "gospels", "約翰福音 2:1-11",   "迦拿婚筵六口石缸水變上好酒", "Nuptiae in Cana",       648, 314, "capture",    "jesus",       "theme-bible-galilee",  "這是耶穌所行的頭一件神蹟，顯出祂的榮耀來。", "🏺 婚筵酒竭窘迫疑惑"],
  [67, "gospels", "馬太福音 5:1-16",   "八福山寶訓造在山上的城發光", "Sermo in Monte",        654, 308, "defend",     "jesus",       "theme-bible-galilee",  "你們是世上的光。城造在山上是不能隱藏的。", "🌑 斗底幽暗世俗風潮"],
  [68, "gospels", "馬可福音 2:1-12",   "迦百農拆通房頂縋下癱子得赦", "Sanatio Paralytici",   656, 307, "capture",    "jesus",       "theme-bible-galilee",  "我吩咐你，起來！拿你的褥子回家去吧。", "📜 議論褻瀆之文士階層"],
  [69, "gospels", "馬可福音 4:35-41",  "斥責狂風怒濤「住了吧靜了吧」","Ventus et Mare",       657, 313, "evacuate",   "jesus",       "theme-bible-galilee",  "住了吧！靜了吧！風就止住，大大地平靜了。", "🌪️ 加利利忽起之暴浪"],
  [70, "gospels", "馬可福音 5:1-20",   "格拉森岸邊釋放被群鬼附著者", "Liberatio Gerasenorum", 661, 314, "annihilate", "jesus",       "theme-bible-galilee",  "將主為你所做的是何等大的事，是怎樣憐憫你，都告訴他們。", "⛓️ 格拉森墳塋群鬼營壘"],
  [71, "gospels", "路加福音 7:1-10",   "迦百農百夫長「只要說一句話」","Fides Centurionis",    655, 307, "capture",    "jesus",       "theme-bible-galilee",  "這麼大的信心，就是在以色列中，我也沒有遇見過。", "🤒 瀕死重疾陰霾權勢"],
  [72, "gospels", "路加福音 7:11-17",  "拿因城門按棺「少年人請起來」","Resurrectio Naim",     649, 317, "defend",     "jesus",       "theme-bible-canaan",   "少年人，我吩咐你，起來！那死人就坐起，並且說話。", "⚰️ 死亡絕望哀哭權勢"],
  [73, "gospels", "馬太福音 14:13-21", "伯賽大青草野地五餅二魚飽飫", "Quinque Panes",        658, 306, "defend",     "jesus",       "theme-bible-galilee",  "他們都吃，並且吃飽了；把剩下的零碎收拾起來，裝滿了十二個籃子。", "🏜️ 野地五千人之飢匱"],
  [74, "gospels", "馬太福音 14:22-33", "四更天踏浪而行伸手援救彼得", "Ambulatio super Mare",  656, 311, "breakthrough","jesus",      "theme-bible-galilee",  "你們放心！是我，不要怕！", "🌊 逆風駭浪小信驚慌"],
  [75, "gospels", "約翰福音 4:5-42",   "撒瑪利亞敘加雅各井旁談活水", "Puteus Jacob",          649, 329, "capture",    "jesus",       "theme-bible-canaan",   "人若喝我所賜的水就永遠不渴；我所賜的水要在他裡頭成為泉源，直湧到永生。", "🏺 午正乾渴成見隔閡"],
  [76, "gospels", "馬太福音 16:13-20", "該撒利亞腓立比認信磐石教會", "Confessio Petri",      658, 292, "defend",     "peter",       "theme-bible-canaan",   "你是基督，是永生神的兒子……我要把我的教會建造在這磐石上。", "⛩️ 陰間權柄敵擋之門"],
  [77, "gospels", "馬太福音 17:1-9",   "黑門高山變像面容如日摩西顯", "Transfiguratio Domini", 660, 288, "capture",    "jesus",       "theme-bible-cosmos",   "臉面明亮如日頭，衣裳潔白如光。", "🌫️ 山下不信愁煩世代"],
  [78, "gospels", "路加福音 10:1-20",  "差遣七十門徒雙人成行踐蛇蠍", "Missio Septuaginta",   650, 335, "breakthrough","jesus",      "theme-bible-canaan",   "要收的莊稼多，做工的人少。所以我差你們去，如同羊羔進入狼群。", "🦂 蛇蠍仇敵一切能力"],
  [79, "gospels", "路加福音 10:25-37", "耶利哥下坡路慈憫撒瑪利亞人", "Bonus Samaritanus",    650, 346, "evacuate",   "jesus",       "theme-bible-canaan",   "你去照樣行吧。", "🗡️ 荒徑強盜劫掠伏兵"],
  [80, "gospels", "約翰福音 9:1-38",   "西羅亞池洗眼生來瞎眼見光明", "Piscina Siloam",       646, 350, "capture",    "jesus",       "theme-bible-jerusalem","有一件事我知道，從前我是眼瞎的，如今能看見了。", "🌑 逐出會堂宗教恐嚇"],
  [81, "gospels", "約翰福音 10:11-18", "好牧人捨命作門領羊進出得草", "Bonus Pastor",         644, 352, "defend",     "jesus",       "theme-bible-canaan",   "我是好牧人；好牧人為羊捨命。", "🐺 吞噬殺戮之盜賊豺狼"],
  [82, "gospels", "約翰福音 11:1-44",  "伯大尼墓洞大呼「拉撒路出來」","Resurrectio Lazari",   648, 349, "capture",    "jesus",       "theme-bible-jerusalem","復活在我，生命也在我。信我的人雖然死了，也必復活！", "🪨 死亡封石四日幽暗"],
  [83, "gospels", "路加福音 19:1-10",  "耶利哥桑樹撒該就位救恩臨門", "Zacchaeus in Hiericho", 652, 345, "capture",    "jesus",       "theme-bible-canaan",   "人子來，為要尋找、拯救失喪的人。", "💰 貪婪盤剝私下譏誚"],
  [84, "gospels", "馬太福音 21:1-11",  "棕樹主日騎驢入聖城和散那呼", "Ingressus Hierosolymam",646,348,"breakthrough","jesus",      "theme-bible-jerusalem","和散那歸於大衛的子孫！奉主名來的是應當稱頌的！", "🏛️ 偽善宗教賊窩權勢"],
  [85, "gospels", "約翰福音 13:1-17",  "馬可樓束腰洗腳彼此相愛新約", "Mandatum Novum",       645, 349, "defend",     "jesus",       "theme-bible-passion",  "我賜給你們一條新命令，乃是叫你們彼此相愛。", "🌑 爭大驕傲賣主黑夜"],
  [86, "gospels", "馬太福音 26:36-46", "客西馬尼園儆醒祈禱順服天父", "Agonia in Gethsemane",  647, 348, "defend",     "jesus",       "theme-bible-passion",  "不要照我的意思，只要照你的意思。", "⚔️ 刀棒火把捉拿之差役"],
  [87, "gospels", "約翰福音 19:17-30", "各各他山十架「成了」裂聖殿幔","Consummatum Est",      646, 347, "defend",     "jesus",       "theme-bible-passion",  "成了！便低下頭，將靈魂交付神了。", "🌑 午正遍地黑暗罪權"],
  [88, "gospels", "馬太福音 28:1-10",  "七日清晨大地震天使報主復活", "Resurrectio Domini",   646, 348, "annihilate", "jesus",       "theme-bible-newjerusalem","祂不在這裡，照祂所說的，已經復活了！", "🛡️ 羅馬印封兵丁死鉤"],
  [89, "gospels", "路加福音 24:13-35", "以馬忤斯路上解經擘餅心火熱", "In Via Emmaus",        641, 347, "breakthrough","jesus",      "theme-bible-canaan",   "在路上祂和我們說話，給我們講解聖經的時候，我們的心豈不是火熱的嗎？", "🌫️ 愁煩迷糊疑惑陰霾"],
  [90, "gospels", "約翰福音 21:1-19",  "提比哩亞海晨炭託付「餵我羊」","Pascite Oves Meas",    656, 312, "capture",    "jesus",       "theme-bible-galilee",  "主啊，是的，你知道我愛你。耶穌說：你餵養我的小羊。", "🌊 悔痛退後網羅創傷"],

  // 六、使徒行傳與新天新地 (91-120)
  [91,  "acts", "使徒行傳 1:6-11",   "橄欖山升天應許直到地極作見證", "Ascensio Domini",      647, 348, "capture",    "peter",  "theme-bible-jerusalem","但聖靈降臨在你們身上，你們就必得著能力，並要直到地極，作我的見證。", "🏛️ 列邦幽暗未聞道壁"],
  [92,  "acts", "使徒行傳 2:1-41",   "五旬節聖靈如大風烈火三千歸主", "Dies Pentecostes",    646, 349, "annihilate", "peter",  "theme-bible-jerusalem","從天上有響聲下來，好像一陣大風吹過，充滿了他們所坐的屋子。", "🗣️ 語言隔閡譏誚阻擾"],
  [93,  "acts", "使徒行傳 3:1-10",   "聖殿美門口奉拿撒勒人名命行走", "Porta Speciosa",       647, 349, "capture",    "peter",  "theme-bible-jerusalem","金銀我都沒有，只把我所有的給你：我奉拿撒勒人耶穌基督的名，叫你起來行走！", "⛓️ 生來瘸腿四旬無力"],
  [94,  "acts", "使徒行傳 4:23-31",  "同心合意高聲祈禱聚會處大震動", "Oratio Apostolorum",   645, 348, "defend",     "peter",  "theme-bible-jerusalem","禱告完了，聚會的地方震動，他們就都被聖靈充滿，放膽講論神的道。", "⚖️ 公會恐嚇嚴禁之令"],
  [95,  "acts", "使徒行傳 7:54-60",  "司提反望天見榮耀面如天使殉道", "Stephanus Protomartyr", 646, 347, "defend",     "stephen","theme-bible-passion",  "我看見天開了，人子站在神的右邊！", "🪨 咬牙切齒頑石之害"],
  [96,  "acts", "使徒行傳 8:26-40",  "下迦薩曠野路腓利向太監解經水禮","Philippus et Eunuchus", 632, 362, "breakthrough","philip", "theme-bible-egypt",    "看哪，這裡有水，我受洗有什麼妨礙呢？", "🏜️ 曠野孤寂經文迷思"],
  [97,  "acts", "使徒行傳 9:1-22",   "大馬士革路天上大光照耀揀選器皿","Conversio Pauli",      685, 272, "capture",    "paul",   "theme-bible-mission",  "他是我所揀選的器皿，要在外邦人和君王並以色列人面前宣揚我的名。", "⚔️ 搜捕信徒城門暗伏"],
  [98,  "acts", "使徒行傳 10:1-48",  "約帕海邊房頂大布異象臨哥尼流家","Visio Joppen",         636, 336, "capture",    "peter",  "theme-bible-mission",  "神已經賜恩給外邦人，叫他們悔改得生命了！", "🧱 族類偏見隔斷高牆"],
  [99,  "acts", "使徒行傳 11:19-26", "敘利亞安提阿門徒首稱基督徒母港","Ecclesia Antiochena",  672, 208, "defend",     "paul",   "theme-bible-mission",  "門徒稱為「基督徒」是從安提阿起首。", "🏛️ 異邦城郭風俗同化"],
  [100, "acts", "使徒行傳 12:5-17",  "教會切切代禱天使引彼得夜出鐵門","Petrus de Carcere",    646, 348, "evacuate",   "peter",  "theme-bible-passion",  "彼得卻被囚在監裡；教會卻為他切切地禱告神。", "⛓️ 希律兵丁兩條鐵鍊"],
  [101, "acts", "使徒行傳 13:1-12",  "禁食差派首航居比路帕弗斥術士", "Navigatio Cypria",     548, 218, "breakthrough","paul",  "theme-bible-mission",  "要為我分派巴拿巴和掃羅，去做我召他們所做的工。", "🧙 敵擋真道術士以呂馬"],
  [102, "acts", "使徒行傳 14:1-23",  "以哥念路司得遭損進城堅固門徒", "Lystra et Derbe",      535, 162, "defend",     "paul",   "theme-bible-mission",  "我們進入神的國，必須經歷許多艱難。", "🪨 煽惑眾人石擊敵對"],
  [103, "acts", "使徒行傳 15:1-31",  "耶路撒冷會議辨明真道不加重擔", "Concilium Hierosolymam",646, 349, "defend",     "peter",  "theme-bible-jerusalem","因為聖靈和我們定意不將別的重擔放在你們身上。", "📜 律法轄制擾亂異端"],
  [104, "acts", "使徒行傳 16:6-10",  "特羅亞夜間馬其頓異象呼聲西渡", "Vocatio Macedonica",   402, 122, "breakthrough","paul",  "theme-bible-mission",  "請你過到馬其頓來幫助我們！", "🌊 愛琴風暴未辟荒途"],
  [105, "acts", "使徒行傳 16:16-34", "腓立比內監半夜頌禱地動囚鎖落", "Hymni in Carcere",     342, 88,  "annihilate", "paul",   "theme-bible-mission",  "當信主耶穌，你和你一家都必得救！", "⛓️ 內監木狗嚴酷囚禁"],
  [106, "acts", "使徒行傳 17:1-15",  "庇哩亞賢明甘心領受天天考查聖經","Nobiliores Beroeenses",322, 108, "defend",     "paul",   "theme-bible-mission",  "這地方的人賢於帖撒羅尼迦的人，甘心領受這道，天天考查聖經。", "🔥 浮浪匪類聚眾嫉妒"],
  [107, "acts", "使徒行傳 17:16-34", "雅典亞略巴古宣告創造宇宙真神", "Areopagus Atheniensis", 332, 178, "capture",    "paul",   "theme-bible-mission",  "我們生活、動作、存留，都在乎祂。", "🏛️ 滿城偶像虛妄哲士"],
  [108, "acts", "使徒行傳 18:1-11",  "哥林多夜得主諭「此城百姓甚多」","Corinthus Fidelis",   312, 185, "defend",     "paul",   "theme-bible-mission",  "不要怕，只管講，不要閉口，有我與你同在，因為在這城裡我有許多百姓。", "⚖️ 訟庭刁難同夥攻擊"],
  [109, "acts", "使徒行傳 19:1-20",  "推喇奴學房真道大興焚燒巫術卷", "Schola Tyranni",       422, 165, "annihilate", "paul",   "theme-bible-mission",  "主的道大大興旺，而且得勝，就是這樣。", "🏛️ 銀匠合夥偶像狂號"],
  [110, "acts", "使徒行傳 20:17-38", "米利都海灘訣別行完路程施比受福","Litus Mileti",         426, 176, "defend",     "paul",   "theme-bible-mission",  "我卻不以性命為念，也不看為寶貴，只要行完我的路程，成就我所受的職事。", "🐺 殘害群羊兇暴豺狼"],
  [111, "acts", "使徒行傳 27:13-44", "地中海十四日暗夜天使保全眾命", "Euroaquilo et Naufragium",245,235,"evacuate",  "paul",   "theme-bible-flood",    "現在我還勸你們放心，因為你們眾人，一個也不失喪。", "🌪️ 友拉革羅滔天狂浪"],
  [112, "acts", "使徒行傳 28:1-31",  "米利大甩蛇入火抵羅馬放膽傳神國","Malta ad Romam",      72,  82,  "breakthrough","paul",  "theme-bible-mission",  "放膽傳講神國的道，將主耶穌基督的事教導人，並沒有人禁止。", "🐍 柴火毒蛇御營鐐銬"],
  [113, "acts", "羅馬書 8:31-39",    "誰能隔絕基督的愛靠主得勝有餘", "Superatores per Christum",75, 86,  "annihilate", "paul",   "theme-bible-mission",  "然而，靠著愛我們的主，在這一切的事上已經得勝有餘了。", "⚔️ 患難困苦飢餒刀劍"],
  [114, "acts", "以弗所書 6:10-18",  "穿戴全副軍裝信德藤牌滅惡者火箭","Panoplia Dei",        424, 166, "defend",     "paul",   "theme-bible-mission",  "要穿戴神所賜的全副軍裝，就能抵擋魔鬼的詭計……成就了一切，還能站立得穩。", "🏹 幽暗管轄惡魔火箭"],
  [115, "acts", "希伯來書 11-12章",  "雲彩見證人圍繞仰望信心創始者", "Nubes Testium",        646, 348, "breakthrough","paul",  "theme-bible-jerusalem","我們既有這許多的見證人，如同雲彩圍著我們，就當放下各樣的重擔，存心忍耐。", "⛓️ 纏累罪孽沉重阻擾"],
  [116, "acts", "啟示錄 1-3章",      "拔摩海島見七金燈台榮耀首先末後","Septem Candelabra",    404, 174, "capture",    "john",   "theme-bible-cosmos",   "不要懼怕！我是首先的，我是末後的，又是那存活的；我曾死過，現在又活了。", "🌑 起初愛心冷卻危機"],
  [117, "acts", "啟示錄 4-5章",      "寶座前碧玉如水晶玻璃海配啟書卷","Thronus et Mare Vitreum",406,172,"defend",   "john",   "theme-bible-newjerusalem","曾被殺的羔羊是配得權柄、豐富、智慧、能力、尊貴、榮耀、頌讚的！", "📜 七印封嚴歷史奧秘"],
  [118, "acts", "啟示錄 7:9-17",     "萬國白衣棕樹大群眾羔羊親牧養", "Turba Magna in Albis", 402, 176, "defend",     "john",   "theme-bible-newjerusalem","因為寶座中的羔羊必牧養他們，領他們到生命水的泉源；神也必擦去他們一切的眼淚。", "🌪️ 大患難傷地害海風"],
  [119, "acts", "啟示錄 12:7-11",    "米迦勒摔下古蛇大龍羔羊寶血獲勝","Michael et Draco",    405, 175, "annihilate", "john",   "theme-bible-newjerusalem","弟兄勝過牠，是因羔羊的血和自己所見證的道；他們雖至於死，也不愛惜性命。", "🐉 晝夜控告弟兄大龍"],
  [120, "acts", "啟示錄 21-22章",    "聖城新耶路撒冷天降同住生命河流", "Hierusalem Nova",     646, 348, "annihilate", "john",   "theme-bible-newjerusalem","看哪，神的帳幕在人間！祂要與人同住，他們要作祂的子民。神要親自與他們同在，作他們的神。", "💀 最後仇敵死亡陰間"]
];



/* ============ 5B. 120 關地圖資料庫（第 1 篇至第 60 篇） ============ */
const HANDCRAFTED_120 = {
  // ---------------- 一、摩西五經 (1-20) ----------------
  1: {
    fName: "🌌 太初深淵運行陣（空虛混沌與真光分明）",
    t: ["vv~BB~vv", "v~vvvv~v", "~~vvvv~~", "~vv~~vv~", "~vvLLvv~", "~~L~~L~~", "v~LLLL~v", "vv~HH~vv"],
    p: [P("hq",7,3,"yahweh"), P("bomber",6,2), P("bomber",6,5), P("kamikaze",5,2), P("fighter",5,5), P("fighter",6,3), P("fighter",6,4)],
    a: [P("hq",0,4), P("kamikaze",1,1), P("kamikaze",1,6), P("bomber",0,2), P("fighter",2,1), P("fighter",2,6), P("sub",3,3)]
  },
  2: {
    fName: "🌳 伊甸四河守望陣（基訓比遜諸水環護聖園）",
    t: ["ff.BB.ff", "f~x..x~f", ".~f..f~.", "~~~fa~~~", ".~faaf~.", "f~....~f", "ff.HH.ff", "~~~..~~~"],
    p: [P("hq",6,3,"adam"), P("td",6,4), P("kamikaze",5,2), P("commando",5,5), P("mortar",4,3), P("infantry",5,3), P("infantry",5,4)],
    a: [P("hq",0,4), P("td",1,2), P("commando",1,5), P("partisan",2,1), P("partisan",2,6), P("infantry",2,3), P("infantry",2,4)]
  },
  3: {
    fName: "🌈 亞拉臘山遠航陣（汪洋深淵與彩虹永約彼岸）",
    t: ["bbppppbb", "~~r~~r~~", "~~~mm~~~", "~r~~~~r~", "~~~~r~~~", "~~r~~~~r", "~~~~~~~~", "~~bHHb~~"],
    p: [P("flagship",7,3,"noah"), P("transport",7,4), P("transport",7,2), P("battleship",6,2), P("carrier",6,5), P("cruiser",6,3), P("destroyer",6,4)],
    a: [P("flagship",0,4), P("battleship",1,2), P("cruiser",1,5), P("destroyer",2,1), P("destroyer",2,6), P("sub",3,2), P("sub",3,5)]
  },
  4: {
    fName: "🐪 迦勒底出吾珥陣（跨越兩河荒漠進駐應許）",
    t: ["mm.BB.mm", "m~dddd~m", ".~d..d~.", "..u..u..", "..s..s..", "d.a..a.d", "d.mmmm.d", "dd.HH.dd"],
    p: [P("hq",7,3,"abraham"), P("td",6,1), P("tank",6,6), P("commando",5,2), P("commando",5,5), P("infantry",4,3), P("infantry",4,4)],
    a: [P("hq",0,4), P("tank",1,2), P("tank",1,5), P("artillery",2,2), P("artillery",2,5), P("infantry",2,3), P("infantry",2,4)]
  },
  5: {
    fName: "⚔️ 但地破敵奇襲陣（三百精壯分隊夜擊四王）",
    t: ["mm.BB.mm", "m.cccc.m", "m.tuut.m", "..d..d..", "f......f", "fm.aa.mf", "f......f", "mm.HH.mm"],
    p: [P("hq",7,3,"abraham"), P("commando",4,1), P("commando",4,6), P("partisan",5,1), P("partisan",5,6), P("td",6,2), P("tank",6,5), P("infantry",6,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,2), P("tank",1,5), P("artillery",1,4), P("commando",2,1), P("commando",2,6)]
  },
  6: {
    fName: "🔥 摩利亞山獻祭陣（仰望耶和華以勒之聖山）",
    t: ["mm.BB.mm", "m.mFFm.m", "m.faaf.m", "..mmmm..", "..l..l..", "m.l..l.m", "mm....mm", "mm.HH.mm"],
    p: [P("hq",7,3,"abraham"), P("mortar",6,2), P("mortar",6,5), P("engineer",5,2), P("commando",5,5), P("td",6,3), P("infantry",5,3)],
    a: [P("hq",0,4), P("artillery",1,1), P("artillery",1,6), P("commando",2,2), P("commando",2,5), P("infantry",2,3), P("infantry",2,4)]
  },
  7: {
    fName: "🪜 伯特利枕石啟示陣（曠野夜空天梯與使者升降）",
    t: ["dd.BB.dd", "d.mFFm.d", "d.xLLx.d", "..mLLm..", "..aLLa..", "d.s..s.d", "dd....dd", "dd.HH.dd"],
    p: [P("hq",7,3,"jacob"), P("kamikaze",6,2), P("fighter",6,5), P("bomber",7,2), P("commando",5,2), P("commando",5,5), P("infantry",6,3)],
    a: [P("hq",0,4), P("tank",1,1), P("tank",1,6), P("artillery",2,1), P("artillery",2,6), P("commando",3,2), P("commando",3,5)]
  },
  8: {
    fName: "🌊 雅博渡口較力陣（毗努伊勒黎明見神面得福）",
    t: ["mm.BB.mm", "m.dddd.m", "..d..d..", "~~b~~b~~", "~~~bb~~~", "..a..a..", "m.s..s.m", "mm.HH.mm"],
    p: [P("hq",7,3,"jacob"), P("td",6,2), P("tank",6,5), P("commando",5,3), P("commando",5,4), P("mortar",6,3), P("infantry",5,1)],
    a: [P("hq",0,4), P("td",1,2), P("tank",1,5), P("commando",2,2), P("commando",2,5), P("artillery",1,3), P("infantry",2,3)]
  },
  9: {
    fName: "🌾 埃及七個豐年貯糧陣（積蓄城郭抗禦大饑荒）",
    t: ["dd.BB.dd", "d.uuuu.d", "~..xx..~", "~c.aa.c~", "~c.hh.c~", "~......~", "cc.HH.cc", "~~cccc~~"],
    p: [P("hq",6,3,"joseph"), P("engineer",5,2), P("engineer",5,5), P("td",6,2), P("tank",6,5), P("mortar",4,3), P("infantry",5,3)],
    a: [P("hq",0,4), P("tank",1,1), P("tank",1,6), P("artillery",1,2), P("artillery",1,5), P("commando",2,2), P("commando",2,5)]
  },
  10: {
    fName: "🐊 尼羅河蒲草箱護送陣（穿行茂密蘆葦水道）",
    t: ["ppbbbbpp", "r~~rr~~r", "~~r~~r~~", "~r~~~~r~", "~~~~r~~~", "r~~r~~~r", "~r~~~~r~", "ppbHHbpp"],
    p: [P("flagship",7,3,"moses"), P("mtb",6,2), P("mtb",6,5), P("transport",7,2), P("transport",7,4), P("carrier",6,3), P("cruiser",6,4)],
    a: [P("flagship",0,4), P("battleship",1,2), P("destroyer",1,5), P("cruiser",2,1), P("cruiser",2,6), P("sub",3,3), P("mtb",3,4)]
  },
  11: {
    fName: "🔥 何烈山荊棘烈焰陣（脫鞋受命面謁自有永有者）",
    t: ["mm.BB.mm", "m.xFFx.m", "m.xLLx.m", "d..aa..d", "d.x..x.d", "m......m", "mm.mm.mm", "mm.HH.mm"],
    p: [P("hq",7,3,"moses"), P("kamikaze",6,1), P("engineer",5,2), P("engineer",5,5), P("partisan",6,6), P("mortar",5,3), P("infantry",5,4)],
    a: [P("hq",0,4), P("tank",1,1), P("tank",1,6), P("commando",2,1), P("commando",2,6), P("artillery",0,3), P("infantry",3,2)]
  },
  12: {
    fName: "🩸 歌珊地逾越節塗血陣（羔羊寶血遮蓋長子免禍）",
    t: ["ccBBBBcc", "c.t..t.c", "..u..u..", "h.c..c.h", "h..aa..h", "..h..h..", "c.hHHh.c", "cccccccc"],
    p: [P("hq",6,3,"moses"), P("td",6,1), P("tank",6,6), P("katyusha",5,2), P("katyusha",5,5), P("mortar",4,3), P("infantry",5,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2)]
  },
  13: {
    fName: "🌊 紅海神蹟分水行乾地陣（大東風立水為牆驅退鐵車）",
    t: ["~bbFFbb~", "~~~bb~~~", "~~rbb~~~", "~~~bbr~~", "~~rbb~~~", "~~~bb~~~", "~~bbbb~~", "d.bHHb.d"],
    p: [P("hq",7,3,"moses"), P("bomber",7,4), P("td",6,2), P("tank",6,5), P("katyusha",6,3), P("artillery",6,4), P("commando",5,3), P("infantry",5,4)],
    a: [P("hq",0,4), P("armoredtrain",0,2), P("armoredtrain",0,5), P("tank",1,3), P("tank",1,4), P("commando",2,3), P("infantry",2,4)]
  },
  14: {
    fName: "🌴 汛曠野嗎哪與以琳泉陣（七十株棕樹水泉止息怨言）",
    t: ["dd.BB.dd", "d.x..x.d", "s..ss..s", "ds.aa.sd", "d.s..s.d", "s..dd..s", "dd.HH.dd", "dddddddd"],
    p: [P("hq",6,3,"moses"), P("transport",6,4), P("td",5,2), P("tank",5,5), P("mortar",4,2), P("mortar",4,5), P("infantry",5,3)],
    a: [P("hq",0,4), P("tank",1,1), P("tank",1,6), P("commando",2,2), P("commando",2,5), P("artillery",1,3), P("infantry",2,3)]
  },
  15: {
    fName: "🙌 利非訂高舉神杖代求陣（亞倫戶珥扶持直至日落大捷）",
    t: ["dd.BB.dd", "d.t..t.d", "d......d", "..d..d..", "m..aa..m", "mm.mm.mm", "m.dHHd.m", "mmmmmmmm"],
    p: [P("hq",6,3,"moses"), P("mortar",4,3), P("mortar",4,4), P("td",5,1), P("tank",5,6), P("commando",4,1), P("commando",4,6)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("commando",2,2), P("commando",2,5), P("artillery",0,2)]
  },
  16: {
    fName: "⚡ 西乃聖山立約頒法陣（密雲雷轟受誡與砸碎金牛犢）",
    t: ["mm.BB.mm", "mw.FF.wm", "m.mmmm.m", "..a..a..", "..u..u..", "d.x..x.d", "d......d", "dd.HH.dd"],
    p: [P("hq",7,3,"moses"), P("kamikaze",6,2), P("bomber",6,5), P("partisan",5,2), P("partisan",5,5), P("mortar",5,3), P("engineer",5,4)],
    a: [P("hq",0,4), P("tank",1,2), P("tank",1,5), P("artillery",0,2), P("artillery",0,5), P("commando",3,1), P("commando",3,6)]
  },
  17: {
    fName: "⛺ 曠野十二支派拱衛會幕陣（按纛安營與雲彩覆庇）",
    t: ["dd.BB.dd", "d.u..u.d", "..t..t..", "d.aHHa.d", "d.hHHh.d", "..t..t..", "d.s..s.d", "dddddddd"],
    p: [P("hq",4,3,"moses"), P("katyusha",3,2), P("katyusha",3,5), P("td",4,1), P("tank",4,6), P("commando",2,3), P("commando",2,4), P("mortar",5,3)],
    a: [P("hq",0,4), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",6,1), P("commando",6,6)]
  },
  18: {
    fName: "🍇 以實各谷窺探應許陣（信者不懼高牆偉人）",
    t: ["mm.BB.mm", "m.cFFc.m", "f.m..m.f", "f.m..m.f", "..f..f..", "d.a..a.d", "d......d", "dd.HH.dd"],
    p: [P("hq",7,3,"caleb"), P("partisan",5,1), P("partisan",5,6), P("commando",6,2), P("commando",6,5), P("td",6,3), P("tank",6,4)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",2,2), P("artillery",2,5), P("infantry",3,3)]
  },
  19: {
    fName: "🐍 尋曠野高舉銅蛇瞻仰陣（仰望信從即脫火蛇劇毒）",
    t: ["dd.BB.dd", "d.x..x.d", "x..xx..x", "d.xLLx.d", "d..aa..d", "x.d..d.x", "d......d", "dd.HH.dd"],
    p: [P("hq",7,3,"moses"), P("engineer",5,2), P("engineer",5,5), P("partisan",6,1), P("partisan",6,6), P("kamikaze",6,3), P("mortar",6,4)],
    a: [P("hq",0,4), P("commando",1,2), P("commando",1,5), P("partisan",2,1), P("partisan",2,6), P("artillery",0,3)]
  },
  20: {
    fName: "🏔️ 毗斯迦山巔交接權柄陣（遙望流奶與蜜之福地）",
    t: ["cc.BB.cc", "~.F==F.~", "~..==..~", "b.t==t.b", "m..aa..m", "mw....wm", "ww.mm.ww", "ww.HH.ww"],
    p: [P("hq",7,3,"joshua"), P("td",6,2), P("tank",6,5), P("bomber",7,4), P("commando",5,2), P("commando",5,5), P("katyusha",5,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2)]
  },

  // ---------------- 二、迦南征服與士師秉政 (21-35) ----------------
  21: {
    fName: "🌊 約旦河漲溢立起吉甲立石陣（祭司抬約櫃踏水止流）",
    t: ["cc.FF.cc", "b..cc..b", "~~~bb~~~", "~~rbb~~~", "~~~bbr~~", "~~~bb~~~", "b..aa..b", "dd.HH.dd"],
    p: [P("hq",7,3,"joshua"), P("katyusha",6,2), P("katyusha",6,5), P("td",6,3), P("tank",6,4), P("commando",5,3), P("commando",5,4)],
    a: [P("hq",0,4), P("td",1,2), P("tank",1,5), P("battleship",3,1), P("destroyer",4,6), P("artillery",1,3), P("infantry",2,3)]
  },
  22: {
    fName: "📯 繞城七日羊角吹響耶利哥塌陷陣（堅固雙重城牆應聲崩折）",
    t: ["m.tttt.m", ".tuFFut.", ".tuBBut.", ".tuuuut.", ".tttttt.", "..a..a..", "........", "..lHHl.."],
    p: [P("hq",7,3,"joshua"), P("katyusha",7,4), P("katyusha",7,2), P("td",6,2), P("tank",6,5), P("commando",5,1), P("commando",5,6), P("engineer",6,3)],
    a: [P("hq",2,3), P("td",2,4), P("tank",1,2), P("tank",1,5), P("artillery",2,2), P("artillery",2,5), P("infantry",3,3)]
  },
  23: {
    fName: "🗡️ 艾城伸矛伏兵合擊大捷陣（西側設伏火焚堅城）",
    t: ["mm.BB.mm", "m.cuuc.m", "f.t..t.f", "f..dd..f", "m......m", "m.d..d.m", "..a..a..", "dd.HH.dd"],
    p: [P("hq",7,3,"joshua"), P("commando",2,0), P("commando",3,0), P("partisan",2,7), P("td",6,2), P("tank",6,5), P("artillery",6,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",2,3), P("tank",2,4), P("commando",3,2), P("commando",3,5), P("artillery",1,2)]
  },
  24: {
    fName: "☀️ 伯和崙下坡路日頭停留大追擊陣（天降大冰雹擊潰五王）",
    t: ["mm.BB.mm", "m.d==d.m", "..m==m..", "L..==..L", "L.a==a.L", "..m..m..", "m......m", "mm.HH.mm"],
    p: [P("hq",7,3,"joshua"), P("bomber",6,1), P("td",6,3), P("tank",6,4), P("katyusha",6,6), P("commando",5,2), P("commando",5,5)],
    a: [P("hq",0,4), P("td",1,2), P("tank",1,5), P("tank",2,1), P("tank",2,6), P("artillery",0,3), P("commando",2,3)]
  },
  25: {
    fName: "🐎 米倫水邊焚車斷蹄奇襲陣（夏瑣北方龐大車陣瓦解）",
    t: ["cc.BB.cc", "c~bbbb~c", "~~r..r~~", "~~~..~~~", "b..tt..b", "b.a..a.b", "........", "mm.HH.mm"],
    p: [P("hq",7,3,"joshua"), P("td",6,2), P("tank",6,5), P("commando",5,1), P("commando",5,6), P("katyusha",6,3), P("artillery",6,4)],
    a: [P("hq",0,4), P("armoredtrain",1,2), P("armoredtrain",1,5), P("tank",1,3), P("tank",1,4), P("commando",2,2), P("commando",2,5)]
  },
  26: {
    fName: "⛰️ 希伯崙基列亞巴攻克三巨子陣（八十五載壯志克取山地）",
    t: ["mm.BB.mm", "m.mFFm.m", "mm.tt.mm", "m..mm..m", "..m..m..", "m.a..a.m", "m......m", "mm.HH.mm"],
    p: [P("hq",7,3,"caleb"), P("partisan",5,1), P("partisan",5,6), P("commando",6,2), P("commando",6,5), P("mortar",6,3), P("engineer",6,4)],
    a: [P("hq",0,4), P("td",1,3), P("tank",2,2), P("tank",2,5), P("artillery",0,2), P("artillery",0,5), P("commando",3,1)]
  },
  27: {
    fName: "🪨 示劍大橡樹下石前矢志陣（除絕外邦假神立定家規）",
    t: ["mm.BB.mm", "m.u..u.m", "m..cc..m", "f.t..t.f", "f.a..a.f", "m......m", "mc.HH.cm", "mmmmmmmm"],
    p: [P("hq",6,3,"joshua"), P("td",5,2), P("tank",5,5), P("katyusha",6,2), P("katyusha",6,5), P("mortar",4,3), P("mortar",4,4)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",2,2), P("artillery",2,5), P("commando",3,1)]
  },
  28: {
    fName: "🌴 他泊山俯衝破西西拉鐵車陣（女先知底波拉督戰巴拉）",
    t: ["cc.BB.cc", "g.t..t.g", "gg....gg", "~g.gg.g~", "..m..m..", "m.maam.m", "mm....mm", "mm.HH.mm"],
    p: [P("hq",7,3,"deborah"), P("commando",4,1), P("commando",4,6), P("partisan",5,2), P("partisan",5,5), P("td",6,2), P("tank",6,5)],
    a: [P("hq",0,4), P("armoredtrain",1,2), P("armoredtrain",1,5), P("tank",2,2), P("tank",2,5), P("artillery",0,3), P("infantry",2,3)]
  },
  29: {
    fName: "🌊 基順河激流星宿軌道爭戰陣（泥濘阻滯鐵車古河沖敵）",
    t: ["bb.BB.bb", "~g.cc.g~", "~~g..g~~", "~~~bb~~~", "~~g..g~~", "~g.aa.g~", "b......b", "bb.HH.bb"],
    p: [P("hq",7,3,"deborah"), P("bomber",6,1), P("fighter",6,6), P("td",6,2), P("tank",6,5), P("commando",5,2), P("commando",5,5)],
    a: [P("hq",0,4), P("armoredtrain",1,3), P("tank",1,2), P("tank",1,5), P("artillery",0,2), P("artillery",0,5), P("commando",2,2)]
  },
  30: {
    fName: "🌾 俄弗拉酒醡耶和華沙龍顯現陣（橡樹下受印平息驚恐）",
    t: ["dd.BB.dd", "d.x..x.d", "d..uu..d", "f.t..t.f", "f..aa..f", "..h..h..", "f.hHHh.f", "ffffffff"],
    p: [P("hq",6,3,"gideon"), P("commando",5,1), P("commando",5,6), P("td",5,2), P("tank",5,5), P("mortar",4,3), P("engineer",4,4)],
    a: [P("hq",0,4), P("commando",1,1), P("commando",1,6), P("tank",1,3), P("tank",1,4), P("artillery",2,2), P("artillery",2,5)]
  },
  31: {
    fName: "🔥 哈律泉旁三百精兵碎瓶破敵陣（耶和華和基甸的刀）",
    t: ["m..BB..m", "m.cccc.m", "f.txxt.f", "..g..g..", "........", ".m.aa.m.", ".f....f.", "..sHHs.."],
    p: [P("hq",7,3,"gideon"), P("commando",4,0), P("commando",4,7), P("commando",5,3), P("partisan",5,4), P("td",6,2), P("katyusha",6,5)],
    a: [P("hq",0,4), P("td",0,3), P("tank",1,2), P("tank",1,5), P("artillery",1,3), P("artillery",1,4), P("commando",2,1)]
  },
  32: {
    fName: "🛡️ 基列米斯巴登高平定亞捫陣（重誓許主奮戰拓境）",
    t: ["dd.BB.dd", "d.c..c.d", "m.t..t.m", "mm....mm", "..m..m..", "m.a..a.m", "m.cHHc.m", "mmmmmmmm"],
    p: [P("hq",6,3,"jephthah"), P("td",5,2), P("tank",5,5), P("commando",4,1), P("commando",4,6), P("mortar",5,3), P("mortar",5,4)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2)]
  },
  33: {
    fName: "🦴 利希山窪驢腮骨掃千軍陣（呼求破裂湧泉復原）",
    t: ["cc.BB.cc", "d.t..t.d", "d.u..u.d", "m......m", "m.s~~s.m", "d..aa..d", "d......d", "dd.HH.dd"],
    p: [P("hq",7,3,"samson"), P("td",5,3), P("td",5,4), P("commando",6,1), P("commando",6,6), P("partisan",5,1), P("partisan",5,6)],
    a: [P("hq",0,4), P("tank",1,2), P("tank",1,5), P("tank",2,2), P("tank",2,5), P("artillery",1,3), P("artillery",1,4)]
  },
  34: {
    fName: "🌾 伯利恆麥田庇蔭蒙福陣（波阿斯留穗恩澤賢德婦）",
    t: ["dd.BB.dd", "f.u..u.f", "f......f", "..f..f..", "=.a..a.=", "=..hh..=", "f.hHHh.f", "ffffffff"],
    p: [P("hq",6,3,"ruth"), P("transport",6,4), P("td",5,2), P("tank",5,5), P("mortar",4,2), P("engineer",4,5), P("fighter",6,1)],
    a: [P("hq",0,4), P("tank",1,2), P("tank",1,5), P("commando",2,1), P("commando",2,6), P("artillery",0,3), P("infantry",2,3)]
  },
  35: {
    fName: "🪨 米斯巴大發雷聲立以便以謝陣（到如今耶和華都幫助我們）",
    t: ["cc.BB.cc", "c.tFFt.c", "m..uu..m", "m......m", "..m..m..", "..a..a..", "c......c", "cc.HH.cc"],
    p: [P("hq",7,3,"samuel"), P("katyusha",6,2), P("katyusha",6,5), P("td",6,3), P("tank",6,4), P("commando",5,1), P("commando",5,6)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2)]
  },

  // ---------------- 三、大衛王朝與王國興衰 (36-50) ----------------
  36: {
    fName: "🧗 密抹隘口雙尖峰攀巖大捷陣（非在乎人多人少之信）",
    t: ["cc.BB.cc", "m.t..t.m", "mm.dd.mm", "m.m..m.m", "m.m..m.m", "..a..a..", "m......m", "mm.HH.mm"],
    p: [P("hq",7,3,"jonathan"), P("partisan",5,1), P("partisan",5,6), P("commando",6,2), P("commando",6,5), P("td",6,3), P("tank",6,4)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,2), P("tank",1,5), P("artillery",0,2), P("artillery",0,5), P("commando",2,3)]
  },
  37: {
    fName: "🐑 伯利恆草場牧童搏殺猛獸陣（受膏者忠心護群之操練）",
    t: ["mm.BB.mm", "f.x..x.f", "f......f", "..f..f..", "..s~~s..", "f.a..a.f", "f.hHHh.f", "ffffffff"],
    p: [P("hq",6,3,"david"), P("artillery",5,2), P("artillery",5,5), P("td",6,1), P("tank",6,6), P("commando",4,2), P("commando",4,5)],
    a: [P("hq",0,4), P("commando",1,1), P("commando",1,6), P("partisan",2,2), P("partisan",2,5), P("tank",1,3), P("infantry",2,3)]
  },
  38: {
    fName: "🪨 以拉谷機弦甩石擊倒歌利亞陣（倚靠萬軍耶和華之名得勝）",
    t: ["mm.BB.mm", "m.cccc.m", "m..tt..m", "~~~bb~~~", "~~bbbb~~", "m..aa..m", "m......m", "mm.HH.mm"],
    p: [P("hq",7,3,"david"), P("artillery",5,2), P("artillery",5,5), P("td",6,2), P("tank",6,5), P("commando",6,1), P("commando",6,6)],
    a: [P("hq",0,4), P("td",2,3), P("tank",2,4), P("tank",1,2), P("tank",1,5), P("artillery",1,3), P("artillery",1,4)]
  },
  39: {
    fName: "⛰️ 亞杜蘭巖穴聚眾操練剛強陣（患難貧困中立國之基石）",
    t: ["cc.BB.cc", "c.d..d.c", "..t..t..", "m..uu..m", "mm.aa.mm", "m.mHHm.m", "m......m", "mmmmmmmm"],
    p: [P("hq",5,3,"david"), P("commando",4,1), P("commando",4,6), P("partisan",5,1), P("partisan",5,6), P("td",6,2), P("tank",6,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2)]
  },
  40: {
    fName: "🦌 隱基底野羊磐石割裾存恤陣（不伸手加害耶和華受膏者）",
    t: ["dd.BB.dd", "m.d..d.m", "m..mm..m", "~s.tt.s~", "~s.aa.s~", "m......m", "mm.HH.mm", "~~~mm~~~"],
    p: [P("hq",6,3,"david"), P("commando",5,1), P("commando",5,6), P("td",5,2), P("tank",5,5), P("artillery",6,2), P("mortar",6,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,2), P("tank",1,5), P("commando",2,1), P("commando",2,6), P("artillery",0,3)]
  },
  41: {
    fName: "🏰 水道奇襲克取錫安保障陣（定名大衛之城建基立業）",
    t: ["mm.BB.mm", "mc.FF.cm", "c.tttt.c", "c.~..~.c", "..~..~..", "..b..b..", "..a..a..", "cc.HH.cc"],
    p: [P("hq",7,3,"david"), P("commando",5,2), P("commando",5,5), P("partisan",6,1), P("partisan",6,6), P("td",6,3), P("tank",6,4)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,2), P("tank",1,5), P("artillery",0,2), P("artillery",0,5), P("infantry",2,3)]
  },
  42: {
    fName: "🎺 吹號歡呼迎約櫃入錫安陣（聖樂歌詠大衛踴躍起舞）",
    t: ["ccppppcc", "c.c==c.c", "..t==t..", "f..==..f", "f.a==a.f", "..l==l..", "c.lHHl.c", "cccccccc"],
    p: [P("hq",6,3,"david"), P("transport",6,4), P("transport",5,4), P("katyusha",5,2), P("katyusha",5,5), P("td",6,2), P("tank",6,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",2,1), P("artillery",2,6), P("commando",3,2)]
  },
  43: {
    fName: "☁️ 所羅門聖殿獻殿榮雲充溢陣（萬民禱告天降大榮耀）",
    t: ["cc.BB.cc", "c.t..t.c", "c.i~~i.c", "=.c..c.=", "=.a..a.=", "c.hHHh.c", "c.iiii.c", "cccccccc"],
    p: [P("hq",5,3,"solomon"), P("katyusha",4,2), P("katyusha",4,5), P("td",5,1), P("tank",5,6), P("bomber",6,2), P("fighter",6,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2)]
  },
  44: {
    fName: "🦅 基立溪畔烏鴉供養與撒勒法陣（罈麵瓶油永不斷絕之信）",
    t: ["dd.BB.dd", "d.x..x.d", "d.u..u.d", "~~~bb~~~", "d..aa..d", "d.h..h.d", "c.hHHh.c", "cccccccc"],
    p: [P("hq",6,3,"elijah"), P("fighter",5,1), P("fighter",5,6), P("transport",6,4), P("td",5,2), P("tank",5,5), P("mortar",4,3)],
    a: [P("hq",0,4), P("tank",1,2), P("tank",1,5), P("commando",2,2), P("commando",2,5), P("artillery",1,3), P("infantry",2,3)]
  },
  45: {
    fName: "🔥 迦密山巔築壇倒水天火降臨陣（彰顯唯獨耶和華是真神）",
    t: ["~~.BB.~~", "~g.cc.g~", ".g.uu.g.", "m..aa..m", "mm.aa.mm", "m......m", ".f....f.", "..mHHm.."],
    p: [P("hq",4,3,"elijah"), P("kamikaze",5,3), P("bomber",5,4), P("mortar",5,2), P("mortar",5,5), P("td",6,2), P("tank",6,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,4), P("artillery",2,1), P("artillery",2,6), P("mortar",2,3), P("mortar",2,4)]
  },
  46: {
    fName: "🌬️ 何烈山洞微小聲音安撫陣（烈風崩山地震之後靜聽主語）",
    t: ["dd.BB.dd", "d.x..x.d", "m..dd..m", "mm.uu.mm", "m.m..m.m", "m.a..a.m", "mw.HH.wm", "wwwwwwww"],
    p: [P("hq",6,3,"elijah"), P("kamikaze",5,2), P("bomber",5,5), P("partisan",4,2), P("partisan",4,5), P("mortar",5,3), P("td",5,4)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("commando",2,2), P("commando",2,5), P("artillery",0,2)]
  },
  47: {
    fName: "🌪️ 旋風火車乘風升天加倍感動陣（外衣擊打約旦水分流）",
    t: ["mm.FF.mm", "d..LL..d", "~~~bb~~~", "~~rbb~~~", "~~~bbr~~", "b..LL..b", "c..aa..c", "cc.HH.cc"],
    p: [P("hq",7,3,"elisha"), P("armoredtrain",6,2), P("bomber",6,5), P("td",6,3), P("tank",6,4), P("commando",5,2), P("commando",5,5)],
    a: [P("hq",0,4), P("td",1,2), P("tank",1,5), P("battleship",3,1), P("destroyer",4,6), P("commando",2,3), P("commando",2,4)]
  },
  48: {
    fName: "🐎 多坍山城開眼見火車火馬陣（與我們同在的比他們更多）",
    t: ["cc.BB.cc", "c.d..d.c", "m..tt..m", "mm.cc.mm", "mm.HH.mm", "m..aa..m", "d......d", "dddddddd"],
    p: [P("hq",4,3,"elisha"), P("armoredtrain",3,2), P("armoredtrain",3,5), P("td",4,2), P("tank",4,5), P("commando",5,2), P("commando",5,5)],
    a: [P("hq",0,4), P("armoredtrain",1,1), P("armoredtrain",1,6), P("tank",1,3), P("tank",1,4), P("artillery",0,2), P("artillery",0,5)]
  },
  49: {
    fName: "🎵 提哥亞荒野讚美詩班前行大捷陣（聖潔禮服稱謝破三國聯軍）",
    t: ["mm.BB.mm", "d.t..t.d", "d.u..u.d", "..d..d..", "..a==a..", "c.l==l.c", "c......c", "cc.HH.cc"],
    p: [P("hq",7,3,"jehoshaphat"), P("katyusha",5,2), P("katyusha",5,5), P("katyusha",5,3), P("td",6,2), P("tank",6,5), P("commando",6,1)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",2,2), P("artillery",2,5), P("commando",2,3)]
  },
  50: {
    fName: "👼 希西家聖殿展書懇求天使夜護陣（高踞重壘抵禦亞述巨力）",
    t: ["dd.BB.dd", "d.t..t.d", "..u..u..", "c.tttt.c", "c.~aa~.c", "c.hHHh.c", "cccccccc", "~~~cc~~~"],
    p: [P("hq",5,3,"hezekiah"), P("kamikaze",4,2), P("bomber",4,5), P("td",5,1), P("tank",5,6), P("katyusha",6,2), P("artillery",6,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,1)]
  },

  // ---------------- 四、先知默示與被擄歸回 (51-60) ----------------
  51: {
    fName: "🔥 至高寶座撒拉弗紅炭沾唇陣（聖哉三呼罪孽除盡奉差）",
    t: ["cc.BB.cc", "c.iFFi.c", "c.tLLt.c", "=.aLLa.=", "=..LL..=", "c.h..h.c", "cc.HH.cc", "cccccccc"],
    p: [P("hq",6,3,"isaiah"), P("kamikaze",5,2), P("kamikaze",5,5), P("bomber",6,2), P("td",6,5), P("mortar",4,3), P("mortar",4,4)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",2,2), P("artillery",2,5), P("infantry",3,2)]
  },
  52: {
    fName: "📜 迦巴魯河畔寄書被擄平安指望陣（七十年後必定眷顧歸回）",
    t: ["cc.BB.cc", "~c.uu.c~", "~~....~~", "~f.aa.f~", "~f.hh.f~", "~~....~~", "~c.HH.c~", "~~cccc~~"],
    p: [P("hq",6,3,"jeremiah"), P("td",5,2), P("tank",5,5), P("engineer",4,2), P("mortar",4,5), P("fighter",6,2), P("commando",6,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,2), P("tank",1,5), P("artillery",0,2), P("artillery",0,5), P("commando",2,3)]
  },
  53: {
    fName: "🌬️ 平原枯骨遵命預言氣息復生陣（極枯骸骨化為耶和華大軍）",
    t: ["dd.BB.dd", "d.u..u.d", "u..xx..u", "d.u..u.d", "d..aa..d", "u......u", "d.dHHd.d", "dddddddd"],
    p: [P("hq",6,3,"ezekiel"), P("kamikaze",5,1), P("bomber",5,6), P("td",5,2), P("tank",5,5), P("commando",4,2), P("commando",4,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",2,2), P("artillery",2,5), P("commando",3,1)]
  },
  54: {
    fName: "🔥 杜拉平原烈火窯中神子同行陣（寸絲不損見證至高真神）",
    t: ["cc.BB.cc", "c.t..t.c", "d.xLLx.d", "d.LLLL.d", "d.aHHa.d", "d.x..x.d", "c......c", "cccccccc"],
    p: [P("hq",4,3,"daniel"), P("kamikaze",3,3), P("kamikaze",3,4), P("td",4,2), P("tank",4,5), P("commando",5,2), P("commando",5,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",6,1)]
  },
  55: {
    fName: "🦁 面向耶路撒冷三時祈禱封住獅口陣（使者護庇義僕安然無恙）",
    t: ["cc.BB.cc", "c.c..c.c", "m.tuut.m", "m.x..x.m", "m..aa..m", "c.h==h.c", "c.hHHh.c", "cccccccc"],
    p: [P("hq",6,3,"daniel"), P("kamikaze",5,3), P("td",5,2), P("tank",5,5), P("commando",4,2), P("commando",4,5), P("mortar",6,2)],
    a: [P("hq",0,4), P("commando",1,2), P("commando",1,5), P("partisan",2,1), P("partisan",2,6), P("tank",1,3), P("artillery",0,3)]
  },
  56: {
    fName: "🐋 滄海深淵魚腹悔改求告陣（深水巨浸吐在旱地傳道）",
    t: ["ccppppcc", "~~r~~r~~", "~r~~~~r~", "~~~~r~~~", "~~r~~~~r", "~r~~~~r~", "~~~~~~~~", "ppbHHbpp"],
    p: [P("flagship",7,3,"jonah"), P("sub",6,2), P("sub",6,5), P("transport",7,4), P("transport",7,2), P("battleship",6,3), P("carrier",6,4)],
    a: [P("flagship",0,4), P("battleship",1,2), P("cruiser",1,5), P("destroyer",2,1), P("destroyer",2,6), P("sub",3,3), P("mtb",3,4)]
  },
  57: {
    fName: "📖 奉旨歸回於原基立壇獻祭陣（稱謝耶和華本為善慈愛長存）",
    t: ["dd.BB.dd", "c.uFFu.c", "c.uLLu.c", "..u..u..", "=.a..a.=", "c......c", "cc.HH.cc", "cccccccc"],
    p: [P("hq",6,3,"ezra"), P("engineer",5,2), P("engineer",5,5), P("katyusha",6,2), P("katyusha",6,5), P("td",5,3), P("tank",5,4)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2)]
  },
  58: {
    fName: "👑 書珊王宮內院伸出金杖轉危為安陣（禁食祈求翻轉滅族毒計）",
    t: ["cc.BB.cc", "c.i..i.c", "f.c==c.f", "f..==..f", "c.a==a.c", "c.i..i.c", "cc.HH.cc", "cccccccc"],
    p: [P("hq",6,3,"esther"), P("td",5,2), P("td",5,5), P("tank",6,2), P("tank",6,5), P("commando",4,2), P("commando",4,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2)]
  },
  59: {
    fName: "🧱 尼希米五十二日一手作工一手兵器修垣陣（號角在旁嚴密警備）",
    t: ["dd.BB.dd", "d.u..u.d", "t.tuut.t", "t..aa..t", "t.c..c.t", "t.hHHh.t", "tttttttt", "cccccccc"],
    p: [P("hq",5,3,"nehemiah"), P("engineer",3,2), P("engineer",3,5), P("td",4,2), P("tank",4,5), P("katyusha",5,2), P("artillery",5,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,1)]
  },
  60: {
    fName: "🌅 公義日頭興起光線醫治破曉陣（跨越兩約四百載沈寂守望）",
    t: ["vv.BB.vv", "v.xFFx.v", "u.xLLx.u", "..LLLL..", "..aLLa..", "c......c", "cc.HH.cc", "cccccccc"],
    p: [P("hq",6,3,"malachi"), P("bomber",5,2), P("bomber",5,5), P("kamikaze",6,2), P("td",6,5), P("commando",4,2), P("commando",4,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",2,1), P("artillery",2,6), P("commando",3,2)]
 
},






// ---------------- 五、四福音神蹟與主耶穌生平 (61-90) ----------------
  61: {
    fName: "🌟 伯利恆客店馬槽晨星顯現陣（牧羊人夜間野地看守羊群）",
    t: ["cc.BB.cc", "c.tFFt.c", "f..LL..f", "...LL...", "f.aLLa.f", "f.h..h.f", "..hHHh..", "ffffffff"],
    p: [P("hq",6,3,"jesus"), P("kamikaze",5,2), P("bomber",5,5), P("fighter",4,2), P("fighter",4,5), P("td",6,2), P("tank",6,5), P("infantry",5,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("infantry",1,4)]
  },
  62: {
    fName: "🐪 東方博士開寶盒獻乳香沒藥陣（別路繞行避開希律暗哨）",
    t: ["ddppppdd", "d.=..=.d", "m.=tt=.m", "m..uu..m", "d..LL..d", "d.aLLa.d", "c......c", "cc.HH.cc"],
    p: [P("hq",7,3,"jesus"), P("transport",6,2), P("transport",6,5), P("fighter",6,1), P("fighter",6,6), P("td",6,3), P("tank",6,4), P("commando",5,2)],
    a: [P("hq",0,4), P("commando",1,2), P("commando",1,5), P("tank",2,1), P("tank",2,6), P("artillery",1,3), P("infantry",3,3), P("infantry",3,4)]
  },
  63: {
    fName: "🕊️ 約旦河受洗天開聖靈如鴿降臨陣（天上有聲音稱讚愛子）",
    t: ["dd.BB.dd", "d.bFFb.d", "~~~bb~~~", "~~r~~r~~", "~~~bb~~~", "d.bLLb.d", "d.a..a.d", "dd.HH.dd"],
    p: [P("hq",7,3,"johnbaptist"), P("fighter",6,2), P("fighter",6,5), P("partisan",5,2), P("partisan",5,5), P("td",6,3), P("tank",6,4), P("infantry",5,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  64: {
    fName: "🏜️ 猶太曠野禁食四十晝夜「經上記著說」陣（徹底擊退魔鬼三重試誘）",
    t: ["mm.BB.mm", "md.cc.dm", "d.txxt.d", "d..aa..d", "d.x..x.d", "d......d", "dm.HH.md", "mm....mm"],
    p: [P("hq",6,3,"jesus"), P("td",5,3), P("td",5,4), P("kamikaze",6,4), P("bomber",6,2), P("commando",5,2), P("commando",5,5), P("fighter",6,5)],
    a: [P("hq",0,4), P("kamikaze",1,3), P("td",1,4), P("tank",2,1), P("tank",2,6), P("artillery",1,2), P("artillery",1,5), P("commando",3,1)]
  },
  65: {
    fName: "🐟 革尼撒勒湖開到水深處下網得人陣（整夜勞力後雙船滿網）",
    t: ["pp.BB.pp", "b~rFFr~b", "~~~..~~~", "~~r~~r~~", "~~~~~~~~", "~r~~~~r~", "b~....~b", "ppbHHbpp"],
    p: [P("flagship",7,3,"jesus"), P("carrier",6,2), P("carrier",6,5), P("battleship",6,3), P("cruiser",6,4), P("destroyer",5,2), P("destroyer",5,5)],
    a: [P("flagship",0,4), P("battleship",1,2), P("cruiser",1,5), P("destroyer",2,1), P("destroyer",2,6), P("sub",3,3), P("sub",3,4)]
  },
  66: {
    fName: "🏺 迦拿婚筵六口石缸水變上等美酒陣（顯出榮耀門徒信從）",
    t: ["cc.BB.cc", "c.hFFh.c", "c.i..i.c", "..h..h..", "=.a..a.=", "=......=", "c.hHHh.c", "cccccccc"],
    p: [P("hq",6,3,"jesus"), P("td",5,2), P("tank",5,5), P("katyusha",6,2), P("artillery",6,5), P("commando",4,2), P("commando",4,5), P("infantry",5,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("infantry",2,4)]
  },
  67: {
    fName: "⛰️ 八福山寶訓天國八福造在山上的城陣（門徒圍坐傳講公義真道）",
    t: ["~~.BB.~~", "~b.cc.b~", "b..tt..b", "f......f", "m.aLLa.m", "mm.HH.mm", "m.f..f.m", "mmmmmmmm"],
    p: [P("hq",5,3,"jesus"), P("bomber",4,2), P("bomber",4,5), P("td",5,1), P("tank",5,6), P("mortar",4,3), P("mortar",4,4), P("infantry",3,2)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,2), P("tank",1,5), P("artillery",2,1), P("artillery",2,6), P("commando",2,3), P("commando",2,4)]
  },
  68: {
    fName: "🏠 迦百農拆通房頂縋下癱子得蒙赦罪陣（見他們的信心吩咐行走）",
    t: ["cc.BB.cc", "c.hFFh.c", "h.huuh.h", "h..aa..h", "..h..h..", "=.c..c.=", "c.hHHh.c", "cccccccc"],
    p: [P("hq",6,3,"jesus"), P("engineer",5,2), P("engineer",5,5), P("commando",4,1), P("commando",4,6), P("td",5,3), P("tank",5,4), P("mortar",6,2)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("infantry",2,3), P("infantry",2,4)]
  },
  69: {
    fName: "⛵ 斥責加利利海狂風大浪「住了吧！靜了吧！」陣（風浪平息門徒敬畏）",
    t: ["pppppppp", "~b~r~~b~", "~~r~~r~~", "~~~~r~~~", "~r~~~~r~", "~~~rr~~~", "~b~~~~b~", "ppbHHbpp"],
    p: [P("flagship",7,3,"jesus"), P("transport",7,4), P("transport",7,2), P("battleship",6,3), P("carrier",6,4), P("cruiser",6,2), P("destroyer",6,5)],
    a: [P("flagship",0,4), P("battleship",1,3), P("cruiser",1,4), P("destroyer",2,2), P("destroyer",2,5), P("sub",3,3), P("sub",3,4)]
  },
  70: {
    fName: "⛓️ 格拉森墳塋釋放被「群」污鬼附著者陣（污鬼入豬投海得釋放）",
    t: ["uu.BB.uu", "u.txxt.u", "m.u..u.m", "m..aa..m", "~b....b~", "~~b..b~~", "~~bHHb~~", "~~~~~~~~"],
    p: [P("hq",6,3,"jesus"), P("kamikaze",5,2), P("bomber",5,5), P("td",5,3), P("tank",5,4), P("commando",4,2), P("commando",4,5), P("cruiser",6,1)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("commando",2,2), P("commando",2,5), P("artillery",0,2), P("artillery",0,5)]
  },
  71: {
    fName: "🛡️ 迦百農百夫長「只要說一句話」僕人痊癒陣（外邦極大信心得稱許）",
    t: ["cc.BB.cc", "c.=FF=.c", "..t==t..", "c..==..c", "c.a==a.c", "..h..h..", "c..HH..c", "cccccccc"],
    p: [P("hq",6,3,"jesus"), P("td",5,3), P("tank",5,2), P("tank",5,5), P("katyusha",6,2), P("artillery",6,5), P("commando",4,2), P("commando",4,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  72: {
    fName: "🌿 拿因城門棺槓「少年人我吩咐你起來」陣（寡婦獨生子死而復生）",
    t: ["uu.BB.uu", "u.t..t.u", "..l==l..", "f.c==c.f", "f.a==a.f", "..c..c..", "c.hHHh.c", "cccccccc"],
    p: [P("hq",6,3,"jesus"), P("kamikaze",5,2), P("td",5,3), P("tank",5,4), P("bomber",5,5), P("commando",4,2), P("commando",4,5), P("infantry",6,2)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  73: {
    fName: "🍞 伯賽大青草野地五餅二魚祝謝擘開陣（五千人飽足零碎滿十二籃）",
    t: ["dd.BB.dd", "d.x..x.d", "f......f", "f..aa..f", "..f..f..", "~b....b~", "~b.HH.b~", "~~~~~~~~"],
    p: [P("hq",6,3,"jesus"), P("transport",5,3), P("transport",5,4), P("td",5,2), P("tank",5,5), P("mortar",4,2), P("mortar",4,5), P("infantry",4,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("commando",2,2), P("commando",2,5), P("artillery",0,2), P("artillery",0,5)]
  },
  74: {
    fName: "🌊 四更天湖面行走「是我，不要怕！」伸手救彼得陣（踏平逆風幽暗）",
    t: ["pp.FF.pp", "~b~LL~b~", "~~rLLr~~", "~~~LL~~~", "~~rLLr~~", "~r~LL~r~", "~b~LL~b~", "ppbHHbpp"],
    p: [P("flagship",7,3,"jesus"), P("battleship",6,2), P("carrier",6,5), P("td",6,3), P("commando",6,4), P("cruiser",5,2), P("destroyer",5,5)],
    a: [P("flagship",0,4), P("battleship",1,2), P("cruiser",1,5), P("destroyer",2,1), P("destroyer",2,6), P("sub",3,2), P("sub",3,5)]
  },
  75: {
    fName: "💧 撒瑪利亞敘加雅各井旁賜永生活水陣（午正談道引導全城歸信）",
    t: ["mm.BB.mm", "m.cFFc.m", "d.u..u.d", "d.s~~s.d", "d.s~~s.d", "..a..a..", "d......d", "dd.HH.dd"],
    p: [P("hq",7,3,"jesus"), P("td",6,2), P("tank",6,5), P("commando",5,2), P("commando",5,5), P("mortar",5,3), P("partisan",5,4), P("infantry",6,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  76: {
    fName: "🪨 該撒利亞腓立比「你是基督永生神之子」認信陣（磐石上建造教會）",
    t: ["uu.BB.uu", "u.x..x.u", "m.t..t.m", "m..~~..m", "mm.aa.mm", "mw.HH.wm", "ww.mm.ww", "wwwwwwww"],
    p: [P("hq",5,3,"peter"), P("td",4,2), P("td",4,5), P("tank",5,2), P("tank",5,5), P("commando",3,2), P("commando",3,5), P("infantry",4,3)],
    a: [P("hq",0,4), P("kamikaze",1,3), P("td",1,4), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2)]
  },
  77: {
    fName: "✨ 黑門聖山變像面容如日摩西以利亞同現陣（雲中出聲「要聽祂！」）",
    t: ["dd.BB.dd", "m.uFFu.m", "w.mLLm.w", "ww.LL.ww", "w.aLLa.w", "m......m", "mm.HH.mm", "wwwwwwww"],
    p: [P("hq",6,3,"jesus"), P("bomber",5,2), P("kamikaze",5,5), P("td",5,3), P("armoredtrain",5,4), P("commando",4,2), P("commando",4,5), P("fighter",6,2)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  78: {
    fName: "👣 差遣七十個門徒兩個兩個宣告神國臨近陣（如羊入狼群踐踏蛇蠍）",
    t: ["cc.FF.cc", "c.=..=.c", "f.=xx=.f", "..=..=..", "d.=aa=.d", "d.=..=.d", "c.=HH=.c", "cccccccc"],
    p: [P("hq",6,3,"jesus"), P("td",5,1), P("tank",5,6), P("commando",4,1), P("commando",4,6), P("partisan",5,2), P("partisan",5,5), P("infantry",4,2)],
    a: [P("hq",0,4), P("td",1,2), P("tank",1,5), P("commando",2,1), P("commando",2,6), P("artillery",0,2), P("artillery",0,5), P("infantry",2,3)]
  },
  79: {
    fName: "🫏 耶利哥下坡路慈憐撒瑪利亞人裹傷客店陣（跨越強盜荒徑動了慈心）",
    t: ["ccppppcc", "m.h==h.m", "m.x==x.m", "d..==..d", "d.x==x.d", "m.a==a.m", "c......c", "cc.HH.cc"],
    p: [P("hq",7,3,"jesus"), P("transport",6,3), P("transport",6,4), P("td",6,2), P("tank",6,5), P("commando",5,2), P("commando",5,5), P("engineer",5,3)],
    a: [P("hq",0,4), P("commando",1,2), P("commando",1,5), P("partisan",2,1), P("partisan",2,6), P("tank",1,3), P("artillery",0,2), P("infantry",3,2)]
  },
  80: {
    fName: "🌊 西羅亞奉差水池生來瞎眼洗後重見天日陣（坦承從前眼瞎如今能見）",
    t: ["cc.BB.cc", "c.tFFt.c", "c.~LL~.c", "..~~~~..", "..bLLb..", "c.a..a.c", "cc.HH.cc", "cccccccc"],
    p: [P("hq",6,3,"jesus"), P("bomber",5,2), P("kamikaze",5,5), P("td",5,3), P("tank",5,4), P("commando",4,1), P("commando",4,6), P("infantry",6,2)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  81: {
    fName: "🐑 好牧人捨命作羊之門領羊得豐盛生命陣（驅退偷竊殺害豺狼）",
    t: ["dd.BB.dd", "f.x..x.f", "f......f", "t.t..t.t", "t.a..a.t", "t..ff..t", "t.fHHf.t", "tttttttt"],
    p: [P("hq",6,3,"jesus"), P("td",3,3), P("tank",3,4), P("commando",4,2), P("commando",4,5), P("mortar",5,2), P("mortar",5,5), P("infantry",5,3)],
    a: [P("hq",0,4), P("commando",1,1), P("commando",1,6), P("partisan",2,2), P("partisan",2,5), P("tank",1,3), P("artillery",0,2), P("artillery",0,5)]
  },
  82: {
    fName: "🪨 伯大尼墓洞輥開石頭大聲呼喚拉撒路出來陣（復活在我生命也在我）",
    t: ["mm.BB.mm", "m.uFFu.m", "f.tuut.f", "f..LL..f", "..aLLa..", "h......h", "hc.HH.ch", "hhhhhhhh"],
    p: [P("hq",6,3,"jesus"), P("kamikaze",5,3), P("td",5,2), P("tank",5,5), P("engineer",4,2), P("engineer",4,5), P("commando",5,4), P("fighter",6,2)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  83: {
    fName: "🌳 耶利哥桑樹撒該俯就今日救恩臨到這家陣（尋找拯救失喪之人）",
    t: ["cc.BB.cc", "c.hFFh.c", "f.c==c.f", "f..==..f", "s.f==f.s", "s.a==a.s", "c......c", "cc.HH.cc"],
    p: [P("hq",7,3,"jesus"), P("td",6,2), P("tank",6,5), P("commando",5,2), P("commando",5,5), P("mortar",5,3), P("katyusha",5,4), P("infantry",6,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  84: {
    fName: "🌿 棕樹主日騎驢駒榮入聖城和散那歸大衛子孫陣（謙和君王就職受敬拜）",
    t: ["cc.FF.cc", "c.t==t.c", "c..==..c", "~~~bb~~~", "f..==..f", "fm.aa.mf", "m..==..m", "mm.HH.mm"],
    p: [P("hq",7,3,"jesus"), P("katyusha",6,2), P("katyusha",6,5), P("td",6,3), P("tank",6,4), P("commando",5,2), P("commando",5,5), P("infantry",4,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  85: {
    fName: "🥣 錫安馬可樓束腰洗腳彼此相愛新命令陣（立新約的血與擘餅筵席）",
    t: ["cc.BB.cc", "c.u..u.c", "h.tttt.h", "h.~aa~.h", "h.hHHh.h", "h......h", "cccccccc", "cccccccc"],
    p: [P("hq",4,3,"jesus"), P("td",3,2), P("tank",3,5), P("commando",4,1), P("commando",4,6), P("mortar",5,2), P("engineer",5,5), P("infantry",3,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  86: {
    fName: "🫒 客西馬尼園極其傷痛禱告「願祢旨意成就」陣（汗如血滴順服苦杯）",
    t: ["cc.BB.cc", "c.t..t.c", "~~~bb~~~", "f.f..f.f", "ff.aa.ff", "f.fHHf.f", "ff....ff", "mmmmmmmm"],
    p: [P("hq",5,3,"jesus"), P("kamikaze",4,3), P("td",4,2), P("tank",4,5), P("mortar",5,2), P("mortar",5,5), P("commando",3,2), P("fighter",6,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("commando",2,2), P("commando",2,5), P("artillery",0,2), P("artillery",0,5)]
  },
  87: {
    fName: "✝️ 各各他髑髏地十架「成了！」殿幔從上裂為兩半陣（流血捨身開新活路）",
    t: ["vv.BB.vv", "v.t..t.v", "m.uLLu.m", "mm.LL.mm", "m.aLLa.m", "c.tLLt.c", "cc.HH.cc", "cccccccc"],
    p: [P("hq",6,3,"jesus"), P("kamikaze",5,3), P("bomber",5,4), P("td",5,2), P("tank",5,5), P("commando",4,2), P("fighter",6,2), P("fighter",6,5)],
    a: [P("hq",0,4), P("kamikaze",1,3), P("td",1,4), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2)]
  },
  88: {
    fName: "🌅 七日第一日清晨空墓大地震天使宣告「祂已復活！」陣（死權毒鉤徹底粉碎）",
    t: ["uu.BB.uu", "u.t..t.u", "f.uLLu.f", "f..LL..f", "f.aLLa.f", "..LLLL..", "f..HH..f", "ffffffff"],
    p: [P("hq",6,3,"jesus"), P("kamikaze",5,2), P("kamikaze",5,5), P("bomber",5,3), P("td",5,4), P("commando",4,2), P("fighter",6,2), P("fighter",6,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  89: {
    fName: "🔥 以馬忤斯路上講解基督受害與擘餅心裡火熱陣（眼睛明亮認出主）",
    t: ["hh.FF.hh", "f.h==h.f", "m..==..m", "..f==f..", "..a==a..", "c..==..c", "cc.HH.cc", "cccccccc"],
    p: [P("hq",6,3,"jesus"), P("td",5,2), P("tank",5,5), P("bomber",6,2), P("commando",4,2), P("commando",4,5), P("partisan",5,3), P("infantry",4,3)],
    a: [P("hq",0,4), P("td",1,2), P("tank",1,5), P("artillery",0,2), P("artillery",0,5), P("commando",2,1), P("commando",2,6), P("infantry",3,2)]
  },
  90: {
    fName: "🐟 提比哩亞海晨光炭火烤魚「你餵養我的羊」陣（三次託付重燃愛火）",
    t: ["pp.BB.pp", "~b.FF.b~", "~~~~~~~~", "~~r~~r~~", "~~~~~~~~", "~b.aa.b~", "bb.aa.bb", "ppbHHbpp"],
    p: [P("flagship",7,3,"jesus"), P("carrier",6,2), P("battleship",6,5), P("cruiser",5,2), P("destroyer",5,5), P("td",6,3), P("commando",6,4), P("fighter",7,4)],
    a: [P("flagship",0,4), P("battleship",1,2), P("cruiser",1,5), P("destroyer",2,1), P("destroyer",2,6), P("sub",3,3), P("sub",3,4)]
  },

  // ---------------- 六、使徒行傳、書信與啟示錄 (91-120) ----------------
  91: {
    fName: "☁️ 橄欖山巔聖靈降臨得著能力直到地極見證陣（白衣天使應許同樣再來）",
    t: ["cc.BB.cc", "c.=FF=.c", "f..==..f", "m.fLLf.m", "mm.aa.mm", "m..LL..m", "mc.HH.cm", "mmmmmmmm"],
    p: [P("hq",6,3,"peter"), P("bomber",5,2), P("fighter",5,5), P("td",5,3), P("tank",5,4), P("commando",4,2), P("commando",4,5), P("infantry",4,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  92: {
    fName: "🕊️ 五旬節如大風烈火分開落在各人頭上陣（口說別國鄉談三千人悔改）",
    t: ["c..BB..c", ".c.==.c.", "..h..h..", ".=hHHh=.", ".=haah=.", "..h..h..", ".c.==.c.", "c......c"],
    p: [P("hq",3,3,"peter"), P("kamikaze",3,4), P("td",4,3), P("katyusha",4,4), P("fighter",2,3), P("fighter",2,4), P("commando",3,2), P("commando",3,5)],
    a: [P("hq",0,4), P("tank",0,2), P("tank",0,5), P("artillery",1,1), P("artillery",1,6), P("commando",6,1), P("commando",6,6), P("infantry",1,3)]
  },
  93: {
    fName: "🏛️ 聖殿美門口「金銀我都沒有奉拿撒勒人耶穌名」陣（瘸腿健步跳躍讚美神）",
    t: ["cc.BB.cc", "c.iFFi.c", "c.t==t.c", "..i==i..", "..a==a..", "c.l==l.c", "cc.HH.cc", "cccccccc"],
    p: [P("hq",6,3,"peter"), P("td",5,2), P("tank",5,5), P("commando",4,2), P("commando",4,5), P("katyusha",5,3), P("mortar",5,4), P("infantry",6,2)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  94: {
    fName: "🙏 耶路撒冷同心合意禱告聚會處震動聖靈充滿陣（放膽講論神道凡物公用）",
    t: ["cc.BB.cc", "c.t..t.c", "..u..u..", "h.c..c.h", "h.aLLa.h", "h.hHHh.h", "cccccccc", "cccccccc"],
    p: [P("hq",5,3,"peter"), P("kamikaze",4,3), P("bomber",4,4), P("td",4,2), P("tank",4,5), P("commando",3,2), P("commando",3,5), P("mortar",5,2)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  95: {
    fName: "✨ 司提反公會前定睛望天看見神榮耀與人子陣（面貌如天使求赦頑梗石頭）",
    t: ["mm.BB.mm", "m.u..u.m", "u..tt..u", "..uLLu..", "c.aLLa.c", "c.t..t.c", "cc.HH.cc", "cccccccc"],
    p: [P("hq",6,3,"stephen"), P("kamikaze",5,3), P("bomber",5,4), P("td",5,2), P("tank",5,5), P("commando",4,2), P("fighter",6,2), P("fighter",6,5)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",2,2), P("artillery",2,5), P("commando",2,3), P("commando",2,4)]
  },
  96: {
    fName: "💧 迦薩曠野路貼近太監車讀以賽亞書傳福音陣（曠野歡喜受洗傳承外邦）",
    t: ["dd.FF.dd", "d.=..=.d", "d.=~~=.d", "s.=~~=.s", "d..==..d", "d.a==a.d", "d......d", "dd.HH.dd"],
    p: [P("hq",7,3,"philip"), P("armoredtrain",6,3), P("fighter",6,2), P("fighter",6,5), P("td",5,2), P("tank",5,5), P("commando",5,3), P("partisan",5,4)],
    a: [P("hq",0,4), P("td",1,2), P("tank",1,5), P("commando",2,1), P("commando",2,6), P("artillery",0,2), P("artillery",0,5)]
  },
  97: {
    fName: "⚡ 大馬士革路大光撲地「掃羅！你為何逼迫我？」陣（直街盲目三日悔改復明）",
    t: ["cc.BB.cc", "c.tFFt.c", "c.h==h.c", "..L==L..", "d.L==L.d", "d.a==a.d", "d......d", "dd.HH.dd"],
    p: [P("hq",7,3,"paul"), P("bomber",6,2), P("kamikaze",6,5), P("td",5,3), P("tank",5,4), P("commando",5,2), P("commando",5,5), P("infantry",6,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  98: {
    fName: "⛵ 約帕海邊硝皮匠房頂大布異象聖靈臨哥尼流陣（神所潔淨不可當作俗物）",
    t: ["cc.BB.cc", "~b.FF.b~", "~b.cc.b~", "~~b==b~~", "~~b==b~~", "~p.aa.p~", "~p.h..h.", "~ppHHhh."],
    p: [P("hq",7,3,"peter"), P("fighter",6,2), P("bomber",6,5), P("td",5,3), P("tank",5,4), P("cruiser",5,1), P("commando",4,4), P("infantry",6,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,2), P("tank",1,5), P("destroyer",3,0), P("artillery",0,2), P("commando",2,3), P("commando",2,4)]
  },
  99: {
    fName: "🏛️ 敘利亞安提阿門徒首稱「基督徒」海外宣教母港陣（巴拿巴保羅同心牧養）",
    t: ["cc.BB.cc", "c.c..c.c", "~b.tt.b~", "~~~bb~~~", "c..aa..c", "c.h==h.c", "cc.HH.cc", "cccccccc"],
    p: [P("hq",6,3,"paul"), P("td",5,2), P("tank",5,5), P("katyusha",6,2), P("artillery",6,5), P("commando",4,2), P("commando",4,5), P("infantry",4,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  100: {
    fName: "⛓️ 耶路撒冷內監鐵鍊脫落天使引彼得出鐵門陣（切切禱告羅大開門相迎）",
    t: ["hhhhhhhh", "c.h==h.c", "c..==..c", "t.tLLt.t", "t.uLLu.t", "t.xLLx.t", "cc.HH.cc", "tttttttt"],
    p: [P("hq",6,3,"peter"), P("kamikaze",5,3), P("transport",6,4), P("transport",6,2), P("td",4,2), P("tank",4,5), P("commando",5,2), P("engineer",5,4)],
    a: [P("hq",0,4), P("td",1,2), P("tank",1,5), P("tank",2,1), P("tank",2,6), P("commando",3,1), P("commando",3,6)]
  },
  101: {
    fName: "⛵ 差派保羅巴拿巴首航居比路帕弗城斥責術士陣（省長信從真道）",
    t: ["cc.FF.cc", "bb.cc.bb", "~r~~~~r~", "~~~mm~~~", "~~~~~~~~", "~r~~~~r~", "bb.aa.bb", "ppbHHbpp"],
    p: [P("flagship",7,3,"paul"), P("battleship",6,2), P("carrier",6,5), P("cruiser",5,2), P("destroyer",5,5), P("fighter",6,3), P("bomber",6,4)],
    a: [P("flagship",0,4), P("battleship",1,2), P("cruiser",1,5), P("destroyer",2,1), P("destroyer",2,6), P("sub",4,2), P("sub",4,5)]
  },
  102: {
    fName: "⛰️ 加拉太以哥念與路司得城外重傷起立進城堅固門徒陣（進神國必經多艱難）",
    t: ["mm.BB.mm", "m.c..c.m", "d.u..u.d", "d.t..t.d", "..a..a..", "m.c..c.m", "mc.HH.cm", "mmmmmmmm"],
    p: [P("hq",6,3,"paul"), P("td",5,2), P("tank",5,5), P("commando",4,2), P("commando",4,5), P("engineer",5,3), P("mortar",5,4), P("infantry",4,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  103: {
    fName: "📜 耶路撒冷使徒公會議「不將重擔加在外邦人身上」陣（真理辯明福音合一）",
    t: ["cc.BB.cc", "c.t..t.c", "c..uu..c", "=.c..c.=", "=.aLLa.=", "c.hHHh.c", "cccccccc", "cccccccc"],
    p: [P("hq",5,3,"peter"), P("td",4,2), P("td",4,5), P("tank",5,1), P("tank",5,6), P("katyusha",4,3), P("mortar",4,4), P("commando",3,2)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  104: {
    fName: "🌊 特羅亞夜間異象「請到馬其頓來幫助我們」跨洋陣（福音首度西渡歐洲）",
    t: ["pp.FF.pp", "bb.cc.bb", "~~r~~r~~", "~~~mm~~~", "~~r~~r~~", "~~~~~~~~", "bb.aa.bb", "ppbHHbpp"],
    p: [P("flagship",7,3,"paul"), P("battleship",6,2), P("carrier",6,5), P("cruiser",5,2), P("destroyer",5,5), P("mtb",6,3), P("fighter",6,4)],
    a: [P("flagship",0,4), P("battleship",1,2), P("cruiser",1,5), P("destroyer",2,1), P("destroyer",2,6), P("sub",4,3), P("sub",4,4)]
  },
  105: {
    fName: "🎵 腓立比內監半夜禱告唱詩讚美地大震動門開鎖落陣（當信主耶穌全家必得救）",
    t: ["cc.BB.cc", "c.t..t.c", "t.tuut.t", "t.xLLx.t", "t.aHHa.t", "t..cc..t", "cccccccc", "tttttttt"],
    p: [P("hq",4,3,"paul"), P("katyusha",3,2), P("katyusha",3,5), P("kamikaze",3,3), P("td",3,4), P("engineer",4,2), P("engineer",4,5), P("commando",5,2)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,1), P("commando",2,6)]
  },
  106: {
    fName: "📖 庇哩亞會堂「甘心領受這道天天考查聖經」賢明守望陣（考證道與經相符）",
    t: ["cc.BB.cc", "c.u..u.c", "f.t..t.f", "f.c==c.f", "=.aLLa.=", "c.hHHh.c", "cccccccc", "ffffffff"],
    p: [P("hq",5,3,"paul"), P("td",4,2), P("td",4,5), P("tank",5,1), P("tank",5,6), P("mortar",4,3), P("mortar",4,4), P("commando",3,2)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  107: {
    fName: "🏛️ 雅典亞略巴古宣告創造天地真神「我們生活動作都在乎祂」陣（辨正假神）",
    t: ["mm.BB.mm", "mc.FF.cm", "c.i..i.c", "m.u..u.m", "m.a==a.m", "c..==..c", "cc.HH.cc", "cccccccc"],
    p: [P("hq",6,3,"paul"), P("td",5,2), P("td",5,5), P("bomber",6,2), P("fighter",6,5), P("commando",4,2), P("commando",4,5), P("infantry",5,3)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  108: {
    fName: "⛺ 哥林多地峽同工織帳「不要怕只管講在這城裡我有許多百姓」陣（堅立教會）",
    t: ["~p.BB.p~", "~b.cc.b~", "c.t..t.c", "c.h..h.c", "c.a==a.c", "~b.HH.b~", "~p.cc.p~", "~~~~~~~~"],
    p: [P("hq",5,3,"paul"), P("engineer",4,2), P("engineer",4,5), P("td",4,3), P("tank",4,4), P("commando",3,2), P("commando",3,5), P("cruiser",5,0)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,2), P("tank",1,5), P("destroyer",1,0), P("destroyer",1,7), P("commando",2,2), P("commando",2,5)]
  },
  109: {
    fName: "🔥 以弗所推喇奴學房主的道大大興旺焚燒巫術虛妄陣（神蹟彰顯勝偶像）",
    t: ["cc.BB.cc", "c.i..i.c", "c.txxt.c", "..uLLu..", "=.aLLa.=", "c.h..h.c", "cc.HH.cc", "cccccccc"],
    p: [P("hq",6,3,"paul"), P("kamikaze",5,2), P("bomber",5,5), P("td",5,3), P("tank",5,4), P("commando",4,1), P("commando",4,6), P("infantry",6,2)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  110: {
    fName: "🏖️ 米利都海灘同長老跪下痛哭離別「施比受更為有福」陣（防禦兇暴豺狼）",
    t: ["dd.BB.dd", "f.x..x.f", "f.t..t.f", "..f..f..", "bb.aa.bb", "~b.HH.b~", "~pppppp~", "~~~~~~~~"],
    p: [P("hq",5,3,"paul"), P("td",4,2), P("tank",4,5), P("commando",3,2), P("commando",3,5), P("mortar",4,3), P("mortar",4,4), P("battleship",6,2)],
    a: [P("hq",0,4), P("commando",1,1), P("commando",1,6), P("partisan",2,2), P("partisan",2,5), P("tank",1,3), P("artillery",0,2), P("artillery",0,5)]
  },
  111: {
    fName: "🌪️ 亞得里亞海友拉革羅十四日暗夜天使宣告「一人也不失喪」陣（擱淺破船獲救）",
    t: ["bbbbbbbb", "~~r~~r~~", "~r~~~~r~", "~~~~r~~~", "~~r~~~~r", "~r~~~r~~", "~~~~~~~~", "ppbHHbpp"],
    p: [P("flagship",7,3,"paul"), P("transport",7,4), P("transport",7,2), P("battleship",6,2), P("carrier",6,5), P("cruiser",6,3), P("destroyer",6,4)],
    a: [P("flagship",0,4), P("battleship",1,2), P("cruiser",1,5), P("destroyer",2,1), P("destroyer",2,6), P("sub",3,3), P("sub",3,4)]
  },
  112: {
    fName: "🐍 米利大島土人前火堆甩蛇入火無傷直抵羅馬陣（放膽傳講神國的事）",
    t: ["cc.FF.cc", "c.c==c.c", "..t==t..", "~~b==b~~", "b.x==x.b", "b.a==a.b", "~b.HH.b~", "~~~~~~~~"],
    p: [P("hq",6,3,"paul"), P("kamikaze",5,2), P("td",5,3), P("tank",5,4), P("bomber",5,5), P("commando",4,2), P("commando",4,5), P("partisan",6,2)],
    a: [P("hq",0,4), P("td",1,2), P("tank",1,5), P("artillery",0,2), P("artillery",0,5), P("commando",2,1), P("commando",2,6)]
  },
  113: {
    fName: "👑 羅馬獄中「誰能使我們與基督的愛隔絕靠主得勝有餘」陣（超越患難刀劍）",
    t: ["mm.BB.mm", "m.txxt.m", "d.u..u.d", "..L==L..", "..a==a..", "c.l==l.c", "cc.HH.cc", "cccccccc"],
    p: [P("hq",6,3,"paul"), P("td",5,2), P("td",5,5), P("tank",5,3), P("katyusha",5,4), P("bomber",6,2), P("kamikaze",6,5), P("commando",4,2)],
    a: [P("hq",0,4), P("td",1,3), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2), P("commando",2,5)]
  },
  114: {
    fName: "🛡️ 以弗所書穿戴神所賜全副軍裝「抵擋魔鬼詭計站立得穩」陣（信德滅盡火箭）",
    t: ["vv.BB.vv", "v.x..x.v", "m.tuut.m", "m......m", "t.tLLt.t", "t.aHHa.t", "cccccccc", "tttttttt"],
    p: [P("hq",5,3,"paul"), P("td",4,3), P("td",4,4), P("tank",4,1), P("tank",4,6), P("katyusha",5,2), P("mortar",5,5), P("commando",3,2)],
    a: [P("hq",0,4), P("kamikaze",1,3), P("td",1,4), P("artillery",1,1), P("artillery",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,1)]
  },
  115: {
    fName: "🏛️ 希伯來書「雲彩見證人放下重擔仰望信心創始成終者」陣（忍耐奔跑前程）",
    t: ["cc.FF.cc", "w.i==i.w", "w.L==L.w", "m.x==x.m", "m..==..m", "d.a==a.d", "d......d", "dd.HH.dd"],
    p: [P("hq",7,3,"paul"), P("td",6,2), P("tank",6,5), P("bomber",6,3), P("kamikaze",6,4), P("commando",5,2), P("commando",5,5), P("partisan",4,3)],
    a: [P("hq",0,4), P("td",1,2), P("tank",1,5), P("artillery",0,2), P("artillery",0,5), P("commando",2,1), P("commando",2,6)]
  },
  116: {
    fName: "🕯️ 拔摩海島主日被聖靈感動見七金燈台中間榮耀人子陣（手握七星首先末後）",
    t: ["~~.BB.~~", "~b.FF.b~", "~c.LL.c~", "~L.aa.L~", "~c.LL.c~", "~b.aa.b~", "~~bHHb~~", "~~~~~~~~"],
    p: [P("hq",6,3,"john"), P("kamikaze",5,2), P("bomber",5,5), P("td",5,3), P("tank",5,4), P("fighter",4,2), P("fighter",4,5), P("cruiser",6,1)],
    a: [P("hq",0,4), P("td",1,3), P("tank",2,2), P("tank",2,5), P("destroyer",1,0), P("destroyer",1,7), P("commando",3,2), P("commando",3,5)]
  },
  117: {
    fName: "💎 天上寶座如碧玉紅寶石水晶玻璃海四活物尊崇陣（被殺羔羊配展開七印）",
    t: ["vv.BB.vv", "v.i..i.v", "i.iiii.i", "i.i~~i.i", "i.aHHa.i", "i.iiii.i", "cccccccc", "iiiiiiii"],
    p: [P("hq",4,3,"john"), P("kamikaze",3,2), P("kamikaze",3,5), P("bomber",4,2), P("td",4,5), P("katyusha",5,2), P("katyusha",5,5), P("fighter",3,3)],
    a: [P("hq",0,4), P("kamikaze",1,3), P("td",1,4), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,1)]
  },
  118: {
    fName: "🌴 各國各族身穿白衣手拿棕樹枝寶座羔羊牧養陣（領到生命泉擦去眼淚）",
    t: ["vv.BB.vv", "d.x..x.d", "f.t..t.f", "f.i~~i.f", "f.a~~a.f", "c.iHHi.c", "cccccccc", "ffffffff"],
    p: [P("hq",5,3,"john"), P("kamikaze",4,2), P("bomber",4,5), P("td",4,3), P("tank",4,4), P("katyusha",5,1), P("katyusha",5,6), P("infantry",3,2)],
    a: [P("hq",0,4), P("kamikaze",1,3), P("td",1,4), P("tank",1,1), P("tank",1,6), P("artillery",0,2), P("artillery",0,5), P("commando",2,2)]
  },
  119: {
    fName: "🐉 天上爭戰米迦勒摔下古蛇大龍「因羔羊之血與見證之道」陣（控告者受審）",
    t: ["vv.BB.vv", "v.txxt.v", "m.iLLi.m", "m.LLLL.m", "=.aLLa.=", "m.i..i.m", "mm.HH.mm", "mmmmmmmm"],
    p: [P("hq",6,3,"john"), P("kamikaze",5,2), P("kamikaze",5,5), P("bomber",5,3), P("td",5,4), P("armoredtrain",6,2), P("tank",6,5), P("commando",4,2)],
    a: [P("hq",0,4), P("kamikaze",1,2), P("kamikaze",1,5), P("td",1,3), P("td",1,4), P("tank",2,1), P("tank",2,6), P("artillery",0,2)]
  },
  // #120 史詩大結局：12×12 聖城新耶路撒冷與生命水河決戰
  120: {
    rows: 12, cols: 12,
    fName: "🏛️ 聖城新耶路撒冷 · 十二寶石根基與生命水河 12×12 史詩終章陣",
    t: [
      "ccBBBBBBBBcc",
      "c.iiiiiiii.c",
      "f.i~~~~~~i.f",
      "i.~~cccc~~.i",
      "i.~~cLLc~~.i",
      "i.~~cLLc~~.i",
      "i.~~cccc~~.i",
      "f.i~~~~~~i.f",
      "c.iiiaaiii.c",
      "c..bbbbbb..c",
      "c..bHHHHb..c",
      "cc..hhhh..cc"
    ],
    p: [
      P("hq", 10, 5, "john"), P("hq", 10, 6, "john"),
      P("td", 9, 4), P("td", 9, 7),
      P("tank", 9, 3), P("tank", 9, 8),
      P("bomber", 8, 4), P("bomber", 8, 7),
      P("kamikaze", 8, 5), P("kamikaze", 8, 6),
      P("katyusha", 9, 2), P("katyusha", 9, 9),
      P("artillery", 10, 3), P("artillery", 10, 8),
      P("commando", 8, 2), P("commando", 8, 9),
      P("infantry", 10, 4), P("infantry", 10, 7), P("fighter", 11, 3), P("fighter", 11, 8)
    ],
    a: [
      P("hq", 0, 5), P("hq", 0, 6),
      P("td", 1, 4), P("td", 1, 7),
      P("tank", 1, 3), P("tank", 1, 8),
      P("kamikaze", 2, 4), P("kamikaze", 2, 7),
      P("artillery", 0, 2), P("artillery", 0, 9),
      P("commando", 2, 3), P("commando", 2, 8),
      P("infantry", 1, 5), P("infantry", 1, 6), P("fighter", 0, 3), P("fighter", 0, 8)
    ]
  }
};

const THEATER_META = {
  pentateuch: { name: "摩西五經", ally: "🕎 聖約族長與出埃及會眾" },
  joshua:     { name: "迦南士師", ally: "📯 約書亞與以色列士師" },
  kingdom:    { name: "大衛列王", ally: "👑 大衛王朝與先知門徒" },
  prophets:   { name: "先知歸回", ally: "🔥 守望先知與重修城垣百姓" },
  gospels:    { name: "四福音書", ally: "✝️ 主耶穌與十二使徒門徒" },
  acts:       { name: "使徒啟示錄", ally: "⛵ 初代教會使徒與得勝聖徒" }
};

function generateBattleFromCatalog(entry) {
  const [id, theater, ref, name, en, mapX, mapY, kind, heroId, theme, quote, foeName] = entry;
  const meta = THEATER_META[theater];
  const heroObj = BIBLICAL_HEROES[heroId] || BIBLICAL_HEROES.moses;
  const hc = HANDCRAFTED_120[id];

  const rows = hc.rows || 8;
  const cols = hc.cols || 8;
  const terrain = hc.t.slice();
  const player = JSON.parse(JSON.stringify(hc.p));
  const ai = JSON.parse(JSON.stringify(hc.a));
  if (ai[0]) ai[0].foeName = foeName;

  // 動態掃描棋盤上的應許立石標竿 (F) 座標
  const fZones = [];
  for (let r = 0; r < rows; r++) {
    for (let c = 0; c < cols; c++) {
      if (terrain[r][c] === "F") fZones.push([r, c]);
    }
  }
  if (kind === "capture" && fZones.length === 0) {
    fZones.push([0, 4]);
  }
  const fCoordStr = fZones.map(([zr, zc]) => `${String.fromCharCode(65 + zc)}${rows - zr}`).join(" 或 ");

  const objMap = {
    annihilate: {
      kind: "annihilate",
      text: `【專屬陣型：${hc.fName}】\n✅ 勝利條件：調度「${heroObj.name}」與精兵，擊破「${foeName}」的核心主帥，或全數化解敵方部隊。\n❌ 失敗條件：我方領袖主帥失守或部隊全數退場。`
    },
    capture: {
      kind: "capture",
      zones: fZones,
      need: 1,
      text: `【專屬陣型：${hc.fName}】\n✅ 勝利條件：突破「${foeName}」防線，派遣任意我方同行者踏上前方「📜 應許立石標竿 F（座標 ${fCoordStr}）」，或直接擊破敵方主帥。\n❌ 失敗條件：我方領袖主帥失守。`
    },
    defend: {
      kind: "defend",
      turns: 8,
      text: `【專屬陣型：${hc.fName}】\n✅ 勝利條件：面對「${foeName}」的圍困，堅守「⛺ 至聖所會幕 H」滿 8 個聖曆回合不失守，或主動出擊擊破敵方主帥。\n❌ 失敗條件：我方領袖主帥在 8 回合內被攻陷。`
    },
    breakthrough: {
      kind: "breakthrough",
      targetRow: 0,
      need: 1,
      text: `【專屬陣型：${hc.fName}】\n✅ 勝利條件：衝破「${foeName}」的封鎖，護送至少 1 名我方同行者抵達最北端應許邊界（第 ${rows} 橫列 🌈），或擊破敵方主帥。\n❌ 失敗條件：我方領袖主帥失守。`
    },
    evacuate: {
      kind: "evacuate",
      evacRow: 0,
      need: 2,
      text: `【專屬陣型：${hc.fName}】\n✅ 勝利條件：在「${foeName}」的攔截下，護送至少 2 隊我方船隻／同行者平安抵達最北端立約岸（第 ${rows} 橫列 🌈），或擊破敵方主帥。\n❌ 失敗條件：我方領袖主帥失守或剩餘部隊不足 2 隊。`
    }
  };

  if (id === 120) {
    objMap.annihilate.text = `【★第 120 篇史詩終章：${hc.fName}】\n✅ 勝利條件：12×12 宏大聖城沙盤！雙方隔著水晶玻璃海與生命河對峙。請善用神蹟與聖徒大軍，徹底擊破北方雙魔王核心「${foeName}」（F12 與 G12）以解鎖最高榮譽【👑 希伯來書的雲彩見證人】徽章！\n❌ 失敗條件：我方雙使徒主帥皆失守。`;
  }

  return {
    id, theater, ref, name, en, mapX, mapY, theme, quote,
    heroId, foeName,
    formationName: hc.fName,
    isHandcrafted: true,
    year: ref,
    location: `${meta.name} · ${ref}`,
    allies: `${heroObj.name}`,
    axis: foeName,
    difficulty: id === 120 ? 3 : ((id % 3) + 1),
    rows, cols, terrain,
    player, ai,
    objective: objMap[kind] || objMap.annihilate,
    history: `【經文出處】《${ref}》——「${quote}」\n【歷史對陣】本篇由「${heroObj.name}（${heroObj.title}）」親自領軍，迎戰聖經中的「${foeName}」。\n【地圖與勝負準則】「${hc.fName}」。點擊領袖可施放 1 次「${heroObj.skillName}」，踏上築壇處(a)或點擊「📖 庇哩亞問答」可累積信心呼求四大神蹟！`
  };
}

const BATTLES = CHAPTER_CATALOG.map(generateBattleFromCatalog);

/* ============ 5D. 庇哩亞聖經教育互動問答題庫（正統神學考釋版） ============ */
const BIBLE_QUIZ_BANK = [
  {
    q: "在《創世記》1:1-3 中，地是空虛混沌、淵面黑暗時，是誰運行在水面上，並說「要有光」？",
    opts: ["A. 摩西與亞倫", "B. 神的靈（耶和華造物之主）", "C. 亞伯拉罕", "D. 大衛王"],
    ans: 1,
    exp: "《創世記》1:2-3：「地是空虛混沌，淵面黑暗；神的靈運行在水面上。神說：『要有光』，就有了光。」"
  },
  {
    q: "在《創世記》22 章，亞伯拉罕在摩利亞山上築壇獻以撒時，神預備了一隻公羊代替他的兒子，亞伯拉罕給那地方起名叫什麼？",
    opts: ["A. 耶和華沙龍", "B. 耶和華以勒（意思說：在耶和華的山上必有預備）", "C. 伯特利", "D. 毗努伊勒"],
    ans: 1,
    exp: "《創世記》22:14：「亞伯拉罕給那地方起名叫『耶和華以勒』，直到今日人還說：『在耶和華的山上必有預備。』」"
  },
  {
    q: "在《創世記》32 章，雅各夜間在雅博渡口與神人較力直到黎明得著祝福，他的名字被改為什麼？",
    opts: ["A. 以色列（因為你與神與人較力，都得了勝）", "B. 以掃", "C. 約瑟", "D. 便雅憫"],
    ans: 0,
    exp: "《創世記》32:28：「那人說：『你的名不要再叫雅各，要叫以色列；因為你與神與人較力，都得了勝。』」"
  },
  {
    q: "在《出埃及記》14 章過紅海時，法老率領多少輛「特選的戰車」追趕以色列人？",
    opts: ["A. 一百輛", "B. 三百輛", "C. 六百輛特選戰車並埃及所有的戰車", "D. 一千輛"],
    ans: 2,
    exp: "《出埃及記》14:7：「並帶著六百輛特選的車和埃及所有的車，每輛都有車兵長。」"
  },
  {
    q: "在《出埃及記》17 章利非訂之戰中，當約書亞在山下爭戰時，是哪兩個人在山頂扶著摩西舉起的手？",
    opts: ["A. 迦勒與拿順", "B. 亞倫與戶珥", "C. 拿答與亞比戶", "D. 以利亞撒與以他瑪"],
    ans: 1,
    exp: "《出埃及記》17:12：「亞倫與戶珥扶著他的手，一個在這邊，一個在那邊，他的手就穩住，直到日落的時候。」"
  },
  {
    q: "在《約書亞記》6 章攻克耶利哥城時，以色列百姓在第七日清早繞城幾次後呼喊，城牆便塌陷？",
    opts: ["A. 一次", "B. 三次", "C. 七次", "D. 十二次"],
    ans: 2,
    exp: "《約書亞記》6:15：「第七日清早，黎明的時候，他們起來，照樣繞城七次；惟獨這日繞城七次。」"
  },
  {
    q: "在《士師記》7 章，基甸遵照神的指示篩選後，最終只帶多少名捧水舔水的勇士夜襲米甸營？",
    opts: ["A. 十二人", "B. 七十人", "C. 三百人", "D. 三千人"],
    ans: 2,
    exp: "《士師記》7:7：「耶和華對基甸說：『我要用這舔水的三百人拯救你們，將米甸人交在你手中。』」"
  },
  {
    q: "在《撒母耳記上》7:12，撒母耳立石在米斯巴和善的中間，起名叫什麼，意思說「到如今耶和華都幫助我們」？",
    opts: ["A. 以便以謝 (Ebenezer)", "B. 伯特利", "C. 吉甲", "D. 毗努伊勒"],
    ans: 0,
    exp: "《撒母耳記上》7:12：「撒母耳將一塊石頭立在米斯巴和善的中間，給石頭起名叫以便以謝，說：『到如今耶和華都幫助我們。』」"
  },
  {
    q: "《撒母耳記上》17 章中，牧童大衛在以拉谷迎戰歌利亞時，在溪中挑選了幾顆光滑石子？",
    opts: ["A. 一顆", "B. 三顆", "C. 五顆光滑石子", "D. 七顆"],
    ans: 2,
    exp: "《撒母耳記上》17:40：「手中拿杖，又在溪中挑選了五塊光滑石子，放在袋裡……手中拿著甩石的機弦，就去迎那非利士人。」"
  },
  {
    q: "《列王紀上》18 章迦密山上，先知以利亞獨自一人與王后耶洗別所供養的多少名巴力先知對決？",
    opts: ["A. 一百名", "B. 四百五十名巴力先知", "C. 七十名", "D. 一千名"],
    ans: 1,
    exp: "《列王紀上》18:22：「以利亞對眾民說：『作耶和華先知的只剩下我一個人；巴力的先知卻有四百五十個人。』」"
  },
  {
    q: "在《馬太福音》4 章曠野中，主耶穌面對魔鬼的三次試探，是以何種話語擊退仇敵？",
    opts: ["A. 呼喚十二營天使", "B. 引聖經的話說：「經上記著說……」", "C. 顯神蹟將石頭變餅", "D. 降下雷火"],
    ans: 1,
    exp: "《馬太福音》4:4,7,10：主耶穌三次皆引《申命記》聖言回答「經上記著說……」，顯明神的話語乃聖靈的寶劍。"
  },
  {
    q: "在《使徒行傳》16 章，保羅與西拉在歐洲哪一座城市的牢獄中，半夜禱告唱詩讚美神，地大震動監門全開？",
    opts: ["A. 雅典", "B. 腓立比", "C. 哥林多", "D. 以弗所"],
    ans: 1,
    exp: "《使徒行傳》16:25-26：「約在半夜，保羅和西拉禱告，唱詩讚美神……忽然，地大震動，甚至監牢的地基都搖動了，監門立刻全開。」"
  },
  {
    q: "在《啟示錄》12:11 中，天上有大聲音宣告：「弟兄勝過那古蛇大龍，是因什麼？」",
    opts: ["A. 因兵馬甲冑", "B. 因羔羊的血和自己所見證的道；他們雖至於死，也不愛惜性命", "C. 因深溝高壘", "D. 因金銀寶物"],
    ans: 1,
    exp: "《啟示錄》12:11：「弟兄勝過牠，是因羔羊的血和自己所見證的道。他們雖至於死，也不愛惜性命。」"
  }
];

function triggerBibleQuiz() {
  if (!state || state.over) return;
  BiblicalAudio.playHarpChord([440, 554.37, 659.25], 0.07);
  const b = state.battle;
  const useCustom = Math.random() < 0.45;
  let qObj;
  if (useCustom) {
    const heroName = BIBLICAL_HEROES[b.heroId].name;
    const wrongHeroes = Object.values(BIBLICAL_HEROES)
      .filter(h => h.id !== b.heroId)
      .sort(() => Math.random() - 0.5)
      .slice(0, 3)
      .map(h => h.name);
    const rawOpts = [heroName, ...wrongHeroes].sort(() => Math.random() - 0.5);
    const ansIdx = rawOpts.indexOf(heroName);
    qObj = {
      q: `【本章經文考釋 · ${b.ref}】在《${b.name}》篇章中，我們面對的歷史對手是「${b.foeName}」，請問親自領軍我方同行的聖經領袖是誰？`,
      opts: rawOpts.map((o, i) => `${String.fromCharCode(65 + i)}. ${o}`),
      ans: ansIdx,
      exp: `本章出自《${b.ref}》：「${b.quote}」，由「${heroName}（${BIBLICAL_HEROES[b.heroId].title}）」對陣「${b.foeName}」。`
    };
  } else {
    qObj = BIBLE_QUIZ_BANK[(b.id + state.turnNum) % BIBLE_QUIZ_BANK.length];
  }

  const optsHtml = qObj.opts.map((opt, idx) =>
    `<button class="quiz-opt-btn" data-idx="${idx}">${opt}</button>`
  ).join("");

  openModal(`
    <h2>📖 庇哩亞聖經查考問答（答對賜予 +3 信心）</h2>
    <p style="color:#ffe180;font-weight:700">${qObj.q}</p>
    <div id="quiz-opts-wrap" style="margin-top:12px">${optsHtml}</div>
    <div id="quiz-feedback" style="margin-top:12px;font-size:13.5px;line-height:1.7"></div>
  `, [{ label: "返回棋局", onClick: closeModal }]);

  document.querySelectorAll("#quiz-opts-wrap .quiz-opt-btn").forEach(btn => {
    btn.addEventListener("click", () => {
      const idx = +btn.dataset.idx;
      const fb = document.getElementById("quiz-feedback");
      document.querySelectorAll("#quiz-opts-wrap .quiz-opt-btn").forEach(bEl => bEl.disabled = true);
      if (idx === qObj.ans) {
        BiblicalAudio.playMiracleChime();
        state.faith = Math.min(10, state.faith + 3);
        userStats.quizCorrect = (userStats.quizCorrect || 0) + 1;
        saveUserStats();
        updateAllPanels();
        addLog(`📖 【庇哩亞考釋正確】甘心領受真道！獲得 +3 點信心值！`, "good");
        fb.innerHTML = `<div style="color:var(--good);font-weight:800">✅ 考釋正確！信心值 +3（當前 ${state.faith}/10）</div><div style="color:var(--text);margin-top:4px">${qObj.exp}</div>`;
      } else {
        BiblicalAudio.playHarpNote(246.94, 0.5);
        fb.innerHTML = `<div style="color:var(--danger);font-weight:800">❌ 回答未契合經文，查考聖經使我們更有屬天智慧！</div><div style="color:var(--text);margin-top:4px">經文正解：${qObj.exp}</div>`;
      }
    });
  });
}

/* ============ 6. 存檔與雲彩見證人狀態管理 ============ */
const STORAGE_KEY = "BIBLICAL_CHESS_120_SOLEMN_V5";
let userStats = {
  wonIds: [],
  miraclesUsed: 0,
  heroSkillsUsed: 0,
  sabbathsKept: 0,
  quizCorrect: 0,
  bookmarks: {}
};

function loadUserStats() {
  try {
    const raw = localStorage.getItem(STORAGE_KEY) || localStorage.getItem("BIBLICAL_CHESS_120_SAVE_V4");
    if (raw) Object.assign(userStats, JSON.parse(raw));
  } catch (e) {}
}
function saveUserStats() {
  try { localStorage.setItem(STORAGE_KEY, JSON.stringify(userStats)); } catch (e) {}
}

function getCurrentRank() {
  const n = userStats.wonIds.length;
  let cur = BIBLICAL_RANKS[0];
  for (const r of BIBLICAL_RANKS) if (n >= r.min) cur = r;
  return cur;
}

function updateTopRankPill() {
  const pill = document.getElementById("btn-honors-map");
  if (!pill) return;
  const rk = getCurrentRank();
  pill.innerHTML = `${rk.badge} <b>${rk.title}</b> <span style="color:var(--accent)">(${userStats.wonIds.length}/120 卷)</span>`;
}

/* ============ 7. 戰棋核心規則與全向尋路引擎 ============ */
let state = null;
let selectedDifficulty = 2;
let selectedLoadout = "standard";

function inBounds(st, r, c) { return r >= 0 && r < st.rows && c >= 0 && c < st.cols; }
function terrAt(st, r, c) { return (st.battle.terrain[r] && st.battle.terrain[r][c]) || "."; }
function coordName(st, r, c) { return `${String.fromCharCode(65 + c)}${st.rows - r}`; }

function piecesOf(st, side) {
  const arr = [];
  for (let r = 0; r < st.rows; r++) for (let c = 0; c < st.cols; c++) {
    const p = st.board[r][c];
    if (p && p.side === side) arr.push(p);
  }
  return arr;
}

function findKing(st, side) {
  for (const p of piecesOf(st, side)) if (PIECE_DEFS[p.type].isKing) return p;
  return null;
}

function canStand(def, tChar) {
  const t = TERRAIN[tChar] || TERRAIN["."];
  if (tChar === "L") return true; // 太初真光大道所有單位皆可通行
  if (def.domain === "air") return true;
  if (t.void) return false; // 混沌深淵僅空中屬天信使可跨越
  if (def.domain === "water") return !!t.water || tChar === "p" || tChar === "b" || tChar === "F" || tChar === "H";
  if (t.water && !t.land) return false;
  if (tChar === "x" && !def.ignoreMine) return false;
  if (t.infOnly && def.vehicle) return false;
  if (t.noVehicle && def.vehicle) return false;
  return true;
}

function canCapture(attDef, defPiece, destTerr) {
  if (attDef.noAttack) return false;
  const defDef = PIECE_DEFS[defPiece.type];
  if (attDef.noAir && defDef.domain === "air") return false;
  if (attDef.waterOnly && !TERRAIN[destTerr]?.water) return false;
  return canStand(attDef, destTerr);
}

function rawMovesFor(st, p) {
  const def = PIECE_DEFS[p.type];
  const moves = [];
  const r = p.r, c = p.c;

  const tryCell = (nr, nc, mode = "both") => {
    if (!inBounds(st, nr, nc)) return false;
    const t = terrAt(st, nr, nc);
    const occ = st.board[nr][nc];
    if (!occ) {
      if (mode !== "capOnly" && canStand(def, t)) moves.push({ r: nr, c: nc, cap: false });
      return canStand(def, t);
    } else {
      if (occ.side !== p.side && mode !== "moveOnly" && canCapture(def, occ, t)) {
        moves.push({ r: nr, c: nc, cap: true });
      }
      return false;
    }
  };

  const slide = (dirs) => {
    for (const [dr, dc] of dirs) {
      for (let step = 1; step < Math.max(st.rows, st.cols); step++) {
        if (!tryCell(r + dr * step, c + dc * step)) break;
      }
    }
  };

  if (def.move === "king") {
    for (let dr = -1; dr <= 1; dr++) for (let dc = -1; dc <= 1; dc++) {
      if (dr || dc) tryCell(r + dr, c + dc);
    }
  } else if (def.move === "knight") {
    for (const [dr, dc] of [[-2,-1],[-2,1],[-1,-2],[-1,2],[1,-2],[1,2],[2,-1],[2,1]]) {
      tryCell(r + dr, c + dc);
    }
  } else if (def.move === "rook") {
    slide([[-1,0],[1,0],[0,-1],[0,1]]);
  } else if (def.move === "bishop") {
    slide([[-1,-1],[-1,1],[1,-1],[1,1]]);
  } else if (def.move === "queen") {
    slide([[-1,0],[1,0],[0,-1],[0,1],[-1,-1],[-1,1],[1,-1],[1,1]]);
  } else if (def.move === "pawn") {
    const dirVec = (p.side === "player" ? st.battle.pDir : st.battle.aDir) || (p.side === "player" ? [-1, 0] : [1, 0]);
    const [dr, dc] = dirVec;
    if (tryCell(r + dr, c + dc, "moveOnly")) {
      const distMoved = Math.abs(r - (p.startR ?? r)) + Math.abs(c - (p.startC ?? c));
      if (distMoved === 0) tryCell(r + dr * 2, c + dc * 2, "moveOnly");
    }
    if (dr !== 0) {
      tryCell(r + dr, c - 1, "capOnly");
      tryCell(r + dr, c + 1, "capOnly");
    } else {
      tryCell(r - 1, c + dc, "capOnly");
      tryCell(r + 1, c + dc, "capOnly");
    }
  }
  return moves;
}

function legalMoves(st, p) {
  return rawMovesFor(st, p);
}

function computeThreatSet(st, enemySide) {
  const set = new Set();
  for (const p of piecesOf(st, enemySide)) {
    for (const m of rawMovesFor(st, p)) set.add(`${m.r},${m.c}`);
  }
  return set;
}

/* ============ 8. 全景聖地沙盤與 120 篇章篩選 ============ */
let activeTheaterFilter = "all";
let activeSearchQuery = "";

function renderWorldMapPins() {
  const gridG = document.getElementById("gridlines");
  if (gridG && !gridG.children.length) {
    let ghtml = "";
    for (let x = 100; x < 1000; x += 100) ghtml += `<line x1="${x}" y1="0" x2="${x}" y2="520"/>`;
    for (let y = 80; y < 520; y += 80) ghtml += `<line x1="0" y1="${y}" x2="1000" y2="${y}"/>`;
    gridG.innerHTML = ghtml;
  }

  const pinsG = document.getElementById("pins");
  const listEl = document.getElementById("battle-list-items");
  const q = activeSearchQuery.trim().toLowerCase();

  const filtered = BATTLES.filter(b => {
    if (activeTheaterFilter !== "all" && b.theater !== activeTheaterFilter) return false;
    const heroName = BIBLICAL_HEROES[b.heroId]?.name || "";
    if (q && !(
      b.name.toLowerCase().includes(q) ||
      b.ref.toLowerCase().includes(q) ||
      b.foeName.toLowerCase().includes(q) ||
      b.formationName.toLowerCase().includes(q) ||
      heroName.toLowerCase().includes(q)
    )) return false;
    return true;
  });

  pinsG.innerHTML = filtered.map(b => {
    const won = userStats.wonIds.includes(b.id) ? "won-pin" : "";
    const jx = b.mapX + ((b.id * 7) % 15) - 7;
    const jy = b.mapY + ((b.id * 11) % 15) - 7;
    return `<g class="pin th-${b.theater} ${won}" data-id="${b.id}" transform="translate(${jx},${jy})">
      <circle class="pin-ring" r="8"/>
      <circle class="pin-dot" r="4.8"/>
    </g>`;
  }).join("");

  listEl.innerHTML = filtered.map(b => {
    const won = userStats.wonIds.includes(b.id);
    const hero = BIBLICAL_HEROES[b.heroId];
    return `<button class="bl-item" data-id="${b.id}">
      <span class="bl-idx">#${String(b.id).padStart(3, "0")}</span>
      <div class="bl-main">
        <div class="bl-name">${won ? "✅ " : ""}${b.name}</div>
        <div class="bl-meta"><em class="bl-kind">${b.ref}</em> · 👑${hero.name.split(" ")[0]} vs ${b.foeName}</div>
      </div>
      <span class="bl-stars">${"★".repeat(b.difficulty)}</span>
    </button>`;
  }).join("");

  const hoverCard = document.getElementById("map-hover-card");
  pinsG.querySelectorAll(".pin").forEach(pin => {
    const id = +pin.dataset.id;
    const b = BATTLES.find(x => x.id === id);
    pin.addEventListener("mouseenter", (e) => {
      BiblicalAudio.playHarpNote(587.33, 0.25, 0, 0.05);
      hoverCard.innerHTML = `
        <div style="color:var(--accent);font-weight:800;font-size:14px">#${b.id} ${b.name}</div>
        <div style="color:#ffe180;font-size:11.5px;margin:2px 0">📖 ${b.ref} ｜ ${b.formationName}</div>
        <div style="color:#75d4a9;font-size:11.5px;margin-bottom:4px">👑 ${BIBLICAL_HEROES[b.heroId].name} ⚔️ 對陣：${b.foeName}</div>
        <div style="color:var(--text);font-size:12px;line-height:1.5">「${b.quote}」</div>
      `;
      hoverCard.classList.add("visible");
      const wrapRect = document.getElementById("map-wrap").getBoundingClientRect();
      const x = Math.min(wrapRect.width - 290, Math.max(12, e.clientX - wrapRect.left + 14));
      const y = Math.min(wrapRect.height - 130, Math.max(12, e.clientY - wrapRect.top - 20));
      hoverCard.style.left = x + "px";
      hoverCard.style.top = y + "px";
    });
    pin.addEventListener("mouseleave", () => hoverCard.classList.remove("visible"));
    pin.addEventListener("click", () => openBriefing(b));
  });

  listEl.querySelectorAll(".bl-item").forEach(btn => {
    const id = +btn.dataset.id;
    const b = BATTLES.find(x => x.id === id);
    btn.addEventListener("mouseenter", () => {
      const p = pinsG.querySelector(`.pin[data-id="${id}"]`);
      if (p) p.classList.add("lit");
    });
    btn.addEventListener("mouseleave", () => {
      const p = pinsG.querySelector(`.pin[data-id="${id}"]`);
      if (p) p.classList.remove("lit");
    });
    btn.addEventListener("click", () => openBriefing(b));
  });
}

/* ============ 9. 畫面二：經文導讀與出征配置 ============ */
function showScreen(id) {
  for (const s of ["screen-map", "screen-brief", "screen-game"]) {
    document.getElementById(s).classList.toggle("hidden", s !== id);
  }
}

function openBriefing(battle) {
  BiblicalAudio.playHarpChord([293.66, 369.99, 440], 0.07);
  showScreen("screen-brief");
  document.body.className = battle.theme || "theme-map";
  const hero = BIBLICAL_HEROES[battle.heroId];

  let miniCells = "";
  const pMap = new Map(battle.player.map(u => [`${u.r},${u.c}`, u]));
  const aMap = new Map(battle.ai.map(u => [`${u.r},${u.c}`, u]));
  for (let r = 0; r < battle.rows; r++) {
    for (let c = 0; c < battle.cols; c++) {
      const t = battle.terrain[r][c];
      const pu = pMap.get(`${r},${c}`), au = aMap.get(`${r},${c}`);
      let inner = "";
      if (pu) inner = `<div class="mini-unit player">${pieceIcon(pu.type)}</div>`;
      else if (au) inner = `<div class="mini-unit ai">${pieceIcon(au.type)}</div>`;
      miniCells += `<div class="mini-cell" style="background:${TERR_COLOR[t] || "var(--plain)"}">${inner}</div>`;
    }
  }

  const body = document.getElementById("brief-body");
  body.innerHTML = `
    <div id="brief-title-row">
      <h2>📜 第 ${battle.id} 篇：${battle.name} </h2>
      <span class="en">${battle.en} · 《${battle.ref}》</span>
    </div>
    <div class="brief-meta">👑 聖史領袖：<b style="color:#75d4a9">${hero.name}</b> ⚔️ 歷史對敵：<b style="color:#e87b7b">${battle.foeName}</b> ｜ 陣型：<b style="color:#ffe180">${battle.formationName}</b></div>

    <div class="scripture-quote-banner">
      「${battle.quote}」
      <small>—— 聖經《${battle.ref}》</small>
    </div>

    <div class="brief-cols">
      <div>
        <div class="brief-card">
          <h3>🕯️ 經文背景、對敵解析與聖地陣型</h3>
          <p>${battle.history}</p>
        </div>
        <div class="brief-card">
          <h3>👑 本章聖史領袖：${hero.name}（${hero.title}）</h3>
          <p><b>經文金句：</b>${hero.quote}（${hero.ref}）\n<b>主動神聖恩賜【${hero.skillName}】：</b>${hero.skillDesc}</p>
        </div>
        <div class="brief-card">
          <h3>🛡️ 選擇聖所同行軍裝編制</h3>
          <div class="loadout-pick">
            <div class="loadout-card ${selectedLoadout==="standard"?"selected":""}" data-lo="standard">
              <div class="lc-title">⚖️ 標準聖所編制</div>
              <div class="lc-desc">均衡配屬信德藤牌、聖靈寶劍與信心門徒，起始 4 點信心。</div>
            </div>
            <div class="loadout-card ${selectedLoadout==="faith"?"selected":""}" data-lo="faith">
              <div class="lc-title">✨ 信心代求編制</div>
              <div class="lc-desc">起始直接擁有 7 點高信心值！開局即可祈求分海、降嗎哪或日停。</div>
            </div>
            <div class="loadout-card ${selectedLoadout==="praise"?"selected":""}" data-lo="praise">
              <div class="lc-title">📯 頌讚前鋒編制</div>
              <div class="lc-desc">全體我方同行者開局自動蒙恩披戴「恩典神聖護盾」，堅立不移。</div>
            </div>
          </div>
        </div>
      </div>

      <div>
        <div class="brief-card">
          <h3>🗺️ 本章獨立地貌與勝負準則預覽 (${battle.rows}×${battle.cols})</h3>
          <div class="mini-preview-wrap">
            <div class="mini-board-grid" style="grid-template-columns:repeat(${battle.cols}, 22px)">${miniCells}</div>
            <div style="font-size:12.5px;color:var(--text);text-align:left;white-space:pre-line;background:rgba(0,0,0,.3);padding:8px 10px;border-radius:5px;border:1px solid var(--line)">${battle.objective.text}</div>
          </div>
        </div>
        <div class="brief-card">
          <h3>🔥 選擇試煉強度（對手 AI 智慧）</h3>
          <div class="ai-pick">
            <div class="ai-card ${selectedDifficulty===1?"selected":""}" data-diff="1">
              <div class="ai-name">🌱 曠野慕道</div>
              <div class="ai-stars">★☆☆</div>
              <div class="ai-desc">專注於靜心查經與體會聖經神學默想。</div>
            </div>
            <div class="ai-card ${selectedDifficulty===2?"selected":""}" data-diff="2">
              <div class="ai-name">🛡️ 剛強勇士</div>
              <div class="ai-stars">★★☆</div>
              <div class="ai-desc">對手懂得守護主帥與要隘，考驗戰術調度。</div>
            </div>
            <div class="ai-card ${selectedDifficulty===3?"selected":""}" data-diff="3">
              <div class="ai-name">👑 雲彩得勝者</div>
              <div class="ai-stars">★★★</div>
              <div class="ai-desc">深層歷史推演，必須穿戴神的全副軍裝方能克敵。</div>
            </div>
          </div>
        </div>
        <div style="text-align:center;margin-top:16px">
          <button class="btn big" id="btn-start-battle">📯 吹角展開聖約棋局</button>
        </div>
      </div>
    </div>
  `;

  body.querySelectorAll(".loadout-card").forEach(el => {
    el.addEventListener("click", () => {
      BiblicalAudio.playHarpNote(440, 0.35);
      selectedLoadout = el.dataset.lo;
      body.querySelectorAll(".loadout-card").forEach(c => c.classList.toggle("selected", c === el));
    });
  });
  body.querySelectorAll(".ai-card").forEach(el => {
    el.addEventListener("click", () => {
      BiblicalAudio.playHarpNote(523.25, 0.35);
      selectedDifficulty = +el.dataset.diff;
      body.querySelectorAll(".ai-card").forEach(c => c.classList.toggle("selected", c === el));
    });
  });
  document.getElementById("btn-start-battle").addEventListener("click", () => startBattle(battle));
}

/* ============ 10. 畫面三：棋局初始化、渲染與互動 ============ */
function startBattle(battle) {
  BiblicalAudio.playShofar();
  showScreen("screen-game");
  document.body.className = battle.theme || "theme-map";
  const bCopy = JSON.parse(JSON.stringify(battle));

  state = {
    battle: bCopy,
    rows: bCopy.rows,
    cols: bCopy.cols,
    board: Array.from({ length: bCopy.rows }, () => Array(bCopy.cols).fill(null)),
    turn: "player",
    turnNum: 1,
    faith: selectedLoadout === "faith" ? 7 : 4,
    heroSkillUsed: false,
    extraTurnPending: false,
    showThreat: false,
    hintMove: null,
    selected: null,
    legal: [],
    lastMove: null,
    captured: { player: [], ai: [] },
    historyStack: [],
    over: false
  };

  for (const u of bCopy.player) {
    state.board[u.r][u.c] = {
      type: u.type, side: "player", r: u.r, c: u.c, startR: u.r, startC: u.c,
      heroId: u.heroId || null,
      entrenched: selectedLoadout === "praise" || !!u.heroId
    };
  }
  for (const u of bCopy.ai) {
    state.board[u.r][u.c] = {
      type: u.type, side: "ai", r: u.r, c: u.c, startR: u.r, startC: u.c,
      foeName: u.foeName || null,
      entrenched: !!PIECE_DEFS[u.type].isKing
    };
  }

  document.getElementById("game-title").textContent = `📜 #${bCopy.id} ${bCopy.name}（${bCopy.ref}）`;
  document.getElementById("battle-log").innerHTML = "";
  addLog(`🕯️ 展開《${bCopy.ref}》：「${bCopy.quote}」`, "good");
  addLog(`👑 聖史領袖「${BIBLICAL_HEROES[bCopy.heroId].name}」迎戰「${bCopy.foeName}」（${bCopy.formationName}）！`, "cap");

  buildBoard();
  updateAllPanels();
}

function addLog(msg, cls = "") {
  const box = document.getElementById("battle-log");
  if (!box) return;
  const div = document.createElement("div");
  div.className = `lg ${cls}`;
  div.textContent = msg;
  box.prepend(div);
}

function buildBoard() {
  const st = state;
  if (!st) return;
  const boardEl = document.getElementById("board");
  const sq = Math.min(60, Math.floor((window.innerHeight - 230) / st.rows));
  boardEl.style.setProperty("--sq", sq + "px");
  boardEl.style.gridTemplateColumns = `repeat(${st.cols}, var(--sq))`;

  document.getElementById("row-labels").innerHTML = Array.from({ length: st.rows }, (_, r) =>
    `<span style="height:${sq}px">${st.rows - r}</span>`).join("");
  document.getElementById("col-labels").innerHTML = Array.from({ length: st.cols }, (_, c) =>
    `<span style="width:${sq}px">${String.fromCharCode(65 + c)}</span>`).join("");

  const threats = st.showThreat ? computeThreatSet(st, "ai") : new Set();

  let html = "";
  for (let r = 0; r < st.rows; r++) {
    for (let c = 0; c < st.cols; c++) {
      const t = terrAt(st, r, c);
      const tCls = TERR_CLASS[t] || "t-p";
      const isEvac = (st.battle.objective.kind === "evacuate" || st.battle.objective.kind === "breakthrough") && r === 0;
      const isSel = st.selected && st.selected.r === r && st.selected.c === c;
      const leg = st.legal.find(m => m.r === r && m.c === c);
      const isLast = st.lastMove && ((st.lastMove.fr === r && st.lastMove.fc === c) || (st.lastMove.tr === r && st.lastMove.tc === c));
      const isHintFrom = st.hintMove && st.hintMove.fr === r && st.hintMove.fc === c;
      const isHintTo = st.hintMove && st.hintMove.tr === r && st.hintMove.tc === c;

      let cls = `cell ${tCls}`;
      if (isEvac) cls += " zone-evac";
      if (isSel) cls += " sel";
      if (leg) cls += leg.cap ? " legalcap" : " legal";
      if (isLast) cls += " lastmove";
      if (threats.has(`${r},${c}`)) cls += " enemy-threat";
      if (isHintFrom) cls += " hint-from";
      if (isHintTo) cls += " hint-to";

      let mark = "";
      if (t === "F") mark = `<span class="mark" title="應許立石標竿 (F)：佔領目標">📜</span>`;
      else if (t === "H" || t === "B") mark = `<span class="mark">⛺</span>`;

      const p = st.board[r][c];
      let pieceHtml = "";
      if (p) {
        const heroMeta = p.heroId ? BIBLICAL_HEROES[p.heroId] : null;
        const foeBoss = p.foeName || (p.side === "ai" && PIECE_DEFS[p.type].isKing ? st.battle.foeName : null);
        let tagHtml = "";
        if (heroMeta) tagHtml = `<span class="hero-tag">👑${heroMeta.name.split(" ")[0]}</span>`;
        else if (foeBoss) tagHtml = `<span class="hero-tag">${foeBoss.slice(0, 6)}</span>`;

        const shieldBadge = p.entrenched ? `<span class="entrench-badge" title="神聖護盾：可抵擋一次衝擊">🛡️</span>` : "";
        const vetStar = p.promoted ? `<span class="vet-star">⭐</span>` : "";
        pieceHtml = `<div class="piece ${p.side} ${heroMeta ? "is-hero" : ""} ${foeBoss ? "is-foe-boss" : ""} ${p.side === "player" && st.turn === "player" ? "movable" : ""}">
          ${pieceIcon(p.type)}
          ${tagHtml}${shieldBadge}${vetStar}
        </div>`;
      }

      html += `<div class="${cls}" data-r="${r}" data-c="${c}"><div class="deco"></div>${mark}${pieceHtml}</div>`;
    }
  }
  boardEl.innerHTML = html;

  boardEl.querySelectorAll(".cell").forEach(cell => {
    cell.addEventListener("click", () => onCellClick(+cell.dataset.r, +cell.dataset.c));
  });
}

function onCellClick(r, c) {
  const st = state;
  if (!st || st.over || st.turn !== "player") return;
  st.hintMove = null;

  const leg = st.legal.find(m => m.r === r && m.c === c);
  if (st.selected && leg) {
    executeMove(st.selected, r, c);
    return;
  }

  const p = st.board[r][c];
  if (p && p.side === "player") {
    BiblicalAudio.playHarpNote(440 + (7 - r) * 35, 0.45);
    st.selected = p;
    st.legal = legalMoves(st, p);
    buildBoard();
    renderSelectedUnitCard(p);
  } else if (p && p.side === "ai") {
    BiblicalAudio.playHarpNote(293.66, 0.35);
    st.selected = null;
    st.legal = [];
    buildBoard();
    renderSelectedUnitCard(p);
  } else {
    st.selected = null;
    st.legal = [];
    buildBoard();
    renderSelectedUnitCard(null);
  }
}

function renderSelectedUnitCard(p) {
  const box = document.getElementById("sel-box");
  const badge = document.getElementById("sel-coord-badge");
  if (!p) {
    badge.textContent = "點擊棋盤棋子";
    box.innerHTML = "點擊棋盤上我方領袖或對手主將，可檢視其正統聖經背景與主動恩賜。";
    return;
  }
  const def = PIECE_DEFS[p.type];
  const t = TERRAIN[terrAt(state, p.r, p.c)];
  badge.textContent = `${coordName(state, p.r, p.c)} · ${t ? t.name : ""}`;

  if (p.side === "ai") {
    const isBoss = PIECE_DEFS[p.type].isKing;
    box.innerHTML = `
      <div style="color:#e87b7b;font-weight:800;font-size:13.5px">${isBoss ? `對手主將：${state.battle.foeName}` : `對陣方：${def.name}`} ${p.entrenched ? "🛡️重甲" : ""}</div>
      <div style="color:#ffe180;font-size:11px;margin:2px 0">戰術步法：${def.chess}</div>
      <div style="font-size:11.5px;color:var(--dim)">${isBoss ? `本篇《${state.battle.ref}》之核心歷史對敵。化解其前鋒並擊破主帥，即可成就本章聖役！` : def.desc}</div>
    `;
    return;
  }

  let heroHtml = "";
  if (p.heroId && BIBLICAL_HEROES[p.heroId]) {
    const h = BIBLICAL_HEROES[p.heroId];
    heroHtml = `
      <div style="margin-top:7px;padding-top:6px;border-top:1px dashed var(--line)">
        <div style="color:#ffe180;font-weight:800">👑 ${h.name} · 【${h.skillName}】</div>
        <div style="font-size:11px;color:var(--dim);margin:2px 0">${h.skillDesc}</div>
        <button class="hero-skill-btn" id="btn-cast-hero-skill" ${state.heroSkillUsed ? "disabled" : ""}>
          <span>✨ 施放聖史主動恩賜</span>
          <span>${state.heroSkillUsed ? "本局已施放" : "每局免費施放 1 次"}</span>
        </button>
      </div>
    `;
  }

  box.innerHTML = `
    <div style="display:flex;align-items:center;gap:8px;margin-bottom:4px">
      <b style="color:var(--accent);font-size:14px">${def.name}</b>
      <span style="color:#ffe180;font-size:11px">（${def.chess}）</span>
      ${p.entrenched ? `<span style="color:var(--good);font-size:11px">🛡️神聖護盾</span>` : ""}
    </div>
    <div style="font-size:11.5px;color:var(--dim)">${def.desc}</div>
    ${heroHtml}
  `;

  const btnHero = document.getElementById("btn-cast-hero-skill");
  if (btnHero) {
    btnHero.addEventListener("click", () => {
      if (state.heroSkillUsed || state.over || state.turn !== "player") return;
      saveSnapshot();
      const h = BIBLICAL_HEROES[p.heroId];
      const msg = h.cast(state, p);
      state.heroSkillUsed = true;
      userStats.heroSkillsUsed++;
      saveUserStats();
      addLog(msg, "good");
      buildBoard();
      updateAllPanels();
      renderSelectedUnitCard(p);
      checkVictoryAfterAction();
    });
  }
}

function saveSnapshot() {
  state.historyStack.push(JSON.stringify({
    terrain: state.battle.terrain,
    board: state.board,
    turnNum: state.turnNum,
    faith: state.faith,
    heroSkillUsed: state.heroSkillUsed,
    captured: state.captured
  }));
  if (state.historyStack.length > 12) state.historyStack.shift();
}

function executeMove(p, tr, tc) {
  const st = state;
  saveSnapshot();
  const fr = p.r, fc = p.c;
  const target = st.board[tr][tc];
  const def = PIECE_DEFS[p.type];

  if (target && target.entrenched) {
    BiblicalAudio.playHarpChord([392, 523.25], 0.06);
    target.entrenched = false;
    st.selected = null;
    st.legal = [];
    st.lastMove = { fr, fc, tr, tc };
    const tName = target.foeName || PIECE_DEFS[target.type].name;
    addLog(`🛡️ 我方破除了 ${coordName(st, tr, tc)}「${tName}」的外層防護！再擊一次即可化解！`, "cap");
    finishTurn("player");
    return;
  }

  if (target) {
    BiblicalAudio.playHarpChord([329.63, 440, 659.25], 0.05);
    st.captured[p.side].push(target.type);
    const tName = target.foeName || PIECE_DEFS[target.type].name;
    addLog(`⚔️ 我方「${def.name}」於 ${coordName(st, tr, tc)} 化解了「${tName}」！(+1 信心)`, "cap");
    st.faith = Math.min(10, st.faith + 1);
  } else {
    if (def.domain === "water" || terrAt(st, tr, tc) === "b") BiblicalAudio.playSeaWaves(0.5);
    else BiblicalAudio.playHarpNote(523.25 + (7 - tr) * 30, 0.5);
    addLog(`👣 「${def.name}」推進至 ${coordName(st, tr, tc)}。`);
  }

  st.board[fr][fc] = null;
  p.r = tr; p.c = tc;
  st.board[tr][tc] = p;
  st.lastMove = { fr, fc, tr, tc };
  st.selected = null;
  st.legal = [];

  if (terrAt(st, tr, tc) === "x" && def.ignoreMine) {
    const rows = st.battle.terrain.map(r => r.split(""));
    rows[tr][tc] = ".";
    st.battle.terrain = rows.map(r => r.join(""));
    addLog(`🧱 修垣工匠清除了 ${coordName(st, tr, tc)} 的曠野荊棘網羅！`, "good");
  }

  if (terrAt(st, tr, tc) === "a") {
    BiblicalAudio.playMiracleChime();
    st.faith = Math.min(10, st.faith + 2);
    p.entrenched = true;
    addLog(`🔥 在 ${coordName(st, tr, tc)} 築壇獻祭求告主名！獲得 +2 信心與神聖護盾！`, "good");
  }

  if (p.type === "infantry" && tr === 0) {
    BiblicalAudio.playMiracleChime();
    p.type = "td";
    p.promoted = true;
    p.entrenched = true;
    addLog(`🕊️ 信心門徒奔走抵達應許終點，領受聖靈恩賜晉升為「聖靈寶劍真道」！`, "good");
  }

  finishTurn("player");
}

function finishTurn(sideJustMoved) {
  const st = state;
  buildBoard();
  updateAllPanels();
  if (checkVictoryAfterAction()) return;

  if (sideJustMoved === "player") {
    if (st.extraTurnPending) {
      st.extraTurnPending = false;
      BiblicalAudio.playMiracleChime();
      addLog(`☀️ 【亞雅崙日頭停留神蹟生效】日頭停住！我方連續行動！`, "good");
      updateAllPanels();
      return;
    }
    st.turn = "ai";
    updateAllPanels();
    document.getElementById("thinking").classList.remove("hidden");
    setTimeout(runAiTurn, 420);
  } else {
    st.turn = "player";
    st.turnNum++;
    st.faith = Math.min(10, st.faith + 1);

    const dayIdx = (st.turnNum - 1) % 7;
    if (dayIdx === 6) {
      BiblicalAudio.playHarpChord([293.66, 369.99, 440, 587.33, 739.99], 0.09);
      st.faith = Math.min(10, st.faith + 2);
      userStats.sabbathsKept++;
      saveUserStats();
      for (const u of piecesOf(st, "player")) {
        const t = terrAt(st, u.r, u.c);
        if (t === "H" || t === "B" || t === "a" || t === "c") u.entrenched = true;
      }
      addLog(`🕯️ 【第七日 · 聖安息日降臨】全隊恢復 +2 信心，駐守聖所與會堂者自動披戴神聖護盾！`, "good");
    }
    document.getElementById("thinking").classList.add("hidden");
    buildBoard();
    updateAllPanels();
    checkVictoryAfterAction();
  }
}

/* ============ 11. 對手 AI 推演引擎 ============ */
function runAiTurn() {
  const st = state;
  if (!st || st.over) return;

  const pKing = findKing(st, "player");
  const allMoves = [];
  for (const p of piecesOf(st, "ai")) {
    for (const m of legalMoves(st, p)) {
      let score = (m.r - p.r) * 10 + (Math.random() * 8);
      const target = st.board[m.r][m.c];
      if (target) {
        score += PIECE_DEFS[target.type].value * (target.entrenched ? 0.35 : 1.25);
      }
      if (pKing && selectedDifficulty >= 2) {
        const distBefore = Math.abs(p.r - pKing.r) + Math.abs(p.c - pKing.c);
        const distAfter = Math.abs(m.r - pKing.r) + Math.abs(m.c - pKing.c);
        score += (distBefore - distAfter) * 14;
      }
      allMoves.push({ p, r: m.r, c: m.c, score });
    }
  }

  if (!allMoves.length) {
    finishTurn("ai");
    return;
  }

  allMoves.sort((a, b) => b.score - a.score);
  const chosen = selectedDifficulty === 1
    ? allMoves[Math.floor(Math.random() * Math.min(3, allMoves.length))]
    : allMoves[0];

  const { p, r: tr, c: tc } = chosen;
  const fr = p.r, fc = p.c;
  const target = st.board[tr][tc];

  if (target && target.entrenched) {
    target.entrenched = false;
    st.lastMove = { fr, fc, tr, tc };
    addLog(`🛡️ 我方「${PIECE_DEFS[target.type].name}」靠著神聖護盾抵禦了「${st.battle.foeName}」的衝擊！`, "good");
    finishTurn("ai");
    return;
  }

  if (target) {
    BiblicalAudio.playHarpNote(220, 0.55);
    st.captured.ai.push(target.type);
    addLog(`⚠️ 「${st.battle.foeName}」部隊阻滯了 ${coordName(st, tr, tc)} 的「${PIECE_DEFS[target.type].name}」！`, "cap");
  }

  st.board[fr][fc] = null;
  p.r = tr; p.c = tc;
  st.board[tr][tc] = p;
  st.lastMove = { fr, fc, tr, tc };

  finishTurn("ai");
}

/* ============ 12. 勝負判定、終章大圓滿與徽章解鎖 ============ */
function checkVictoryAfterAction() {
  const st = state;
  if (!st || st.over) return true;

  const pKing = findKing(st, "player");
  const aKing = findKing(st, "ai");
  const pUnits = piecesOf(st, "player");
  const aUnits = piecesOf(st, "ai");

  if (!pKing || pUnits.length === 0) {
    endGame(false, `我方聖史核心在「${st.battle.foeName}」的攔阻下失守，當重回主前得力！`);
    return true;
  }
  if (!aKing || aUnits.length === 0) {
    endGame(true, `憑著聖約信心與真理，成功克服歷史強敵「${st.battle.foeName}」！`);
    return true;
  }

  const obj = st.battle.objective;
  if (obj.kind === "capture" && obj.zones) {
    let held = 0;
    for (const [zr, zc] of obj.zones) {
      const occ = st.board[zr][zc];
      if (occ && occ.side === "player") held++;
    }
    if (held >= (obj.need || 1)) {
      endGame(true, "我方使者已踏上應許立石標竿 (以便以謝)！");
      return true;
    }
  } else if (obj.kind === "defend") {
    if (st.turnNum > (obj.turns || 8)) {
      endGame(true, `面對「${st.battle.foeName}」四面包圍，堅守至聖所會幕滿 ${obj.turns} 回合安然堅立！`);
      return true;
    }
  } else if (obj.kind === "breakthrough") {
    const reached = pUnits.filter(u => u.r === (obj.targetRow ?? 0)).length;
    if (reached >= (obj.need || 1)) {
      endGame(true, "同行者衝破重重阻礙，成功進駐應許邊界！");
      return true;
    }
  } else if (obj.kind === "evacuate") {
    if (pUnits.length < (obj.need || 2)) {
      endGame(false, `我方同行船隊／部隊不足 ${obj.need || 2} 隊，無法達成聖役託付！`);
      return true;
    }
    const reached = pUnits.filter(u => u.r === (obj.evacRow ?? 0)).length;
    if (reached >= (obj.need || 2)) {
      endGame(true, "立約使者平安抵達彩虹永約彼岸！");
      return true;
    }
  }
  return false;
}

function endGame(isWin, reason) {
  state.over = true;
  if (isWin) BiblicalAudio.playMiracleChime();
  else BiblicalAudio.playHarpChord([293.66, 261.63, 220], 0.12);

  const b = state.battle;
  if (isWin && !userStats.wonIds.includes(b.id)) {
    userStats.wonIds.push(b.id);
    saveUserStats();
    updateTopRankPill();
  }

  // 第 120 篇大圓滿專屬祝賀
  if (isWin && b.id === 120) {
    BiblicalAudio.playHarpChord([523.25, 659.25, 783.99, 1046.5, 1318.5, 1567.98], 0.08);
    openModal(`
      <div class="result-big win">👑 榮耀大圓滿 👑</div>
      <h2>🏛️ 恭喜您！完成《聖約經緯》全卷 120 篇永恆對局！</h2>
      <p style="color:#ffe180;font-weight:700">${reason}</p>
      <div class="scripture-quote-banner" style="margin-top:12px">
        「那美好的仗你已經打過了，當跑的路你已經跑盡了，所信的道你已經守住了！」（提摩太後書 4:7）
        <small>—— 《啟示錄 21-22章》聖城新耶路撒冷</small>
      </div>
      <p style="margin-top:10px">您已獲頒最高榮譽紀念章：<b>【👑 希伯來書的雲彩見證人（大圓滿）】</b>！您的信心腳蹤已銘刻於雲彩見證人館。</p>
    `, [
      { label: "🏛️ 進入雲彩見證人榮譽館", onClick: () => { closeModal(); showHonorsModal(); } },
      { label: "🗺 榮耀歸於神，返回聖地全景地圖", cls: "ghost", onClick: () => { closeModal(); renderWorldMapPins(); showScreen("screen-map"); } }
    ]);
    return;
  }

  const nextBattle = BATTLES.find(x => x.id === b.id + 1);
  openModal(`
    <div class="result-big ${isWin ? "win" : "lose"}">${isWin ? "哈利路亞 · 信心得勝" : "曠野磨練 · 重新得力"}</div>
    <h2>📜 第 ${b.id} 篇：${b.name}（${b.ref}）</h2>
    <p style="color:#ffe180;font-weight:700">${reason}</p>
    <div class="scripture-quote-banner" style="margin-top:12px">
      「${b.quote}」
      <small>—— 已獲取聖言金句卡《${b.ref}》</small>
    </div>
    <p>對陣紀錄：👑 <b>${BIBLICAL_HEROES[b.heroId].name}</b> vs <b>${b.foeName}</b>（歷時 ${state.turnNum} 聖曆回合）</p>
  `, [
    { label: "📖 參與本章庇哩亞問答", cls: "ghost", onClick: () => { closeModal(); state.over = false; triggerBibleQuiz(); state.over = true; } },
    { label: "↻ 重啟本篇", cls: "ghost", onClick: () => { closeModal(); startBattle(b); } },
    ...(nextBattle ? [{ label: `➡️ 下一篇：#${nextBattle.id} ${nextBattle.name}`, onClick: () => { closeModal(); openBriefing(nextBattle); } }] : []),
    { label: "🗺 返回全景地圖", cls: "ghost", onClick: () => { closeModal(); renderWorldMapPins(); showScreen("screen-map"); } }
  ]);
}

/* ============ 13. 右側屬靈控制台更新 ============ */
function updateAllPanels() {
  const st = state;
  if (!st) return;

  const dayInfo = CREATION_DAYS[(st.turnNum - 1) % 7];
  const sabbathBar = document.getElementById("sabbath-bar");
  sabbathBar.classList.toggle("is-sabbath", dayInfo.day === 7);
  sabbathBar.innerHTML = `
    <span><b>🗓️ 第 ${st.turnNum} 聖曆回合（${dayInfo.name} · ${dayInfo.ref}）</b></span>
    <span style="color:#ffe180">${dayInfo.desc}</span>
  `;

  const ti = document.getElementById("turn-indicator");
  ti.className = st.turn === "player" ? "you" : "foe";
  ti.textContent = st.turn === "player"
    ? `🕊️ 聖約回合：👑 ${BIBLICAL_HEROES[st.battle.heroId].name}`
    : `⚔️ 敵陣推演：${st.battle.foeName}`;

  document.getElementById("faith-badge").textContent = `信心 ${st.faith} / 10`;
  document.getElementById("faith-bar-fill").style.width = `${(st.faith / 10) * 100}%`;
  document.getElementById("btn-miracle-manna").disabled = st.turn !== "player" || st.faith < 3;
  document.getElementById("btn-miracle-waters").disabled = st.turn !== "player" || st.faith < 4;
  document.getElementById("btn-miracle-shofar").disabled = st.turn !== "player" || st.faith < 5;
  document.getElementById("btn-miracle-gibeon").disabled = st.turn !== "player" || st.faith < 7;

  document.getElementById("obj-text").textContent = st.battle.objective.text;
  const pCount = piecesOf(st, "player").length;
  const aCount = piecesOf(st, "ai").length;
  document.getElementById("obj-progress").innerHTML = `
    <div class="pg-row"><span>👑 聖約方（${BIBLICAL_HEROES[st.battle.heroId].name.split(" ")[0]}）：</span><b class="good">${pCount} 隊</b></div>
    <div class="pg-row"><span>⚔️ 對陣方（${st.battle.foeName.slice(0, 10)}）：</span><b class="bad">${aCount} 隊</b></div>
    <div class="pg-row"><span>📐 陣型：</span><b class="acc">${st.battle.formationName.slice(0, 12)}</b></div>
  `;

  const usedTerr = [...new Set(st.battle.terrain.join("").split(""))];
  document.getElementById("terrain-legend").innerHTML = usedTerr.map(ch => {
    const t = TERRAIN[ch];
    return t ? `<div class="tl-item"><span class="tl-swatch" style="background:${TERR_COLOR[ch]}"></span><span>${t.name}</span></div>` : "";
  }).join("");

  const pUnits = piecesOf(st, "player");
  const aUnits = piecesOf(st, "ai");
  document.getElementById("forces-lists").innerHTML = `
    <div class="fl-side">
      <div class="fl-name">👑 ${st.battle.allies} (${pUnits.length})</div>
      <div class="fl-units fl-player">${pUnits.map(u => `<span title="${PIECE_DEFS[u.type].name}">${pieceIcon(u.type)}</span>`).join("")}</div>
    </div>
    <div class="fl-side">
      <div class="fl-name">⚔️ ${st.battle.axis} (${aUnits.length})</div>
      <div class="fl-units fl-ai">${aUnits.map(u => `<span title="${PIECE_DEFS[u.type].name}">${pieceIcon(u.type)}</span>`).join("")}</div>
    </div>
  `;

  document.getElementById("player-banner").innerHTML = `👑 <b>${st.battle.allies}</b> ｜ 已退敵：<span class="lost">${st.captured.player.map(t => pieceIcon(t)).join("") || "無"}</span>`;
  document.getElementById("ai-banner").innerHTML = `⚔️ <b>對手：${st.battle.axis}</b> ｜ 我方暫息：<span class="lost">${st.captured.ai.map(t => pieceIcon(t)).join("") || "無"}</span>`;
}

/* ============ 14. 彈窗與圖鑑系統 ============ */
function openModal(html, btns = [{ label: "關閉", onClick: closeModal }], wide = false) {
  const overlay = document.getElementById("modal-overlay");
  const box = document.getElementById("modal-box");
  box.classList.toggle("wide", wide);
  document.getElementById("modal-content").innerHTML = html;
  const btnWrap = document.getElementById("modal-btns");
  btnWrap.innerHTML = "";
  for (const b of btns) {
    const el = document.createElement("button");
    el.className = `btn ${b.cls || ""}`;
    el.textContent = b.label;
    el.addEventListener("click", b.onClick);
    btnWrap.appendChild(el);
  }
  overlay.classList.remove("hidden");
}

function closeModal() {
  document.getElementById("modal-overlay").classList.add("hidden");
}

function showCodexModal() {
  BiblicalAudio.playHarpNote(523.25, 0.4);
  const items = Object.entries(PIECE_DEFS).map(([k, d]) => `
    <div class="codex-item">
      <div class="ci-icon">${pieceIcon(k)}</div>
      <div>
        <div class="ci-name">${d.name}</div>
        <div class="ci-chess">${d.chess} · ${DOMAIN_NAME[d.domain]}</div>
        <div class="ci-desc">${d.desc}</div>
      </div>
    </div>
  `).join("");
  openModal(`
    <h2>🛡️ 神的全副軍裝 · 22 種聖約器物與異象圖鑑</h2>
    <p>「要穿戴神所賜的全副軍裝，就能抵擋魔鬼的詭計。」（以弗所書 6:11）</p>
    <div class="codex-grid">${items}</div>
  `, [{ label: "明白聖約軍裝", onClick: closeModal }], true);
}

function showHeroesModal() {
  BiblicalAudio.playHarpNote(587.33, 0.4);
  const items = Object.values(BIBLICAL_HEROES).map(h => `
    <div class="codex-item">
      <div class="ci-icon" style="font-size:20px">👑</div>
      <div>
        <div class="ci-name">${h.name} · <small style="color:#ffe180">${h.title}</small></div>
        <div class="ci-chess">主動恩賜：【${h.skillName}】（${h.ref}）</div>
        <div class="ci-desc">${h.skillDesc}<br><em style="color:var(--text)">${h.quote}</em></div>
      </div>
    </div>
  `).join("");
  openModal(`
    <h2>👑 聖經 36 位核心領袖與屬靈恩賜錄</h2>
    <p>自《創世記》「耶和華造物之靈」、先祖亞伯拉罕、摩西、約書亞、大衛，至新約「主耶穌基督」與諸位使徒，每卷篇章皆由專屬聖經領袖親自領軍！</p>
    <div class="codex-grid">${items}</div>
  `, [{ label: "關閉", onClick: closeModal }], true);
}

function showHonorsModal() {
  BiblicalAudio.playMiracleChime();
  const rk = getCurrentRank();
  const medalsHtml = BIBLICAL_MEDALS.map(m => {
    const ok = m.check(userStats);
    return `<div class="medal-card ${ok ? "unlocked" : ""}">
      <div class="medal-icon">${m.icon}</div>
      <div>
        <div style="font-weight:800;color:var(--accent);font-size:13px">${m.name}</div>
        <div style="font-size:11.5px;color:var(--dim)">${m.desc}</div>
      </div>
    </div>`;
  }).join("");

  openModal(`
    <h2>🏛️ 雲彩見證人館 · 聖史紀念徽章</h2>
    <p>當前屬靈身量：<b>${rk.badge} ${rk.title}</b> ｜ 已成聖卷：<b>${userStats.wonIds.length} / 120 篇</b> ｜ 庇哩亞答對：<b>${userStats.quizCorrect || 0} 題</b></p>
    <div class="medals-grid" style="margin-top:12px">${medalsHtml}</div>
  `, [{ label: "繼續奔跑天路", onClick: closeModal }], true);
}

function showBookmarksModal() {
  const curSave = userStats.bookmarks.slot1;
  openModal(`
    <h2>💾 聖卷書籤（存檔保存與讀取）</h2>
    <p>您的 120 卷聖史進程自動保存在瀏覽器本地快取中。您亦可將特定對局夾入聖卷書籤：</p>
    <div class="brief-card" style="margin-top:10px">
      <h3>🔖 聖卷夾頁書籤 #1</h3>
      <p>${curSave ? `已保存：第 ${curSave.battleId} 篇《${curSave.battleName}》· 第 ${curSave.turnNum} 回合` : "目前尚無書籤紀錄"}</p>
    </div>
  `, [
    ...(state && !state.over ? [{
      label: "📥 夾入當前書籤",
      onClick: () => {
        userStats.bookmarks.slot1 = {
          battleId: state.battle.id,
          battleName: state.battle.name,
          turnNum: state.turnNum,
          faith: state.faith,
          terrain: state.battle.terrain,
          board: state.board
        };
        saveUserStats();
        closeModal();
        addLog("💾 已將當前聖卷棋局夾入書籤！", "good");
      }
    }] : []),
    ...(curSave ? [{
      label: "📤 翻至書籤進度",
      onClick: () => {
        const b = BATTLES.find(x => x.id === curSave.battleId);
        if (b) {
          closeModal();
          startBattle(b);
          state.turnNum = curSave.turnNum;
          state.faith = curSave.faith;
          state.battle.terrain = curSave.terrain;
          state.board = curSave.board;
          buildBoard();
          updateAllPanels();
          addLog("📖 已從聖卷書籤重啟進程！", "good");
        }
      }
    }] : []),
    { label: "關閉", cls: "ghost", onClick: closeModal }
  ]);
}

function showHelpModal() {
  openModal(`
    <h2>❔ 聖約經緯 · 戰術與神學教育指南</h2>
    <h3>1. 🌌 120 卷地貌與聖史勝負準則</h3>
    <p>・全 120 關每一關的地貌、雙方陣容與對敵皆依據正統聖經歷史雕琢！
    ・在右側「🎯 本章勝負準則與經文目標」面板中，清楚載明【✅ 勝利條件】（擊退主帥、踏上指定座標之應許標竿 F、堅守會幕、突破彼岸等）與【❌ 失敗條件】。</p>
    <h3>2. 👑 36 位聖史領袖專屬恩賜</h3>
    <p>點擊棋盤上帶有皇冠標籤的我方領袖，每局可免費施放 1 次主動神蹟（如摩西分海、約書亞吹號塌牆、大衛五顆溪石、以西結枯骨成軍、主基督平靜風浪）。</p>
    <h3>3. ✨ 四大動態神蹟介入與庇哩亞查經系統</h3>
    <p>對局中進駐「🔥 築壇處 (a)」或點擊「📖 庇哩亞問答」答對聖經考釋問題可獲 +3 點信心值，隨時祈求「🍞 嗎哪與五餅二魚」、「🌊 分開紅海／約旦河」、「📯 耶利哥吹角塌牆」與「☀️ 亞雅崙日頭停留」！</p>
  `, [{ label: "敬聆受教", onClick: closeModal }]);
}

/* ============ 15. 事件監聽綁定與全向拓撲重構執行 ============ */
function initEvents() {
  document.getElementById("btn-audio-toggle").addEventListener("click", () => BiblicalAudio.toggle());
  document.getElementById("btn-audio-game").addEventListener("click", () => BiblicalAudio.toggle());
  document.getElementById("btn-codex-map").addEventListener("click", showCodexModal);
  document.getElementById("btn-heroes-map").addEventListener("click", showHeroesModal);
  document.getElementById("btn-honors-map").addEventListener("click", showHonorsModal);
  document.getElementById("btn-saves-map").addEventListener("click", showBookmarksModal);
  document.getElementById("btn-help-map").addEventListener("click", showHelpModal);

  document.querySelectorAll("#bl-tabs .bl-tab, .map-legend-item").forEach(el => {
    el.addEventListener("click", () => {
      BiblicalAudio.playHarpNote(493.88, 0.3);
      activeTheaterFilter = el.dataset.th || "all";
      document.querySelectorAll("#bl-tabs .bl-tab").forEach(t => t.classList.toggle("active", t.dataset.th === activeTheaterFilter));
      renderWorldMapPins();
    });
  });
  document.getElementById("bl-search").addEventListener("input", (e) => {
    activeSearchQuery = e.target.value;
    renderWorldMapPins();
  });

  const svgMap = document.getElementById("worldmap");
  document.getElementById("btn-zoom-canaan").addEventListener("click", () => svgMap.setAttribute("viewBox", "510 260 220 220"));
  document.getElementById("btn-zoom-all").addEventListener("click", () => svgMap.setAttribute("viewBox", "0 0 1000 520"));

  document.getElementById("btn-brief-back").addEventListener("click", () => {
    document.body.className = "theme-map";
    showScreen("screen-map");
  });
  document.getElementById("btn-game-back").addEventListener("click", () => {
    document.body.className = "theme-map";
    renderWorldMapPins();
    showScreen("screen-map");
  });

  document.getElementById("btn-quiz-game").addEventListener("click", triggerBibleQuiz);
  document.getElementById("btn-tac-quiz").addEventListener("click", triggerBibleQuiz);

  document.getElementById("btn-scripture-game").addEventListener("click", () => {
    if (!state) return;
    const b = state.battle;
    openModal(`
      <h2>📜 《${b.ref}》· ${b.name}</h2>
      <div class="scripture-quote-banner">「${b.quote}」<small>—— ${b.ref}</small></div>
      <p>${b.history}</p>
    `);
  });
  document.getElementById("btn-codex-game").addEventListener("click", showCodexModal);
  document.getElementById("btn-saves-game").addEventListener("click", showBookmarksModal);
  document.getElementById("btn-restart").addEventListener("click", () => {
    if (state) startBattle(BATTLES.find(x => x.id === state.battle.id));
  });

  // 四大動態信心神蹟按鈕
  document.getElementById("btn-miracle-manna").addEventListener("click", () => {
    if (!state || state.turn !== "player" || state.faith < 3) return;
    BiblicalAudio.playMiracleChime();
    saveSnapshot();
    state.faith -= 3;
    userStats.miraclesUsed++;
    saveUserStats();
    for (const p of piecesOf(state, "player")) p.entrenched = true;
    addLog("🍞 【神蹟：嗎哪與五餅二魚】全體同行者蒙恩披戴「神聖護盾」！", "good");
    buildBoard();
    updateAllPanels();
  });

  document.getElementById("btn-miracle-waters").addEventListener("click", () => {
    if (!state || state.turn !== "player" || state.faith < 4) return;
    BiblicalAudio.playSeaWaves(1.4);
    saveSnapshot();
    state.faith -= 4;
    userStats.miraclesUsed++;
    saveUserStats();
    const rows = state.battle.terrain.map(r => r.split(""));
    let parted = 0;
    for (let r = 0; r < state.rows; r++) for (let c = 0; c < state.cols; c++) {
      if ((rows[r][c] === "~" || rows[r][c] === "r" || rows[r][c] === "g") && !state.board[r][c]) {
        rows[r][c] = "b"; parted++;
      }
    }
    state.battle.terrain = rows.map(r => r.join(""));
    addLog(`🌊 【神蹟：分開紅海／約旦河】大風吹起！${parted} 處水域沼澤立起為乾地走廊(b)！`, "good");
    buildBoard();
    updateAllPanels();
  });

  document.getElementById("btn-miracle-shofar").addEventListener("click", () => {
    if (!state || state.turn !== "player" || state.faith < 5) return;
    BiblicalAudio.playShofar();
    saveSnapshot();
    state.faith -= 5;
    userStats.miraclesUsed++;
    saveUserStats();
    const rows = state.battle.terrain.map(r => r.split(""));
    let cleared = 0;
    for (let r = 0; r < state.rows; r++) for (let c = 0; c < state.cols; c++) {
      if (rows[r][c] === "u" || rows[r][c] === "x" || rows[r][c] === "t") { rows[r][c] = "."; cleared++; }
    }
    state.battle.terrain = rows.map(r => r.join(""));
    addLog(`📯 【神蹟：耶利哥吹角塌牆】祭司吹響羊角號！${cleared} 處石牆、廢墟與荊棘化為平坦！`, "good");
    buildBoard();
    updateAllPanels();
  });

  document.getElementById("btn-miracle-gibeon").addEventListener("click", () => {
    if (!state || state.turn !== "player" || state.faith < 7) return;
    BiblicalAudio.playMiracleChime();
    saveSnapshot();
    state.faith -= 7;
    state.extraTurnPending = true;
    userStats.miraclesUsed++;
    saveUserStats();
    addLog("☀️ 【神蹟：亞雅崙日頭停留】禱告蒙悅納，日頭停住！我方獲得連續行動回合！", "good");
    updateAllPanels();
  });

  document.getElementById("btn-tac-undo").addEventListener("click", () => {
    if (!state || !state.historyStack.length || state.turn !== "player") return;
    BiblicalAudio.playHarpNote(392, 0.35);
    const prev = JSON.parse(state.historyStack.pop());
    state.battle.terrain = prev.terrain;
    state.board = prev.board;
    state.turnNum = prev.turnNum;
    state.faith = prev.faith;
    state.heroSkillUsed = prev.heroSkillUsed;
    state.captured = prev.captured;
    state.selected = null;
    state.legal = [];
    buildBoard();
    updateAllPanels();
    addLog("↩ 已回溯至上一戰步。");
  });

  document.getElementById("btn-tac-threat").addEventListener("click", (e) => {
    if (!state) return;
    BiblicalAudio.playHarpNote(440, 0.25);
    state.showThreat = !state.showThreat;
    e.currentTarget.classList.toggle("active", state.showThreat);
    buildBoard();
  });

  document.getElementById("btn-tac-hint").addEventListener("click", () => {
    if (!state || state.turn !== "player") return;
    BiblicalAudio.playHarpChord([440, 554.37, 659.25], 0.06);
    let best = null, bestScore = -9999;
    for (const p of piecesOf(state, "player")) {
      for (const m of legalMoves(state, p)) {
        let sc = (p.r - m.r) * 15;
        const tgt = state.board[m.r][m.c];
        if (tgt) sc += PIECE_DEFS[tgt.type].value;
        if (sc > bestScore) { bestScore = sc; best = { fr: p.r, fc: p.c, tr: m.r, tc: m.c, p }; }
      }
    }
    if (best) {
      state.hintMove = best;
      buildBoard();
      addLog(`💡 屬靈默想：調度 ${coordName(state, best.fr, best.fc)} 的「${PIECE_DEFS[best.p.type].name}」前往 ${coordName(state, best.tr, best.tc)}。`, "good");
    }
  });

  // 全向空間拓撲自動對齊演算法
  BATTLES.forEach(b => {
    if (b.id === 1 || b.id === 120) return;
    const isNaval = [3, 10, 56, 65, 69, 74, 90, 101, 104, 111].includes(b.id);
    if ([13, 29, 47, 65, 74, 101, 111].includes(b.id)) {
      b.pDir = [0, 1]; b.aDir = [0, -1]; b.targetEdge = "east";
    } else if ([4, 8, 21, 52, 57, 62, 98, 104].includes(b.id)) {
      b.pDir = [0, -1]; b.aDir = [0, 1]; b.targetEdge = "west";
    } else if ([18, 20, 24, 28, 36, 67, 77, 84, 91].includes(b.id)) {
      b.pDir = [1, 0]; b.aDir = [-1, 0]; b.targetEdge = "south";
    } else {
      b.pDir = [-1, 0]; b.aDir = [1, 0]; b.targetEdge = "north";
    }
  });
}

// 啟動全卷遊戲
loadUserStats();
updateTopRankPill();
renderWorldMapPins();
initEvents();



















































/* ============ 120 關空間拓撲、非對稱經文地貌與全向戰術佈陣徹底重構引擎 ============ */
(function() {
  if (typeof BATTLES === "undefined" || typeof PIECE_DEFS === "undefined") return;

  const TOPOLOGY_BUILDERS = {
    west_to_east(id, heroId, isNaval) {
      const rows = (id === 13 || id === 74) ? 9 : 8;
      const cols = (id === 13 || id === 74) ? 10 : 8;
      const midC = Math.floor(cols / 2);
      const grid = Array.from({ length: rows }, (_, r) =>
        Array.from({ length: cols }, (__, c) => {
          const h = (id * 31 + r * 17 + c * 23) % 100;
          if (isNaval) return (c === 0 || c === cols - 1) ? "p" : (h < 22 ? "r" : "~");
          if (c >= midC - 1 && c <= midC) {
            if (r === Math.floor(rows / 2) || r === (id % (rows - 2)) + 1) return "b";
            return "~";
          }
          if (h < 15) return "m";
          if (h < 28) return "f";
          if (h < 38) return "t";
          return ".";
        })
      );
      const pr = Math.floor(rows / 2) + ((id % 3) - 1);
      const ar = Math.floor(rows / 2) - ((id % 3) - 1);
      grid[pr][0] = "H";
      grid[ar][cols - 1] = "B";
      grid[1][cols - 2] = "F";
      grid[rows - 2][cols - 2] = "F";
      grid[Math.max(1, pr - 2)][2] = "a";

      const kType = isNaval ? "flagship" : "hq";
      const p = [
        P(kType, pr, 0, heroId),
        P(isNaval ? "battleship" : "td", Math.max(0, pr - 1), 1),
        P(isNaval ? "carrier" : "tank", Math.min(rows - 1, pr + 1), 1),
        P(isNaval ? "cruiser" : "katyusha", Math.max(0, pr - 2), 0),
        P(isNaval ? "destroyer" : "artillery", Math.min(rows - 1, pr + 2), 0),
        P(isNaval ? "mtb" : "commando", Math.max(1, pr - 2), 2),
        P(isNaval ? "sub" : "commando", Math.min(rows - 2, pr + 2), 2),
        P(isNaval ? "transport" : "infantry", pr, 2),
        P("fighter", 0, 1)
      ];
      const a = [
        P(kType, ar, cols - 1),
        P(isNaval ? "battleship" : "td", Math.max(0, ar - 1), cols - 2),
        P(isNaval ? "cruiser" : "tank", Math.min(rows - 1, ar + 1), cols - 2),
        P(isNaval ? "destroyer" : "artillery", Math.max(0, ar - 2), cols - 1),
        P(isNaval ? "destroyer" : "artillery", Math.min(rows - 1, ar + 2), cols - 1),
        P(isNaval ? "sub" : "commando", Math.max(1, ar - 2), cols - 3),
        P(isNaval ? "mtb" : "commando", Math.min(rows - 2, ar + 2), cols - 3),
        P(isNaval ? "sub" : "infantry", ar, cols - 3)
      ];
      return {
        rows, cols, grid, p, a,
        pDir: [0, 1], aDir: [0, -1], targetEdge: "east",
        topoLabel: "⬅️➡️ 西岸向東岸橫渡強攻陣"
      };
    },

    east_to_west(id, heroId, isNaval) {
      const rows = 8, cols = (id === 21 || id === 4) ? 10 : 8;
      const midC = Math.floor(cols / 2);
      const grid = Array.from({ length: rows }, (_, r) =>
        Array.from({ length: cols }, (__, c) => {
          const h = (id * 29 + r * 19 + c * 13) % 100;
          if (isNaval) return (c === 0 || c === cols - 1) ? "p" : (h < 20 ? "r" : "~");
          if (id === 21 || id === 8) {
            if (c === midC) return (r === 2 || r === 5) ? "b" : "~";
          }
          if (r === 3 || r === 4) return "=";
          if (h < 16) return "d";
          if (h < 28) return "m";
          if (h < 38) return "u";
          return ".";
        })
      );
      const pr = (id % 2 === 0) ? 2 : 5;
      const ar = (id % 2 === 0) ? 5 : 2;
      grid[pr][cols - 1] = "H";
      grid[ar][0] = "B";
      grid[1][1] = "F";
      grid[rows - 2][1] = "F";
      grid[pr][cols - 3] = "a";

      const kType = isNaval ? "flagship" : "hq";
      const p = [
        P(kType, pr, cols - 1, heroId),
        P(isNaval ? "transport" : "td", Math.max(0, pr - 1), cols - 2),
        P(isNaval ? "battleship" : "tank", Math.min(rows - 1, pr + 1), cols - 2),
        P(isNaval ? "carrier" : "katyusha", Math.max(0, pr - 2), cols - 1),
        P(isNaval ? "cruiser" : "commando", Math.min(rows - 1, pr + 2), cols - 2),
        P(isNaval ? "mtb" : "partisan", 1, cols - 3),
        P(isNaval ? "destroyer" : "mortar", rows - 2, cols - 3),
        P(isNaval ? "transport" : "infantry", pr, cols - 3)
      ];
      const a = [
        P(kType, ar, 0),
        P(isNaval ? "battleship" : "td", Math.max(0, ar - 1), 1),
        P(isNaval ? "cruiser" : "tank", Math.min(rows - 1, ar + 1), 1),
        P(isNaval ? "destroyer" : "artillery", Math.max(0, ar - 2), 0),
        P(isNaval ? "sub" : "commando", 1, 2),
        P(isNaval ? "mtb" : "commando", rows - 2, 2),
        P(isNaval ? "sub" : "infantry", ar, 2)
      ];
      return {
        rows, cols, grid, p, a,
        pDir: [0, -1], aDir: [0, 1], targetEdge: "west",
        topoLabel: "➡️⬅️ 東方向西方應許地推進陣"
      };
    },

    north_to_south(id, heroId) {
      const rows = (id === 24 || id === 28) ? 9 : 8;
      const cols = 8;
      const grid = Array.from({ length: rows }, (_, r) =>
        Array.from({ length: cols }, (__, c) => {
          const h = (id * 41 + r * 13 + c * 29) % 100;
          if (r <= 2) return (c === 3 || c === 4) ? "l" : (h < 50 ? "m" : "f");
          if (r >= rows - 2) return h < 35 ? "c" : "g";
          if (h < 15) return "t";
          if (h < 28) return "f";
          return ".";
        })
      );
      const pc = 2 + (id % 4);
      const ac = 5 - (id % 4);
      grid[0][pc] = "H";
      grid[rows - 1][ac] = "B";
      grid[rows - 2][1] = "F";
      grid[rows - 2][cols - 2] = "F";
      grid[2][pc] = "a";

      const p = [
        P("hq", 0, pc, heroId),
        P("td", 1, Math.max(0, pc - 1)),
        P("tank", 1, Math.min(cols - 1, pc + 1)),
        P("commando", 1, 0),
        P("commando", 1, cols - 1),
        P("partisan", 2, 1),
        P("partisan", 2, cols - 2),
        P("mortar", 0, Math.max(0, pc - 2)),
        P("infantry", 2, pc),
        P("fighter", 0, Math.min(cols - 1, pc + 2))
      ];
      const a = [
        P("hq", rows - 1, ac),
        P("armoredtrain", rows - 2, Math.max(0, ac - 1)),
        P("td", rows - 2, Math.min(cols - 1, ac + 1)),
        P("tank", rows - 2, 1),
        P("tank", rows - 2, cols - 2),
        P("artillery", rows - 1, Math.max(0, ac - 2)),
        P("artillery", rows - 1, Math.min(cols - 1, ac + 2)),
        P("infantry", rows - 3, ac)
      ];
      return {
        rows, cols, grid, p, a,
        pDir: [1, 0], aDir: [-1, 0], targetEdge: "south",
        topoLabel: "⬇️ 北方聖山高地向南俯衝陣"
      };
    },

    center_hold(id, heroId) {
      const rows = 9, cols = 9;
      const cr = 4, cc = 4;
      const grid = Array.from({ length: rows }, (_, r) =>
        Array.from({ length: cols }, (__, c) => {
          const dist = Math.abs(r - cr) + Math.abs(c - cc);
          if (dist === 0) return "H";
          if (dist === 1) return (r === cr || c === cc) ? "a" : "h";
          if (dist === 2) return (r === cr || c === cc) ? "=" : "t";
          const h = (id * 19 + r * 23 + c * 31) % 100;
          if (h < 14) return "u";
          if (h < 26) return "f";
          if (h < 35) return "d";
          return ".";
        })
      );
      grid[0][4] = "B";
      grid[0][0] = "F";
      grid[rows - 1][cols - 1] = "F";

      const p = [
        P("hq", cr, cc, heroId),
        P("td", cr - 1, cc),
        P("tank", cr + 1, cc),
        P("katyusha", cr, cc - 1),
        P("armoredtrain", cr, cc + 1),
        P("commando", cr - 1, cc - 1),
        P("commando", cr - 1, cc + 1),
        P("mortar", cr + 1, cc - 1),
        P("engineer", cr + 1, cc + 1)
      ];
      const a = [
        P("hq", 0, 4),
        P("td", 0, 1),
        P("td", 0, 7),
        P("tank", 8, 1),
        P("tank", 8, 7),
        P("artillery", 1, 0),
        P("artillery", 1, 8),
        P("commando", 7, 0),
        P("commando", 7, 8),
        P("infantry", 1, 4)
      ];
      return {
        rows, cols, grid, p, a,
        pDir: [-1, 0], aDir: [1, 0], targetEdge: "north",
        topoLabel: "🎯 中央聖所／山寨四面重圍反擊陣"
      };
    },

    outer_siege(id, heroId) {
      const rows = 9, cols = 9;
      const cr = 4, cc = 4;
      const grid = Array.from({ length: rows }, (_, r) =>
        Array.from({ length: cols }, (__, c) => {
          const dist = Math.max(Math.abs(r - cr), Math.abs(c - cc));
          if (r === cr && c === cc) return "B";
          if (dist === 1) return (r === cr - 1 && c === cc) ? "F" : "c";
          if (dist === 2) return (r === cr + 2 && c === cc) ? "u" : "t";
          return ".";
        })
      );
      grid[8][4] = "H";
      grid[8][2] = "a";
      grid[0][4] = "a";

      const p = [
        P("hq", 8, 4, heroId),
        P("katyusha", 8, 1),
        P("katyusha", 8, 7),
        P("td", 4, 0),
        P("tank", 4, 8),
        P("commando", 0, 2),
        P("commando", 0, 6),
        P("engineer", 7, 3),
        P("mortar", 7, 5),
        P("bomber", 0, 4)
      ];
      const a = [
        P("hq", cr, cc),
        P("td", cr - 1, cc - 1),
        P("td", cr - 1, cc + 1),
        P("tank", cr + 1, cc - 1),
        P("tank", cr + 1, cc + 1),
        P("artillery", cr, cc - 1),
        P("artillery", cr, cc + 1),
        P("infantry", cr + 1, cc)
      ];
      return {
        rows, cols, grid, p, a,
        pDir: [-1, 0], aDir: [1, 0], targetEdge: "north",
        topoLabel: "📯 四方繞城外圍合圍攻堅陣（敵居城心）"
      };
    },

    sw_to_ne_diagonal(id, heroId) {
      const rows = 8, cols = 8;
      const grid = Array.from({ length: rows }, (_, r) =>
        Array.from({ length: cols }, (__, c) => {
          if (r + c === 7) return "=";
          if (r + c === 6 || r + c === 8) return (id % 2 === 0) ? "." : "d";
          const h = (id * 37 + r * 11 + c * 19) % 100;
          if (h < 25) return "m";
          if (h < 42) return "f";
          if (h < 52) return "t";
          return "d";
        })
      );
      grid[7][0] = "H";
      grid[0][7] = "B";
      grid[1][6] = "F";
      grid[0][5] = "F";
      grid[5][2] = "a";

      const p = [
        P("hq", 7, 0, heroId),
        P("td", 6, 1),
        P("tank", 7, 2),
        P("katyusha", 5, 0),
        P("commando", 5, 1),
        P("commando", 6, 2),
        P("partisan", 4, 1),
        P("mortar", 6, 0),
        P("infantry", 5, 2),
        P("fighter", 7, 1)
      ];
      const a = [
        P("hq", 0, 7),
        P("td", 1, 6),
        P("tank", 0, 5),
        P("tank", 2, 7),
        P("artillery", 1, 7),
        P("commando", 2, 5),
        P("commando", 1, 4),
        P("infantry", 2, 6),
        P("infantry", 3, 5)
      ];
      return {
        rows, cols, grid, p, a,
        pDir: [-1, 0], aDir: [1, 0], targetEdge: "north",
        topoLabel: "📐 西南角向東北角斜向峽谷遠征陣"
      };
    },

    se_to_nw_diagonal(id, heroId) {
      const rows = 8, cols = 8;
      const grid = Array.from({ length: rows }, (_, r) =>
        Array.from({ length: cols }, (__, c) => {
          if (r === c) return "L";
          if (Math.abs(r - c) === 1) return ".";
          const h = (id * 43 + r * 17 + c * 29) % 100;
          if (h < 22) return "m";
          if (h < 38) return "u";
          if (h < 50) return "x";
          return "s";
        })
      );
      grid[7][7] = "H";
      grid[0][0] = "B";
      grid[1][1] = "F";
      grid[0][2] = "F";
      grid[5][5] = "a";

      const p = [
        P("hq", 7, 7, heroId),
        P("kamikaze", 6, 6),
        P("td", 7, 5),
        P("tank", 5, 7),
        P("commando", 5, 6),
        P("commando", 6, 5),
        P("engineer", 4, 6),
        P("mortar", 6, 7),
        P("infantry", 5, 5)
      ];
      const a = [
        P("hq", 0, 0),
        P("td", 1, 1),
        P("tank", 0, 2),
        P("tank", 2, 0),
        P("artillery", 1, 0),
        P("artillery", 0, 1),
        P("commando", 2, 2),
        P("infantry", 1, 2),
        P("infantry", 2, 1)
      ];
      return {
        rows, cols, grid, p, a,
        pDir: [-1, 0], aDir: [1, 0], targetEdge: "north",
        topoLabel: "📐 東南角向西北角真光走廊推進陣"
      };
    },

    ambush_pincer(id, heroId) {
      const rows = 9, cols = 9;
      const grid = Array.from({ length: rows }, (_, r) =>
        Array.from({ length: cols }, (__, c) => {
          if (c === 0 || c === cols - 1) return "f";
          if (c === 1 || c === cols - 2) return (r >= 2 && r <= 6) ? "m" : ".";
          if (r === 4 && (c === 3 || c === 5)) return "a";
          return ".";
        })
      );
      grid[8][4] = "H";
      grid[1][4] = "B";
      grid[0][4] = "F";

      const p = [
        P("hq", 8, 4, heroId),
        P("td", 7, 3),
        P("tank", 7, 5),
        P("commando", 2, 0),
        P("partisan", 3, 0),
        P("katyusha", 4, 0),
        P("commando", 2, 8),
        P("partisan", 3, 8),
        P("katyusha", 4, 8),
        P("infantry", 7, 4)
      ];
      const a = [
        P("hq", 1, 4),
        P("td", 3, 4),
        P("tank", 3, 3),
        P("tank", 3, 5),
        P("artillery", 2, 3),
        P("artillery", 2, 5),
        P("commando", 4, 4),
        P("infantry", 2, 4)
      ];
      return {
        rows, cols, grid, p, a,
        pDir: [-1, 0], aDir: [1, 0], targetEdge: "north",
        topoLabel: "🔥 左右高山雙翼伏兵三面合圍陣"
      };
    },

    twin_ridges_valley(id, heroId) {
      const rows = 9, cols = 9;
      const grid = Array.from({ length: rows }, (_, r) =>
        Array.from({ length: cols }, (__, c) => {
          if (r === 4) return (c === 2 || c === 4 || c === 6) ? "b" : "~";
          if (r === 3 || r === 5) return (c === 4) ? "b" : (c % 2 === 0 ? "s" : ".");
          if (r === 1 || r === 7) return (c >= 2 && c <= 6) ? "m" : "f";
          return ".";
        })
      );
      grid[8][2] = "H";
      grid[0][6] = "B";
      grid[0][2] = "F";
      grid[6][4] = "a";

      const p = [
        P("hq", 8, 2, heroId),
        P("artillery", 6, 2),
        P("artillery", 6, 6),
        P("td", 7, 4),
        P("tank", 6, 1),
        P("tank", 6, 7),
        P("commando", 5, 3),
        P("commando", 5, 5),
        P("infantry", 5, 4),
        P("fighter", 8, 6)
      ];
      const a = [
        P("hq", 0, 6),
        P("td", 3, 4),
        P("tank", 2, 2),
        P("tank", 2, 6),
        P("artillery", 1, 3),
        P("artillery", 1, 5),
        P("commando", 2, 4),
        P("infantry", 2, 1),
        P("infantry", 2, 7)
      ];
      return {
        rows, cols, grid, p, a,
        pDir: [-1, 0], aDir: [1, 0], targetEdge: "north",
        topoLabel: "🪨 兩山隔溪交錯對峙陣（主帥偏置）"
      };
    }
  };

  function assignTopologyForBattle(b) {
    const id = b.id;
    if (id === 1 || id === 120) return;

    const isNaval = [3, 10, 56, 65, 69, 74, 90, 101, 104, 111].includes(id);
    let built;

    if ([13, 29, 47, 65, 74, 101, 111].includes(id)) {
      built = TOPOLOGY_BUILDERS.west_to_east(id, b.heroId, isNaval);
    } else if ([4, 8, 21, 52, 57, 62, 98, 104].includes(id)) {
      built = TOPOLOGY_BUILDERS.east_to_west(id, b.heroId, isNaval);
    } else if ([18, 20, 24, 28, 36, 67, 77, 84, 91].includes(id)) {
      built = TOPOLOGY_BUILDERS.north_to_south(id, b.heroId);
    } else if ([2, 9, 12, 17, 30, 39, 43, 48, 50, 54, 55, 59, 76, 81, 85, 92, 94, 100, 105, 114, 117].includes(id)) {
      built = TOPOLOGY_BUILDERS.center_hold(id, b.heroId);
    } else if ([22, 41, 45, 58, 70, 82, 88, 109, 116, 119].includes(id)) {
      built = TOPOLOGY_BUILDERS.outer_siege(id, b.heroId);
    } else if ([5, 6, 15, 26, 33, 40, 51, 61, 68, 71, 79, 83, 89, 93, 97, 102, 112, 115].includes(id)) {
      built = TOPOLOGY_BUILDERS.sw_to_ne_diagonal(id, b.heroId);
    } else if ([7, 11, 14, 16, 19, 27, 32, 34, 35, 37, 44, 46, 53, 60, 63, 66, 72, 73, 75, 87, 95, 96, 99, 103, 106, 107, 108, 110, 118].includes(id)) {
      built = TOPOLOGY_BUILDERS.se_to_nw_diagonal(id, b.heroId);
    } else if ([23, 31, 49, 64, 78, 113].includes(id)) {
      built = TOPOLOGY_BUILDERS.ambush_pincer(id, b.heroId);
    } else {
      built = TOPOLOGY_BUILDERS.twin_ridges_valley(id, b.heroId);
    }

    b.rows = built.rows;
    b.cols = built.cols;
    b.terrain = built.grid.map(row => row.join(""));
    b.player = built.p;
    b.ai = built.a;
    if (b.ai[0]) b.ai[0].foeName = b.foeName;
    b.pDir = built.pDir;
    b.aDir = built.aDir;
    b.targetEdge = built.targetEdge;
    b.formationName = `${b.formationName.split("（")[0]} · ${built.topoLabel}`;

    const fZones = [];
    for (let r = 0; r < b.rows; r++) {
      for (let c = 0; c < b.cols; c++) {
        if (b.terrain[r][c] === "F") fZones.push([r, c]);
      }
    }
    const fCoordStr = fZones.map(([zr, zc]) => `${String.fromCharCode(65 + zc)}${b.rows - zr}`).join(" 或 ");
    const edgeNameMap = {
      north: `最北端邊界（第 ${b.rows} 橫列）`,
      south: `最南端邊界（第 1 橫列）`,
      east: `最東岸邊界（${String.fromCharCode(64 + b.cols)} 直行）`,
      west: `最西岸邊界（A 直行）`
    };
    const edgeDesc = edgeNameMap[b.targetEdge || "north"];

    if (b.objective.kind === "capture") {
      b.objective.zones = fZones;
      b.objective.text = `【${b.formationName}】\n✅ 勝利條件：突破「${b.foeName}」防線，派遣任意我方同行者踏上「📜 應許立石標竿 F（座標 ${fCoordStr}）」，或直接擊破敵方主帥。\n❌ 失敗條件：我方領袖主帥失守。`;
    } else if (b.objective.kind === "breakthrough") {
      b.objective.text = `【${b.formationName}】\n✅ 勝利條件：衝破「${b.foeName}」的封鎖，護送至少 1 名我方同行者抵達${edgeDesc}，或擊破敵方主帥。\n❌ 失敗條件：我方領袖主帥失守。`;
    } else if (b.objective.kind === "evacuate") {
      b.objective.text = `【${b.formationName}】\n✅ 勝利條件：在「${b.foeName}」攔截下，護送至少 2 隊我方同行者平安抵達${edgeDesc}，或擊破敵方主帥。\n❌ 失敗條件：我方主帥失守或部隊不足 2 隊。`;
    } else if (b.objective.kind === "defend") {
      b.objective.text = `【${b.formationName}】\n✅ 勝利條件：面對「${b.foeName}」四面進逼，堅守「⛺ 至聖所會幕 H」滿 8 回合不失守，或主動出擊擊破敵方主帥。\n❌ 失敗條件：我方領袖主帥在 8 回合內失守。`;
    } else {
      b.objective.text = `【${b.formationName}】\n✅ 勝利條件：運用本關獨特的空間地形與領袖恩賜，徹底擊破「${b.foeName}」的核心主帥！\n❌ 失敗條件：我方領袖主帥失守。`;
    }
  }

  BATTLES.forEach(assignTopologyForBattle);

  const origCheckVictory = window.checkVictoryAfterAction;
  window.checkVictoryAfterAction = function() {
    const st = state;
    if (!st || st.over) return true;
    const edge = st.battle.targetEdge || "north";
    const isAtEdge = (u) => {
      if (edge === "east") return u.c === st.cols - 1;
      if (edge === "west") return u.c === 0;
      if (edge === "south") return u.r === st.rows - 1;
      return u.r === 0;
    };
    const obj = st.battle.objective;
    if (obj.kind === "breakthrough" || obj.kind === "evacuate") {
      const pUnits = piecesOf(st, "player");
      const reached = pUnits.filter(isAtEdge).length;
      const need = obj.need || (obj.kind === "evacuate" ? 2 : 1);
      if (reached >= need) {
        endGame(true, `同行者已成功跨越險阻抵達目標應許岸（共 ${reached} 隊抵達）！`);
        return true;
      }
    }
    return origCheckVictory();
  };

  renderWorldMapPins();
  console.log("✅ [120關空間拓撲重構完成] 已全面啟用 9 大空間幾何結構！");
})();

</script>
</body>
</html>
