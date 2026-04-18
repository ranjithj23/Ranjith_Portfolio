# Ranjith_Portfolio
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Ranjith J — Digital Marketer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,400&display=swap" rel="stylesheet"/>
<style>
/* ===== CSS VARIABLES ===== */
:root{
  --bg:#07071a;
  --indigo:#1a1033;
  --pink:#ff2d78;
  --cyan:#00e5ff;
  --amber:#ffb703;
  --white:#f0f0ff;
  --muted:#8888aa;
  --card:#0f0f28;
  --card2:#13133a;
  --border:rgba(255,255,255,0.07);
  --font-head:'Syne',sans-serif;
  --font-body:'DM Sans',sans-serif;
  --glow-pink:0 0 20px rgba(255,45,120,0.5);
  --glow-cyan:0 0 20px rgba(0,229,255,0.5);
  --glow-amber:0 0 20px rgba(255,183,3,0.4);
}

/* ===== RESET ===== */
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{
  font-family:var(--font-body);
  background:var(--bg);
  color:var(--white);
  overflow-x:hidden;
  cursor:none;
}

/* ===== NOISE OVERLAY ===== */
body::before{
  content:'';
  position:fixed;inset:0;
  background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
  pointer-events:none;z-index:9999;opacity:.4;
}

/* ===== SCROLLBAR ===== */
::-webkit-scrollbar{width:5px;}
::-webkit-scrollbar-track{background:var(--bg);}
::-webkit-scrollbar-thumb{background:linear-gradient(var(--pink),var(--cyan));border-radius:3px;}

/* ===== CUSTOM CURSOR ===== */
#cursor-dot{
  position:fixed;width:8px;height:8px;
  background:var(--cyan);border-radius:50%;
  pointer-events:none;z-index:99999;
  transform:translate(-50%,-50%);
  box-shadow:0 0 10px var(--cyan),0 0 20px var(--cyan);
  transition:background .2s;
}
#cursor-ring{
  position:fixed;width:32px;height:32px;
  border:1.5px solid rgba(0,229,255,0.5);
  border-radius:50%;pointer-events:none;z-index:99998;
  transform:translate(-50%,-50%);
  transition:transform .12s ease,width .2s,height .2s,border-color .2s;
}

/* ===== PARTICLE CANVAS ===== */
#particle-canvas{
  position:fixed;inset:0;z-index:0;
  pointer-events:none;
}

/* ===== LOADER ===== */
#loader{
  position:fixed;inset:0;z-index:99997;
  background:var(--bg);
  display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  gap:28px;
  transition:opacity .8s ease, visibility .8s ease;
}
#loader.hidden{opacity:0;visibility:hidden;}
.loader-initials{
  font-family:var(--font-head);
  font-size:clamp(60px,10vw,100px);
  font-weight:800;
  background:linear-gradient(135deg,var(--pink),var(--cyan),var(--amber));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  animation:loaderPulse 1.4s ease-in-out infinite alternate;
}
@keyframes loaderPulse{
  from{filter:brightness(1);}
  to{filter:brightness(1.4);}
}
.loader-bar-wrap{
  width:220px;height:3px;
  background:rgba(255,255,255,0.08);
  border-radius:99px;overflow:hidden;
}
.loader-bar{
  height:100%;width:0;
  background:linear-gradient(90deg,var(--pink),var(--cyan),var(--amber));
  border-radius:99px;
  animation:loadFill 2s ease forwards;
}
@keyframes loadFill{to{width:100%;}}
.loader-text{
  font-size:13px;letter-spacing:3px;
  color:var(--muted);text-transform:uppercase;
}

/* ===== NAVBAR ===== */
nav{
  position:fixed;top:0;left:0;right:0;z-index:1000;
  padding:0 5%;
  height:70px;
  display:flex;align-items:center;justify-content:space-between;
  background:rgba(7,7,26,0.6);
  backdrop-filter:blur(20px);
  border-bottom:1px solid var(--border);
  transform:translateY(-100%);
  animation:slideDown .8s .2s ease forwards;
}
@keyframes slideDown{to{transform:translateY(0);}}
.nav-logo{
  font-family:var(--font-head);font-weight:800;font-size:1.25rem;
  background:linear-gradient(90deg,var(--pink),var(--cyan));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  text-decoration:none;
}
.nav-links{display:flex;gap:32px;list-style:none;}
.nav-links a{
  font-size:.875rem;font-weight:500;letter-spacing:.5px;
  color:var(--muted);text-decoration:none;
  position:relative;transition:color .2s;
  text-transform:uppercase;font-size:12px;letter-spacing:1.5px;
}
.nav-links a::after{
  content:'';position:absolute;bottom:-4px;left:0;right:0;
  height:1.5px;background:linear-gradient(90deg,var(--pink),var(--cyan));
  transform:scaleX(0);transform-origin:left;transition:transform .3s ease;
}
.nav-links a:hover{color:var(--white);}
.nav-links a:hover::after{transform:scaleX(1);}
.hamburger{display:none;flex-direction:column;gap:5px;cursor:none;background:none;border:none;}
.hamburger span{display:block;width:24px;height:2px;background:var(--white);transition:.3s;}

/* ===== SECTIONS BASE ===== */
section{position:relative;z-index:1;padding:110px 8% 80px;}
.section-label{
  font-size:11px;letter-spacing:3px;text-transform:uppercase;
  color:var(--pink);margin-bottom:12px;font-weight:600;
}
.section-title{
  font-family:var(--font-head);font-size:clamp(32px,5vw,52px);
  font-weight:800;line-height:1.1;margin-bottom:48px;
  color:var(--white);
}
.section-title span{
  background:linear-gradient(135deg,var(--pink),var(--cyan));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}

