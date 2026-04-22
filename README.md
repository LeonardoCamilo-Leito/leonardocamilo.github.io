<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Leonardo Camilo — Minimal / Deep Tech</title>
<meta name="description" content="Leonardo Camilo — Underground DJ & Producer. Minimal, Deep Tech, Dub Techno."/>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=IBM+Plex+Mono:ital,wght@0,300;0,400;1,300&family=Syne:wght@400;700;800&display=swap" rel="stylesheet"/>
<style>
/* ─── RESET ─────────────────────────────────────────── */
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth;font-size:16px}
img{display:block;max-width:100%}
a{color:inherit;text-decoration:none}
ul{list-style:none}
button{background:none;border:none;cursor:pointer}

/* ─── TOKENS ─────────────────────────────────────────── */
:root{
  --black:#000;
  --white:#fff;
  --off:#f2f0eb;
  --g1:#d6d4cf;
  --g2:#888884;
  --g3:#3a3a38;
  --g4:#1c1c1a;
  --g5:#0e0e0c;
  --display:'Bebas Neue',sans-serif;
  --mono:'IBM Plex Mono',monospace;
  --body:'Syne',sans-serif;
  --ease-out:cubic-bezier(.16,1,.3,1);
  --ease-in-out:cubic-bezier(.76,0,.24,1);
}

/* ─── BASE ───────────────────────────────────────────── */
body{
  background:var(--black);
  color:var(--white);
  font-family:var(--body);
  overflow-x:hidden;
  cursor:none;
}

/* ─── CURSOR ─────────────────────────────────────────── */
#c-dot{
  width:5px;height:5px;
  background:var(--white);
  border-radius:50%;
  position:fixed;top:0;left:0;
  pointer-events:none;z-index:9999;
  mix-blend-mode:difference;
  transform:translate(-50%,-50%);
}
#c-ring{
  width:28px;height:28px;
  border:1px solid rgba(255,255,255,.6);
  border-radius:50%;
  position:fixed;top:0;left:0;
  pointer-events:none;z-index:9998;
  mix-blend-mode:difference;
  transform:translate(-50%,-50%);
  transition:width .25s var(--ease-out),height .25s var(--ease-out),border-color .25s;
}
#c-ring.expand{width:52px;height:52px;border-color:rgba(255,255,255,.3)}

/* ─── NAV ────────────────────────────────────────────── */
#nav{
  position:fixed;top:0;left:0;right:0;
  z-index:400;
  display:flex;align-items:center;justify-content:space-between;
  padding:1.75rem 3.5rem;
  transition:padding .4s var(--ease-out),background .4s,backdrop-filter .4s;
}
#nav.compact{
  padding:1.1rem 3.5rem;
  background:rgba(0,0,0,.75);
  backdrop-filter:blur(18px);
  border-bottom:1px solid var(--g4);
}
.nav-logo{
  font-family:var(--mono);
  font-size:.7rem;
  letter-spacing:.18em;
  text-transform:uppercase;
  opacity:.9;
  display:flex;align-items:center;gap:.75rem;
}
.nav-logo-dot{
  width:6px;height:6px;
  border:1px solid var(--g2);
  border-radius:50%;
  animation:blink 2.5s ease infinite;
}
@keyframes blink{0%,100%{opacity:.3}50%{opacity:1}}
.nav-links{display:flex;gap:3rem;align-items:center}
.nav-links a{
  font-family:var(--mono);
  font-size:.62rem;
  letter-spacing:.15em;
  text-transform:uppercase;
  color:var(--g2);
  transition:color .2s;
  position:relative;
}
.nav-links a::after{
  content:'';
  position:absolute;left:0;bottom:-3px;
  width:0;height:1px;
  background:var(--white);
  transition:width .3s var(--ease-out);
}
.nav-links a:hover{color:var(--white)}
.nav-links a:hover::after{width:100%}
.nav-menu-btn{
  display:none;
  flex-direction:column;gap:5px;
  width:24px;cursor:none;
}
.nav-menu-btn span{
  display:block;height:1px;background:var(--white);
  transition:transform .3s,opacity .3s;
}

