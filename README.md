<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>Paper Pals</title>
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-title" content="Paper Pals">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="theme-color" content="#ffffff" id="themeMeta">
<link rel="apple-touch-icon" href="https://i.postimg.cc/Pxy94hpV/Untitled276-20261101160123.jpg">
<link rel="preconnect" href="https://fonts.googleapis.com"><link rel="preconnect" href="https://fonts.gstatic.com" crossorigin><link href="https://fonts.googleapis.com/css2?family=Nunito:wght@900&display=swap" rel="stylesheet">
<link rel="icon" href="https://i.postimg.cc/Pxy94hpV/Untitled276-20261101160123.jpg">
<script>
(function(){
 try{
  var ua=navigator.userAgent||"";
  var ios=/iPad|iPhone|iPod/.test(ua)||(navigator.platform==="MacIntel"&&navigator.maxTouchPoints>1);
  var android=/Android/i.test(ua);
  var mm=function(q){return window.matchMedia&&window.matchMedia(q).matches};
  var standalone=navigator.standalone===true||mm("(display-mode: standalone)")||mm("(display-mode: fullscreen)")||mm("(display-mode: minimal-ui)")||(document.referrer||"").indexOf("android-app://")===0;
  var dev=false;try{dev=localStorage.getItem("rpsDeveloperMode")==="true"}catch(e){}
  document.documentElement.classList.add(ios?"ios":"thick");
  if((ios||android)&&!standalone&&!dev)document.documentElement.classList.add("gated");
 }catch(e){}
})();
</script>
<script src="https://unpkg.com/peerjs@1.5.4/dist/peerjs.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<style>
:root{--blue:#3978ff;--purple:#8857f5;--pink:#ff5688;--green:#25c58a;--bg:#ffffff;--ink:#202944;
--muted:color-mix(in srgb,var(--ink) 55%,var(--bg));--soft:color-mix(in srgb,var(--bg) 92%,var(--ink));--line:color-mix(in srgb,var(--bg) 84%,var(--ink))}
*{box-sizing:border-box}
body{margin:0;min-height:100vh;background:var(--bg);color:var(--ink);font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif}
button,input,select{font:inherit}
button{cursor:pointer}
button:focus-visible,input:focus-visible,select:focus-visible{outline:3px solid #9cbcff;outline-offset:3px}
.ico{display:inline-block;width:1.15em;height:1.15em;flex:none;vertical-align:-.2em}
[data-i]{display:inline-flex;align-items:center;line-height:0}
.language{position:absolute;top:16px;right:16px;border:2px solid var(--line);color:var(--blue);background:var(--bg);border-radius:13px;padding:9px 14px;font-weight:800;z-index:5}
main{position:relative;z-index:2;min-height:100vh;display:grid;place-items:center;padding:85px 16px 70px}
.screen{width:100%;max-width:560px;text-align:center;animation:appear .22s ease}
.hidden{display:none!important}
@keyframes appear{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:translateY(0)}}
h1{font-size:clamp(35px,7vw,51px);line-height:1.12;letter-spacing:-2px;margin:0 auto 30px;max-width:450px;font-weight:900}
.logo{display:flex;flex-direction:column;align-items:center;max-width:none;margin:0 auto 28px;letter-spacing:0;line-height:.92;font-family:ui-rounded,"SF Pro Rounded","Arial Rounded MT Bold","Varela Round",Nunito,"Trebuchet MS",system-ui,sans-serif;font-weight:900;font-size:clamp(64px,21vw,124px)}
.logo .word{display:flex;justify-content:center}
/* LOGO de letras (contorno redondeado) — las sombras del contorno se generan por JS (ver script del <head>) */
.logo .l{position:relative;isolation:isolate;display:inline-block;margin:0 .01em;font-style:normal;color:var(--c);transform:translateY(var(--y,0em)) rotate(var(--r,0deg));filter:drop-shadow(0 .055em 0 var(--s)) drop-shadow(0 .09em .05em #2a3a6a26);animation:bob 2.6s ease-in-out var(--dl,0s) infinite}
.logo .l::before{content:attr(data-t);position:absolute;left:0;top:0;z-index:-1;color:var(--o)}
html.ios .logo .l::before{text-shadow:none;-webkit-text-stroke:.2em var(--o)}
.logo .half i{font-style:normal;color:var(--c1);clip-path:inset(-.4em 50% -.4em -.4em)}
.logo .half b{position:absolute;left:0;top:0;font-weight:inherit;color:var(--c2);clip-path:inset(-.4em -.4em -.4em 50%)}
.c-blue{--c:#9bbcff;--o:#5f86e8;--s:#4468c9}
.c-red{--c:#ff9db1;--o:#e8678a;--s:#c8486b}
.c-green{--c:#8ee3c0;--o:#3fbf93;--s:#2c9a73}
.c-half{--c1:#9bbcff;--c2:#ff9db1;--o:#8a7fe0;--s:#6a5fc0}
@keyframes bob{0%,100%{transform:translateY(var(--y,0em)) rotate(var(--r,0deg))}50%{transform:translateY(calc(var(--y,0em) - .05em)) rotate(var(--r,0deg))}}
@media (prefers-reduced-motion:reduce){.logo .l{animation:none}}
/* palabras pastel (Piedra / Papel / Tijera) */
.pword{display:inline-block;position:relative;font-family:ui-rounded,"SF Pro Rounded","Arial Rounded MT Bold",Nunito,"Trebuchet MS",system-ui,sans-serif;font-weight:900;color:var(--c);letter-spacing:.01em}
/* instalación */
#installGate{display:none}
html.gated #installGate{display:block;position:fixed;inset:0;z-index:150;background:var(--bg);overflow-y:auto;-webkit-overflow-scrolling:touch}
html.gated body{overflow:hidden}
html.gated main,html.gated .profile-card{display:none!important}
html.gated #devCorner,html.gated .language{z-index:160}
.gate-inner{max-width:560px;margin:0 auto;padding:60px 18px 100px;text-align:center}
.gate-inner .logo{font-size:clamp(56px,18vw,104px);margin:0 auto 22px}
.gate-title{display:block;margin:0 0 10px;font-size:clamp(26px,7vw,40px);line-height:1.1;letter-spacing:-1.2px;font-weight:900}
.gate-sub{margin:0 auto 22px;max-width:440px;color:var(--muted);font-size:15px;font-weight:700;line-height:1.5}
.gate-card{border:2px solid var(--line);border-radius:26px;padding:22px 18px;text-align:left;background:var(--bg)}
.gate-card h3{margin:0 0 16px;font-size:22px;font-weight:900;color:var(--blue)}
.gate-step{display:flex;gap:14px;align-items:flex-start;margin:0 0 16px}
.gate-num{flex:none;width:36px;height:36px;border-radius:12px;background:var(--blue);color:#fff;font-weight:900;font-size:17px;display:flex;align-items:center;justify-content:center;box-shadow:0 4px 0 #2458c8}
.gate-step p{margin:0;padding-top:5px;font-size:16px;line-height:1.45;font-weight:800}
.gate-step .ico{width:1.3em;height:1.3em;vertical-align:-.3em}
.gate-note{margin-top:6px;padding:14px 16px;border-radius:16px;border:2px solid #f5d77c;background:#fff4d6;color:#7a5300;font-size:14px;font-weight:800;line-height:1.5;text-align:left}
.gate-note.ok{border-color:#9be0c0;background:#e9fbf3;color:#137a4d}
.gate-top{margin:0 0 14px}.gate-install{margin:0 0 18px}
.gate-switch{margin-top:16px;border:0;background:transparent;color:var(--blue);font-weight:850;font-size:14px;padding:10px}
/* botones */
.btn{display:inline-flex;align-items:center;justify-content:center;gap:8px;width:245px;min-height:54px;border-radius:15px;border:0;font-size:16px;font-weight:850;transition:transform .15s,box-shadow .15s;color:var(--ink)}
.btn .ico{width:1.25em;height:1.25em}
.btn:hover:not(:disabled){transform:translateY(-2px)}
.play{background:var(--blue);color:#fff;box-shadow:0 4px 0 #2458c8}
.coming{background:var(--bg);border:2px solid var(--line);box-shadow:0 4px 0 var(--line)}
.vip{background:#fff5d5;color:#8b6200;border:2px solid #f5d77c;box-shadow:0 4px 0 #e7c35f}
.danger{background:#e0475b;color:#fff;box-shadow:0 4px 0 #b52d40}
.back{color:var(--blue);background:var(--soft);box-shadow:none}
.menu-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;width:100%}
.menu-grid .btn{width:100%}
.m-play{grid-column:1;grid-row:1;min-height:90px;font-size:19px}
.m-del{grid-column:1;grid-row:2;min-height:90px;font-size:17px}
.m-set{grid-column:2;grid-row:1/3;flex-direction:column;gap:6px;font-size:21px}
.m-del .ico{width:1em;height:1em}
.m-set .big .ico{width:72px;height:72px}
.m-vip{grid-column:1/3;min-height:46px}
.m-look{grid-column:1/3;min-height:46px}
.mode-grid{display:grid;grid-template-columns:1fr 1fr;gap:14px;width:100%;margin-bottom:6px}
.mode-card{min-height:320px;border-radius:23px;border:2px solid var(--line);background:var(--bg);box-shadow:0 4px 0 var(--line);padding:20px 12px;display:flex;flex-direction:column;align-items:center;justify-content:space-between;text-align:center;color:var(--ink);font-weight:900}
.mode-title{font-size:20px;line-height:1.2}
.mode-icon .ico{width:108px;height:108px}
.mode-multi{border-bottom:5px solid var(--blue)}.mode-bots{border-bottom:5px solid var(--green)}
.subtitle{color:var(--muted);line-height:1.6;margin:-12px auto 23px;max-width:380px}
.card{border:2px solid var(--line);border-radius:23px;padding:24px;background:var(--bg);text-align:left}
h2{display:flex;align-items:center;gap:10px;font-size:27px;letter-spacing:-.8px;margin:0 0 18px}
h2 .ico{width:1em;height:1em;vertical-align:baseline}
.field{margin:17px 0}
label{display:block;font-size:14px;font-weight:800;margin-bottom:8px}
input,select{width:100%;padding:12px;border:2px solid var(--line);background:var(--bg);border-radius:11px;color:var(--ink)}
input[type=color]{height:52px;padding:4px;cursor:pointer}
.note{color:var(--muted);font-size:13px;line-height:1.5}
.card-actions{display:flex;gap:12px;margin-top:22px}
.card-actions .btn{width:50%;font-size:14px}
.coinbar{display:inline-flex;align-items:center;gap:8px;background:#fff7d9;border:2px solid #ffe8a0;color:#725000;border-radius:14px;padding:10px 15px;font-weight:900;margin:0 auto 20px}
.coinbar .ico{width:24px;height:24px}
.full{width:100%;margin-top:12px}
.menu-link{display:inline-flex;align-items:center;gap:6px;border:0;background:transparent;color:var(--muted);margin-top:8px;padding:10px;font-weight:750}
.menu-link:hover{color:var(--blue)}
.dev-status{display:inline-flex;align-items:center;gap:6px;background:#e9fbf3;color:#16764f;border-radius:9px;padding:5px 9px;font-size:12px;font-weight:900;margin-bottom:12px}
#devCorner{position:fixed;left:14px;bottom:14px;width:46px;height:46px;z-index:99;border:2px solid var(--line);background:var(--bg);border-radius:15px;padding:0;display:flex;align-items:center;justify-content:center}
#devCorner .ico{width:24px;height:24px}
.dev-modal{position:fixed;inset:0;z-index:200;background:#17213b80;display:grid;place-items:center;padding:20px}
.dev-box{width:100%;max-width:340px;background:var(--bg);color:var(--ink);border-radius:22px;padding:25px;box-shadow:0 15px 50px #0003;text-align:center}
.dev-box h2{margin-bottom:8px;justify-content:center}
.dev-box p{font-size:14px;color:var(--muted);margin-bottom:18px;line-height:1.5}
.dev-box input{text-align:center;font-size:22px;letter-spacing:7px;font-weight:900}
.dev-buttons{display:flex;gap:10px;margin-top:16px}
.dev-buttons button{width:50%;min-height:45px;border:0;border-radius:12px;font-weight:850}
.dev-cancel{background:var(--soft);color:var(--blue)}
.dev-submit{background:var(--blue);color:#fff}
.dev-submit.red{background:#e0475b}
.warn-ico .ico{width:64px;height:64px}
/* perfil */
.profile-card{position:absolute;top:14px;left:14px;z-index:5;display:flex;align-items:center;gap:10px;max-width:calc(100% - 96px);padding:8px 10px 8px 8px;border-radius:15px;background:var(--blue);color:#fff;box-shadow:0 4px 0 #2458c8}
.avatar{display:block;width:42px;height:42px;flex:none;border-radius:50%;border:3px solid #fff;background-size:cover;background-position:center}
.profile-name{min-width:0;max-width:120px;font-size:15px;font-weight:850;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.profile-edit{flex:none;display:flex;align-items:center;justify-content:center;width:30px;height:30px;padding:0;border:0;border-radius:50%;background:#ffffff2e}
.profile-edit .ico{width:16px;height:16px}
.profile-box{max-width:360px}
.profile-box input{font-size:16px;letter-spacing:0;font-weight:700;text-align:center}
.profile-box .field{text-align:left;margin:12px 0}
.avatar-big{width:104px;height:104px;margin:6px auto 4px;border-radius:50%;border:4px solid var(--line);background-size:cover;background-position:center}
.photo-actions{display:flex;flex-direction:column;gap:10px;margin:14px 0}
.photo-actions .btn{width:100%;min-height:46px;font-size:14px;cursor:pointer}
.sr-only{position:absolute;width:1px;height:1px;opacity:0;pointer-events:none;overflow:hidden}
/* reglas */
.rules-box{max-width:400px;max-height:88vh;overflow-y:auto;text-align:left}
.rules-box h2{justify-content:center}
.rule-row{border:2px solid var(--line);border-radius:14px;padding:11px 12px;margin-bottom:9px;font-size:15px;line-height:1.8}
.rule-row .win{color:#137a4d;font-weight:800}.rule-row .lose{color:#c43b4a;font-weight:800}
.rule-main{display:flex;align-items:center;gap:8px;font-size:17px;font-weight:900}
.rule-main .ico{width:1.6em;height:1.6em}
/* ajustes */
.theme-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:10px}
.swatch{border:3px solid var(--line);border-radius:14px;height:62px;display:flex;align-items:flex-end;justify-content:center;padding:4px 2px;font-size:11px;font-weight:900;overflow:hidden}
.swatch.on{border-color:var(--blue);box-shadow:0 0 0 3px #3978ff33}
.preview{margin-top:14px;padding:14px;border-radius:14px;background:var(--soft);font-weight:850;text-align:center}
/* ====== ESCENA 3D ====== */
#stage3d{position:fixed;inset:0;width:100%;height:100%;z-index:0;display:block;touch-action:none}
html.has3d .card{background:color-mix(in srgb,var(--bg) 93%,transparent)}
.home-gap{height:clamp(150px,27vh,270px);pointer-events:none}
html:not(.has3d) .home-gap{display:none}
#home .logo{font-size:clamp(52px,15vw,98px);margin-bottom:4px}
#playTitle{display:inline-block;padding:6px 22px;border-radius:18px;background:color-mix(in srgb,var(--bg) 86%,transparent);backdrop-filter:blur(6px);-webkit-backdrop-filter:blur(6px)}
html.ingame #devCorner{display:none}
/* partida */
#game{position:fixed;inset:0;z-index:3;max-width:560px;margin:0 auto;padding:10px 10px calc(10px + env(safe-area-inset-bottom));display:none;flex-direction:column;gap:8px;text-align:center}
#game:not(.hidden){display:flex}
.g-hud{border-radius:18px;padding:8px;background:color-mix(in srgb,var(--bg) 84%,transparent);backdrop-filter:blur(6px);-webkit-backdrop-filter:blur(6px);border:2px solid color-mix(in srgb,var(--line) 70%,transparent)}
.g-row{display:flex;align-items:center;gap:8px;flex-wrap:wrap;padding-right:72px;min-height:44px;margin-bottom:6px}
.g-row .coinbar{margin:0;padding:6px 10px}
.g-row .coinbar .ico{width:20px;height:20px}
.g-row .dev-status{margin:0}
.round-count{color:var(--purple);font-size:18px;font-weight:900;letter-spacing:2px}
.scoreboard{display:grid;grid-template-columns:1fr auto 1fr;align-items:center;gap:10px;border-radius:16px;padding:6px 8px;background:var(--soft)}
.score-number{font-size:40px;line-height:1;font-weight:900}
.score-name{font-size:15px;font-weight:800;color:var(--muted);overflow-wrap:anywhere;margin-top:2px}
.vs{color:var(--pink);font-size:20px;font-weight:900}
.g-sub{margin:0 auto;padding:6px 14px;border-radius:14px;background:color-mix(in srgb,var(--bg) 84%,transparent);backdrop-filter:blur(6px);-webkit-backdrop-filter:blur(6px);font-size:17px;font-weight:900;max-width:100%}
.g-sub:empty{display:none}
.g-stage{position:relative;flex:1;min-height:150px}
#gameAnchor{position:absolute;left:0;right:0;top:0;bottom:34%;pointer-events:none}
.result{position:absolute;left:0;right:0;bottom:0;max-height:64%;overflow:auto;background:color-mix(in srgb,var(--bg) 80%,transparent);backdrop-filter:blur(6px);-webkit-backdrop-filter:blur(6px);border-radius:18px;padding:8px 6px;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:6px;line-height:1.3;font-size:15px;font-weight:800;overflow-wrap:anywhere}
.countdown-word{font-size:clamp(44px,13vw,64px);font-weight:900;line-height:1.05;animation:pop .3s ease}
.countdown-word .pword{font-size:clamp(38px,11vw,54px)}
@keyframes pop{0%{transform:scale(.65);opacity:.3}100%{transform:scale(1);opacity:1}}
.rtitle{font-size:21px;font-weight:900;line-height:1.2}
.rtitle.win{color:#25c58a}.rtitle.lose{color:#e0475b}.rtitle.draw,.rtitle.none{color:var(--purple)}
.rfinal{font-size:21px;font-weight:900;color:var(--blue)}
.duel{display:grid;grid-template-columns:repeat(auto-fit,minmax(84px,1fr));gap:8px;width:100%}
.pcard{background:var(--bg);border:3px solid var(--line);border-radius:16px;padding:6px 4px;display:flex;flex-direction:column;align-items:center;gap:2px;min-width:0}
.pcard.win{border-color:#25c58a;background:color-mix(in srgb,#25c58a 14%,var(--bg))}
.pcard.lose{border-color:#e0475b;opacity:.8}
.pname{font-size:13px;font-weight:900;color:var(--muted);overflow-wrap:anywhere}
.pcard .ico{width:44px;height:44px}
.pmove{font-size:20px;line-height:1.1}
.pmove .pword{font-size:20px}
.nothing{font-size:22px;font-weight:900;color:var(--muted)}
.choices{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:8px;margin:0}
.choice{min-width:0;min-height:96px;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:4px;background:var(--bg);border:3px solid var(--line);border-radius:20px;color:var(--ink);font-weight:900;padding:6px 2px;box-shadow:0 4px 0 var(--line)}
.choice .ico{width:48px;height:48px}
.choice .pword{font-size:20px}
.choice:hover:not(:disabled){transform:translateY(-2px)}
.choice:disabled{cursor:not-allowed;opacity:.4}
.g-btns{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.g-btns .btn{width:100%;min-height:42px;font-size:14px;margin:0}
.swatch{position:relative;flex-direction:column;align-items:center;justify-content:flex-end;gap:2px}
.swatch .p{display:inline-flex;align-items:center;gap:3px;background:#fff7d9;color:#725000;border-radius:8px;padding:1px 5px;font-size:11px}
.swatch .p .ico{width:12px;height:12px}
.swatch.lockd{opacity:.9}
.voice-on{background:#e9fbf3!important;border-color:#25c58a!important}
.slot-info{background:var(--soft);border-radius:13px;padding:13px;margin:12px 0;line-height:1.7}
.vip-card{border:2px solid #f0d78e;background:#fffaf0;color:#202944;border-radius:18px;padding:18px;text-align:center;margin:15px 0}
.vip-title{font-size:28px;color:#a87900;font-weight:950}
.online-status{background:var(--soft);border-radius:13px;padding:14px;margin:14px 0;line-height:1.7;text-align:center;font-size:14px;min-height:50px}
.room-code{display:inline-block;font-size:32px;font-weight:950;letter-spacing:6px;color:var(--blue);margin:4px 0}
.or-line{text-align:center;color:var(--muted);font-size:13px;font-weight:800;margin:16px 0 4px}
#joinCode{text-align:center;letter-spacing:5px;font-weight:900;font-size:20px;text-transform:uppercase}
@media(max-height:660px){.g-stage{min-height:110px}.choice{min-height:72px}.choice .ico{width:36px;height:36px}.choice .pword{font-size:17px}.score-number{font-size:32px}}
@media(max-width:420px){.card{padding:19px 14px}h1{letter-spacing:-1.5px}.mode-card{min-height:270px;padding:16px 8px}.mode-title{font-size:17px}.mode-icon .ico{width:88px;height:88px}.profile-name{max-width:90px}}
.logo .tag3d{font-size:.2em;line-height:1;letter-spacing:.25em;margin-top:.15em;color:var(--muted);font-weight:900;animation:none}
.g-hud>.round-count{text-align:center;margin:0 0 6px;line-height:1}
#stage3d{pointer-events:none}
#game .g-btns,#game .choices{position:relative;z-index:5}
/* personaje */
#look .home-gap{height:clamp(140px,24vh,230px)}
#lookBody{max-height:38vh;overflow-y:auto;padding-right:4px}
.chips{display:flex;flex-wrap:wrap;gap:8px}
.chip{width:38px;height:38px;border-radius:50%;border:3px solid var(--line);padding:0;color:var(--muted);font-weight:900}
.chip.on{border-color:var(--blue);box-shadow:0 0 0 3px #3978ff33}
.opt{padding:9px 12px;border:2px solid var(--line);border-radius:12px;background:var(--bg);color:var(--ink);font-weight:800;font-size:14px}
.opt.on{border-color:var(--blue);background:var(--soft)}
.look-actions{display:flex;gap:10px;margin:0 0 14px}
.look-actions .btn{width:33.3%;min-height:46px;font-size:13px}
</style>
<script>
/* Sombras del contorno del logo y de las palabras (se generan para no repetir 50 valores a mano) */
(function(){
 function ring(r,n,c){var a=[];for(var i=0;i<n;i++){var t=i/n*Math.PI*2;a.push((r*Math.cos(t)).toFixed(3)+"em "+(r*Math.sin(t)).toFixed(3)+"em 0 "+c)}return a.join(",")}
 var o="var(--o)",s="";
 s+=".logo .l::before{text-shadow:"+ring(.1,36,o)+","+ring(.055,18,o)+"}";
 s+="html.thick .logo .l::before{text-shadow:"+ring(.112,36,o)+","+ring(.062,18,o)+"}";
 s+="html.thick .logo .l{text-shadow:"+ring(.012,16,"currentColor")+","+ring(.006,8,"currentColor")+"}";
 s+=".pword{text-shadow:"+ring(.08,16,o)+","+ring(.04,16,o)+",0 .1em 0 "+o+"}";
 var st=document.createElement("style");st.textContent=s;document.head.appendChild(st);
})();
</script>
</head>
<body>
<button class="language" id="languageBtn" onclick="toggleLanguage()">EN</button>
<button id="devCorner" aria-label="Developer access" onclick="developerCorner()"><span data-i="lock"></span></button>

<div id="installGate" role="dialog" aria-modal="true" aria-labelledby="gateTitle">
 <div class="gate-inner">
  <h1 class="logo" id="gateLogo" aria-label="Paper Pals"></h1>
  <h2 class="gate-title" id="gateTitle"></h2>
  <p class="gate-sub" id="gateSub"></p>
  <div id="gateBody"></div>
 </div>
</div>

<div class="profile-card" id="profileCard">
 <span class="avatar" id="profileAvatar"></span>
 <span class="profile-name" id="profileName">Jugador</span>
 <button class="profile-edit" aria-label="Editar perfil" onclick="openProfileEditor()"><span data-i="pencil"></span></button>
</div>

<div id="profileModal" class="dev-modal hidden" onclick="if(event.target===this)closeProfileEditor()">
 <div class="dev-box profile-box">
  <h2 id="profileModalTitle"></h2>
  <div class="avatar-big" id="profileAvatarBig"></div>
  <div class="photo-actions">
   <label class="btn coming" for="photoInput" id="photoPickBtn"></label>
   <button class="btn back" id="photoRemoveBtn" onclick="removePendingPhoto()"></button>
  </div>
  <input type="file" id="photoInput" class="sr-only" accept="image/*" onchange="handlePhotoFile(this)">
  <div class="field">
   <label for="profileNameInput" id="profileNameLabel"></label>
   <input id="profileNameInput" maxlength="14" autocomplete="off" placeholder="Jugador">
  </div>
  <div class="dev-buttons">
   <button class="dev-cancel" id="profileCancelBtn" onclick="closeProfileEditor()"></button>
   <button class="dev-submit" id="profileSaveBtn" onclick="saveProfileEditor()"></button>
  </div>
 </div>
</div>

<div id="devModal" class="dev-modal hidden">
 <div class="dev-box">
  <h2><span data-i="lock"></span>Developer Access</h2>
  <p>Ingresa el código de desarrollador:</p>
  <input id="devCodeInput" type="password" inputmode="numeric" maxlength="6" placeholder="••••••" autocomplete="off">
  <div class="dev-buttons">
   <button class="dev-cancel" onclick="closeDeveloperModal()">Cancelar</button>
   <button class="dev-submit" onclick="submitDeveloperCode()">Desbloquear</button>
  </div>
 </div>
</div>

<div id="deleteModal" class="dev-modal hidden" onclick="if(event.target===this)closeDelete()">
 <div class="dev-box">
  <div class="warn-ico" data-i="trash" data-c="#e0475b"></div>
  <h2 id="delTitle"></h2>
  <p id="delText"></p>
  <div class="dev-buttons">
   <button class="dev-cancel" id="delCancel" onclick="closeDelete()"></button>
   <button class="dev-submit red" id="delConfirm" onclick="confirmDelete()"></button>
  </div>
 </div>
</div>

<div id="rulesModal" class="dev-modal hidden" onclick="if(event.target===this)closeRules()">
 <div class="dev-box rules-box">
  <h2 id="rulesTitle"></h2>
  <div id="rulesList"></div>
  <button class="btn play full" id="rulesCloseBtn" onclick="closeRules()"></button>
 </div>
</div>

<main>
<section class="screen" id="home">
<h1 class="logo" aria-label="Paper Pals">
 <span class="word" aria-hidden="true">
  <span class="l c-blue" style="--r:-6deg;--y:.03em;--dl:0s" data-t="P">P</span>
  <span class="l c-blue" style="--r:5deg;--y:-.04em;--dl:.12s" data-t="a">a</span>
  <span class="l c-half half" style="--r:-3deg;--y:.04em;--dl:.24s" data-t="p"><i>p</i><b>p</b></span>
  <span class="l c-red" style="--r:6deg;--y:-.03em;--dl:.36s" data-t="e">e</span>
  <span class="l c-red" style="--r:-4deg;--y:.03em;--dl:.48s" data-t="r">r</span>
 </span>
 <span class="word" aria-hidden="true">
  <span class="l c-green" style="--r:5deg;--y:-.02em;--dl:.6s" data-t="P">P</span>
  <span class="l c-green" style="--r:-5deg;--y:.04em;--dl:.72s" data-t="a">a</span>
  <span class="l c-green" style="--r:4deg;--y:-.03em;--dl:.84s" data-t="l">l</span>
  <span class="l c-green" style="--r:-6deg;--y:.03em;--dl:.96s" data-t="s">s</span>
 </span>
 <span class="tag3d" aria-hidden="true">3D</span>
</h1>
<div class="home-gap" aria-hidden="true"></div>
<div class="coinbar"><span data-i="coin"></span><span id="homeCoins">0</span><span class="coinsLabel">monedas</span></div>
<div id="devBadgeHome" class="dev-status hidden">MODO DESARROLLADOR ∞</div>
<div id="vipBadgeHome" class="dev-status hidden"><span data-i="crown"></span>VIP ACTIVADO</div>
<div class="menu-grid">
<button class="btn play m-play" id="menuPlay" onclick="showScreen('playMenu')">Jugar</button>
<button class="btn coming m-del" id="menuDel" onclick="openDelete()"></button>
<button class="btn coming m-set" onclick="openSettings()"><span id="menuSet">Configuraciones</span><span class="big" data-i="gear"></span></button>
<button class="btn vip m-vip" onclick="openVIP()"><span data-i="crown"></span>VIP</button>
<button class="btn coming m-look" id="menuLook" onclick="openLook()"></button>
</div>
</section>

<section class="screen hidden" id="playMenu">
<h1 id="playTitle">Jugar</h1>
<div class="mode-grid">
<button class="mode-card mode-multi" onclick="openLocalSetup()"><span class="mode-title" id="modeMultiTitle">Multijugador</span><span class="mode-icon" data-i="people" aria-hidden="true"></span></button>
<button class="mode-card mode-bots" onclick="openBotsSetup()"><span class="mode-title" id="modeBotsTitle">Jugar contra bots</span><span class="mode-icon" data-i="robot" aria-hidden="true"></span></button>
</div>
<button class="btn back full" id="playBackBtn" onclick="showScreen('home')">Volver al menú</button>
</section>

<section class="screen hidden" id="settings">
<div class="card">
<h2><span data-i="gear"></span><span id="setTitle"></span></h2>
<div class="coinbar"><span data-i="coin"></span><span id="settingsCoins">0</span><span class="coinsLabel">monedas</span></div>
<p class="note" id="setPriceNote"></p>
<label id="setThemeLbl"></label>
<div class="theme-grid" id="themeGrid"></div>
<div class="field"><label for="bgColor" id="setBgLbl"></label><input type="color" id="bgColor" oninput="customColors()"><button class="btn vip full" id="unlockCustom" onclick="buyCustom()"></button></div>
<div class="field"><label for="inkColor" id="setInkLbl"></label><input type="color" id="inkColor" oninput="customColors()"></div>
<div class="preview" id="setPreview"></div>
<button class="btn coming full" id="setReset" onclick="applyPreset(0)"></button>
<button class="btn back full" id="setBack" onclick="showScreen('home')"></button>
</div>
</section>

<section class="screen hidden" id="vipScreen">
<div class="card">
<h2><span data-i="crown"></span>Membresía VIP</h2>
<div class="vip-card">
<div class="vip-title">VIP</div>
<div style="font-size:30px;font-weight:950;margin:10px" id="vipPriceText">2,500</div>
<p>Desbloquea el estilo VIP de tu cuenta.</p>
</div>
<ul>
<li>Insignia VIP en el menú.</li>
<li>Nombre VIP en tus partidas.</li>
<li>Estilo exclusivo para tu cuenta.</li>
</ul>
<p class="note">El VIP se compra una sola vez y queda guardado en este dispositivo.</p>
<button class="btn vip full" id="buyVipButton" onclick="buyVIP()">Comprar VIP</button>
<button class="btn back full" onclick="showScreen('home')">Volver</button>
</div>
</section>

<section class="screen hidden" id="look">
<div class="home-gap" id="lookGap" aria-hidden="true"></div>
<div class="card">
<h2 id="lookTitle"></h2>
<div class="look-actions">
<button class="btn coming" id="lookRandom" onclick="randomLook()"></button>
<button class="btn coming" id="lookReset" onclick="resetLook()"></button>
<button class="btn play" id="lookDone" onclick="showScreen('home')"></button>
</div>
<div id="lookBody"></div>
</div>
</section>

<section class="screen hidden" id="setup">
<div class="card">
<h2><span data-i="robot"></span><span id="botsSetupTitle"></span></h2>
<div class="field">
<label for="botCount" id="botCountLabel"></label>
<select id="botCount">
<option value="1">1 bot</option>
<option value="2">2 bots</option>
<option value="3">3 bots</option>
</select>
</div>
<div class="card-actions">
<button class="btn back" id="botsBackBtn" onclick="showScreen('playMenu')"></button>
<button class="btn play" id="botsStartBtn" onclick="startGame()"></button>
</div>
</div>
</section>

<section class="screen hidden" id="localSetup">
<div class="card">
<h2><span data-i="globe"></span>Multijugador online</h2>
<p class="subtitle">Juega con un amigo desde otro teléfono. Los dos necesitan internet.</p>
<button class="btn play full" id="createRoomBtn" onclick="createRoom()">Crear sala</button>
<div class="or-line">— o —</div>
<div class="field">
<label for="joinCode">Código de la sala</label>
<input id="joinCode" maxlength="5" placeholder="ABCDE" autocomplete="off">
</div>
<button class="btn coming full" id="joinRoomBtn" onclick="joinRoom()">Unirme a la sala</button>
<div class="online-status hidden" id="onlineStatus"></div>
<div class="slot-info"><strong>¿Cómo funciona?</strong><br>Uno crea la sala y le pasa el código al otro. El primero en ganar 3 rondas gana.</div>
<button class="btn back full" onclick="showScreen('playMenu')">Volver</button>
</div>
</section>

<section class="screen hidden" id="game">
 <h2 id="arenaTitle" class="sr-only">Arena de batalla</h2>
 <div class="g-hud">
  <div class="g-row">
   <div class="coinbar"><span data-i="coin"></span><span id="gameCoins">0</span><span class="coinsLabel">monedas</span></div>
   <div id="devBadgeGame" class="dev-status hidden">MODO DESARROLLADOR ∞</div>
   <div id="vipBadgeGame" class="dev-status hidden"><span data-i="crown"></span>VIP</div>
  </div>
  <div class="round-count" id="roundCount">RONDA 1</div>
  <div class="scoreboard">
   <div><div class="score-number" id="playerScore">0</div><div class="score-name" id="playerScoreName">Jugador</div></div>
   <div class="vs">VS</div>
   <div><div class="score-number" id="botScore">0</div><div class="score-name" id="botScoreName">Bot 1</div></div>
  </div>
 </div>
 <p class="g-sub" id="arenaSubtitle"></p>
 <div class="g-stage">
  <div id="gameAnchor"></div>
  <div class="result" id="result" aria-live="polite"></div>
 </div>
 <div class="choices" id="choices"></div>
 <div class="g-btns">
  <button class="btn coming" id="rulesBtn" onclick="openRules()"></button>
  <button class="btn play" id="newGameBtn" onclick="startGame()">Nueva partida</button>
  <button class="btn coming hidden" id="voiceBtn" onclick="toggleVoice()"></button>
  <button class="btn back" id="menuLink" onclick="leaveGame()">Menú principal</button>
 </div>
 <audio id="voiceAudio" autoplay playsinline></audio>
</section>
</main>

<script>
/* ALMACENAMIENTO: localStorage + respaldo en window.name */
const MEM_PREFIX="RPSDATA:";
let memStore={};
try{if(typeof window.name==="string"&&window.name.indexOf(MEM_PREFIX)===0)memStore=JSON.parse(window.name.slice(MEM_PREFIX.length))||{}}catch(e){memStore={}}
function storeGet(k){try{const v=localStorage.getItem(k);if(v!==null)return v}catch(e){}return Object.prototype.hasOwnProperty.call(memStore,k)?memStore[k]:null}
function storeSet(k,v){try{localStorage.setItem(k,v)}catch(e){}memStore[k]=v;try{window.name=MEM_PREFIX+JSON.stringify(memStore)}catch(e){}}
try{if(navigator.storage&&navigator.storage.persist)navigator.storage.persist()}catch(e){}

/* =====================================================================
   ESCENA 3D: parque (medio realista, medio cartón) + personaje que hace
   los gestos de piedra / papel / tijera con la mano.
   Si WebGL o three.js no cargan, Stage = null y el juego funciona igual.
   ===================================================================== */
const Stage=(function(){
 if(typeof THREE==="undefined")return null;
 let renderer,cv;
 try{renderer=new THREE.WebGLRenderer({antialias:true,powerPreference:"high-performance"});cv=renderer.domElement}catch(e){return null}
 try{
  const MOBILE=/Android|iPhone|iPad|iPod/i.test(navigator.userAgent||"")||(navigator.platform==="MacIntel"&&navigator.maxTouchPoints>1);
  cv.id="stage3d";cv.setAttribute("aria-hidden","true");
  document.body.insertBefore(cv,document.body.firstChild);
  document.documentElement.classList.add("has3d");
  let W=window.innerWidth,H=window.innerHeight;
  renderer.setPixelRatio(Math.min(window.devicePixelRatio||1,MOBILE?1.75:2));
  renderer.setSize(W,H,false);
  renderer.outputEncoding=THREE.sRGBEncoding;
  renderer.toneMapping=THREE.ACESFilmicToneMapping;
  renderer.toneMappingExposure=1;
  renderer.shadowMap.enabled=true;
  renderer.shadowMap.type=THREE.PCFSoftShadowMap;

  const scene=new THREE.Scene();
  const col=h=>new THREE.Color(h).convertSRGBToLinear();
  const rnd=(a,b)=>a+Math.random()*(b-a);
  function ctex(w,h,draw,rx,ry){
   const c=document.createElement("canvas");c.width=w;c.height=h;draw(c.getContext("2d"),w,h);
   const t=new THREE.CanvasTexture(c);t.encoding=THREE.sRGBEncoding;t.wrapS=t.wrapT=THREE.RepeatWrapping;
   if(rx)t.repeat.set(rx,ry||rx);t.anisotropy=4;return t;
  }
  /* cartón: grano + ondulado fino */
  const grain=ctex(128,128,(x,w,h)=>{
   x.fillStyle="#f2eee7";x.fillRect(0,0,w,h);
   for(let i=0;i<1800;i++){const v=195+Math.random()*60|0;x.fillStyle="rgba("+v+","+v+","+(v-10)+",.4)";x.fillRect(Math.random()*w,Math.random()*h,1+Math.random()*2,1+Math.random()*2)}
   x.fillStyle="rgba(120,90,50,.08)";for(let y=0;y<h;y+=5)x.fillRect(0,y,w,1);
  });
  const grassT=ctex(256,256,(x,w,h)=>{
   x.fillStyle="#6a9845";x.fillRect(0,0,w,h);
   for(let i=0;i<420;i++){x.fillStyle="hsla("+(80+Math.random()*35|0)+",45%,"+(30+Math.random()*28|0)+"%,.3)";x.beginPath();x.arc(Math.random()*w,Math.random()*h,3+Math.random()*12,0,6.3);x.fill()}
   for(let i=0;i<1400;i++){x.strokeStyle="hsla("+(85+Math.random()*30|0)+",50%,"+(25+Math.random()*35|0)+"%,.5)";x.lineWidth=1;const px=Math.random()*w,py=Math.random()*h;x.beginPath();x.moveTo(px,py);x.lineTo(px+rnd(-2,2),py-rnd(3,7));x.stroke()}
  },22,22);
  const sandT=ctex(128,128,(x,w,h)=>{
   x.fillStyle="#d3bc90";x.fillRect(0,0,w,h);
   for(let i=0;i<500;i++){x.fillStyle="rgba("+(140+Math.random()*70|0)+","+(120+Math.random()*60|0)+",85,.5)";x.fillRect(Math.random()*w,Math.random()*h,1+Math.random()*3,1+Math.random()*3)}
  });
  const skyT=ctex(4,256,(x,w,h)=>{
   const g=x.createLinearGradient(0,0,0,h);
   g.addColorStop(0,"#4a8bde");g.addColorStop(.45,"#86bdf0");g.addColorStop(.72,"#d6eaf9");g.addColorStop(.74,"#e6f0d8");g.addColorStop(1,"#e6f0d8");
   x.fillStyle=g;x.fillRect(0,0,w,h);
  });
  skyT.wrapS=skyT.wrapT=THREE.ClampToEdgeWrapping;

  const M=(c,o)=>new THREE.MeshStandardMaterial(Object.assign({color:col(c),map:grain,roughness:.88,metalness:0,flatShading:true},o||{}));
  const OUT=new THREE.MeshBasicMaterial({color:col("#2a1f17"),side:THREE.BackSide});
  function mk(g,m,ol,sc){
   const me=new THREE.Mesh(g,m);me.castShadow=true;me.receiveShadow=true;
   if(ol!==false){const o=new THREE.Mesh(g,OUT);o.scale.setScalar(sc||1.08);me.add(o)}
   return me;
  }

  /* ---------- luces ---------- */
  const hemi=new THREE.HemisphereLight(col("#bcd6ff"),col("#4f6a35"),.6);scene.add(hemi);
  const sun=new THREE.DirectionalLight(col("#ffe3b3"),1.7);
  sun.position.set(-6,9,6.5);sun.target.position.set(0,0,0);scene.add(sun,sun.target);
  sun.castShadow=true;sun.shadow.mapSize.set(MOBILE?1024:2048,MOBILE?1024:2048);
  const sc=sun.shadow.camera;sc.left=-9;sc.right=9;sc.top=9;sc.bottom=-9;sc.near=1;sc.far=40;
  sun.shadow.bias=-.0004;sun.shadow.normalBias=.03;
  const fill=new THREE.DirectionalLight(col("#9fc0ff"),.25);fill.position.set(6,3,8);scene.add(fill);

  /* ---------- cielo, niebla, colinas ---------- */
  const dome=new THREE.Mesh(new THREE.SphereGeometry(160,24,16),new THREE.MeshBasicMaterial({map:skyT,side:THREE.BackSide,fog:false,toneMapped:false,depthWrite:false}));
  scene.add(dome);
  const fogBase=col("#d4e6f3");
  scene.fog=new THREE.Fog(fogBase.clone(),22,90);
  const hillM=M("#5d8a4b");
  [[-34,-70,32,9],[10,-78,40,10],[48,-66,30,8],[-70,-60,26,7]].forEach(h=>{
   const m=new THREE.Mesh(new THREE.SphereGeometry(h[2],20,12),hillM);m.scale.y=h[3]/h[2];m.position.set(h[0],-1,h[1]);m.receiveShadow=false;scene.add(m);
  });

  /* ---------- suelo y camino ---------- */
  const ground=new THREE.Mesh(new THREE.PlaneGeometry(240,240),new THREE.MeshStandardMaterial({map:grassT,color:0xffffff,roughness:1}));
  ground.rotation.x=-Math.PI/2;ground.receiveShadow=true;scene.add(ground);
  const pathPts=[[1.8,12],[2.6,3],[4.6,-4],[3,-12],[-2,-22],[-3,-48]].map(p=>new THREE.Vector3(p[0],0,p[1]));
  const curve=new THREE.CatmullRomCurve3(pathPts);
  const samples=curve.getPoints(60);
  (function(){
   const pos=[],uv=[],idx=[];
   for(let i=0;i<=60;i++){
    const p=samples[i],tg=curve.getTangent(i/60),nx=-tg.z,nz=tg.x,w=1.55*(1-i/60*.45);
    pos.push(p.x+nx*w,.012,p.z+nz*w,p.x-nx*w,.012,p.z-nz*w);uv.push(0,i*.7,1,i*.7);
    if(i<60){const a=i*2;idx.push(a,a+2,a+1,a+1,a+2,a+3)}
   }
   const g=new THREE.BufferGeometry();
   g.setAttribute("position",new THREE.Float32BufferAttribute(pos,3));
   g.setAttribute("uv",new THREE.Float32BufferAttribute(uv,2));
   g.setIndex(idx);g.computeVertexNormals();
   const m=new THREE.Mesh(g,new THREE.MeshStandardMaterial({map:sandT,color:0xffffff,roughness:1,side:THREE.DoubleSide}));
   m.receiveShadow=true;scene.add(m);
  })();
  function nearPath(x,z,d){for(let i=0;i<samples.length;i+=2){const p=samples[i];if((p.x-x)*(p.x-x)+(p.z-z)*(p.z-z)<d*d)return true}return false}

  /* pasto alto (instancias) */
  (function(){
   const N=MOBILE?420:800;
   const geo=new THREE.ConeGeometry(.05,.3,4);geo.translate(0,.15,0);
   const inst=new THREE.InstancedMesh(geo,new THREE.MeshStandardMaterial({roughness:1,flatShading:true}),N);
   const d=new THREE.Object3D(),c=new THREE.Color();let k=0;
   while(k<N){
    const x=rnd(-13,13),z=rnd(-16,7);
    if(nearPath(x,z,1.8))continue;
    d.position.set(x,0,z);d.rotation.set(rnd(-.25,.25),rnd(0,6),rnd(-.25,.25));d.scale.setScalar(rnd(.7,1.6));d.updateMatrix();
    inst.setMatrixAt(k,d.matrix);c.setHSL(rnd(.22,.3),.5,rnd(.2,.38));c.convertSRGBToLinear();inst.setColorAt(k,c);k++;
   }
   inst.receiveShadow=true;scene.add(inst);
  })();
  /* flores (instancias) */
  (function(){
   const beds=[[3.4,2.2],[-3.6,-1.6],[-5.5,1.5]],N=beds.length*26;
   const heads=new THREE.InstancedMesh(new THREE.SphereGeometry(.075,7,5),new THREE.MeshStandardMaterial({roughness:.8,flatShading:true}),N);
   const stems=new THREE.InstancedMesh(new THREE.CylinderGeometry(.01,.01,1,4),new THREE.MeshStandardMaterial({color:col("#3b7a33"),roughness:1}),N);
   const pal=["#ff5b6e","#ffd23f","#ff8fc0","#ffffff","#a67cff","#ff9a3d"],d=new THREE.Object3D(),c=new THREE.Color();let k=0;
   beds.forEach(b=>{for(let i=0;i<26;i++){
    const a=rnd(0,6.28),r=Math.sqrt(Math.random())*.95,h=rnd(.22,.45),x=b[0]+Math.cos(a)*r,z=b[1]+Math.sin(a)*r;
    d.position.set(x,h/2,z);d.rotation.set(0,0,0);d.scale.set(1,h,1);d.updateMatrix();stems.setMatrixAt(k,d.matrix);
    d.position.set(x,h+.02,z);d.scale.setScalar(1);d.updateMatrix();heads.setMatrixAt(k,d.matrix);
    c.set(pal[(Math.random()*pal.length)|0]).convertSRGBToLinear();heads.setColorAt(k,c);k++;
   }});
   heads.castShadow=true;scene.add(heads,stems);
  })();

  /* ---------- árboles ---------- */
  const leafM=["#4f8a3c","#5c9a43","#3f7a35","#6aa84c"].map(c=>M(c));
  const barkM=M("#6b4a2f");
  const trees=[];
  function tree(x,z,s,kind){
   const g=new THREE.Group();g.position.set(x,0,z);g.scale.setScalar(s);
   const trunk=mk(new THREE.CylinderGeometry(.16,.27,2.8,8),barkM,false);trunk.position.y=1.4;g.add(trunk);
   const can=new THREE.Group();can.position.y=3.1;g.add(can);
   if(kind==="pine"){
    for(let i=0;i<4;i++){const c=mk(new THREE.ConeGeometry(1.55-i*.3,1.5,8),leafM[i%3],false);c.position.y=i*.85-.6;can.add(c)}
   }else{
    for(let i=0;i<14;i++){
     const r=.6+Math.random()*.7,b=mk(new THREE.IcosahedronGeometry(r,1),leafM[i%4],false),a=Math.random()*6.28,dd=Math.random()*1.7;
     b.position.set(Math.cos(a)*dd,Math.random()*1.4,Math.sin(a)*dd);b.rotation.set(Math.random()*3,Math.random()*3,0);can.add(b);
    }
   }
   g.userData={can:can,ph:Math.random()*6};trees.push(g);scene.add(g);return g;
  }
  tree(-4.8,2.8,1.55);               /* árbol grande fuera de cuadro: tira sombra moteada sobre el personaje */
  tree(-4.2,-5.5,1.25);tree(5.8,-7.5,1.5);tree(-9.5,-11,1.4);tree(9.5,-15,1.3);
  tree(-15,-8,1.2,"pine");tree(14,-6,1.3,"pine");tree(-6,-22,1.5,"pine");tree(2,-28,1.6,"pine");tree(17,-24,1.5,"pine");tree(-18,-20,1.6,"pine");

  /* ---------- mobiliario del parque ---------- */
  (function(){
   const wood=M("#a8743f"),metal=M("#2c3038",{map:null,metalness:.6,roughness:.5});
   const g=new THREE.Group();
   for(let i=0;i<3;i++){const p=mk(new THREE.BoxGeometry(1.5,.05,.14),wood,false);p.position.set(0,.5,-.18+i*.18);g.add(p)}
   for(let i=0;i<2;i++){const p=mk(new THREE.BoxGeometry(1.5,.05,.12),wood,false);p.position.set(0,.76+i*.17,-.36);p.rotation.x=-.15;g.add(p)}
   [-.65,.65].forEach(s=>{const l=mk(new THREE.BoxGeometry(.06,.5,.55),metal,false);l.position.set(s,.25,-.1);g.add(l);const b=mk(new THREE.BoxGeometry(.06,.5,.05),metal,false);b.position.set(s,.7,-.38);g.add(b)});
   g.position.set(-3.6,0,-4.2);g.rotation.y=.35;scene.add(g);
   /* bote de basura */
   const bin=mk(new THREE.CylinderGeometry(.2,.17,.55,10),M("#3f6b52"),false);bin.position.set(-2.5,.28,-4.6);scene.add(bin);
   const lid=mk(new THREE.CylinderGeometry(.22,.22,.05,10),M("#2e4f3c"),false);lid.position.set(-2.5,.57,-4.6);scene.add(lid);
  })();
  const lamps=[];
  function lamp(x,z){
   const dark=M("#2b2f3a",{map:null,metalness:.5,roughness:.5}),g=new THREE.Group();g.position.set(x,0,z);
   const pole=mk(new THREE.CylinderGeometry(.05,.075,3.4,8),dark,false);pole.position.y=1.7;g.add(pole);
   const cap=mk(new THREE.BoxGeometry(.34,.06,.34),dark,false);cap.position.y=3.5;g.add(cap);
   const glass=new THREE.Mesh(new THREE.SphereGeometry(.17,10,8),new THREE.MeshStandardMaterial({color:col("#fff2c8"),emissive:col("#ffd98a"),emissiveIntensity:.2}));glass.position.y=3.3;g.add(glass);
   const light=new THREE.PointLight(col("#ffd9a0"),0,9,2);light.position.y=3.2;g.add(light);
   lamps.push({glass:glass,light:light});scene.add(g);
  }
  lamp(2.3,-6.8);lamp(-7.5,-3);lamp(6.5,-1);
  /* arbustos */
  [[-6.8,-2.5,1],[-7.4,-3.4,.8],[6.8,-2.2,1.1],[7.6,-3,.8],[-1.5,-9,1],[1.2,-9.5,1.2],[8.5,-9,1.3],[-10,-6,1.2]].forEach(b=>{
   const g=new THREE.Group();g.position.set(b[0],0,b[1]);g.scale.setScalar(b[2]);
   for(let i=0;i<4;i++){const m=mk(new THREE.IcosahedronGeometry(.5+Math.random()*.2,1),leafM[i%4],false);m.position.set(rnd(-.5,.5),.4+Math.random()*.2,rnd(-.4,.4));g.add(m)}
   scene.add(g);
  });
  /* columpios */
  const swings=[];
  (function(){
   const bar=M("#c4423a",{map:null,metalness:.3,roughness:.6}),seatM=M("#2f6cc8"),ropeM=M("#d9d2c2",{map:null});
   const g=new THREE.Group();g.position.set(8.4,0,-11);g.rotation.y=-.5;
   const top=mk(new THREE.CylinderGeometry(.06,.06,3.4,8),bar,false);top.rotation.z=Math.PI/2;top.position.y=2.4;g.add(top);
   [-1.6,1.6].forEach(sx=>[-1,1].forEach(sz=>{const l=mk(new THREE.CylinderGeometry(.05,.05,2.5,6),bar,false);l.position.set(sx,1.2,sz*.28);l.rotation.x=sz*-.22;g.add(l)}));
   [-.6,.6].forEach(px=>{
    const piv=new THREE.Group();piv.position.set(px,2.4,0);g.add(piv);
    [-.2,.2].forEach(rx=>{const r=mk(new THREE.CylinderGeometry(.012,.012,1.75,4),ropeM,false);r.position.set(rx,-.88,0);piv.add(r)});
    const s=mk(new THREE.BoxGeometry(.55,.05,.22),seatM,false);s.position.y=-1.75;piv.add(s);swings.push({p:piv,ph:px+Math.random()});
   });
   scene.add(g);
  })();
  /* estanque con patitos */
  const ducks=[];
  (function(){
   const pond=new THREE.Mesh(new THREE.CircleGeometry(1,40),new THREE.MeshStandardMaterial({color:col("#4e93b8"),roughness:.12,metalness:.15}));
   pond.rotation.x=-Math.PI/2;pond.scale.set(3.3,2.2,1);pond.position.set(-7.2,.03,-9.5);pond.receiveShadow=true;scene.add(pond);
   const stoneM=M("#9a9a92");
   for(let i=0;i<20;i++){const a=i/20*6.28,s=mk(new THREE.IcosahedronGeometry(rnd(.18,.3),0),stoneM,false);s.position.set(-7.2+Math.cos(a)*3.45,.1,-9.5+Math.sin(a)*2.35);s.rotation.set(rnd(0,3),rnd(0,3),0);scene.add(s)}
   for(let i=0;i<2;i++){
    const d=new THREE.Group(),y=M("#ffd23f"),o=M("#ff8f1f");
    const b=mk(new THREE.SphereGeometry(.17,8,6),y,false);b.scale.set(1,.8,1.3);d.add(b);
    const h=mk(new THREE.SphereGeometry(.1,8,6),y,false);h.position.set(0,.16,.16);d.add(h);
    const bk=mk(new THREE.BoxGeometry(.07,.03,.09),o,false);bk.position.set(0,.15,.27);d.add(bk);
    d.position.y=.08;scene.add(d);ducks.push({g:d,a:i*3.1,r:i?1.2:.8});
   }
  })();
  /* cerca de madera al fondo */
  (function(){
   const wood=M("#b08a58");
   const posts=new THREE.InstancedMesh(new THREE.BoxGeometry(.12,1,.12),wood,34),d=new THREE.Object3D();
   for(let i=0;i<34;i++){d.position.set(-26+i*1.6,.5,-32);d.updateMatrix();posts.setMatrixAt(i,d.matrix)}
   posts.castShadow=true;scene.add(posts);
   [.35,.8].forEach(y=>{const r=new THREE.Mesh(new THREE.BoxGeometry(53,.08,.05),wood);r.position.set(0,y,-31.94);scene.add(r)});
  })();
  /* nubes de cartón */
  const clouds=[],cloudM=new THREE.MeshBasicMaterial({color:0xffffff,fog:false,toneMapped:false});
  for(let i=0;i<6;i++){
   const g=new THREE.Group();
   for(let j=0;j<5;j++){const s=new THREE.Mesh(new THREE.SphereGeometry(rnd(3,5.5),10,8),cloudM);s.position.set(j*4.2-8,rnd(-1,1.5),rnd(-1,1));s.scale.y=.55;g.add(s)}
   g.position.set(rnd(-90,90),rnd(26,40),rnd(-110,-80));g.scale.setScalar(rnd(.8,1.4));scene.add(g);clouds.push(g);
  }
  /* hojitas cayendo */
  const leaves=[],leafMat=["#d6a93a","#7fb04a","#c8662e","#5e9a3f"].map(c=>new THREE.MeshStandardMaterial({color:col(c),side:THREE.DoubleSide,roughness:.9}));
  for(let i=0;i<(MOBILE?14:26);i++){
   const m=new THREE.Mesh(new THREE.PlaneGeometry(.12,.08),leafMat[i%4]);
   m.userData={vx:rnd(.1,.35),vy:rnd(.18,.4),sp:rnd(1,3),ph:Math.random()*6};
   m.position.set(rnd(-6,6),rnd(0,6),rnd(-6,4));scene.add(m);leaves.push(m);
  }

  /* ---------- personaje ---------- */
  const GEST={
   rock:{c1:[1.45,1.5,1.5,1.5],c2:[1.5,1.55,1.55,1.5],sp:[0,0,0,0],th:[1.25,.95,.8]},
   paper:{c1:[.05,.03,.05,.08],c2:[.05,.03,.05,.08],sp:[.14,.05,-.05,-.16],th:[-.85,.15,.1]},
   scissors:{c1:[.03,.03,1.5,1.5],c2:[.03,.03,1.55,1.5],sp:[.2,-.12,0,0],th:[1.25,.95,.8]},
   none:{c1:[.9,.9,.9,.9],c2:[1,1,1,1],sp:[0,0,0,0],th:[1,.6,.5]}
  };
  const clonePose=g=>({c1:g.c1.slice(),c2:g.c2.slice(),sp:g.sp.slice(),th:g.th.slice()});
  function makeHand(skin){
   const h=new THREE.Group();
   const palm=mk(new THREE.BoxGeometry(.2,.22,.075),skin);palm.position.y=.11;h.add(palm);
   const fingers=[];
   [[-.075,.095,.08,.027],[-.025,.105,.086,.027],[.025,.095,.08,.026],[.072,.075,.062,.023]].forEach(f=>{
    const g1=new THREE.Group();g1.position.set(f[0],.22,0);h.add(g1);
    const p1=mk(new THREE.CylinderGeometry(f[3],f[3],f[1],8),skin,true,1.12);p1.position.y=f[1]/2;g1.add(p1);
    const g2=new THREE.Group();g2.position.y=f[1];g1.add(g2);
    const p2=mk(new THREE.CylinderGeometry(f[3]*.95,f[3]*.95,f[2],8),skin,true,1.12);p2.position.y=f[2]/2;g2.add(p2);
    const tip=mk(new THREE.SphereGeometry(f[3]*.95,8,6),skin,true,1.12);tip.position.y=f[2];g2.add(tip);
    fingers.push({g1:g1,g2:g2});
   });
   const t1=new THREE.Group();t1.position.set(.1,.05,.025);h.add(t1);
   const q1=mk(new THREE.CylinderGeometry(.03,.03,.085,8),skin,true,1.12);q1.position.y=.0425;t1.add(q1);
   const t2=new THREE.Group();t2.position.y=.085;t1.add(t2);
   const q2=mk(new THREE.CylinderGeometry(.028,.028,.07,8),skin,true,1.12);q2.position.y=.035;t2.add(q2);
   const qt=mk(new THREE.SphereGeometry(.028,8,6),skin,true,1.12);qt.position.y=.07;t2.add(qt);
   return {group:h,fingers:fingers,t1:t1,t2:t2};
  }
  function makeChar(o){
   const root=new THREE.Group(),
    skin=M(o.skin),shirt=M(o.shirt),pants=M(o.pants),hair=M(o.hair),shoe=M("#2e2926"),
    white=M("#ffffff"),dark=M("#1d1a1a",{map:null}),blush=M("#ff9aa2");
   [-1,1].forEach(s=>{
    const leg=mk(new THREE.CylinderGeometry(.095,.085,.85,10),pants);leg.position.set(s*.11,.5,0);root.add(leg);
    const sh=mk(new THREE.BoxGeometry(.17,.1,.28),shoe);sh.position.set(s*.11,.06,.04);root.add(sh);
   });
   const body=new THREE.Group();root.add(body);
   const hips=mk(new THREE.CylinderGeometry(.2,.2,.18,12),pants);hips.position.y=.95;body.add(hips);
   const torso=mk(new THREE.CylinderGeometry(.22,.19,.64,12),shirt);torso.position.y=1.17;body.add(torso);
   const neck=mk(new THREE.CylinderGeometry(.065,.07,.1,8),skin);neck.position.y=1.52;body.add(neck);
   const headG=new THREE.Group();headG.position.set(0,1.55,0);body.add(headG);
   const head=mk(new THREE.SphereGeometry(.22,18,14),skin);head.scale.set(1,1.06,1);head.position.y=.2;headG.add(head);
   const cap=mk(new THREE.SphereGeometry(.238,18,12,0,Math.PI*2,0,Math.PI*.52),hair,true,1.05);cap.position.set(0,.215,-.005);cap.rotation.x=-.3;headG.add(cap);
   const back=mk(new THREE.SphereGeometry(.2,12,10),hair,true,1.05);back.position.set(0,.19,-.06);headG.add(back);
   const eyes=[];
   [-1,1].forEach(s=>{
    const eg=new THREE.Group();eg.position.set(s*.085,.23,.178);headG.add(eg);
    const e=mk(new THREE.SphereGeometry(.05,10,8),white,false);e.scale.z=.6;eg.add(e);
    const p=mk(new THREE.SphereGeometry(.028,8,6),dark,false);p.position.z=.03;eg.add(p);eyes.push(eg);
    const br=mk(new THREE.BoxGeometry(.09,.02,.02),dark,false);br.position.set(s*.085,.31,.2);br.rotation.z=-s*.12;headG.add(br);
    const ear=mk(new THREE.SphereGeometry(.045,8,6),skin);ear.position.set(s*.215,.2,0);headG.add(ear);
    const ch=mk(new THREE.SphereGeometry(.04,8,6),blush,false);ch.scale.z=.3;ch.position.set(s*.14,.14,.175);headG.add(ch);
   });
   const nose=mk(new THREE.SphereGeometry(.035,8,6),skin,false);nose.position.set(0,.19,.215);headG.add(nose);
   const mouth=new THREE.Mesh(new THREE.TorusGeometry(.055,.012,6,14,Math.PI),dark);mouth.position.set(0,.115,.205);mouth.rotation.z=Math.PI;headG.add(mouth);
   /* ropa y accesorios personalizables */
   const ac=M(o.acc||"#ffcc33"),gold=M("#f5b301");
   if(o.style==="hoodie"){const hd=mk(new THREE.TorusGeometry(.13,.06,8,14),shirt);hd.position.set(0,1.52,-.02);hd.rotation.x=Math.PI/2;body.add(hd);const pk=mk(new THREE.BoxGeometry(.24,.1,.05),shirt);pk.position.set(0,1.0,.2);body.add(pk)}
   if(o.style==="dress"){const sk=mk(new THREE.CylinderGeometry(.2,.36,.5,14),shirt);sk.position.y=.7;root.add(sk)}
   if(o.style==="suit"){const ti=mk(new THREE.BoxGeometry(.07,.32,.03),ac,false);ti.position.set(0,1.25,.205);body.add(ti);[-1,1].forEach(s=>{const lp=mk(new THREE.BoxGeometry(.04,.18,.02),white,false);lp.position.set(s*.07,1.4,.205);lp.rotation.z=s*.45;body.add(lp)})}
   if(o.hat==="cap"){const c=mk(new THREE.SphereGeometry(.26,16,10,0,Math.PI*2,0,Math.PI*.5),ac,true,1.05);c.position.y=.225;headG.add(c);const v=mk(new THREE.BoxGeometry(.2,.025,.14),ac,true,1.1);v.position.set(0,.28,.27);v.rotation.x=.2;headG.add(v)}
   if(o.hat==="beanie"){const c=mk(new THREE.SphereGeometry(.26,16,10,0,Math.PI*2,0,Math.PI*.55),ac,true,1.05);c.position.y=.2;headG.add(c);const p=mk(new THREE.SphereGeometry(.06,8,6),ac,true,1.1);p.position.y=.47;headG.add(p)}
   if(o.hat==="tophat"){const b=mk(new THREE.CylinderGeometry(.27,.27,.03,16),ac,true,1.1);b.position.y=.42;headG.add(b);const c=mk(new THREE.CylinderGeometry(.15,.15,.3,16),ac,true,1.06);c.position.y=.57;headG.add(c)}
   if(o.hat==="crown"){const b=mk(new THREE.CylinderGeometry(.19,.19,.07,14),gold,true,1.08);b.position.y=.45;headG.add(b);for(let i=0;i<5;i++){const a=i/5*6.283,p=mk(new THREE.ConeGeometry(.04,.1,4),gold,true,1.1);p.position.set(Math.cos(a)*.17,.54,Math.sin(a)*.17);headG.add(p)}}
   if(o.hat==="bow"){[-1,1].forEach(s=>{const w=mk(new THREE.SphereGeometry(.06,8,6),ac,true,1.1);w.scale.set(1.5,1,.5);w.position.set(s*.075,.44,.1);headG.add(w)});const k=mk(new THREE.SphereGeometry(.035,8,6),ac,true,1.1);k.position.set(0,.44,.1);headG.add(k)}
   if(o.face==="glasses"||o.face==="sun"){const isSun=o.face==="sun",lm=isSun?dark:M("#2b2b33",{map:null});[-1,1].forEach(s=>{const g=isSun?mk(new THREE.BoxGeometry(.1,.07,.02),lm,false):new THREE.Mesh(new THREE.TorusGeometry(.055,.01,6,16),lm);g.position.set(s*.085,.23,.24);headG.add(g)});const br2=mk(new THREE.BoxGeometry(.05,.012,.012),lm,false);br2.position.set(0,.235,.24);headG.add(br2)}
   if(o.face==="mustache"){const mu=mk(new THREE.BoxGeometry(.13,.028,.03),hair,false);mu.position.set(0,.155,.225);headG.add(mu)}
   if(o.neck==="scarf"){const scf=mk(new THREE.TorusGeometry(.11,.05,8,16),ac,true,1.08);scf.position.y=1.53;scf.rotation.x=Math.PI/2;body.add(scf);const tl=mk(new THREE.BoxGeometry(.09,.26,.03),ac,true,1.1);tl.position.set(.1,1.38,.2);body.add(tl)}
   if(o.neck==="bowtie"){[-1,1].forEach(s=>{const c=mk(new THREE.ConeGeometry(.045,.08,4),ac,true,1.1);c.position.set(s*.05,1.47,.21);c.rotation.z=-s*Math.PI/2;body.add(c)});const k=mk(new THREE.SphereGeometry(.025,8,6),ac,true,1.1);k.position.set(0,1.47,.21);body.add(k)}
   /* brazo que juega (el derecho del personaje, a la izquierda en pantalla) */
   const armR=new THREE.Group();armR.position.set(-.3,1.42,0);body.add(armR);
   const ball=mk(new THREE.SphereGeometry(.08,10,8),shirt);armR.add(ball);
   const up=mk(new THREE.CylinderGeometry(.065,.06,.3,8),shirt);up.position.y=-.15;armR.add(up);
   const elbow=new THREE.Group();elbow.position.y=-.3;armR.add(elbow);
   const fore=mk(new THREE.CylinderGeometry(.055,.045,.28,8),skin);fore.position.y=-.14;elbow.add(fore);
   const hand=makeHand(o.glove?M(o.glove):skin);hand.group.position.y=-.28;hand.group.rotation.x=Math.PI;hand.group.scale.setScalar(.85);elbow.add(hand.group);
   /* brazo libre */
   const armL=new THREE.Group();armL.position.set(.3,1.42,0);body.add(armL);
   const ball2=mk(new THREE.SphereGeometry(.08,10,8),shirt);armL.add(ball2);
   const up2=mk(new THREE.CylinderGeometry(.065,.06,.3,8),shirt);up2.position.y=-.15;armL.add(up2);
   const elb2=new THREE.Group();elb2.position.y=-.3;armL.add(elb2);
   const fore2=mk(new THREE.CylinderGeometry(.055,.045,.26,8),skin);fore2.position.y=-.13;elb2.add(fore2);
   const fist2=mk(new THREE.SphereGeometry(.07,10,8),skin);fist2.position.y=-.29;elb2.add(fist2);

   const ch={
    root:root,seed:Math.random()*6,
    pose:clonePose(GEST.rock),target:GEST.rock,
    pumpT:99,pumpAmt:.3,revT:99,react:"none",reactT:99,m:0,blinkT:9,nextBlink:1+Math.random()*3,
    resetPose(){this.target=GEST.rock;this.react="none";this.reactT=99;this.pumpAmt=.3;this.pumpT=99},
    beat(){this.pumpT=0;this.pumpAmt=1},
    reveal(move,react){this.target=(move&&GEST[move])||GEST.none;this.revT=0;this.react=react||"draw";this.reactT=0;this.pumpT=99},
    update(dt,t){
     const k=1-Math.exp(-dt*16),P=this.pose,T=this.target;
     ["c1","c2","sp"].forEach(key=>{for(let i=0;i<4;i++)P[key][i]+=(T[key][i]-P[key][i])*k});
     for(let i=0;i<3;i++)P.th[i]+=(T.th[i]-P.th[i])*k;
     hand.fingers.forEach((f,i)=>{f.g1.rotation.x=P.c1[i];f.g1.rotation.z=P.sp[i];f.g2.rotation.x=P.c2[i]});
     hand.t1.rotation.set(P.th[1],0,P.th[0]);hand.t2.rotation.x=P.th[2];
     this.pumpT+=dt;this.revT+=dt;this.reactT+=dt;this.blinkT+=dt;
     const down=this.pumpT<.4?Math.sin(this.pumpT/.4*Math.PI):0;
     const idle=Math.sin(t*2.2+this.seed)*.04;
     const env=this.revT<.45?Math.sin(this.revT/.45*Math.PI):0;
     armR.rotation.x=-1.0+down*.55*this.pumpAmt+idle-env*.3;
     armR.rotation.z=-.35;
     elbow.rotation.x=-1.84;
     hand.group.scale.setScalar(.85*(1+env*.35));
     /* ánimo */
     const mt=this.react==="win"?1:this.react==="lose"?-1:this.react==="draw"?.25:0;
     this.m+=(mt-this.m)*Math.min(1,dt*8);
     mouth.rotation.z=this.m>=0?Math.PI:0;mouth.scale.y=.25+Math.abs(this.m)*.75;mouth.position.y=.115-(this.m<0?-.03:0);
     const celebrate=this.react==="win"&&this.reactT<2.6;
     root.position.y=celebrate?Math.abs(Math.sin(this.reactT*9))*.12:0;
     const laT=celebrate?-2.9:.06+Math.sin(t*1.6+this.seed)*.03;
     armL.rotation.x+=(laT-armL.rotation.x)*Math.min(1,dt*10);
     armL.rotation.z+=((celebrate?.3:.12)-armL.rotation.z)*Math.min(1,dt*10);
     elb2.rotation.x=celebrate?-.2:-.25;
     const nod=this.react==="lose"?.38:0;
     headG.rotation.x+=(nod-headG.rotation.x)*Math.min(1,dt*6);
     headG.rotation.y=Math.sin(t*.8+this.seed)*.12;
     body.position.y=Math.sin(t*2+this.seed)*.006;
     if(t>this.nextBlink){this.blinkT=0;this.nextBlink=t+2+Math.random()*3}
     const bl=this.blinkT<.15?1-Math.sin(this.blinkT/.15*Math.PI)*.92:1;
     eyes.forEach(e=>e.scale.y=bl);
    }
   };
   return ch;
  }
  const LOOKS=[
   {skin:"#f1c9a5",shirt:"#4f7bd9",pants:"#3b4a6b",hair:"#3b2a20"},
   {skin:"#d9a077",shirt:"#d9546f",pants:"#5a4a3a",hair:"#c98a3c"},
   {skin:"#a8714b",shirt:"#3fa57a",pants:"#444a55",hair:"#1f1a18"}
  ];
  const chars=LOOKS.map(l=>{const c=makeChar(l);scene.add(c.root);return c});

  /* ---------- cámara ---------- */
  const D=7.4,camera=new THREE.PerspectiveCamera(40,W/H,.1,300);
  let mode="home",count=1,homeT=0,gi=0;
  function layout(n){
   const sp=n===1?0:(n===2?1.35:1.3);
   chars.forEach((c,i)=>{c.root.visible=i<n;const x=(i-(n-1)/2)*sp;c.root.position.set(x,0,n===3&&i===1?-.15:0);c.root.rotation.y=-x*.07});
  }
  layout(1);
  function anchorRect(){
   let el=null;
   if(mode==="game")el=document.getElementById("gameAnchor");
   else if(mode==="look")el=document.getElementById("lookGap");
   else{const h=document.getElementById("home");if(h&&!h.classList.contains("hidden"))el=h.querySelector(".home-gap")}
   if(el){const r=el.getBoundingClientRect();if(r.height>40&&r.width>40)return r}
   return {left:0,top:70,width:W,height:Math.max(160,H*.3)};
  }
  function update(dt,t){
   const r=anchorRect(),aspect=Math.max(.2,r.width/r.height);
   const need=Math.max(2.35,count*1.3/aspect);
   let fov=2*Math.atan((H*need/r.height)/(2*D))*180/Math.PI;
   fov=Math.max(10,Math.min(85,fov));
   const cx=r.left+r.width/2,cy=r.top+r.height/2;
   camera.fov=fov;camera.aspect=W/H;
   camera.setViewOffset(W,H,W/2-cx,H/2-cy,W,H);
   camera.position.set(Math.sin(t*.25)*.3,1.55,D);camera.lookAt(0,.95,0);
   if(mode!=="game"){
    homeT+=dt;
    if(homeT>1.7){homeT=0;gi=(gi+1)%3;const mv=["rock","paper","scissors"][gi];chars.forEach(c=>{c.beat();c.reveal(mv,"draw")})}
   }
   chars.forEach(c=>{if(c.root.visible)c.update(dt,t)});
   trees.forEach(g=>{const u=g.userData;u.can.rotation.z=Math.sin(t*.7+u.ph)*.015;u.can.rotation.x=Math.cos(t*.6+u.ph)*.012});
   swings.forEach(s=>{s.p.rotation.x=Math.sin(t*1.3+s.ph)*.35});
   ducks.forEach(d=>{const a=t*.25+d.a;d.g.position.x=-7.2+Math.cos(a)*d.r*1.6;d.g.position.z=-9.5+Math.sin(a)*d.r;d.g.rotation.y=-a+Math.PI;d.g.position.y=.08+Math.sin(t*2+d.a)*.015});
   clouds.forEach(c=>{c.position.x+=dt*.8;if(c.position.x>110)c.position.x=-110});
   leaves.forEach(m=>{const u=m.userData;m.position.x+=u.vx*dt;m.position.y-=u.vy*dt;m.rotation.x+=u.sp*dt;m.rotation.y+=u.sp*.7*dt;m.position.z+=Math.sin(t+u.ph)*.2*dt;if(m.position.y<.05||m.position.x>7){m.position.set(rnd(-7,-1),rnd(4,6.5),rnd(-6,4))}});
  }
  let last=0;
  function loop(ts){
   requestAnimationFrame(loop);
   if(document.hidden||document.documentElement.classList.contains("gated"))return;
   const dt=Math.min(.05,(ts-last)/1000||.016);last=ts;
   try{update(dt,ts/1000);renderer.render(scene,camera)}catch(e){}
  }
  window.addEventListener("resize",()=>{W=window.innerWidth;H=window.innerHeight;renderer.setSize(W,H,false)});
  requestAnimationFrame(loop);

  let custom=null,cur0=null;
  function swap0(l){cur0=l;const old=chars[0];scene.remove(old.root);const c=makeChar(Object.assign({},LOOKS[0],l||{}));chars[0]=c;scene.add(c.root);layout(count)}
  const api={
   setLook(l){custom=Object.assign({},l);if(mode!=="game")swap0(custom)},
   screen(id){
    mode=id==="game"?"game":id==="look"?"look":"home";
    const want=mode==="game"?null:custom;
    if(cur0!==want)swap0(want);
    if(mode!=="game"){count=1;layout(1);chars.forEach(c=>c.resetPose());homeT=1.5}
    else chars.forEach(c=>c.resetPose());
   },
   setCount(n){count=Math.max(1,Math.min(3,n|0));layout(count)},
   reset(){chars.forEach(c=>c.resetPose())},
   beat(){chars.forEach(c=>c.beat())},
   reveal(list){list.forEach((o,i)=>{if(chars[i])chars[i].reveal(o.move,o.react)})},
   mood(l){
    l=Math.max(0,Math.min(1,l));const k=.22+.78*l;
    sun.intensity=.25+1.45*l;hemi.intensity=.22+.38*l;fill.intensity=.1+.15*l;
    dome.material.color.setScalar(k);scene.fog.color.copy(fogBase).multiplyScalar(k);cloudM.color.setScalar(.35+.65*l);
    renderer.toneMappingExposure=.85+.15*l;
    lamps.forEach(L=>{L.light.intensity=(1-l)*1.8;L.glass.material.emissiveIntensity=.2+(1-l)*1.3});
   }
  };
  Object.keys(api).forEach(k=>{const f=api[k];api[k]=function(){try{return f.apply(api,arguments)}catch(e){}}});
  return api;
 }catch(err){
  try{cv.remove()}catch(e){}
  document.documentElement.classList.remove("has3d");
  return null;
 }
})();

/* ICONOS */
const ICON_COLORS={lock:"#3978ff",gear:"#3978ff",book:"#8857f5",robot:"#3978ff",people:"#3978ff",globe:"#3978ff",check:"#25c58a",pencil:"#ffffff",share:"#3978ff",dots:"#3978ff",trash:"#e0475b",mic:"#3978ff"};
const ICONS={
rock:`<path d="M7 33 L13 17 L24 9 L36 13 L42 26 L38 38 L13 40 Z" fill="#9aa5b8" stroke="#9aa5b8" stroke-width="4" stroke-linejoin="round"/><path d="M24 9 L36 13 L42 26 L31 23 Z" fill="#c3cbda" stroke="#c3cbda" stroke-width="3" stroke-linejoin="round"/><path d="M7 33 L13 17 L21 24 L13 40 Z" fill="#7e8aa0" stroke="#7e8aa0" stroke-width="3" stroke-linejoin="round"/>`,
paper:`<path d="M12 5 H29 L39 15 V41 a2 2 0 0 1 -2 2 H12 a2 2 0 0 1 -2 -2 V7 a2 2 0 0 1 2 -2 Z" fill="#dce8ff"/><path d="M29 5 V13 a2 2 0 0 0 2 2 H39 Z" fill="#8fb0ff"/><path d="M16 25 H32 M16 31 H32 M16 37 H25" stroke="#3978ff" stroke-width="3" stroke-linecap="round" fill="none"/>`,
scissors:`<path fill-rule="evenodd" d="M6 38 a7 7 0 1 0 14 0 a7 7 0 1 0 -14 0 Z M10 38 a3 3 0 1 0 6 0 a3 3 0 1 0 -6 0 Z" fill="#ff5688"/><path fill-rule="evenodd" d="M28 38 a7 7 0 1 0 14 0 a7 7 0 1 0 -14 0 Z M32 38 a3 3 0 1 0 6 0 a3 3 0 1 0 -6 0 Z" fill="#ff5688"/><path d="M38 6 L17 31 M10 6 L31 31" stroke="#aeb8cc" stroke-width="5" stroke-linecap="round" fill="none"/><circle cx="24" cy="22.5" r="3" fill="#7b849b"/>`,
coin:`<circle cx="24" cy="24" r="20" fill="#f5a623"/><circle cx="24" cy="24" r="15.5" fill="#ffca45"/><rect x="21" y="14" width="6" height="20" rx="3" fill="#f5a623"/>`,
pencil:`<path d="M32 10 L38 16 L16 38 L10 32 Z" fill="__C__"/><path d="M10 32 L16 38 L6 42 Z" fill="#ffd9a3"/><path d="M32 10 L36.5 5.5 a2 2 0 0 1 2.8 0 L42.5 8.7 a2 2 0 0 1 0 2.8 L38 16 Z" fill="#ff5688"/>`,
share:`<path d="M24 27 V6 M15 14 L24 5 L33 14" stroke="__C__" stroke-width="4.5" stroke-linecap="round" stroke-linejoin="round" fill="none"/><path d="M16 19 H12 a4 4 0 0 0 -4 4 V39 a4 4 0 0 0 4 4 H36 a4 4 0 0 0 4 -4 V23 a4 4 0 0 0 -4 -4 H32" stroke="__C__" stroke-width="4.5" stroke-linecap="round" stroke-linejoin="round" fill="none"/>`,
dots:`<circle cx="24" cy="9" r="4.5" fill="__C__"/><circle cx="24" cy="24" r="4.5" fill="__C__"/><circle cx="24" cy="39" r="4.5" fill="__C__"/>`,
lock:`<path d="M15 21 V15 a9 9 0 0 1 18 0 V21" stroke="__C__" stroke-width="5" fill="none" stroke-linecap="round"/><rect x="9" y="20" width="30" height="23" rx="6" fill="__C__"/><circle cx="24" cy="30" r="3.5" fill="#fff"/><rect x="22.5" y="31" width="3" height="7" rx="1.5" fill="#fff"/>`,
crown:`<path d="M5 37 L8 14 L18 24 L24 9 L30 24 L40 14 L43 37 Z" fill="#f5b301" stroke="#f5b301" stroke-width="3" stroke-linejoin="round"/><rect x="5" y="37" width="38" height="6" rx="2.5" fill="#e09a00"/><circle cx="24" cy="29" r="3" fill="#fff"/>`,
book:`<rect x="9" y="4" width="31" height="40" rx="4.5" fill="__C__"/><rect x="9" y="4" width="8" height="40" rx="4" fill="#000" opacity=".18"/><rect x="22" y="13" width="13" height="3.5" rx="1.75" fill="#fff"/><rect x="22" y="21" width="9" height="3.5" rx="1.75" fill="#fff"/>`,
gear:`<g fill="__C__"><rect x="20.5" y="3" width="7" height="12" rx="2.5"/><rect x="20.5" y="3" width="7" height="12" rx="2.5" transform="rotate(45 24 24)"/><rect x="20.5" y="3" width="7" height="12" rx="2.5" transform="rotate(90 24 24)"/><rect x="20.5" y="3" width="7" height="12" rx="2.5" transform="rotate(135 24 24)"/><rect x="20.5" y="3" width="7" height="12" rx="2.5" transform="rotate(180 24 24)"/><rect x="20.5" y="3" width="7" height="12" rx="2.5" transform="rotate(225 24 24)"/><rect x="20.5" y="3" width="7" height="12" rx="2.5" transform="rotate(270 24 24)"/><rect x="20.5" y="3" width="7" height="12" rx="2.5" transform="rotate(315 24 24)"/><circle cx="24" cy="24" r="14"/></g><circle cx="24" cy="24" r="5.5" fill="#fff"/>`,
robot:`<rect x="22.75" y="7" width="2.5" height="8" fill="__C__"/><circle cx="24" cy="6" r="3.5" fill="#ff5688"/><rect x="9" y="14" width="30" height="26" rx="8" fill="__C__"/><rect x="3" y="22" width="5" height="10" rx="2.5" fill="__C__"/><rect x="40" y="22" width="5" height="10" rx="2.5" fill="__C__"/><circle cx="17" cy="26" r="3.5" fill="#fff"/><circle cx="31" cy="26" r="3.5" fill="#fff"/><rect x="18" y="33" width="12" height="3" rx="1.5" fill="#fff"/>`,
people:`<circle cx="34" cy="19" r="6" fill="#25c58a"/><path d="M25 43 C25 33 29 29 34 29 C39 29 43 33 43 43 Z" fill="#25c58a"/><circle cx="17" cy="15" r="8" fill="__C__"/><path d="M3 43 C3 31 9 25 17 25 C25 25 31 31 31 43 Z" fill="__C__"/>`,
globe:`<circle cx="24" cy="24" r="20" fill="__C__"/><g fill="none" stroke="#fff" stroke-width="2.5" stroke-linecap="round"><ellipse cx="24" cy="24" rx="8" ry="20"/><path d="M4 24 H44 M8 14 H40 M8 34 H40"/></g>`,
trash:`<path d="M8 12 H40" stroke="__C__" stroke-width="4.5" stroke-linecap="round"/><path d="M18 12 V8 a2 2 0 0 1 2 -2 H28 a2 2 0 0 1 2 2 V12" stroke="__C__" stroke-width="4" fill="none"/><path d="M11 16 H37 L35 41 a3 3 0 0 1 -3 3 H16 a3 3 0 0 1 -3 -3 Z" fill="__C__"/><path d="M20 22 V37 M28 22 V37" stroke="#fff" stroke-width="3.5" stroke-linecap="round"/>`,
mic:`<rect x="16" y="4" width="16" height="25" rx="8" fill="__C__"/><path d="M9 22 a15 15 0 0 0 30 0 M24 37 V44 M17 44 H31" stroke="__C__" stroke-width="4" stroke-linecap="round" fill="none"/>`,
check:`<path d="M10 25 L20 35 L38 13" stroke="__C__" stroke-width="6" stroke-linecap="round" stroke-linejoin="round" fill="none"/>`,
unknown:`<circle cx="24" cy="24" r="18" fill="#e8ecf5"/>`
};
function ico(name,color){
 const body=ICONS[name]||ICONS.unknown;
 const c=color||ICON_COLORS[name]||"#3978ff";
 return `<svg class="ico" viewBox="0 0 48 48" aria-hidden="true" focusable="false">${body.split("__C__").join(c)}</svg>`;
}
function hydrateIcons(){document.querySelectorAll("[data-i]").forEach(el=>{el.innerHTML=ico(el.getAttribute("data-i"),el.getAttribute("data-c")||undefined)})}

const VIP_PRICE=2500;
const tools=["rock","paper","scissors"];
const toolNames={rock:"Piedra",paper:"Papel",scissors:"Tijera"};
const englishNames={rock:"Rock",paper:"Paper",scissors:"Scissors"};
const rules={rock:["scissors"],paper:["rock"],scissors:["paper"]};
/* colores pastel del título */
const WORD_COL={rock:["#9bbcff","#5f86e8"],paper:["#ff9db1","#e8678a"],scissors:["#8ee3c0","#3fbf93"]};

let lang="es";
let playerName="Jugador",bots=[];
let playerScore=0,botScore=0,round=1,finished=false;
let countdownTimer=null,countdownToken=0,choiceWindowOpen=false;
let chosenThisRound=false,phaseIndex=0,savedMove=null,savedBotResults=null;
let coins=Math.max(0,Number(storeGet("rpsCoins")||0))||0;
let developerMode=storeGet("rpsDeveloperMode")==="true";
let hasVIP=storeGet("rpsVIP")==="true";

function t(es,en){return lang==="es"?es:en}
function label(id){return (lang==="es"?toolNames:englishNames)[id]||id}
function icon(id){return ico(rules[id]?id:"unknown")}
function wordHtml(id){const c=WORD_COL[id]||["#9bbcff","#5f86e8"];return `<span class="pword" style="--c:${c[0]};--o:${c[1]}">${label(id)}</span>`}
function escapeHtml(s){return String(s).replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]))}
function nameWithVip(n){return escapeHtml(n)+(hasVIP?" "+ico("crown"):"")}
function displayCoins(){return developerMode?"∞":coins.toLocaleString()}
function beatsMove(a,b){return a!==b&&(rules[a]||[]).includes(b)}
function randomFrom(a){return a[Math.floor(Math.random()*a.length)]}
function validMove(x){return (x&&tools.includes(x))?x:null}
function saveEconomy(){storeSet("rpsCoins",String(coins));storeSet("rpsVIP",String(hasVIP));updateCoins()}

/* TEMA */
const PRESETS=[
 ["Claro","Light","#ffffff","#202944"],["Oscuro","Dark","#141a2e","#f1f4ff"],
 ["Rosa","Pink","#ffe3ec","#4a1f33"],["Menta","Mint","#dcf7ec","#14423a"],
 ["Cielo","Sky","#dcebff","#1b2c5a"],["Lavanda","Lavender","#ebe3ff","#3a2470"],
 ["Amarillo","Yellow","#fff3c9","#4a3a00"],["Negro","Black","#000000","#ffffff"]
];
const HEX_RE=/^#[0-9a-fA-F]{6}$/;
let theme={bg:"#ffffff",ink:"#202944"};
const THEME_PRICE=70;
let ownedThemes=[0],ownedCustom=false;
try{const a=JSON.parse(storeGet("rpsThemes")||"[0]");if(Array.isArray(a))ownedThemes=[0].concat(a.filter(n=>Number.isInteger(n)&&n>0&&n<8))}catch(e){}
ownedCustom=storeGet("rpsCustomBg")==="true";
function saveThemes(){storeSet("rpsThemes",JSON.stringify(ownedThemes));storeSet("rpsCustomBg",String(ownedCustom));saveEconomy()}
function spend(n){if(developerMode)return true;if(coins<n){alert(t("¡No tienes suficientes monedas! Ganas 2 monedas por cada ronda que ganes.","Not enough coins! You earn 2 coins for every round you win."));return false}coins-=n;return true}
function loadTheme(){
 const b=storeGet("rpsBg"),i=storeGet("rpsInk");
 if(b&&HEX_RE.test(b))theme.bg=b;
 if(i&&HEX_RE.test(i))theme.ink=i;
 paintTheme();
}
function paintTheme(){
 const r=document.documentElement.style;
 r.setProperty("--bg",theme.bg);r.setProperty("--ink",theme.ink);
 const m=document.getElementById("themeMeta");if(m)m.setAttribute("content",theme.bg);
 /* tema oscuro = parque de noche (farolas encendidas) */
 if(Stage&&HEX_RE.test(theme.bg)){
  const n=parseInt(theme.bg.slice(1),16),lum=(0.299*(n>>16&255)+0.587*(n>>8&255)+0.114*(n&255))/255;
  Stage.mood(Math.min(1,lum*1.25));
 }
}
function setTheme(bg,ink){
 theme.bg=bg;theme.ink=ink;storeSet("rpsBg",bg);storeSet("rpsInk",ink);
 paintTheme();renderSettings();
}
function applyPreset(i){
 const p=PRESETS[i];
 if(!ownedThemes.includes(i)){
  if(!confirm(t("¿Comprar el tema "+p[0]+" por "+THEME_PRICE+" monedas?","Buy the "+p[1]+" theme for "+THEME_PRICE+" coins?")))return;
  if(!spend(THEME_PRICE))return;
  ownedThemes.push(i);saveThemes();
 }
 setTheme(p[2],p[3]);
}
function buyCustom(){
 if(ownedCustom)return;
 if(!confirm(t("¿Desbloquear el fondo personalizado por "+THEME_PRICE+" monedas?","Unlock the custom background for "+THEME_PRICE+" coins?")))return;
 if(!spend(THEME_PRICE))return;
 ownedCustom=true;saveThemes();renderSettings();
}
function customColors(){
 const bg=ownedCustom?document.getElementById("bgColor").value:theme.bg;
 setTheme(bg,document.getElementById("inkColor").value);
}
function renderSettings(){
 document.getElementById("setTitle").textContent=t("Configuraciones","Settings");
 document.getElementById("setThemeLbl").textContent=t("Tema","Theme");
 document.getElementById("setBgLbl").textContent=t("Color de fondo (cualquier color)","Background color (any color)");
 document.getElementById("setPriceNote").textContent=t("Los temas cuestan "+THEME_PRICE+" monedas cada uno. Ganas 2 monedas por ronda ganada.","Themes cost "+THEME_PRICE+" coins each. You earn 2 coins per round won.");
 document.getElementById("bgColor").classList.toggle("hidden",!ownedCustom&&!developerMode);
 const uc=document.getElementById("unlockCustom");uc.classList.toggle("hidden",ownedCustom||developerMode);
 uc.innerHTML=ico("coin")+t("Desbloquear fondo personalizado · ","Unlock custom background · ")+THEME_PRICE;
 document.getElementById("setInkLbl").textContent=t("Color de las letras (cualquier color)","Text color (any color)");
 document.getElementById("setReset").textContent=t("Volver al tema claro (gratis)","Back to light theme (free)");
 document.getElementById("setBack").textContent=t("Volver al menú","Back to menu");
 document.getElementById("setPreview").textContent=t("Así se verán tus letras","This is how your text will look");
 document.getElementById("bgColor").value=theme.bg;
 document.getElementById("inkColor").value=theme.ink;
 const g=document.getElementById("themeGrid");g.innerHTML="";
 PRESETS.forEach((p,i)=>{
  const b=document.createElement("button");
  b.className="swatch"+((theme.bg.toLowerCase()===p[2]&&theme.ink.toLowerCase()===p[3])?" on":"");
  const own=ownedThemes.includes(i)||developerMode;
  b.style.background=p[2];b.style.color=p[3];
  b.innerHTML=t(p[0],p[1])+(own?"":`<span class="p">${ico("coin")}${THEME_PRICE}</span>`);
  if(!own)b.classList.add("lockd");
  b.onclick=()=>applyPreset(i);g.appendChild(b);
 });
}
function openSettings(){renderSettings();showScreen("settings")}

/* PERSONAJE */
const SKINS=["#fbe1cc","#f1c9a5","#d9a077","#a8714b","#7a4a2e","#4b2e1f","#ffd1e0","#bfe3ff","#b5e8a8"];
const COLS=["#4f7bd9","#d9546f","#3fa57a","#f2b134","#8857f5","#ff8fc0","#2c3038","#f4f4f4","#ff7a3d","#25b8c9"];
const HAIRS=["#3b2a20","#1f1a18","#c98a3c","#e8c872","#a33a2a","#8857f5","#ff8fc0","#e8e8e8"];
const PANTSC=["#3b4a6b","#5a4a3a","#444a55","#1f2433","#7a6a4f","#2f5d8a","#6b3a5a"];
const STYLES=[["tee","Camiseta","T-shirt"],["hoodie","Sudadera","Hoodie"],["dress","Vestido","Dress"],["suit","Traje","Suit"]];
const HATS=[["none","Ninguno","None"],["cap","Gorra","Cap"],["beanie","Gorro","Beanie"],["tophat","Sombrero","Top hat"],["crown","Corona","Crown"],["bow","Moño","Bow"]];
const FACES=[["none","Ninguno","None"],["glasses","Lentes","Glasses"],["sun","Gafas de sol","Sunglasses"],["mustache","Bigote","Mustache"]];
const NECKS=[["none","Ninguno","None"],["scarf","Bufanda","Scarf"],["bowtie","Corbatín","Bow tie"]];
const LOOK_DEF={skin:"#f1c9a5",shirt:"#4f7bd9",pants:"#3b4a6b",hair:"#3b2a20",acc:"#ffcc33",glove:"",style:"tee",hat:"none",face:"none",neck:"none"};
const LOOK_SECTIONS=[
 ["skin","Piel","Skin","c",SKINS],["hair","Cabello","Hair","c",HAIRS],
 ["style","Ropa","Clothes","o",STYLES],["shirt","Color de ropa","Clothes color","c",COLS],["pants","Pantalón","Pants","c",PANTSC],
 ["hat","Cabeza","Head","o",HATS],["face","Cara","Face","o",FACES],["neck","Cuello","Neck","o",NECKS],
 ["acc","Color de accesorios","Accessory color","c",COLS],["glove","Guante","Glove","c",[""].concat(COLS)]
];
let look=Object.assign({},LOOK_DEF);
function loadLook(){
 try{
  const o=JSON.parse(storeGet("rpsLook")||"{}");
  ["skin","shirt","pants","hair","acc"].forEach(k=>{if(HEX_RE.test(o[k]))look[k]=o[k]});
  if(o.glove===""||HEX_RE.test(o.glove))look.glove=o.glove||"";
  [["style",STYLES],["hat",HATS],["face",FACES],["neck",NECKS]].forEach(p=>{if(p[1].some(x=>x[0]===o[p[0]]))look[p[0]]=o[p[0]]});
 }catch(e){}
}
function applyLook(){storeSet("rpsLook",JSON.stringify(look));if(Stage)Stage.setLook(look);renderLook()}
function renderLook(){
 document.getElementById("lookTitle").innerHTML=ico("people")+t("Personaje","Character");
 document.getElementById("lookRandom").textContent=t("Aleatorio","Random");
 document.getElementById("lookReset").textContent=t("Reiniciar","Reset");
 document.getElementById("lookDone").textContent=t("Listo","Done");
 const body=document.getElementById("lookBody"),sy=body.scrollTop;
 body.innerHTML=LOOK_SECTIONS.map(s=>`<div class="field"><label>${t(s[1],s[2])}</label><div class="chips">`+s[4].map(v=>{
  const val=s[3]==="o"?v[0]:v,on=look[s[0]]===val;
  if(s[3]==="o")return `<button class="opt${on?" on":""}" data-k="${s[0]}" data-v="${val}">${t(v[1],v[2])}</button>`;
  return `<button class="chip${on?" on":""}" aria-label="${val||"none"}" data-k="${s[0]}" data-v="${val}" style="background:${val||"var(--bg)"}">${val?"":"✕"}</button>`;
 }).join("")+`</div></div>`).join("");
 body.scrollTop=sy;
}
function randomLook(){
 LOOK_SECTIONS.forEach(s=>{const v=randomFrom(s[4]);look[s[0]]=s[3]==="o"?v[0]:v});
 if(Math.random()<.6)look.glove="";
 applyLook();
}
function resetLook(){look=Object.assign({},LOOK_DEF);applyLook()}
function openLook(){renderLook();showScreen("look")}
document.getElementById("lookBody").addEventListener("click",e=>{
 const b=e.target.closest("[data-k]");if(!b)return;
 look[b.dataset.k]=b.dataset.v;applyLook();
});

/* BORRAR DATOS */
function openDelete(){
 document.getElementById("delTitle").textContent=t("¿Borrar todos los datos?","Delete all data?");
 document.getElementById("delText").textContent=t("¡Advertencia! Se borrarán tus monedas, el VIP, tu perfil, el tema y todos tus ajustes de este dispositivo. Esta acción no se puede deshacer.","Warning! Your coins, VIP, profile, theme and all settings on this device will be erased. This cannot be undone.");
 document.getElementById("delCancel").textContent=t("Cancelar","Cancel");
 document.getElementById("delConfirm").textContent=t("Sí, borrar todo","Yes, delete all");
 document.getElementById("deleteModal").classList.remove("hidden");
}
function closeDelete(){document.getElementById("deleteModal").classList.add("hidden")}
function confirmDelete(){
 try{Object.keys(localStorage).filter(k=>k.indexOf("rps")===0).forEach(k=>localStorage.removeItem(k))}catch(e){}
 memStore={};try{window.name=""}catch(e){}
 location.reload();
}

/* PERFIL */
let profile={name:"Jugador",photo:"",color:""};
let pendingPhoto="";
const PHOTO_RE=/^data:image\/(jpeg|png|webp);base64,[A-Za-z0-9+\/=]+$/;
const COLOR_RE=/^hsl\(\d{1,3},\d{1,3}%,\d{1,3}%\)$/;
function randomPastel(){return "hsl("+Math.floor(Math.random()*360)+",72%,82%)"}
function loadProfile(){
 const n=String(storeGet("rpsProfileName")||"").trim().slice(0,14);
 profile.name=n||"Jugador";
 const ph=storeGet("rpsProfilePhoto");
 profile.photo=(ph&&PHOTO_RE.test(ph))?ph:"";
 let col=storeGet("rpsProfileColor");
 if(!col||!COLOR_RE.test(col)){col=randomPastel();storeSet("rpsProfileColor",col)}
 profile.color=col;
}
function saveProfile(){storeSet("rpsProfileName",profile.name);storeSet("rpsProfilePhoto",profile.photo||"");storeSet("rpsProfileColor",profile.color);renderProfile()}
function paintAvatar(el,photo){if(!el)return;el.style.backgroundColor=profile.color;el.style.backgroundImage=photo?'url("'+photo+'")':"none"}
function renderProfile(){
 document.getElementById("profileName").textContent=profile.name;
 paintAvatar(document.getElementById("profileAvatar"),profile.photo);
 playerName=profile.name;
}
function refreshEditorAvatar(){
 paintAvatar(document.getElementById("profileAvatarBig"),pendingPhoto);
 document.getElementById("photoRemoveBtn").classList.toggle("hidden",!pendingPhoto);
}
function openProfileEditor(){
 pendingPhoto=profile.photo;
 document.getElementById("profileModalTitle").innerHTML=ico("pencil","#3978ff")+t("Editar perfil","Edit profile");
 document.getElementById("photoPickBtn").textContent=t("Elegir foto","Choose photo");
 document.getElementById("photoRemoveBtn").textContent=t("Quitar foto","Remove photo");
 document.getElementById("profileNameLabel").textContent=t("Nombre","Name");
 document.getElementById("profileCancelBtn").textContent=t("Cancelar","Cancel");
 document.getElementById("profileSaveBtn").textContent=t("Guardar","Save");
 document.getElementById("profileNameInput").value=profile.name;
 refreshEditorAvatar();
 document.getElementById("profileModal").classList.remove("hidden");
}
function closeProfileEditor(){document.getElementById("profileModal").classList.add("hidden")}
function removePendingPhoto(){pendingPhoto="";refreshEditorAvatar()}
function handlePhotoFile(input){
 const file=input.files&&input.files[0];
 input.value="";
 if(!file)return;
 if(!file.type||file.type.indexOf("image/")!==0){alert(t("Elige un archivo de imagen.","Choose an image file."));return}
 const reader=new FileReader();
 reader.onerror=()=>alert(t("No se pudo leer esa imagen.","Could not read that image."));
 reader.onload=()=>{
  const img=new Image();
  img.onerror=()=>alert(t("No se pudo leer esa imagen.","Could not read that image."));
  img.onload=()=>{
   const size=160,canvas=document.createElement("canvas");
   canvas.width=size;canvas.height=size;
   const ctx=canvas.getContext("2d"),s=Math.min(img.width,img.height);
   ctx.drawImage(img,(img.width-s)/2,(img.height-s)/2,s,s,0,0,size,size);
   pendingPhoto=canvas.toDataURL("image/jpeg",0.82);
   refreshEditorAvatar();
  };
  img.src=reader.result;
 };
 reader.readAsDataURL(file);
}
function saveProfileEditor(){
 const n=document.getElementById("profileNameInput").value.trim().slice(0,14);
 profile.name=n||"Jugador";
 profile.photo=pendingPhoto&&PHOTO_RE.test(pendingPhoto)?pendingPhoto:"";
 saveProfile();closeProfileEditor();
}

/* ONLINE */
const PEER_PREFIX="rps-stone-paper-";
const PROTO=4;
let onlineMode=false,peer=null,conn=null,onlineCode="",onlineRole="A",oppName="Oponente",blocked=false;
let localMove=null,myDone=false,rid=0,picks={},resolveTimer=null;

function updateCoins(){
 ["homeCoins","gameCoins","settingsCoins"].forEach(id=>{const el=document.getElementById(id);if(el)el.textContent=displayCoins()});
 document.querySelectorAll(".coinsLabel").forEach(el=>el.textContent=t("monedas","coins"));
 ["devBadgeHome","devBadgeGame"].forEach(id=>{const el=document.getElementById(id);if(el)el.classList.toggle("hidden",!developerMode)});
 ["vipBadgeHome","vipBadgeGame"].forEach(id=>{const el=document.getElementById(id);if(el)el.classList.toggle("hidden",!hasVIP)});
}
function showScreen(id){
 if(id!=="game")cancelCountdown();
 if(id!=="game"&&id!=="localSetup")closeOnline();
 document.querySelectorAll(".screen").forEach(s=>s.classList.add("hidden"));
 document.getElementById(id).classList.remove("hidden");
 document.getElementById("profileCard").classList.toggle("hidden",id!=="home");
 document.documentElement.classList.toggle("ingame",id==="game");
 if(Stage)Stage.screen(id);
 updateCoins();
}
function openVIP(){
 showScreen("vipScreen");
 const price=VIP_PRICE.toLocaleString();
 document.getElementById("vipPriceText").innerHTML=price+" "+ico("coin");
 const btn=document.getElementById("buyVipButton");
 btn.innerHTML=hasVIP?"VIP ACTIVADO":ico("crown")+t("Comprar VIP · ","Buy VIP · ")+price+" "+ico("coin");
 btn.disabled=hasVIP;
}
function buyVIP(){
 if(hasVIP)return;
 if(!developerMode&&coins<VIP_PRICE){alert(t("¡No tienes suficientes monedas!","Not enough coins!"));return}
 if(!developerMode)coins-=VIP_PRICE;
 hasVIP=true;saveEconomy();openVIP();
 alert(t("¡Ahora eres VIP!","You are now VIP!"));
}
function applyTexts(){
 document.getElementById("menuLook").innerHTML=ico("people")+t("Personaje","Character");
 document.getElementById("menuPlay").textContent=t("Jugar","Play");
 document.getElementById("menuDel").innerHTML=ico("trash")+t("Borrar datos","Delete data");
 document.getElementById("menuSet").textContent=t("Configuraciones","Settings");
 document.getElementById("rulesBtn").innerHTML=ico("book")+t("Ver reglas","View rules");
 document.getElementById("playTitle").textContent=t("Jugar","Play");
 document.getElementById("modeMultiTitle").textContent=t("Multijugador","Multiplayer");
 document.getElementById("modeBotsTitle").textContent=t("Jugar contra bots","Play vs bots");
 document.getElementById("playBackBtn").textContent=t("Volver al menú","Back to menu");
 document.getElementById("botsSetupTitle").textContent=t("Jugar contra bots","Play vs bots");
 document.getElementById("botCountLabel").textContent=t("Cantidad de bots","Number of bots");
 document.getElementById("botsBackBtn").textContent=t("Volver","Back");
 document.getElementById("botsStartBtn").textContent=t("Comenzar","Start");
 document.getElementById("newGameBtn").textContent=t("Nueva partida","New game");
 document.getElementById("menuLink").textContent=t("Menú principal","Main menu");
 document.getElementById("arenaTitle").textContent=onlineMode?"Multijugador online":t("Arena de batalla","Battle arena");
}
function toggleLanguage(){
 lang=lang==="es"?"en":"es";
 document.documentElement.lang=lang;
 document.getElementById("languageBtn").textContent=lang==="es"?"EN":"ES";
 applyTexts();renderChoices();updateCoins();renderSettings();updateVoiceBtn();
 if(!document.getElementById("look").classList.contains("hidden"))renderLook();
 if(!document.getElementById("vipScreen").classList.contains("hidden"))openVIP();
 if(!document.getElementById("rulesModal").classList.contains("hidden"))renderRulesPanel();
 if(!document.getElementById("deleteModal").classList.contains("hidden"))openDelete();
 if(!document.getElementById("game").classList.contains("hidden")&&(finished||(!choiceWindowOpen&&!countdownTimer)))document.getElementById("result").innerHTML=`<div class="rtitle draw">${t("Elige tu herramienta.","Choose your tool.")}</div>`;
 if(shouldGate())renderGate();
}

function leaveGame(){
 if(onlineMode&&!confirm(t("¿Salir de la partida online? Tu oponente será desconectado.","Leave the online match? Your opponent will be disconnected.")))return;
 showScreen("home");
}

/* CHAT DE VOZ (PeerJS call) */
let myVoice=false,oppVoice=false,voiceConnected=false,localStream=null,voiceCall=null;
function updateVoiceBtn(){
 const b=document.getElementById("voiceBtn");if(!b)return;
 b.classList.toggle("hidden",!onlineMode);
 b.classList.toggle("voice-on",myVoice);
 let txt;
 if(!myVoice)txt=oppVoice?t("Tu oponente activó la voz · toca para unirte","Your opponent turned voice on · tap to join"):t("Activar chat de voz","Turn on voice chat");
 else if(voiceConnected)txt=t("Voz conectada · toca para apagar","Voice connected · tap to turn off");
 else txt=t("Micrófono activo · esperando a tu oponente · toca para apagar","Mic on · waiting for opponent · tap to turn off");
 b.innerHTML=ico("mic")+txt;
}
function attachCall(call){
 if(voiceCall&&voiceCall!==call){try{voiceCall.close()}catch(e){}}
 voiceCall=call;
 call.on("stream",st=>{const a=document.getElementById("voiceAudio");a.srcObject=st;a.play().catch(()=>{});voiceConnected=true;updateVoiceBtn()});
 call.on("close",()=>{if(voiceCall===call){voiceCall=null;voiceConnected=false;updateVoiceBtn()}});
 call.on("error",()=>{});
}
function onIncomingCall(call){
 if(!conn||call.peer!==conn.peer||!myVoice||!localStream){try{call.close()}catch(e){}return}
 call.answer(localStream);attachCall(call);
}
function maybeStartCall(){
 /* solo el invitado (B) llama, y solo cuando los dos tienen la voz activa */
 if(onlineRole!=="B"||!myVoice||!oppVoice||!peer||!conn||!localStream||voiceConnected)return;
 attachCall(peer.call(conn.peer,localStream));
}
async function toggleVoice(){
 if(!onlineMode||!conn)return;
 if(myVoice){stopVoice(false);return}
 if(!navigator.mediaDevices||!navigator.mediaDevices.getUserMedia){alert(t("Tu navegador no permite usar el micrófono.","Your browser can't use the microphone."));return}
 try{localStream=await navigator.mediaDevices.getUserMedia({audio:{echoCancellation:true,noiseSuppression:true}})}
 catch(e){alert(t("No se pudo usar el micrófono. Permite el acceso al micrófono e inténtalo de nuevo.","Couldn't use the microphone. Allow microphone access and try again."));return}
 myVoice=true;sendToOpponent({type:"voice",on:true});
 updateVoiceBtn();maybeStartCall();
}
function stopVoice(silent){
 const had=myVoice;
 myVoice=false;oppVoice=false;voiceConnected=false;
 try{if(voiceCall)voiceCall.close()}catch(e){}
 voiceCall=null;
 if(localStream){localStream.getTracks().forEach(tr=>tr.stop());localStream=null}
 const a=document.getElementById("voiceAudio");if(a)a.srcObject=null;
 if(had&&!silent)sendToOpponent({type:"voice",on:false});
 updateVoiceBtn();
}

/* REGLAS */
function listIcons(arr){return arr.map(id=>icon(id)+" "+label(id)).join(", ")||"—"}
function renderRulesPanel(){
 document.getElementById("rulesTitle").innerHTML=ico("book")+t("Reglas","Rules");
 document.getElementById("rulesCloseBtn").textContent=t("Cerrar","Close");
 const list=document.getElementById("rulesList");list.innerHTML="";
 tools.forEach(id=>{
  const loses=tools.filter(x=>beatsMove(x,id));
  const row=document.createElement("div");row.className="rule-row";
  row.innerHTML=`<div class="rule-main">${icon(id)} ${wordHtml(id)}</div><div><span class="win">${t("Gana a","Beats")}</span> ${listIcons(rules[id])}</div><div><span class="lose">${t("Pierde contra","Loses to")}</span> ${listIcons(loses)}</div>`;
  list.appendChild(row);
 });
}
function openRules(){renderRulesPanel();document.getElementById("rulesModal").classList.remove("hidden")}
function closeRules(){document.getElementById("rulesModal").classList.add("hidden")}

/* BOTS: solo piedra, papel o tijera */
function openBotsSetup(){applyTexts();showScreen("setup")}
function generateBots(n){return Array.from({length:n},(_,i)=>({name:"Bot "+(i+1),tools:tools.slice()}))}

/* PANTALLA DE PARTIDA */
function renderChoices(){
 const c=document.getElementById("choices");c.innerHTML="";
 tools.forEach(id=>{
  const b=document.createElement("button");b.className="choice";b.disabled=true;b.onclick=()=>playRound(id);
  b.innerHTML=icon(id)+wordHtml(id);
  c.appendChild(b);
 });
}
function setChoicesEnabled(e){document.querySelectorAll(".choice").forEach(b=>b.disabled=!e)}
function cancelCountdown(){
 if(countdownTimer)clearTimeout(countdownTimer);
 countdownTimer=null;countdownToken++;choiceWindowOpen=false;
 chosenThisRound=false;savedMove=null;savedBotResults=null;setChoicesEnabled(false);
}
function pcard(name,move,state){
 return `<div class="pcard ${state}"><div class="pname">${name}</div>${move?icon(move):`<div class="nothing">—</div>`}<div class="pmove">${move?wordHtml(move):`<span class="nothing">${t("Nada","Nothing")}</span>`}</div></div>`;
}
function duelHtml(mine,opps,myState){
 const cards=pcard(nameWithVip(playerName),mine,myState)+opps.map(o=>{
  let s="draw";
  if(mine&&o.move){s=beatsMove(o.move,mine)?"win":beatsMove(mine,o.move)?"lose":"draw"}
  else if(mine&&!o.move)s="lose";else if(!mine&&o.move)s="win";
  return pcard(escapeHtml(o.name),o.move,s);
 }).join("");
 return `<div class="duel">${cards}</div>`;
}
function startGame(){
 closeOnline();
 playerName=profile.name;
 const count=Number(document.getElementById("botCount").value)||1;
 bots=generateBots(count);
 playerScore=0;botScore=0;round=1;finished=false;
 applyTexts();
 document.getElementById("playerScore").textContent="0";
 document.getElementById("botScore").textContent="0";
 document.getElementById("playerScoreName").innerHTML=nameWithVip(playerName);
 document.getElementById("botScoreName").textContent=bots.map(b=>b.name).join(", ");
 document.getElementById("roundCount").textContent=t("RONDA ","ROUND ")+round;
 document.getElementById("newGameBtn").classList.remove("hidden");
 document.getElementById("newGameBtn").onclick=()=>startGame();
 if(Stage)Stage.setCount(count);
 renderChoices();showScreen("game");countdown();
}
function countdown(){
 cancelCountdown();const token=countdownToken;let index=0;
 phaseIndex=0;chosenThisRound=false;savedMove=null;savedBotResults=null;
 choiceWindowOpen=true;localMove=null;myDone=false;setChoicesEnabled(false);
 if(Stage)Stage.reset();
 const sub=document.getElementById("arenaSubtitle"),res=document.getElementById("result");
 function next(){
  if(token!==countdownToken||!choiceWindowOpen)return;
  phaseIndex=index;
  if(Stage)Stage.beat();
  if(index<3){
   sub.textContent=t("El juego comienza en 1, 2, 3","The game starts in 1, 2, 3");
   res.innerHTML=`<div class="countdown-word">${index+1}</div>`;
  }else{
   const id=tools[index-3];
   sub.innerHTML=t("¡Elige ahora! ","Choose now! ")+wordHtml(id);
   res.innerHTML=`<div class="countdown-word">${wordHtml(id)}</div>`;
  }
  setChoicesEnabled(index>=3&&index<=5&&!chosenThisRound);
  index++;
  countdownTimer=setTimeout(index<6?next:finish,800);
 }
 function finish(){
  if(token!==countdownToken)return;
  countdownTimer=null;choiceWindowOpen=false;setChoicesEnabled(false);
  if(onlineMode){
   myDone=true;
   if(onlineRole==="B")sendToOpponent({type:"pick",rid:rid,move:localMove||null});
   sub.textContent=t("Esperando a tu oponente…","Waiting for your opponent…");
   res.innerHTML=(localMove?`<div class="rtitle draw">${t("Tu herramienta:","Your tool:")}</div><div>${icon(localMove)}</div><div class="pmove">${wordHtml(localMove)}</div>`:`<div class="rtitle none">${t("No elegiste nada.","You chose nothing.")}</div>`)+`<div>${t("Esperando a","Waiting for")} ${escapeHtml(oppName)}…</div>`;
   if(onlineRole==="A")hostTryResolve();
  }else if(chosenThisRound&&savedMove&&savedBotResults)resolveRound(savedMove,savedBotResults);
  else{
   sub.textContent=t("¡Se acabó el tiempo!","Time's up!");
   res.innerHTML=`<div class="rtitle none">${t("No elegiste nada.","You chose nothing.")}</div>`;
   const tk=countdownToken;
   countdownTimer=setTimeout(()=>{if(tk!==countdownToken||finished)return;countdown()},1800);
  }
 }
 next();
}
function playRound(move){
 if(!choiceWindowOpen||chosenThisRound||finished||phaseIndex<3||phaseIndex>5)return;
 chosenThisRound=true;savedMove=move;
 if(onlineMode){localMove=move;setChoicesEnabled(false);return}
 savedBotResults=bots.map(b=>({name:b.name,move:randomFrom(b.tools)}));
 setChoicesEnabled(false);
}
function titleHtml(out){
 const m={win:t("¡Ganaste esta ronda! +2 monedas","You won this round! +2 coins"),lose:t("¡Perdiste esta ronda!","You lost this round!"),draw:t("¡Empate!","Draw!"),none:t("Nadie eligió.","Nobody chose.")};
 return `<div class="rtitle ${out}">${m[out]}</div>`;
}
function resolveRound(move,botResults){
 let wins=0,losses=0;
 botResults.forEach(b=>{if(beatsMove(move,b.move))wins++;else if(beatsMove(b.move,move))losses++});
 const out=wins>losses?"win":losses>wins?"lose":"draw";
 if(out==="win"){playerScore++;if(!developerMode)coins+=2;saveEconomy()}
 if(out==="lose")botScore++;
 document.getElementById("playerScore").textContent=playerScore;
 document.getElementById("botScore").textContent=botScore;
 /* los personajes 3D muestran su gesto y reaccionan */
 if(Stage)Stage.reveal(botResults.map(b=>({move:b.move,react:beatsMove(b.move,move)?"win":beatsMove(move,b.move)?"lose":"draw"})));
 let html=titleHtml(out)+duelHtml(move,botResults,out);
 if(playerScore>=3||botScore>=3){
  finished=true;
  html+=`<div class="rfinal">${playerScore>botScore?t("¡Ganaste la partida!","You won the match!"):t("¡Perdiste la partida!","You lost the match!")}</div>`;
  document.getElementById("arenaSubtitle").textContent=t("Partida terminada","Match over");
  document.getElementById("result").innerHTML=html;
  return;
 }
 document.getElementById("result").innerHTML=html;
 document.getElementById("arenaSubtitle").textContent=t("¡Prepárate para la siguiente ronda!","Get ready for the next round!");
 const token=countdownToken;
 countdownTimer=setTimeout(()=>{
  if(token!==countdownToken||finished)return;
  round++;document.getElementById("roundCount").textContent=t("RONDA ","ROUND ")+round;countdown();
 },2600);
}

/* MULTIJUGADOR ONLINE (PeerJS): el anfitrión decide el resultado */
function setStatus(html){
 const el=document.getElementById("onlineStatus");
 if(!html){el.classList.add("hidden");el.innerHTML="";return}
 el.classList.remove("hidden");el.innerHTML=html;
}
function openLocalSetup(){blocked=false;closeOnline();setStatus("");showScreen("localSetup")}
function randomCode(){const ch="ABCDEFGHJKLMNPQRSTUVWXYZ23456789";let c="";for(let i=0;i<5;i++)c+=ch[Math.floor(Math.random()*ch.length)];return c}
function sendToOpponent(d){try{if(conn&&conn.open)conn.send(d)}catch(e){}}
function closeOnline(){
 const c=conn,p=peer;
 conn=null;peer=null;onlineMode=false;picks={};myDone=false;rid=0;
 if(resolveTimer){clearTimeout(resolveTimer);resolveTimer=null}
 try{if(c)c.close()}catch(e){}
 try{if(p)p.destroy()}catch(e){}
 document.getElementById("createRoomBtn").disabled=false;
 document.getElementById("joinRoomBtn").disabled=false;
 stopVoice(true);
}
function versionMismatch(notify){
 blocked=true;
 if(notify)sendToOpponent({type:"badver"});
 setStatus("Tu amigo y tú tienen versiones distintas del juego. Los dos deben recargar la página para tener la más nueva y volver a intentarlo.");
 const c=conn;setTimeout(()=>{if(conn===c)closeOnline()},400);
}
function createRoom(){
 if(typeof Peer==="undefined"){alert("No se pudo cargar PeerJS. Revisa tu conexión a internet.");return}
 blocked=false;closeOnline();
 playerName=profile.name;onlineCode=randomCode();onlineRole="A";
 setStatus("Creando sala…");
 document.getElementById("createRoomBtn").disabled=true;
 document.getElementById("joinRoomBtn").disabled=true;
 const myPeer=new Peer(PEER_PREFIX+onlineCode);peer=myPeer;
 myPeer.on("call",onIncomingCall);
 myPeer.on("open",()=>{if(peer!==myPeer)return;setStatus(`Sala creada. Pásale este código a tu amigo:<br><span class="room-code">${onlineCode}</span><br>Esperando a tu oponente…`)});
 myPeer.on("connection",c=>{
  if(peer!==myPeer)return;
  if(conn){try{c.close()}catch(e){}return}
  conn=c;wireConn(c);
 });
 myPeer.on("error",e=>{
  if(peer!==myPeer)return;
  if(e.type==="unavailable-id"){closeOnline();createRoom();return}
  closeOnline();setStatus("Error de conexión ("+e.type+"). Inténtalo de nuevo.");
 });
}
function joinRoom(){
 if(typeof Peer==="undefined"){alert("No se pudo cargar PeerJS. Revisa tu conexión a internet.");return}
 const code=document.getElementById("joinCode").value.trim().toUpperCase();
 if(code.length!==5){alert("El código tiene 5 caracteres.");return}
 blocked=false;closeOnline();
 playerName=profile.name;onlineCode=code;onlineRole="B";
 setStatus("Conectando con la sala "+escapeHtml(code)+"…");
 document.getElementById("createRoomBtn").disabled=true;
 document.getElementById("joinRoomBtn").disabled=true;
 const myPeer=new Peer();peer=myPeer;
 myPeer.on("call",onIncomingCall);
 myPeer.on("open",()=>{
  if(peer!==myPeer)return;
  const c=myPeer.connect(PEER_PREFIX+code,{reliable:true});
  conn=c;wireConn(c);
  setTimeout(()=>{if(peer===myPeer&&conn===c&&!c.open){closeOnline();setStatus("No se pudo conectar. Revisa el código e inténtalo de nuevo.")}},12000);
 });
 myPeer.on("error",e=>{
  if(peer!==myPeer)return;
  closeOnline();
  setStatus(e.type==="peer-unavailable"?"No se encontró esa sala. Revisa el código.":"Error de conexión ("+e.type+"). Inténtalo de nuevo.");
 });
}
function wireConn(c){
 c.on("open",()=>{if(c!==conn)return;if(onlineRole==="B")c.send({type:"hello",name:profile.name,ver:PROTO})});
 c.on("data",d=>{if(c===conn)onData(d)});
 c.on("close",()=>{
  if(c!==conn||blocked)return;
  const wasPlaying=onlineMode;
  closeOnline();closeRules();
  alert("Tu oponente se desconectó.");
  if(wasPlaying)showScreen("home");else{setStatus("");showScreen("localSetup")}
 });
 c.on("error",()=>{});
}
function onData(d){
 if(!d||typeof d!=="object")return;
 if(d.type==="badver"){versionMismatch(false);return}
 if(d.type==="hello"){
  if(d.ver!==PROTO){versionMismatch(true);return}
  oppName=String(d.name||"Oponente").slice(0,18);
  if(onlineRole==="A"){
   if(onlineMode)return;
   sendToOpponent({type:"hello",name:playerName,ver:PROTO});
   setupOnlineUI();startOnlineMatch();
  }
 }else if(d.type==="round"){
  if(onlineRole!=="B")return;
  if(!onlineMode)setupOnlineUI();
  if(d.reset)resetOnlineScores();
  round=Number(d.round)||1;rid=Number(d.rid)||0;
  document.getElementById("roundCount").textContent="RONDA "+round;
  countdown();
 }else if(d.type==="pick"){
  if(onlineRole!=="A"||!onlineMode||Number(d.rid)!==rid)return;
  picks[rid]={move:validMove(d.move)};hostTryResolve();
 }else if(d.type==="result"){
  if(onlineRole!=="B"||!onlineMode||Number(d.rid)!==rid)return;
  cancelCountdown();myDone=false;
  playerScore=Number(d.gs)||0;botScore=Number(d.hs)||0;
  const out=d.o==="guest"?"win":d.o==="host"?"lose":(d.o==="none"?"none":"draw");
  if(out==="win"&&!developerMode){coins+=2;saveEconomy()}
  finished=!!d.over;
  showOnlineResult(validMove(d.gm),validMove(d.hm),out,finished);
 }else if(d.type==="voice"){
  oppVoice=!!d.on;
  if(!oppVoice){try{if(voiceCall)voiceCall.close()}catch(e){}voiceCall=null;voiceConnected=false}
  updateVoiceBtn();maybeStartCall();
 }else if(d.type==="rematch"){
  if(onlineRole==="A"&&finished)startOnlineMatch();
 }
}
function setupOnlineUI(){
 onlineMode=true;
 applyTexts();
 document.getElementById("playerScoreName").innerHTML=nameWithVip(playerName);
 document.getElementById("botScoreName").textContent=oppName;
 document.getElementById("newGameBtn").classList.add("hidden");
 resetOnlineScores();renderChoices();
 if(Stage)Stage.setCount(1);
 showScreen("game");updateVoiceBtn();
 document.getElementById("result").innerHTML=`<div class="rtitle draw">¡Prepárate!</div>`;
}
function resetOnlineScores(){
 playerScore=0;botScore=0;round=1;finished=false;picks={};myDone=false;
 document.getElementById("playerScore").textContent="0";
 document.getElementById("botScore").textContent="0";
 document.getElementById("roundCount").textContent="RONDA 1";
 document.getElementById("newGameBtn").classList.add("hidden");
}
function startOnlineMatch(){resetOnlineScores();nextOnlineRound(true)}
function nextOnlineRound(reset){
 if(resolveTimer){clearTimeout(resolveTimer);resolveTimer=null}
 rid++;picks={};
 document.getElementById("roundCount").textContent="RONDA "+round;
 sendToOpponent({type:"round",rid:rid,round:round,reset:!!reset});
 countdown();
}
function hostTryResolve(){
 if(!onlineMode||onlineRole!=="A"||!myDone||finished)return;
 const p=picks[rid];
 if(!p){
  if(!resolveTimer){
   const r=rid;
   resolveTimer=setTimeout(()=>{
    resolveTimer=null;
    if(!onlineMode||rid!==r||!myDone||picks[r])return;
    picks[r]={move:null};hostTryResolve();
   },10000);
  }
  return;
 }
 if(resolveTimer){clearTimeout(resolveTimer);resolveTimer=null}
 myDone=false;delete picks[rid];
 const hm=localMove,gm=p.move;
 let o;
 if(!hm&&!gm)o="none";
 else if(hm&&!gm)o="host";
 else if(!hm&&gm)o="guest";
 else if(beatsMove(hm,gm))o="host";
 else if(beatsMove(gm,hm))o="guest";
 else o="draw";
 if(o==="host"){playerScore++;if(!developerMode)coins+=2;saveEconomy()}
 if(o==="guest")botScore++;
 const over=playerScore>=3||botScore>=3;
 sendToOpponent({type:"result",rid:rid,round:round,hm:hm||null,gm:gm||null,o:o,hs:playerScore,gs:botScore,over:over});
 finished=over;
 showOnlineResult(hm,gm,o==="host"?"win":o==="guest"?"lose":o,over);
 if(!over){
  const scored=(o==="host"||o==="guest"),token=countdownToken;
  countdownTimer=setTimeout(()=>{
   if(!onlineMode||finished||token!==countdownToken)return;
   if(scored)round++;
   nextOnlineRound(false);
  },2800);
 }
}
function showOnlineResult(mine,opp,out,over){
 document.getElementById("playerScore").textContent=playerScore;
 document.getElementById("botScore").textContent=botScore;
 /* el personaje 3D (tu oponente) muestra su gesto */
 if(Stage)Stage.reveal([{move:opp,react:out==="win"?"lose":out==="lose"?"win":"draw"}]);
 let html=titleHtml(out)+duelHtml(mine,[{name:oppName,move:opp}],out);
 if(out==="draw"||out==="none")html+=`<div>${t("Se repite la ronda.","The round repeats.")}</div>`;
 if(over){
  html+=`<div class="rfinal">${playerScore>botScore?t("¡Ganaste la partida!","You won the match!"):t("¡Perdiste la partida!","You lost the match!")}</div>`;
  document.getElementById("arenaSubtitle").textContent=t("Partida terminada","Match over");
  const nb=document.getElementById("newGameBtn");
  nb.textContent=t("Revancha","Rematch");nb.classList.remove("hidden");nb.onclick=requestRematch;
 }else document.getElementById("arenaSubtitle").textContent=t("¡Prepárate para la siguiente ronda!","Get ready for the next round!");
 document.getElementById("result").innerHTML=html;
}
function requestRematch(){
 if(!onlineMode||!finished)return;
 if(onlineRole==="A")startOnlineMatch();
 else{
  sendToOpponent({type:"rematch"});
  document.getElementById("newGameBtn").classList.add("hidden");
  document.getElementById("arenaSubtitle").textContent="Esperando que el anfitrión inicie la revancha…";
 }
}

/* PANTALLA DE INSTALACIÓN */
let deferredPrompt=null,gatePlatform=null,justInstalled=false;
function detectPlatform(){
 const ua=navigator.userAgent||"";
 if(/iPad|iPhone|iPod/.test(ua)||(navigator.platform==="MacIntel"&&navigator.maxTouchPoints>1))return "ios";
 if(/Android/i.test(ua))return "android";
 return "other";
}
function isStandalone(){
 try{
  if(navigator.standalone===true)return true;
  if(window.matchMedia){for(const m of["standalone","fullscreen","minimal-ui","window-controls-overlay"])if(window.matchMedia("(display-mode: "+m+")").matches)return true}
  if((document.referrer||"").indexOf("android-app://")===0)return true;
 }catch(e){}
 return false;
}
function inAppBrowser(){return /FBAN|FBAV|Instagram|TikTok|musical_ly|Bytedance|Snapchat|MicroMessenger|Twitter|; wv\)|GSA\//i.test(navigator.userAgent||"")}
function shouldGate(){return detectPlatform()!=="other"&&!isStandalone()&&!developerMode}
function applyGate(){const g=shouldGate();document.documentElement.classList.toggle("gated",g);if(g)renderGate()}
function stepRow(n,h){return `<div class="gate-step"><span class="gate-num">${n}</span><p>${h}</p></div>`}
function gateIosCard(){
 return `<div class="gate-card"><h3>${t("En iPhone o iPad","On iPhone or iPad")}</h3>`+
 stepRow(1,t(`Toca el botón <b>Compartir</b> ${ico("share")} (el cuadrado con una flecha hacia arriba).`,`Tap the <b>Share</b> button ${ico("share")} (the square with an arrow pointing up).`))+
 stepRow(2,t(`Busca y selecciona <b>Agregar a pantalla de inicio</b>.`,`Find and select <b>Add to Home Screen</b>.`))+
 stepRow(3,t(`Toca <b>Agregar</b> en la esquina superior derecha.`,`Tap <b>Add</b> in the top right corner.`))+
 stepRow(4,t(`Cierra el navegador y abre Paper Pals desde el nuevo ícono.`,`Close the browser and open Paper Pals from the new icon.`))+
 `<div class="gate-note">${t("En Safari, el botón Compartir está en la barra del navegador (abajo en iPhone, arriba en iPad). Si no lo ves, toca los tres puntos ••• de la barra.","In Safari, the Share button is in the browser bar (bottom on iPhone, top on iPad). If you can't see it, tap the three dots ••• in the bar.")}</div></div>`;
}
function gateAndroidCard(){
 return `<div class="gate-card"><h3>${t("En Android","On Android")}</h3>`+
 stepRow(1,t(`Toca el menú del navegador ${ico("dots")} (los tres puntos, arriba a la derecha en Chrome).`,`Tap the browser menu ${ico("dots")} (the three dots, top right in Chrome).`))+
 stepRow(2,t(`Elige <b>Instalar app</b> o <b>Agregar a la pantalla principal</b>.`,`Choose <b>Install app</b> or <b>Add to Home screen</b>.`))+
 stepRow(3,t(`Confirma tocando <b>Instalar</b> o <b>Agregar</b>.`,`Confirm by tapping <b>Install</b> or <b>Add</b>.`))+
 stepRow(4,t(`Cierra el navegador y abre Paper Pals desde el nuevo ícono.`,`Close the browser and open Paper Pals from the new icon.`))+
 `<div class="gate-note">${t("Funciona mejor en Chrome. Si abriste el juego desde otra app, ábrelo primero en Chrome.","Works best in Chrome. If you opened the game from another app, open it in Chrome first.")}</div></div>`;
}
function renderGate(){
 const logo=document.getElementById("gateLogo");
 if(!logo.firstChild){const src=document.querySelector("#home .logo");if(src)logo.innerHTML=src.innerHTML}
 const plat=gatePlatform||(detectPlatform()==="android"?"android":"ios");
 document.getElementById("gateTitle").textContent=t("Agregar a pantalla de inicio","Add to Home Screen");
 document.getElementById("gateSub").textContent=t("Instala Paper Pals en tu dispositivo para abrirlo como una aplicación.","Install Paper Pals on your device to open it like an app.");
 let html="";
 if(justInstalled)html+=`<div class="gate-note ok gate-top">${t("¡Listo! Paper Pals ya está instalado. Cierra esta pestaña y ábrelo desde su nuevo ícono.","Done! Paper Pals is installed. Close this tab and open it from its new icon.")}</div>`;
 if(inAppBrowser())html+=`<div class="gate-note gate-top">${t("Parece que abriste el juego dentro de otra app (TikTok, Instagram, etc.). Ábrelo en Safari o Chrome y sigue los pasos desde ahí.","It looks like you opened the game inside another app (TikTok, Instagram, etc.). Open it in Safari or Chrome and follow the steps from there.")}</div>`;
 if(plat==="android"&&deferredPrompt)html+=`<button class="btn play full gate-install" onclick="installNow()">${t("Instalar ahora","Install now")}</button>`;
 html+=plat==="ios"?gateIosCard():gateAndroidCard();
 html+=`<button class="gate-switch" onclick="switchGatePlatform()">${plat==="ios"?t("¿Usas Android? Ver pasos","Using Android? See steps"):t("¿Usas iPhone o iPad? Ver pasos","Using iPhone or iPad? See steps")}</button>`;
 document.getElementById("gateBody").innerHTML=html;
}
function switchGatePlatform(){
 const cur=gatePlatform||(detectPlatform()==="android"?"android":"ios");
 gatePlatform=cur==="ios"?"android":"ios";renderGate();
}
function installNow(){
 if(!deferredPrompt)return;
 const p=deferredPrompt;deferredPrompt=null;
 try{p.prompt();if(p.userChoice&&p.userChoice.then)p.userChoice.then(()=>renderGate(),()=>renderGate())}catch(e){}
 renderGate();
}
window.addEventListener("beforeinstallprompt",e=>{e.preventDefault();deferredPrompt=e;if(shouldGate())renderGate()});
window.addEventListener("appinstalled",()=>{deferredPrompt=null;justInstalled=true;if(shouldGate())renderGate()});
try{
 const mq=window.matchMedia("(display-mode: standalone)");
 if(mq.addEventListener)mq.addEventListener("change",applyGate);else if(mq.addListener)mq.addListener(applyGate);
}catch(e){}

/* Ícono de la app al agregarla a la pantalla de inicio */
const APP_ICON="https://i.postimg.cc/Pxy94hpV/Untitled276-20261101160123.jpg";
function setupInstallMeta(){
 try{
  if(/^https?:$/.test(location.protocol)){
   const base=location.href.split("#")[0].split("?")[0];
   const manifest={name:"Paper Pals",short_name:"Paper Pals",start_url:base,scope:base.replace(/[^\/]*$/,""),display:"standalone",background_color:"#ffffff",theme_color:"#ffffff",
    icons:[{src:APP_ICON,sizes:"192x192",type:"image/jpeg",purpose:"any"},{src:APP_ICON,sizes:"512x512",type:"image/jpeg",purpose:"any"}]};
   const l=document.createElement("link");l.rel="manifest";
   l.href=URL.createObjectURL(new Blob([JSON.stringify(manifest)],{type:"application/manifest+json"}));
   document.head.appendChild(l);
  }
 }catch(e){}
}

/* DESARROLLADOR */
function developerCorner(){
 if(developerMode){developerMode=false;storeSet("rpsDeveloperMode","false");updateCoins();applyGate();alert("Modo desarrollador desactivado.");return}
 document.getElementById("devCodeInput").value="";
 document.getElementById("devModal").classList.remove("hidden");
 document.getElementById("devCodeInput").focus();
}
function closeDeveloperModal(){document.getElementById("devModal").classList.add("hidden")}
function submitDeveloperCode(){
 if(document.getElementById("devCodeInput").value.trim()==="11583"){
  developerMode=true;storeSet("rpsDeveloperMode","true");
  closeDeveloperModal();updateCoins();applyGate();alert("¡Modo desarrollador activado!");
 }else{alert("Código incorrecto.");document.getElementById("devCodeInput").value=""}
}
document.getElementById("devCodeInput").addEventListener("keydown",e=>{if(e.key==="Enter")submitDeveloperCode();if(e.key==="Escape")closeDeveloperModal()});
document.addEventListener("keydown",e=>{if(e.key==="Escape"){closeRules();closeProfileEditor();closeDelete()}});

loadTheme();
loadProfile();
hydrateIcons();
renderProfile();
applyTexts();
renderChoices();
document.getElementById("result").innerHTML=`<div class="rtitle draw">Elige tu herramienta.</div>`;
updateCoins();
setupInstallMeta();
applyGate();
loadLook();
if(Stage)Stage.setLook(look);
if(Stage)Stage.screen("home");
</script>
</body>
</html>
