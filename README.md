git init
git add .
git commit -m "first upload"
git branch -M main
git remote add origin YOUR_GITHUB_REPO_URL
git push -u origin main

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>RIVAL FC | May 9 Fight Night</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Barlow:ital,wght@0,300;0,400;0,600;0,700;1,400&family=Barlow+Condensed:wght@400;600;700&display=swap" rel="stylesheet">
<style>
:root {
  --red:#C8102E; --gold:#D4AF37; --dark:#080808; --dark2:#0f0f0f;
  --fd:'Bebas Neue',sans-serif; --fb:'Barlow',sans-serif; --fc:'Barlow Condensed',sans-serif;
}
*{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{background:var(--dark);color:#f0f0f0;font-family:var(--fb);overflow-x:hidden;}

/* ── NAV ── */
#nav{position:fixed;top:0;left:0;width:100%;z-index:1000;display:flex;justify-content:space-between;align-items:center;padding:0 50px;height:72px;background:rgba(8,8,8,.93);backdrop-filter:blur(14px);border-bottom:1px solid rgba(200,16,46,.25);transition:height .3s,background .3s;}
#nav.scrolled{height:60px;background:rgba(4,4,4,.98);}
.nav-logo{font-family:var(--fd);font-size:30px;color:#fff;letter-spacing:4px;text-decoration:none;}
.nav-logo em{color:var(--red);font-style:normal;}
.nav-links{display:flex;gap:28px;list-style:none;align-items:center;}
.nav-links a{color:rgba(255,255,255,.7);text-decoration:none;font-family:var(--fc);font-size:12px;letter-spacing:2.5px;text-transform:uppercase;font-weight:600;transition:color .2s;position:relative;}
.nav-links a::after{content:'';position:absolute;bottom:-5px;left:0;width:0;height:1px;background:var(--red);transition:width .3s;}
.nav-links a:hover{color:#fff;}
.nav-links a:hover::after{width:100%;}
.nav-cta{background:var(--red)!important;color:#fff!important;padding:8px 18px;clip-path:polygon(6px 0%,100% 0%,calc(100% - 6px) 100%,0 100%);}
.nav-cta:hover{background:#a80d27!important;}
.nav-cta::after{display:none!important;}

/* hamburger */
.hbg{display:none;flex-direction:column;justify-content:center;gap:5px;width:36px;height:36px;background:none;border:none;cursor:pointer;padding:4px;}
.hbg span{display:block;width:100%;height:2px;background:#fff;border-radius:2px;transition:all .3s;transform-origin:center;}
.hbg.open span:nth-child(1){transform:translateY(7px) rotate(45deg);}
.hbg.open span:nth-child(2){opacity:0;transform:scaleX(0);}
.hbg.open span:nth-child(3){transform:translateY(-7px) rotate(-45deg);}

/* drawer */
.drw-ov{position:fixed;inset:0;z-index:1040;background:rgba(0,0,0,.6);backdrop-filter:blur(4px);opacity:0;pointer-events:none;transition:opacity .3s;}
.drw-ov.open{opacity:1;pointer-events:all;}
.drw{position:fixed;top:0;right:-100%;width:min(320px,85vw);height:100dvh;background:#080808;border-left:1px solid rgba(200,16,46,.25);z-index:1050;display:flex;flex-direction:column;padding:90px 32px 40px;gap:4px;transition:right .4s cubic-bezier(.23,1,.32,1);overflow-y:auto;}
.drw.open{right:0;}
.drw a{font-family:var(--fd);font-size:30px;letter-spacing:3px;color:rgba(255,255,255,.7);text-decoration:none;padding:9px 0;border-bottom:1px solid rgba(255,255,255,.07);transition:color .2s;}
.drw a:hover{color:#fff;}
.drw .drw-cta{color:var(--red);border-color:rgba(200,16,46,.2);}

/* ── FLOATING BAR ── */
#fbar{position:fixed;bottom:0;left:0;width:100%;z-index:990;background:linear-gradient(90deg,#0a0a0a,#16030a 45%,#0a0a0a);border-top:1px solid rgba(200,16,46,.4);padding:10px 50px;display:flex;align-items:center;justify-content:center;gap:28px;transform:translateY(100%);transition:transform .55s cubic-bezier(.23,1,.32,1);}
#fbar.show{transform:translateY(0);}
.fb-ev{font-family:var(--fc);font-size:13px;letter-spacing:3.5px;text-transform:uppercase;color:rgba(255,255,255,.45);border-right:1px solid rgba(255,255,255,.12);padding-right:26px;}
.fb-lbl{font-family:var(--fc);font-size:13px;letter-spacing:3px;text-transform:uppercase;color:var(--red);}
.fb-units{display:flex;align-items:center;gap:6px;}
.fb-u{text-align:center;min-width:46px;}
.fb-n{font-family:var(--fd);font-size:30px;line-height:1;color:#fff;}
.fb-s{font-family:var(--fc);font-size:11px;letter-spacing:2.5px;text-transform:uppercase;color:rgba(255,255,255,.4);margin-top:2px;}
.fb-col{font-family:var(--fd);font-size:26px;color:var(--red);opacity:.6;padding-bottom:8px;}
.fb-cta{margin-left:auto;font-family:var(--fc);font-size:12px;letter-spacing:2.5px;text-transform:uppercase;color:var(--gold);text-decoration:none;border:1px solid rgba(212,175,55,.35);padding:7px 18px;transition:all .25s;}
.fb-cta:hover{background:rgba(212,175,55,.1);}

/* ── SHARED SECTION ── */
section{min-height:100vh;position:relative;display:flex;flex-direction:column;justify-content:center;}
.s-bg{position:absolute;inset:0;background-size:cover;background-position:center;}
.s-ov{position:absolute;inset:0;}
.wrap{position:relative;z-index:2;padding:110px 60px 90px;max-width:1160px;margin:0 auto;width:100%;}
.eyebrow{display:block;font-family:var(--fc);font-size:15px;letter-spacing:5px;text-transform:uppercase;color:var(--red);margin-bottom:14px;}
.stitle{font-family:var(--fd);font-size:clamp(52px,8vw,100px);line-height:.92;color:#fff;}
.srule{width:50px;height:2px;background:linear-gradient(90deg,var(--red),var(--gold));margin-top:22px;}

/* buttons */
.btn-r{font-family:var(--fc);font-size:14px;letter-spacing:3px;text-transform:uppercase;font-weight:700;padding:14px 36px;background:var(--red);color:#fff;border:none;cursor:pointer;text-decoration:none;display:inline-block;transition:all .3s;clip-path:polygon(8px 0%,100% 0%,calc(100% - 8px) 100%,0 100%);}
.btn-r:hover{background:#a80d27;transform:translateY(-2px);}
.btn-g{font-family:var(--fc);font-size:14px;letter-spacing:3px;text-transform:uppercase;font-weight:700;padding:14px 36px;background:transparent;color:rgba(255,255,255,.85);border:1px solid rgba(255,255,255,.3);cursor:pointer;text-decoration:none;display:inline-block;transition:all .3s;clip-path:polygon(8px 0%,100% 0%,calc(100% - 8px) 100%,0 100%);}
.btn-g:hover{border-color:var(--gold);color:var(--gold);}

/* reveal */
.rv{opacity:0;transform:translateY(36px);transition:opacity .75s ease,transform .75s ease;}
.rv.on{opacity:1;transform:translateY(0);}

/* ── HERO ── */
#home{overflow:hidden;}
.hero-bg{background-image:url('https://scontent-atl3-1.xx.fbcdn.net/v/t39.30808-6/657726652_26924310963868014_37800289183006365_n.jpg?_nc_cat=105&ccb=1-7&_nc_sid=13d280&_nc_ohc=xoA8YjxWu40Q7kNvwGyHPQl&_nc_oc=Adoa1-L9rgA6HPYzFyy6zexXiJOUtSdgaSSNRCspquJz1FWBz-LbUZEoYZxkzRuZpClECRuVLocdV3986KIFiDR1&_nc_zt=23&_nc_ht=scontent-atl3-1.xx&_nc_gid=CRVC_7Cm_XZPvK3wt9brUA&_nc_ss=7a3a8&oh=00_AfxzsUlvjlBYVo2KU7nlVY7LtIfPCk9reFqObz8oKS9gCQ&oe=69D0CE9D');}
.hero-ov{background:linear-gradient(160deg,rgba(0,0,0,.88),rgba(80,0,15,.3) 50%,rgba(0,0,0,.82));}
#home::after{content:'';position:absolute;inset:0;z-index:1;pointer-events:none;background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)' opacity='0.07'/%3E%3C/svg%3E");opacity:.35;}
.hero-in{min-height:100vh;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:80px 24px 110px;position:relative;z-index:2;}
.h-pre{font-family:var(--fc);font-size:13px;letter-spacing:6px;text-transform:uppercase;color:#fff;margin-bottom:22px;opacity:0;animation:fadeUp .9s ease .2s forwards;}
.h-logo{font-family:var(--fd);font-size:clamp(90px,18vw,200px);line-height:.88;color:#fff;text-shadow:0 0 100px rgba(200,16,46,.4);opacity:0;animation:fadeUp .9s ease .45s forwards;}
.h-logo span{color:var(--red);display:block;}
.h-tag{font-family:var(--fc);font-size:clamp(15px,2.5vw,22px);letter-spacing:5px;color:#fff;margin-top:18px;opacity:0;animation:fadeUp .9s ease .7s forwards;}
.h-venue{font-family:var(--fd);font-size:clamp(14px,2.6vw,30px);color:#fff;letter-spacing:4px;margin-top:12px;opacity:0;animation:fadeUp .9s ease .9s forwards;text-decoration:none;border-bottom:1px solid rgba(255,255,255,.25);padding-bottom:3px;transition:color .25s,border-color .25s;}
.h-venue:hover{color:var(--gold);border-color:var(--gold);}
.h-cd{display:flex;align-items:center;gap:12px;margin:42px 0 36px;flex-wrap:wrap;justify-content:center;opacity:0;animation:fadeUp .9s ease 1.1s forwards;}
.hcd{background:rgba(255,255,255,.04);border:1px solid rgba(200,16,46,.28);backdrop-filter:blur(8px);padding:18px 22px;min-width:90px;text-align:center;position:relative;overflow:hidden;}
.hcd::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,rgba(200,16,46,.6),transparent);}
.hcd-n{font-family:var(--fd);font-size:58px;line-height:1;color:#fff;}
.hcd-l{font-family:var(--fc);font-size:10px;letter-spacing:3px;text-transform:uppercase;color:var(--gold);margin-top:5px;}
.hcd-sep{font-family:var(--fd);font-size:46px;color:var(--red);opacity:.6;margin-bottom:14px;}
.h-ctas{display:flex;gap:14px;justify-content:center;flex-wrap:wrap;opacity:0;animation:fadeUp .9s ease 1.35s forwards;}
.h-scroll{position:absolute;bottom:36px;left:50%;transform:translateX(-50%);display:flex;flex-direction:column;align-items:center;gap:8px;z-index:2;opacity:0;animation:fadeIn 1s ease 2.5s forwards;}
.h-scroll span{font-family:var(--fc);font-size:9px;letter-spacing:4px;text-transform:uppercase;opacity:.35;}
.scroll-b{width:1px;height:42px;background:linear-gradient(to bottom,rgba(200,16,46,.8),transparent);animation:sPulse 2s ease infinite;}
@keyframes fadeUp{from{opacity:0;transform:translateY(28px);}to{opacity:1;transform:translateY(0);}}
@keyframes fadeIn{from{opacity:0;}to{opacity:1;}}
@keyframes sPulse{0%,100%{opacity:.4;height:42px;}50%{opacity:1;height:58px;}}

/* ── EVENT ── */
#event{background:var(--dark2);}
.ev-bg{background-image:url('https://scontent-atl3-3.xx.fbcdn.net/v/t39.30808-6/648110213_26677470618552051_6380660066897119591_n.jpg?_nc_cat=107&ccb=1-7&_nc_sid=13d280&_nc_ohc=aF3RqcUDBRcQ7kNvwGZpOiM&_nc_oc=AdrK88ccIxQctQLQhBhQR72pRkOuIB-NE7OLtFDlinQFtyTFZRf7I93ERxtMnP6va8ZfxaU5zWqEy4POszJdeiXS&_nc_zt=23&_nc_ht=scontent-atl3-3.xx&_nc_gid=KEcEaXf6KekLR3hHrdFBEA&_nc_ss=7a3a8&oh=00_AfwOzbJ8m4F8cNjaAPqJszEy_OKalmhhWDwEJPmxWvaJaw&oe=69D0A444');opacity:.06;}
.ev-grid{display:grid;grid-template-columns:1fr 1fr;gap:2px;margin-top:50px;}
.ecard{background:rgba(255,255,255,.027);border:1px solid rgba(255,255,255,.065);border-left:2px solid rgba(200,16,46,.6);padding:30px 26px;transition:all .3s;}
.ecard:hover{background:rgba(255,255,255,.05);border-left-color:var(--gold);}
.ecard-icon{font-size:26px;margin-bottom:12px;}
.elbl{font-family:var(--fc);font-size:12px;letter-spacing:4px;text-transform:uppercase;color:var(--red);margin-bottom:8px;}
.eval{font-family:var(--fd);font-size:30px;color:#fff;line-height:1.1;}
.esub{font-size:13px;color:rgba(255,255,255,.4);margin-top:5px;}
.ecard-full{grid-column:1/-1;display:flex;align-items:center;justify-content:space-between;gap:24px;}
.ebtn{display:inline-flex;align-items:center;gap:7px;margin-top:14px;font-family:var(--fc);font-size:12px;letter-spacing:2.5px;text-transform:uppercase;font-weight:700;color:var(--red);background:none;border:1px solid rgba(200,16,46,.35);padding:8px 16px;cursor:pointer;text-decoration:none;transition:all .25s;}
.ebtn:hover{background:rgba(200,16,46,.1);border-color:var(--red);color:#fff;}
.ebtn.cal{color:var(--gold);border-color:rgba(212,175,55,.35);}
.ebtn.cal:hover{background:rgba(212,175,55,.1);border-color:var(--gold);color:#fff;}
.ebtn.fb{color:#4267B2;border-color:rgba(66,103,178,.35);}
.ebtn.fb:hover{background:rgba(66,103,178,.1);border-color:#4267B2;color:#fff;}

/* ── FIGHT CARD ── */
#fights{background:var(--dark);}
.fg-bg{background-image:url('https://69c8c3c6a9fb0ef7c01329fe.imgix.net/lispypic.png');opacity:.055;}
.fstack{display:flex;flex-direction:column;gap:3px;margin-top:50px;}
.frow{background:rgba(255,255,255,.026);border:1px solid rgba(255,255,255,.055);padding:24px 32px;display:grid;grid-template-columns:1fr auto 1fr;align-items:center;gap:20px;transition:background .3s;position:relative;overflow:hidden;}
.frow::before{content:'';position:absolute;left:0;top:0;bottom:0;width:0;background:var(--red);transition:width .3s;}
.frow:hover::before{width:2px;}
.frow:hover{background:rgba(200,16,46,.04);}
.frow.main{background:rgba(200,16,46,.07);border-color:rgba(200,16,46,.22);padding:34px 36px;}
.frow.main::before{width:3px;}
.fl{display:flex;flex-direction:row;align-items:center;gap:14px;}
.fr{display:flex;flex-direction:row-reverse;align-items:center;gap:14px;}
.fpw{flex-shrink:0;position:relative;}
.fpw a{display:block;}
.fph{width:62px;height:62px;border-radius:50%;object-fit:cover;border:2px solid rgba(255,255,255,.12);display:block;background:#1a1a1a;transition:border-color .25s,transform .25s;}
.frow.main .fph{width:80px;height:80px;border-color:rgba(200,16,46,.4);}
.fpw a:hover .fph{border-color:var(--red);transform:scale(1.07);}
.ftip{position:absolute;bottom:-24px;left:50%;transform:translateX(-50%);font-family:var(--fc);font-size:9px;letter-spacing:1.5px;text-transform:uppercase;color:var(--red);white-space:nowrap;opacity:0;transition:opacity .2s;pointer-events:none;}
.fpw:hover .ftip{opacity:1;}
.finfo{display:flex;flex-direction:column;}
.fr .finfo{align-items:flex-end;text-align:right;}
.fname{font-family:var(--fd);font-size:clamp(22px,3vw,36px);color:#fff;line-height:1;}
.frow.main .fname{font-size:clamp(28px,4.5vw,50px);}
.frec{font-family:var(--fc);font-size:15px;letter-spacing:2px;color:rgba(255,255,255,.38);margin-top:4px;}
.ftag{font-family:var(--fc);font-size:13px;letter-spacing:2px;text-transform:uppercase;color:var(--gold);margin-top:6px;}
.vsc{display:flex;flex-direction:column;align-items:center;gap:6px;}
.vsb{font-family:var(--fc);font-size:12px;letter-spacing:2px;text-transform:uppercase;padding:4px 13px;border-radius:1px;}
.vsb.me{background:var(--red);color:#fff;}
.vsb.cm{background:rgba(212,175,55,.2);color:var(--gold);border:1px solid rgba(212,175,55,.4);}
.vsb.pr{background:rgba(255,255,255,.07);color:rgba(255,255,255,.45);}
.vsw{font-family:var(--fd);font-size:32px;color:var(--red);}
.frow.main .vsw{font-size:46px;}
.vswt{font-family:var(--fc);font-size:13px;letter-spacing:2px;text-transform:uppercase;color:rgba(255,255,255,.3);}
.fnote{margin-top:22px;font-family:var(--fc);font-size:13px;letter-spacing:2px;text-transform:uppercase;color:rgba(255,255,255,.22);}
.tba-c{width:62px;height:62px;border-radius:50%;flex-shrink:0;background:rgba(255,255,255,.05);border:2px dashed rgba(255,255,255,.15);display:flex;align-items:center;justify-content:center;font-size:22px;}

/* ── TICKETS ── */
#tickets{background:var(--dark2);}
.tk-bg{background-image:url('https://69c8c3c6a9fb0ef7c01329fe.imgix.net/handwraps.png');opacity:.055;}
.tk-row{display:grid;grid-template-columns:repeat(3,1fr);gap:18px;margin-top:50px;}
.tcard{background:rgba(255,255,255,.028);border:1px solid rgba(255,255,255,.07);padding:40px 28px;display:flex;flex-direction:column;transition:transform .3s;position:relative;overflow:hidden;}
.tcard::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;}
.tcard.ga::before{background:rgba(255,255,255,.2);}
.tcard.vip::before{background:var(--gold);}
.tcard.cage::before{background:var(--red);}
.tcard.vip{border-color:rgba(212,175,55,.25);background:rgba(212,175,55,.04);}
.tcard.cage{border-color:rgba(200,16,46,.2);}
.tcard:hover{transform:translateY(-6px);}
.ttier{font-family:var(--fc);font-size:14px;letter-spacing:5px;text-transform:uppercase;color:rgba(255,255,255,.4);margin-bottom:22px;}
.tcard.vip .ttier{color:var(--gold);}
.tcard.cage .ttier{color:var(--red);}
.tprice{font-family:var(--fd);font-size:78px;line-height:1;color:#fff;}
.tcard.vip .tprice{color:var(--gold);}
.tcard.cage .tprice{color:var(--red);}
.tper{font-family:var(--fc);font-size:13px;color:rgba(255,255,255,.3);margin-bottom:26px;}
.tfeats{list-style:none;flex:1;margin-bottom:26px;}
.tfeats li{font-size:14px;color:rgba(255,255,255,.55);padding:9px 0;border-bottom:1px solid rgba(255,255,255,.055);}
.tfeats li em{font-style:normal;color:var(--gold);margin-right:7px;}
.tbtn{font-family:var(--fc);font-size:13px;letter-spacing:3px;text-transform:uppercase;font-weight:700;padding:14px 24px;text-align:center;text-decoration:none;display:block;cursor:pointer;transition:all .25s;border:none;}
.tbtn.ga{background:rgba(255,255,255,.09);color:#fff;}
.tbtn.ga:hover{background:rgba(255,255,255,.17);}
.tbtn.vip{background:var(--gold);color:#000;}
.tbtn.vip:hover{background:#c4a230;}
.tbtn.cage{background:var(--red);color:#fff;}
.tbtn.cage:hover{background:#a80d27;}
.urgency{margin-top:28px;background:rgba(200,16,46,.07);border:1px solid rgba(200,16,46,.2);padding:16px 26px;font-family:var(--fc);font-size:16px;letter-spacing:2px;text-align:center;color:rgba(255,255,255,.6);}
.urgency strong{color:var(--red);}

/* ── PREVIOUS EVENT ── */
#previous{background:var(--dark);}
.prev-bg{background-image:url('https://scontent-atl3-3.xx.fbcdn.net/v/t39.30808-6/649708734_26703985502567229_4328430274390572322_n.jpg?_nc_cat=107&ccb=1-7&_nc_sid=13d280&_nc_ohc=7nqpjnJOHUkQ7kNvwGK6Sz-&_nc_oc=AdoQUb468zXDt3ZaIY0gEBDA62BBRfYl9vTkQhtvXD4iV3kLez0cZajTNyIJAb-yG8ZvpXq76gbBYrMqT7UygmCA&_nc_zt=23&_nc_ht=scontent-atl3-3.xx&_nc_gid=rPP_5uI_nX_53Hwn_UEYOQ&_nc_ss=7a3a8&oh=00_AfyLKbFQYNpujjVzhuwyqW0iMMD2PITGtllFyYKCIw1-Sg&oe=69D0A9DD');opacity:.05;}
.prev-grid{display:grid;grid-template-columns:1.4fr 1fr;gap:40px;margin-top:50px;align-items:start;}
.prev-embed{position:relative;padding-bottom:56.25%;height:0;overflow:hidden;border:1px solid rgba(200,16,46,.25);}
.prev-embed iframe{position:absolute;top:0;left:0;width:100%;height:100%;border:none;}
.prev-side{display:flex;flex-direction:column;gap:18px;}
.prev-ic{background:rgba(255,255,255,.027);border:1px solid rgba(255,255,255,.065);border-left:2px solid var(--gold);padding:20px 22px;}
.prev-ic-lbl{font-family:var(--fc);font-size:12px;letter-spacing:3px;text-transform:uppercase;color:var(--gold);margin-bottom:6px;}
.prev-ic-val{font-family:var(--fd);font-size:24px;color:#fff;line-height:1.1;}
.prev-ic-sub{font-size:13px;color:rgba(255,255,255,.4);margin-top:4px;}
.btn-yt{display:inline-flex;align-items:center;gap:10px;font-family:var(--fc);font-size:13px;letter-spacing:2.5px;text-transform:uppercase;font-weight:700;padding:14px 28px;background:#FF0000;color:#fff;text-decoration:none;transition:background .25s;clip-path:polygon(7px 0%,100% 0%,calc(100% - 7px) 100%,0 100%);}
.btn-yt:hover{background:#cc0000;}

/* ── PPV / WATCH LIVE ── */
#ppv{background:var(--dark2);}
.ppv-bg{background-image:url('https://scontent-atl3-3.xx.fbcdn.net/v/t39.30808-6/645586962_26674723475493432_1879089222653774194_n.jpg?_nc_cat=107&ccb=1-7&_nc_sid=13d280&_nc_ohc=uW5RtPgzfY4Q7kNvwELT4ld&_nc_oc=Adpc-NP5QG-Uljxr0HSOfXVQDr242BkQm_C2aJfLjm9pHvvxe0eecIQgiL76lZbGfdhcbMjpVf9Wdt3pFPiTUfWA&_nc_zt=23&_nc_ht=scontent-atl3-3.xx&_nc_gid=APsJ2yhtL-k-_AV2vPzkXg&_nc_ss=7a3a8&oh=00_AfwwTEPOxIoCChNujhpz_pU0pwvj3kvDxHiDgpP4ANUQiw&oe=69D0BBB5');opacity:.05;}
.ppv-layout{display:grid;grid-template-columns:1fr 1fr;gap:40px;margin-top:50px;align-items:start;}

/* stream embed / placeholder */
.ppv-screen{background:#000;border:1px solid rgba(200,16,46,.25);aspect-ratio:16/9;display:flex;align-items:center;justify-content:center;position:relative;overflow:hidden;}
.ppv-screen iframe{position:absolute;inset:0;width:100%;height:100%;border:none;}
.ppv-placeholder{display:flex;flex-direction:column;align-items:center;justify-content:center;gap:14px;height:100%;width:100%;background:repeating-linear-gradient(45deg,rgba(200,16,46,.04),rgba(200,16,46,.04) 1px,transparent 1px,transparent 20px);padding:30px;}
.ppv-ph-icon{font-size:54px;opacity:.4;}
.ppv-ph-txt{font-family:var(--fd);font-size:24px;letter-spacing:3px;color:rgba(255,255,255,.25);text-align:center;}
.ppv-ph-sub{font-family:var(--fc);font-size:12px;letter-spacing:2px;color:rgba(255,255,255,.18);text-transform:uppercase;text-align:center;}

/* PPV purchase panel */
.ppv-panel{display:flex;flex-direction:column;gap:16px;}
.ppv-price-card{background:rgba(200,16,46,.07);border:1px solid rgba(200,16,46,.25);padding:28px 24px;position:relative;overflow:hidden;}
.ppv-price-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:var(--red);}
.ppv-price-label{font-family:var(--fc);font-size:11px;letter-spacing:4px;text-transform:uppercase;color:var(--red);margin-bottom:8px;}
.ppv-price-amount{font-family:var(--fd);font-size:72px;line-height:1;color:#fff;}
.ppv-price-per{font-family:var(--fc);font-size:13px;color:rgba(255,255,255,.35);margin-bottom:20px;}
.ppv-features{list-style:none;margin-bottom:22px;}
.ppv-features li{font-size:14px;color:rgba(255,255,255,.55);padding:8px 0;border-bottom:1px solid rgba(255,255,255,.055);}
.ppv-features li em{font-style:normal;color:var(--gold);margin-right:7px;}
.btn-ppv{font-family:var(--fc);font-size:14px;letter-spacing:3px;text-transform:uppercase;font-weight:700;padding:16px 24px;background:var(--red);color:#fff;border:none;cursor:pointer;text-decoration:none;display:block;text-align:center;transition:all .3s;clip-path:polygon(8px 0%,100% 0%,calc(100% - 8px) 100%,0 100%);}
.btn-ppv:hover{background:#a80d27;transform:translateY(-2px);}
.ppv-info-cards{display:flex;flex-direction:column;gap:10px;}
.ppv-ic{background:rgba(255,255,255,.027);border:1px solid rgba(255,255,255,.065);border-left:2px solid var(--gold);padding:16px 18px;}
.ppv-ic-lbl{font-family:var(--fc);font-size:11px;letter-spacing:3px;text-transform:uppercase;color:var(--gold);margin-bottom:5px;}
.ppv-ic-val{font-family:var(--fd);font-size:22px;color:#fff;line-height:1.1;}
.ppv-ic-sub{font-size:13px;color:rgba(255,255,255,.4);margin-top:3px;}
.ppv-note{background:rgba(212,175,55,.06);border:1px solid rgba(212,175,55,.2);padding:16px 20px;font-family:var(--fc);font-size:13px;letter-spacing:1.5px;color:rgba(255,255,255,.5);line-height:1.6;}
.ppv-note strong{color:var(--gold);}
.ppv-note a{color:var(--gold);text-decoration:none;}
.ppv-note a:hover{text-decoration:underline;}

/* PPV success modal */
.ppv-modal-back{position:fixed;inset:0;z-index:3000;background:rgba(0,0,0,.88);backdrop-filter:blur(8px);display:flex;align-items:center;justify-content:center;opacity:0;pointer-events:none;transition:opacity .35s ease;}
.ppv-modal-back.open{opacity:1;pointer-events:all;}
.ppv-modal{background:#0f0f0f;border:1px solid rgba(200,16,46,.35);width:min(540px,94vw);padding:40px;position:relative;transform:translateY(30px) scale(.97);transition:transform .35s cubic-bezier(.23,1,.32,1);}
.ppv-modal-back.open .ppv-modal{transform:translateY(0) scale(1);}
.ppv-modal-close{position:absolute;top:16px;right:16px;background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.12);color:rgba(255,255,255,.7);width:32px;height:32px;border-radius:50%;font-size:16px;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .2s;}
.ppv-modal-close:hover{background:var(--red);border-color:var(--red);color:#fff;}
.ppv-modal-icon{font-size:48px;margin-bottom:16px;}
.ppv-modal-title{font-family:var(--fd);font-size:42px;color:#fff;letter-spacing:2px;line-height:1;margin-bottom:10px;}
.ppv-modal-body{font-family:var(--fc);font-size:15px;letter-spacing:1.5px;color:rgba(255,255,255,.55);line-height:1.6;margin-bottom:24px;}
.ppv-modal-link{display:block;font-family:var(--fc);font-size:13px;letter-spacing:2px;padding:14px 20px;background:rgba(200,16,46,.1);border:1px solid rgba(200,16,46,.3);color:var(--red);text-decoration:none;text-align:center;transition:all .25s;margin-bottom:10px;}
.ppv-modal-link:hover{background:rgba(200,16,46,.2);color:#fff;}
.ppv-modal-note{font-family:var(--fc);font-size:12px;letter-spacing:1.5px;color:rgba(255,255,255,.3);text-align:center;margin-top:8px;}

/* ── SPONSORS ── */
#sponsors{background:var(--dark);}
.sp-bg{background-image:url('https://scontent-atl3-3.xx.fbcdn.net/v/t39.30808-6/498635473_122120156816835318_7407636166361306628_n.jpg?_nc_cat=109&ccb=1-7&_nc_sid=dd6889&_nc_ohc=sWLY2-95RcQQ7kNvwH4l830&_nc_oc=AdoddpMSgi3I-W97th9IRvMhQQwbzvy9Djkr-A_H8HCrIoyH-zZwendu6u60mC8x5hKbwVjZlb47yLsysocWD9m2&_nc_zt=23&_nc_ht=scontent-atl3-3.xx&_nc_gid=t049WNLiGlTZpf4s6YOrQA&_nc_ss=7a3a8&oh=00_AfwQa32ZCCc1sE9tUNE-AF2moYaQO5mXYjtqv5BuQxIc1A&oe=69D0A8F3');opacity:.05;}
.sp-intro{max-width:640px;margin-top:18px;font-size:16px;line-height:1.7;color:rgba(255,255,255,.55);}
.sp-tiers{display:grid;grid-template-columns:repeat(3,1fr);gap:2px;margin-top:50px;}
.sp-card{background:rgba(255,255,255,.027);border:1px solid rgba(255,255,255,.065);padding:36px 28px;position:relative;overflow:hidden;transition:background .3s;}
.sp-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;}
.sp-card.brz::before{background:#cd7f32;}
.sp-card.slv::before{background:#aaa;}
.sp-card.gld::before{background:var(--gold);}
.sp-card:hover{background:rgba(255,255,255,.05);}
.sp-tlbl{font-family:var(--fc);font-size:12px;letter-spacing:4px;text-transform:uppercase;margin-bottom:10px;}
.sp-card.brz .sp-tlbl{color:#cd7f32;}
.sp-card.slv .sp-tlbl{color:#aaa;}
.sp-card.gld .sp-tlbl{color:var(--gold);}
.sp-tname{font-family:var(--fd);font-size:42px;color:#fff;line-height:1;margin-bottom:20px;}
.sp-perks{list-style:none;}
.sp-perks li{font-size:14px;color:rgba(255,255,255,.5);padding:9px 0;border-bottom:1px solid rgba(255,255,255,.055);}
.sp-perks li em{font-style:normal;color:var(--gold);margin-right:7px;}
.sp-cta{margin-top:40px;background:rgba(200,16,46,.06);border:1px solid rgba(200,16,46,.2);padding:36px 40px;display:flex;align-items:center;justify-content:space-between;gap:30px;}
.sp-cta h3{font-family:var(--fd);font-size:36px;color:#fff;letter-spacing:2px;margin-bottom:6px;}
.sp-cta p{font-family:var(--fc);font-size:14px;letter-spacing:1.5px;color:rgba(255,255,255,.45);}
.btn-em{font-family:var(--fc);font-size:13px;letter-spacing:2.5px;text-transform:uppercase;font-weight:700;padding:15px 28px;background:transparent;color:var(--gold);border:1px solid rgba(212,175,55,.5);text-decoration:none;display:inline-block;white-space:nowrap;transition:all .3s;clip-path:polygon(7px 0%,100% 0%,calc(100% - 7px) 100%,0 100%);}
.btn-em:hover{background:rgba(212,175,55,.12);border-color:var(--gold);color:#fff;}

/* ── MAP MODAL ── */
.m-back{position:fixed;inset:0;z-index:2000;background:rgba(0,0,0,.82);backdrop-filter:blur(6px);display:flex;align-items:center;justify-content:center;opacity:0;pointer-events:none;transition:opacity .35s ease;}
.m-back.open{opacity:1;pointer-events:all;}
.m-box{background:#111;border:1px solid rgba(200,16,46,.3);width:min(780px,94vw);max-height:90vh;display:flex;flex-direction:column;overflow:hidden;transform:translateY(30px) scale(.97);transition:transform .35s cubic-bezier(.23,1,.32,1);}
.m-back.open .m-box{transform:translateY(0) scale(1);}
.m-head{display:flex;align-items:center;justify-content:space-between;padding:18px 24px;border-bottom:1px solid rgba(255,255,255,.07);flex-shrink:0;}
.m-title{font-family:var(--fd);font-size:22px;color:#fff;letter-spacing:2px;}
.m-sub{font-family:var(--fc);font-size:11px;letter-spacing:2px;text-transform:uppercase;color:rgba(255,255,255,.35);margin-top:2px;}
.m-close{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.12);color:rgba(255,255,255,.7);width:34px;height:34px;border-radius:50%;font-size:18px;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .2s;flex-shrink:0;}
.m-close:hover{background:var(--red);border-color:var(--red);color:#fff;}
.m-box iframe{width:100%;height:420px;border:none;display:block;flex-shrink:0;}
.m-foot{padding:16px 24px;display:flex;gap:12px;align-items:center;border-top:1px solid rgba(255,255,255,.07);flex-shrink:0;}
.m-addr{font-family:var(--fc);font-size:13px;letter-spacing:1px;color:rgba(255,255,255,.45);flex:1;}
.btn-dir{font-family:var(--fc);font-size:12px;letter-spacing:2.5px;text-transform:uppercase;font-weight:700;padding:10px 20px;background:var(--red);color:#fff;text-decoration:none;white-space:nowrap;transition:background .2s;clip-path:polygon(5px 0%,100% 0%,calc(100% - 5px) 100%,0 100%);}
.btn-dir:hover{background:#a80d27;}

/* ── FOOTER ── */
footer{background:#050505;border-top:1px solid rgba(200,16,46,.18);padding:50px 60px 110px;text-align:center;}
.ft-logo{font-family:var(--fd);font-size:52px;color:#fff;letter-spacing:6px;}
.ft-logo em{color:var(--red);font-style:normal;}
.ft-sub{font-family:var(--fc);font-size:15px;letter-spacing:4px;text-transform:uppercase;color:rgba(255,255,255,.35);margin:10px 0 28px;}
.ft-nav{display:flex;gap:24px;justify-content:center;list-style:none;margin-bottom:22px;flex-wrap:wrap;}
.ft-nav a{color:rgba(255,255,255,.45);text-decoration:none;font-family:var(--fc);font-size:14px;letter-spacing:2.5px;text-transform:uppercase;transition:color .2s;}
.ft-nav a:hover{color:var(--red);}
.ft-copy{font-size:13px;color:rgba(255,255,255,.28);}

/* ── MOBILE ── */
@media(max-width:768px){
  #nav{padding:0 20px;}
  .nav-links{display:none;}
  .hbg{display:flex;}
  .wrap{padding:90px 20px 80px;}
  .hero-in{padding:90px 20px 130px;}
  .h-cd{gap:6px;}
  .hcd{padding:12px 14px;min-width:68px;}
  .hcd-n{font-size:38px;}
  .hcd-sep{font-size:30px;}
  .h-ctas{flex-direction:column;align-items:center;}
  #fbar{padding:10px 16px;gap:10px;}
  .fb-ev,.fb-cta{display:none;}
  .fb-n{font-size:22px;}
  .fb-s{font-size:9px;}
  .ev-grid{grid-template-columns:1fr;}
  .ecard-full{flex-direction:column;align-items:flex-start;gap:14px;}
  .fstack{gap:6px;}
  .frow{grid-template-columns:1fr;padding:18px 16px;gap:10px;text-align:center;}
  .fl{flex-direction:column;align-items:center;}
  .fr{flex-direction:column;align-items:center;}
  .fr .finfo{align-items:center;text-align:center;}
  .fph{width:54px;height:54px;}
  .frow.main .fph{width:68px;height:68px;}
  .vsc{padding:4px 0;}
  .tk-row{grid-template-columns:1fr;}
  .prev-grid{grid-template-columns:1fr;}
  .ppv-layout{grid-template-columns:1fr;}
  .sp-tiers{grid-template-columns:1fr;}
  .sp-cta{flex-direction:column;align-items:flex-start;}
  .btn-em{font-size:11px;padding:12px 18px;}
  .m-box iframe{height:260px;}
  .m-foot{flex-direction:column;align-items:flex-start;gap:10px;}
  footer{padding:40px 20px 110px;}
  .ft-nav{gap:14px;}
}
@media(max-width:400px){
  .hcd{min-width:60px;padding:10px;}
  .hcd-n{font-size:32px;}
  .stitle{font-size:46px;}
}
</style>
</head>
<body>

<!-- NAV -->
<nav id="nav">
  <a href="#home" class="nav-logo">RIVAL <em>FC</em></a>
  <ul class="nav-links">
    <li><a href="#home">Home</a></li>
    <li><a href="#event">Event</a></li>
    <li><a href="#fights">Fight Card</a></li>
    <li><a href="#previous">Past Events</a></li>
    <li><a href="#ppv">Watch Live</a></li>
    <li><a href="#sponsors">Sponsors</a></li>
    <li><a href="#tickets" class="nav-cta">Get Tickets</a></li>
  </ul>
  <button class="hbg" id="hbg" aria-label="Menu">
    <span></span><span></span><span></span>
  </button>
</nav>

<!-- MOBILE DRAWER -->
<div class="drw-ov" id="drwOv"></div>
<nav class="drw" id="drw">
  <a href="#home"     class="dl">Home</a>
  <a href="#event"    class="dl">Event</a>
  <a href="#fights"   class="dl">Fight Card</a>
  <a href="#previous" class="dl">Past Events</a>
  <a href="#ppv"      class="dl">Watch Live</a>
  <a href="#sponsors" class="dl">Sponsors</a>
  <a href="#tickets"  class="dl drw-cta">Get Tickets</a>
</nav>

<!-- FLOATING COUNTDOWN BAR -->
<div id="fbar">
  <span class="fb-ev">May 9 &middot; Paducah, KY</span>
  <span class="fb-lbl">Fight Night In</span>
  <div class="fb-units">
    <div class="fb-u"><div class="fb-n" id="fb-d">00</div><div class="fb-s">Days</div></div>
    <span class="fb-col">:</span>
    <div class="fb-u"><div class="fb-n" id="fb-h">00</div><div class="fb-s">Hrs</div></div>
    <span class="fb-col">:</span>
    <div class="fb-u"><div class="fb-n" id="fb-m">00</div><div class="fb-s">Min</div></div>
    <span class="fb-col">:</span>
    <div class="fb-u"><div class="fb-n" id="fb-s">00</div><div class="fb-s">Sec</div></div>
  </div>
  <a href="#tickets" class="fb-cta">Get Tickets &rarr;</a>
</div>

<!-- HERO -->
<section id="home">
  <div class="s-bg hero-bg"></div>
  <div class="s-ov hero-ov"></div>
  <div class="hero-in">
    <p class="h-pre">&#128293; Live MMA Action &mdash; Paducah, Kentucky</p>
    <h1 class="h-logo">RIVAL<span>FC</span></h1>
    <p class="h-tag">Fight Night &nbsp;&middot;&nbsp; May 9, 2026</p>
    <a class="h-venue" href="https://www.google.com/maps/dir/?api=1&destination=6725+US-45,+Paducah,+KY+42001" target="_blank" rel="noopener">
      &#128205; ST. JOHN'S KNIGHTS OF COLUMBUS
    </a>
    <div class="h-cd">
      <div class="hcd"><div class="hcd-n" id="hd">00</div><div class="hcd-l">Days</div></div>
      <span class="hcd-sep">:</span>
      <div class="hcd"><div class="hcd-n" id="hh">00</div><div class="hcd-l">Hours</div></div>
      <span class="hcd-sep">:</span>
      <div class="hcd"><div class="hcd-n" id="hm">00</div><div class="hcd-l">Minutes</div></div>
      <span class="hcd-sep">:</span>
      <div class="hcd"><div class="hcd-n" id="hs">00</div><div class="hcd-l">Seconds</div></div>
    </div>
    <div class="h-ctas">
      <a href="#tickets" class="btn-r">&#127903;&#65039; Get Tickets</a>
      <a href="#fights"  class="btn-g">View Fight Card</a>
    </div>
  </div>
  <div class="h-scroll"><span>Scroll</span><div class="scroll-b"></div></div>
</section>

<!-- EVENT -->
<section id="event">
  <div class="s-bg ev-bg"></div>
  <div class="wrap">
    <div class="rv">
      <span class="eyebrow">Event Information</span>
      <h2 class="stitle">THE<br>VENUE</h2>
      <div class="srule"></div>
    </div>
    <div class="ev-grid">

      <div class="ecard rv" style="transition-delay:.08s">
        <div class="ecard-icon">&#128205;</div>
        <div class="elbl">Venue</div>
        <div class="eval">St. John's Knights<br>of Columbus</div>
        <div class="esub">6725 US-45, Paducah, KY 42001</div>
        <button class="ebtn" onclick="openMap()">&#128506;&#65039; &nbsp;View on Map</button>
      </div>

      <div class="ecard rv" style="transition-delay:.16s">
        <div class="ecard-icon">&#128197;</div>
        <div class="elbl">Date</div>
        <div class="eval">Saturday<br>May 9, 2026</div>
        <div class="esub">All ages welcome</div>
        <a class="ebtn cal" href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=RIVAL+FC+MMA+EVENT&dates=20260509T180000/20260509T230000&details=Live+MMA+Action+at+RIVAL+FC&location=St+Johns+Knights+of+Columbus%2C+6725+US-45%2C+Paducah%2C+KY+42001" target="_blank" rel="noopener">
          &#128198; &nbsp;Add to Google Calendar
        </a>
      </div>

      <div class="ecard rv" style="transition-delay:.24s">
        <div class="ecard-icon">&#128682;</div>
        <div class="elbl">Doors Open</div>
        <div class="eval">6:00 PM</div>
        <div class="esub">Early entry for VIP &amp; Cage-Side</div>
      </div>

      <div class="ecard rv" style="transition-delay:.32s">
        <div class="ecard-icon">&#129354;</div>
        <div class="elbl">First Fight</div>
        <div class="eval">7:00 PM</div>
        <div class="esub">Prelim bouts kick off the night</div>
      </div>

      <div class="ecard ecard-full rv" style="transition-delay:.4s">
        <div>
          <div class="elbl">&#128176; Tickets Starting At</div>
          <div class="eval" style="font-size:38px">$35</div>
          <div class="esub" style="margin-top:6px">General Admission &mdash; Limited seats available</div>
        </div>
        <a href="#tickets" class="btn-r" style="white-space:nowrap">Secure Your Seat &rarr;</a>
      </div>

      <div class="ecard ecard-full rv" style="transition-delay:.48s">
        <div>
          <div class="ecard-icon">&#9993;&#65039;</div>
          <div class="elbl">Questions? Contact Us</div>
          <div class="eval" style="font-size:20px">Paducahbushidomma@gmail.com</div>
          <div class="esub" style="margin-top:6px">Event info, group tickets &amp; sponsorship inquiries</div>
          <a class="ebtn fb" href="https://www.facebook.com/profile.php?id=61577618753919" target="_blank" rel="noopener" style="margin-top:12px">
            &#128

248; &nbsp;Follow us on Facebook
          </a>
        </div>
        <a href="mailto:Paducahbushidomma@gmail.com" class="btn-r" style="white-space:nowrap">Send Email &rarr;</a>
      </div>

    </div>
  </div>
</section>

<!-- FIGHT CARD -->
<section id="fights">
  <div class="s-bg fg-bg"></div>
  <div class="wrap">
    <div class="rv">
      <span class="eyebrow">May 9 &middot; Main Card</span>
      <h2 class="stitle">FIGHT<br>CARD</h2>
      <div class="srule"></div>
    </div>
    <div class="fstack">

      <!-- PRO MAIN EVENT -->
      <div class="frow main rv" style="transition-delay:.08s">
        <div class="fl">
          <div class="fpw">
            <a href="https://www.tapology.com/fightcenter/fighters/217410-charlie-nellinger" target="_blank" rel="noopener">
              <img class="fph" src="https://images.tapology.com/letterbox_images/217410/default/charlie2.jpg?1741456026" alt="Charlie Nellinger">
            </a>
            <span class="ftip">Tapology &#8599;</span>
          </div>
          <div class="finfo">
            <div class="fname">Charlie Nelinger</div>
            <div class="frec">2 &ndash; 2 &ndash; 0</div>
          </div>
        </div>
        <div class="vsc">
          <span class="vsb me">Pro Main Event</span>
          <span class="vsw">VS</span>
          <span class="vswt">Flyweight &middot; 3 Rds</span>
        </div>
        <div class="fr">
          <div class="fpw">
            <a href="https://www.tapology.com/fightcenter/fighters/172179-william-caylor-jr" target="_blank" rel="noopener">
              <img class="fph" src="https://images.tapology.com/letterbox_images/172179/default/Willy_Caylor.jpg?1571457349" alt="Will caylor">
            </a>
            <span class="ftip">Tapology &#8599;</span>
          </div>
          <div class="finfo" style="align-items:flex-end;text-align:right">
            <div class="fname">Will caylor</div>
            <div class="frec">1 &ndash; 2 &ndash; 0</div>
            <div class="ftag">Hometown Favorite</div>
          </div>
        </div>
      </div>

      <!-- CO-MAIN -->
      <div class="frow rv" style="transition-delay:.16s">
        <div class="fl">
          <div class="fpw">
            <a href="https://www.tapology.com/fightcenter/fighters/203484-will-pittman" target="_blank" rel="noopener">
              <img class="fph" src="https://images.tapology.com/letterbox_images/203484/default/pittman.jpg?1698670505" alt="Fighter C">
            </a>
            <span class="ftip">Tapology &#8599;</span>
          </div>
          <div class="finfo">
            <div class="fname">Will Pittman</div>
            <div class="frec">6 &ndash; 9 &ndash; 0</div>
          </div>
        </div>
        <div class="vsc">
          <span class="vsb cm">Co-Main</span>
          <span class="vsw" style="font-size:26px">VS</span>
          <span class="vswt">Featherweight &middot; 3 Rds</span>
        </div>
        <div class="fr">
          <div class="fpw">
            <a href="https://www.tapology.com/fightcenter/fighters" target="_blank" rel="noopener">
              <img class="fph" src="https://images.tapology.com/letterbox_images/318296/default/mf1.jpg?1752845299" alt="Fighter D">
            </a>
            <span class="ftip">Tapology &#8599;</span>
          </div>
          <div class="finfo" style="align-items:flex-end;text-align:right">
            <div class="fname">TBA</div>
            <div class="frec">- &ndash; - &ndash; 0</div>
          </div>
        </div>
      </div>

      <!-- PRELIM 1 -->
      <div class="frow rv" style="transition-delay:.24s">
        <div class="fl">
          <div class="tba-c">?</div>
          <div class="finfo"><div class="fname" style="font-size:26px">TBA</div><div class="frec">&mdash;</div></div>
        </div>
        <div class="vsc">
          <span class="vsb pr">Prelim</span>
          <span class="vsw" style="font-size:24px">VS</span>
          <span class="vswt">Lightweight &middot; 3 Rds</span>
        </div>
        <div class="fr">
          <div class="tba-c">?</div>
          <div class="finfo" style="align-items:flex-end;text-align:right"><div class="fname" style="font-size:26px">TBA</div><div class="frec">&mdash;</div></div>
        </div>
      </div>

      <!-- PRELIM 2 -->
      <div class="frow rv" style="transition-delay:.32s">
        <div class="fl">
          <div class="tba-c">?</div>
          <div class="finfo"><div class="fname" style="font-size:26px">TBA</div><div class="frec">&mdash;</div></div>
        </div>
        <div class="vsc">
          <span class="vsb pr">Prelim</span>
          <span class="vsw" style="font-size:24px">VS</span>
          <span class="vswt">Featherweight &middot; 3 Rds</span>
        </div>
        <div class="fr">
          <div class="tba-c">?</div>
          <div class="finfo" style="align-items:flex-end;text-align:right"><div class="fname" style="font-size:26px">TBA</div><div class="frec">&mdash;</div></div>
        </div>
      </div>

    </div>
    <p class="fnote rv" style="transition-delay:.4s">* Additional bouts announced as the event approaches. Card subject to change.</p>
  </div>
</section>

<!-- TICKETS -->
<section id="tickets">
  <div class="s-bg tk-bg"></div>
  <div class="wrap">
    <div class="rv" style="text-align:center">
      <span class="eyebrow" style="text-align:center">Secure Your Seat</span>
      <h2 class="stitle">TICKETS</h2>
      <div class="srule" style="margin:22px auto 0"></div>
    </div>
    <div class="tk-row">

      <div class="tcard ga rv" style="transition-delay:.08s">
        <div class="ttier">General Admission</div>
        <div class="tprice">$35</div>
        <div class="tper">per person</div>
        <ul class="tfeats">
          <li><em>&#10003;</em> General seating area</li>
          <li><em>&#10003;</em> Full fight card access</li>
          <li><em>&#10003;</em> Venue concessions</li>
        </ul>
        <a href="https://buy.stripe.com/test_3cIaEQeKOexIbg22Q3gMw00" target="_blank" class="tbtn ga">Buy GA Ticket</a>
      </div>

      <div class="tcard vip rv" style="transition-delay:.16s">
        <div class="ttier">VIP</div>
        <div class="tprice">$45</div>
        <div class="tper">per person</div>
        <ul class="tfeats">
          <li><em>&#10003;</em> Reserved VIP seating</li>
          <li><em>&#10003;</em> Priority entry</li>
          <li><em>&#10003;</em> Exclusive lounge access</li>
          <li><em>&#10003;</em> Full fight card access</li>
        </ul>
        <a href="https://buy.stripe.com/YOUR_VIP_LINK" target="_blank" class="tbtn vip">Buy VIP Ticket</a>
      </div>

      <div class="tcard cage rv" style="transition-delay:.24s">
        <div class="ttier">Cage-Side</div>
        <div class="tprice">$500</div>
        <div class="tper">per person</div>
        <ul class="tfeats">
          <li><em>&#10003;</em> Front row cage access</li>
          <li><em>&#10003;</em> VIP entry &amp; lounge</li>
          <li><em>&#10003;</em> Exclusive fighter access</li>
          <li><em>&#10003;</em> Commemorative package</li>
          <li><em>&#10003;</em> Premium experience</li>
        </ul>
        <a href="https://buy.stripe.com/YOUR_CAGE_LINK" target="_blank" class="tbtn cage">Buy Cage-Side</a>
      </div>

    </div>
    <div class="urgency rv" style="transition-delay:.32s">&#9888;&#65039; <strong>LIMITED AVAILABILITY</strong> &mdash; Cage-Side &amp; VIP seats are selling fast.</div>
  </div>
</section>

<!-- PREVIOUS EVENT -->
<section id="previous">
  <div class="s-bg prev-bg"></div>
  <div class="wrap">
    <div class="rv">
      <span class="eyebrow">Catch Up On The Action</span>
      <h2 class="stitle">PREVIOUS<br>EVENT</h2>
      <div class="srule"></div>
    </div>
    <div class="prev-grid">
      <div class="prev-embed rv" style="transition-delay:.08s">
        <iframe src="https://www.youtube.com/embed/nIi4hmJXC1E" title="RIVAL FC Previous Event" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen loading="lazy"></iframe>
      </div>
      <div class="prev-side rv" style="transition-delay:.16s">
        <div class="prev-ic">
          <div class="prev-ic-lbl">&#127902; Latest Fight Film</div>
          <div class="prev-ic-val">RIVAL FC</div>
          <div class="prev-ic-sub">Watch our most recent full event &mdash; relive every round of the action.</div>
        </div>
        <div class="prev-ic">
          <div class="prev-ic-lbl">&#128250; Full Archive</div>
          <div class="prev-ic-val">YouTube Channel</div>
          <div class="prev-ic-sub">Every RIVAL FC event lives on our channel. Subscribe so you never miss a fight.</div>
        </div>
        <a href="https://www.youtube.com/@Rival-FC" target="_blank" rel="noopener" class="btn-yt">
          &#9654;&#65039; &nbsp;Watch on YouTube
        </a>
      </div>
    </div>
  </div>
</section>

<!-- PPV / WATCH LIVE -->
<section id="ppv">
  <div class="s-bg ppv-bg"></div>
  <div class="wrap">
    <div class="rv">
      <span class="eyebrow">Can't Make It In Person?</span>
      <h2 class="stitle">WATCH<br>LIVE</h2>
      <div class="srule"></div>
    </div>
    <div class="ppv-layout">

      <!-- Stream window -->
      <div class="rv" style="transition-delay:.08s">
        <div class="ppv-screen">
          <div class="ppv-placeholder">
            <div class="ppv-ph-icon">&#128250;</div>
            <div class="ppv-ph-txt">LIVESTREAM<br>COMING SOON</div>
            <div class="ppv-ph-sub">Stream unlocks after purchase &middot; May 9, 7 PM CT</div>
          </div>
          <!--
            TO ACTIVATE ON FIGHT NIGHT:
            1. Delete the ppv-placeholder div above.
            2. Paste your Vimeo private embed iframe here.
            Example:
            <iframe src="https://player.vimeo.com/video/YOUR_VIDEO_ID?badge=0&autopause=0&player_id=0&app_id=58479"
              frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen
              title="RIVAL FC May 9 Live"></iframe>
          -->
        </div>
        <div class="ppv-info-cards" style="margin-top:16px">
          <div class="ppv-ic">
            <div class="ppv-ic-lbl">&#128197; Stream Date</div>
            <div class="ppv-ic-val">Saturday, May 9</div>
            <div class="ppv-ic-sub">Fights start 7:00 PM Central Time</div>
          </div>
          <div class="ppv-ic">
            <div class="ppv-ic-lbl">&#128225; Platform</div>
            <div class="ppv-ic-val">Vimeo Premium</div>
            <div class="ppv-ic-sub">Password-protected &mdash; your access code arrives by email after purchase</div>
          </div>
        </div>
      </div>

      <!-- Purchase panel -->
      <div class="rv" style="transition-delay:.16s">
        <div class="ppv-price-card">
          <div class="ppv-price-label">&#127894;&#65039; PPV Access Pass</div>
          <div class="ppv-price-amount">$25</div>
          <div class="ppv-price-per">one-time &middot; watch from anywhere</div>
          <ul class="ppv-features">
            <li><em>&#10003;</em> Full fight card &mdash; all bouts live</li>
            <li><em>&#10003;</em> Prelims + Main Card included</li>
            <li><em>&#10003;</em> HD stream via Vimeo Premium</li>
            <li><em>&#10003;</em> Access code emailed instantly</li>
            <li><em>&#10003;</em> Watch on phone, tablet or TV</li>
            <li><em>&#10003;</em> No subscription required</li>
          </ul>
          <!-- Replace YOUR_PPV_STRIPE_LINK with your Stripe payment link for a $15 PPV product -->
          <a href="https://buy.stripe.com/YOUR_PPV_STRIPE_LINK" target="_blank" rel="noopener" class="btn-ppv" onclick="showPPVConfirm(event)">
            &#127894;&#65039; &nbsp;Buy PPV Access &mdash; $25
          </a>
        </div>
        <div class="ppv-note" style="margin-top:16px">
          <strong>How it works:</strong> Purchase below via Stripe. After checkout you'll receive an email with a private Vimeo link and password. On fight night, return here or visit that link to watch. Questions? Email <a href="mailto:Paducahbushidomma@gmail.com">Paducahbushidomma@gmail.com</a>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- PPV CONFIRM MODAL -->
<div class="ppv-modal-back" id="ppvModal">
  <div class="ppv-modal">
    <button class="ppv-modal-close" id="ppvModalClose">&#10005;</button>
    <div class="ppv-modal-icon">&#127381;</div>
    <div class="ppv-modal-title">ALMOST THERE!</div>
    <div class="ppv-modal-body">
      You're being taken to our secure checkout. After payment, your private stream link and password will be emailed to you within minutes. Keep that email &mdash; it's your ticket in on fight night.
    </div>
    <a href="https://buy.stripe.com/YOUR_PPV_STRIPE_LINK" target="_blank" rel="noopener" class="ppv-modal-link" onclick="closePPVModal()">
      Continue to Secure Checkout &rarr;
    </a>
    <p class="ppv-modal-note">Powered by Stripe &middot; 256-bit encrypted &middot; Instant email delivery</p>
  </div>
</div>

<!-- SPONSORS -->
<section id="sponsors">
  <div class="s-bg sp-bg"></div>
  <div class="wrap">
    <div class="rv">
      <span class="eyebrow">Partner With Us</span>
      <h2 class="stitle">SPONSORSHIP<br>OPPORTUNITIES</h2>
      <div class="srule"></div>
      <p class="sp-intro">Put your brand in front of a passionate fight-night crowd. RIVAL FC offers flexible packages that get your name on the cage, on our screens, and in front of every fan in the building.</p>
    </div>
    <div class="sp-tiers">
      <div class="sp-card brz rv" style="transition-delay:.08s">
        <div class="sp-tlbl">Bronze</div>
        <div class="sp-tname">Corner<br>Sponsor</div>
        <ul class="sp-perks">
          <li><em>&#10003;</em> Logo on event banner</li>
          <li><em>&#10003;</em> Social media mention</li>
          <li><em>&#10003;</em> 2 complimentary GA tickets</li>
          <li><em>&#10003;</em> Ring announcer shoutout</li>
        </ul>
      </div>
      <div class="sp-card slv rv" style="transition-delay:.16s">
        <div class="sp-tlbl">Silver</div>
        <div class="sp-tname">Card<br>Sponsor</div>
        <ul class="sp-perks">
	  <li><em>&#10003;</em> All Bronze benefits</li>
          <li><em>&#10003;</em> Logo on banner &amp; cage</li>
          <li><em>&#10003;</em> Featured social media post</li>
          <li><em>&#10003;</em> 4 complimentary VIP tickets</li>
          <li><em>&#10003;</em> Ring announcer shoutout</li>
          <li><em>&#10003;</em> Logo on event merch</li>
	  <li><em>&#10003;</em> PPV advertisment time-slots</li>
        </ul>
      </div>
      <div class="sp-card gld rv" style="transition-delay:.24s">
        <div class="sp-tlbl">Gold</div>
        <div class="sp-tname">Title<br>Sponsor</div>
        <ul class="sp-perks">
  	  <li><em>&#10003;</em> All Bronze and Silver benefits</li>
          <li><em>&#10003;</em> Promotional space on RIVALFC website</li>
          <li><em>&#10003;</em> Premium cage placement</li>
          <li><em>&#10003;</em> complimentary VIP table </li>
          <li><em>&#10003;</em> Dedicated social campaign</li>
          <li><em>&#10003;</em> Logo on all promotional materials</li>
          <li><em>&#10003;</em> Rival fc presented by "your buisness" </li>
        </ul>
      </div>
    </div>
    <div class="sp-cta rv" style="transition-delay:.32s">
      <div>
        <h3>READY TO GET INVOLVED?</h3>
        <p>Reach out directly to discuss custom packages and pricing.</p>
      </div>
      <a href="mailto:Paducahbushidomma@gmail.com" class="btn-em">&#9993;&#65039; &nbsp;Paducahbushidomma@gmail.com</a>
    </div>
  </div>
</section>

<!-- MAP MODAL -->
<div class="m-back" id="mBack">
  <div class="m-box">
    <div class="m-head">
      <div>
        <div class="m-title">RIVAL FC &mdash; EVENT VENUE</div>
        <div class="m-sub">St. John's Knights of Columbus &middot; Paducah, KY</div>
      </div>
      <button class="m-close" id="mClose">&#10005;</button>
    </div>
    <iframe id="mFrame" src="" data-src="https://maps.google.com/maps?q=6725+US-45,+Paducah,+KY+42001&output=embed" allowfullscreen loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
    <div class="m-foot">
      <div class="m-addr">&#128205; 6725 US-45, Paducah, KY 42001</div>
      <a class="btn-dir" href="https://www.google.com/maps/dir/?api=1&destination=6725+US-45,+Paducah,+KY+42001" target="_blank" rel="noopener">Get Directions &rarr;</a>
    </div>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <div class="ft-logo">RIVAL <em>FC</em></div>
  <p class="ft-sub">May 9, 2026 &middot; Paducah, Kentucky</p>
  <ul class="ft-nav">
    <li><a href="#home">Home</a></li>
    <li><a href="#event">Event</a></li>
    <li><a href="#fights">Fight Card</a></li>
    <li><a href="#previous">Past Events</a></li>
    <li><a href="#ppv">Watch Live</a></li>
    <li><a href="#sponsors">Sponsors</a></li>
    <li><a href="#tickets">Tickets</a></li>
  </ul>
  <p class="ft-copy">&copy; @BushidoMA &mdash; All Rights Reserved.</p>
</footer>

<script>
/* HAMBURGER */
var hbg=document.getElementById('hbg'),drw=document.getElementById('drw'),drwOv=document.getElementById('drwOv');
function openDrw(){hbg.classList.add('open');drw.classList.add('open');drwOv.classList.add('open');document.body.style.overflow='hidden';}
function closeDrw(){hbg.classList.remove('open');drw.classList.remove('open');drwOv.classList.remove('open');document.body.style.overflow='';}
hbg.addEventListener('click',function(){drw.classList.contains('open')?closeDrw():openDrw();});
drwOv.addEventListener('click',closeDrw);
document.querySelectorAll('.dl').forEach(function(a){a.addEventListener('click',closeDrw);});

/* MAP MODAL */
var mBack=document.getElementById('mBack'),mFrame=document.getElementById('mFrame'),mClose=document.getElementById('mClose');
function openMap(){if(!mFrame.getAttribute('src')){mFrame.setAttribute('src',mFrame.dataset.src);}mBack.classList.add('open');document.body.style.overflow='hidden';}
function closeMap(){mBack.classList.remove('open');document.body.style.overflow='';}
mClose.addEventListener('click',closeMap);
mBack.addEventListener('click',function(e){if(e.target===mBack)closeMap();});

/* PPV MODAL */
var ppvModal=document.getElementById('ppvModal'),ppvModalClose=document.getElementById('ppvModalClose');
function showPPVConfirm(e){e.preventDefault();ppvModal.classList.add('open');document.body.style.overflow='hidden';}
function closePPVModal(){ppvModal.classList.remove('open');document.body.style.overflow='';}
ppvModalClose.addEventListener('click',closePPVModal);
ppvModal.addEventListener('click',function(e){if(e.target===ppvModal)closePPVModal();});

/* ESCAPE */
document.addEventListener('keydown',function(e){if(e.key==='Escape'){closeDrw();closeMap();closePPVModal();}});

/* COUNTDOWN */
var EV=new Date('May 9, 2026 19:00:00').getTime();
function pad(n){return String(n).padStart(2,'0');}
function tick(){
  var diff=EV-Date.now();
  if(diff<=0)return;
  var d=Math.floor(diff/86400000),h=Math.floor((diff%86400000)/3600000),m=Math.floor((diff%3600000)/60000),s=Math.floor((diff%60000)/1000);
  document.getElementById('hd').textContent=pad(d);
  document.getElementById('hh').textContent=pad(h);
  document.getElementById('hm').textContent=pad(m);
  document.getElementById('hs').textContent=pad(s);
  document.getElementById('fb-d').textContent=pad(d);
  document.getElementById('fb-h').textContent=pad(h);
  document.getElementById('fb-m').textContent=pad(m);
  document.getElementById('fb-s').textContent=pad(s);
}
setInterval(tick,1000);tick();

/* FLOATING BAR */
var heroSec=document.getElementById('home'),fbar=document.getElementById('fbar');
window.addEventListener('scroll',function(){fbar.classList.toggle('show',heroSec.getBoundingClientRect().bottom<0);},{passive:true});

/* NAV SHRINK */
var mainNav=document.getElementById('nav');
window.addEventListener('scroll',function(){mainNav.classList.toggle('scrolled',window.scrollY>60);},{passive:true});

/* SCROLL REVEAL */
var rvEls=document.querySelectorAll('.rv');
var obs=new IntersectionObserver(function(entries){entries.forEach(function(e){if(e.isIntersecting)e.target.classList.add('on');});},{threshold:0.1});
rvEls.forEach(function(el){obs.observe(el);});
</script>
</body>
</html>