/* ─── HERO ───────────────────────────────────────────── */
#hero{
  position:relative;
  min-height:100svh;
  display:grid;
  grid-template-rows:1fr auto;
  padding:0 3.5rem;
  overflow:hidden;
}
.hero-center{
  display:flex;flex-direction:column;
  justify-content:center;
  padding-top:7rem;
  padding-bottom:2rem;
  position:relative;z-index:2;
}
.hero-tag{
  font-family:var(--mono);
  font-size:.62rem;
  letter-spacing:.22em;
  text-transform:uppercase;
  color:var(--g2);
  display:flex;align-items:center;gap:1.2rem;
  margin-bottom:1.8rem;
  opacity:0;transform:translateY(14px);
  transition:opacity .7s var(--ease-out),transform .7s var(--ease-out);
}
.hero-tag.in{opacity:1;transform:none}
.hero-tag-line{
  display:block;width:36px;height:1px;
  background:var(--g3);
}
.hero-name{
  font-family:var(--display);
  font-size:clamp(5rem,16vw,18rem);
  line-height:.87;
  letter-spacing:-.01em;
  color:var(--white);
  opacity:0;transform:translateY(30px);
  transition:opacity .9s var(--ease-out) .1s,transform .9s var(--ease-out) .1s;
}
.hero-name.in{opacity:1;transform:none}
.hero-name-stroke{
  -webkit-text-stroke:1px rgba(255,255,255,.18);
  color:transparent;
  display:block;
}
.hero-sub{
  margin-top:2.5rem;
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:3rem;
  opacity:0;transform:translateY(20px);
  transition:opacity .8s var(--ease-out) .3s,transform .8s var(--ease-out) .3s;
}
.hero-sub.in{opacity:1;transform:none}
.hero-bio{
  font-size:.92rem;
  color:var(--g2);
  line-height:1.95;
  max-width:360px;
}
.hero-bio strong{color:var(--white);font-weight:700}
.hero-ctas{
  display:flex;flex-direction:column;
  gap:1rem;align-items:flex-end;
  justify-content:flex-end;
}
.btn{
  font-family:var(--mono);
  font-size:.62rem;
  letter-spacing:.14em;
  text-transform:uppercase;
  padding:.8rem 2rem;
  transition:background .2s,color .2s,transform .2s;
  display:inline-block;
  white-space:nowrap;
}
.btn-white{background:var(--white);color:var(--black)}
.btn-white:hover{background:var(--g1);transform:translateY(-2px)}
.btn-outline{
  border:1px solid var(--g3);color:var(--g2);
}
.btn-outline:hover{border-color:var(--white);color:var(--white);transform:translateY(-2px)}

/* HERO BOTTOM BAR */
.hero-bottom{
  position:relative;z-index:2;
  display:flex;align-items:center;justify-content:space-between;
  padding:1.5rem 0;
  border-top:1px solid var(--g4);
  opacity:0;
  transition:opacity .8s var(--ease-out) .55s;
}
.hero-bottom.in{opacity:1}
.hero-bottom-links{
  display:flex;gap:2rem;
}
.hero-bottom-links a{
  font-family:var(--mono);font-size:.6rem;
  letter-spacing:.14em;text-transform:uppercase;
  color:var(--g3);transition:color .2s;
}
.hero-bottom-links a:hover{color:var(--white)}
.hero-scroll{
  font-family:var(--mono);font-size:.58rem;
  letter-spacing:.2em;text-transform:uppercase;
  color:var(--g3);
  display:flex;align-items:center;gap:1rem;
}
.hero-scroll-track{
  width:50px;height:1px;
  background:var(--g4);
  position:relative;overflow:hidden;
}
.hero-scroll-track::after{
  content:'';position:absolute;
  top:0;left:-100%;width:100%;height:100%;
  background:var(--g2);
  animation:track 2.4s ease infinite;
}
@keyframes track{to{left:100%}}

/* BIG BG LETTER */
.hero-bg-glyph{
  position:absolute;
  top:50%;right:-2vw;
  transform:translateY(-50%);
  font-family:var(--display);
  font-size:clamp(40vw,55vw,70rem);
  line-height:1;
  color:transparent;
  -webkit-text-stroke:1px rgba(255,255,255,.028);
  pointer-events:none;user-select:none;
  z-index:1;
  will-change:transform;
}

/* OSCILLOSCOPE deco */
.osc-wrap{
  position:absolute;bottom:5rem;right:3.5rem;
  z-index:2;
  opacity:.25;
}
.osc-label{
  font-family:var(--mono);font-size:.5rem;
  letter-spacing:.15em;text-transform:uppercase;
  color:var(--g2);margin-bottom:.5rem;text-align:right;
}
.osc{display:flex;align-items:flex-end;gap:2px;height:32px}
.osc b{
  display:block;width:2px;border-radius:1px;
  background:var(--g2);
  animation:oscBar 1.3s ease-in-out infinite;
}
.osc b:nth-child(1){height:6px;animation-delay:0s}
.osc b:nth-child(2){height:18px;animation-delay:.08s}
.osc b:nth-child(3){height:10px;animation-delay:.16s}
.osc b:nth-child(4){height:28px;animation-delay:.04s}
.osc b:nth-child(5){height:14px;animation-delay:.22s}
.osc b:nth-child(6){height:22px;animation-delay:.1s}
.osc b:nth-child(7){height:8px;animation-delay:.18s}
.osc b:nth-child(8){height:32px;animation-delay:.06s}
.osc b:nth-child(9){height:12px;animation-delay:.24s}
.osc b:nth-child(10){height:20px;animation-delay:.14s}
.osc b:nth-child(11){height:6px;animation-delay:.2s}
.osc b:nth-child(12){height:16px;animation-delay:.02s}
@keyframes oscBar{
  0%,100%{transform:scaleY(.35);opacity:.4}
  50%{transform:scaleY(1);opacity:1}
}

/* ─── SECTION SHARED ─────────────────────────────────── */
.section{padding:7rem 3.5rem}
.sec-header{
  display:flex;align-items:baseline;
  justify-content:space-between;
  padding-bottom:1.5rem;
  border-bottom:1px solid var(--g4);
  margin-bottom:4rem;
  gap:2rem;
  flex-wrap:wrap;
}
.sec-tag{
  font-family:var(--mono);font-size:.6rem;
  letter-spacing:.2em;text-transform:uppercase;
  color:var(--g2);
  display:flex;align-items:center;gap:.8rem;
}
.sec-tag::before{
  content:'';display:block;
  width:24px;height:1px;background:var(--g3);
}
.sec-title{
  font-family:var(--display);
  font-size:clamp(3rem,6vw,7rem);
  letter-spacing:.02em;line-height:.9;
  color:var(--white);
}
.sec-link{
  font-family:var(--mono);font-size:.6rem;
  letter-spacing:.14em;text-transform:uppercase;
  color:var(--g2);
  border-bottom:1px solid var(--g3);
  padding-bottom:2px;
  transition:color .2s,border-color .2s;
  white-space:nowrap;
}
.sec-link:hover{color:var(--white);border-color:var(--white)}

