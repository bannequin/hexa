[hexa-bcnc.html](https://github.com/user-attachments/files/26533102/hexa-bcnc.html)
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="apple-mobile-web-app-title" content="Alptech">
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
<!-- MSAL — authentification Microsoft 365 -->
<script src="https://alcdn.msauth.net/browser/2.38.3/js/msal-browser.min.js"></script>
<title>HEXA — Groupe BCNC · Plateforme de gestion</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Syne:wght@600;700;800&family=DM+Sans:wght@300;400;500&family=Space+Grotesk:wght@400;500;600;700&display=swap');
*{box-sizing:border-box;margin:0;padding:0;}
:root{
  --cyan:#2abbda;--cl:#eaf9fc;--cb:#b3eaf4;
  --dark:#12161c;--mid:#3d4a56;--muted:#7a8d97;--hint:#aab8c0;
  --bg:#f0f4f7;--white:#fff;--bd:#e0e8ec;
  --red:#e04444;--rbg:#fff5f5;--rbd:#fca5a5;
  --ora:#c47d0a;--obg:#fff7e6;--obd:#f5d98a;
  --grn:#2a9d6f;--gbg:#eaf7f1;--gbd:#a8dfc5;
  --pur:#6c5ce7;--pbg:#f0eeff;--pbd:#c4b8f8;
  --num:'Space Grotesk',sans-serif;
}
body{font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--dark);min-height:100vh;}
.app{max-width:900px;margin:0 auto;padding:16px 16px 60px;}

/* ── HEADER ── */
.hdr{background:var(--white);border-radius:16px;border:1px solid var(--bd);padding:13px 20px;display:flex;align-items:center;justify-content:space-between;margin-bottom:16px;}
.logo{font-family:'Syne',sans-serif;font-size:22px;font-weight:800;letter-spacing:-0.5px;}
.logo em{color:var(--cyan);font-style:normal;}
.logo-sub{font-size:9px;color:var(--muted);letter-spacing:1.5px;text-transform:uppercase;margin-top:1px;}
.hdr-right{display:flex;align-items:center;gap:8px;}
.role-pill{font-size:11px;font-weight:500;padding:5px 12px;border-radius:20px;cursor:pointer;border:1.5px solid var(--bd);background:var(--white);color:var(--muted);font-family:'DM Sans',sans-serif;transition:all .2s;}
.role-pill.active-agence{background:var(--pbg);color:var(--pur);border-color:var(--pbd);}
.role-pill.active-tech{background:var(--cl);color:var(--cyan);border-color:var(--cb);}
.role-pill.active-dir{background:var(--obg);color:var(--ora);border-color:var(--obd);}

/* ── VIEWS ── */
.view{display:none;}
.view.active{display:block;animation:fi .2s ease;}
@keyframes fi{from{opacity:0;transform:translateY(6px);}to{opacity:1;transform:none;}}

/* ── ROLE SELECTOR ── */
/* ── HOME REDESIGN ── */
.home-hero{background:var(--white);border-radius:20px;padding:36px 28px 32px;margin-bottom:16px;position:relative;overflow:hidden;text-align:center;border:1px solid var(--bd);box-shadow:0 2px 12px rgba(30,44,58,.06);}
.home-hero::before{content:'';position:absolute;top:-80px;right:-80px;width:300px;height:300px;border-radius:50%;background:radial-gradient(circle,rgba(42,187,218,.06) 0%,transparent 70%);}
.home-hero::after{content:'';position:absolute;bottom:-60px;left:-40px;width:220px;height:220px;border-radius:50%;background:radial-gradient(circle,rgba(108,92,231,.04) 0%,transparent 70%);}
.home-hero-logo{height:80px;object-fit:contain;display:block;margin:0 auto 18px;position:relative;z-index:1;}
.home-platform{font-size:11px;color:var(--muted);letter-spacing:1.8px;text-transform:uppercase;margin-bottom:20px;position:relative;z-index:1;}
.home-divider{width:40px;height:2px;background:linear-gradient(90deg,transparent,var(--cyan),transparent);margin:0 auto 16px;position:relative;z-index:1;}
.home-prompt{font-size:13px;color:var(--hint);position:relative;z-index:1;}