/* ===== HERO ===== */
#hero{
  min-height:100vh;
  display:grid;grid-template-columns:1fr 1fr;gap:60px;
  align-items:center;
  padding:120px 8% 80px;
}
.hero-left{}
.avail-badge{
  display:inline-flex;align-items:center;gap:8px;
  background:rgba(0,229,255,0.08);border:1px solid rgba(0,229,255,0.2);
  border-radius:99px;padding:6px 16px;margin-bottom:28px;
  font-size:12px;letter-spacing:1px;color:var(--cyan);font-weight:500;
  animation:fadeUp .6s .5s ease both;
}
.avail-badge .dot{
  width:7px;height:7px;border-radius:50%;background:var(--cyan);
  animation:blink 1.5s ease-in-out infinite;
}
@keyframes blink{0%,100%{opacity:1;}50%{opacity:0.2;}}
.hero-name{
  font-family:var(--font-head);
  font-size:clamp(48px,7vw,88px);
  font-weight:800;line-height:1;
  background:linear-gradient(90deg,#fff 0%,var(--pink) 30%,var(--cyan) 60%,var(--amber) 90%,#fff 100%);
  background-size:300% auto;
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  animation:shimmerText 5s linear infinite, fadeUp .8s .3s ease both;
}
@keyframes shimmerText{
  0%{background-position:0% center;}
  100%{background-position:300% center;}
}
.hero-role{
  font-size:clamp(16px,2.5vw,22px);color:var(--muted);
  margin:18px 0 36px;font-weight:300;letter-spacing:.5px;
  animation:fadeUp .7s .6s ease both;
}
.hero-role span{color:var(--amber);font-weight:500;}
.hero-btns{
  display:flex;flex-wrap:wrap;gap:16px;
  animation:fadeUp .7s .8s ease both;
}
.btn-primary{
  display:inline-flex;align-items:center;gap:8px;
  background:linear-gradient(135deg,var(--pink),#c0006b);
  color:#fff;text-decoration:none;font-weight:600;font-size:.875rem;
  padding:14px 28px;border-radius:8px;border:none;cursor:none;
  box-shadow:var(--glow-pink);transition:transform .2s,box-shadow .2s;
  letter-spacing:.3px;
}
.btn-primary:hover{transform:translateY(-3px);box-shadow:0 0 30px rgba(255,45,120,0.7);}
.btn-outline{
  display:inline-flex;align-items:center;gap:8px;
  background:transparent;color:var(--cyan);
  border:1.5px solid rgba(0,229,255,0.4);
  text-decoration:none;font-weight:600;font-size:.875rem;
  padding:13px 28px;border-radius:8px;cursor:none;
  transition:transform .2s,background .2s,box-shadow .2s;letter-spacing:.3px;
}
.btn-outline:hover{
  background:rgba(0,229,255,0.08);transform:translateY(-3px);
  box-shadow:var(--glow-cyan);
}

/* ===== HERO RIGHT — 3D CARD ===== */
.hero-right{
  display:flex;align-items:center;justify-content:center;
  position:relative;
  animation:fadeUp .8s .4s ease both;
}
.hero-card-wrap{
  position:relative;
  animation:float3d 6s ease-in-out infinite;
}
@keyframes float3d{
  0%,100%{transform:translateY(0) rotateY(0deg) rotateX(0deg);}
  25%{transform:translateY(-15px) rotateY(5deg) rotateX(2deg);}
  50%{transform:translateY(-8px) rotateY(-3deg) rotateX(-2deg);}
  75%{transform:translateY(-18px) rotateY(2deg) rotateX(3deg);}
}
.hero-orb{
  position:absolute;top:50%;left:50%;
  transform:translate(-50%,-50%);
  width:260px;height:260px;border-radius:50%;
  background:radial-gradient(circle,rgba(255,45,120,0.3) 0%,rgba(0,229,255,0.1) 50%,transparent 70%);
  filter:blur(30px);animation:orbPulse 4s ease-in-out infinite;
}
@keyframes orbPulse{
  0%,100%{transform:translate(-50%,-50%) scale(1);}
  50%{transform:translate(-50%,-50%) scale(1.2);}
}
.spin-ring{
  position:absolute;top:50%;left:50%;
  width:280px;height:280px;
  transform:translate(-50%,-50%);
  border:2px dashed rgba(0,229,255,0.3);
  border-radius:50%;animation:spinRing 15s linear infinite;
}
.spin-ring2{
  position:absolute;top:50%;left:50%;
  width:310px;height:310px;
  transform:translate(-50%,-50%);
  border:1px dashed rgba(255,45,120,0.2);
  border-radius:50%;animation:spinRing 22s linear infinite reverse;
}
@keyframes spinRing{to{transform:translate(-50%,-50%) rotate(360deg);}}
.hero-card{
  width:280px;padding:32px 28px;
  background:var(--card2);
  border:1px solid rgba(255,255,255,0.1);
  border-radius:20px;
  backdrop-filter:blur(20px);
  position:relative;z-index:2;
  box-shadow:0 30px 80px rgba(0,0,0,0.5),inset 0 1px 0 rgba(255,255,255,0.1);
}
.card-avatar{
  width:72px;height:72px;border-radius:16px;
  background:linear-gradient(135deg,var(--pink),var(--cyan));
  display:flex;align-items:center;justify-content:center;
  font-family:var(--font-head);font-size:24px;font-weight:800;
  margin-bottom:16px;
  box-shadow:var(--glow-pink);
}
.card-name{font-family:var(--font-head);font-size:1.1rem;font-weight:700;margin-bottom:4px;}
.card-role{font-size:.8rem;color:var(--muted);margin-bottom:24px;}
.card-stats{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;}
.stat{text-align:center;}
.stat-num{
  font-family:var(--font-head);font-size:1.3rem;font-weight:700;
  background:linear-gradient(135deg,var(--pink),var(--amber));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}
.stat-label{font-size:.65rem;color:var(--muted);margin-top:2px;text-transform:uppercase;letter-spacing:.5px;}
.card-divider{height:1px;background:var(--border);margin:20px 0;}

/* ===== MARQUEE ===== */
.marquee-section{
  padding:20px 0;overflow:hidden;position:relative;z-index:1;
  border-top:1px solid var(--border);border-bottom:1px solid var(--border);
  background:rgba(7,7,26,0.4);
}
.marquee-track{
  display:flex;gap:48px;
  animation:marquee 22s linear infinite;
  width:max-content;
}
.marquee-section:hover .marquee-track{animation-play-state:paused;}
@keyframes marquee{from{transform:translateX(0);}to{transform:translateX(-50%);}}
.marquee-item{
  display:flex;align-items:center;gap:10px;
  font-size:13px;font-weight:500;color:var(--muted);
  white-space:nowrap;letter-spacing:.5px;text-transform:uppercase;
}
.marquee-dot{color:var(--pink);font-size:18px;}

/* ===== SKILLS ===== */
#skills{background:linear-gradient(180deg,var(--bg) 0%,rgba(26,16,51,0.4) 100%);}
.skills-grid{display:grid;grid-template-columns:1fr 1fr;gap:48px;}
.skills-bars{}
.skill-cat{margin-bottom:32px;}
.skill-cat-title{
  font-family:var(--font-head);font-size:.8rem;font-weight:700;
  color:var(--cyan);letter-spacing:2px;text-transform:uppercase;margin-bottom:16px;
}
.skill-item{margin-bottom:16px;}
.skill-header{
  display:flex;justify-content:space-between;
  font-size:.8rem;font-weight:500;margin-bottom:6px;
}
.skill-pct{color:var(--muted);}
.bar-track{
  height:6px;background:rgba(255,255,255,0.06);
  border-radius:99px;overflow:hidden;
}
.bar-fill{
  height:100%;width:0;border-radius:99px;
  background:linear-gradient(90deg,var(--pink),var(--cyan));
  position:relative;transition:width 1.4s cubic-bezier(.25,.8,.25,1);
}
.bar-fill::after{
  content:'';position:absolute;inset:0;
  background:linear-gradient(90deg,transparent,rgba(255,255,255,0.4),transparent);
  transform:translateX(-100%);animation:shimmerBar 2s 1.5s ease forwards;
}
@keyframes shimmerBar{to{transform:translateX(200%);}}
.chips-cloud{padding-top:8px;}
.chips-title{
  font-family:var(--font-head);font-size:.8rem;font-weight:700;
  color:var(--amber);letter-spacing:2px;text-transform:uppercase;margin-bottom:20px;
}
.chips-wrap{display:flex;flex-wrap:wrap;gap:10px;}
.chip{
  padding:6px 14px;border-radius:99px;
  font-size:.75rem;font-weight:500;letter-spacing:.3px;
  border:1px solid rgba(255,255,255,0.1);
  background:rgba(255,255,255,0.04);
  color:var(--muted);cursor:default;
  transition:transform .25s,color .25s,border-color .25s,box-shadow .25s;
}
.chip:hover{
  transform:translateY(-4px);color:var(--white);
  border-color:rgba(0,229,255,0.4);box-shadow:var(--glow-cyan);
}
.chip.pink:hover{border-color:rgba(255,45,120,0.4);box-shadow:var(--glow-pink);color:var(--pink);}
.chip.amber:hover{border-color:rgba(255,183,3,0.4);box-shadow:var(--glow-amber);color:var(--amber);}

/* ===== EXPERIENCE / TIMELINE ===== */
#experience{}
.timeline{position:relative;padding-left:32px;}
.timeline::before{
  content:'';position:absolute;left:0;top:0;bottom:0;width:2px;
  background:linear-gradient(180deg,var(--pink),var(--cyan),var(--amber));
  border-radius:2px;
}
.tl-item{
  position:relative;margin-bottom:48px;
  opacity:0;transform:translateX(-30px);
  transition:opacity .7s ease,transform .7s ease;
}
.tl-item.visible{opacity:1;transform:translateX(0);}
.tl-dot{
  position:absolute;left:-39px;top:18px;
  width:14px;height:14px;border-radius:50%;
  background:linear-gradient(135deg,var(--pink),var(--cyan));
  border:2px solid var(--bg);
  box-shadow:0 0 12px var(--pink);
}
.exp-card{
  background:var(--card);
  border:1px solid var(--border);border-radius:16px;
  padding:28px 28px 24px;
  transition:transform .3s,box-shadow .3s;
}
.exp-card:hover{
  transform:translateX(8px);
  box-shadow:0 8px 40px rgba(255,45,120,0.15);
}
.exp-header{display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:12px;margin-bottom:8px;}
.exp-title{font-family:var(--font-head);font-size:1.1rem;font-weight:700;}
.exp-meta{font-size:.8rem;color:var(--muted);margin-bottom:16px;}
.exp-company{color:var(--cyan);font-weight:500;}
.exp-date{
  font-size:.75rem;color:var(--amber);font-weight:500;
  background:rgba(255,183,3,0.1);border:1px solid rgba(255,183,3,0.2);
  padding:4px 12px;border-radius:99px;white-space:nowrap;
}
.exp-type-badge{
  font-size:.7rem;font-weight:700;letter-spacing:1px;text-transform:uppercase;
  padding:3px 10px;border-radius:99px;
  background:rgba(255,45,120,0.12);border:1px solid rgba(255,45,120,0.3);
  color:var(--pink);margin-left:10px;
}
.exp-list{list-style:none;display:flex;flex-direction:column;gap:8px;margin-bottom:16px;}
.exp-list li{
  font-size:.85rem;color:var(--muted);line-height:1.6;padding-left:16px;position:relative;
}
.exp-list li::before{
  content:'▸';position:absolute;left:0;color:var(--cyan);font-size:.7rem;top:2px;
}
.badge-chips{display:flex;flex-wrap:wrap;gap:8px;}
.badge{
  font-size:.7rem;font-weight:600;padding:3px 10px;border-radius:6px;
  background:rgba(0,229,255,0.08);color:var(--cyan);
  border:1px solid rgba(0,229,255,0.15);
}

/* ===== PROJECTS ===== */
#projects{}
.projects-grid{
  display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
  gap:24px;
}
.proj-card{
  background:var(--card);border:1px solid var(--border);
  border-radius:16px;padding:28px;position:relative;overflow:hidden;
  transition:transform .3s,box-shadow .3s;
  opacity:0;transform:translateY(30px);
  transition:opacity .6s ease,transform .6s ease,box-shadow .3s;
}
.proj-card::before{
  content:'';position:absolute;top:0;left:-100%;right:0;height:2px;
  background:linear-gradient(90deg,transparent,var(--pink),var(--cyan),transparent);
  transition:left .4s ease;
}
.proj-card:hover::before{left:0;}
.proj-card:hover{
  transform:translateY(-8px);
  box-shadow:0 20px 60px rgba(0,0,0,0.4),0 0 30px rgba(0,229,255,0.1);
}
.proj-card.visible{opacity:1;transform:translateY(0);}
.proj-emoji{font-size:2rem;margin-bottom:14px;display:block;}
.proj-name{
  font-family:var(--font-head);font-size:1rem;font-weight:700;
  margin-bottom:10px;color:var(--white);
}
.proj-desc{font-size:.8rem;color:var(--muted);line-height:1.6;margin-bottom:16px;}
.proj-tags{display:flex;flex-wrap:wrap;gap:6px;}
.proj-tag{
  font-size:.7rem;font-weight:500;padding:3px 10px;border-radius:6px;
  background:rgba(255,183,3,0.08);color:var(--amber);
  border:1px solid rgba(255,183,3,0.15);
}

/* ===== EDUCATION ===== */
#education{background:linear-gradient(180deg,rgba(26,16,51,0.3) 0%,var(--bg) 100%);}
.edu-grid{display:grid;grid-template-columns:1fr 1fr;gap:24px;margin-bottom:56px;}
.edu-card{
  background:var(--card);border:1px solid var(--border);
  border-radius:16px;padding:28px;
  transition:transform .3s,box-shadow .3s;
  opacity:0;transform:translateY(20px);
}
.edu-card.visible{opacity:1;transform:translateY(0);transition:opacity .6s,transform .6s;}
.edu-card:hover{
  transform:translateY(-4px);
  box-shadow:0 12px 40px rgba(255,45,120,0.1);
}
.edu-degree{font-family:var(--font-head);font-size:1rem;font-weight:700;margin-bottom:6px;}
.edu-school{font-size:.85rem;color:var(--cyan);margin-bottom:12px;}
.edu-meta{display:flex;gap:12px;flex-wrap:wrap;}
.edu-score{
  font-size:.75rem;font-weight:600;padding:3px 12px;border-radius:99px;
  background:rgba(255,183,3,0.1);color:var(--amber);
  border:1px solid rgba(255,183,3,0.2);
}
.edu-year{font-size:.75rem;color:var(--muted);}

/* ===== CERTIFICATIONS ===== */
.certs-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:16px;}
.cert-card{
  background:var(--card2);border:1px solid var(--border);
  border-radius:12px;padding:20px;
  display:flex;align-items:center;gap:14px;
  transition:transform .25s,border-color .25s;
  opacity:0;transform:translateX(-20px);
}
.cert-card.visible{opacity:1;transform:translateX(0);transition:opacity .5s,transform .5s;}
.cert-card:hover{transform:translateX(6px);border-color:rgba(0,229,255,0.25);}
.cert-icon{
  font-size:1.5rem;width:44px;height:44px;
  background:rgba(0,229,255,0.08);border-radius:10px;
  display:flex;align-items:center;justify-content:center;flex-shrink:0;
}
.cert-name{font-size:.83rem;font-weight:600;margin-bottom:3px;}
.cert-source{font-size:.72rem;color:var(--muted);}

/* ===== LANGUAGES ===== */
.lang-badges{display:flex;gap:16px;flex-wrap:wrap;margin-top:32px;}
.lang-badge{
  display:flex;align-items:center;gap:10px;
  padding:12px 20px;border-radius:12px;
  background:var(--card2);border:1px solid var(--border);
  animation:fadeUp .5s ease both;
}
.lang-flag{font-size:1.5rem;}
.lang-info{}
.lang-name{font-family:var(--font-head);font-size:.9rem;font-weight:700;}
.lang-level{font-size:.72rem;color:var(--cyan);}

/* ===== CONTACT ===== */
#contact{background:linear-gradient(180deg,var(--bg) 0%,rgba(26,16,51,0.5) 100%);}
.contact-inner{display:grid;grid-template-columns:1fr 1fr;gap:60px;align-items:center;}
.contact-cards{display:flex;flex-direction:column;gap:16px;}
.contact-card{
  display:flex;align-items:center;gap:16px;
  background:var(--card);border:1px solid var(--border);
  border-radius:14px;padding:20px 22px;
  transition:transform .3s,box-shadow .3s;
  opacity:0;transform:translateX(-20px);
}
.contact-card.visible{opacity:1;transform:translateX(0);transition:opacity .5s,transform .5s;}
.contact-card:hover{
  transform:translateX(10px);
  box-shadow:0 8px 30px rgba(0,229,255,0.12);
}
.contact-icon{
  width:44px;height:44px;border-radius:10px;
  display:flex;align-items:center;justify-content:center;font-size:1.2rem;
  flex-shrink:0;
}
.contact-icon.pink{background:rgba(255,45,120,0.12);}
.contact-icon.cyan{background:rgba(0,229,255,0.12);}
.contact-icon.amber{background:rgba(255,183,3,0.12);}
.contact-label{font-size:.72rem;color:var(--muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:3px;}
.contact-val{font-size:.88rem;font-weight:500;color:var(--white);}
.contact-val a{color:inherit;text-decoration:none;}
.contact-val a:hover{color:var(--cyan);}
.contact-right{
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  gap:32px;
}
.pulse-avatar{
  position:relative;width:160px;height:160px;
  display:flex;align-items:center;justify-content:center;
}
.pulse-avatar .avatar-inner{
  width:110px;height:110px;border-radius:50%;
  background:linear-gradient(135deg,var(--pink),var(--cyan));
  display:flex;align-items:center;justify-content:center;
  font-family:var(--font-head);font-size:2rem;font-weight:800;
  position:relative;z-index:3;
  box-shadow:var(--glow-pink);
}
.ripple{
  position:absolute;border-radius:50%;
  border:1.5px solid rgba(0,229,255,0.3);
  animation:rippleOut 3s ease-out infinite;
}
.ripple:nth-child(1){width:120px;height:120px;animation-delay:0s;}
.ripple:nth-child(2){width:140px;height:140px;animation-delay:1s;}
.ripple:nth-child(3){width:160px;height:160px;animation-delay:2s;}
@keyframes rippleOut{
  0%{transform:scale(1);opacity:.6;}
  100%{transform:scale(1.8);opacity:0;}
}
.contact-tagline{
  text-align:center;font-size:1rem;color:var(--muted);
  max-width:300px;line-height:1.6;
}
.contact-tagline strong{color:var(--white);}

/* ===== FOOTER ===== */
footer{
  text-align:center;padding:28px;font-size:.78rem;color:var(--muted);
  border-top:1px solid var(--border);position:relative;z-index:1;
}
footer span{color:var(--pink);}

/* ===== SCROLL REVEAL BASE ===== */
.reveal{opacity:0;transform:translateY(40px);transition:opacity .7s ease,transform .7s ease;}
.reveal.visible{opacity:1;transform:translateY(0);}
.reveal-left{opacity:0;transform:translateX(-40px);transition:opacity .7s ease,transform .7s ease;}
.reveal-left.visible{opacity:1;transform:translateX(0);}
.reveal-right{opacity:0;transform:translateX(40px);transition:opacity .7s ease,transform .7s ease;}
.reveal-right.visible{opacity:1;transform:translateX(0);}

/* ===== RESPONSIVE ===== */
@media(max-width:900px){
  #hero{grid-template-columns:1fr;text-align:center;}
  .hero-right{display:none;}
  .hero-btns{justify-content:center;}
  .avail-badge{margin-left:auto;margin-right:auto;}
  .skills-grid{grid-template-columns:1fr;}
  .edu-grid{grid-template-columns:1fr;}
  .contact-inner{grid-template-columns:1fr;}
  .contact-right{display:none;}
  .nav-links{display:none;flex-direction:column;position:fixed;top:70px;left:0;right:0;background:rgba(7,7,26,0.97);padding:24px;gap:20px;}
  .nav-links.open{display:flex;}
  .hamburger{display:flex;}
  section{padding:90px 6% 60px;}
}
@media(max-width:540px){
  .projects-grid{grid-template-columns:1fr;}
  .certs-grid{grid-template-columns:1fr;}
}

/* ===== FADE UP KEYFRAME ===== */
@keyframes fadeUp{
  from{opacity:0;transform:translateY(30px);}
  to{opacity:1;transform:translateY(0);}
}
</style>
</head>
<body>

<!-- CURSOR -->
<div id="cursor-dot"></div>
<div id="cursor-ring"></div>

<!-- PARTICLE CANVAS -->
<canvas id="particle-canvas"></canvas>

<!-- LOADER -->
<div id="loader">
  <div class="loader-initials">RJ</div>
  <div class="loader-bar-wrap">
    <div class="loader-bar"></div>
  </div>
  <div class="loader-text">Initializing Portfolio</div>
</div>

<!-- NAVBAR -->
<nav id="navbar">
  <a href="#hero" class="nav-logo">Ranjith J</a>
  <ul class="nav-links" id="navLinks">
    <li><a href="#skills">Skills</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#education">Education</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <button class="hamburger" id="hamburger" aria-label="Menu">
    <span></span><span></span><span></span>
  </button>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-left">
    <div class="avail-badge">
      <span class="dot"></span>Available for Opportunities
    </div>
    <h1 class="hero-name">Ranjith J</h1>
    <p class="hero-role">
      <span>Digital Marketer</span> — SEO · SEM · Social Media · Paid Ads
    </p>
    <div class="hero-btns">
      <a href="#contact" class="btn-primary">✉ Get In Touch</a>
      <a href="#projects" class="btn-outline">↓ View My Work</a>
    </div>
  </div>
  <div class="hero-right">
    <div class="hero-card-wrap">
      <div class="hero-orb"></div>
      <div class="spin-ring"></div>
      <div class="spin-ring2"></div>
      <div class="hero-card">
        <div class="card-avatar">RJ</div>
        <div class="card-name">Ranjith J</div>
        <div class="card-role">Digital Marketer · Bengaluru, KA</div>
        <div class="card-divider"></div>
        <div class="card-stats">
          <div class="stat">
            <div class="stat-num">100+</div>
            <div class="stat-label">Daily CX</div>
          </div>
          <div class="stat">
            <div class="stat-num">25%</div>
            <div class="stat-label">Lead Boost</div>
          </div>
          <div class="stat">
            <div class="stat-num">40%</div>
            <div class="stat-label">Followers↑</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee-section">
  <div class="marquee-track" id="marqueeTrack">
    <span class="marquee-item"><span class="marquee-dot">✦</span> Digitide Solutions</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> WHY Global Service</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> thiruthanigaiinfracity</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> mmkbites</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> Dental Clinic</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> exodusexpeditions</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> keshavafabrics.com</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> Google Ads Certified</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> HubSpot SEO Pro</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> Meta Ads Manager</span>
    <!-- duplicate for seamless loop -->
    <span class="marquee-item"><span class="marquee-dot">✦</span> Digitide Solutions</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> WHY Global Service</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> thiruthanigaiinfracity</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> mmkbites</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> Dental Clinic</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> exodusexpeditions</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> keshavafabrics.com</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> Google Ads Certified</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> HubSpot SEO Pro</span>
    <span class="marquee-item"><span class="marquee-dot">✦</span> Meta Ads Manager</span>
  </div>
</div>

<!-- SKILLS -->
<section id="skills">
  <div class="reveal">
    <div class="section-label">What I Know</div>
    <h2 class="section-title">Technical <span>Skills</span></h2>
  </div>
  <div class="skills-grid">
    <div class="skills-bars reveal-left">
      <div class="skill-cat">
        <div class="skill-cat-title">SEO &amp; SEM</div>
        <div class="skill-item">
          <div class="skill-header"><span>Keyword Research &amp; Mapping</span><span class="skill-pct">92%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="92"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-header"><span>On-Page / Off-Page SEO</span><span class="skill-pct">90%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="90"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-header"><span>SEMrush / Ubersuggest</span><span class="skill-pct">85%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="85"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-header"><span>Screaming Frog / GSC</span><span class="skill-pct">80%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="80"></div></div>
        </div>
      </div>
      <div class="skill-cat">
        <div class="skill-cat-title">Paid Advertising</div>
        <div class="skill-item">
          <div class="skill-header"><span>Google Ads</span><span class="skill-pct">88%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="88"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-header"><span>Meta Ads Manager</span><span class="skill-pct">86%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="86"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-header"><span>A/B Testing &amp; CRO</span><span class="skill-pct">82%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="82"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-header"><span>Lead Generation</span><span class="skill-pct">84%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="84"></div></div>
        </div>
      </div>
      <div class="skill-cat">
        <div class="skill-cat-title">Analytics &amp; Reporting</div>
        <div class="skill-item">
          <div class="skill-header"><span>Google Analytics 4 (GA4)</span><span class="skill-pct">87%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="87"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-header"><span>Google Tag Manager</span><span class="skill-pct">78%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="78"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-header"><span>Meta Business Suite</span><span class="skill-pct">83%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="83"></div></div>
        </div>
      </div>
      <div class="skill-cat">
        <div class="skill-cat-title">Social Media &amp; Email</div>
        <div class="skill-item">
          <div class="skill-header"><span>Instagram / Facebook / LinkedIn</span><span class="skill-pct">91%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="91"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-header"><span>Buffer / Scheduling</span><span class="skill-pct">80%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="80"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-header"><span>Mailchimp / Email Marketing</span><span class="skill-pct">78%</span></div>
          <div class="bar-track"><div class="bar-fill" data-pct="78"></div></div>
        </div>
      </div>
    </div>
    <div class="chips-cloud reveal-right">
      <div class="chips-title">Tech Stack &amp; Tools</div>
      <div class="chips-wrap">
        <span class="chip">WordPress</span>
        <span class="chip pink">Elementor</span>
        <span class="chip amber">Yoast SEO</span>
        <span class="chip">WooCommerce</span>
        <span class="chip pink">SEMrush</span>
        <span class="chip">Ubersuggest</span>
        <span class="chip amber">Screaming Frog</span>
        <span class="chip">Google Ads</span>
        <span class="chip pink">Meta Ads Manager</span>
        <span class="chip">GA4</span>
        <span class="chip amber">GTM</span>
        <span class="chip">Mailchimp</span>
        <span class="chip pink">Canva</span>
        <span class="chip">Buffer</span>
        <span class="chip amber">ChatGPT</span>
        <span class="chip">Google Gemini</span>
        <span class="chip pink">Claude AI</span>
        <span class="chip">Ahrefs</span>
        <span class="chip amber">Answer the Public</span>
        <span class="chip">HTML</span>
        <span class="chip pink">CSS</span>
        <span class="chip">Contact Form 7</span>
        <span class="chip amber">Google Search Console</span>
        <span class="chip">Co-Pilot</span>
        <span class="chip pink">Duplicate Checker</span>
        <span class="chip">PageSpeed Insights</span>
        <span class="chip amber">XML Sitemaps</span>
        <span class="chip">Schema Markup</span>
        <span class="chip pink">CRM Tools</span>
        <span class="chip">Meta Business Suite</span>
      </div>
    </div>
  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="reveal">
    <div class="section-label">Career Path</div>
    <h2 class="section-title">Work <span>Experience</span></h2>
  </div>
  <div class="timeline">
    <div class="tl-item">
      <div class="tl-dot"></div>
      <div class="exp-card">
        <div class="exp-header">
          <div>
            <span class="exp-title">Customer Care Executive</span>
            <span class="exp-type-badge">Full-Time</span>
          </div>
          <span class="exp-date">Jan 2024 — Present</span>
        </div>
        <div class="exp-meta">
          <span class="exp-company">Digitide Solutions Limited</span> · Bengaluru, Karnataka
        </div>
        <ul class="exp-list">
          <li>Managed 100+ daily customer interactions using CRM tools, generating leads and contributing to business sales growth across service lines.</li>
          <li>Converted inbound queries into sales opportunities through effective communication, achieving consistently high customer satisfaction scores.</li>
          <li>Built strong customer relationships by providing timely, personalised solutions and maintaining detailed interaction records in CRM systems.</li>
        </ul>
        <div class="badge-chips">
          <span class="badge">CRM Tools</span>
          <span class="badge">Lead Generation</span>
          <span class="badge">Customer Satisfaction</span>
          <span class="badge">Sales Conversion</span>
        </div>
      </div>
    </div>
    <div class="tl-item">
      <div class="tl-dot"></div>
      <div class="exp-card">
        <div class="exp-header">
          <div>
            <span class="exp-title">Digital Marketing Intern</span>
            <span class="exp-type-badge" style="background:rgba(0,229,255,0.1);border-color:rgba(0,229,255,0.3);color:var(--cyan);">Internship</span>
          </div>
          <span class="exp-date">Mar 2025 — Sep 2025</span>
        </div>
        <div class="exp-meta">
          <span class="exp-company">WHY Global Service</span> · Chennai, Tamil Nadu
        </div>
        <ul class="exp-list">
          <li>Worked on live projects spanning SEO, SMM, SEM, Email Marketing and Content Marketing to boost brand presence and lead generation.</li>
          <li>Executed SEM campaigns on Google Ads managing a monthly budget of ₹40,000 — achieved a <strong style="color:var(--cyan)">15% reduction in CPC</strong> through A/B testing of ad copies.</li>
          <li>Designed and managed paid social campaigns on Meta Ads Manager targeting specific demographics, resulting in a <strong style="color:var(--pink)">25% increase in lead generation</strong>.</li>
          <li>Built and maintained WordPress websites including theme customisation, plugin configuration, SEO optimisation, and performance tuning using Yoast SEO.</li>
          <li>Managed social profiles on Instagram, Facebook, and LinkedIn; grew combined following by <strong style="color:var(--amber)">40%</strong> through consistent posting, hashtag strategy, and community engagement.</li>
          <li>Analysed campaign performance using Google Analytics 4 and Meta Business Suite; prepared weekly reports with actionable insights for the marketing team.</li>
        </ul>
        <div class="badge-chips">
          <span class="badge">Google Ads</span>
          <span class="badge">Meta Ads</span>
          <span class="badge">SEO</span>
          <span class="badge">GA4</span>
          <span class="badge">WordPress</span>
          <span class="badge">Social Media</span>
          <span class="badge">A/B Testing</span>
          <span class="badge">Email Marketing</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="reveal">
    <div class="section-label">What I've Built</div>
    <h2 class="section-title">Personal <span>Projects</span></h2>
  </div>
  <div class="projects-grid">
    <div class="proj-card">
      <span class="proj-emoji">🌐</span>
      <div class="proj-name">WordPress Digital Marketing Business Website</div>
      <div class="proj-desc">Designed and developed a fully functional digital marketing business website for keshavafabrics.com. Implemented technical SEO best practices including XML sitemaps, robots.txt, schema markup, and page speed optimisation — achieving a 90+ score on Google PageSpeed Insights.</div>
      <div class="proj-tags">
        <span class="proj-tag">WordPress</span>
        <span class="proj-tag">Elementor</span>
        <span class="proj-tag">Yoast SEO</span>
        <span class="proj-tag">Schema Markup</span>
        <span class="proj-tag">PageSpeed</span>
        <span class="proj-tag">Claude AI</span>
      </div>
    </div>
    <div class="proj-card">
      <span class="proj-emoji">✍️</span>
      <div class="proj-name">SEO Content Writing</div>
      <div class="proj-desc">Developed SEO-friendly content for brands including thiruthanigaiinfracity to boost visibility and engagement. Published on Medium. Used advanced AI and SEO tools to research, write, and optimise high-ranking articles with keyword-rich, audience-focused copy.</div>
      <div class="proj-tags">
        <span class="proj-tag">ChatGPT</span>
        <span class="proj-tag">Claude AI</span>
        <span class="proj-tag">Ahrefs</span>
        <span class="proj-tag">Answer the Public</span>
        <span class="proj-tag">Duplicate Checker</span>
        <span class="proj-tag">Medium</span>
      </div>
    </div>
    <div class="proj-card">
      <span class="proj-emoji">📊</span>
      <div class="proj-name">SEO Case Study — Niche Blog</div>
      <div class="proj-desc">Created and managed a personal niche blog — conducted keyword research using Ubersuggest and SEMrush targeting low-competition, high-volume terms. Applied on-page SEO techniques including optimised meta titles, H1–H3 structure, internal linking, and image alt tags.</div>
      <div class="proj-tags">
        <span class="proj-tag">SEMrush</span>
        <span class="proj-tag">Ubersuggest</span>
        <span class="proj-tag">On-Page SEO</span>
        <span class="proj-tag">Meta Tags</span>
        <span class="proj-tag">Internal Linking</span>
      </div>
    </div>
    <div class="proj-card">
      <span class="proj-emoji">🎯</span>
      <div class="proj-name">Meta Ads Mock Campaign — E-Commerce Product Launch</div>
      <div class="proj-desc">Designed a complete Meta Ads strategy for a mock e-commerce product launch including audience segmentation, creative ad design, bidding strategy, and projected ROI analysis. Clients: mmkbites, Dental Clinic &amp; exodusexpeditions. Received distinction grade for strategic depth.</div>
      <div class="proj-tags">
        <span class="proj-tag">Meta Ads Manager</span>
        <span class="proj-tag">Audience Segmentation</span>
        <span class="proj-tag">Ad Creative</span>
        <span class="proj-tag">ROI Analysis</span>
        <span class="proj-tag">CRO</span>
      </div>
    </div>
  </div>
</section>

<!-- EDUCATION & CERTS -->
<section id="education">
  <div class="reveal">
    <div class="section-label">Academic Background</div>
    <h2 class="section-title">Education &amp; <span>Certifications</span></h2>
  </div>
  <div class="edu-grid">
    <div class="edu-card">
      <div class="edu-degree">Bachelor of Computer Science</div>
      <div class="edu-school">Sri Vasavi College, Erode, Tamilnadu</div>
      <div class="edu-meta">
        <span class="edu-score">76.19%</span>
        <span class="edu-year">2019 – 2022</span>
      </div>
    </div>
    <div class="edu-card">
      <div class="edu-degree">Class XII — Maths &amp; Biology</div>
      <div class="edu-school">Govt Boys School, Anthiyur, Tamilnadu</div>
      <div class="edu-meta">
        <span class="edu-score">64.7%</span>
        <span class="edu-year">2017 – 2019</span>
      </div>
    </div>
  </div>

  <div class="reveal" style="margin-bottom:24px;">
    <div class="section-label">Credentials</div>
    <h3 style="font-family:var(--font-head);font-size:1.4rem;font-weight:700;color:var(--white);margin-bottom:28px;">Professional <span style="background:linear-gradient(135deg,var(--pink),var(--cyan));-webkit-background-clip:text;-webkit-text-fill-color:transparent;">Certifications</span></h3>
  </div>
  <div class="certs-grid">
    <div class="cert-card">
      <div class="cert-icon">🎓</div>
      <div>
        <div class="cert-name">Fundamentals of Digital Marketing</div>
        <div class="cert-source">WhyTap · 2025</div>
      </div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">🏆</div>
      <div>
        <div class="cert-name">Google Digital Marketing &amp; Ecommerce</div>
        <div class="cert-source">Coursera · 2026</div>
      </div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">🔍</div>
      <div>
        <div class="cert-name">SEO Professional Certification</div>
        <div class="cert-source">HubSpot · 2026</div>
      </div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">📣</div>
      <div>
        <div class="cert-name">Google Ads Certification</div>
        <div class="cert-source">Coursera · 2026</div>
      </div>
    </div>
  </div>

  <!-- Languages -->
  <div class="reveal" style="margin-top:60px;">
    <div class="section-label">Communication</div>
    <h3 style="font-family:var(--font-head);font-size:1.4rem;font-weight:700;color:var(--white);margin-bottom:8px;">Languages</h3>
  </div>
  <div class="lang-badges">
    <div class="lang-badge" style="animation-delay:.1s;">
      <span class="lang-flag">🇮🇳</span>
      <div class="lang-info">
        <div class="lang-name">Tamil</div>
        <div class="lang-level">Native / Mother Tongue</div>
      </div>
    </div>
    <div class="lang-badge" style="animation-delay:.25s;">
      <span class="lang-flag">🇬🇧</span>
      <div class="lang-info">
        <div class="lang-name">English</div>
        <div class="lang-level">Professional Proficiency</div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="reveal">
    <div class="section-label">Say Hello</div>
    <h2 class="section-title">Get In <span>Touch</span></h2>
  </div>
  <div class="contact-inner">
    <div class="contact-cards">
      <div class="contact-card">
        <div class="contact-icon pink">📧</div>
        <div>
          <div class="contact-label">Email</div>
          <div class="contact-val"><a href="mailto:jranjith2305@gmail.com">jranjith2305@gmail.com</a></div>
        </div>
      </div>
      <div class="contact-card">
        <div class="contact-icon cyan">📞</div>
        <div>
          <div class="contact-label">Phone</div>
          <div class="contact-val"><a href="tel:+917639773496">+91 7639773496</a></div>
        </div>
      </div>
      <div class="contact-card">
        <div class="contact-icon amber">💼</div>
        <div>
          <div class="contact-label">LinkedIn</div>
          <div class="contact-val"><a href="https://linkedin.com/in/jranjith-digital-marketer/" target="_blank">jranjith-digital-marketer</a></div>
        </div>
      </div>
      <div class="contact-card">
        <div class="contact-icon pink">📍</div>
        <div>
          <div class="contact-label">Location</div>
          <div class="contact-val">Bengaluru, Karnataka, India</div>
        </div>
      </div>
      <div class="contact-card">
        <div class="contact-icon cyan">✍️</div>
        <div>
          <div class="contact-label">Medium / Writing</div>
          <div class="contact-val"><a href="https://medium.com/@jranjith2305" target="_blank">medium.com/@jranjith2305</a></div>
        </div>
      </div>
      <div class="contact-card">
        <div class="contact-icon amber">🟢</div>
        <div>
          <div class="contact-label">Availability</div>
          <div class="contact-val">Open to Entry-Level Digital Marketing Roles</div>
        </div>
      </div>
    </div>
    <div class="contact-right">
      <div class="pulse-avatar">
        <div class="ripple"></div>
        <div class="ripple"></div>
        <div class="ripple"></div>
        <div class="avatar-inner">RJ</div>
      </div>
      <div class="contact-tagline">
        <strong>Ready to drive measurable growth</strong> — reach out and let's build something great together.
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  Crafted with <span>♥</span> by Ranjith J · Digital Marketer · Bengaluru, India
</footer>

<script>
/* ============================
   LOADER
============================ */
window.addEventListener('load',()=>{
  setTimeout(()=>{
    document.getElementById('loader').classList.add('hidden');
  },2200);
});

/* ============================
   CUSTOM CURSOR
============================ */
const dot=document.getElementById('cursor-dot');
const ring=document.getElementById('cursor-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{
  mx=e.clientX;my=e.clientY;
  dot.style.left=mx+'px';dot.style.top=my+'px';
});
function animRing(){
  rx+=(mx-rx)*.12;ry+=(my-ry)*.12;
  ring.style.left=rx+'px';ring.style.top=ry+'px';
  requestAnimationFrame(animRing);
}animRing();
document.querySelectorAll('a,button,.chip,.proj-card,.exp-card,.contact-card').forEach(el=>{
  el.addEventListener('mouseenter',()=>{
    ring.style.width='52px';ring.style.height='52px';
    ring.style.borderColor='rgba(255,45,120,0.6)';
  });
  el.addEventListener('mouseleave',()=>{
    ring.style.width='32px';ring.style.height='32px';
    ring.style.borderColor='rgba(0,229,255,0.5)';
  });
});

/* ============================
   PARTICLE CANVAS
============================ */
const canvas=document.getElementById('particle-canvas');
const ctx=canvas.getContext('2d');
let W,H,particles=[];
const COLORS=['#ff2d78','#00e5ff','#ffb703','#a855f7'];
function resize(){
  W=canvas.width=window.innerWidth;
  H=canvas.height=window.innerHeight;
}
resize();window.addEventListener('resize',resize);
class Particle{
  constructor(){this.reset();}
  reset(){
    this.x=Math.random()*W;
    this.y=Math.random()*H;
    this.vx=(Math.random()-.5)*.4;
    this.vy=(Math.random()-.5)*.4;
    this.r=Math.random()*2+.5;
    this.color=COLORS[Math.floor(Math.random()*COLORS.length)];
    this.alpha=Math.random()*.6+.2;
  }
  update(){
    this.x+=this.vx;this.y+=this.vy;
    if(this.x<0||this.x>W||this.y<0||this.y>H)this.reset();
  }
  draw(){
    ctx.beginPath();
    ctx.arc(this.x,this.y,this.r,0,Math.PI*2);
    ctx.fillStyle=this.color;
    ctx.globalAlpha=this.alpha;
    ctx.fill();
    ctx.globalAlpha=1;
  }
}
const N=100;
for(let i=0;i<N;i++)particles.push(new Particle());
function drawLines(){
  for(let i=0;i<particles.length;i++){
    for(let j=i+1;j<particles.length;j++){
      const dx=particles[i].x-particles[j].x;
      const dy=particles[i].y-particles[j].y;
      const dist=Math.sqrt(dx*dx+dy*dy);
      if(dist<130){
        ctx.beginPath();
        ctx.moveTo(particles[i].x,particles[i].y);
        ctx.lineTo(particles[j].x,particles[j].y);
        const alpha=(1-dist/130)*.15;
        ctx.strokeStyle=particles[i].color;
        ctx.globalAlpha=alpha;
        ctx.lineWidth=.6;
        ctx.stroke();
        ctx.globalAlpha=1;
      }
    }
  }
}
function loop(){
  ctx.clearRect(0,0,W,H);
  particles.forEach(p=>{p.update();p.draw();});
  drawLines();
  requestAnimationFrame(loop);
}loop();

/* ============================
   HAMBURGER NAV
============================ */
const ham=document.getElementById('hamburger');
const navLinks=document.getElementById('navLinks');
ham.addEventListener('click',()=>navLinks.classList.toggle('open'));
navLinks.querySelectorAll('a').forEach(a=>a.addEventListener('click',()=>navLinks.classList.remove('open')));

/* ============================
   SCROLL REVEAL
============================ */
const revealObs=new IntersectionObserver((entries)=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.classList.add('visible');
      // stagger children if needed
    }
  });
},{threshold:.12});
document.querySelectorAll('.reveal,.reveal-left,.reveal-right,.tl-item,.proj-card,.edu-card,.cert-card,.contact-card').forEach(el=>{
  revealObs.observe(el);
});

/* ============================
   SKILL BARS (on scroll)
============================ */
const barObs=new IntersectionObserver((entries)=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      const pct=e.target.dataset.pct;
      e.target.style.width=pct+'%';
      barObs.unobserve(e.target);
    }
  });
},{threshold:.1});
document.querySelectorAll('.bar-fill').forEach(b=>barObs.observe(b));

/* ============================
   STAGGER DELAYS
============================ */
document.querySelectorAll('.proj-card').forEach((c,i)=>{
  c.style.transitionDelay=(i*.12)+'s';
});
document.querySelectorAll('.cert-card').forEach((c,i)=>{
  c.style.transitionDelay=(i*.1)+'s';
});
document.querySelectorAll('.contact-card').forEach((c,i)=>{
  c.style.transitionDelay=(i*.09)+'s';
});
document.querySelectorAll('.tl-item').forEach((c,i)=>{
  c.style.transitionDelay=(i*.15)+'s';
});
document.querySelectorAll('.edu-card').forEach((c,i)=>{
  c.style.transitionDelay=(i*.12)+'s';
});
</script>
</body>
</html>