/* REVEAL SYSTEM */
.rv{opacity:0;transform:translateY(32px);
  transition:opacity .85s var(--ease-out),transform .85s var(--ease-out)}
.rv.in{opacity:1;transform:none}
.rv-l{opacity:0;transform:translateX(-28px);
  transition:opacity .85s var(--ease-out),transform .85s var(--ease-out)}
.rv-l.in{opacity:1;transform:none}
.rv-r{opacity:0;transform:translateX(28px);
  transition:opacity .85s var(--ease-out),transform .85s var(--ease-out)}
.rv-r.in{opacity:1;transform:none}
.rv-s{opacity:0;transform:scale(.96);
  transition:opacity .85s var(--ease-out),transform .85s var(--ease-out)}
.rv-s.in{opacity:1;transform:none}
.d1{transition-delay:.06s}.d2{transition-delay:.14s}
.d3{transition-delay:.24s}.d4{transition-delay:.36s}
.d5{transition-delay:.48s}.d6{transition-delay:.62s}

/* ─── RELEASES ───────────────────────────────────────── */
#releases{background:var(--black)}
.releases-grid{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  border:1px solid var(--g4);
}
.rel-card{
  border-right:1px solid var(--g4);
  padding:2.5rem;
  display:flex;flex-direction:column;
  gap:1.5rem;
  position:relative;overflow:hidden;
  transition:background .35s;
  text-decoration:none;color:inherit;
}
.rel-card:last-child{border-right:none}
.rel-card::before{
  content:'';position:absolute;
  inset:0;
  background:var(--g5);
  transform:translateY(100%);
  transition:transform .45s var(--ease-in-out);
  z-index:0;
}
.rel-card:hover::before{transform:translateY(0)}
.rel-card>*{position:relative;z-index:1}

.rel-meta{
  display:flex;align-items:center;justify-content:space-between;
}
.rel-year{
  font-family:var(--mono);font-size:.58rem;
  letter-spacing:.16em;text-transform:uppercase;
  color:var(--g3);
}
.rel-arrow{
  font-size:.9rem;color:var(--g3);
  transform:translateX(-4px);
  transition:transform .3s,color .3s;
}
.rel-card:hover .rel-arrow{transform:translateX(0);color:var(--white)}

.rel-artwork{
  aspect-ratio:1/1;
  background:var(--g4);
  overflow:hidden;
  position:relative;
  display:flex;align-items:center;justify-content:center;
}
.rel-artwork img{
  width:100%;height:100%;object-fit:cover;
  transition:transform .6s var(--ease-out);
}
.rel-card:hover .rel-artwork img{transform:scale(1.04)}
.rel-artwork-placeholder{
  font-family:var(--display);
  font-size:5rem;letter-spacing:-.04em;
  color:var(--g3);
  transition:color .3s;
}
.rel-card:hover .rel-artwork-placeholder{color:var(--g2)}
.rel-artwork-grid{
  position:absolute;inset:0;
  background-image:
    linear-gradient(rgba(255,255,255,.03) 1px,transparent 1px),
    linear-gradient(90deg,rgba(255,255,255,.03) 1px,transparent 1px);
  background-size:24px 24px;
  pointer-events:none;
}

.rel-label{
  font-family:var(--mono);font-size:.58rem;
  letter-spacing:.14em;text-transform:uppercase;
  color:var(--g2);
}
.rel-title{
  font-family:var(--display);
  font-size:2rem;letter-spacing:.04em;
  color:var(--white);line-height:1;
}
.rel-info{
  font-size:.78rem;color:var(--g3);
  font-family:var(--mono);
}

/* ─── TRACKS ─────────────────────────────────────────── */
#tracks{background:var(--g5)}
.track-list{margin-top:.5rem}
.track{
  display:grid;
  grid-template-columns:2.5rem 1fr repeat(3,auto);
  align-items:center;gap:2rem;
  padding:1.4rem 0;
  border-bottom:1px solid rgba(255,255,255,.055);
  position:relative;
  transition:padding-left .3s var(--ease-out);
}
.track:first-child{border-top:1px solid rgba(255,255,255,.055)}
.track::after{
  content:'';
  position:absolute;left:0;bottom:0;
  height:1px;width:0;
  background:var(--white);
  transition:width .5s var(--ease-out);
}
.track:hover{padding-left:.75rem}
.track:hover::after{width:100%}
.track:hover .track-num{opacity:0}
.track:hover .track-play{opacity:1}
.track-num{
  font-family:var(--mono);font-size:.65rem;
  color:var(--g2);opacity:.45;
  transition:opacity .2s;
  grid-row:1;grid-column:1;
}
.track-play{
  font-size:.75rem;color:var(--white);
  opacity:0;transition:opacity .2s;
  grid-row:1;grid-column:1;
  position:absolute;left:0;
}
.track-title{
  font-family:var(--display);
  font-size:clamp(1.3rem,2.5vw,2rem);
  letter-spacing:.04em;
  color:var(--white);
  transition:letter-spacing .3s var(--ease-out);
}
.track:hover .track-title{letter-spacing:.07em}
.track-genre{
  font-family:var(--mono);font-size:.58rem;
  letter-spacing:.1em;text-transform:uppercase;
  color:var(--g3);
}
.track-bpm{
  font-family:var(--mono);font-size:.62rem;
  color:var(--g2);white-space:nowrap;
}
.track-dur{
  font-family:var(--mono);font-size:.65rem;
  color:var(--g2);
}