/* ── ROLE CARDS REDESIGN ── */
.role-selector{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-bottom:20px;}
.role-card{background:var(--white);border-radius:16px;border:2px solid var(--bd);padding:22px 16px 18px;text-align:center;cursor:pointer;transition:all .22s;position:relative;overflow:hidden;}
.role-card::before{content:'';position:absolute;bottom:0;left:0;right:0;height:3px;opacity:0;transition:opacity .2s;}
.role-card:hover{transform:translateY(-3px);box-shadow:0 8px 24px rgba(0,0,0,.1);}
.role-card.agence::before{background:linear-gradient(90deg,var(--pur),#a855f7);}
.role-card.tech::before{background:linear-gradient(90deg,var(--cyan),#06b6d4);}
.role-card.dir::before{background:linear-gradient(90deg,var(--ora),#f59e0b);}
.role-card.agence:hover{border-color:var(--pur);}
.role-card.agence:hover::before{opacity:1;}
.role-card.tech:hover{border-color:var(--cyan);}
.role-card.tech:hover::before{opacity:1;}
.role-card.dir:hover{border-color:var(--ora);}
.role-card.dir:hover::before{opacity:1;}
.rc-logo-wrap{height:54px;display:flex;align-items:center;justify-content:center;margin-bottom:12px;}
.rc-logo-wrap img{max-height:48px;max-width:100%;object-fit:contain;}
.rc-badge{display:inline-block;font-size:9px;font-weight:600;letter-spacing:.8px;text-transform:uppercase;padding:3px 10px;border-radius:20px;margin-bottom:8px;}
.rc-badge.agence{background:var(--pbg);color:var(--pur);border:1px solid var(--pbd);}
.rc-badge.tech{background:var(--cl);color:var(--cyan);border:1px solid var(--cb);}
.rc-badge.dir{background:var(--obg);color:var(--ora);border:1px solid var(--obd);}
.rc-title{font-family:'Syne',sans-serif;font-size:15px;font-weight:700;margin-bottom:5px;color:var(--ink,var(--dark));}
.rc-sub{font-size:11px;color:var(--muted);line-height:1.55;}
@media(max-width:560px){.role-selector{grid-template-columns:1fr;gap:10px;}.home-hero{padding:28px 20px 24px;}.home-hexa{font-size:30px;}}

/* ── CARD ── */
.card{background:var(--white);border-radius:16px;border:1px solid var(--bd);padding:18px 20px;margin-bottom:14px;}
.card-title{font-family:'Syne',sans-serif;font-size:14px;font-weight:700;margin-bottom:14px;display:flex;align-items:center;gap:8px;}
.card-title .dot{width:7px;height:7px;border-radius:50%;background:var(--cyan);}

/* ── TABS ── */
.mode-tabs{display:flex;gap:4px;background:var(--bg);border-radius:12px;padding:4px;margin-bottom:16px;}
.mode-tab{flex:1;padding:9px 6px;border-radius:9px;cursor:pointer;font-size:12px;font-weight:500;color:var(--muted);border:none;background:transparent;font-family:'DM Sans',sans-serif;transition:all .2s;text-align:center;}
.mode-tab.active{background:var(--white);color:var(--dark);box-shadow:0 1px 4px rgba(0,0,0,.08);}

/* ── FORM ── */
.field{margin-bottom:12px;}
label{display:block;font-size:10px;color:var(--muted);letter-spacing:.6px;text-transform:uppercase;margin-bottom:5px;}
input[type=text],input[type=date],input[type=time],select,textarea.fta{width:100%;border:1px solid var(--bd);border-radius:10px;padding:9px 12px;font-size:13px;color:var(--dark);font-family:'DM Sans',sans-serif;background:var(--white);outline:none;transition:border .2s;}
input:focus,select:focus,textarea.fta:focus{border-color:var(--cyan);}
input.ai-f,select.ai-f,textarea.ai-f{border-color:var(--cyan);background:var(--cl);}
textarea.fta{resize:none;line-height:1.55;}
.row2{display:grid;grid-template-columns:1fr 1fr;gap:10px;}
.ai-badge{display:inline-flex;align-items:center;gap:4px;font-size:9px;color:var(--cyan);background:var(--cl);border:1px solid var(--cb);padding:2px 7px;border-radius:10px;margin-left:6px;font-weight:500;}

/* ── PDF DROP ── */
.pdf-drop{border:2px dashed var(--cb);border-radius:14px;background:var(--cl);padding:28px 20px;text-align:center;cursor:pointer;position:relative;margin-bottom:12px;transition:all .2s;}
.pdf-drop:hover{background:#d4f4fa;}
.pdf-drop input{position:absolute;inset:0;opacity:0;cursor:pointer;width:100%;}
.pdf-loaded{display:none;background:var(--gbg);border:1px solid var(--gbd);border-radius:12px;padding:12px 15px;margin-bottom:12px;align-items:center;gap:10px;}
.pdf-loaded.show{display:flex;}
.pdf-remove{background:none;border:none;cursor:pointer;color:var(--muted);font-size:18px;margin-left:auto;}

/* ── BUTTONS ── */
.btn{padding:12px 18px;border-radius:12px;border:none;font-family:'Syne',sans-serif;font-size:13px;font-weight:700;cursor:pointer;transition:all .15s;display:inline-flex;align-items:center;gap:7px;}
.btn-cyan{background:var(--cyan);color:#fff;}
.btn-cyan:hover{background:#22a8c2;}
.btn-dark{background:var(--dark);color:#fff;}
.btn-dark:hover{background:#1e252f;}
.btn-outline{background:var(--white);color:var(--muted);border:1.5px solid var(--bd);}
.btn-green{background:var(--grn);color:#fff;}
.btn-full{width:100%;justify-content:center;}
.btn:disabled{opacity:.4;cursor:not-allowed;}
.spinner-s{width:15px;height:15px;border-radius:50%;border:2px solid rgba(255,255,255,.3);border-top-color:#fff;animation:spin .8s linear infinite;display:none;}
.btn.loading .spinner-s{display:block;}
.btn.loading .btn-txt{display:none;}
@keyframes spin{to{transform:rotate(360deg);}}

/* ── URGENCE ── */
.urg-row{display:flex;gap:6px;margin-bottom:12px;}
.urg-btn{flex:1;padding:8px;border-radius:9px;border:1.5px solid var(--bd);background:var(--white);font-size:11px;font-weight:500;cursor:pointer;font-family:'DM Sans',sans-serif;color:var(--muted);text-align:center;transition:all .2s;}
.urg-btn.sel-u{border-color:var(--red);background:var(--rbg);color:var(--red);}
.urg-btn.sel-n{border-color:var(--ora);background:var(--obg);color:var(--ora);}
.urg-btn.sel-p{border-color:var(--grn);background:var(--gbg);color:var(--grn);}

/* ── TECH PICKER ── */
.tech-list{display:flex;flex-direction:column;gap:7px;margin-bottom:12px;}
.tech-item{display:flex;align-items:center;gap:12px;padding:10px 13px;border-radius:11px;border:1.5px solid var(--bd);cursor:pointer;transition:all .2s;}
.tech-item:hover,.tech-item.sel{border-color:var(--cyan);background:var(--cl);}
.tech-av{width:34px;height:34px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-family:'Syne',sans-serif;font-size:12px;font-weight:700;flex-shrink:0;color:#fff;}
.tech-check{margin-left:auto;color:var(--cyan);display:none;}
.tech-item.sel .tech-check{display:block;}

/* ── INTERVENTION CARDS (Agence + Dirigeant list) ── */
.interv-list{display:flex;flex-direction:column;gap:8px;}
.ii{background:var(--white);border-radius:12px;border:1px solid var(--bd);padding:13px 15px;display:flex;align-items:center;gap:12px;cursor:pointer;transition:border .2s;}
.ii:hover{border-color:var(--cb);}
.ii-bar{width:4px;border-radius:2px;align-self:stretch;flex-shrink:0;}
.ii-bar.urgente{background:var(--red);}
.ii-bar.normale{background:var(--ora);}
.ii-bar.preventive{background:var(--grn);}
.ii-body{flex:1;}
.ii-client{font-size:13px;font-weight:500;}
.ii-meta{font-size:11px;color:var(--muted);margin-top:2px;}
.ii-right{text-align:right;flex-shrink:0;}
.status-pill{font-size:10px;font-weight:500;padding:3px 9px;border-radius:10px;display:inline-block;margin-bottom:3px;}
.status-pill.planif{background:var(--cl);color:var(--cyan);border:1px solid var(--cb);}
.status-pill.terrain{background:var(--obg);color:var(--ora);border:1px solid var(--obd);}
.status-pill.valider{background:var(--pbg);color:var(--pur);border:1px solid var(--pbd);}
.status-pill.envoye{background:var(--gbg);color:var(--grn);border:1px solid var(--gbd);}
.ii-date{font-size:10px;color:var(--muted);font-family:var(--num);}

/* ── TECH VIEW INTERVENTION ── */
.interv-detail{background:var(--white);border-radius:16px;border:2px solid var(--cyan);padding:20px;margin-bottom:14px;}
.interv-detail.urgent{border-color:var(--red);}

/* ── ZONES TECH ── */
.zone-item{background:var(--white);border-radius:12px;border:1px solid var(--bd);padding:13px 15px;margin-bottom:8px;}
.zh{display:flex;align-items:center;justify-content:space-between;margin-bottom:9px;}
.zni{border:none;border-bottom:1.5px solid var(--bd);border-radius:0;padding:4px 0;font-size:13px;font-weight:500;width:72%;}
.zni:focus{outline:none;border-bottom-color:var(--cyan);}
.del-z{background:none;border:none;cursor:pointer;color:var(--hint);font-size:16px;}
.sev-row{display:flex;gap:5px;margin-bottom:9px;}
.sev-btn{flex:1;padding:7px 4px;border-radius:8px;border:1.5px solid var(--bd);background:var(--white);font-size:11px;font-weight:500;cursor:pointer;font-family:'DM Sans',sans-serif;color:var(--muted);text-align:center;transition:all .2s;}
.sev-btn.sc-critique{border-color:var(--red);background:var(--rbg);color:var(--red);}
.sev-btn.sc-majeur{border-color:var(--ora);background:var(--obg);color:var(--ora);}
.sev-btn.sc-mineur{border-color:var(--cyan);background:var(--cl);color:var(--cyan);}
.sev-btn.sc-stable{border-color:var(--grn);background:var(--gbg);color:var(--grn);}
.zone-comment{width:100%;border:1px solid var(--bd);border-radius:8px;padding:8px 10px;font-size:12px;font-family:'DM Sans',sans-serif;resize:none;height:54px;outline:none;}
.zone-comment:focus{border-color:var(--cyan);}
.add-zone-btn{display:flex;align-items:center;justify-content:center;gap:7px;border:1.5px dashed var(--cb);border-radius:12px;padding:12px;cursor:pointer;color:var(--cyan);font-size:13px;font-weight:500;background:transparent;width:100%;font-family:'DM Sans',sans-serif;margin-bottom:12px;}

/* ── PHOTOS ── */
.photo-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:6px;margin-bottom:6px;}
.photo-thumb{aspect-ratio:1;border-radius:8px;overflow:hidden;position:relative;background:var(--bg);border:1px solid var(--bd);}
.photo-thumb img{width:100%;height:100%;object-fit:cover;}
.del-photo{position:absolute;top:3px;right:3px;width:18px;height:18px;border-radius:50%;background:rgba(0,0,0,.55);border:none;cursor:pointer;color:#fff;font-size:10px;display:flex;align-items:center;justify-content:center;}
.photo-add{aspect-ratio:1;border-radius:8px;border:1.5px dashed var(--cb);background:var(--cl);display:flex;flex-direction:column;align-items:center;justify-content:center;cursor:pointer;position:relative;}
.photo-add input{position:absolute;inset:0;opacity:0;cursor:pointer;width:100%;}

/* ── RAPPORT VIEW ── */
.rapport-view{display:none;}
.rapport-view.active{display:block;}

/* ── GENERATING ── */
.generating{text-align:center;padding:40px 20px;}
.spinner-lg{width:52px;height:52px;border-radius:50%;border:3px solid var(--cl);border-top-color:var(--cyan);animation:spin 1s linear infinite;margin:0 auto 18px;}
.gen-steps{margin-top:20px;display:flex;flex-direction:column;gap:7px;}
.gs{display:flex;align-items:center;gap:10px;font-size:12px;color:var(--muted);padding:8px 12px;border-radius:10px;background:var(--white);border:1px solid var(--bd);}
.gs.active{color:var(--cyan);border-color:var(--cb);background:var(--cl);}
.gs.done{color:var(--grn);}

/* ── RAPPORT PREMIUM ── */
.r-hero{background:var(--dark);border-radius:18px;padding:24px;margin-bottom:14px;position:relative;overflow:hidden;}
.r-hero::before{content:'';position:absolute;top:-50px;right:-50px;width:200px;height:200px;border-radius:50%;background:rgba(42,187,218,.06);}
.r-h1{font-family:'Syne',sans-serif;font-size:22px;font-weight:800;color:#fff;line-height:1.2;margin-bottom:4px;}
.r-h1 em{color:var(--cyan);font-style:normal;}
.r-sub{font-size:12px;color:rgba(255,255,255,.38);margin-bottom:18px;}
.r-meta{display:grid;grid-template-columns:repeat(4,1fr);gap:7px;}
.rmc{background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.07);border-radius:9px;padding:9px 11px;}
.rmc .rl{font-size:9px;color:rgba(255,255,255,.28);text-transform:uppercase;letter-spacing:.8px;}
.rmc .rv{font-size:12px;color:rgba(255,255,255,.78);font-weight:500;margin-top:2px;}
.r-sec{font-size:9px;letter-spacing:1.8px;text-transform:uppercase;color:var(--hint);margin:14px 0 10px;display:flex;align-items:center;gap:8px;}
.r-sec::after{content:'';flex:1;height:1px;background:var(--bd);}
.r-zone{background:var(--white);border-radius:14px;border:1px solid var(--bd);margin-bottom:8px;overflow:hidden;}
.rz-hdr{display:flex;align-items:center;justify-content:space-between;padding:12px 16px;border-bottom:1px solid var(--bd);}
.rz-strip{width:4px;height:38px;border-radius:2px;flex-shrink:0;}
.rz-strip.critique{background:var(--red);}
.rz-strip.majeur{background:var(--ora);}
.rz-strip.mineur{background:var(--cyan);}
.rz-strip.stable{background:var(--grn);}
.rz-name{font-family:'Syne',sans-serif;font-size:13px;font-weight:700;margin-left:10px;}
.sev-pill{font-size:10px;font-weight:500;padding:3px 10px;border-radius:20px;}
.sev-pill.critique{background:var(--rbg);color:var(--red);border:1px solid var(--rbd);}
.sev-pill.majeur{background:var(--obg);color:var(--ora);border:1px solid var(--obd);}
.sev-pill.mineur{background:var(--cl);color:var(--cyan);border:1px solid var(--cb);}
.sev-pill.stable{background:var(--gbg);color:var(--grn);border:1px solid var(--gbd);}
.rz-body{padding:13px 16px;}
.rz-body p{font-size:12px;color:var(--mid);line-height:1.7;margin-bottom:9px;}
.sol-box{background:var(--gbg);border:1px solid var(--gbd);border-radius:8px;padding:8px 11px;margin-bottom:8px;}
.sol-box .sl{font-size:9px;color:var(--grn);text-transform:uppercase;letter-spacing:.6px;margin-bottom:2px;}
.sol-box .sv{font-size:12px;color:#1a5740;}
.r-rec{background:var(--white);border-radius:12px;border:1px solid var(--bd);padding:12px 14px;margin-bottom:7px;display:flex;gap:10px;}
.rr-num{width:30px;height:30px;border-radius:8px;display:flex;align-items:center;justify-content:center;font-family:var(--num);font-size:13px;font-weight:700;flex-shrink:0;}
.rr-num.p1{background:var(--rbg);color:var(--red);}
.rr-num.p2{background:var(--obg);color:var(--ora);}
.rr-num.p3{background:var(--gbg);color:var(--grn);}
.rr-t{font-size:12px;font-weight:500;margin-bottom:3px;}
.rr-d{font-size:11px;color:var(--muted);line-height:1.5;margin-bottom:5px;}
.rr-del{font-size:9px;font-weight:500;padding:2px 8px;border-radius:10px;}
.rr-del.p1{background:var(--rbg);color:var(--red);border:1px solid var(--rbd);}
.rr-del.p2{background:var(--obg);color:var(--ora);border:1px solid var(--obd);}
.rr-del.p3{background:var(--gbg);color:var(--grn);border:1px solid var(--gbd);}
.score-row{display:flex;align-items:center;gap:16px;background:var(--white);border-radius:14px;border:1px solid var(--bd);padding:16px;margin-bottom:14px;}
.ring-w{position:relative;width:80px;height:80px;flex-shrink:0;}
.ring-w svg{transform:rotate(-90deg);}
.ring-c{position:absolute;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;}
.r-num{font-family:var(--num);font-size:26px;font-weight:700;line-height:1;}
.r-den{font-size:10px;color:var(--muted);}
.synth{background:var(--white);border-radius:14px;border:1px solid var(--bd);padding:18px;margin-bottom:14px;font-size:14px;color:var(--mid);line-height:1.8;font-style:italic;}
.synth::before{content:'"';font-family:'Syne',sans-serif;font-size:44px;color:var(--cyan);line-height:.7;float:left;margin-right:8px;margin-top:4px;}
.budget-card{background:var(--white);border-radius:14px;border:1px solid var(--bd);padding:18px;margin-bottom:14px;}
.tl-row{display:flex;align-items:center;gap:10px;padding:8px 0;border-bottom:1px solid var(--bg);}
.tl-row:last-child{border-bottom:none;}
.tl-dot{width:30px;height:30px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;border:2px solid;font-family:var(--num);flex-shrink:0;}
.tl-dot.now{background:var(--rbg);color:var(--red);border-color:var(--rbd);}
.tl-dot.soon{background:var(--obg);color:var(--ora);border-color:var(--obd);}
.tl-dot.future{background:var(--pbg);color:var(--pur);border-color:var(--pbd);}
.tl-dot.long{background:var(--gbg);color:var(--grn);border-color:var(--gbd);}
.tl-info{flex:1;}
.tl-period{font-size:12px;font-weight:500;}
.tl-action{font-size:10px;color:var(--muted);}
.tl-bar{flex:0 0 100px;}
.bar-track{background:var(--bg);border-radius:3px;height:6px;overflow:hidden;}
.bar-fill{height:100%;border-radius:3px;transition:width 1.2s ease;}
.bar-fill.now{background:var(--red);}
.bar-fill.soon{background:var(--ora);}
.bar-fill.future{background:var(--pur);}
.bar-fill.long{background:var(--grn);}
.tl-amt{flex:0 0 90px;text-align:right;font-family:var(--num);font-size:12px;font-weight:600;}
.duree-card{background:var(--dark);border-radius:14px;padding:18px;margin-bottom:14px;}
.dv-top{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:14px;}
.dv-t{font-family:'Syne',sans-serif;font-size:14px;font-weight:700;color:#fff;margin-bottom:2px;}
.dv-m{font-size:10px;color:rgba(255,255,255,.3);}
.dv-y{font-family:var(--num);font-size:28px;font-weight:700;color:var(--cyan);line-height:1;}
.dv-l{font-size:9px;color:rgba(255,255,255,.28);}
.dv-track{background:rgba(255,255,255,.07);border-radius:5px;height:10px;overflow:hidden;margin-bottom:10px;}
.dv-fill{height:100%;background:var(--cyan);transition:width 1.4s ease;}
.dv-desc{font-size:11px;color:rgba(255,255,255,.42);line-height:1.7;}
.r-cta{background:var(--white);border-radius:14px;border:2px solid var(--bd);padding:20px;margin-bottom:14px;display:flex;align-items:center;justify-content:space-between;gap:14px;}
.r-cta-t{font-family:'Syne',sans-serif;font-size:17px;font-weight:800;margin-bottom:4px;}
.r-cta-s{font-size:12px;color:var(--muted);}
.cta-btn{background:var(--cyan);color:#fff;font-family:'Syne',sans-serif;font-size:13px;font-weight:700;padding:12px 20px;border-radius:12px;border:none;cursor:pointer;white-space:nowrap;flex-shrink:0;}
.r-footer{background:var(--white);border-radius:12px;border:1px solid var(--bd);padding:14px 18px;display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;align-items:center;margin-bottom:20px;}
.rf-logo{font-family:'Syne',sans-serif;font-size:14px;font-weight:800;}
.rf-logo em{color:var(--cyan);font-style:normal;}
.rf-info{font-size:10px;color:var(--muted);text-align:center;line-height:1.7;}
.rf-contact{text-align:right;font-size:10px;color:var(--muted);line-height:1.7;}
.rf-tel{font-family:var(--num);font-size:12px;font-weight:600;color:var(--dark);}

/* ── DIRIGEANT ── */
.dir-stats{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;margin-bottom:16px;}
.ds{background:var(--white);border-radius:12px;border:1px solid var(--bd);padding:12px 15px;}
.ds .dv{font-family:var(--num);font-size:22px;font-weight:700;}
.ds .dl{font-size:10px;color:var(--muted);margin-top:2px;}
.validate-box{background:var(--pbg);border:1px solid var(--pbd);border-radius:14px;padding:16px;margin-bottom:14px;}
.vb-title{font-family:'Syne',sans-serif;font-size:14px;font-weight:700;color:var(--pur);margin-bottom:8px;}
.vb-item{background:var(--white);border-radius:10px;border:1px solid var(--pbd);padding:12px 14px;margin-bottom:8px;display:flex;align-items:center;gap:12px;}
.vb-item:last-child{margin-bottom:0;}
.vb-client{font-size:13px;font-weight:500;flex:1;}
.vb-meta{font-size:11px;color:var(--muted);}
.vb-actions{display:flex;gap:7px;flex-shrink:0;}
.vb-btn{padding:7px 13px;border-radius:9px;font-size:11px;font-weight:500;cursor:pointer;font-family:'DM Sans',sans-serif;border:none;}
.vb-btn.validate{background:var(--cyan);color:#fff;}
.vb-btn.preview{background:var(--white);color:var(--muted);border:1px solid var(--bd);}

.err-box{background:var(--rbg);border:1px solid var(--rbd);border-radius:12px;padding:12px 15px;margin-bottom:12px;font-size:13px;color:var(--red);}
.info-box{background:var(--cl);border:1px solid var(--cb);border-radius:12px;padding:12px 14px;margin-bottom:12px;display:flex;gap:9px;font-size:12px;color:#1a6d7e;line-height:1.6;}
.section-lbl{font-size:9px;letter-spacing:1.5px;text-transform:uppercase;color:var(--hint);margin-bottom:8px;display:flex;align-items:center;gap:8px;}
.section-lbl::after{content:'';flex:1;height:1px;background:var(--bd);}

/* ── NOTIFICATION BADGE ── */
.notif-badge{position:absolute;top:-5px;right:-5px;width:18px;height:18px;border-radius:50%;background:var(--red);color:#fff;font-size:10px;font-weight:700;display:flex;align-items:center;justify-content:center;font-family:var(--num);border:2px solid var(--white);animation:pulse-badge 2s infinite;}
@keyframes pulse-badge{0%,100%{transform:scale(1);}50%{transform:scale(1.15);}}
.role-pill-wrap{position:relative;display:inline-block;}

/* ── SHARE MODAL ── */
.modal-overlay{position:fixed;inset:0;background:rgba(18,22,28,.55);z-index:200;display:flex;align-items:flex-end;justify-content:center;animation:fadeIn .2s ease;}
@keyframes fadeIn{from{opacity:0;}to{opacity:1;}}
.share-modal{background:var(--white);border-radius:20px 20px 0 0;width:100%;max-width:520px;padding:24px 22px 32px;animation:slideUp .28s cubic-bezier(.22,.68,0,1.2);}
@keyframes slideUp{from{transform:translateY(60px);opacity:0;}to{transform:none;opacity:1;}}
.share-modal-title{font-family:'Syne',sans-serif;font-size:17px;font-weight:700;margin-bottom:4px;}
.share-modal-sub{font-size:12px;color:var(--muted);margin-bottom:18px;}
.share-modal-qr{display:flex;justify-content:center;margin-bottom:16px;}
.share-modal-qr>div{border-radius:12px;overflow:hidden;border:4px solid var(--bg);box-shadow:0 2px 12px rgba(0,0,0,.1);}
.share-actions{display:flex;flex-direction:column;gap:9px;}
.share-action-btn{display:flex;align-items:center;gap:12px;padding:13px 16px;border-radius:12px;border:1.5px solid var(--bd);background:var(--white);cursor:pointer;font-family:'DM Sans',sans-serif;font-size:13px;color:var(--dark);transition:all .15s;text-align:left;}
.share-action-btn:hover{border-color:var(--cyan);background:var(--cl);}
.share-action-btn .sab-icon{font-size:20px;flex-shrink:0;}
.share-action-btn .sab-title{font-weight:500;margin-bottom:1px;}
.share-action-btn .sab-desc{font-size:11px;color:var(--muted);}
.share-modal-close{width:100%;padding:12px;border-radius:12px;border:none;background:var(--bg);color:var(--muted);font-family:'Syne',sans-serif;font-size:13px;font-weight:700;cursor:pointer;margin-top:4px;}

/* ── NOTIF PANEL ── */
.notif-panel{position:fixed;top:0;right:0;bottom:0;width:min(360px,100vw);background:var(--white);box-shadow:-4px 0 32px rgba(0,0,0,.15);z-index:300;display:flex;flex-direction:column;transform:translateX(100%);transition:transform .28s cubic-bezier(.22,.68,0,1.2);}
.notif-panel.open{transform:translateX(0);}
.notif-panel-header{padding:20px 18px 14px;border-bottom:1px solid var(--bd);display:flex;align-items:center;justify-content:space-between;}
.notif-panel-title{font-family:'Syne',sans-serif;font-size:16px;font-weight:700;}
.notif-panel-close{background:none;border:none;font-size:20px;cursor:pointer;color:var(--muted);padding:4px;}
.notif-panel-body{flex:1;overflow-y:auto;padding:12px;}
.notif-item{border:1px solid var(--bd);border-radius:12px;padding:13px 14px;margin-bottom:9px;cursor:pointer;transition:border-color .2s;}
.notif-item:hover{border-color:var(--cyan);}
.notif-item.unread{border-left:3px solid var(--cyan);padding-left:12px;}
.ni-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:5px;}
.ni-type{font-size:10px;font-weight:600;color:var(--cyan);}
.ni-time{font-size:10px;color:var(--muted);}
.ni-title{font-size:13px;font-weight:500;margin-bottom:2px;}
.ni-desc{font-size:11px;color:var(--muted);line-height:1.5;}
.notif-overlay{position:fixed;inset:0;background:rgba(18,22,28,.3);z-index:299;display:none;}
.notif-overlay.open{display:block;}

/* ── SETTINGS TABS ── */
.settings-tabs{display:flex;gap:4px;background:var(--bg);border-radius:10px;padding:4px;margin-bottom:18px;}
.stab{flex:1;padding:8px 6px;border-radius:7px;cursor:pointer;font-size:12px;font-weight:500;color:var(--muted);border:none;background:transparent;font-family:'DM Sans',sans-serif;transition:all .18s;text-align:center;}
.stab.active{background:var(--white);color:var(--dark);box-shadow:0 1px 4px rgba(0,0,0,.08);}
.stab-pane{display:none;}.stab-pane.active{display:block;}

/* ── TECH MANAGEMENT ── */
.tech-mgmt-card{background:var(--bg);border-radius:12px;padding:12px 14px;margin-bottom:8px;display:flex;align-items:center;gap:12px;}
.tmc-av{width:38px;height:38px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-family:'Syne',sans-serif;font-size:13px;font-weight:700;color:#fff;flex-shrink:0;}
.tmc-info{flex:1;}
.tmc-name{font-size:13px;font-weight:500;color:var(--dark);}
.tmc-meta{font-size:10px;color:var(--muted);margin-top:2px;}
.tmc-status{font-size:9px;font-weight:600;padding:2px 8px;border-radius:10px;margin-top:4px;display:inline-block;}
.tmc-status.dispo{background:var(--gbg);color:var(--grn);border:1px solid var(--gbd);}
.tmc-status.occupe{background:var(--obg);color:var(--ora);border:1px solid var(--obd);}
.tmc-status.inactif{background:var(--bg);color:var(--muted);border:1px solid var(--bd);}
.tmc-actions{display:flex;gap:6px;flex-shrink:0;}
.tmc-btn{width:30px;height:30px;border-radius:8px;border:1px solid var(--bd);background:var(--white);cursor:pointer;font-size:14px;display:flex;align-items:center;justify-content:center;transition:all .15s;}
.tmc-btn:hover{border-color:var(--cyan);background:var(--cl);}
.tmc-btn.del:hover{border-color:var(--red);background:var(--rbg);}

/* ── COLOR PICKER ── */
.color-grid{display:grid;grid-template-columns:repeat(8,1fr);gap:6px;margin-top:6px;}
.color-swatch{width:28px;height:28px;border-radius:50%;cursor:pointer;border:2px solid transparent;transition:all .15s;position:relative;}
.color-swatch.selected::after{content:'✓';position:absolute;inset:0;display:flex;align-items:center;justify-content:center;font-size:12px;color:#fff;font-weight:700;}
.color-swatch:hover{transform:scale(1.15);}

/* ── ADD TECH FORM ── */
.add-tech-form{background:var(--cl);border:1px solid var(--cb);border-radius:12px;padding:14px;margin-top:10px;display:none;}
.add-tech-form.open{display:block;}

/* ── CONSOMMABLES TECHNICIEN ── */
.conso-item{display:flex;align-items:center;gap:8px;padding:8px 10px;background:var(--bg);border-radius:9px;margin-bottom:6px;}
.conso-item input{border:none;background:transparent;font-family:'DM Sans',sans-serif;font-size:12px;color:var(--dark);outline:none;flex:1;}
.conso-qty{width:50px;text-align:center;border:1px solid var(--bd)!important;background:var(--white)!important;border-radius:7px;padding:4px 6px;font-size:12px;}
.conso-del{background:none;border:none;color:var(--muted);cursor:pointer;font-size:15px;flex-shrink:0;padding:2px;}
.conso-del:hover{color:var(--red);}
.voice-btn{display:flex;align-items:center;gap:6px;padding:9px 14px;border-radius:10px;border:1.5px dashed var(--cb);background:var(--cl);color:var(--cyan);font-size:12px;font-weight:500;cursor:pointer;font-family:'DM Sans',sans-serif;width:100%;justify-content:center;transition:all .2s;margin-bottom:10px;}
.voice-btn:hover{background:#d4f4fa;}
.voice-btn.recording{border-color:var(--red);background:var(--rbg);color:var(--red);animation:pulse-badge 1.2s infinite;}

/* ── CHIFFRAGE DIRECTEUR ── */
.chiffrage-card{background:var(--white);border-radius:14px;border:1px solid var(--bd);padding:18px 20px;margin-bottom:14px;}
.ch-title{font-family:'Syne',sans-serif;font-size:15px;font-weight:700;margin-bottom:14px;display:flex;align-items:center;gap:8px;}
.ch-row{display:flex;align-items:center;gap:10px;margin-bottom:10px;}
.ch-label{font-size:12px;color:var(--stone,var(--muted));flex:0 0 160px;}
.ch-input{flex:1;border:1px solid var(--bd);border-radius:8px;padding:8px 10px;font-size:13px;font-family:'DM Sans',sans-serif;color:var(--dark);outline:none;transition:border .2s;}
.ch-input:focus{border-color:var(--cyan);}
.ch-unit{font-size:11px;color:var(--muted);white-space:nowrap;}
.ch-total-row{display:flex;align-items:center;justify-content:space-between;padding:12px 14px;border-radius:10px;margin-top:4px;}
.ch-total-row.ht{background:var(--bg);}
.ch-total-row.ttc{background:var(--dark);border-radius:12px;padding:14px 16px;}
.ch-total-label{font-size:12px;font-weight:500;}
.ch-total-val{font-family:'Space Grotesk',sans-serif;font-size:18px;font-weight:700;}
.ch-total-row.ttc .ch-total-label{color:rgba(255,255,255,.6);font-size:13px;}
.ch-total-row.ttc .ch-total-val{color:var(--cyan);font-size:22px;}
.conso-list-dir{background:var(--bg);border-radius:10px;padding:10px 12px;margin-bottom:12px;}
.conso-list-dir-item{font-size:12px;color:var(--mid);padding:3px 0;border-bottom:1px solid var(--bd);display:flex;justify-content:space-between;}
.conso-list-dir-item:last-child{border:none;}
.facturation-badge{display:inline-flex;align-items:center;gap:6px;font-size:10px;font-weight:600;padding:4px 12px;border-radius:20px;}
.facturation-badge.pret{background:var(--gbg);color:var(--grn);border:1px solid var(--gbd);}
.facturation-badge.attente{background:var(--obg);color:var(--ora);border:1px solid var(--obd);}

/* ── MANDANT CARDS ── */
.mandant-card{background:var(--bg);border-radius:12px;padding:12px 14px;margin-bottom:8px;display:flex;align-items:center;gap:12px;}
.mandant-logo-box{width:44px;height:44px;border-radius:10px;object-fit:contain;background:var(--white);border:1px solid var(--bd);display:flex;align-items:center;justify-content:center;font-size:18px;flex-shrink:0;overflow:hidden;}
.mandant-logo-box img{width:100%;height:100%;object-fit:contain;}
.mandant-name{font-size:13px;font-weight:500;color:var(--dark);}
.mandant-meta{font-size:10px;color:var(--muted);margin-top:2px;}
.mandant-badge{font-size:9px;font-weight:600;padding:2px 8px;border-radius:10px;margin-top:4px;display:inline-block;background:var(--pbg);color:var(--pur);border:1px solid var(--pbd);}
.mandant-opt{display:flex;align-items:center;gap:10px;padding:10px 13px;border-radius:10px;border:1.5px solid var(--bd);cursor:pointer;transition:all .18s;background:var(--white);margin-bottom:6px;}
.mandant-opt:hover{border-color:var(--cyan);background:var(--cl);}
.mandant-opt.sel{border-color:var(--cyan);background:var(--cl);}
.mandant-opt-logo{width:32px;height:32px;border-radius:8px;overflow:hidden;background:var(--bg);border:1px solid var(--bd);display:flex;align-items:center;justify-content:center;font-size:14px;flex-shrink:0;}
.mandant-opt-logo img{width:100%;height:100%;object-fit:contain;}
.mandant-opt-name{font-size:12px;font-weight:500;flex:1;}
.mandant-opt-type{font-size:9px;color:var(--muted);}
.mandant-check{color:var(--cyan);font-weight:700;font-size:14px;display:none;}
.mandant-opt.sel .mandant-check{display:block;}
.logo-upload-zone{border:2px dashed var(--cb);border-radius:10px;background:var(--cl);padding:16px;text-align:center;cursor:pointer;position:relative;transition:all .2s;margin-bottom:8px;}
.logo-upload-zone:hover{background:#d4f4fa;}
.logo-upload-zone input{position:absolute;inset:0;opacity:0;cursor:pointer;width:100%;}
.logo-preview-row{display:flex;align-items:center;gap:10px;background:var(--gbg);border:1px solid var(--gbd);border-radius:10px;padding:10px 12px;margin-bottom:8px;}
.logo-preview-row img{width:44px;height:44px;object-fit:contain;border-radius:6px;background:var(--white);}
.add-mandant-form{background:var(--cl);border:1px solid var(--cb);border-radius:12px;padding:14px;margin-top:10px;display:none;}
.add-mandant-form.open{display:block;}

@media(max-width:640px){
  .tech-bottom-nav{position:fixed;bottom:0;left:0;right:0;background:var(--white);border-top:1px solid var(--bd);display:flex;z-index:100;padding-bottom:env(safe-area-inset-bottom);}
  .tbn-btn{flex:1;display:flex;flex-direction:column;align-items:center;gap:3px;padding:10px 6px;border:none;background:none;cursor:pointer;font-size:9px;font-weight:500;color:var(--muted);font-family:'DM Sans',sans-serif;transition:color .15s;}
  .tbn-btn.active{color:var(--cyan);}
  .tbn-btn svg{width:22px;height:22px;}
  #view-tech{padding-bottom:70px;}
  .tech-interv-card{background:var(--white);border-radius:16px;border:1px solid var(--bd);padding:16px;margin-bottom:10px;display:flex;gap:12px;align-items:flex-start;box-shadow:0 1px 4px rgba(0,0,0,.05);}
  .tic-urgence-bar{width:4px;border-radius:2px;align-self:stretch;flex-shrink:0;}
  .tic-urgence-bar.urgente{background:var(--red);}
  .tic-urgence-bar.normale{background:var(--cyan);}
  .tic-urgence-bar.preventive{background:var(--grn);}
}
@media(min-width:641px){.tech-bottom-nav{display:none;}}
@media(max-width:640px){.r-meta{grid-template-columns:1fr 1fr;}.dir-stats{grid-template-columns:1fr 1fr;}}
</style>
</head>
<body>
<div class="app">

<!-- HEADER -->
<div class="hdr">
  <div style="display:flex;align-items:center;gap:12px;">
    <div>
      <div class="logo-sub" id="hdr-entity-name" style="font-size:11px;font-weight:600;letter-spacing:.5px;">Groupe BCNC</div>
    </div>
    <div id="hdr-entity-dot" style="width:8px;height:8px;border-radius:50%;background:#2abbda;flex-shrink:0;transition:background .3s;"></div>
  </div>
  <div class="hdr-right" style="display:flex;align-items:center;gap:8px;">
    <div id="role-switcher" style="display:none;align-items:center;gap:8px;">
      <div class="role-pill-wrap">
        <button class="role-pill" onclick="showView('agence')">🏢 Agence</button>
      </div>
      <div class="role-pill-wrap">
        <button class="role-pill" onclick="showView('tech')">🔧 Technicien</button>
      </div>
      <div class="role-pill-wrap" id="dir-pill-wrap">
        <button class="role-pill" onclick="showView('dir')">👔 Dirigeant</button>
        <span class="notif-badge" id="dir-notif-badge" style="display:none;">0</span>
      </div>
      <button id="notif-bell" onclick="openNotifPanel()" title="Notifications" style="display:none;position:relative;background:var(--bg);border:1.5px solid var(--bd);border-radius:10px;width:36px;height:36px;cursor:pointer;display:none;align-items:center;justify-content:center;font-size:16px;transition:all .2s;" onmouseover="this.style.borderColor='var(--cyan)'" onmouseout="this.style.borderColor='var(--bd)'">🔔</button>
    </div>
    <button onclick="toggleSettings()" id="settings-btn" title="Paramètres" style="background:var(--bg);border:1.5px solid var(--bd);border-radius:10px;padding:6px 10px;cursor:pointer;display:flex;align-items:center;gap:6px;font-size:12px;color:var(--muted);font-family:'DM Sans',sans-serif;transition:all .2s;" onmouseover="this.style.borderColor='var(--cyan)'" onmouseout="this.style.borderColor='var(--bd)'">
      <span style="font-size:14px;">⚙️</span>
      <span id="api-status-dot" style="width:8px;height:8px;border-radius:50%;background:#cbd5da;display:inline-block;transition:background .4s;" title="Clé non testée"></span>
    </button>
    <!-- Sync SharePoint -->
    <button id="sp-sync-btn" onclick="spSignIn()" title="Connexion Microsoft 365" style="background:var(--bg);border:1.5px solid var(--bd);border-radius:10px;padding:6px 10px;cursor:pointer;display:flex;align-items:center;gap:6px;font-size:12px;color:var(--muted);font-family:'DM Sans',sans-serif;transition:all .2s;" onmouseover="this.style.borderColor='#0078d4'" onmouseout="this.style.borderColor='var(--bd)'">
      <span style="font-size:14px;">☁️</span>
      <span id="sp-status-dot" style="width:8px;height:8px;border-radius:50%;background:#cbd5da;display:inline-block;" title="Non connecté"></span>
    </button>
  </div>
</div>

<!-- NOTIFICATION PANEL -->
<div class="notif-overlay" id="notif-overlay" onclick="closeNotifPanel()"></div>
<div class="notif-panel" id="notif-panel">
  <div class="notif-panel-header">
    <div class="notif-panel-title">🔔 Notifications</div>
    <button class="notif-panel-close" onclick="closeNotifPanel()">✕</button>
  </div>
  <div class="notif-panel-body" id="notif-panel-body">
    <div style="text-align:center;padding:30px 0;font-size:13px;color:var(--muted);">Aucune notification</div>
  </div>
</div>

<!-- SHARE MODAL PLACEHOLDER -->
<div id="share-modal-container"></div>

<!-- SETTINGS PANEL -->
<div id="settings-panel" style="display:none;background:var(--white);border:1px solid var(--bd);border-radius:16px;padding:20px;margin-bottom:16px;animation:fi .2s ease;">
  <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:14px;">
    <div style="font-family:'Syne',sans-serif;font-size:15px;font-weight:700;">⚙️ Paramètres Alptech</div>
    <button onclick="toggleSettings()" style="background:none;border:none;cursor:pointer;font-size:20px;color:var(--muted);line-height:1;">×</button>
  </div>

  <div class="settings-tabs">
    <button class="stab active" onclick="switchStab('api')">🔑 API</button>
    <button class="stab" onclick="switchStab('entreprises')">🏗 Entreprises</button>
    <button class="stab" onclick="switchStab('techs')">🔧 Techniciens</button>
    <button class="stab" onclick="switchStab('mandants')">🤝 Mandants</button>
    <button class="stab" onclick="switchStab('company')">⚙️ Groupe</button>
  </div>

  <!-- ── ONGLET API ── -->
  <div class="stab-pane active" id="stab-api">
    <div style="font-size:12px;color:var(--muted);margin-bottom:14px;line-height:1.6;">La clé API est stockée uniquement dans votre navigateur (localStorage). Elle n'est jamais envoyée ailleurs qu'à l'API Anthropic.</div>
    <div style="display:flex;gap:8px;align-items:stretch;margin-bottom:10px;">
      <div style="position:relative;flex:1;">
        <input type="password" id="api-key-input" placeholder="sk-ant-api03-…" style="width:100%;border:1.5px solid var(--bd);border-radius:10px;padding:10px 40px 10px 12px;font-size:13px;color:var(--dark);font-family:'DM Sans',sans-serif;background:var(--white);outline:none;transition:border .2s;" onfocus="this.style.borderColor='var(--cyan)'" onblur="this.style.borderColor='var(--bd)'"/>
        <button onclick="toggleKeyVisibility()" title="Afficher/masquer" style="position:absolute;right:10px;top:50%;transform:translateY(-50%);background:none;border:none;cursor:pointer;font-size:15px;color:var(--muted);">👁</button>
      </div>
      <button onclick="saveApiKey()" class="btn btn-cyan" style="padding:10px 16px;font-size:13px;white-space:nowrap;">Enregistrer</button>
      <button onclick="testApiKey()" id="test-btn" class="btn btn-outline" style="padding:10px 16px;font-size:13px;white-space:nowrap;">
        <span id="test-btn-txt">Tester</span>
        <div class="spinner-s" id="test-spinner" style="display:none;"></div>
      </button>
    </div>
    <div id="api-status-bar" style="display:none;border-radius:10px;padding:10px 14px;font-size:12px;display:flex;align-items:center;gap:8px;"></div>
  </div>

  <!-- ── ONGLET ENTREPRISES ── -->
  <div class="stab-pane" id="stab-entreprises">
    <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:12px;">
      <div style="font-size:12px;color:var(--muted);">Entités du Groupe BCNC. Chaque entreprise a ses techniciens et son directeur.</div>
      <button class="btn btn-cyan" style="padding:8px 14px;font-size:12px;white-space:nowrap;" onclick="openAddEntrepriseForm()">+ Ajouter</button>
    </div>
    <div id="entreprise-mgmt-list"></div>
    <div class="add-mandant-form" id="add-entreprise-form">
      <div style="font-family:'Syne',sans-serif;font-size:13px;font-weight:700;margin-bottom:12px;" id="add-entreprise-form-title">Nouvelle entreprise</div>
      <input type="hidden" id="entreprise-edit-id">
      <div class="field">
        <label>Logo</label>
        <div id="ent-logo-preview-wrap" style="display:none;" class="logo-preview-row">
          <img id="ent-logo-preview-img" src="" alt="logo">
          <div style="flex:1;"><div id="ent-logo-preview-name" style="font-size:12px;font-weight:500;"></div><button onclick="removeEntLogo()" style="font-size:10px;color:var(--red);background:none;border:none;cursor:pointer;margin-top:2px;">✕ Retirer</button></div>
        </div>
        <div class="logo-upload-zone" id="ent-logo-drop">
          <input type="file" accept="image/*" onchange="loadEntLogo(event)">
          <div style="font-size:22px;margin-bottom:4px;">🖼</div>
          <div style="font-size:12px;font-weight:500;color:var(--cyan);">Glisser le logo</div>
          <div style="font-size:10px;color:var(--muted);">PNG fond transparent recommandé</div>
        </div>
      </div>
      <div class="row2">
        <div class="field"><label>Nom de l'entreprise</label><input type="text" id="ent-form-nom" placeholder="Ex : Alptech"/></div>
        <div class="field"><label>Couleur principale</label><input type="color" id="ent-form-couleur" value="#2abbda" style="width:100%;height:38px;border-radius:9px;border:1px solid var(--bd);cursor:pointer;padding:2px;"></div>
      </div>
      <div class="field"><label>Activité</label><input type="text" id="ent-form-activite" placeholder="Ex : Étanchéité · Toiture · Terrasse"/></div>
      <div class="section-lbl" style="margin-top:10px;">Directeur</div>
      <div class="row2">
        <div class="field"><label>Prénom Nom</label><input type="text" id="ent-form-dir-nom" placeholder="Ex : Lucien Iannone"/></div>
        <div class="field"><label>Initiales</label><input type="text" id="ent-form-dir-ini" placeholder="Ex : LI" maxlength="3"/></div>
      </div>
      <div class="row2">
        <div class="field"><label>Email directeur</label><input type="text" id="ent-form-dir-email" placeholder="prenom@entreprise.fr"/></div>
        <div class="field"><label>Téléphone directeur</label><input type="text" id="ent-form-dir-tel" placeholder="06 00 00 00 00"/></div>
      </div>
      <div class="section-lbl" style="margin-top:10px;">Coordonnées</div>
      <div class="row2">
        <div class="field"><label>Email général</label><input type="text" id="ent-form-email" placeholder="contact@entreprise.fr"/></div>
        <div class="field"><label>Téléphone</label><input type="text" id="ent-form-tel" placeholder="04 00 00 00 00"/></div>
      </div>
      <div class="field"><label>Adresse</label><input type="text" id="ent-form-adresse" placeholder="36 Chemin des Fontaines, 38190 Bernin"/></div>
      <div class="row2">
        <div class="field"><label>Site web</label><input type="text" id="ent-form-site" placeholder="www.entreprise.fr"/></div>
        <div class="field"><label>SIRET</label><input type="text" id="ent-form-siret" placeholder="000 000 000 00000"/></div>
      </div>
      <div style="display:flex;gap:8px;margin-top:14px;">
        <button class="btn btn-cyan" style="flex:1;" onclick="saveEntreprise()">✓ Enregistrer</button>
        <button class="btn btn-outline" onclick="closeAddEntrepriseForm()">Annuler</button>
      </div>
    </div>
  </div>

  <!-- ── ONGLET TECHNICIENS ── -->
  <div class="stab-pane" id="stab-techs">
    <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:12px;">
      <div style="font-size:12px;color:var(--muted);">Gérez votre équipe. Les techniciens apparaissent dans l'interface Agence.</div>
      <button class="btn btn-cyan" style="padding:8px 14px;font-size:12px;white-space:nowrap;" onclick="openAddTechForm()">+ Ajouter</button>
    </div>
    <div id="tech-mgmt-list"></div>

    <!-- Formulaire ajout / édition -->
    <div class="add-tech-form" id="add-tech-form">
      <div style="font-family:'Syne',sans-serif;font-size:13px;font-weight:700;margin-bottom:12px;" id="add-tech-form-title">Nouveau technicien</div>
      <input type="hidden" id="tech-edit-id">
      <div class="field"><label>Prénom & Nom</label><input type="text" id="tech-form-name" placeholder="Ex : Jean Dupont" maxlength="40"/></div>
      <div class="field"><label>Spécialité / Poste</label><input type="text" id="tech-form-spec" placeholder="Ex : Expert étanchéité" maxlength="50"/></div>
      <div class="field"><label>Téléphone</label><input type="text" id="tech-form-tel" placeholder="06 00 00 00 00"/></div>
      <div class="field">
        <label>Entreprise rattachée</label>
        <select id="tech-form-entreprise" style="width:100%;border:1px solid var(--bd);border-radius:10px;padding:9px 12px;font-size:13px;font-family:'DM Sans',sans-serif;"></select>
      </div>
      <div class="field">
        <label>Statut</label>
        <select id="tech-form-status">
          <option value="dispo">● Disponible</option>
          <option value="occupe">● En intervention</option>
          <option value="inactif">○ Inactif</option>
        </select>
      </div>
      <div class="field">
        <label>Couleur de l'avatar</label>
        <div class="color-grid" id="color-grid"></div>
      </div>
      <div style="display:flex;gap:8px;margin-top:14px;">
        <button class="btn btn-cyan" style="flex:1;" onclick="saveTech()">✓ Enregistrer</button>
        <button class="btn btn-outline" onclick="closeAddTechForm()">Annuler</button>
      </div>
    </div>
  </div>

  <!-- ── ONGLET MANDANTS ── -->
  <div class="stab-pane" id="stab-mandants">
    <div style="font-size:12px;color:var(--muted);margin-bottom:4px;line-height:1.6;">
      Un mandant est une structure <strong>au nom de qui</strong> vous émettez le rapport. Le logo et le nom du mandant remplacent Alptech dans l'en-tête du rapport client.
    </div>
    <div style="background:var(--obg);border:1px solid var(--obd);border-radius:10px;padding:9px 12px;font-size:11px;color:var(--ora);margin-bottom:14px;display:flex;gap:8px;">
      <span>💡</span><span>Exemple : Alptech intervient pour <strong>Soprim</strong>. Le rapport est émis au nom de Soprim avec son logo. En bas de page : <em>"Expertise réalisée par Alptech pour Soprim."</em></span>
    </div>
    <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:12px;">
      <div style="font-size:12px;color:var(--muted);">Structures mandantes configurées</div>
      <button class="btn btn-cyan" style="padding:8px 14px;font-size:12px;white-space:nowrap;" onclick="openAddMandantForm()">+ Ajouter</button>
    </div>
    <div id="mandant-mgmt-list"></div>

    <!-- Formulaire mandant -->
    <div class="add-mandant-form" id="add-mandant-form">
      <div style="font-family:'Syne',sans-serif;font-size:13px;font-weight:700;margin-bottom:12px;" id="add-mandant-form-title">Nouveau mandant</div>
      <input type="hidden" id="mandant-edit-id">

      <!-- Logo upload -->
      <div class="field">
        <label>Logo (PNG/JPG recommandé, fond blanc)</label>
        <div id="mandant-logo-preview-wrap" style="display:none;" class="logo-preview-row">
          <img id="mandant-logo-preview-img" src="" alt="logo">
          <div style="flex:1;">
            <div id="mandant-logo-preview-name" style="font-size:12px;font-weight:500;"></div>
            <button onclick="removeMandantLogo()" style="font-size:10px;color:var(--red);background:none;border:none;cursor:pointer;margin-top:2px;">✕ Retirer</button>
          </div>
        </div>
        <div class="logo-upload-zone" id="mandant-logo-drop">
          <input type="file" accept="image/*" onchange="loadMandantLogo(event)">
          <div style="font-size:22px;margin-bottom:4px;">🖼</div>
          <div style="font-size:12px;font-weight:500;color:var(--cyan);">Glisser le logo ici</div>
          <div style="font-size:10px;color:var(--muted);">ou cliquer pour parcourir</div>
        </div>
      </div>

      <div class="field"><label>Nom de la structure mandante</label><input type="text" id="mandant-form-name" placeholder="Ex : Soprim, NEXITY, Cités Immobilier…" maxlength="60"/></div>
      <div class="field"><label>Activité / Type</label><input type="text" id="mandant-form-type" placeholder="Ex : Gestionnaire de copropriétés" maxlength="60"/></div>
      <div class="field"><label>Email du mandant</label><input type="text" id="mandant-form-email" placeholder="contact@soprim.fr"/></div>
      <div class="field"><label>Téléphone</label><input type="text" id="mandant-form-tel" placeholder="01 00 00 00 00"/></div>
      <div class="field"><label>Adresse (optionnel)</label><input type="text" id="mandant-form-addr" placeholder="Ex : 12 rue de la Paix, 75001 Paris"/></div>
      <div class="field">
        <label>Couleur principale (header rapport)</label>
        <div style="display:flex;align-items:center;gap:10px;margin-top:6px;">
          <input type="color" id="mandant-form-color" value="#1e3a5f" style="width:40px;height:36px;border-radius:8px;border:1px solid var(--bd);cursor:pointer;padding:2px;">
          <span style="font-size:11px;color:var(--muted);">Couleur utilisée dans l'en-tête du rapport white-label</span>
        </div>
      </div>
      <div style="display:flex;gap:8px;margin-top:14px;">
        <button class="btn btn-cyan" style="flex:1;" onclick="saveMandant()">✓ Enregistrer</button>
        <button class="btn btn-outline" onclick="closeAddMandantForm()">Annuler</button>
      </div>
    </div>
  </div>

  <!-- ── ONGLET GROUPE ── -->
  <div class="stab-pane" id="stab-company">
    <div style="font-size:12px;color:var(--muted);margin-bottom:14px;line-height:1.6;">Informations générales du Groupe BCNC — apparaissent dans le pied de page de tous les rapports.</div>
    <div style="display:flex;align-items:center;gap:12px;background:var(--bg);border-radius:12px;padding:12px;margin-bottom:14px;">
      <img src="" id="co-logo-preview" style="height:38px;object-fit:contain;">
      <div style="font-family:'Syne',sans-serif;font-size:15px;font-weight:700;" id="co-nom-preview">Groupe BCNC</div>
    </div>
    <div class="field"><label>Nom du groupe</label><input type="text" id="co-name" placeholder="Groupe BCNC" maxlength="60"/></div>
    <div class="field"><label>Slogan</label><input type="text" id="co-tagline" placeholder="Entreprendre Ensemble." maxlength="80"/></div>
    <div class="field"><label>Site web</label><input type="text" id="co-web" placeholder="www.groupebcnc.com"/></div>
    <div class="field"><label>Adresse siège</label><input type="text" id="co-adresse" placeholder="36 Chemin des Fontaines, 38190 Bernin"/></div>
    <button class="btn btn-cyan btn-full" onclick="saveCompany()" style="margin-top:4px;">✓ Enregistrer</button>
    <div id="co-status" style="display:none;margin-top:8px;font-size:12px;color:var(--grn);">✓ Informations enregistrées</div>
  </div>
</div>

<!-- ═══ HOME ═══ -->
<div class="view active" id="view-home">

  <!-- Logo unique centré -->
  <div style="text-align:center;padding:32px 20px 24px;">
    <img src="" id="home-bcnc-logo" style="height:140px;object-fit:contain;display:block;margin:0 auto 14px;" alt="HEXA">
    <div style="font-size:10px;color:var(--muted);letter-spacing:2px;text-transform:uppercase;margin-bottom:6px;">Plateforme d'intervention · Groupe BCNC</div>
    <div style="width:32px;height:2px;background:linear-gradient(90deg,transparent,var(--cyan),transparent);margin:0 auto 14px;"></div>
    <div style="font-size:12px;color:var(--hint);">Sélectionnez votre profil</div>
  </div>

  <!-- Cartes de rôle -->
  <div class="role-selector">

    <!-- L'Agence -->
    <div class="role-card agence" onclick="showView('agence')">
      <div class="rc-logo-wrap">
        <svg width="56" height="56" viewBox="0 0 56 56" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="28" cy="28" r="26" fill="#f3f0ff" stroke="#d4c8f8" stroke-width="1.5"/>
          <!-- Téléphone -->
          <rect x="20" y="15" width="16" height="22" rx="3" fill="white" stroke="#7c5ce7" stroke-width="1.5"/>
          <rect x="24" y="33" width="8" height="1.5" rx=".75" fill="#7c5ce7" opacity=".5"/>
          <!-- Signal / ondes -->
          <path d="M30 22c1.5.8 2.5 2.3 2.5 4s-1 3.2-2.5 4" stroke="#7c5ce7" stroke-width="1.5" stroke-linecap="round"/>
          <path d="M32.5 19.5c2.5 1.5 4.2 4.1 4.2 7s-1.7 5.5-4.2 7" stroke="#7c5ce7" stroke-width="1.5" stroke-linecap="round" opacity=".4"/>
          <!-- Écran -->
          <rect x="22" y="18" width="8" height="12" rx="1" fill="#f3f0ff"/>
          <rect x="23" y="19" width="6" height="1.5" rx=".5" fill="#7c5ce7" opacity=".4"/>
          <rect x="23" y="22" width="4" height="1.5" rx=".5" fill="#7c5ce7" opacity=".3"/>
        </svg>
      </div>
      <span class="rc-badge agence">Agence</span>
      <div class="rc-title">L'Agence</div>
      <div class="rc-sub">Réception des demandes, planification, assignation</div>
    </div>

    <!-- Technicien -->
    <div class="role-card tech" onclick="showView('tech')">
      <div class="rc-logo-wrap">
        <svg width="56" height="56" viewBox="0 0 56 56" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="28" cy="28" r="26" fill="#eaf9fc" stroke="#b3eaf4" stroke-width="1.5"/>
          <path d="M14 30c0-7.732 6.268-14 14-14s14 6.268 14 14" fill="#2abbda" opacity=".15"/>
          <path d="M13 30h30" stroke="#2abbda" stroke-width="2.5" stroke-linecap="round"/>
          <path d="M16 30v2a2 2 0 002 2h20a2 2 0 002-2v-2" stroke="#2abbda" stroke-width="2" stroke-linecap="round"/>
          <path d="M15 30c0-7.18 5.82-13 13-13s13 5.82 13 13" stroke="#2abbda" stroke-width="2.5" stroke-linecap="round"/>
          <path d="M21 30h14" stroke="#1a9fbc" stroke-width="2" stroke-linecap="round"/>
          <rect x="23" y="34" width="10" height="5" rx="1.5" fill="#2abbda" opacity=".3"/>
          <rect x="25" y="35" width="6" height="3" rx="1" fill="#2abbda"/>
        </svg>
      </div>
      <span class="rc-badge tech">Terrain</span>
      <div class="rc-title">Technicien</div>
      <div class="rc-sub">Mes interventions, rapport terrain, photos</div>
    </div>

    <!-- Dirigeant -->
    <div class="role-card dir" onclick="showView('dir')">
      <div class="rc-logo-wrap">
        <svg width="56" height="56" viewBox="0 0 56 56" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="28" cy="28" r="26" fill="#fff7e6" stroke="#f5d98a" stroke-width="1.5"/>
          <rect x="16" y="14" width="20" height="26" rx="3" fill="white" stroke="#f5d98a" stroke-width="1.5"/>
          <rect x="19" y="19" width="14" height="2" rx="1" fill="#c47d0a" opacity=".4"/>
          <rect x="19" y="23" width="10" height="2" rx="1" fill="#c47d0a" opacity=".3"/>
          <rect x="19" y="27" width="12" height="2" rx="1" fill="#c47d0a" opacity=".3"/>
          <circle cx="34" cy="34" r="9" fill="#c47d0a"/>
          <path d="M29.5 34l3 3 5-5" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>
      <span class="rc-badge dir">Direction</span>
      <div class="rc-title">Dirigeant</div>
      <div class="rc-sub">Validation des rapports, chiffrage, envoi client</div>
    </div>

  </div>

  <div style="text-align:center;font-size:10px;color:var(--hint);letter-spacing:.5px;padding-bottom:8px;">
    Entreprendre Ensemble. · <span style="font-weight:600;">Groupe BCNC</span>
  </div>
</div>

<!-- ═══ AGENCE ═══ -->
<div class="view" id="view-agence">
  <div style="display:grid;grid-template-columns:1fr 360px;gap:14px;align-items:start;">
  <div>
    <div class="card">
      <div class="card-title"><span class="dot"></span>Nouvelle intervention</div>
      <div class="mode-tabs">
        <button class="mode-tab active" onclick="agMode('pdf')" id="atab-pdf">📄 Ordre de service PDF</button>
        <button class="mode-tab" onclick="agMode('email')" id="atab-email">✉️ Email client</button>
        <button class="mode-tab" onclick="agMode('phone')" id="atab-phone">📞 Appel téléphonique</button>
      </div>
      <!-- PDF -->
      <div id="amode-pdf">
        <div class="pdf-drop" id="ag-pdf-drop" ondragover="event.preventDefault();this.style.background='#d4f4fa'" ondragleave="this.style.background=''" ondrop="agDropPDF(event)">
          <input type="file" accept=".pdf" onchange="agLoadPDF(event)">
          <div style="font-size:32px;margin-bottom:8px;">📄</div>
          <div style="font-family:'Syne',sans-serif;font-size:14px;font-weight:700;margin-bottom:4px;">Glisser l'ordre de service ici</div>
          <div style="font-size:12px;color:var(--muted);">ou <span style="color:var(--cyan);font-weight:500;">cliquer pour parcourir</span> · PDF uniquement</div>
        </div>
        <div class="pdf-loaded" id="ag-pdf-loaded">
          <span style="font-size:24px;">📋</span>
          <div><div id="ag-pdf-name" style="font-size:13px;font-weight:500;"></div><div id="ag-pdf-size" style="font-size:11px;color:var(--muted);margin-top:2px;"></div></div>
          <button class="pdf-remove" onclick="agRemovePDF()">✕</button>
        </div>
        <button class="btn btn-cyan btn-full" id="ag-btn-pdf" onclick="agExtract('pdf')" disabled>
          <div class="spinner-s"></div><span class="btn-txt">✦ Extraire les informations par IA</span>
        </button>
      </div>
      <!-- EMAIL -->
      <div id="amode-email" style="display:none;">
        <div class="field"><label>Coller le contenu de l'email</label><textarea class="fta" id="ag-email-txt" style="height:140px;" placeholder="Coller ici le corps de l'email reçu du client ou du donneur d'ordre..."></textarea></div>
        <button class="btn btn-cyan btn-full" onclick="agExtract('email')"><div class="spinner-s"></div><span class="btn-txt">✦ Extraire les informations par IA</span></button>
      </div>
      <!-- PHONE -->
      <div id="amode-phone" style="display:none;">
        <div class="field"><label>Résumé de l'appel</label><textarea class="fta" id="ag-phone-txt" style="height:110px;" placeholder="Ex : Client Dupont, résidence Les Pins à Toulon, infiltration plafond 3ème étage depuis hier, très urgent, contact 06 12 34 56 78..."></textarea></div>
        <button class="btn btn-cyan btn-full" onclick="agExtract('phone')"><div class="spinner-s"></div><span class="btn-txt">✦ Structurer la demande par IA</span></button>
      </div>
      <!-- EXTRACT RESULT -->
      <div id="ag-extract-result" style="display:none;margin-top:12px;background:var(--cl);border:1px solid var(--cb);border-radius:12px;padding:12px 14px;">
        <div style="font-size:11px;font-weight:500;color:var(--cyan);margin-bottom:8px;">✦ Informations extraites — vérifiez avant de continuer</div>
        <div id="ag-extract-fields" style="display:grid;grid-template-columns:1fr 1fr;gap:6px;"></div>
      </div>
    </div>

    <div class="card">
      <div class="card-title"><span class="dot"></span>Fiche d'intervention</div>

      <!-- ENTREPRISE DESTINATRICE -->
      <div class="section-lbl">Entreprise destinatrice</div>
      <div id="ag-entreprise-selector" style="margin-bottom:4px;"></div>

      <!-- TYPE DE DEMANDE -->
      <div class="section-lbl" style="margin-top:10px;">Type de demande</div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:14px;">
        <div id="td-externe" class="td-btn sel" onclick="setTypeD('externe')" style="border:1.5px solid var(--cyan);background:var(--cl);border-radius:10px;padding:11px 13px;cursor:pointer;transition:all .18s;">
          <div style="font-size:14px;margin-bottom:3px;">👤</div>
          <div style="font-size:12px;font-weight:600;color:var(--cyan);">Client externe</div>
          <div style="font-size:10px;color:var(--muted);margin-top:2px;">Le rapport est émis au nom de l'entreprise destinatrice</div>
        </div>
        <div id="td-interne" class="td-btn" onclick="setTypeD('interne')" style="border:1.5px solid var(--bd);background:var(--white);border-radius:10px;padding:11px 13px;cursor:pointer;transition:all .18s;">
          <div style="font-size:14px;margin-bottom:3px;">🔄</div>
          <div style="font-size:12px;font-weight:600;color:var(--muted);">Demande interne</div>
          <div style="font-size:10px;color:var(--muted);margin-top:2px;">Une entité du groupe commande à une autre</div>
        </div>
      </div>

      <!-- MANDANT INTERNE (visible si interne) -->
      <div id="ag-mandant-interne-wrap" style="display:none;margin-bottom:14px;">
        <div style="font-size:9px;letter-spacing:1.5px;text-transform:uppercase;color:var(--hint);margin-bottom:8px;display:flex;align-items:center;gap:8px;">Entité commanditaire <span style="flex:1;height:1px;background:var(--bd);display:inline-block;"></span></div>
        <div id="ag-mandant-interne-selector"></div>
        <div style="background:var(--obg);border:1px solid var(--obd);border-radius:9px;padding:8px 11px;font-size:11px;color:var(--ora);margin-top:6px;">
          💡 Le rapport final sera émis à l'en-tête de l'entité commanditaire. En pied de page : <em>"Expertise réalisée par [exécutant] pour [commanditaire]"</em>
        </div>
      </div>

      <div class="section-lbl">Donneur d'ordre</div>
      <div class="field"><label>Client / Société <span class="ai-badge" id="ai-cl" style="display:none;">✦ IA</span></label><input type="text" id="ag-client" placeholder="Nom du client"/></div>
      <div class="row2">
        <div class="field"><label>Contact sur place <span class="ai-badge" id="ai-co" style="display:none;">✦ IA</span></label><input type="text" id="ag-contact" placeholder="Prénom Nom"/></div>
        <div class="field"><label>Téléphone <span class="ai-badge" id="ai-tel" style="display:none;">✦ IA</span></label><input type="text" id="ag-tel" placeholder="06 00 00 00 00"/></div>
      </div>
      <div class="section-lbl">Localisation</div>
      <div class="field"><label>Adresse complète <span class="ai-badge" id="ai-ad" style="display:none;">✦ IA</span></label><input type="text" id="ag-adresse" placeholder="Rue, code postal, ville"/></div>
      <div class="row2">
        <div class="field"><label>Bâtiment / Site <span class="ai-badge" id="ai-bat" style="display:none;">✦ IA</span></label><input type="text" id="ag-bat" placeholder="Ex : Bât B, Site 507"/></div>
        <div class="field"><label>Accès / Étage</label><input type="text" id="ag-acces" placeholder="Ex : Toiture terrasse"/></div>
      </div>
      <div class="section-lbl">Nature de la demande</div>
      <div class="field"><label>Type d'intervention <span class="ai-badge" id="ai-ty" style="display:none;">✦ IA</span></label>
        <select id="ag-type">
          <option value="">— Sélectionner —</option>
          <option>Recherche de fuite</option><option>Intervention d'urgence</option><option>Diagnostic toiture</option>
          <option>Diagnostic terrasse</option><option>Réfection étanchéité</option><option>Entretien annuel</option>
          <option>Levée de réserves</option><option>Expertise contradictoire</option>
        </select>
      </div>
      <div class="field"><label>Description du problème <span class="ai-badge" id="ai-de" style="display:none;">✦ IA</span></label><textarea class="fta" id="ag-desc" placeholder="Problème signalé par le client..."></textarea></div>
      <div class="row2">
        <div class="field"><label>Matériaux <span class="ai-badge" id="ai-ma" style="display:none;">✦ IA</span></label>
          <select id="ag-mat"><option value="">— Si connu —</option><option>Membrane bitumineuse</option><option>EPDM</option><option>PVC soudé</option><option>Tuiles</option><option>Ardoise</option><option>Zinc</option><option>Bac acier</option><option>Inconnu</option></select>
        </div>
        <div class="field"><label>N° Ordre de service <span class="ai-badge" id="ai-ref" style="display:none;">✦ IA</span></label><input type="text" id="ag-ref" placeholder="Ex : OS-2025-0847"/></div>
      </div>
      <div class="section-lbl">Niveau d'urgence</div>
      <div class="urg-row">
        <button class="urg-btn" id="urg-u" onclick="setUrg('u')">🔴 Urgente</button>
        <button class="urg-btn" id="urg-n" onclick="setUrg('n')">🟡 Normale</button>
        <button class="urg-btn" id="urg-p" onclick="setUrg('p')">🟢 Préventive</button>
      </div>
      <div class="field"><label>Notes internes</label><textarea class="fta" id="ag-notes" placeholder="Points d'attention, difficultés d'accès..."></textarea></div>
      <div id="ag-err"></div>
    </div>
  </div>

  <div>
    <div class="card">
      <div class="card-title"><span class="dot"></span>Assignation</div>
      <div class="section-lbl">Technicien</div>
      <div class="tech-list" id="ag-tech-list">
        <!-- Rempli dynamiquement depuis DB.technicians -->
      </div>
      <div class="section-lbl">Planification</div>
      <div class="row2">
        <div class="field"><label>Date</label><input type="date" id="ag-date"/></div>
        <div class="field"><label>Heure</label><input type="time" id="ag-heure" value="09:00"/></div>
      </div>
      <div class="field"><label>Durée estimée</label>
        <select id="ag-duree"><option>1h00</option><option>1h30</option><option selected>2h00</option><option>2h30</option><option>3h00</option><option>Demi-journée</option></select>
      </div>
      <div style="background:var(--cl);border:1px solid var(--cb);border-radius:10px;padding:10px 13px;display:flex;align-items:center;gap:8px;font-size:12px;color:var(--cyan);cursor:pointer;margin-bottom:14px;" onclick="openOutlook()">
        <span style="font-size:16px;">📅</span>Créer l'événement dans Outlook <span style="margin-left:auto;">→</span>
      </div>
      <div style="display:flex;flex-direction:column;gap:7px;margin-bottom:14px;">
        <label style="display:flex;align-items:center;gap:7px;font-size:12px;color:var(--mid);cursor:pointer;"><input type="checkbox" id="notif-tech" checked style="accent-color:var(--cyan);"> Notifier le technicien par SMS/app</label>
        <label style="display:flex;align-items:center;gap:7px;font-size:12px;color:var(--mid);cursor:pointer;"><input type="checkbox" id="notif-client" checked style="accent-color:var(--cyan);"> Confirmer le RDV au client</label>
      </div>
      <button class="btn btn-dark btn-full" onclick="agSubmit()">✓ Planifier l'intervention</button>
    </div>

    <div class="card">
      <div class="card-title"><span class="dot"></span>Interventions du jour</div>
      <div class="interv-list" id="ag-list"><div style="text-align:center;padding:20px 0;font-size:13px;color:var(--muted);">Aucune intervention planifiée</div></div>
    </div>
  </div>
  </div>
</div>

<!-- ═══ TECHNICIEN ═══ -->
<div class="view" id="view-tech">
  <!-- MOBILE BOTTOM NAV -->
  <nav class="tech-bottom-nav">
    <button class="tbn-btn active" id="tbn-home" onclick="showTechList();setTbn('home')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/></svg>
      Missions
    </button>
    <button class="tbn-btn" id="tbn-form" onclick="setTbn('form')" style="opacity:.4;pointer-events:none;" id="tbn-form">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M11 4H4a2 2 0 00-2 2v14a2 2 0 002 2h14a2 2 0 002-2v-7"/><path d="M18.5 2.5a2.121 2.121 0 013 3L12 15l-4 1 1-4 9.5-9.5z"/></svg>
      Rapport
    </button>
    <button class="tbn-btn" id="tbn-profile" onclick="showView('home')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="8" r="4"/><path d="M4 20c0-4 3.6-7 8-7s8 3 8 7"/></svg>
      Profil
    </button>
  </nav>
  <div id="tech-list-view">
    <div class="card">
      <div class="card-title"><span class="dot"></span>Mes interventions assignées</div>
      <div class="interv-list" id="tech-interv-list"><div style="text-align:center;padding:20px 0;font-size:13px;color:var(--muted);">Aucune intervention assignée</div></div>
    </div>
  </div>

  <!-- TERRAIN FORM -->
  <div id="tech-form-view" style="display:none;">
    <div class="card">
      <button class="btn btn-outline" onclick="showTechList()" style="margin-bottom:14px;">← Retour</button>
      <div class="card-title"><span class="dot"></span>Rapport terrain</div>
      <div id="tech-interv-header"></div>
    </div>

    <div class="card">
      <div class="card-title"><span class="dot"></span>Zones inspectées</div>
      <div id="tech-zones-container"></div>
      <button class="add-zone-btn" onclick="addZone()">+ Ajouter une zone</button>
    </div>

    <div class="card">
      <div class="card-title"><span class="dot"></span>Solution & durabilité</div>
      <div class="field"><label>Type de solution</label>
        <select id="tech-sol-type"><option>Réparation définitive</option><option>Réparation temporaire</option><option>Diagnostic seul</option><option>Calfeutrement d'urgence</option><option>Travaux à planifier</option></select>
      </div>
      <div class="field"><label>Description de l'intervention</label><textarea class="fta" id="tech-sol-desc" style="height:80px;" placeholder="Technique utilisée, surfaces traitées..."></textarea></div>
      <div class="field"><label>Durabilité estimée de la réparation</label>
        <select id="tech-dura"><option>1 à 3 mois</option><option>6 mois</option><option>1 à 2 ans</option><option selected>3 à 5 ans</option><option>5 à 10 ans</option><option>+10 ans</option></select>
      </div>
      <div class="field"><label>Suivi recommandé</label>
        <select id="tech-suivi"><option>Aucun</option><option>Dans 3 mois</option><option>Dans 6 mois</option><option selected>Annuel</option><option>Urgent</option></select>
      </div>
      <div class="field"><label>Notes internes (confidentielles)</label><textarea class="fta" id="tech-notes" style="height:60px;" placeholder="Points d'attention pour le chiffreur..."></textarea></div>
    </div>

    <!-- ── CONSOMMABLES & MATÉRIAUX ── -->
    <div class="card">
      <div class="card-title"><span class="dot" style="background:var(--ora);"></span>Matériaux & consommables utilisés</div>
      <div style="font-size:11px;color:var(--muted);margin-bottom:12px;line-height:1.6;">Listez tout ce que vous avez utilisé. Le directeur s'en servira pour établir la facturation.</div>

      <!-- Dictée vocale -->
      <button class="voice-btn" id="voice-btn" onclick="toggleVoice()">
        🎙 Dicter les matériaux utilisés
      </button>
      <div id="voice-status" style="display:none;font-size:11px;color:var(--red);margin-bottom:8px;text-align:center;">🔴 Enregistrement en cours… Parlez maintenant</div>

      <!-- Heures sur place -->
      <div class="field">
        <label>Heures passées sur site</label>
        <div style="display:flex;align-items:center;gap:10px;">
          <input type="number" id="tech-heures" min="0.5" max="24" step="0.5" value="2" style="width:80px;border:1px solid var(--bd);border-radius:9px;padding:8px 10px;font-size:14px;font-family:'Space Grotesk',sans-serif;text-align:center;">
          <span style="font-size:12px;color:var(--muted);">heure(s) · taux 40 €/h</span>
          <span style="font-family:'Space Grotesk',sans-serif;font-size:13px;font-weight:600;color:var(--dark);margin-left:auto;" id="tech-heures-montant">80 €</span>
        </div>
      </div>

      <!-- Déplacement -->
      <div class="field">
        <label>Déplacement</label>
        <div style="display:flex;gap:8px;align-items:center;">
          <select id="tech-dep-type" onchange="updateDepl()" style="border:1px solid var(--bd);border-radius:9px;padding:8px 10px;font-size:12px;font-family:'DM Sans',sans-serif;flex:0 0 140px;">
            <option value="forfait">Forfait</option>
            <option value="km">Au kilomètre</option>
            <option value="inclus">Inclus</option>
          </select>
          <input type="number" id="tech-dep-val" value="25" min="0" step="1" style="width:70px;border:1px solid var(--bd);border-radius:9px;padding:8px 10px;font-size:13px;font-family:'Space Grotesk',sans-serif;text-align:center;" oninput="updateDepl()">
          <span id="tech-dep-unit" style="font-size:11px;color:var(--muted);">€</span>
          <span style="font-family:'Space Grotesk',sans-serif;font-size:13px;font-weight:600;color:var(--dark);margin-left:auto;" id="tech-dep-montant">25 €</span>
        </div>
      </div>

      <!-- Liste de matériaux -->
      <div style="font-size:10px;color:var(--muted);text-transform:uppercase;letter-spacing:.8px;margin-bottom:8px;margin-top:4px;">Matériaux & fournitures</div>
      <div id="conso-list"></div>
      <button onclick="addConsoItem()" style="display:flex;align-items:center;gap:6px;padding:8px 13px;border-radius:9px;border:1.5px dashed var(--bd);background:transparent;color:var(--muted);font-size:12px;cursor:pointer;font-family:'DM Sans',sans-serif;margin-bottom:4px;transition:all .2s;" onmouseover="this.style.borderColor='var(--cyan)';this.style.color='var(--cyan)'" onmouseout="this.style.borderColor='var(--bd)';this.style.color='var(--muted)'">
        + Ajouter un article
      </button>
      <div style="font-size:10px;color:var(--muted);font-style:italic;margin-top:4px;">Le montant marchandise sera renseigné par le directeur lors de la validation.</div>
    </div>

    <div class="info-box"><span style="font-size:16px;">🔒</span><div><strong>Votre saisie s'arrête ici.</strong> Le rapport client sera généré automatiquement et validé par le dirigeant avant envoi.</div></div>
    <div id="tech-err"></div>
    <button class="btn btn-green btn-full" onclick="techSubmit()">✓ Soumettre l'intervention</button>
    <div style="height:16px;"></div>
  </div>

  <!-- GENERATING -->
  <div id="tech-generating" style="display:none;">
    <div class="card generating">
      <div class="spinner-lg"></div>
      <div style="font-family:'Syne',sans-serif;font-size:18px;font-weight:700;margin-bottom:6px;">Génération du rapport premium…</div>
      <div style="font-size:13px;color:var(--muted);line-height:1.6;">L'IA Alptech analyse l'intervention<br>et rédige le rapport client complet.</div>
      <div class="gen-steps">
        <div class="gs active" id="tgs1">🔍 Analyse des zones et observations</div>
        <div class="gs" id="tgs2">📊 Calcul du diagnostic et du score</div>
        <div class="gs" id="tgs3">💶 Budget prévisionnel 10 ans</div>
        <div class="gs" id="tgs4">📋 Rédaction du rapport client premium</div>
      </div>
    </div>
  </div>
</div>

<!-- ═══ DIRIGEANT ═══ -->
<div class="view" id="view-dir">
  <div class="dir-stats">
    <div class="ds"><div class="dv" id="dir-stat-total" style="color:var(--dark)">0</div><div class="dl">Total interventions</div></div>
    <div class="ds"><div class="dv" id="dir-stat-valider" style="color:var(--pur)">0</div><div class="dl">Rapports à valider</div></div>
    <div class="ds"><div class="dv" id="dir-stat-cours" style="color:var(--ora)">0</div><div class="dl">En cours</div></div>
    <div class="ds"><div class="dv" id="dir-stat-envoyes" style="color:var(--grn)">0</div><div class="dl">Envoyés ce mois</div></div>
  </div>

  <div id="dir-valider-section" style="display:none;">
    <div class="validate-box">
      <div class="vb-title">⚡ Rapports en attente de validation</div>
      <div id="dir-valider-list"></div>
    </div>
  </div>

  <div class="card">
    <div class="card-title"><span class="dot"></span>Toutes les interventions</div>
    <div class="interv-list" id="dir-all-list"><div style="text-align:center;padding:20px 0;font-size:13px;color:var(--muted);">Aucune intervention enregistrée</div></div>
  </div>

  <!-- RAPPORT PREVIEW -->
  <div id="dir-rapport-preview" style="display:none;">
    <div style="margin-bottom:14px;display:flex;align-items:center;gap:10px;flex-wrap:wrap;">
      <button class="btn btn-outline" onclick="hideDirRapport()">← Retour</button>
      <button class="btn btn-outline" style="font-size:12px;" onclick="document.querySelector('.chiffrage-card').scrollIntoView({behavior:'smooth'})">💶 Aller au chiffrage</button>
    </div>
    <div id="dir-rapport-content"></div>
    <div style="display:flex;gap:10px;margin-bottom:20px;">
      <button class="btn btn-outline" style="flex:1;" onclick="hideDirRapport()">← Retour</button>
      <button class="btn btn-cyan" style="flex:2;" onclick="sendRapport()">✉️ Valider et envoyer au client</button>
    </div>
  </div>
</div>

</div><!-- /app -->

<script>
// ══════════════════════════════════════════════════════
// ── SHAREPOINT / MICROSOFT 365 INTEGRATION ──
// ══════════════════════════════════════════════════════

const SP_CONFIG = {
  clientId:  'ce885b92-7692-4ca5-aae6-756a5e94a792',
  tenantId:  'de95b546-4d79-47f1-aafe-8926ca63e424',
  spHost:    'https://martincharpentefr.sharepoint.com',
  sitePath:  '/sites/HEXA',       // sera créé automatiquement si absent
  listName:  'HexaDB'             // liste SharePoint qui stocke les données
};

const MSAL_CONFIG = {
  auth: {
    clientId:  SP_CONFIG.clientId,
    authority: `https://login.microsoftonline.com/${SP_CONFIG.tenantId}`,
    redirectUri: window.location.origin + window.location.pathname
  },
  cache: { cacheLocation: 'localStorage', storeAuthStateInCookie: false }
};

const SP_SCOPES = ['Sites.ReadWrite.All','User.Read'];

let msalInstance = null;
let spAccount    = null;
let spToken      = null;
let spSiteId     = null;
let spListId     = null;
let spItemId     = null;   // ID de l'item SharePoint qui stocke DB
let spSyncActive = false;

// ── INIT MSAL ──
function initMSAL() {
  try {
    msalInstance = new msal.PublicClientApplication(MSAL_CONFIG);
    msalInstance.initialize().then(() => {
      // Gérer le retour de redirection
      msalInstance.handleRedirectPromise().then(resp => {
        if (resp) { spOnSignedIn(resp.account, resp.accessToken); }
        else {
          // Vérifier si déjà connecté
          const accounts = msalInstance.getAllAccounts();
          if (accounts.length > 0) { spSilentToken(accounts[0]); }
          else { setSpDot('idle'); }
        }
      }).catch(e => { console.warn('MSAL redirect error:', e); setSpDot('idle'); });
    });
  } catch(e) { console.warn('MSAL init failed:', e); }
}

// ── CONNEXION ──
async function spSignIn() {
  if (!msalInstance) { alert('MSAL non initialisé'); return; }
  if (spAccount) { spSignOut(); return; }
  try {
    setSpDot('connecting');
    // Popup d'abord, fallback redirect si bloqué
    try {
      const resp = await msalInstance.loginPopup({ scopes: SP_SCOPES });
      await spOnSignedIn(resp.account, resp.accessToken);
    } catch(e) {
      if (e.errorCode === 'popup_window_error' || e.errorCode === 'user_cancelled') {
        await msalInstance.loginRedirect({ scopes: SP_SCOPES });
      } else throw e;
    }
  } catch(e) {
    console.error('Sign in error:', e);
    setSpDot('error');
    showToastMsg('Connexion Microsoft échouée : ' + (e.message || e), 'err');
  }
}

async function spSilentToken(account) {
  try {
    const resp = await msalInstance.acquireTokenSilent({ scopes: SP_SCOPES, account });
    await spOnSignedIn(account, resp.accessToken);
  } catch(e) {
    // Token expiré — re-login silencieux
    try {
      const resp = await msalInstance.acquireTokenPopup({ scopes: SP_SCOPES });
      await spOnSignedIn(resp.account, resp.accessToken);
    } catch(e2) { setSpDot('idle'); }
  }
}

function spSignOut() {
  if (!msalInstance || !spAccount) return;
  msalInstance.logoutPopup({ account: spAccount }).then(() => {
    spAccount = null; spToken = null; spSiteId = null; spListId = null; spItemId = null;
    spSyncActive = false;
    setSpDot('idle');
    document.getElementById('sp-sync-btn').title = 'Connexion Microsoft 365';
    showToastMsg('Déconnecté de Microsoft 365');
  });
}

async function spOnSignedIn(account, token) {
  spAccount = account;
  spToken   = token;
  setSpDot('connecting');
  document.getElementById('sp-sync-btn').title = `Connecté — ${account.username}`;
  showToastMsg(`✓ Connecté en tant que ${account.name || account.username}`);

  // Initialiser le site et la liste
  try {
    await spEnsureSiteAndList();
    spSyncActive = true;
    setSpDot('ok');
    // Charger la DB depuis SharePoint (priorité sur localStorage)
    await spPullDB();
    // Lancer la sync toutes les 20s
    setInterval(spPullDB, 20000);
    showToastMsg('☁️ Synchronisation SharePoint active');
  } catch(e) {
    console.error('SP init error:', e);
    setSpDot('error');
    showToastMsg('Erreur SharePoint : ' + (e.message || e), 'err');
  }
}

// ── TOKEN REFRESH ──
async function spGetToken() {
  if (!msalInstance || !spAccount) return null;
  try {
    const resp = await msalInstance.acquireTokenSilent({ scopes: SP_SCOPES, account: spAccount });
    spToken = resp.accessToken;
    return spToken;
  } catch(e) {
    const resp = await msalInstance.acquireTokenPopup({ scopes: SP_SCOPES });
    spToken = resp.accessToken;
    return spToken;
  }
}

// ── GRAPH API HELPER ──
async function graphCall(method, url, body) {
  const token = await spGetToken();
  if (!token) throw new Error('Non authentifié');
  const opts = {
    method,
    headers: {
      'Authorization': `Bearer ${token}`,
      'Content-Type': 'application/json',
      'Accept': 'application/json'
    }
  };
  if (body) opts.body = JSON.stringify(body);
  const r = await fetch(url, opts);
  if (!r.ok) {
    const err = await r.json().catch(() => ({}));
    throw new Error(err.error?.message || `HTTP ${r.status}`);
  }
  if (r.status === 204) return null;
  return r.json();
}

// ── ENSURE SITE + LIST ──
async function spEnsureSiteAndList() {
  const base = 'https://graph.microsoft.com/v1.0';

  // 1. Récupérer le siteId
  try {
    const site = await graphCall('GET', `${base}/sites/${SP_CONFIG.spHost.replace('https://','')}${SP_CONFIG.sitePath}`);
    spSiteId = site.id;
  } catch(e) {
    // Site n'existe pas — on utilise le site racine
    const root = await graphCall('GET', `${base}/sites/${SP_CONFIG.spHost.replace('https://','')}`);
    spSiteId = root.id;
    showToastMsg('ℹ️ Site HEXA non trouvé — utilisation du site racine SharePoint');
  }

  // 2. Vérifier si la liste existe
  const lists = await graphCall('GET', `${base}/sites/${spSiteId}/lists?$filter=displayName eq '${SP_CONFIG.listName}'`);
  if (lists.value && lists.value.length > 0) {
    spListId = lists.value[0].id;
  } else {
    // Créer la liste
    const newList = await graphCall('POST', `${base}/sites/${spSiteId}/lists`, {
      displayName: SP_CONFIG.listName,
      columns: [
        { name: 'HexaKey',  text: {} },
        { name: 'HexaData', text: { allowMultipleLines: true, maxLength: 100000 } }
      ],
      list: { template: 'genericList' }
    });
    spListId = newList.id;
    showToastMsg('✓ Liste SharePoint HexaDB créée');
  }

  // 3. Vérifier si l'item DB existe
  const items = await graphCall('GET', `${base}/sites/${spSiteId}/lists/${spListId}/items?$filter=fields/HexaKey eq 'main_db'&$expand=fields`);
  if (items.value && items.value.length > 0) {
    spItemId = items.value[0].id;
  } else {
    spItemId = null; // sera créé au premier push
  }
}

// ── PUSH DB → SHAREPOINT ──
async function spPushDB() {
  if (!spSyncActive || !spSiteId || !spListId) return;
  try {
    const base = 'https://graph.microsoft.com/v1.0';
    // On ne stocke pas les logos (trop lourds) — on les ré-injecte au pull
    const dbToSave = { ...DB };
    // Retirer les logos embarqués pour économiser l'espace
    if (dbToSave.groupe) dbToSave.groupe = { ...dbToSave.groupe, logo: null };
    if (dbToSave.entreprises) dbToSave.entreprises = dbToSave.entreprises.map(e => ({...e, logo: e.id === 'E-ALPTECH' ? null : e.logo}));
    const payload = { fields: { HexaKey: 'main_db', HexaData: JSON.stringify(dbToSave) } };
    if (spItemId) {
      await graphCall('PATCH', `${base}/sites/${spSiteId}/lists/${spListId}/items/${spItemId}/fields`, payload.fields);
    } else {
      const created = await graphCall('POST', `${base}/sites/${spSiteId}/lists/${spListId}/items`, payload);
      spItemId = created.id;
    }
    setSpDot('ok');
  } catch(e) {
    console.warn('SP push error:', e);
    setSpDot('error');
  }
}

// ── PULL DB ← SHAREPOINT ──
async function spPullDB() {
  if (!spSyncActive || !spSiteId || !spListId) return;
  try {
    const base = 'https://graph.microsoft.com/v1.0';
    const items = await graphCall('GET', `${base}/sites/${spSiteId}/lists/${spListId}/items?$filter=fields/HexaKey eq 'main_db'&$expand=fields`);
    if (!items.value || !items.value.length) return;
    const remote = JSON.parse(items.value[0].fields.HexaData);
    spItemId = items.value[0].id;

    // Fusionner : si la version distante est plus récente, elle gagne
    if (!DB._version || (remote._version && remote._version > DB._version)) {
      DB = remote;
      // Ré-injecter les logos embarqués
      if (DB.groupe) DB.groupe.logo = LOGO_BCNC;
      if (DB.entreprises) DB.entreprises.forEach(e => {
        if (e.id === 'E-ALPTECH') e.logo = LOGO_ALPTECH;
      });
      // Sauvegarder localement aussi
      try { localStorage.setItem('hexa_db', JSON.stringify(DB)); } catch(e) {}
      // Rafraîchir la vue active
      const v = document.querySelector('.view.active');
      if (v) {
        const id = v.id;
        if (id === 'view-dir') refreshDirView();
        if (id === 'view-tech') refreshTechList();
        if (id === 'view-agence') refreshAgList();
      }
      refreshNotifBadge();
      setSpDot('ok');
    }
  } catch(e) {
    console.warn('SP pull error:', e);
    setSpDot('warn');
  }
}

// ── STATUS DOT ──
function setSpDot(state) {
  const dot = document.getElementById('sp-status-dot');
  const btn = document.getElementById('sp-sync-btn');
  if (!dot) return;
  const states = {
    idle:       { color: '#cbd5da', title: 'Cliquer pour connecter Microsoft 365', icon: '☁️' },
    connecting: { color: '#f5d98a', title: 'Connexion en cours…',                 icon: '⏳' },
    ok:         { color: '#2a9d6f', title: 'SharePoint synchronisé',               icon: '☁️' },
    warn:       { color: '#c47d0a', title: 'Sync en attente',                      icon: '☁️' },
    error:      { color: '#e04444', title: 'Erreur de synchronisation',            icon: '⚠️' }
  };
  const s = states[state] || states.idle;
  dot.style.background = s.color;
  dot.title = s.title;
  if (btn) {
    btn.querySelector('span:first-child').textContent = s.icon;
    btn.title = s.title;
  }
}

// ── OVERRIDE saveDB ── (push vers SP à chaque sauvegarde)
const _saveDBLocal = function() {
  try { DB._version = Date.now(); localStorage.setItem('hexa_db', JSON.stringify(DB)); } catch(e) {}
};

// ── STATE ──

// ── EMBEDDED LOGOS ──
const LOGO_BCNC = 'data:image/png;base64,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';
const LOGO_ALPTECH = 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAARgAAAB9CAYAAAB5wHzRAAAo5klEQVR42u2deXhT15n/v++590qyvGGzQ5Y2IWwmaRrTbAUkGUhICmaLnEzbNE2blqb9TdpJmq7TSup0mWmbTknbmaHTJek6lRKwzR4SJBGaJg1uGmKbfQ2rjW28yZLuvef9/SHLGDBhMxTI+TyPH7Cse++55577Pe/7nvecAygUCoVCoVAoFAqFQqFQKBQKhUKhUCgUCoVCoVAoFAqFQqFQKBQKhUKhUCgUCoVCoVAoFAqFQqFQKBQKhUKhUCgUCoVCoVAoFAqFQqFQKBQKhUKhUCgUCoVCoVAoFAqFQqFQKBQKhUKhUCgUCoVCoVAoFAqFQqFQKBQKhUKhUCgUCoVCoVAoFAqF4vQwEwIB0Y9nJARYqIpVKBTHC82lfD6FQnH5CYpn2a5hty+uvRUAzs+SYQIzzaze7560eKNHiYxC0X9cdi5BACAAIKaPOYTx+B3P/3kIQiF5rqIQYBCIuJ3Ts0lzfemDkddKQMSB/nW/FAolMJe8uDCLEJH0Vu+eysQThTBYiMIFCAQEgngngenzb4FAQISI5KTK3eOZaJYQjqPCyF/gCUfzQsEgK0tGoXi3CAwzhYjknZWbRoDwUWYkGSIhNOfNd9w4qxwhkn0GaTMicbJYMFMoGOTS6v1uXZefAkkA3EXkGpHWBjwEIkYwqARGoXi3WDB+Zk0XzkcY7AazDbAuhLNd093+28OvjMqIzAmuDREf92/WegkGCUScB/PDLHENgCQYhhCiXdNyfLeF/zIJoZBUI0sKxRUuMAFmASI+tOztUiLxPgZ1EkgAAEmLBbkcwsiZd8JBAgCmLt832rNiR/zW364oAGcCumCmUCgkJy/ZdzUEfBDUTkxaxrBhEporreu580o3bDAQIqmaieIkqzibJsFMgHKlT4V+ORSyPhLpDuzao9Id7WzkFxx71iAiQopYv2rUwoXO7Z//fArM5InFRDxE0pLmf+UMf88UM9H6YxB9whON6kMaGzkC2JpTXJdubXfoTleaHAZBcsbWIZhEYiD2dA4CcBDMdKIF1K+NFQCCIISIAZz1dfzhsAb4EfFDnm85A8wiFAQQxDu6iIFgELFYTAxpbORIRYV9qnvzRyJifJ2fETzHAgWB+pIIRerqGKGQzJ43AFAIOHc3NhjknrjdGXQigQCLmDcm4rGYBPV8nxEK9TyDhsGDKR6LyZ5yntDh+UtAkTrwuXZamecMnLK+L0EuC+X1h8NapKLC9q7cPzuxf8/HHHkFR/WCAp0tO6sxhmm2HhhpbflKpKLC9kRZj/vI8lRuf9IxYOD3zfbWJLkcrkTLngdeq7jjT+PDtY76ignpu9Y2lra9vecrANpdQ4ZpbJoAJCA02Ga71Y4jT7w513f0ggrMlUCABYLgK7KOAgERCAYROiYqmFm9390u0gVItekwnEnkHzwa9/msY+2Vtf4Q+yuBy8O0637B717ZMDzR1fIfiYMHRO5V16YhBAQR23Z6cNpue+a1eaWLSxdtMGoWTDTLqnbcBKfrdWnbGksbQneQlW5tTVltN/113m37A0FQ/d1vOxuazH/v2LNnuHv4yHbN6SSWYIY90DLbX3pl/s0/QSAg+uyR+sHtCwE8ZVn9KN2Z+1urq2O323A8tOqeG9IgwhlZMtmcoOrNQTL0CQ7h/NQLM65pPhdBzI7QearrH9Fycj9qJTqYiPoImgMQxBDUAaHVStuqfnnmuFd6P6dAgEUoRPKDVXUlhtP1XTZNF9gmZjqpvRFl3HQG5Il3TMQMEiwcThNmKhCdOa4GAKYs2zJO07SFtpk2znWkjwCp5eaTnWhfGC8vqcx2Ysd3bKxFKsgGAM/S7RNI49nM0sdSjiHmgRkPgJMg/QAR3mKil0BYFr939L7uyqIAg0JEcnJVbZmreOgTZkvj92Pl4+PZ+j7T9u+P1BmHc8RCMLuoyf1o/OPvSZ1xO1Eu0ulaAzGYaTXRQc+KPT93Dx/5KQIKAIa0TVhW54vWEV4aCLCoL4LEBjbkwT3PapruYDNlE0iTZsp25A0sspoTvwLRXcsWbdBr7pzY5Vu5779yR179BYYYwswsIUnaiTdTtvWbnhGobjO4392+igrJlbXf1nJyb9Nc7ts6W4+sBNGznmhU790jvpPoTl99MDdF8vOugUMLE4f3LALwgj8CEQHssytPtrPhCtfg4Z50WwuE0Pq+NACh6YAQH0q3HPmyd/nW36ZN+3OvELWDmWKxmEAIUjDf7Bo0vNxOdABC9HUPsFNdADM0Vw7Ql55JG0b+ACT271wNoAYAhOSbcq6+drrZ0Qo6RRlP+87aNhxFA9Gxo34rgMqGwYOpL3HxVNWOgu4MEuT9zuKhOrOE1X4UdlfCZFCagDw9L2+Mnps/hi3zvnRr03c9K7b9Jq3Rd/9yNzUsq9mgA5DEeNgxcNC9qebGJgDxWCwmMubyGViHRLKhqvYa3eX+DEjAovbvgmgbAiy63WolMP0lMnGi9WVVO7ZJod9sWYkcy+zY8WrFxLcA4Lpso6jc8R2jaODNZmuzRUR6d2BFk4kuy1U8YvoHwn95/PWKiT/yRKN61HfVlvL1jV/qOJqcaHFqgGm173/1zcoNF8JqOd5agPRVvjmGDcecVEuDrTlzQLZ80hON/j4ei53xtdOtTQSnaDU72/KEEOdc5og/09g1th9MHj54q5VKANI+2TrQNAgpyQYGCSHuIiEqjMKBD8qmw1f7a/nu8UFYoaDXBoCy2SV/jC2t20OGM9c2TT6mK1IQCUmQgwj0C5BwmImOBaTTXrKkJunYfWhElDzalOwakXil5/iktbxr386HpIQTbDPoHCxxBtuJDkiHYzUAxL3eHkH2BKJ6pIKsKdWbPkyG8bSjsHhguuUIkk0HlwNUJVj+DYZx2OxKpHXdlWt1tl1rJ9o+CIg5wpUz0cgr+Dw3HLhv0oqt71+/9PdN3RZTymxvswU4da7PyO7qNBkQuIxCypePwPQSmbVEhwGs7qvH8S3ZfSe5HF8y24/aINKO7zClhpRlO5wF3/tA5OXVcd/kOk80qldPGtwOINqXhXBhgtYggKRNdf/icOc50m0tSTvZZRh5hSVmh5iFUGjJGVkxxwqrEUg777oFsHb2TYcBLD3Do37pXb4pnG5tftZZPMR7eGf9k5FQyXf8JaxFALvbBVh/qoOnhTcUpp05JARpwrJWx2e/b9+ZXDReMaEDwG/6vW11i0s85LOmVG58TM9xLxSGA+mWI+uI6auxmWNfOcXRuwDEEAh8z3f7h+ekmtPfIrDbmbRkL5+MiEhjovORB41AgsFKYC60yPgjEQEAkTp/d1Q+AgCQmvy64XKR3ZbMjC8dfyyRZbMzb6BDNnd+CcBDQxq9nB2VqI9EaLzfzyGiCxegC7CI+CE9K7Zexbb9EZY2iOifmfkzwul6P3W2fRHAkrOxYvo73uUHRHd1npKGwTEa0jhYRD407nlPVe1olvZ3iflzd1ZuejoyJ+MqgYizI1y92dlSI64rKpVHxN8GZD8Tuiz0h/lgUQtES9HJrkM2FpKNbXiiMe38b9aLuBd29lln4jA+a0rlxrm6O38hCQGzo/XnQxIbPxupqLADzCIWiwmv1ytDwWDPSJS/JEINgwdT3Oezoggt9vw6usIxokhbU35zZ+miDUYNQu/aVAf9siw1ER8XY2CmCJE9Y8XWgqSkW82jLQBBoI/OggkCaZMhtEmlizYYkQoykRnyvCiNwOONiTj5LK6q+5xr0LC8ZNOh7evKS34xpbrOLc1UqXA47/RW102NlZe81DvI+A+r29OIZYBZxJZu+d90a/OXdXf+cCQTpQBi2ThQn0OqgQDXLJgoPc+/2fM3SZodqSA7EGD++YLTBT+J4z5Y/XrfgYCI1NXx5JX1w2HRz4UzB+bRpj/EZ5csQCAg/GHWQkQ2ABnPHpOJzXHkZEs6mS1o3uj2d/VI0pWRpdqdC9HV1FVARLmJQwfBto2+BOZYsh3ynUOTrmyw8WJZB3Gv1/ZUbx4E4BFpWSDmhQCQdvDvrI7WA1pOLrPkLwHAeP8lbguHSIYIHC8fe4QYW3V3HjPkdVkL53JqQv6SICEUkpTGN11FgwelW5t3IMULMgmbQZyp0EcqyO5pY8C7fpj6ShEYBoCUs7NJaEYzNMHpo63QDONk8SBiCMEAN77yxgc7gYuX4+KJxbTMteQjzuIhg9Itjfu72jp+A2bx6owJzQxaxFISGca0yUu33BrqcTEuYbjnnxSEIGI4Lrv2EwiISAXZnhVbryLCgzKdAjEH4xUTOjzemDjrxDgiVjkwV5LAELE/zNqrFXd2Sct+Mf+6UdRxaJ+Vbm8HnTg8yrDJoRPDXoEQyf7x5c/CeonW5oH5s5lii0V/ffD2tvGROh3MZJrp/7E6Wpv13HxB0nry0u8BmUDApzewAcgRMp0GQTRebs3H4/VmcnEsc56jeHBuuq15TyqV/3z2mSmZeLfFYPpgvD8zY1pG6r6tOx3zC667Pi+x/4BZMHpUJkOXBBPI1nJcjq7Www22TDwFZoqfZb7I+VgvcZ/PQlXdg8aAgVenW440a7B+DjDV1wUtz+BGLT7f1+CpqnsGzI+TppeXrdg6PnLvDZvOKinrIlK6qEavWTDR3HygfqLmcr/HbG9Jm5b1dwCIx7wXrrzM5ImhXzqGeCwohzQ2crde+oTuYJBY82rFNV3ZEaX+LbskBAKisbFRnNlCaTGBQAAs6LK0ia4YgQkRyQCzCFVM2O6p3DLXVTzkj7kjrh0kk10gYYCEBjJ0Ldl++G1pdt73eoXvUHei0kV4cZniXtgzVmx1Jsz054VugCF/s3b2TYczQcGQHUcQYKb08vqn0d62wMgvzDXbmp8A6JP1kYs3ozvALOoBOt0oUne8wcxYYvi2kVcokkcORV+Zd+OOCy6IRBxH/wV5I8gEZxuwaYy0TBIkNgAgeAGE+r3sFkIhWQ+kz7BlSwDgJfclSRNKYC4JkSF6cfIf37oFAwZ+ltn2MNsDJNtNsqvrxbZ9W/5742fnNyAzQ/vijBxFY1qcfFaietN8I79oTKqlMWEI/ScA0/i6bjcoRNJfwlqkomTPlMra/wPwSQjtfs+STf8WmYs92fT7i1GHZ3xfK7ZeRZb9A82dV5ZubZIg+Q3g2OTUC2G5gIgnLdtYpJPzE8zIgWWdk6PPEKy7XGylO5asm3njptaCukKkaJBMp2BL3geAhzR6uf90RQi7qxPM9KEpVXWx7mkYZzAdBAQCA+QCWICZVaLdpSEybwP4avfTPT7YG7h44pIxw2PSHw5rh9l+XHO6YLW3PPfS7Ak7/eGwFuo1jJsZNWKCvvUps7Pto0ZeYW66reUxgB6PIarhAg6lZ62OKUvr7tVduR+1uhL2OzR6BnExW9YHHcVDBlgdrSzT5qfWzbnx9e7zXBC30xOLaXHAEqZxT+4No39oth89j6kCFhzFRWjbsmkUgE90dQon6WywtCE06jxm2/STNoKILQtCN0YaBQNGnr1nZcNsa7l4I55KYE7TCwcCwuP1irjXa2eT8zyxmNb9+0UTl2wuS0NV/UzdnVuaPtpkQeI/M2uIRE4qtz8c1iIzKzZ5quqqQeQn0MfvWL393+N3Xd8IXJiJlwAQCnb3tEzf1PMKbxOGC5o7N9Og++oxbYl0azOs9tY/m8lkYP3ckpf84bB2ocQlK9QAoLH1Wue+HWFOpXLOdbSGJdhKdICF/ScAEIYwmW2LhAAz5XQ/vX40vqTU3LmwOtpXppob/xPEOtvytM+ShUFEUgqmEYD8FYgIKpP3UlCZkIwfexmpv/32MyWby8Isv6i78zjV2bEyPnfC3zM9/anW9WBi2vIDs7N9np5fWMRtLY+CKOSJRrX4BZsjFcwaJ10ylbTM1qMbzdamX4AycZbj0ASEZiSEtDe9dO/oNzJCevJs5AvxTAEgOu/GHQDu79dz5485Su2bm4XhHER2y0igf3N5CMykGyDIPfHZE9actfUWfm0YXHkM4LLKL7pyBeZEC/UfQDb7c/KyLVM0XZ+SMenpqUycou+Gkk1JD9HY16dU1q2hXHE3ES2YFt7w4xe9pW0Xem0aIiE1V46eam16+uXZE549s/u8COJyQizGH4E4fxfGj0gdOBAEQkSWp6p+hzCM0dDFzReo3GASDn+Ytfa8bXp+xw2n7fB2tkBcVwR5xLGx8HKcb/DuEJjsmiEXeaAva72QZT5pFA1CsvHgX9bNmRBHgMU7ZYZmxYeJf2B3dc7Q8wqGW0J8HEQLPdGofkEtMWZiZgiG8ESjencb6fN6Xq9XhojkRV9h7WymM5wBMW9UByAZvJ5t6x62eXrpog1G3FtqdVsM/dluOFJBticapVX3jj79PQSYaxaQ9FTVXpb5OFf0gtae6C5Xj7AQceb3i7N+anc8gidX198iDMcMu6uTmOlpIDMf6Z2O7Z6TI16ePWGtnU69QprO0paP3R5+JSeT+HVx7qF7NrcV9/n6/LkUc3POLbbTnbOjySXpliZTzy0Y7R6Wc2+mzUQ1KJTAnKD6IsAskMQw34q9a30r9q6fuubwa9QuPwQQewLRi2W5sZD2E0ZhkW52tG1uMnkJmCnu8522N6rPrhcr6IcylSQ9L/86p6vggUyjj6lG36+xnUxwfd3MGzdJ26rWc9wgUKh00QYjO9teVZISmOw7TR5vTISIJCflnSR0r1E46INaTt6tENqHwEzxkM8KXMDtSALMIlLhl5OW148m3ZgnTROk0dP1FRPSnlhMOxOTO0JkIxAQlHd4qdXVuVEYDgmmf/FEo/o/bCmHK5jxfj8DTETav6aPNiWNgsL35Q1z/zBSQbYnFtMCfGbtxR8Oa92CpETpiovBdK8TE/FVWN7qXY8bBQOesjrbkWo+HALw0ZxhVz/sXbankH+96yOhhyl5oYKT9cgsKCXs+i8YRcWudMuRt00pfne2UxM8Xq+I+3zWlKVbnpLp1LNajvtGq21oOUKhxaUjZhk1wHEjPEKQ8IdZA6D5w6cPG1zOC1N33+d5k62DnhSB8orNkytrv6gDP9VcOY95lm46GveNC8QBZHak8HKkLsjZCbYAEAiCYt6Y8Ma8MnRCbK1jaz4pgblC3CIAHKmosL1VO77vKB78pNXR1iWl+bH4rOufm7Js15/SjQeXuIaOnJeig8s8S3bdF5n73qP9vuZKICAiRLbn+TevAugjLCUYvOiVOePbz26VOiDu89pgJnpmd9gq6viGY0Dx9Uh0Pglgcc2nS20s6P1tgk1o776XK36C3oVYJyezI0VUj/sm/MxTWXuNUVj8JdL1b3qWbSnRSf/aS77rtx5zq47NIQgBjFBmnZgp1fV3CN34FptpLccw5tx2zw0dNQuUwFzm2tK9Ir43qlP1rl+6Bo/4WLq18YiV7KpYN+eG6G1/+MvQdTPfu8nz/NZpqcaDlc4hI6amGg++cGflpjmROXSgPye1ebxeEQ+FJAzjUaNgQH66taVJ6sbPs/ORzu5sxJ5YVI8/7Et6qmqfZst8Wjict3oq66bFiV7s+RZBsrRskcaUKcvr82ALXdjmKd0oG4CR45Z2V9vr8bnvz2zLEgxmdUoy2MZFW5eRbD5LQRwfrnUMydF8zJQjiCVLeW47CzgcbFBq/QszJvTsxBD3+Sx/OKxF5kz48pSldU2a7vy2s3jw/HRz492e5Vv+xERVmtQ3ykSiCYNzLcOSznTKGiEYt4IwH4RZzoFDkTy8z2xL23khoD1jXYM5s7UCn2ddsRKYi2wqh4jsaeENhVbn4D+6ho64J9V0aLfVlZz/8vwb/japsu42R35+2FO16Zn47NGBqYvr70417HvOOWSklxsPrp20uL48Pm/81rO1Lk7losWJrGlrdhSmE8n/p+fmkdna/Oz6e8c1eqJRPU5nf/64N2PFdP3utWddoH91D79mSOLg3icB9AgMA0UkhKYXDPh30vSsUJz6ods2jIIidL6dqgQwtzsFv1uQyG3kFmhpHLrgbUOmBWkuPVdz5cDsMk8rEtlnNMSlzXINveo5q7O9790KzuRRde8q0Pn2zp8AeCw7DSFryfjDYS0yq+T7k5e8tR6y6VvC6ZxqFBZ/0u5KfDJ9tNmCUxyhtq50GpwrdGOgo3gQSGhINR02U02HlthShl6ZM+HA+HDYUQ+kQeQy3AVaEuQ8p/IKIt2ZY4AErGSHEpiLgSca1SM+sib/8a2rrdwBz7sGD/9AsvHARrba5r88f8J2T1XtDOFwhtmy8vW8vG9OWbop/6VZ4x6/Pbz3Xnl4/x9zBo+YnWppeMm3ZPucqG9UTXbDtnPvYAhgJjO2OwWiF5KNB0dKi34IZooHg/Icz8n+cFiLPFjR5q2ue8xOp77MRNVZcY3UITH5lrpfStP8oEwmTabTByOJWUrLJCa5CgCGNDayv6SEIgAk28+mmg53CbajwLH0/H4lFJJgptyVKxsS1nv/yJ0drgIU7wEzhejUPbTX65VxAGRjd7K5oY7T574vEhNLZptIyjcydXD8xMaMyLAWmUuvAJhWtmqbL914+D5mOZkEjRKGYxgJDdJMgaXdmGo5shGEFzVC9dp7R9f3xAQBKwSAWYTNo03vIY1/0/teTl9XmWkuFNv9tt3eFWGwTU3uty+XzQDp8hWXjBhMimy+SXfnLnYNGnZ98siBdcKyKtbOvv7wpMq3HtCd7mdhWw5pmzYg2Mgv1O3O1mdis8Y/DGbyLN/za9fAoQ+l21qarY42/8vzx649b5G5cBFsAtQqab3bbukG1vPawR1ba86qHeeNLuWO/BrKW7qU46GQdVr3G712rWSmaVWbh9tOvchmdsA2OxwuV8OL069vPe6YIKD2Nb+MxQUAplRu8/lW7Wu4+9UUe5ftrvKEa/MAwFNd9xnf6p3sW7lDeldss73LtrB3+Vb2rdyRnr7uMHuXbVkyY8VWZ+a7u3581/oOLlt1IDGlcvtcAChdtMHoj2Bvr7VZ+y3WBCKcOMQeYD52rbP46WuoPpDNIbpIuR891ztLV7T/dPvMzuUPh7XuzOZTPm9PNKqfMv0h0F2n55EeEeBzqCtlwZxdeT1R1uI+srxLtt0vXO5n9IIBrnTz4Wd4w55PxUM+y7O0/qt6Tt53ra5OmW5uILYs0vMLwWYadjIBzZ1v5Yy4Rrc62mLW0dS89R+5qcWzdFfQkV8UsNNd0k52PhIvH/XrS9eSURxru/1h0J21VUgIBCiQDYoHgdCVui/3u0pguie4RSrInlK98zHdlbNQc7qRbm15Kl7+ni8CgHf55u9rOflPWp1tNiSLrU89QW2banDtx59Ex+a/48ifV+GajzyGEeUftwjQbTP1t0RX1+y/zn/fPk/V9i/ouQX/SULA6mh9IlZ+/Y/UJuYKxflxeZhb3WuXRirI9lTv/I4jf8BC0nSk25q/1i0u5Fm66Re6u+BJs73VgpQCRCQtE9JMAVJCWhZkOtW9nYmmp9tbLc3husWd417reW7j2PjsUT+2OtseZjNtOQYMesq7dMe/RSrIDnTPtFdNRaG4AgUmwJxZZCkYJM/SXb9wFA36mp3qkum21s/EZ733e55fR12eZVsiRv6AT6bbWiwi6NlFea6a/whu+Px/oKDkAxg2436MfvwHGPD+SZCpBISu6WZnuyV04wZy56ydvPiNW+OzRz1jJTr9ZqKj01k87F89S3f9tGdC33G+81kIDjP1xGNO+DwQ4D4/P3mrkl6fnZiGHggIfzisZcp37Fw9sYAT40CnKM9JsYNTlO/YZ6epg2PxBjrp3vq4x7O6fu8Y1wkxr5OOOVX991HeM77f7L0x04kxkez3+9puptc0gpPiZyedJ/t573rpdV3lIvUD2SxbT7g2j9wFf3AUDZxltrckZDL1UHzO9c9N+v3LRdqAoRHDnTc1Iy6k9761Hf8dQMe2jbjq/s+ic1sdml9fi5HzHsGwGf8Eq7MVJDQwS1tz5mgsZavs6vKvm3/TmimV23y6MydsDBg0KHnk0B+Qt+uhuM9nZYYGu/32Cz1M2Nf5A2e5ot1FW9T8nG/y3TMydpkMK/c3+qX4IPyRiIjU+TlSQfbk53cPF05a7CgedHu6tfkI0sn743NGrb2zsmaEbuRXajnuD5htLSYRGTgh6pdq2I/E3m2wOtqQajqExN5tmXVNSfSsbUokNDuVtIVhFGpud7WnsvbB+Jwbnpu0ZPsMbmlcnDNkxIdTDVzoCdc+4A0iEQJJ+P0aMktDnnKtkOw8p7KlWyaTw/GgTCYOCpuefmne+CZ/uNZxxKl9XTOMEmmm9jrajOCqB29oB4h9VXUlIHFPlOiHPQJbVTtKI+3+teXjvlNWVeeH0F9ZO2vMfgCYXrX5vbaGr0CyrZmp4Jr5NzcAgK9q86PR2fTfZc/X3wJDDF1bPnYlAPiWbbpTGK6PcypxyIb2dLx87BEAKKvetEBP2pEXKiY0+8OsNbk2fV3ojptsM73f1Kzg+pk3tXR/71tGQVFOqq3l1Vj5uOd7L0aezaj2VtbdprvcjwLslGbq+bWzxj0PZvJE6ty6S/uG5s4bmu5oj8Tm0PLsMb6qzY/KlPXbeMWEjhkrtjpTpvUNzXCMlWZ6l52SoXjFhA7Pr3e5tEFdj6ydNf6nZZX1cy1pb14378ZNAFBWtfmjen7eZKuzI2Wl7J+su69kOwCeWr35A3A4Ps1m+pBN1s/iMyccOullDwSE95YHvqIbxi22mTokSQseq5f6bxqFAwtSrUdej5WX/AkApj638To2jIDmcrfJVMf6l8pL/pRpt3VGU47+A82dJ6zO9r1tBzt/XPPpUqu7oXFZdX3AFnJRdxkEAPZVb3rAWTx4YqrlSG20fNyvA8yiZmmNK8G5jxqFA65KtbUui5WPfSnzTOtKhO74FxAfltL8eXRmyZ5LXbguPReJiCMVFTZCJH0r95RoOSLmKB5ye+rokT12KnFXdPaotXdWvjnG4ciPaq6cD5jtrRaEMHpZZD0/137sCRof+AUV3TKZRs57hEpCv6KBd9xFMpUg0vQeV4OE0GQ6zWzbLuHKiUypqv30+rmjamRHcmqy6XCda8R7PkQu9+pQEOwPs1b2iR+t81Rt/zYAPtWwYcPgwRnrkGUJMeVD6K8dvSbRlokllZimZv5YWnaewzB+tmr77zt6lmAgugvS/qepi18bGPFnsms16G4I8bWy6k2ziMRw2zIHZ81xG/LbzLycde0p5A3tPGY+y3umrdx2t3AZD4Ct8T3VK3m8YFlITH9tTFpt2e8zw9fpQh6QmQBo26mnbcvMJZaL1r9+YyuQMdcZuB2E7ToZGwFQKHhMYDMTBlkbnOY3YKf/bKfTR9zcuWLGiq0OEEnh0r4g2T7Kth4ios9Nq95xTSj7chDK4NJdALDqnhvSZiq5UNpWPmv807i/JLMI93vcOoOmIsCCNe19mkbDe/VMd8iUVU3MbwsDc7PCL2GPBVDMNr+eIxwt2TZ23MMKBll3O35mm6bbsPT/9c4a05yN+zFwB2y5i6G9mXVXpEMfBUJK6Pgfhvho9iXvchUVsOTrSRgLCfAWjMwZASKAiCdXbX4vS75f2MIHAP4IqLSmRifgIZlO1WkaNjAzhQBOs2sECOXSMtfZjJ09bYzF9QCGS8k1bbKrsc97UQLzDiYkM81YsdXpXbbnV2Wr9m+WprXOkV80On30yFtWoqts3ZzRb0xeWnur05n7otAdo832toxb1Of0Dkb+mJtRfGsZnIOGI+/68Si+bSpcw64GW+aJ1wYJQdK2pDTTUnfnL/JU1z0Zr7hhO3e0TksdOfQXAJ3e5bsrG3P2riHNuNM5aPjXPdW7Hg4RST+femYvS5mGJiwhTVkzcaKZETXi9TNvagHLowAaEQrJuM9nTV1cP5AYH9Jycg9IPf9T2cYjCAVsWUEwT5HMcyWcTQAQ88YEExW0HehcGb139I41dw/v7BFNIhNMt0No72WhJ3o5JWlousUk7PqKCeleHmVS1x097lR87vuPEtBiC72ht5tFoC7JpAmLk90v50ludqRiQlpKHBHMzcvKJya6cgzqVv8RBLFhzd3DdxFxh01WETKzdAiSk7ols2Ylr6+4pREsj+bKAY3Zekg5U5l9n0MkiaUAH0sjYOIuYejlkqWHQeuOtQJk6p9Yrrp3dOpUz+nF6de3EriF4Gw4fiEt6oKABpuTPWY/i06wHC1tsYCZ38yUjymZTJoE5BHzJ5nRPihRty+7YJUB+581d149iB72RFkf7wfPLC21GfwEWLqlyY9OrKnRA0FQ06HkHsn0NZJ8iyHgz2Y3kyCTNGHCtnFdcmdKBXnPAk8MGog4aevf0xzOe+x02mXkDShOt7e8aXZ0TV1/35id/nBY04kO6wW591htzaM1p5ggJI091U+q7cjY5KG3x6bNrrGptqbM/zsSYwWLPr+vOcR42+RxBG2MRfKF0kUbjHjFhEN7N7/hA8TbzqKh5aQJH0sJs7WlFsBfwEyRXlP3T65hkYRluSSJcXetqi3OtPls0JA7NZk8Jk46T5PgF0DaD0G49vbw3hwAsBgMjY5qrekgQAVOsmwgs+IcE/5vwMi8P5Ut3bywbOmWkT07JjAOvXjvqBAnEr8ktnvKxxan2DKdBDnOU715UK8esF2So/ekQ2JGp8OZFNk3NRQEM8s0gQdZmj0BAAdOJayQtkTmpWxs7JSZDoT+h0Gfnb7m7f9l8M7ozNEbu7eQYRJoTzmsnhc7syiY6BCyTcu6nK/eeU0XMf31rrX7fwvGMC3terNn2QZG0uxo/xGBFgqiyb0aeAqm5WChjSmr2ji0V6D85HgkUafpSHW/E8EeTxskijUNN2atNSapM9GqNX/+xRcIYkRmpURi02UaDN60umzYV4m4ocF10w1xn88qq9o4lCEcpBlPE/Obom3LlBCRfG3lNgOgedAdxUwkUZOp48IR+UM04nIJdjMzZ+NUzEjJtGlohnFdqzFuxDvci6JPCwaAb9nOT0//zd9zAaBs9YG0p3rn80B2/+N/HL6qnZ+eFm1OeVfstXwr9x2647m6a08eXTqZ0g0bjLIXd4/3Ld3yvhMzhD3h2rzeDeTOyk352f/fHt6bk315PFHWp68+mAtksoyzmcxZa2Va9Y5rylZsHd/bXfOEa/M80ah+e3hvTjZrOXv8tBcOjPMsqb15fLi2Z6P66asP5p64lekJ5SMAmP7834fcHW+4ZfKSt65+pxE1f7jWkRXI3sd7luwaMH313gknfn/66oO5J74s3ZnZJ51/6pp9o3vK3n3MzOoN7tJFGwwwk2fJrgE954hG9btW7R87fdmWm3vXQ5+dXLg2r1cdEABMCv9t8N3xhlumVddec+ycx57HtDU7CntWSGSmOys35YOZZlbvd8+s3uDO1oX/uLrOtO9Mfbwx4K61B0pPfA/uWrLt6rIVO246cWTJt3LTmKkrtr6/V91e0gJzyRbOu3T3RzRXzu/srs4HYjXPRvwlQYpUkA1mCmR8fwQu4PXrS0CRCpKelbuu1YSrQprJBY7CQdeZHa1tZrK9bP3ccTUXZu/i7iB3Xwth9RHQu1g7PvYLvUfBzjU4edxxl9co1DktcPYuHX26oA/BE93l8i3f89WyVfun/8PMwO7ciWnVO67xrty3vGz1wd1lqw+smbx4y62Zcp7FimqBQN8bnZ98X3T8EG4ff+urLvqa83T873Ta8pzqvH19dsa5GKc6/ozq4tTPvc8lKU/IUzmT+j+v++W+n0fP70ynrYvs56eqj74+P9N7UZyd6/QP73x7uR8Xcj1fhUJxMYK+0ajeX+uunrfLks3KDFx+s1kVCsXlYUqpaL1CoVAoFAqFQqFQKBQKhUKhUCgUCoVCoVAoFAqFQqFQKBQKhUKhUCgUCoVCoVAoFAqFQqFQKBQKhUKhUCgUCoVCoVAoFAqFQqFQKBQKhUKhUCgUCoVCoVAoFAqFQqFQKBQKhUKhUCgUCoVCoVAoFAqFQqFQKBQKhUKhUCgUCoVCoVAoFAqFQqFQKBQKhULxbuT/AzLUoriBFMsPAAAAAElFTkSuQmCC';
// ITS and Soprim logos can be added via settings
const LOGO_HEXA = 'data:image/jpeg;base64,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';

const LOGO_AGENCE = 'data:image/jpeg;base64,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R7LNhdmMZdOplyYVTG5me8sUTpH0zHTMEchYC9oOQ045GVwHZ6qwsst+p7ne9RUVZK9/4akt7QaapODjxskfq4+y/oCsAoaUHIpoc/8Apj/6VmNt8TpzHetL6m118NVhfFZzDVWeodKyiggLDUUwD2CQR9y7Dur1dyR3Ut098TlquX8Estr0lfK25ylkFTTQRtAp8AAlnPzAe/TgdyOyvbAWNlPDHI+RkTGvf9Tg0Au+5800bcv7raOh178RkWnKiZ9M2ttTQyVoz0PbDK5px5jqAyPMZX4Ni7bfbJv2616k8b+JUVumpnGQ9WWMaxsZa79TekDB9MLrAwxukEhjYXgYDsDI/dPBj8TxfDb14x1Y5x906e+16u2nLuidWs+HPVuqrRq+03CSG4ziopK6mjDvHaC/pwSQCCH+vyuBBCvfbPXsm4mnzeXWC4WZhlcyNtXjEzR2ew8Et98DnOM91KpqeKoAEsTJADkB7QcH91kAwrEaSZ2IiKoIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAhAPflEQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREH/2Q==';


// ── GROUPE BCNC — DONNÉES INITIALES ──
const DEFAULT_GROUPE = {
  nom: 'Groupe BCNC',
  slogan: 'Entreprendre Ensemble.',
  site: 'www.groupebcnc.com',
  adresse: '36 Chemin des Fontaines, 38190 Bernin',
  logo: LOGO_BCNC
};

const DEFAULT_ENTREPRISES = [
  {
    id: 'E-ALPTECH',
    nom: 'Alptech',
    activite: 'Étanchéité · Toiture · Terrasse',
    couleur: '#2abbda',
    couleurSecondaire: '#12161c',
    logo: LOGO_ALPTECH,
    directeur: { nom: 'Lucien Iannone', initiales: 'LI', tel: '06.40.15.50.25', email: 'LI@alptech-etancheite.fr' },
    tel: '06.40.15.50.25',
    email: 'LI@alptech-etancheite.fr',
    site: 'www.alptech-etancheite.fr',
    adresse: '36 Chemin des Fontaines, 38190 Bernin',
    siret: '',
    active: true
  },
  {
    id: 'E-ITS',
    nom: 'I.T.S. Isère',
    activite: 'Intervention Toiture Services — Diagnostic, urgences, entretien, charpente, zinguerie',
    couleur: '#e63329',
    couleurSecondaire: '#1a1a1a',
    logo: null,
    directeur: { nom: 'Mourad Fentrouci', initiales: 'MF', tel: '06.35.15.13.55', email: 'grenoble@itstoiture.com' },
    tel: '06.35.15.13.55',
    email: 'grenoble@itstoiture.com',
    site: 'www.intervention-toiture-isere.fr',
    adresse: '36 Chemin des Fontaines, 38190 Bernin',
    siret: '9532164700021',
    active: true
  },
  {
    id: 'E-SOPRIM',
    nom: 'Soprim',
    activite: 'Rénovation de toitures-terrasses · Étanchéité depuis 1996',
    couleur: '#1a9fd4',
    couleurSecondaire: '#0a3a5a',
    logo: null,
    directeur: { nom: 'Éric Monaco', initiales: 'EM', tel: '06.83.34.24.51', email: 'em@soprim-etancheite.com' },
    tel: '06.83.34.24.51',
    email: 'em@soprim-etancheite.com',
    site: 'www.soprim-etancheite.com',
    adresse: '36 Chemin des Fontaines, 38190 Bernin',
    siret: '40846048300063',
    active: true
  }
];

const DEFAULT_TECHS = [
  {id:'T1', nom:'Irid Abdelkader', initiales:'IA', couleur:'#2abbda', spec:'Expert étanchéité', tel:'06 11 22 33 44', statut:'dispo', entrepriseId:'E-ALPTECH'},
  {id:'T2', nom:'Bouzid Hacen',    initiales:'BH', couleur:'#2abbda', spec:'Technicien étanchéité', tel:'06 55 66 77 88', statut:'dispo', entrepriseId:'E-ALPTECH'},
  {id:'T3', nom:'Romain Moreau',   initiales:'RM', couleur:'#2abbda', spec:'Spécialiste terrasse', tel:'06 99 00 11 22', statut:'occupe', entrepriseId:'E-ALPTECH'}
];

const DEFAULT_COMPANY = DEFAULT_ENTREPRISES[0];

let DB = {
  interventions: [],
  groupe: {...DEFAULT_GROUPE},
  entreprises: [...DEFAULT_ENTREPRISES],
  technicians: [...DEFAULT_TECHS],
  company: {...DEFAULT_COMPANY},
  mandants: [],
  notifications: []
};
let agPdfData = null, agUrg = null, agTech = null, agMandantId = null;
let agEntrepriseId = 'E-ALPTECH';  // entreprise destinatrice sélectionnée
let agTypeD = 'externe';            // 'externe' ou 'interne'
let agMandantInterneId = null;      // si interne : entité commanditaire
let techCurrentId = null, techZoneIdx = 0, techZonePhotos = {};
let consoItems = []; // liste des consommables saisis par le tech
let voiceRecognition = null;

// ── STORAGE ──
function saveDB() {
  try { DB._version = Date.now(); localStorage.setItem('hexa_db', JSON.stringify(DB)); } catch(e) {}
  if (spSyncActive) spPushDB();  // sync SharePoint en arrière-plan
}
function loadDB() {
  try {
    const d = localStorage.getItem('hexa_db') || localStorage.getItem('alptech_db');
    if (d) {
      const parsed = JSON.parse(d);
      DB = parsed;
      if (!DB.groupe) DB.groupe = {...DEFAULT_GROUPE};
      if (!DB.entreprises || !DB.entreprises.length) DB.entreprises = [...DEFAULT_ENTREPRISES];
      if (!DB.technicians || !DB.technicians.length) DB.technicians = [...DEFAULT_TECHS];
      if (!DB.company) DB.company = {...DEFAULT_COMPANY};
      if (!DB.notifications) DB.notifications = [];
      if (!DB.mandants) DB.mandants = [];
      // Restore embedded logos (not stored in localStorage to save space)
      DB.groupe.logo = LOGO_BCNC;
      DB.entreprises.forEach(e => {
        if (e.id === 'E-ALPTECH' && !e.logo) e.logo = LOGO_ALPTECH;
      });
    }
  } catch(e) {}
}

// ── VIEWS ──
function showView(v) {
  document.querySelectorAll('.view').forEach(el => el.classList.remove('active'));
  document.getElementById('view-' + v).classList.add('active');
  const rs = document.getElementById('role-switcher');
  rs.style.display = v === 'home' ? 'none' : 'flex';
  const bell = document.getElementById('notif-bell');
  if(bell) bell.style.display = (v==='dir' && (DB.notifications||[]).filter(n=>!n.read&&n.role==='dir').length>0) ? 'flex' : 'none';
  document.querySelectorAll('.role-pill').forEach(p => {
    p.className = 'role-pill';
    if (p.textContent.toLowerCase().includes(v === 'agence' ? 'agence' : v === 'tech' ? 'tech' : 'dir')) p.className = 'role-pill active-' + v;
  });
  if(v==='tech'){ setTbn('home'); const tbn=document.querySelector('.tech-bottom-nav'); if(tbn)tbn.style.display='flex'; }
  if (v === 'tech') refreshTechList();
  if (v === 'dir') refreshDirView();
  if (v === 'agence') refreshAgList();
  updateHeaderForView(v);
  window.scrollTo(0, 0);
}
// ── CONSOMMABLES TECHNICIEN ──

function renderConsoList() {
  const el = document.getElementById('conso-list');
  if (!el) return;
  if (!consoItems.length) {
    el.innerHTML = '<div style="font-size:11px;color:var(--muted);padding:6px 0;font-style:italic;">Aucun article. Ajoutez via le bouton ou la dictée vocale.</div>';
    return;
  }
  el.innerHTML = consoItems.map((c,i) => `
    <div class="conso-item">
      <input type="text" value="${c.designation}" placeholder="Désignation" oninput="consoItems[${i}].designation=this.value" style="flex:2;">
      <input type="number" class="conso-qty" value="${c.quantite}" min="0" step="0.1" oninput="consoItems[${i}].quantite=parseFloat(this.value)||0">
      <input type="text" value="${c.unite}" placeholder="unité" oninput="consoItems[${i}].unite=this.value" style="width:55px;border:1px solid var(--bd)!important;background:var(--white)!important;border-radius:7px;padding:4px 6px;font-size:11px;text-align:center;">
      <button class="conso-del" onclick="removeConso(${i})">✕</button>
    </div>`).join('');
}

function addConsoItem(designation, quantite, unite) {
  designation = designation || '';
  quantite = quantite || 1;
  unite = unite || 'u';
  consoItems.push({ designation, quantite, unite });
  renderConsoList();
  setTimeout(() => {
    const inputs = document.querySelectorAll('.conso-item input[type=text]');
    if (inputs.length) inputs[inputs.length - 2].focus();
  }, 50);
}

function removeConso(idx) {
  consoItems.splice(idx, 1);
  renderConsoList();
}

function toggleVoice() {
  const btn = document.getElementById('voice-btn');
  const status = document.getElementById('voice-status');
  if (!('webkitSpeechRecognition' in window) && !('SpeechRecognition' in window)) {
    alert('Dictée vocale non disponible. Utilisez Chrome sur mobile.');
    return;
  }
  if (voiceRecognition) {
    voiceRecognition.stop(); voiceRecognition = null;
    btn.classList.remove('recording');
    btn.innerHTML = '🎙 Dicter les matériaux utilisés';
    if(status) status.style.display = 'none';
    return;
  }
  const SR = window.SpeechRecognition || window.webkitSpeechRecognition;
  voiceRecognition = new SR();
  voiceRecognition.lang = 'fr-FR';
  voiceRecognition.continuous = true;
  voiceRecognition.interimResults = false;
  btn.classList.add('recording');
  btn.innerHTML = '⏹ Arrêter la dictée';
  if(status) status.style.display = 'block';
  voiceRecognition.onresult = e => {
    const t = e.results[e.results.length-1][0].transcript.trim();
    const m = t.match(/^([\d.,]+)\s+(\S+)\s+(.+)$/);
    if (m) { addConsoItem(m[3], parseFloat(m[1].replace(',','.')), m[2]); }
    else { addConsoItem(t, 1, 'u'); }
  };
  voiceRecognition.onerror = () => {
    btn.classList.remove('recording');
    btn.innerHTML = '🎙 Dicter les matériaux utilisés';
    if(status) status.style.display = 'none';
    voiceRecognition = null;
  };
  voiceRecognition.onend = () => { if (voiceRecognition) { try { voiceRecognition.start(); } catch(e){} } };
  voiceRecognition.start();
}

function updateDepl() {
  const type = document.getElementById('tech-dep-type');
  const valEl = document.getElementById('tech-dep-val');
  const unit = document.getElementById('tech-dep-unit');
  const mont = document.getElementById('tech-dep-montant');
  if (!type || !valEl || !unit || !mont) return;
  const val = parseFloat(valEl.value||0);
  if (type.value === 'km') { unit.textContent = 'km × 0,40 €'; mont.textContent = (val*0.40).toFixed(0)+' €'; }
  else if (type.value === 'inclus') { unit.textContent = ''; mont.textContent = '0 €'; }
  else { unit.textContent = '€'; mont.textContent = val.toFixed(0)+' €'; }
}

document.addEventListener('input', function(e) {
  if (e.target && e.target.id === 'tech-heures') {
    const h = parseFloat(e.target.value)||0;
    const el = document.getElementById('tech-heures-montant');
    if(el) el.textContent = (h*40).toFixed(0)+' €';
  }
});

// ── CHIFFRAGE DIRECTEUR ──

function buildChiffrageHTML(interv) {
  const D = (interv.rapport && interv.rapport.D) ? interv.rapport.D : {};
  const conso = D.consommables || [];
  const heures = D.heures || 0;
  const dep = D.deplacement || {};
  const montDep = dep.type === 'km' ? (dep.valeur||0)*0.40 : dep.type === 'inclus' ? 0 : (dep.valeur||0);
  const saved = interv.chiffrage || {};
  const fmtDate = saved.valideLe ? new Date(saved.valideLe).toLocaleDateString('fr-FR') : '';

  const consoRows = conso.length
    ? conso.map(c => `<div class="conso-list-dir-item"><span>${c.quantite} ${c.unite} — ${c.designation}</span></div>`).join('')
    : '<div style="font-size:11px;color:var(--muted);font-style:italic;">Aucun matériau renseigné</div>';

  const badgeHtml = (interv.chiffrage && interv.chiffrage.valide)
    ? '<span class="facturation-badge pret">✓ Prêt pour facturation</span>'
    : '<span class="facturation-badge attente">En attente</span>';

  const valideNote = (interv.chiffrage && interv.chiffrage.valide)
    ? `<div style="margin-top:10px;background:var(--gbg);border:1px solid var(--gbd);border-radius:10px;padding:10px 12px;font-size:12px;color:var(--grn);">✓ Validé le ${fmtDate} · Transmis à l'assistante</div>`
    : '';

  const hVal = saved.heures !== undefined ? saved.heures : heures;
  const depVal = saved.deplacement !== undefined ? saved.deplacement : montDep.toFixed(0);
  const marchVal = saved.marchandises || 0;
  const margeVal = saved.marge !== undefined ? saved.marge : 30;
  const notesVal = saved.notes || '';

  return `
  <div class="chiffrage-card">
    <div class="ch-title">💶 Chiffrage de l'intervention ${badgeHtml}</div>
    <div style="font-size:10px;color:var(--muted);text-transform:uppercase;letter-spacing:.8px;margin-bottom:6px;">Matériaux déclarés par ${D.tech||'le technicien'}</div>
    <div class="conso-list-dir">${consoRows}</div>
    <div class="ch-row">
      <span class="ch-label">Main d'oeuvre</span>
      <input type="number" class="ch-input" id="ch-heures" value="${hVal}" min="0" step="0.5" oninput="updateChiffrage()" style="max-width:70px;">
      <span class="ch-unit">h × 40 €/h =</span>
      <span style="font-family:'Space Grotesk',sans-serif;font-size:13px;font-weight:600;min-width:70px;text-align:right;" id="ch-heures-mont">${hVal*40} €</span>
    </div>
    <div class="ch-row">
      <span class="ch-label">Déplacement</span>
      <input type="number" class="ch-input" id="ch-dep" value="${depVal}" min="0" step="1" oninput="updateChiffrage()" style="max-width:90px;">
      <span class="ch-unit">€</span>
    </div>
    <div class="ch-row">
      <span class="ch-label">Marchandises HT</span>
      <input type="number" class="ch-input" id="ch-march" value="${marchVal}" min="0" step="1" oninput="updateChiffrage()" style="max-width:110px;">
      <span class="ch-unit">€ HT</span>
    </div>
    <div class="ch-row">
      <span class="ch-label">Marge (%)</span>
      <input type="number" class="ch-input" id="ch-marge" value="${margeVal}" min="0" max="100" step="1" oninput="updateChiffrage()" style="max-width:70px;">
      <span class="ch-unit">%</span>
    </div>
    <div style="height:1px;background:var(--bd);margin:12px 0;"></div>
    <div class="ch-total-row ht"><span class="ch-total-label">Total HT (avec marge)</span><span class="ch-total-val" id="ch-ht">— €</span></div>
    <div class="ch-total-row ht" style="margin-top:4px;"><span class="ch-total-label" style="color:var(--muted);">TVA 10%</span><span class="ch-total-val" style="font-size:14px;color:var(--muted);" id="ch-tva">— €</span></div>
    <div class="ch-total-row ttc" style="margin-top:8px;"><span class="ch-total-label">Total TTC</span><span class="ch-total-val" id="ch-ttc">— €</span></div>
    <div style="height:1px;background:var(--bd);margin:14px 0;"></div>
    <div class="field" style="margin-bottom:10px;">
      <label>Notes pour l'assistante</label>
      <textarea class="fta" id="ch-notes" style="height:60px;" placeholder="Références chantier, conditions de règlement...">${notesVal}</textarea>
    </div>
    <button class="btn btn-green btn-full" onclick="validerChiffrage('${interv.id}')">✓ Valider le chiffrage — transmettre pour facturation</button>
    ${valideNote}
  </div>`;
}

function updateChiffrage() {
  const h = parseFloat(document.getElementById('ch-heures')&&document.getElementById('ch-heures').value||0);
  const dep = parseFloat(document.getElementById('ch-dep')&&document.getElementById('ch-dep').value||0);
  const march = parseFloat(document.getElementById('ch-march')&&document.getElementById('ch-march').value||0);
  const marge = parseFloat(document.getElementById('ch-marge')&&document.getElementById('ch-marge').value||30)/100;
  const montH = h*40;
  const hEl = document.getElementById('ch-heures-mont');
  if(hEl) hEl.textContent = montH.toFixed(0)+' €';
  const baseHT = montH+dep+march;
  const avecMarge = baseHT*(1+marge);
  const tva = avecMarge*0.10;
  const ttc = avecMarge+tva;
  function fmt(v){ return v.toFixed(2).replace('.',',').replace(/\B(?=(\d{3})+(?!\d))/g,' ')+' €'; }
  const htEl = document.getElementById('ch-ht');
  const tvaEl = document.getElementById('ch-tva');
  const ttcEl = document.getElementById('ch-ttc');
  if(htEl) htEl.textContent = fmt(avecMarge);
  if(tvaEl) tvaEl.textContent = fmt(tva);
  if(ttcEl) ttcEl.textContent = fmt(ttc);
}

function validerChiffrage(id) {
  const i = DB.interventions.find(x=>x.id===id);
  if (!i) return;
  const h = parseFloat(document.getElementById('ch-heures')&&document.getElementById('ch-heures').value||0);
  const dep = parseFloat(document.getElementById('ch-dep')&&document.getElementById('ch-dep').value||0);
  const march = parseFloat(document.getElementById('ch-march')&&document.getElementById('ch-march').value||0);
  const marge = parseFloat(document.getElementById('ch-marge')&&document.getElementById('ch-marge').value||30);
  const notes = document.getElementById('ch-notes')&&document.getElementById('ch-notes').value||'';
  const avecMarge = (h*40+dep+march)*(1+marge/100);
  const tva = avecMarge*0.10;
  const ttc = avecMarge+tva;
  i.chiffrage = { heures:h, deplacement:dep, marchandises:march, marge, totalHT:avecMarge, tva, totalTTC:ttc, notes, valide:true, valideLe:new Date().toISOString() };
  saveDB();
  addNotification({ type:'chiffrage', title:'Chiffrage validé — '+i.client, desc:avecMarge.toFixed(0)+' € HT · '+ttc.toFixed(0)+' € TTC · Prêt pour facturation', intervId:id, role:'dir' });
  showToastMsg('✓ Chiffrage validé ! Transmis pour facturation.');
  setTimeout(()=>previewRapport(id),300);
}


function initHEXA() {
  const logo = document.getElementById('home-bcnc-logo');
  if (logo) logo.src = LOGO_HEXA;
  renderEntrepriseSelector();
  renderAgTechList();
}

// Render enterprise selector in agence form
function renderEntrepriseSelector() {
  const el = document.getElementById('ag-entreprise-selector');
  if (!el) return;
  const actives = (DB.entreprises || []).filter(e => e.active !== false);
  el.innerHTML = actives.map(e => {
    const isSelected = e.id === agEntrepriseId;
    const logoHtml = e.logo
      ? `<img src="${e.logo}" style="width:100%;height:100%;object-fit:contain;">`
      : `<div style="font-family:'Syne',sans-serif;font-size:11px;font-weight:700;color:${e.couleur};">${e.nom.substring(0,2).toUpperCase()}</div>`;
    return `<div class="mandant-opt ${isSelected?'sel':''}" onclick="selectEntreprise('${e.id}')">
      <div class="mandant-opt-logo">${logoHtml}</div>
      <div style="flex:1;">
        <div class="mandant-opt-name" style="color:${isSelected?e.couleur:'var(--dark)'};">${e.nom}</div>
        <div class="mandant-opt-type">${e.activite.split('·')[0].trim()}</div>
      </div>
      <span class="mandant-check" style="color:${e.couleur};">✓</span>
    </div>`;
  }).join('');
}

function selectEntreprise(id) {
  agEntrepriseId = id;
  renderEntrepriseSelector();
  renderAgTechList(); // filter techs by entreprise
  // Update header dot color
  const e = (DB.entreprises||[]).find(x=>x.id===id);
  if (e) {
    const dot = document.getElementById('hdr-entity-dot');
    const name = document.getElementById('hdr-entity-name');
    if (dot) dot.style.background = e.couleur;
    if (name) name.textContent = e.nom;
  }
  // Update interne selector (exclude current)
  if (agTypeD === 'interne') renderMandantInterneSelector(id);
}

// Type de demande
function setTypeD(type) {
  agTypeD = type;
  const ext = document.getElementById('td-externe');
  const int = document.getElementById('td-interne');
  const wrap = document.getElementById('ag-mandant-interne-wrap');
  if (type === 'externe') {
    ext.style.border='1.5px solid var(--cyan)'; ext.style.background='var(--cl)';
    ext.querySelector('div:nth-child(2)').style.color='var(--cyan)';
    int.style.border='1.5px solid var(--bd)'; int.style.background='var(--white)';
    int.querySelector('div:nth-child(2)').style.color='var(--muted)';
    if(wrap) wrap.style.display='none';
  } else {
    int.style.border='1.5px solid var(--pur)'; int.style.background='var(--pbg)';
    int.querySelector('div:nth-child(2)').style.color='var(--pur)';
    ext.style.border='1.5px solid var(--bd)'; ext.style.background='var(--white)';
    ext.querySelector('div:nth-child(2)').style.color='var(--muted)';
    if(wrap) wrap.style.display='block';
    renderMandantInterneSelector(agEntrepriseId);
  }
}

function renderMandantInterneSelector(excludeId) {
  const el = document.getElementById('ag-mandant-interne-selector');
  if (!el) return;
  // Toutes les entreprises actives — y compris l'exécutante (cas Alptech → Alptech)
  const all = (DB.entreprises||[]).filter(e => e.active !== false);
  if (!all.length) {
    el.innerHTML = '<div style="font-size:11px;color:var(--muted);">Aucune entité du groupe disponible.</div>';
    return;
  }
  el.innerHTML = all.map(e => {
    const isSelected = e.id === agMandantInterneId;
    const logoHtml = e.logo
      ? `<img src="${e.logo}" style="width:100%;height:100%;object-fit:contain;">`
      : `<div style="font-family:'Syne',sans-serif;font-size:11px;font-weight:700;color:${e.couleur};">${e.nom.substring(0,2).toUpperCase()}</div>`;
    return `<div class="mandant-opt ${isSelected?'sel':''}" onclick="selectMandantInterne('${e.id}')">
      <div class="mandant-opt-logo">${logoHtml}</div>
      <div style="flex:1;">
        <div class="mandant-opt-name" style="color:${isSelected?e.couleur:'var(--dark)'};">${e.nom}</div>
        <div class="mandant-opt-type">${e.activite.split('·')[0].trim()}</div>
      </div>
      <span class="mandant-check" style="color:${e.couleur};">✓</span>
    </div>`;
  }).join('');
}

function selectMandantInterne(id) {
  agMandantInterneId = id;
  renderMandantInterneSelector(agEntrepriseId);
}

// Update header when switching views
function updateHeaderForView(v) {
  const dot = document.getElementById('hdr-entity-dot');
  const name = document.getElementById('hdr-entity-name');
  if (v === 'home') {
    if(dot) dot.style.background='var(--cyan)';
    if(name) name.textContent='Groupe BCNC';
    return;
  }
  if (v === 'agence') {
    if(dot) dot.style.background='var(--pur)';
    if(name) name.textContent="L'Agence";
    return;
  }
  // For tech/dir, show entreprise color if set
  const e = (DB.entreprises||[]).find(x=>x.id===agEntrepriseId);
  if(e && dot) dot.style.background=e.couleur;
  if(name) name.textContent = v==='tech'?'Technicien':v==='dir'?'Dirigeant':'';
}

// ── AGENCE ──
function agMode(m) {
  ['pdf','email','phone'].forEach(x => {
    document.getElementById('amode-' + x).style.display = x === m ? 'block' : 'none';
    document.getElementById('atab-' + x).classList.toggle('active', x === m);
  });
}
function agDropPDF(e) { e.preventDefault(); const f = e.dataTransfer.files[0]; if(f) agProcessPDF(f); }
function agLoadPDF(e) { const f = e.target.files[0]; if(f) agProcessPDF(f); }
function agProcessPDF(file) {
  const r = new FileReader();
  r.onload = e => { agPdfData = e.target.result.split(',')[1]; document.getElementById('ag-pdf-drop').style.display='none'; const lo=document.getElementById('ag-pdf-loaded'); lo.classList.add('show'); document.getElementById('ag-pdf-name').textContent=file.name; document.getElementById('ag-pdf-size').textContent=(file.size/1024).toFixed(0)+' Ko'; document.getElementById('ag-btn-pdf').disabled=false; };
  r.readAsDataURL(file);
}
function agRemovePDF() { agPdfData=null; document.getElementById('ag-pdf-drop').style.display='block'; document.getElementById('ag-pdf-loaded').classList.remove('show'); document.getElementById('ag-btn-pdf').disabled=true; document.getElementById('ag-extract-result').style.display='none'; }

async function agExtract(mode) {
  const btnMap = {'pdf':'ag-btn-pdf','email':null,'phone':null};
  let messages;
  const prompt = `Extrait les informations et retourne UNIQUEMENT un JSON brut (sans backticks) :
{"client":"","contact":"","telephone":"","adresse":"","batiment":"","type_intervention":"","description":"","materiaux":"","reference_os":"","urgence":"normale"}
urgence="urgente" si urgent/sinistre/infiltration active. Laisse vide si absent.`;

  if (mode === 'pdf') {
    if (!agPdfData) return;
    const btn = document.getElementById('ag-btn-pdf');
    btn.disabled = true; btn.classList.add('loading');
    messages = [{ role:'user', content:[{type:'document',source:{type:'base64',media_type:'application/pdf',data:agPdfData}},{type:'text',text:prompt}] }];
    try { const R = await callAI(messages, 800); agFillForm(R); } catch(e){ alert('Erreur: '+e.message); }
    btn.disabled = false; btn.classList.remove('loading');
  } else if (mode === 'email') {
    const txt = document.getElementById('ag-email-txt').value.trim();
    if (!txt) { alert('Collez le contenu de l\'email.'); return; }
    const btn = document.querySelector('#amode-email .btn'); btn.disabled=true; btn.classList.add('loading');
    messages = [{ role:'user', content: prompt + '\n\nEMAIL:\n' + txt }];
    try { const R = await callAI(messages, 800); agFillForm(R); } catch(e){ alert('Erreur: '+e.message); }
    btn.disabled=false; btn.classList.remove('loading');
  } else {
    const txt = document.getElementById('ag-phone-txt').value.trim();
    if (!txt) { alert('Décrivez la demande.'); return; }
    const btn = document.querySelector('#amode-phone .btn'); btn.disabled=true; btn.classList.add('loading');
    messages = [{ role:'user', content: prompt + '\n\nNOTE APPEL:\n' + txt }];
    try { const R = await callAI(messages, 800); agFillForm(R); } catch(e){ alert('Erreur: '+e.message); }
    btn.disabled=false; btn.classList.remove('loading');
  }
}

function agFillForm(R) {
  const map = [['ag-client','client','ai-cl'],['ag-contact','contact','ai-co'],['ag-tel','telephone','ai-tel'],['ag-adresse','adresse','ai-ad'],['ag-bat','batiment','ai-bat'],['ag-desc','description','ai-de'],['ag-ref','reference_os','ai-ref']];
  const erFields = [];
  map.forEach(([fid,key,bid]) => { if(R[key]){ const el=document.getElementById(fid); if(el){el.value=R[key];el.classList.add('ai-f');} const b=document.getElementById(bid); if(b)b.style.display='inline-flex'; erFields.push(`<div style="background:var(--white);border-radius:8px;padding:7px 10px;border:1px solid var(--cb);"><div style="font-size:9px;color:var(--muted);text-transform:uppercase;">${key.replace('_',' ')}</div><div style="font-size:12px;font-weight:500;margin-top:1px;">${R[key]}</div></div>`); } });
  if(R.type_intervention){ const sel=document.getElementById('ag-type'); const opts=Array.from(sel.options); const m=opts.find(o=>o.text.toLowerCase().includes(R.type_intervention.toLowerCase().substring(0,6))); if(m){sel.value=m.value;sel.classList.add('ai-f');document.getElementById('ai-ty').style.display='inline-flex';} }
  if(R.materiaux){ const sel=document.getElementById('ag-mat'); const opts=Array.from(sel.options); const m=opts.find(o=>o.text.toLowerCase().includes(R.materiaux.toLowerCase().substring(0,4))); if(m){sel.value=m.value;sel.classList.add('ai-f');document.getElementById('ai-ma').style.display='inline-flex';} }
  if(R.urgence){ const uMap={'urgente':'u','normale':'n','preventive':'p'}; setUrg(uMap[R.urgence.toLowerCase()]||'n'); }
  const er = document.getElementById('ag-extract-result'); er.style.display='block'; document.getElementById('ag-extract-fields').innerHTML=erFields.join('');
  document.getElementById('ag-client').scrollIntoView({behavior:'smooth',block:'start'});
}

function setUrg(u) { agUrg=u; ['u','n','p'].forEach(x=>{const b=document.getElementById('urg-'+x);if(b)b.className='urg-btn'+(x===u?' sel-'+u:'');}); }
function selTech(el,name,initials,color) {
  document.querySelectorAll('.tech-item').forEach(t=>t.classList.remove('sel'));
  el.classList.add('sel');
  agTech={name, nom:name, initials, initiales:initials, color, couleur:color};
}

function openOutlook() {
  const client = document.getElementById('ag-client').value||'Intervention';
  const date = document.getElementById('ag-date').value;
  const heure = document.getElementById('ag-heure').value||'09:00';
  const type = document.getElementById('ag-type').value||'Intervention';
  if (!date) { alert('Choisissez une date.'); return; }
  const dt = new Date(date+'T'+heure+':00');
  const dtEnd = new Date(dt.getTime()+2*3600*1000);
  const fmt = d => d.toISOString().replace(/-|:|\.\d{3}/g,'').slice(0,15)+'Z';
  const url = `https://outlook.live.com/calendar/0/deeplink/compose?subject=${encodeURIComponent('Alptech — '+type+' · '+client)}&startdt=${fmt(dt)}&enddt=${fmt(dtEnd)}&body=${encodeURIComponent('Intervention Alptech\nClient : '+client+'\nAdresse : '+(document.getElementById('ag-adresse').value||''))}&allday=false`;
  window.open(url,'_blank');
}

function agSubmit() {
  const client = document.getElementById('ag-client').value.trim();
  if (!client) { document.getElementById('ag-err').innerHTML='<div class="err-box">Renseignez le nom du client.</div>'; return; }
  if (!agTech) { document.getElementById('ag-err').innerHTML='<div class="err-box">Sélectionnez un technicien.</div>'; return; }
  if (!document.getElementById('ag-date').value) { document.getElementById('ag-err').innerHTML='<div class="err-box">Choisissez une date.</div>'; return; }
  document.getElementById('ag-err').innerHTML='';

  const interv = {
    id: 'INT-' + Date.now(),
    client, contact: document.getElementById('ag-contact').value,
    tel: document.getElementById('ag-tel').value,
    adresse: document.getElementById('ag-adresse').value,
    batiment: document.getElementById('ag-bat').value,
    acces: document.getElementById('ag-acces').value,
    type: document.getElementById('ag-type').value||'Intervention',
    description: document.getElementById('ag-desc').value,
    materiaux: document.getElementById('ag-mat').value,
    ref: document.getElementById('ag-ref').value,
    urgence: agUrg==='u'?'urgente':agUrg==='p'?'preventive':'normale',
    notes: document.getElementById('ag-notes').value,
    tech: agTech,
    date: document.getElementById('ag-date').value,
    heure: document.getElementById('ag-heure').value||'09:00',
    duree: document.getElementById('ag-duree').value,
    mandantId: agMandantId || null,
    entrepriseId: agEntrepriseId,
    typeD: agTypeD,
    mandantInterneId: agTypeD === 'interne' ? agMandantInterneId : null,
    statut: 'planif',
    createdAt: new Date().toISOString(),
    rapport: null
  };
  DB.interventions.unshift(interv);
  saveDB();
  refreshAgList();
  addNotification({
    type:'planification',
    title:`Intervention planifiée — ${client}`,
    desc:`${interv.type} · ${interv.tech.name} · ${formatDate(interv.date)} ${interv.heure}`,
    intervId: interv.id,
    role:'dir'
  });
  agResetForm();
  // Show share modal for the technician
  showShareModal(interv);
}

// ── SHARE MODAL ──
function showShareModal(interv) {
  const baseUrl = window.location.href.split('#')[0];
  const deepLink = baseUrl + '#tech-' + interv.id;
  const smsBody = encodeURIComponent(`🔧 Alptech — Nouvelle intervention\n👤 ${interv.client}\n📍 ${interv.adresse||'—'}\n📅 ${formatDate(interv.date)} à ${interv.heure}\n🔗 Ouvrez ce lien pour accéder à votre fiche :\n${deepLink}`);
  const mailBody = encodeURIComponent(`Bonjour ${interv.tech?.name||''},\n\nUne intervention vous a été assignée :\n\n• Client : ${interv.client}\n• Adresse : ${interv.adresse||'—'}\n• Date : ${formatDate(interv.date)} à ${interv.heure}\n• Type : ${interv.type}\n\nAccédez à votre fiche directement ici :\n${deepLink}\n\nBonne intervention !\nAlptech`);
  const container = document.getElementById('share-modal-container');
  container.innerHTML = `
  <div class="modal-overlay" id="share-overlay" onclick="closeShareModal(event)">
    <div class="share-modal" onclick="event.stopPropagation()">
      <div style="width:40px;height:4px;background:var(--bd);border-radius:2px;margin:0 auto 18px;"></div>
      <div class="share-modal-title">✅ Intervention planifiée !</div>
      <div class="share-modal-sub">Partagez ce lien avec <strong>${interv.tech?.name||'le technicien'}</strong> pour qu'il accède à sa fiche depuis son téléphone.</div>
      <div class="share-modal-qr"><div id="qr-code"></div></div>
      <div style="text-align:center;font-size:10px;color:var(--muted);margin-bottom:14px;">Scannez le QR code ou choisissez une option</div>
      <div class="share-actions">
        <button class="share-action-btn" onclick="shareSMS('${smsBody}')">
          <span class="sab-icon">💬</span>
          <div><div class="sab-title">Envoyer par SMS</div><div class="sab-desc">Ouvre l'app SMS avec le lien pré-rempli</div></div>
          <span style="margin-left:auto;color:var(--muted);">→</span>
        </button>
        <button class="share-action-btn" onclick="shareWhatsApp('${encodeURIComponent('🔧 Alptech — ' + interv.client + ' · ' + formatDate(interv.date) + '\n' + deepLink)}')">
          <span class="sab-icon">📱</span>
          <div><div class="sab-title">Envoyer par WhatsApp</div><div class="sab-desc">Partage direct via WhatsApp</div></div>
          <span style="margin-left:auto;color:var(--muted);">→</span>
        </button>
        <button class="share-action-btn" onclick="shareEmail('Alptech — Intervention ${interv.client}','${mailBody}')">
          <span class="sab-icon">✉️</span>
          <div><div class="sab-title">Envoyer par email</div><div class="sab-desc">Ouvre votre client mail avec le message</div></div>
          <span style="margin-left:auto;color:var(--muted);">→</span>
        </button>
        <button class="share-action-btn" onclick="copyLink('${deepLink}')">
          <span class="sab-icon">🔗</span>
          <div><div class="sab-title">Copier le lien</div><div class="sab-desc" style="word-break:break-all;">${deepLink.length>55?deepLink.substring(0,55)+'…':deepLink}</div></div>
          <span style="margin-left:auto;color:var(--muted);">→</span>
        </button>
      </div>
      <button class="share-modal-close" onclick="closeShareModal()">Fermer</button>
    </div>
  </div>`;
  setTimeout(()=>{
    try{ new QRCode(document.getElementById('qr-code'),{text:deepLink,width:156,height:156,colorDark:'#12161c',colorLight:'#ffffff',correctLevel:QRCode.CorrectLevel.M}); }
    catch(e){ document.getElementById('qr-code').innerHTML='<div style="width:156px;height:156px;background:var(--bg);border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:11px;color:var(--muted);text-align:center;padding:10px;">QR disponible<br>en ligne</div>'; }
  },80);
}
function closeShareModal(e){ if(e&&e.target!==document.getElementById('share-overlay'))return; document.getElementById('share-modal-container').innerHTML=''; }
function shareSMS(b){window.open('sms:?body='+b);}
function shareWhatsApp(b){window.open('https://wa.me/?text='+b);}
function shareEmail(s,b){window.open('mailto:?subject='+encodeURIComponent(s)+'&body='+b);}
function copyLink(url){
  if(navigator.clipboard){navigator.clipboard.writeText(url).then(()=>showToastMsg('🔗 Lien copié !'));}
  else{const t=document.createElement('textarea');t.value=url;document.body.appendChild(t);t.select();document.execCommand('copy');t.remove();showToastMsg('🔗 Lien copié !');}
}
function showToastMsg(msg, type){
  const t=document.createElement('div');
  const bg = type==='err' ? 'var(--red)' : type==='warn' ? 'var(--ora)' : 'var(--grn)';
  t.style.cssText=`position:fixed;bottom:24px;left:50%;transform:translateX(-50%);background:${bg};color:#fff;padding:11px 22px;border-radius:12px;font-family:Syne,sans-serif;font-weight:700;font-size:13px;z-index:999;max-width:90vw;text-align:center;box-shadow:0 4px 16px rgba(0,0,0,.2);`;
  t.textContent=msg;
  document.body.appendChild(t);
  setTimeout(()=>t.remove(), type==='err'?4500:2800);
}

// ── NOTIFICATIONS ──
function addNotification(notif){
  if(!DB.notifications)DB.notifications=[];
  DB.notifications.unshift({...notif,id:'N-'+Date.now(),read:false,ts:new Date().toISOString()});
  if(DB.notifications.length>50)DB.notifications=DB.notifications.slice(0,50);
  saveDB(); refreshNotifBadge();
}
function refreshNotifBadge(){
  if(!DB.notifications)return;
  const unread=DB.notifications.filter(n=>!n.read&&n.role==='dir').length;
  const badge=document.getElementById('dir-notif-badge');
  const bell=document.getElementById('notif-bell');
  if(badge){badge.style.display=unread>0?'flex':'none';badge.textContent=unread>9?'9+':String(unread);}
  if(bell){bell.style.display=unread>0?'flex':'none';}
}
function openNotifPanel(){
  document.getElementById('notif-panel').classList.add('open');
  document.getElementById('notif-overlay').classList.add('open');
  renderNotifPanel();
  if(DB.notifications){DB.notifications.filter(n=>n.role==='dir').forEach(n=>n.read=true);saveDB();refreshNotifBadge();}
}
function closeNotifPanel(){
  document.getElementById('notif-panel').classList.remove('open');
  document.getElementById('notif-overlay').classList.remove('open');
}
function renderNotifPanel(){
  const body=document.getElementById('notif-panel-body');
  const notifs=(DB.notifications||[]).filter(n=>n.role==='dir');
  if(!notifs.length){body.innerHTML='<div style="text-align:center;padding:30px 0;font-size:13px;color:var(--muted);">Aucune notification</div>';return;}
  const icons={planification:'📅',validation:'⚡',envoi:'✅',chiffrage:'💶'};
  const labels={planification:'Planification',validation:'Validation requise',envoi:'Rapport envoyé',chiffrage:'Chiffrage validé'};
  body.innerHTML=notifs.map(n=>`
    <div class="notif-item ${n.read?'':'unread'}" onclick="notifClick('${n.intervId||''}')">
      <div class="ni-header">
        <span class="ni-type">${icons[n.type]||'🔔'} ${labels[n.type]||n.type}</span>
        <span class="ni-time">${timeAgo(n.ts)}</span>
      </div>
      <div class="ni-title">${n.title}</div>
      <div class="ni-desc">${n.desc}</div>
    </div>`).join('');
}
function notifClick(intervId){
  closeNotifPanel();
  if(!intervId)return;
  const i=DB.interventions.find(x=>x.id===intervId);
  if(!i)return;
  showView('dir');
  if(i.rapport)setTimeout(()=>previewRapport(intervId),200);
}
function timeAgo(ts){
  const d=(Date.now()-new Date(ts).getTime())/1000;
  if(d<60)return 'À l\'instant';
  if(d<3600)return Math.floor(d/60)+' min';
  if(d<86400)return Math.floor(d/3600)+'h';
  return Math.floor(d/86400)+'j';
}

// ── DEEP LINK ──
function handleDeepLink(){
  const hash=window.location.hash;
  if(!hash.startsWith('#tech-'))return;
  const intervId=hash.replace('#tech-','');
  if(!intervId)return;
  setTimeout(()=>{
    showView('tech');
    setTimeout(()=>{
      const i=DB.interventions.find(x=>x.id===intervId);
      if(i&&i.statut==='planif'){openTechForm(intervId);history.replaceState(null,'',window.location.pathname);}
      else if(i){showToastMsg('Cette intervention a déjà été soumise.');history.replaceState(null,'',window.location.pathname);}
      else{showToastMsg('Intervention introuvable.');}
    },350);
  },100);
}

// ── POLLING AUTO-REFRESH ──
function startPolling(){
  setInterval(()=>{
    if (spSyncActive) {
      // SharePoint gère la sync — pas besoin de localStorage polling
      return;
    }
    // Fallback localStorage (single device)
    try{
      const raw=localStorage.getItem('alptech_db');
      if(!raw)return;
      const fresh=JSON.parse(raw);
      if(fresh&&JSON.stringify(fresh.interventions?.length)!==JSON.stringify(DB.interventions?.length)){
        DB=fresh;
        const v=document.querySelector('.view.active');
        if(v){const id=v.id;if(id==='view-dir')refreshDirView();if(id==='view-tech')refreshTechList();if(id==='view-agence')refreshAgList();}
        refreshNotifBadge();
      }
    }catch(e){}
  },20000);
}

// ── MOBILE BOTTOM NAV ──
function setTbn(key){
  ['home','form','profile'].forEach(k=>{const b=document.getElementById('tbn-'+k);if(b)b.classList.toggle('active',k===key);});
}

function agResetForm() {
  ['ag-client','ag-contact','ag-tel','ag-adresse','ag-bat','ag-acces','ag-desc','ag-ref','ag-notes'].forEach(id=>{ const el=document.getElementById(id); if(el){el.value='';el.classList.remove('ai-f');} });
  ['ag-type','ag-mat'].forEach(id=>{ const el=document.getElementById(id); if(el){el.selectedIndex=0;el.classList.remove('ai-f');} });
  document.querySelectorAll('.ai-badge').forEach(b=>b.style.display='none');
  document.getElementById('ag-extract-result').style.display='none';
  document.querySelectorAll('.urg-btn').forEach(b=>b.className='urg-btn');
  document.querySelectorAll('.tech-item').forEach(t=>t.classList.remove('sel'));
  agUrg=null; agTech=null; agMandantId=null; agMandantInterneId=null; agTypeD='externe';
  setTypeD('externe');
  agRemovePDF();
  document.getElementById('ag-email-txt').value='';
  document.getElementById('ag-phone-txt').value='';
}

function refreshAgList() {
  renderAgTechList();
  const el = document.getElementById('ag-list');
  if (!DB.interventions.length) { el.innerHTML='<div style="text-align:center;padding:20px 0;font-size:13px;color:var(--muted);">Aucune intervention</div>'; return; }
  el.innerHTML = DB.interventions.slice(0,8).map(i => {
    const e = (DB.entreprises||[]).find(x=>x.id===i.entrepriseId);
    const techCouleur = i.tech?.color || i.tech?.couleur || e?.couleur || '#2abbda';
    const techIni = i.tech?.initials || i.tech?.initiales || '?';
    const techNom = i.tech?.name || i.tech?.nom || '—';
    const urgBar = i.urgence==='urgente'?'var(--red)':i.urgence==='preventive'?'var(--grn)':'var(--ora)';
    return `<div class="ii">
      <div class="ii-bar" style="background:${urgBar};"></div>
      <div class="ii-body">
        <div class="ii-client">${i.client}</div>
        <div class="ii-meta">${i.type} · ${i.adresse||'—'}</div>
        <div style="display:flex;align-items:center;gap:6px;margin-top:3px;flex-wrap:wrap;">
          <div style="width:16px;height:16px;border-radius:50%;background:${techCouleur};display:flex;align-items:center;justify-content:center;font-size:7px;font-weight:700;color:#fff;flex-shrink:0;">${techIni}</div>
          <span style="font-size:10px;color:var(--muted);">${techNom}</span>
          ${e ? `<span style="font-size:9px;font-weight:600;color:${e.couleur};background:${e.couleur}12;padding:1px 7px;border-radius:8px;">${e.nom}</span>` : ''}
          ${i.typeD==='interne' ? `<span style="font-size:9px;color:var(--pur);background:var(--pbg);padding:1px 7px;border-radius:8px;">🔄 Interne</span>` : ''}
        </div>
      </div>
      <div class="ii-right">
        <span class="status-pill ${i.statut}">${{planif:'Planifié',terrain:'Terrain',valider:'À valider',envoye:'Envoyé'}[i.statut]||i.statut}</span>
        <div class="ii-date">${formatDate(i.date)} ${i.heure}</div>
      </div>
    </div>`;
  }).join('');
}

// ── TECHNICIEN ──

function openTechForm(id) {
  techCurrentId = id;
  techZoneIdx = 0;
  techZonePhotos = {};
  consoItems = [];
  renderConsoList();
  const i = DB.interventions.find(x => x.id === id);
  if (!i) return;
  document.getElementById('tech-list-view').style.display = 'none';
  document.getElementById('tech-form-view').style.display = 'block';
  // Activate mobile bottom nav
  setTbn('form');
  const tbnForm = document.getElementById('tbn-form');
  if(tbnForm){ tbnForm.style.opacity='1'; tbnForm.style.pointerEvents='auto'; }
  document.getElementById('tech-zones-container').innerHTML = '';
  const e = (DB.entreprises||[]).find(x=>x.id===i.entrepriseId);
  const couleur = e?.couleur || 'var(--cyan)';
  const isUrgent = i.urgence === 'urgente';
  document.getElementById('tech-interv-header').innerHTML = `
    <div style="background:${isUrgent?'var(--rbg)':'var(--cl)'};border:1px solid ${isUrgent?'var(--rbd)':'var(--cb)'};border-radius:12px;padding:14px 16px;">
      <div style="display:flex;align-items:center;gap:8px;margin-bottom:6px;">
        <div style="font-size:10px;color:var(--muted);text-transform:uppercase;letter-spacing:.8px;">${isUrgent?'⚡ Urgence':'Intervention planifiée'}</div>
        ${e ? `<span style="font-size:9px;font-weight:700;color:${e.couleur};background:${e.couleur}15;padding:1px 8px;border-radius:8px;">${e.nom}</span>` : ''}
        ${i.typeD==='interne' ? `<span style="font-size:9px;color:var(--pur);">🔄 Interne</span>` : ''}
      </div>
      <div style="font-family:Syne,sans-serif;font-size:16px;font-weight:700;">${i.client}</div>
      <div style="font-size:12px;color:var(--muted);margin-top:3px;">${i.type} · ${i.adresse||''}</div>
      ${i.description?`<div style="font-size:12px;color:var(--mid);margin-top:8px;line-height:1.5;">${i.description}</div>`:''}
    </div>`;
  addZone();
  window.scrollTo(0, 0);
}

function showTechList() {
  document.getElementById('tech-list-view').style.display='block';
  document.getElementById('tech-form-view').style.display='none';
  document.getElementById('tech-generating').style.display='none';
  techCurrentId=null;
  setTbn('home');
  const tbnForm = document.getElementById('tbn-form');
  if(tbnForm){ tbnForm.style.opacity='.4'; tbnForm.style.pointerEvents='none'; }
}

function addZone(name='', sev='critique', comment='') {
  techZoneIdx++;
  const id = techZoneIdx;
  const el = document.createElement('div');
  el.className='zone-item'; el.id='z-'+id;
  el.innerHTML=`<div class="zh"><input class="zni" type="text" placeholder="Nom de la zone" value="${name}" id="zn-${id}"/><button class="del-z" onclick="document.getElementById('z-${id}').remove()">✕</button></div>
    <div class="sev-row"><button class="sev-btn ${sev==='critique'?'sc-critique':''}" onclick="zSev(this,${id},'critique')">Critique</button><button class="sev-btn ${sev==='majeur'?'sc-majeur':''}" onclick="zSev(this,${id},'majeur')">Majeur</button><button class="sev-btn ${sev==='mineur'?'sc-mineur':''}" onclick="zSev(this,${id},'mineur')">Mineur</button><button class="sev-btn ${sev==='stable'?'sc-stable':''}" onclick="zSev(this,${id},'stable')">Stable</button></div>
    <textarea class="zone-comment" placeholder="Observations sur cette zone…" id="zc-${id}">${comment}</textarea>
    <input type="hidden" id="zs-${id}" value="${sev}">
    <div style="margin-top:9px;border-top:1px solid var(--bd);padding-top:9px;">
      <div style="font-size:9px;color:var(--muted);text-transform:uppercase;letter-spacing:.6px;margin-bottom:7px;">Photos</div>
      <div class="photo-grid" id="pg-${id}"><div class="photo-add"><span style="font-size:18px;color:var(--cyan);">📷</span><span style="font-size:9px;color:var(--cyan);margin-top:2px;">Ajouter</span><input type="file" accept="image/*" capture="environment" multiple onchange="handlePhotos(event,${id})"></div></div>
    </div>`;
  document.getElementById('tech-zones-container').appendChild(el);
}

function zSev(btn,id,sev) { btn.closest('.sev-row').querySelectorAll('.sev-btn').forEach(b=>b.className='sev-btn'); btn.className='sev-btn sc-'+sev; document.getElementById('zs-'+id).value=sev; }

function getZones() {
  return Array.from(document.querySelectorAll('.zone-item')).map(z => {
    const id=z.id.replace('z-','');
    return { name:document.getElementById('zn-'+id).value.trim(), sev:document.getElementById('zs-'+id).value, comment:document.getElementById('zc-'+id).value.trim(), photos:techZonePhotos[id]||[] };
  }).filter(z=>z.name);
}

function resizeImage(file, maxPx=900, q=0.78) {
  return new Promise(res => {
    const img=new Image(), url=URL.createObjectURL(file);
    img.onload=()=>{ let w=img.width,h=img.height; if(w>maxPx||h>maxPx){if(w>h){h=Math.round(h*maxPx/w);w=maxPx;}else{w=Math.round(w*maxPx/h);h=maxPx;}} const c=document.createElement('canvas'); c.width=w; c.height=h; c.getContext('2d').drawImage(img,0,0,w,h); URL.revokeObjectURL(url); res(c.toDataURL('image/jpeg',q).split(',')[1]); };
    img.src=url;
  });
}

async function handlePhotos(e,zid) {
  const files=Array.from(e.target.files); if(!files.length)return;
  if(!techZonePhotos[zid])techZonePhotos[zid]=[];
  for(const f of files){ if(techZonePhotos[zid].length>=4)break; const b64=await resizeImage(f); techZonePhotos[zid].push({b64,preview:'data:image/jpeg;base64,'+b64}); }
  renderPhotoGrid(zid); e.target.value='';
}

function renderPhotoGrid(zid) {
  const grid=document.getElementById('pg-'+zid); const photos=techZonePhotos[zid]||[];
  grid.innerHTML='';
  photos.forEach((p,i)=>{ const d=document.createElement('div'); d.className='photo-thumb'; d.innerHTML=`<img src="${p.preview}"><button class="del-photo" onclick="techZonePhotos[${zid}].splice(${i},1);renderPhotoGrid(${zid})">✕</button>`; grid.appendChild(d); });
  if(photos.length<4){ const a=document.createElement('div'); a.className='photo-add'; a.innerHTML=`<span style="font-size:18px;color:var(--cyan);">📷</span><span style="font-size:9px;color:var(--cyan);margin-top:2px;">Ajouter</span><input type="file" accept="image/*" capture="environment" multiple onchange="handlePhotos(event,${zid})">`; grid.appendChild(a); }
}

async function techSubmit() {
  const zones = getZones();
  if (!zones.length) { document.getElementById('tech-err').innerHTML='<div class="err-box">Ajoutez au moins une zone.</div>'; return; }
  document.getElementById('tech-err').innerHTML='';
  const i = DB.interventions.find(x=>x.id===techCurrentId);
  if (!i) return;

  document.getElementById('tech-form-view').style.display='none';
  document.getElementById('tech-generating').style.display='block';
  window.scrollTo(0,0);

  const gsIds=['tgs1','tgs2','tgs3','tgs4'];
  let gi=0;
  const gsi=setInterval(()=>{ if(gi>0)document.getElementById(gsIds[gi-1]).className='gs done'; if(gi<gsIds.length){document.getElementById(gsIds[gi]).className='gs active';gi++;}else clearInterval(gsi); },2200);

  const D = {
    client:i.client, adresse:i.adresse, type:i.type, urgence:i.urgence,
    tech:i.tech?.name||'Technicien', duree:i.duree,
    mat:i.materiaux||'Non renseigné', age:'Inconnu',
    origine:'Demande client', origineDetail:i.description||'',
    solution:document.getElementById('tech-sol-type').value,
    solutionDetail:document.getElementById('tech-sol-desc').value,
    durabilite:document.getElementById('tech-dura').value,
    suivi:document.getElementById('tech-suivi').value,
    zones,
    heures: parseFloat(document.getElementById('tech-heures')?.value||2),
    deplacement: {
      type: document.getElementById('tech-dep-type')?.value||'forfait',
      valeur: parseFloat(document.getElementById('tech-dep-val')?.value||25)
    },
    consommables: [...consoItems]
  };

  const zonesText = D.zones.map(z=>`- Zone "${z.name}" | Sévérité: ${z.sev} | Observation: "${z.comment||'Aucune'}"`).join('\n');

  const prompt = `Tu es expert senior en étanchéité Alptech. Génère un rapport JSON brut (sans backticks) :
{
  "score":<1-10>,
  "etat_label":<"État critique"|"État dégradé"|"État moyen"|"Bon état"|"Excellent état">,
  "etat_desc":<phrase courte>,
  "synthese":<2-3 phrases professionnelles pour le client>,
  "zones":[{"nom":<str>,"severite":<str>,"diagnostic":<2 phrases>,"observations_visuelles":<str ou null>,"solution_appliquee":<str>,"durabilite_locale":<str>}],
  "recommandations":[{"titre":<str>,"description":<str>,"priorite":<"urgent"|"court_terme"|"preventif">,"delai":<str>}],
  "budget_previsionnel":{"total_estime":<str>,"echeancier":[{"periode":<str>,"action":<str>,"montant":<str>,"montant_pct":<1-100>,"priorite":<"now"|"soon"|"future"|"long">}]},
  "duree_vie":{"annees_restantes_label":<str>,"annees_ecoulees":<int>,"annees_totales":<int>,"description":<str>}
}

Client: ${D.client} | Adresse: ${D.adresse} | Type: ${D.type} | Urgence: ${D.urgence}
Technicien: ${D.tech} | Matériaux: ${D.mat}
Solution: ${D.solution} — ${D.solutionDetail}
Durabilité: ${D.durabilite} | Suivi: ${D.suivi}
ZONES:
${zonesText}`;

  const allPhotos = [];
  D.zones.forEach(z=>{(z.photos||[]).slice(0,2).forEach(p=>allPhotos.push({b64:p.b64,zone:z.name,sev:z.sev}));});
  const msgContent = [];
  allPhotos.slice(0,6).forEach(p=>{ msgContent.push({type:'image',source:{type:'base64',media_type:'image/jpeg',data:p.b64}}); msgContent.push({type:'text',text:`[Photo zone "${p.zone}" — ${p.sev}]`}); });
  const photoNote = allPhotos.length > 0 ? `\n\nANALYSE VISUELLE : ${allPhotos.length} photo(s). Enrichis observations_visuelles.` : '';
  msgContent.push({type:'text',text:prompt+photoNote});

  try {
    clearInterval(gsi); gsIds.forEach(id=>document.getElementById(id).className='gs done');
    const R = await callAI([{role:'user',content:msgContent}], 2500);
    // Save rapport to intervention
    i.statut = 'valider';
    i.rapport = { data: R, D, createdAt: new Date().toISOString(), zones: D.zones };
    saveDB();
    addNotification({
      type:'validation',
      title:`Rapport à valider — ${i.client}`,
      desc:`${i.type} · Rapport généré par ${i.tech?.name||'technicien'} · En attente de votre validation`,
      intervId: i.id,
      role:'dir'
    });
    refreshNotifBadge();
    document.getElementById('tech-generating').style.display='none';
    showTechList();
    const toast=document.createElement('div');
    toast.style.cssText='position:fixed;bottom:24px;left:50%;transform:translateX(-50%);background:var(--grn);color:#fff;padding:12px 24px;border-radius:12px;font-family:Syne,sans-serif;font-weight:700;font-size:14px;z-index:999;';
    toast.textContent='✓ Rapport généré ! En attente de validation par le dirigeant.';
    document.body.appendChild(toast);
    setTimeout(()=>toast.remove(),4000);
  } catch(e) {
    clearInterval(gsi);
    document.getElementById('tech-generating').style.display='none';
    document.getElementById('tech-form-view').style.display='block';
    document.getElementById('tech-err').innerHTML='<div class="err-box">Erreur : '+e.message+'</div>';
    gsIds.forEach(id=>document.getElementById(id).className='gs');
  }
}

// ── DIRIGEANT ──
function refreshDirView() {
  const total = DB.interventions.length;
  const valider = DB.interventions.filter(i=>i.statut==='valider').length;
  const cours = DB.interventions.filter(i=>['planif','terrain'].includes(i.statut)).length;
  const envoyes = DB.interventions.filter(i=>i.statut==='envoye').length;
  document.getElementById('dir-stat-total').textContent = total;
  document.getElementById('dir-stat-valider').textContent = valider;
  document.getElementById('dir-stat-cours').textContent = cours;
  document.getElementById('dir-stat-envoyes').textContent = envoyes;

  const buildCard = i => {
    const e = (DB.entreprises||[]).find(x=>x.id===i.entrepriseId);
    const urgBar = i.urgence==='urgente'?'var(--red)':i.urgence==='preventive'?'var(--grn)':'var(--ora)';
    const techNom = i.tech?.nom || i.tech?.name || '—';
    const emetteurId = i.typeD==='interne' ? i.mandantInterneId : i.entrepriseId;
    const emetteur = (DB.entreprises||[]).find(x=>x.id===emetteurId);
    return `<div class="ii" ${i.rapport?`onclick="previewRapport('${i.id}')"`:''} style="${i.rapport?'cursor:pointer;':''}">
      <div class="ii-bar" style="background:${urgBar};"></div>
      <div class="ii-body">
        <div class="ii-client">${i.client}</div>
        <div class="ii-meta">${i.type} · ${i.adresse||'—'}</div>
        <div style="display:flex;align-items:center;gap:6px;margin-top:4px;flex-wrap:wrap;">
          <span style="font-size:10px;color:var(--muted);">${techNom}</span>
          ${e ? `<span style="font-size:9px;font-weight:600;color:${e.couleur};background:${e.couleur}15;padding:1px 7px;border-radius:8px;">${e.nom}</span>` : ''}
          ${i.typeD==='interne' && emetteur ? `<span style="font-size:9px;color:var(--pur);background:var(--pbg);padding:1px 7px;border-radius:8px;">→ ${emetteur.nom}</span>` : ''}
        </div>
      </div>
      <div class="ii-right">
        <span class="status-pill ${i.statut}">${{planif:'Planifié',terrain:'Terrain',valider:'À valider',envoye:'Envoyé'}[i.statut]||i.statut}</span>
        <div class="ii-date">${formatDate(i.date)}</div>
      </div>
    </div>`;
  };

  // Rapports à valider
  const toVal = DB.interventions.filter(i=>i.statut==='valider');
  const vSection = document.getElementById('dir-valider-section');
  vSection.style.display = toVal.length ? 'block' : 'none';
  document.getElementById('dir-valider-list').innerHTML = toVal.map(i => {
    const e = (DB.entreprises||[]).find(x=>x.id===i.entrepriseId);
    return `<div class="vb-item">
      <div style="flex:1;">
        <div class="vb-client">${i.client}</div>
        <div class="vb-meta">${i.type} · ${i.tech?.nom||i.tech?.name||'—'} · ${formatDate(i.date)}</div>
        ${e ? `<div style="font-size:9px;font-weight:600;color:${e.couleur};margin-top:3px;">${e.nom}</div>` : ''}
      </div>
      <div class="vb-actions">
        <button class="vb-btn preview" onclick="previewRapport('${i.id}')">👁 Voir</button>
        <button class="vb-btn validate" onclick="validateAndSend('${i.id}')">✓ Valider</button>
      </div>
    </div>`;
  }).join('');

  // All list
  const allEl = document.getElementById('dir-all-list');
  if (!total) { allEl.innerHTML='<div style="text-align:center;padding:20px 0;font-size:13px;color:var(--muted);">Aucune intervention</div>'; return; }

  // Group by company
  const grouped = {};
  DB.interventions.forEach(i => {
    const eid = i.entrepriseId || 'autre';
    if (!grouped[eid]) grouped[eid] = [];
    grouped[eid].push(i);
  });

  allEl.innerHTML = Object.entries(grouped).map(([eid, items]) => {
    const e = (DB.entreprises||[]).find(x=>x.id===eid);
    const grpHdr = e ? `<div style="font-size:9px;font-weight:600;color:${e.couleur};letter-spacing:1px;text-transform:uppercase;padding:8px 0 5px;border-bottom:1px solid ${e.couleur}22;margin-bottom:6px;">${e.nom} — ${items.length} intervention${items.length>1?'s':''}</div>` : '';
    return grpHdr + items.map(i => buildCard(i)).join('');
  }).join('');
}

let previewingId = null;
function previewRapport(id) {
  previewingId = id;
  const i = DB.interventions.find(x=>x.id===id);
  if (!i || !i.rapport) return;
  document.getElementById('dir-rapport-preview').style.display='block';
  document.getElementById('dir-all-list').closest('.card').style.display='none';
  document.getElementById('dir-valider-section').style.display='none';
  document.getElementById('dir-rapport-content').innerHTML = buildRapportHTML(i) + buildChiffrageHTML(i);
  window.scrollTo(0,0);
  setTimeout(()=>{ animateReport(); updateChiffrage(); },250);
}

function hideDirRapport() {
  document.getElementById('dir-rapport-preview').style.display='none';
  document.getElementById('dir-all-list').closest('.card').style.display='block';
  refreshDirView();
}

function sendRapport() {
  const i = DB.interventions.find(x=>x.id===previewingId);
  if (!i) return;
  i.statut = 'envoye';
  saveDB();
  hideDirRapport();
  const toast=document.createElement('div');
  toast.style.cssText='position:fixed;bottom:24px;left:50%;transform:translateX(-50%);background:var(--grn);color:#fff;padding:12px 24px;border-radius:12px;font-family:Syne,sans-serif;font-weight:700;font-size:14px;z-index:999;';
  toast.textContent='✉️ Rapport envoyé au client !';
  document.body.appendChild(toast);
  setTimeout(()=>toast.remove(),3500);
}

function validateAndSend(id) {
  previewingId = id;
  const i = DB.interventions.find(x=>x.id===id);
  if (!i || !i.rapport) return;
  if (confirm(`Valider et envoyer le rapport à ${i.client} ?`)) {
    i.statut='envoye';
    saveDB();
    addNotification({
      type:'envoi',
      title:`Rapport envoyé — ${i.client}`,
      desc:`${i.type} · Rapport transmis au client`,
      intervId: i.id,
      role:'dir'
    });
    refreshDirView();
    const t=document.createElement('div');
    t.style.cssText='position:fixed;bottom:24px;left:50%;transform:translateX(-50%);background:var(--grn);color:#fff;padding:12px 24px;border-radius:12px;font-family:Syne,sans-serif;font-weight:700;font-size:14px;z-index:999;';
    t.textContent='✉️ Rapport envoyé au client !';
    document.body.appendChild(t);
    setTimeout(()=>t.remove(),3500);
  }
}

// ── BUILD RAPPORT HTML ──
function buildRapportHTML(interv) {
  const R = interv.rapport.data;
  const D = interv.rapport.D;
  const today = new Date().toLocaleDateString('fr-FR',{day:'numeric',month:'long',year:'numeric'});
  const scoreColor = R.score<=3?'var(--red)':R.score<=5?'var(--ora)':R.score<=7?'var(--cyan)':'var(--grn)';
  const circ = 220;
  const offset = (circ*(1-R.score/10)).toFixed(0);

  // ── WHITE-LABEL : détermine l'émetteur du rapport ──
  const entreprise = (DB.entreprises||[]).find(e=>e.id===interv.entrepriseId) || DB.entreprises?.[0];
  const isInterne = interv.typeD === 'interne' && interv.mandantInterneId;
  const emetteur = isInterne
    ? (DB.entreprises||[]).find(e=>e.id===interv.mandantInterneId) || entreprise
    : entreprise;
  const executant = entreprise;
  const couleurEmetteur = emetteur?.couleur || '#2abbda';
  const logoEmetteur = emetteur?.logo || null;
  const nomEmetteur = emetteur?.nom || 'Alptech';
  const activiteEmetteur = emetteur?.activite || 'Étanchéité · Toiture · Terrasse';
  const emailEmetteur = emetteur?.email || 'contact@alptech-etancheite.fr';
  const telEmetteur = emetteur?.tel || '—';
  const dirEmetteur = emetteur?.directeur?.nom || '—';
  const refNum = 'INT-' + new Date().getFullYear() + '-' + interv.id.slice(-4);

  const logoHtml = logoEmetteur
    ? `<img src="${logoEmetteur}" style="height:32px;object-fit:contain;max-width:140px;">`
    : `<div style="font-family:Syne,sans-serif;font-size:16px;font-weight:800;">${nomEmetteur}</div>`;

  const heroBg = `background:linear-gradient(135deg,${couleurEmetteur} 0%,${couleurEmetteur}cc 100%)`;

  const pmap = {urgent:'p1',court_terme:'p2',preventif:'p3'};
  const recsHTML = (R.recommandations||[]).map(rec=>{
    const cls=pmap[rec.priorite]||'p2';
    return `<div class="r-rec"><div class="rr-num ${cls}">${{urgent:'!',court_terme:'~',preventif:'✓'}[rec.priorite]||'~'}</div><div><div class="rr-t">${rec.titre}</div><div class="rr-d">${rec.description}</div><span class="rr-del ${cls}">${rec.delai}</span></div></div>`;
  }).join('');

  const zonesHTML = (R.zones||[]).map((z,zi)=>{
    const zData=(interv.rapport.zones||[])[zi]||{};
    const photos=zData.photos||[];
    let photosHTML='';
    if(photos.length>=2){photosHTML=`<div style="display:grid;grid-template-columns:1fr 1fr;gap:2px;border-radius:10px;overflow:hidden;border:1px solid var(--bd);margin-bottom:10px;position:relative;"><div style="position:absolute;top:0;bottom:0;left:calc(50% - 1px);width:2px;background:#fff;z-index:2;"></div><div style="position:relative;"><div style="aspect-ratio:4/3;overflow:hidden;"><img src="${photos[0].preview}" style="width:100%;height:100%;object-fit:cover;"></div><div style="position:absolute;bottom:0;left:0;right:0;padding:5px;font-size:9px;font-weight:600;text-align:center;background:rgba(196,125,10,.85);color:#fff;text-transform:uppercase;letter-spacing:.6px;">Avant</div></div><div style="position:relative;"><div style="aspect-ratio:4/3;overflow:hidden;"><img src="${photos[1].preview}" style="width:100%;height:100%;object-fit:cover;"></div><div style="position:absolute;bottom:0;left:0;right:0;padding:5px;font-size:9px;font-weight:600;text-align:center;background:rgba(42,157,111,.85);color:#fff;text-transform:uppercase;letter-spacing:.6px;">Après</div></div></div>`;}
    else if(photos.length===1){photosHTML=`<div style="border-radius:10px;overflow:hidden;aspect-ratio:4/3;max-width:220px;margin-bottom:10px;"><img src="${photos[0].preview}" style="width:100%;height:100%;object-fit:cover;"></div>`;}
    const vis=z.observations_visuelles?`<div style="background:var(--pbg);border:1px solid var(--pbd);border-radius:10px;padding:8px 11px;margin-bottom:8px;font-size:12px;color:#4a3ea8;line-height:1.6;display:flex;gap:7px;"><span>👁</span>${z.observations_visuelles}</div>`:'';
    const sol=z.solution_appliquee?`<div class="sol-box"><div class="sl">Solution appliquée</div><div class="sv">${z.solution_appliquee}</div></div>`:'';
    const dur=z.durabilite_locale?`<div style="display:inline-flex;align-items:center;gap:5px;font-size:11px;font-weight:500;padding:4px 11px;border-radius:20px;background:var(--pbg);color:var(--pur);border:1px solid var(--pbd);">⏱ ${z.durabilite_locale}</div>`:'';
    return `<div class="r-zone"><div class="rz-hdr"><div style="display:flex;align-items:center;"><div class="rz-strip ${z.severite||'mineur'}"></div><div class="rz-name">${z.nom}</div></div><span class="sev-pill ${z.severite||'mineur'}">${z.severite}</span></div><div class="rz-body">${photosHTML}<p>${z.diagnostic||''}</p>${vis}${sol}${dur}</div></div>`;
  }).join('');

  const bp=R.budget_previsionnel||{};
  const maxPct=Math.max(...(bp.echeancier||[]).map(e=>e.montant_pct||0),1);
  const tlHTML=(bp.echeancier||[]).map(e=>{
    const w=Math.round((e.montant_pct||0)/maxPct*100);
    return `<div class="tl-row"><div class="tl-dot ${e.priorite||'future'}">${{now:'!',soon:'~',future:'◦',long:'✓'}[e.priorite]||'◦'}</div><div class="tl-info"><div class="tl-period">${e.periode}</div><div class="tl-action">${e.action}</div></div><div class="tl-bar"><div class="bar-track"><div class="bar-fill ${e.priorite||'future'}" style="width:0%" data-w="${w}"></div></div></div><div class="tl-amt">${e.montant}</div></div>`;
  }).join('');

  const dv=R.duree_vie||{};
  const soustraitanceNote = isInterne && executant && emetteur && executant.id !== emetteur.id
    ? `<div style="background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.12);border-radius:9px;padding:8px 12px;margin-top:12px;font-size:10px;color:rgba(255,255,255,.55);">Expertise réalisée par <strong style="color:rgba(255,255,255,.8);">${executant.nom}</strong> pour <strong style="color:rgba(255,255,255,.8);">${emetteur.nom}</strong> — Groupe BCNC</div>`
    : `<div style="margin-top:10px;font-size:9px;color:rgba(255,255,255,.3);">Groupe BCNC · Entreprendre Ensemble.</div>`;

  return `
  <div class="r-hero" style="${heroBg}">
    <div style="display:inline-flex;align-items:center;font-size:10px;font-weight:500;padding:4px 12px;border-radius:20px;margin-bottom:12px;background:rgba(255,255,255,.15);color:rgba(255,255,255,.9);border:1px solid rgba(255,255,255,.25);">${D.type}</div>
    <div class="r-h1">${D.type} — <em>${D.client}</em></div>
    <div class="r-sub">${D.adresse||''}</div>
    <div class="r-meta">
      <div class="rmc"><div class="rl">Client</div><div class="rv">${D.client}</div></div>
      <div class="rmc"><div class="rl">Date</div><div class="rv">${today}</div></div>
      <div class="rmc"><div class="rl">Technicien</div><div class="rv">${D.tech}</div></div>
      <div class="rmc"><div class="rl">Durée</div><div class="rv">${D.duree||'—'}</div></div>
    </div>
    ${soustraitanceNote}
  </div>

  <div class="score-row">
    <div class="ring-w">
      <svg width="80" height="80" viewBox="0 0 80 80"><circle cx="40" cy="40" r="34" fill="none" stroke="#e3e8ec" stroke-width="6"/><circle id="r-ring" cx="40" cy="40" r="34" fill="none" stroke="${scoreColor}" stroke-width="6" stroke-linecap="round" stroke-dasharray="${circ}" stroke-dashoffset="${circ}"/></svg>
      <div class="ring-c"><div class="r-num" style="color:${scoreColor}">${R.score}</div><div class="r-den">/10</div></div>
    </div>
    <div>
      <div style="font-family:Syne,sans-serif;font-size:16px;font-weight:700;color:${scoreColor};margin-bottom:4px;">${R.etat_label||'Diagnostic'}</div>
      <div style="font-size:12px;color:var(--muted);line-height:1.5;">${R.etat_desc||''}</div>
    </div>
  </div>

  <div class="r-sec">Synthèse</div>
  <div class="synth">${R.synthese||''}</div>

  <div class="r-sec">Diagnostic par zone</div>
  ${zonesHTML}

  <div class="r-sec" style="margin-top:4px;">Recommandations</div>
  ${recsHTML}

  <div class="r-sec">Budget prévisionnel 10 ans</div>
  <div class="budget-card">
    <div style="display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:14px;">
      <div><div style="font-family:Syne,sans-serif;font-size:15px;font-weight:700;">Plan financier patrimonial</div><div style="font-size:11px;color:var(--muted);margin-top:2px;">${D.client} · ${D.mat}</div></div>
      <div style="background:var(--pbg);border:1px solid var(--pbd);border-radius:10px;padding:9px 14px;text-align:center;"><div style="font-size:9px;color:var(--pur);text-transform:uppercase;letter-spacing:.8px;">Total estimé</div><div style="font-family:'Space Grotesk',sans-serif;font-size:18px;font-weight:700;color:var(--pur);">${bp.total_estime||'—'}</div></div>
    </div>${tlHTML}
  </div>

  <div class="r-sec">Durée de vie estimée</div>
  <div class="duree-card">
    <div class="dv-top"><div><div class="dv-t">${D.mat}</div><div class="dv-m">${D.client}</div></div><div><div class="dv-y">${dv.annees_restantes_label||'—'}</div><div class="dv-l">années restantes</div></div></div>
    <div class="dv-track"><div class="dv-fill" id="r-dv-fill" style="width:0%"></div></div>
    <div class="dv-desc">${dv.description||''}</div>
  </div>

  <div class="r-cta">
    <div><div style="font-size:9px;color:var(--hint);text-transform:uppercase;letter-spacing:1px;margin-bottom:7px;">Prochaine étape</div><div class="r-cta-t">Demander un devis</div><div class="r-cta-s">${D.client} · ${D.type}</div></div>
    <button class="cta-btn" style="background:${couleurEmetteur};">Demander un devis →</button>
  </div>

  <div class="r-footer">
    <div>${logoHtml}<div style="font-size:10px;color:var(--muted);margin-top:4px;line-height:1.7;">${activiteEmetteur.split('·')[0]}<br>${emailEmetteur}</div></div>
    <div class="rf-info">Rapport #${refNum} · ${today}<br>Dir. ${dirEmetteur}<br><span style="color:var(--hint);">Groupe BCNC · Document certifié</span></div>
    <div class="rf-contact"><div class="rf-tel">📞 ${telEmetteur}</div><div>${emailEmetteur}</div><div>Urgences 7j/7</div></div>
  </div>`;
}

function animateReport() {
  const ring=document.getElementById('r-ring');
  if(ring){ring.style.transition='stroke-dashoffset 1.3s ease'; const i=DB.interventions.find(x=>x.id===previewingId); if(i&&i.rapport){ring.style.strokeDashoffset=(220*(1-i.rapport.data.score/10)).toFixed(0);}}
  document.querySelectorAll('.bar-fill[data-w]').forEach(b=>{b.style.transition='width 1.2s ease';b.style.width=b.getAttribute('data-w')+'%';});
  const df=document.getElementById('r-dv-fill');
  if(df){const i=DB.interventions.find(x=>x.id===previewingId); if(i&&i.rapport&&i.rapport.data.duree_vie){const dv=i.rapport.data.duree_vie;const pct=dv.annees_totales?Math.min(100,Math.round(dv.annees_ecoulees/dv.annees_totales*100)):55;df.style.transition='width 1.4s ease';df.style.width=pct+'%';}}
}

// ── MANDANTS MANAGEMENT ──
let mandantLogoData = null;
let editingMandantId = null;

function renderMandantMgmt() {
  const list = document.getElementById('mandant-mgmt-list');
  if (!list) return;
  if (!DB.mandants || !DB.mandants.length) {
    list.innerHTML = '<div style="text-align:center;padding:20px;font-size:13px;color:var(--muted);">Aucun mandant externe. Cliquez sur + Ajouter.</div>';
    return;
  }
  list.innerHTML = DB.mandants.map(m => {
    const logoHtml = m.logo
      ? `<img src="${m.logo}" style="width:100%;height:100%;object-fit:contain;">`
      : `<div style="font-family:'Syne',sans-serif;font-size:12px;font-weight:700;color:${m.couleur||'var(--cyan)'};">${(m.nom||'').substring(0,2).toUpperCase()}</div>`;
    return `<div class="mandant-card">
      <div class="mandant-logo-box">${logoHtml}</div>
      <div style="flex:1;">
        <div class="mandant-name">${m.nom}</div>
        <div class="mandant-meta">${m.type||'—'} · ${m.email||'—'}</div>
        <div class="mandant-meta">${m.tel||''}</div>
      </div>
      <div class="tmc-actions">
        <button class="tmc-btn" onclick="editMandant('${m.id}')">✏️</button>
        <button class="tmc-btn del" onclick="deleteMandant('${m.id}')">🗑</button>
      </div>
    </div>`;
  }).join('');
}

function openAddMandantForm(prefillId) {
  editingMandantId = prefillId || null;
  mandantLogoData = null;
  const form = document.getElementById('add-mandant-form');
  const title = document.getElementById('add-mandant-form-title');
  const drop = document.getElementById('mandant-logo-drop');
  const preview = document.getElementById('mandant-logo-preview-wrap');
  if(drop) drop.style.display='block';
  if(preview) preview.style.display='none';
  form.classList.add('open');
  if (prefillId) {
    const m = (DB.mandants||[]).find(x=>x.id===prefillId);
    if (!m) return;
    title.textContent = 'Modifier — ' + m.nom;
    document.getElementById('mandant-form-name').value = m.nom||'';
    document.getElementById('mandant-form-type').value = m.type||'';
    document.getElementById('mandant-form-email').value = m.email||'';
    document.getElementById('mandant-form-tel').value = m.tel||'';
    document.getElementById('mandant-form-addr').value = m.adresse||'';
    document.getElementById('mandant-form-color').value = m.couleur||'#1e3a5f';
    if (m.logo) {
      mandantLogoData = m.logo;
      document.getElementById('mandant-logo-preview-img').src = m.logo;
      document.getElementById('mandant-logo-preview-name').textContent = m.nom;
      if(preview) preview.style.display='flex';
      if(drop) drop.style.display='none';
    }
  } else {
    title.textContent = 'Nouveau mandant';
    ['mandant-form-name','mandant-form-type','mandant-form-email','mandant-form-tel','mandant-form-addr'].forEach(id=>{
      const el=document.getElementById(id); if(el) el.value='';
    });
    document.getElementById('mandant-form-color').value='#1e3a5f';
  }
}

function closeAddMandantForm() {
  const form = document.getElementById('add-mandant-form');
  if(form) form.classList.remove('open');
  editingMandantId=null; mandantLogoData=null;
}

function loadMandantLogo(event) {
  const file = event.target.files[0]; if(!file) return;
  const r = new FileReader();
  r.onload = e => {
    mandantLogoData = e.target.result;
    document.getElementById('mandant-logo-preview-img').src = mandantLogoData;
    document.getElementById('mandant-logo-preview-name').textContent = file.name;
    document.getElementById('mandant-logo-preview-wrap').style.display='flex';
    document.getElementById('mandant-logo-drop').style.display='none';
  };
  r.readAsDataURL(file);
}

function removeMandantLogo() {
  mandantLogoData=null;
  document.getElementById('mandant-logo-preview-wrap').style.display='none';
  document.getElementById('mandant-logo-drop').style.display='block';
}

function saveMandant() {
  const nom = document.getElementById('mandant-form-name').value.trim();
  if (!nom) { alert('Le nom est obligatoire.'); return; }
  const data = {
    nom,
    type: document.getElementById('mandant-form-type').value.trim(),
    email: document.getElementById('mandant-form-email').value.trim(),
    tel: document.getElementById('mandant-form-tel').value.trim(),
    adresse: document.getElementById('mandant-form-addr').value.trim(),
    couleur: document.getElementById('mandant-form-color').value,
    logo: mandantLogoData || null
  };
  if (!DB.mandants) DB.mandants = [];
  if (editingMandantId) {
    const idx = DB.mandants.findIndex(x=>x.id===editingMandantId);
    if (idx>=0) DB.mandants[idx] = { ...DB.mandants[idx], ...data };
  } else {
    DB.mandants.push({ id:'M-'+Date.now(), ...data });
  }
  saveDB();
  closeAddMandantForm();
  renderMandantMgmt();
}

function editMandant(id) { openAddMandantForm(id); }

function deleteMandant(id) {
  const m = (DB.mandants||[]).find(x=>x.id===id);
  if (!m || !confirm(`Supprimer ${m.nom} ?`)) return;
  DB.mandants = DB.mandants.filter(x=>x.id!==id);
  saveDB();
  renderMandantMgmt();
}

function switchStab(tab) {
  const tabs = ['api','entreprises','techs','mandants','company'];
  document.querySelectorAll('.stab').forEach((b,i) => b.classList.toggle('active', tabs[i]===tab));
  document.querySelectorAll('.stab-pane').forEach(p => p.classList.remove('active'));
  document.getElementById('stab-'+tab).classList.add('active');
  if (tab === 'entreprises') renderEntrepriseMgmt();
  if (tab === 'techs') renderTechMgmt();
  if (tab === 'mandants') renderMandantMgmt();
  if (tab === 'company') loadCompanyForm();
}

// ── ENTREPRISE MANAGEMENT ──
let entLogoData = null;
let editingEntId = null;

function renderEntrepriseMgmt() {
  const list = document.getElementById('entreprise-mgmt-list');
  if (!list) return;
  list.innerHTML = (DB.entreprises||[]).map(e => {
    const logoHtml = e.logo
      ? `<img src="${e.logo}" style="width:100%;height:100%;object-fit:contain;">`
      : `<div style="font-family:'Syne',sans-serif;font-size:12px;font-weight:700;color:${e.couleur};">${(e.nom||'').substring(0,2).toUpperCase()}</div>`;
    const techCount = DB.technicians.filter(t=>t.entrepriseId===e.id).length;
    return `<div class="mandant-card">
      <div class="mandant-logo-box" style="border-color:${e.couleur}20;">${logoHtml}</div>
      <div style="flex:1;">
        <div class="mandant-name" style="color:${e.couleur};">${e.nom}</div>
        <div class="mandant-meta">${e.activite?.split('·')[0].trim()||'—'}</div>
        <div class="mandant-meta">Dir. ${e.directeur?.nom||'—'} · ${techCount} technicien${techCount>1?'s':''}</div>
        <span class="mandant-badge" style="background:${e.couleur}15;color:${e.couleur};border-color:${e.couleur}30;">${e.active!==false?'Active':'Archivée'}</span>
      </div>
      <div class="tmc-actions">
        <button class="tmc-btn" onclick="editEntreprise('${e.id}')" title="Modifier">✏️</button>
        <button class="tmc-btn del" onclick="toggleEntreprise('${e.id}')" title="${e.active!==false?'Archiver':'Réactiver'}">${e.active!==false?'📦':'♻️'}</button>
      </div>
    </div>`;
  }).join('');
}

function openAddEntrepriseForm(prefillId) {
  editingEntId = prefillId || null;
  entLogoData = null;
  const form = document.getElementById('add-entreprise-form');
  const title = document.getElementById('add-entreprise-form-title');
  form.classList.add('open');
  document.getElementById('ent-logo-preview-wrap').style.display='none';
  document.getElementById('ent-logo-drop').style.display='block';
  if (prefillId) {
    const e = (DB.entreprises||[]).find(x=>x.id===prefillId);
    if (!e) return;
    title.textContent = 'Modifier — ' + e.nom;
    document.getElementById('ent-form-nom').value = e.nom||'';
    document.getElementById('ent-form-activite').value = e.activite||'';
    document.getElementById('ent-form-couleur').value = e.couleur||'#2abbda';
    document.getElementById('ent-form-dir-nom').value = e.directeur?.nom||'';
    document.getElementById('ent-form-dir-ini').value = e.directeur?.initiales||'';
    document.getElementById('ent-form-dir-email').value = e.directeur?.email||'';
    document.getElementById('ent-form-dir-tel').value = e.directeur?.tel||'';
    document.getElementById('ent-form-email').value = e.email||'';
    document.getElementById('ent-form-tel').value = e.tel||'';
    document.getElementById('ent-form-adresse').value = e.adresse||'';
    document.getElementById('ent-form-site').value = e.site||'';
    document.getElementById('ent-form-siret').value = e.siret||'';
    if (e.logo) {
      entLogoData = e.logo;
      document.getElementById('ent-logo-preview-img').src = e.logo;
      document.getElementById('ent-logo-preview-name').textContent = e.nom;
      document.getElementById('ent-logo-preview-wrap').style.display='flex';
      document.getElementById('ent-logo-drop').style.display='none';
    }
  } else {
    title.textContent = 'Nouvelle entreprise';
    ['ent-form-nom','ent-form-activite','ent-form-dir-nom','ent-form-dir-ini','ent-form-dir-email','ent-form-dir-tel','ent-form-email','ent-form-tel','ent-form-adresse','ent-form-site','ent-form-siret'].forEach(id=>{
      const el=document.getElementById(id); if(el) el.value='';
    });
    document.getElementById('ent-form-couleur').value='#2abbda';
  }
}

function closeAddEntrepriseForm() {
  document.getElementById('add-entreprise-form').classList.remove('open');
  editingEntId=null; entLogoData=null;
}

function loadEntLogo(event) {
  const file = event.target.files[0]; if(!file) return;
  const r = new FileReader();
  r.onload = e => {
    entLogoData = e.target.result;
    document.getElementById('ent-logo-preview-img').src = entLogoData;
    document.getElementById('ent-logo-preview-name').textContent = file.name;
    document.getElementById('ent-logo-preview-wrap').style.display='flex';
    document.getElementById('ent-logo-drop').style.display='none';
  };
  r.readAsDataURL(file);
}

function removeEntLogo() {
  entLogoData=null;
  document.getElementById('ent-logo-preview-wrap').style.display='none';
  document.getElementById('ent-logo-drop').style.display='block';
}

function saveEntreprise() {
  const nom = document.getElementById('ent-form-nom').value.trim();
  if (!nom) { alert('Le nom est obligatoire.'); return; }
  const data = {
    nom,
    activite: document.getElementById('ent-form-activite').value.trim(),
    couleur: document.getElementById('ent-form-couleur').value,
    couleurSecondaire: '#1a1a1a',
    logo: entLogoData || null,
    directeur: {
      nom: document.getElementById('ent-form-dir-nom').value.trim(),
      initiales: document.getElementById('ent-form-dir-ini').value.trim().toUpperCase(),
      email: document.getElementById('ent-form-dir-email').value.trim(),
      tel: document.getElementById('ent-form-dir-tel').value.trim()
    },
    email: document.getElementById('ent-form-email').value.trim(),
    tel: document.getElementById('ent-form-tel').value.trim(),
    adresse: document.getElementById('ent-form-adresse').value.trim(),
    site: document.getElementById('ent-form-site').value.trim(),
    siret: document.getElementById('ent-form-siret').value.trim(),
    active: true
  };
  if (editingEntId) {
    const idx = DB.entreprises.findIndex(x=>x.id===editingEntId);
    if (idx>=0) DB.entreprises[idx] = { ...DB.entreprises[idx], ...data };
  } else {
    DB.entreprises.push({ id:'E-'+Date.now(), ...data });
  }
  saveDB();
  closeAddEntrepriseForm();
  renderEntrepriseMgmt();
  renderEntrepriseSelector();
}

function editEntreprise(id) { openAddEntrepriseForm(id); }

function toggleEntreprise(id) {
  const e = DB.entreprises.find(x=>x.id===id);
  if (!e) return;
  e.active = !e.active;
  saveDB();
  renderEntrepriseMgmt();
  renderEntrepriseSelector();
}


// ── TECH COLORS ──
const TECH_COLORS = ['#2abbda','#6c5ce7','#c47d0a','#2a9d6f','#e04444','#e879a0','#0ea5e9','#8b5cf6','#f59e0b','#10b981','#ef4444','#6366f1','#ec4899','#14b8a6','#f97316','#84cc16'];
let selectedColor = TECH_COLORS[0];
let editingTechId = null;

function buildColorGrid() {
  const grid = document.getElementById('color-grid');
  if (!grid) return;
  grid.innerHTML = TECH_COLORS.map(c => `
    <div class="color-swatch ${c===selectedColor?'selected':''}" style="background:${c};" onclick="pickColor('${c}',this)"></div>
  `).join('');
}

function pickColor(c, el) {
  selectedColor = c;
  document.querySelectorAll('.color-swatch').forEach(s => s.classList.remove('selected'));
  el.classList.add('selected');
}

function initials(name) {
  return name.trim().split(/\s+/).map(w=>w[0].toUpperCase()).join('').substring(0,2);
}

// ── RENDER TECH LIST IN SETTINGS ──
function renderTechMgmt() {
  const list = document.getElementById('tech-mgmt-list');
  if (!DB.technicians.length) {
    list.innerHTML = '<div style="text-align:center;padding:20px;font-size:13px;color:var(--muted);">Aucun technicien. Cliquez sur + Ajouter.</div>';
    return;
  }
  const statusLabel = {dispo:'Disponible', occupe:'En intervention', inactif:'Inactif'};
  // Group by entreprise
  const grouped = {};
  DB.technicians.forEach(t => {
    const eid = t.entrepriseId || 'autre';
    if (!grouped[eid]) grouped[eid] = [];
    grouped[eid].push(t);
  });
  list.innerHTML = Object.entries(grouped).map(([eid, techs]) => {
    const e = (DB.entreprises||[]).find(x=>x.id===eid);
    const grpHeader = e ? `<div style="font-size:9px;font-weight:600;color:${e.couleur};letter-spacing:1px;text-transform:uppercase;margin:8px 0 6px;">${e.nom}</div>` : '';
    return grpHeader + techs.map(t => `
      <div class="tech-mgmt-card">
        <div class="tmc-av" style="background:${t.couleur || e?.couleur || 'var(--cyan)'}">${t.initiales}</div>
        <div class="tmc-info">
          <div class="tmc-name">${t.nom}</div>
          <div class="tmc-meta">${t.spec||'—'} ${t.tel ? '· ' + t.tel : ''}</div>
          <span class="tmc-status ${t.statut||'dispo'}">${statusLabel[t.statut||'dispo']}</span>
        </div>
        <div class="tmc-actions">
          <button class="tmc-btn" onclick="editTech('${t.id}')" title="Modifier">✏️</button>
          <button class="tmc-btn del" onclick="deleteTech('${t.id}')" title="Supprimer">🗑</button>
        </div>
      </div>`).join('');
  }).join('');
}

// ── RENDER TECH LIST IN AGENCE (filtré par entreprise) ──
function renderAgTechList() {
  const el = document.getElementById('ag-tech-list');
  if (!el) return;
  const filtered = DB.technicians.filter(t =>
    (t.entrepriseId === agEntrepriseId || t.entrepriseId === (DB.technicians[0]?.entrepriseId)) &&
    t.statut !== 'inactif'
  ).filter(t => t.entrepriseId === agEntrepriseId);

  if (!filtered.length) {
    const all = DB.technicians.filter(t => t.statut !== 'inactif');
    if (!all.length) {
      el.innerHTML = '<div style="font-size:12px;color:var(--muted);padding:10px 0;">Aucun technicien. Ajoutez-en dans ⚙️ Paramètres.</div>';
      return;
    }
    // fallback: show all active techs
    renderTechItems(el, all);
    return;
  }
  renderTechItems(el, filtered);
}

function renderTechItems(el, techs) {
  const e = (DB.entreprises||[]).find(x=>x.id===agEntrepriseId);
  const couleur = e?.couleur || 'var(--cyan)';
  const statusLabel = {dispo:'● Disponible', occupe:'● En intervention', inactif:'○ Inactif'};
  const statusColor = {dispo:'var(--grn)', occupe:'var(--ora)', inactif:'var(--hint)'};
  el.innerHTML = techs.map(t => `
    <div class="tech-item" onclick="selTech(this,'${t.nom}','${t.initiales}','${t.couleur || couleur}')">
      <div class="tech-av" style="background:${t.couleur || couleur}">${t.initiales}</div>
      <div>
        <div style="font-size:13px;font-weight:500;">${t.nom}</div>
        <div style="font-size:10px;color:${statusColor[t.statut]||'var(--muted)'};margin-top:2px;">${statusLabel[t.statut]||t.statut}</div>
        ${t.spec ? `<div style="font-size:10px;color:var(--muted);">${t.spec}</div>` : ''}
      </div>
      <span class="tech-check">✓</span>
    </div>`).join('');
}


// ── REFRESH TECH LIST FOR TECHNICIAN VIEW ──
function refreshTechList() {
  const el = document.getElementById('tech-interv-list');
  const techNoms = DB.technicians.map(t => t.nom || t.name);
  const mine = DB.interventions.filter(i => techNoms.includes(i.tech?.name) && i.statut === 'planif');
  if (!mine.length) { el.innerHTML='<div style="text-align:center;padding:20px 0;font-size:13px;color:var(--muted);">Aucune intervention assignée</div>'; return; }
  el.innerHTML = mine.map(i => {
    const e = (DB.entreprises||[]).find(x=>x.id===i.entrepriseId);
    const couleur = e?.couleur || 'var(--cyan)';
    return `<div class="ii" onclick="openTechForm('${i.id}')">
      <div class="ii-bar" style="background:${couleur};width:4px;border-radius:2px;align-self:stretch;flex-shrink:0;"></div>
      <div class="ii-body">
        <div class="ii-client">${i.client}</div>
        <div class="ii-meta">${i.type} · ${i.adresse||'—'}</div>
        ${e ? `<div style="font-size:9px;font-weight:600;color:${e.couleur};margin-top:3px;letter-spacing:.4px;">${e.nom.toUpperCase()}</div>` : ''}
        ${i.description?'<div style="font-size:11px;color:var(--muted);margin-top:2px;">'+i.description.substring(0,60)+(i.description.length>60?'…':'')+'</div>':''}
      </div>
      <div class="ii-right">
        <span class="status-pill planif">À faire</span>
        <div class="ii-date">${formatDate(i.date)} ${i.heure}</div>
        ${i.urgence==='urgente'?'<div style="font-size:10px;color:var(--red);font-weight:500;margin-top:3px;">⚡ Urgent</div>':''}
      </div>
    </div>`;
  }).join('');
}

// ── OPEN / CLOSE ADD FORM ──
function openAddTechForm(prefillId) {
  editingTechId = prefillId || null;
  selectedColor = TECH_COLORS[0];
  const form = document.getElementById('add-tech-form');
  const title = document.getElementById('add-tech-form-title');
  // Populate entreprise select
  const sel = document.getElementById('tech-form-entreprise');
  if (sel) {
    sel.innerHTML = (DB.entreprises||[]).filter(e=>e.active!==false).map(e =>
      `<option value="${e.id}">${e.nom}</option>`
    ).join('');
    sel.value = agEntrepriseId || DB.entreprises[0]?.id || 'E-ALPTECH';
  }
  form.classList.add('open');
  if (prefillId) {
    const t = DB.technicians.find(x=>x.id===prefillId);
    if (!t) return;
    title.textContent = 'Modifier le technicien';
    document.getElementById('tech-form-name').value = t.nom || t.name || '';
    document.getElementById('tech-form-spec').value = t.spec||'';
    document.getElementById('tech-form-tel').value = t.tel||'';
    document.getElementById('tech-form-status').value = t.statut || t.status || 'dispo';
    if (sel) sel.value = t.entrepriseId || DB.entreprises[0]?.id;
    selectedColor = t.couleur || t.color || TECH_COLORS[0];
  } else {
    title.textContent = 'Nouveau technicien';
    ['tech-form-name','tech-form-spec','tech-form-tel'].forEach(id => {
      const el = document.getElementById(id); if(el) el.value='';
    });
    document.getElementById('tech-form-status').value = 'dispo';
  }
  buildColorGrid();
}

function closeAddTechForm() {
  document.getElementById('add-tech-form').classList.remove('open');
  editingTechId = null;
}

// ── SAVE TECH ──
function saveTech() {
  const name = document.getElementById('tech-form-name').value.trim();
  if (!name) { alert('Le nom est obligatoire.'); return; }
  const spec = document.getElementById('tech-form-spec').value.trim();
  const tel = document.getElementById('tech-form-tel').value.trim();
  const statut = document.getElementById('tech-form-status').value;
  const entrepriseId = document.getElementById('tech-form-entreprise')?.value || 'E-ALPTECH';
  const e = (DB.entreprises||[]).find(x=>x.id===entrepriseId);
  const couleurDefault = e?.couleur || selectedColor;
  const ini = initials(name);

  if (editingTechId) {
    const t = DB.technicians.find(x=>x.id===editingTechId);
    if (t) {
      t.nom=name; t.name=name; // keep both for compat
      t.initiales=ini; t.initials=ini;
      t.couleur=selectedColor; t.color=selectedColor;
      t.spec=spec; t.tel=tel; t.statut=statut; t.status=statut;
      t.entrepriseId=entrepriseId;
    }
  } else {
    DB.technicians.push({
      id:'T-'+Date.now(),
      nom:name, name,
      initiales:ini, initials:ini,
      couleur:selectedColor, color:selectedColor,
      spec, tel,
      statut, status:statut,
      entrepriseId
    });
  }
  saveDB();
  closeAddTechForm();
  renderTechMgmt();
  renderAgTechList();
}

// ── EDIT / DELETE TECH ──
function editTech(id) { openAddTechForm(id); }

function deleteTech(id) {
  const t = DB.technicians.find(x=>x.id===id);
  if (!t) return;
  if (!confirm(`Supprimer ${t.nom||t.name} ? Cette action est irréversible.`)) return;
  DB.technicians = DB.technicians.filter(x=>x.id!==id);
  saveDB();
  renderTechMgmt();
  renderAgTechList();
}

// ── GROUPE SETTINGS ──
function loadCompanyForm() {
  const g = DB.groupe || {};
  document.getElementById('co-name').value = g.nom||'Groupe BCNC';
  document.getElementById('co-tagline').value = g.slogan||'Entreprendre Ensemble.';
  document.getElementById('co-web').value = g.site||'www.groupebcnc.com';
  const addrEl = document.getElementById('co-adresse');
  if (addrEl) addrEl.value = g.adresse||'36 Chemin des Fontaines, 38190 Bernin';
  const preview = document.getElementById('co-logo-preview');
  if (preview) preview.src = g.logo || LOGO_BCNC;
  const nomPreview = document.getElementById('co-nom-preview');
  if (nomPreview) nomPreview.textContent = g.nom||'Groupe BCNC';
}

function saveCompany() {
  if (!DB.groupe) DB.groupe = {};
  DB.groupe.nom = document.getElementById('co-name').value.trim() || 'Groupe BCNC';
  DB.groupe.slogan = document.getElementById('co-tagline').value.trim();
  DB.groupe.site = document.getElementById('co-web').value.trim();
  const addrEl = document.getElementById('co-adresse');
  if (addrEl) DB.groupe.adresse = addrEl.value.trim();
  saveDB();
  const s = document.getElementById('co-status');
  s.style.display='block'; setTimeout(()=>s.style.display='none',2500);
  // Update header
  document.getElementById('hdr-entity-name').textContent = DB.groupe.nom;
  document.getElementById('home-bcnc-logo').src = DB.groupe.logo || LOGO_BCNC;
}

// ── API KEY MANAGEMENT ──
const FALLBACK_KEY = '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';
function getApiKey(){ return localStorage.getItem('alptech_api_key') || FALLBACK_KEY; }

function toggleSettings(){
  const p=document.getElementById('settings-panel');
  const visible=p.style.display==='block';
  p.style.display=visible?'none':'block';
  if(!visible){
    // Reset to API tab
    switchStab('api');
    const k=localStorage.getItem('alptech_api_key')||'';
    document.getElementById('api-key-input').value=k;
    const saved=localStorage.getItem('alptech_api_key_status');
    if(saved==='ok') setStatusDot('ok');
    else if(saved==='err') setStatusDot('err');
    else setStatusDot('idle');
  }
}

function toggleKeyVisibility(){
  const i=document.getElementById('api-key-input');
  i.type=i.type==='password'?'text':'password';
}

function saveApiKey(){
  const val=document.getElementById('api-key-input').value.trim();
  if(!val){ alert('Veuillez entrer une clé API.'); return; }
  localStorage.setItem('alptech_api_key', val);
  localStorage.removeItem('alptech_api_key_status');
  setStatusDot('idle');
  showStatusBar('Clé enregistrée. Cliquez sur "Tester" pour vérifier qu\'elle fonctionne.','info');
}

function setStatusDot(state){
  const d=document.getElementById('api-status-dot');
  if(!d)return;
  if(state==='ok'){d.style.background='#2a9d6f';d.title='Clé API active';}
  else if(state==='err'){d.style.background='#e04444';d.title='Clé API invalide';}
  else{d.style.background='#cbd5da';d.title='Clé non testée';}
}

function showStatusBar(msg, type){
  const b=document.getElementById('api-status-bar');
  if(!b)return;
  b.style.display='flex';
  const cfg={ok:{bg:'var(--gbg)',bd:'var(--gbd)',col:'#1a6b42',icon:'✅'},err:{bg:'var(--rbg)',bd:'var(--rbd)',col:'var(--red)',icon:'❌'},info:{bg:'var(--cl)',bd:'var(--cb)',col:'#1a6d7e',icon:'ℹ️'}};
  const c=cfg[type]||cfg.info;
  b.style.cssText=`display:flex;align-items:center;gap:8px;border-radius:10px;padding:10px 14px;font-size:12px;background:${c.bg};border:1px solid ${c.bd};color:${c.col};`;
  b.innerHTML=`<span>${c.icon}</span><span>${msg}</span>`;
}

async function testApiKey(){
  const key=document.getElementById('api-key-input').value.trim() || getApiKey();
  if(!key){alert('Entrez d\'abord une clé API.'); return;}
  const btn=document.getElementById('test-btn-txt');
  const spin=document.getElementById('test-spinner');
  btn.style.display='none'; spin.style.display='inline-block';
  showStatusBar('Test en cours…','info');
  try{
    const res=await fetch('https://api.anthropic.com/v1/messages',{
      method:'POST',
      headers:{'Content-Type':'application/json','x-api-key':key,'anthropic-version':'2023-06-01','anthropic-dangerous-direct-browser-access':'true'},
      body:JSON.stringify({model:'claude-sonnet-4-20250514',max_tokens:10,messages:[{role:'user',content:'Réponds juste: OK'}]})
    });
    if(res.ok){
      setStatusDot('ok');
      localStorage.setItem('alptech_api_key_status','ok');
      showStatusBar('Connexion réussie — la clé API fonctionne correctement.','ok');
    } else {
      const err=await res.json().catch(()=>({}));
      setStatusDot('err');
      localStorage.setItem('alptech_api_key_status','err');
      showStatusBar(`Erreur ${res.status} — ${err.error?.message||'Clé invalide ou expirée.'}`, 'err');
    }
  } catch(e){
    setStatusDot('err');
    showStatusBar('Impossible de joindre l\'API Anthropic. Vérifiez votre connexion.','err');
  } finally{
    btn.style.display='inline'; spin.style.display='none';
  }
}

// Restore dot state on load
(function initApiStatus(){
  const s=localStorage.getItem('alptech_api_key_status');
  if(s==='ok') setTimeout(()=>setStatusDot('ok'),100);
  else if(s==='err') setTimeout(()=>setStatusDot('err'),100);
})();

// ── AI CALL ──
async function callAI(messages, maxTokens=1000) {
  const res = await fetch('https://api.anthropic.com/v1/messages',{
    method:'POST', headers:{'Content-Type':'application/json','x-api-key':getApiKey(),'anthropic-version':'2023-06-01','anthropic-dangerous-direct-browser-access':'true'},
    body:JSON.stringify({model:'claude-sonnet-4-20250514',max_tokens:maxTokens,messages})
  });
  if(!res.ok) throw new Error('API '+res.status);
  const data=await res.json();
  const raw=data.content.map(b=>b.text||'').join('');
  return JSON.parse(raw.replace(/```json|```/g,'').trim());
}

// ── UTILS ──
function formatDate(dateStr) {
  if(!dateStr)return '—';
  const d=new Date(dateStr);
  const today=new Date(); const tom=new Date(today.getTime()+86400000);
  if(d.toDateString()===today.toDateString())return 'Aujourd\'hui';
  if(d.toDateString()===tom.toDateString())return 'Demain';
  return d.toLocaleDateString('fr-FR',{day:'numeric',month:'short'});
}

// ── INIT ──
loadDB();
const todayStr=new Date().toISOString().split('T')[0];
const agDateEl=document.getElementById('ag-date');
if(agDateEl)agDateEl.value=todayStr;

// Init HEXA — logos, company selector, tech list
initHEXA();

// Init Microsoft 365 / SharePoint
initMSAL();

// Init notifications badge
refreshNotifBadge();

// Start polling
startPolling();

// Handle deep link
handleDeepLink();
window.addEventListener('hashchange', handleDeepLink);
</script>
</body>
</html>