.tracks-footer{
  margin-top:3rem;
  display:flex;align-items:center;
  gap:2.5rem;flex-wrap:wrap;
}
.wave-mini{display:flex;align-items:flex-end;gap:2px;height:18px}
.wave-mini span{
  display:block;width:2px;border-radius:1px;
  background:var(--g3);
  animation:wm 1.4s ease-in-out infinite;
}
.wave-mini span:nth-child(1){height:5px;animation-delay:0s}
.wave-mini span:nth-child(2){height:12px;animation-delay:.1s}
.wave-mini span:nth-child(3){height:8px;animation-delay:.2s}
.wave-mini span:nth-child(4){height:16px;animation-delay:.05s}
.wave-mini span:nth-child(5){height:6px;animation-delay:.15s}
.wave-mini span:nth-child(6){height:11px;animation-delay:.25s}
.wave-mini span:nth-child(7){height:4px;animation-delay:.08s}
@keyframes wm{
  0%,100%{transform:scaleY(.4);opacity:.3}
  50%{transform:scaleY(1);opacity:.8}
}

/* ─── ABOUT ──────────────────────────────────────────── */
#about{background:var(--black)}
.about-grid{
  display:grid;
  grid-template-columns:5fr 7fr;
  gap:5rem;align-items:start;
}
.about-img-wrap{
  position:relative;
}
.about-img{
  width:100%;aspect-ratio:3/4;
  background:var(--g4);overflow:hidden;
  position:relative;
}
.about-img img{
  width:100%;height:100%;object-fit:cover;
  filter:grayscale(100%);
  transition:filter .5s,transform .6s var(--ease-out);
}
.about-img:hover img{filter:grayscale(60%);transform:scale(1.02)}
.about-img-placeholder{
  position:absolute;inset:0;
  display:flex;align-items:center;justify-content:center;
  flex-direction:column;gap:1rem;
}
.about-img-grid{
  position:absolute;inset:0;
  background-image:
    repeating-linear-gradient(0deg,transparent,transparent 29px,rgba(255,255,255,.04) 30px),
    repeating-linear-gradient(90deg,transparent,transparent 29px,rgba(255,255,255,.04) 30px);
  pointer-events:none;
}
.about-img-label{
  position:absolute;left:0;right:0;bottom:0;
  padding:1.25rem 1.5rem;
  font-family:var(--mono);font-size:.55rem;
  letter-spacing:.14em;text-transform:uppercase;
  color:var(--g3);
  background:linear-gradient(transparent,rgba(0,0,0,.6));
}
.about-img-corner{
  position:absolute;
  width:20px;height:20px;
  border-color:rgba(255,255,255,.15);
  border-style:solid;
}
.about-img-corner.tl{top:1rem;left:1rem;border-width:1px 0 0 1px}
.about-img-corner.tr{top:1rem;right:1rem;border-width:1px 1px 0 0}
.about-img-corner.bl{bottom:1rem;left:1rem;border-width:0 0 1px 1px}
.about-img-corner.br{bottom:1rem;right:1rem;border-width:0 1px 1px 0}

.about-counter{
  margin-top:2rem;
  display:grid;grid-template-columns:1fr 1fr;
  gap:1px;background:var(--g4);
}
.counter-cell{
  background:var(--black);
  padding:1.5rem;
}
.counter-num{
  font-family:var(--display);
  font-size:3.5rem;letter-spacing:-.02em;
  color:var(--white);line-height:1;
  margin-bottom:.3rem;
}
.counter-label{
  font-family:var(--mono);font-size:.58rem;
  letter-spacing:.14em;text-transform:uppercase;
  color:var(--g2);
}

.about-content{}
.about-headline{
  font-family:var(--display);
  font-size:clamp(2.5rem,5vw,5rem);
  letter-spacing:.02em;line-height:.92;
  color:var(--white);
  margin-bottom:2.5rem;
}
.about-headline em{
  font-style:normal;
  -webkit-text-stroke:1px rgba(255,255,255,.3);
  color:transparent;
}
.about-text{
  font-size:.9rem;color:var(--g2);
  line-height:2.1;margin-bottom:1.4rem;
}
.about-text strong{color:var(--white);font-weight:700}
.about-tags{
  display:flex;flex-wrap:wrap;gap:.5rem;
  margin-top:2.5rem;
}
.tag{
  font-family:var(--mono);font-size:.58rem;
  letter-spacing:.1em;text-transform:uppercase;
  padding:.35rem .9rem;
  border:1px solid var(--g3);
  color:var(--g2);
  transition:background .2s,color .2s,border-color .2s;
}
.tag:hover,.tag.active{
  background:var(--white);color:var(--black);
  border-color:var(--white);
}

/* ─── LABELS STRIP ───────────────────────────────────── */
#strip{
  padding:3rem 3.5rem;
  background:var(--g5);
  border-top:1px solid var(--g4);
  border-bottom:1px solid var(--g4);
  overflow:hidden;
}
.strip-inner{
  display:flex;align-items:center;gap:5rem;
  animation:marquee 18s linear infinite;
  width:max-content;
}
.strip-inner:hover{animation-play-state:paused}
.strip-item{
  font-family:var(--display);font-size:1.4rem;
  letter-spacing:.1em;color:var(--g3);
  white-space:nowrap;
  transition:color .3s;
}
.strip-item:hover{color:var(--white)}
.strip-sep{
  width:4px;height:4px;
  background:var(--g3);border-radius:50%;
  flex-shrink:0;
}
@keyframes marquee{
  from{transform:translateX(0)}
  to{transform:translateX(-50%)}
}

/* ─── CONTACT ────────────────────────────────────────── */
#contact{
  background:var(--black);
  padding:8rem 3.5rem 7rem;
  position:relative;overflow:hidden;
}
.contact-bg{
  position:absolute;
  bottom:-8vw;right:-5vw;
  font-family:var(--display);
  font-size:clamp(20vw,28vw,40rem);
  line-height:1;
  color:transparent;
  -webkit-text-stroke:1px rgba(255,255,255,.03);
  pointer-events:none;user-select:none;
  white-space:nowrap;
}
.contact-grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:6rem;align-items:end;
  position:relative;z-index:1;
}
.contact-big{
  font-family:var(--display);
  font-size:clamp(4rem,10vw,11rem);
  letter-spacing:-.01em;line-height:.88;
  color:var(--white);
}
.contact-big span{
  display:block;
  -webkit-text-stroke:1px rgba(255,255,255,.25);
  color:transparent;
}
.contact-right{}
.contact-desc{
  font-size:.88rem;color:var(--g2);
  line-height:2;margin-bottom:2.5rem;
  max-width:320px;
}
.contact-email-wrap{
  margin-bottom:2.5rem;
}
.contact-email-label{
  font-family:var(--mono);font-size:.55rem;
  letter-spacing:.18em;text-transform:uppercase;
  color:var(--g3);margin-bottom:.5rem;
}
.contact-email{
  font-family:var(--mono);font-size:1rem;
  letter-spacing:.04em;color:var(--white);
  border-bottom:1px solid var(--g3);
  padding-bottom:4px;
  display:inline-block;
  transition:border-color .2s,color .2s;
}
.contact-email:hover{border-color:var(--white)}
.socials{
  display:flex;flex-direction:column;gap:.75rem;
}
.social-row-item{
  display:flex;align-items:center;
  justify-content:space-between;
  padding:.75rem 0;
  border-bottom:1px solid rgba(255,255,255,.06);
  transition:padding-left .25s;
}
.social-row-item:hover{padding-left:.5rem}
.social-name{
  font-family:var(--mono);font-size:.62rem;
  letter-spacing:.14em;text-transform:uppercase;
  color:var(--g2);transition:color .2s;
}
.social-row-item:hover .social-name{color:var(--white)}
.social-arrow{font-size:.75rem;color:var(--g3);transition:color .2s}
.social-row-item:hover .social-arrow{color:var(--white)}

/* ─── FOOTER ─────────────────────────────────────────── */
footer{
  background:var(--g5);
  border-top:1px solid var(--g4);
  padding:2rem 3.5rem;
  display:grid;
  grid-template-columns:1fr auto 1fr;
  align-items:center;gap:2rem;
}
.foot-logo{
  font-family:var(--mono);font-size:.6rem;
  letter-spacing:.16em;text-transform:uppercase;
  color:var(--g3);
}
.foot-center{
  font-family:var(--mono);font-size:.55rem;
  letter-spacing:.12em;text-transform:uppercase;
  color:var(--g4);text-align:center;
}
.foot-right{
  font-family:var(--mono);font-size:.55rem;
  letter-spacing:.1em;text-transform:uppercase;
  color:var(--g3);text-align:right;
}

/* ─── RESPONSIVE ─────────────────────────────────────── */
@media(max-width:900px){
  #nav{padding:1.5rem 1.5rem}
  #nav.compact{padding:1rem 1.5rem}
  .nav-links{display:none}
  .nav-menu-btn{display:flex}
  #hero{padding:0 1.5rem}
  .hero-bg-glyph{display:none}
  .osc-wrap{display:none}
  .hero-sub{grid-template-columns:1fr}
  .hero-ctas{align-items:flex-start}
  .section{padding:5rem 1.5rem}
  .releases-grid{grid-template-columns:1fr}
  .rel-card{border-right:none;border-bottom:1px solid var(--g4)}
  .rel-card:last-child{border-bottom:none}
  .track{grid-template-columns:2rem 1fr auto;gap:1rem}
  .track-genre,.track-bpm{display:none}
  .about-grid{grid-template-columns:1fr}
  .about-counter{grid-template-columns:repeat(4,1fr)}
  .contact-grid{grid-template-columns:1fr}
  .contact-big{font-size:clamp(4rem,15vw,8rem)}
  footer{grid-template-columns:1fr 1fr;grid-template-rows:auto auto}
  .foot-center{grid-column:1/-1;order:3}
  #contact{padding:5rem 1.5rem 4rem}
  body{cursor:auto}
  #c-dot,#c-ring{display:none}
}
@media(max-width:500px){
  .about-counter{grid-template-columns:1fr 1fr}
  .sec-title{font-size:clamp(2.5rem,12vw,5rem)}
}
</style>
</head>
<body>

<!-- CURSOR -->
<div id="c-dot"></div>
<div id="c-ring"></div>

<!-- ── NAV ──────────────────────────────────────────── -->
<nav id="nav">
  <a href="#hero" class="nav-logo">
    <span class="nav-logo-dot"></span>
    LC — Artist
  </a>
  <ul class="nav-links">
    <li><a href="#releases">Releases</a></li>
    <li><a href="#tracks">Tracks</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#contact">Booking</a></li>
  </ul>
  <button class="nav-menu-btn" aria-label="Menu">
    <span></span><span></span><span></span>
  </button>
</nav>

<!-- ── HERO ─────────────────────────────────────────── -->
<section id="hero">
  <div class="hero-bg-glyph" aria-hidden="true">L</div>

  <div class="osc-wrap" aria-hidden="true">
    <p class="osc-label">Signal</p>
    <div class="osc">
      <b></b><b></b><b></b><b></b><b></b><b></b>
      <b></b><b></b><b></b><b></b><b></b><b></b>
    </div>
  </div>

  <div class="hero-center">
    <p class="hero-tag" id="h-tag">
      <span class="hero-tag-line"></span>
      DJ &amp; Producer · Minimal / Deep Tech
    </p>
    <h1 class="hero-name" id="h-name">
      Leonardo
      <span class="hero-name-stroke">Camilo</span>
    </h1>
    <div class="hero-sub" id="h-sub">
      <p class="hero-bio">
        Productor y DJ underground de <strong>Minimal / Deep Tech</strong>,
        <strong>Deep House</strong> y <strong>Dub Techno</strong>.
        Construyendo paisajes sonoros desde las frecuencias analógicas
        hasta los límites del dancefloor.
      </p>
      <div class="hero-ctas">
        <a href="https://www.beatport.com/es/artist/leonardo-camilo/718404" target="_blank" class="btn btn-white">Escuchar en Beatport</a>
        <a href="#contact" class="btn btn-outline">Booking &amp; Contacto</a>
      </div>
    </div>
  </div>

  <div class="hero-bottom" id="h-bot">
    <div class="hero-bottom-links">
      <a href="https://ecoulsnd.bandcamp.com/album/future-view" target="_blank">Bandcamp</a>
      <a href="https://soundcloud.com/ecoul_snd/premiere-leonardo-camilo-future-view" target="_blank">SoundCloud</a>
      <!-- AGREGA MÁS REDES AQUÍ -->
    </div>
    <div class="hero-scroll">
      <div class="hero-scroll-track"></div>
      Scroll
    </div>
  </div>
</section>

<!-- ── RELEASES ──────────────────────────────────────── -->
<section class="section" id="releases">
  <div class="sec-header rv">
    <span class="sec-tag">Discografía</span>
    <h2 class="sec-title">Releases</h2>
    <a href="https://www.beatport.com/es/artist/leonardo-camilo/718404" target="_blank" class="sec-link">Ver todo en Beatport →</a>
  </div>

  <div class="releases-grid">

    <!-- RELEASE 1 — Future View -->
    <a href="https://ecoulsnd.bandcamp.com/album/future-view" target="_blank" class="rel-card rv d1">
      <div class="rel-meta">
        <span class="rel-year">2024 · ECOUL SND · ECOUL104</span>
        <span class="rel-arrow">↗</span>
      </div>
      <div class="rel-artwork">
        <div class="rel-artwork-grid"></div>
        <!-- ↓ REEMPLAZA con: <img src="assets/cover-future-view.jpg" alt="Future View"> -->
        <div class="rel-artwork-placeholder">FV</div>
      </div>
      <div>
        <p class="rel-label">EP · 4 Tracks</p>
        <p class="rel-title">Future View</p>
        <p class="rel-info">Minimal / Deep Tech · 127 BPM · G Min</p>
      </div>
    </a>

    <!-- RELEASE 2 — Simply Minimal Vol.17 -->
    <div class="rel-card rv d2">
      <div class="rel-meta">
        <span class="rel-year">2024 · Simply Minimal</span>
        <span class="rel-arrow">↗</span>
      </div>
      <div class="rel-artwork">
        <div class="rel-artwork-grid"></div>
        <!-- ↓ REEMPLAZA con: <img src="assets/cover-simply-minimal.jpg" alt="Simply Minimal"> -->
        <div class="rel-artwork-placeholder">SM</div>
      </div>
      <div>
        <p class="rel-label">Compilation · Feature</p>
        <p class="rel-title">Simply Minimal</p>
        <p class="rel-info">Vol. 17 · Minimal / Deep Tech</p>
      </div>
    </div>

    <!-- RELEASE 3 — Minimal Taurus -->
    <div class="rel-card rv d3">
      <div class="rel-meta">
        <span class="rel-year">2024 · Minimal Taurus</span>
        <span class="rel-arrow">↗</span>
      </div>
      <div class="rel-artwork">
        <div class="rel-artwork-grid"></div>
        <!-- ↓ REEMPLAZA con: <img src="assets/cover-minimal-taurus.jpg" alt="Minimal Taurus"> -->
        <div class="rel-artwork-placeholder">MT</div>
      </div>
      <div>
        <p class="rel-label">Compilation · Feature</p>
        <p class="rel-title">Minimal Taurus</p>
        <p class="rel-info">Minimal / Deep Tech</p>
      </div>
    </div>

  </div>
</section>

<!-- ── TRACKS ────────────────────────────────────────── -->
<section class="section" id="tracks">
  <div class="sec-header rv">
    <span class="sec-tag">Future View EP — ECOUL104</span>
    <h2 class="sec-title">Tracklist</h2>
  </div>

  <div class="track-list">
    <div class="track rv d1">
      <span class="track-num">01</span>
      <span class="track-play">▶</span>
      <span class="track-title">Future View</span>
      <span class="track-genre">Minimal / Deep</span>
      <span class="track-bpm">127 BPM · G Min</span>
      <span class="track-dur">06:35</span>
    </div>
    <div class="track rv d2">
      <span class="track-num">02</span>
      <span class="track-play">▶</span>
      <span class="track-title">Analog Dialog</span>
      <span class="track-genre">Minimal / Deep</span>
      <span class="track-bpm">— BPM</span>
      <span class="track-dur">07:14</span>
    </div>
    <div class="track rv d3">
      <span class="track-num">03</span>
      <span class="track-play">▶</span>
      <span class="track-title">Floating Attention</span>
      <span class="track-genre">Minimal / Deep</span>
      <span class="track-bpm">— BPM</span>
      <span class="track-dur">09:06</span>
    </div>
    <div class="track rv d4">
      <span class="track-num">04</span>
      <span class="track-play">▶</span>
      <span class="track-title">Inside Frequencies</span>
      <span class="track-genre">Minimal / Deep</span>
      <span class="track-bpm">— BPM</span>
      <span class="track-dur">10:22</span>
    </div>
  </div>

  <div class="tracks-footer rv d5">
    <div class="wave-mini" aria-hidden="true">
      <span></span><span></span><span></span>
      <span></span><span></span><span></span><span></span>
    </div>
    <a href="https://www.beatport.com/es/artist/leonardo-camilo/718404" target="_blank" class="sec-link">Escuchar en Beatport →</a>
    <a href="https://ecoulsnd.bandcamp.com/album/future-view" target="_blank" class="sec-link">Descargar en Bandcamp →</a>
  </div>
</section>

<!-- ── LABELS MARQUEE ────────────────────────────────── -->
<div id="strip">
  <div class="strip-inner" aria-hidden="true">
    <span class="strip-item">ECOUL SND</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Simply Minimal</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Minimal Taurus</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Beatport</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Bandcamp</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Minimal / Deep Tech</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Dub Techno</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Deep House</span>
    <span class="strip-sep"></span>
    <!-- duplicado para loop continuo -->
    <span class="strip-item">ECOUL SND</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Simply Minimal</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Minimal Taurus</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Beatport</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Bandcamp</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Minimal / Deep Tech</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Dub Techno</span>
    <span class="strip-sep"></span>
    <span class="strip-item">Deep House</span>
    <span class="strip-sep"></span>
  </div>
</div>

<!-- ── ABOUT ─────────────────────────────────────────── -->
<section class="section" id="about">
  <div class="sec-header rv">
    <span class="sec-tag">El artista</span>
    <h2 class="sec-title">About</h2>
  </div>

  <div class="about-grid">

    <div class="rv-l">
      <div class="about-img">
        <div class="about-img-grid"></div>
        <!-- ↓ REEMPLAZA con: <img src="assets/foto-press.jpg" alt="Leonardo Camilo"> -->
        <div class="about-img-placeholder">
          <span style="font-family:var(--mono);font-size:.6rem;letter-spacing:.15em;color:var(--g3);text-transform:uppercase;">Press Photo</span>
        </div>
        <div class="about-img-corner tl"></div>
        <div class="about-img-corner tr"></div>
        <div class="about-img-corner bl"></div>
        <div class="about-img-corner br"></div>
        <div class="about-img-label">Leonardo Camilo — Artist</div>
      </div>

      <div class="about-counter">
        <div class="counter-cell rv d1">
          <div class="counter-num" data-target="5">0</div>
          <div class="counter-label">Años activo</div>
        </div>
        <div class="counter-cell rv d2">
          <div class="counter-num" data-target="40">0</div>
          <div class="counter-label">Tracks</div>
        </div>
        <div class="counter-cell rv d3">
          <div class="counter-num" data-target="3">0</div>
          <div class="counter-label">Sellos</div>
        </div>
        <div class="counter-cell rv d4">
          <div class="counter-num" data-target="10">0</div>
          <div class="counter-label">Compilaciones</div>
        </div>
      </div>
    </div>

    <div class="about-content">
      <h3 class="about-headline rv d1">
        Underground<br/>
        <em>Sound &amp;</em><br/>
        Vision
      </h3>
      <p class="about-text rv d2">
        <strong>Leonardo Camilo</strong> es un productor y DJ underground cuya música habita
        en los límites entre el minimal house clásico, el deep tech y el dub techno.
        Sus composiciones construyen paisajes sonoros hipnóticos que invitan a perderse
        en frecuencias analógicas y texturas profundas.
      </p>
      <p class="about-text rv d3">
        También conocido como <strong>L.A. / Leonar.do</strong>, su EP
        <strong>Future View</strong> (ECOUL SND, 2024) consolidó su presencia en la
        escena underground global, con pistas que alcanzan los diez minutos de viaje
        ininterrumpido en el dancefloor.
      </p>
      <p class="about-text rv d4">
        Su trabajo aparece en compilaciones internacionales junto a artistas de la escena
        minimal latinoamericana y europea, con lanzamientos distribuidos en
        Beatport, Bandcamp y plataformas de streaming globales.
      </p>
      <div class="about-tags rv d5">
        <span class="tag active">Minimal</span>
        <span class="tag active">Deep Tech</span>
        <span class="tag active">Dub Techno</span>
        <span class="tag">Deep House</span>
        <span class="tag">Underground</span>
        <span class="tag">Electronic</span>
      </div>
    </div>

  </div>
</section>

<!-- ── CONTACT ───────────────────────────────────────── -->
<section id="contact">
  <div class="contact-bg" aria-hidden="true">BOOK</div>

  <div class="contact-grid">
    <div>
      <h2 class="contact-big rv">
        Booking
        <span>&amp; Contact</span>
      </h2>
    </div>

    <div class="contact-right rv d2">
      <p class="contact-desc">
        Disponible para bookings, colaboraciones, remixes y producción.
        Responde en menos de 48 horas.
      </p>

      <div class="contact-email-wrap">
        <p class="contact-email-label">Email directo</p>
        <!-- ↓ CAMBIA POR TU EMAIL REAL -->
        <a href="mailto:hola@leonardocamilo.com" class="contact-email">
          hola@leonardocamilo.com
        </a>
      </div>

      <div class="socials">
        <a href="https://www.beatport.com/es/artist/leonardo-camilo/718404" target="_blank" class="social-row-item">
          <span class="social-name">Beatport</span>
          <span class="social-arrow">↗</span>
        </a>
        <a href="https://ecoulsnd.bandcamp.com/album/future-view" target="_blank" class="social-row-item">
          <span class="social-name">Bandcamp</span>
          <span class="social-arrow">↗</span>
        </a>
        <a href="https://soundcloud.com/ecoul_snd/premiere-leonardo-camilo-future-view" target="_blank" class="social-row-item">
          <span class="social-name">SoundCloud</span>
          <span class="social-arrow">↗</span>
        </a>
        <!-- ↓ AGREGA Instagram, etc. con el mismo patrón -->
        <a href="#" class="social-row-item">
          <span class="social-name">Instagram</span>
          <span class="social-arrow">↗</span>
        </a>
      </div>
    </div>
  </div>
</section>

<!-- ── FOOTER ────────────────────────────────────────── -->
<footer>
  <p class="foot-logo">LC — Leonardo Camilo</p>
  <p class="foot-center">Minimal / Deep Tech · Underground Electronic</p>
  <p class="foot-right">© 2025 All rights reserved</p>
</footer>

<!-- ── SCRIPTS ───────────────────────────────────────── -->
<script>
/* Cursor */
const dot=document.getElementById('c-dot');
const ring=document.getElementById('c-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{
  mx=e.clientX;my=e.clientY;
  dot.style.left=mx+'px';dot.style.top=my+'px';
});
(function loop(){
  rx+=(mx-rx)*.1;ry+=(my-ry)*.1;
  ring.style.left=rx+'px';ring.style.top=ry+'px';
  requestAnimationFrame(loop);
})();
document.querySelectorAll('a,button,.rel-card,.track,.social-row-item').forEach(el=>{
  el.addEventListener('mouseenter',()=>ring.classList.add('expand'));
  el.addEventListener('mouseleave',()=>ring.classList.remove('expand'));
});

/* Nav compact */
const nav=document.getElementById('nav');
window.addEventListener('scroll',()=>{
  nav.classList.toggle('compact',scrollY>80);
},{ passive:true });

/* Hero entrance */
window.addEventListener('load',()=>{
  setTimeout(()=>document.getElementById('h-tag').classList.add('in'),200);
  setTimeout(()=>document.getElementById('h-name').classList.add('in'),350);
  setTimeout(()=>document.getElementById('h-sub').classList.add('in'),550);
  setTimeout(()=>document.getElementById('h-bot').classList.add('in'),720);
});

/* Scroll reveal */
const revealEls=document.querySelectorAll('.rv,.rv-l,.rv-r,.rv-s');
const revObs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){e.target.classList.add('in');revObs.unobserve(e.target)}
  });
},{threshold:0.1,rootMargin:'0px 0px -60px 0px'});
revealEls.forEach(el=>revObs.observe(el));

/* Animated counters */
function animateCount(el){
  const target=+el.dataset.target;
  const dur=1200;const step=16;
  const inc=target/(dur/step);
  let cur=0;
  const t=setInterval(()=>{
    cur=Math.min(cur+inc,target);
    el.textContent=Math.floor(cur)+(cur>=target&&target>=10?'+':'');
    if(cur>=target)clearInterval(t);
  },step);
}
const cntObs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.querySelectorAll('[data-target]').forEach(animateCount);
      cntObs.unobserve(e.target);
    }
  });
},{threshold:0.4});
document.querySelectorAll('.about-counter').forEach(el=>cntObs.observe(el));

/* Parallax bg glyph */
const glyph=document.querySelector('.hero-bg-glyph');
if(glyph){
  window.addEventListener('scroll',()=>{
    glyph.style.transform=`translateY(calc(-50% + ${scrollY*.18}px))`;
  },{passive:true});
}
</script>
</body>
</html>
