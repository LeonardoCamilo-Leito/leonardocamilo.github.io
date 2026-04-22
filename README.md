[leonardo-camilo-artist.html](https://github.com/user-attachments/files/26984457/leonardo-camilo-artist.html) 
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Leonardo Camilo — Minimal / Deep Tech</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=IBM+Plex+Mono:ital,wght@0,300;0,400;1,300&family=DM+Sans:wght@300;400&display=swap" rel="stylesheet"/>
<style>
*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

:root {
  --black: #000000;
  --white: #ffffff;
  --off-white: #f0efeb;
  --gray-1: #e8e8e6;
  --gray-2: #999998;
  --gray-3: #444443;
  --gray-4: #1a1a1a;
  --display: 'Bebas Neue', sans-serif;
  --mono: 'IBM Plex Mono', monospace;
  --sans: 'DM Sans', sans-serif;
}

html { scroll-behavior: smooth; }

body {
  background: var(--black);
  color: var(--white);
  font-family: var(--sans);
  font-size: 15px;
  line-height: 1.7;
  overflow-x: hidden;
  cursor: none;
}

/* Grain overlay */
body::before {
  content: '';
  position: fixed; inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='1'/%3E%3C/svg%3E");
  opacity: 0.03;
  pointer-events: none;
  z-index: 1000;
}

/* Custom cursor */
.cursor {
  width: 6px; height: 6px;
  background: var(--white);
  border-radius: 50%;
  position: fixed; top: 0; left: 0;
  pointer-events: none; z-index: 9999;
  mix-blend-mode: difference;
  transition: transform 0.1s;
}
.cursor-ring {
  width: 30px; height: 30px;
  border: 1px solid rgba(255,255,255,0.5);
  border-radius: 50%;
  position: fixed; top: 0; left: 0;
  pointer-events: none; z-index: 9998;
  mix-blend-mode: difference;
  transition: width 0.3s, height 0.3s, opacity 0.3s;
}

/* NAV */
nav {
  position: fixed; top: 0; left: 0; right: 0;
  z-index: 500;
  padding: 1.5rem 3rem;
  display: flex; align-items: center; justify-content: space-between;
  mix-blend-mode: difference;
}
.nav-logo {
  font-family: var(--mono);
  font-size: 0.75rem;
  letter-spacing: 0.15em;
  color: var(--white);
  text-decoration: none;
  text-transform: uppercase;
}
.nav-links { display: flex; gap: 2.5rem; list-style: none; }
.nav-links a {
  font-family: var(--mono);
  font-size: 0.65rem;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  color: var(--white);
  text-decoration: none;
  opacity: 0.5;
  transition: opacity 0.2s;
}
.nav-links a:hover { opacity: 1; }

/* SCROLL REVEAL */
.reveal {
  opacity: 0; transform: translateY(30px);
  transition: opacity 0.9s cubic-bezier(.16,1,.3,1), transform 0.9s cubic-bezier(.16,1,.3,1);
}
.reveal.visible { opacity: 1; transform: translateY(0); }
.reveal-left {
  opacity: 0; transform: translateX(-30px);
  transition: opacity 0.9s cubic-bezier(.16,1,.3,1), transform 0.9s cubic-bezier(.16,1,.3,1);
}
.reveal-left.visible { opacity: 1; transform: translateX(0); }
.d1 { transition-delay: 0.05s; }
.d2 { transition-delay: 0.15s; }
.d3 { transition-delay: 0.25s; }
.d4 { transition-delay: 0.38s; }
.d5 { transition-delay: 0.52s; }
.d6 { transition-delay: 0.68s; }

/* HERO */
#hero {
  min-height: 100vh;
  display: flex; flex-direction: column;
  justify-content: flex-end;
  padding: 0 3rem 4rem;
  position: relative; overflow: hidden;
}

.hero-bg-text {
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  font-family: var(--display);
  font-size: clamp(18vw, 22vw, 25vw);
  color: transparent;
  -webkit-text-stroke: 1px rgba(255,255,255,0.04);
  white-space: nowrap;
  pointer-events: none;
  user-select: none;
  letter-spacing: -0.02em;
}

.hero-meta {
  font-family: var(--mono);
  font-size: 0.65rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--gray-2);
  margin-bottom: 1.5rem;
  display: flex; align-items: center; gap: 2rem;
}
.hero-meta::before {
  content: '';
  display: block; width: 50px; height: 1px;
  background: var(--gray-3);
}

.hero-name {
  font-family: var(--display);
  font-size: clamp(5.5rem, 14vw, 16rem);
  line-height: 0.88;
  letter-spacing: -0.02em;
  color: var(--white);
  margin-bottom: 2rem;
  position: relative;
}

.hero-bottom {
  display: flex; justify-content: space-between;
  align-items: flex-end; flex-wrap: wrap; gap: 2rem;
}

.hero-bio {
  max-width: 380px;
  font-size: 0.875rem;
  line-height: 1.8;
  color: var(--gray-2);
}
.hero-bio strong { color: var(--white); font-weight: 400; }

.hero-links {
  display: flex; gap: 1.5rem;
  font-family: var(--mono);
  font-size: 0.65rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}
.hero-links a {
  color: var(--gray-2);
  text-decoration: none;
  border-bottom: 1px solid var(--gray-3);
  padding-bottom: 2px;
  transition: color 0.2s, border-color 0.2s;
}
.hero-links a:hover { color: var(--white); border-color: var(--white); }

.scroll-indicator {
  position: absolute;
  right: 3rem; bottom: 4rem;
  writing-mode: vertical-rl;
  font-family: var(--mono);
  font-size: 0.6rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--gray-3);
  display: flex; align-items: center; gap: 1rem;
}
.scroll-indicator::after {
  content: '';
  display: block; width: 1px; height: 60px;
  background: linear-gradient(to bottom, var(--gray-3), transparent);
  animation: scrollPulse 2s ease infinite;
}
@keyframes scrollPulse {
  0%, 100% { opacity: 0.3; }
  50% { opacity: 1; }
}

/* DIVIDER */
.h-line { width: 100%; height: 1px; background: var(--gray-4); }

/* RELEASES */
#releases {
  padding: 6rem 3rem;
  background: var(--black);
}
.section-head {
  display: flex; justify-content: space-between;
  align-items: baseline; margin-bottom: 4rem;
  border-bottom: 1px solid var(--gray-4);
  padding-bottom: 1.5rem;
}
.section-tag {
  font-family: var(--mono);
  font-size: 0.65rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--gray-2);
}
.section-title {
  font-family: var(--display);
  font-size: clamp(2.5rem, 5vw, 5rem);
  color: var(--white);
  letter-spacing: 0.02em;
  line-height: 1;
}

.releases-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1px;
  background: var(--gray-4);
}
.release-card {
  background: var(--black);
  padding: 2.5rem;
  position: relative; overflow: hidden;
  transition: background 0.3s;
}
.release-card:hover { background: var(--gray-4); }
.release-card::after {
  content: '→';
  position: absolute; top: 2.5rem; right: 2.5rem;
  font-size: 1.2rem;
  color: var(--white);
  opacity: 0;
  transform: translateX(-8px);
  transition: opacity 0.3s, transform 0.3s;
}
.release-card:hover::after { opacity: 0.5; transform: translateX(0); }
.release-year {
  font-family: var(--mono);
  font-size: 0.6rem;
  letter-spacing: 0.2em;
  color: var(--gray-2);
  margin-bottom: 2rem;
  text-transform: uppercase;
}
.release-art {
  width: 100%; aspect-ratio: 1;
  background: var(--gray-4);
  margin-bottom: 1.5rem;
  display: flex; align-items: center; justify-content: center;
  position: relative; overflow: hidden;
}
.release-art-inner {
  font-family: var(--display);
  font-size: 4rem;
  color: var(--gray-3);
  letter-spacing: -0.05em;
  transition: transform 0.4s, color 0.3s;
}
.release-card:hover .release-art-inner {
  transform: scale(1.05);
  color: var(--white);
}
.release-art-lines {
  position: absolute; inset: 0;
  background-image: repeating-linear-gradient(0deg, transparent, transparent 19px, rgba(255,255,255,0.03) 20px);
}
.release-label {
  font-family: var(--mono);
  font-size: 0.6rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--gray-2);
  margin-bottom: 0.5rem;
}
.release-name {
  font-family: var(--display);
  font-size: 1.8rem;
  letter-spacing: 0.05em;
  color: var(--white);
  margin-bottom: 0.4rem;
}
.release-type {
  font-size: 0.75rem;
  color: var(--gray-2);
}

/* TRACKLIST */
#tracks {
  padding: 6rem 3rem;
  background: var(--gray-4);
}
.tracks-list { margin-top: 1rem; }
.track-row {
  display: grid;
  grid-template-columns: 3rem 1fr auto auto;
  align-items: center;
  gap: 1.5rem;
  padding: 1.3rem 0;
  border-bottom: 1px solid rgba(255,255,255,0.06);
  cursor: pointer;
  transition: background 0.2s;
  position: relative;
}
.track-row:first-child { border-top: 1px solid rgba(255,255,255,0.06); }
.track-row:hover { padding-left: 1rem; }
.track-num {
  font-family: var(--mono);
  font-size: 0.7rem;
  color: var(--gray-2);
  opacity: 0.5;
}
.track-title {
  font-family: var(--display);
  font-size: 1.4rem;
  letter-spacing: 0.05em;
  color: var(--white);
  transition: color 0.2s;
}
.track-row:hover .track-title { color: var(--white); }
.track-bpm {
  font-family: var(--mono);
  font-size: 0.62rem;
  color: var(--gray-2);
  letter-spacing: 0.1em;
  text-transform: uppercase;
}
.track-dur {
  font-family: var(--mono);
  font-size: 0.68rem;
  color: var(--gray-2);
}

/* WAVEFORM decoration */
.waveform {
  display: flex; align-items: center;
  gap: 3px; height: 20px;
}
.waveform span {
  display: block; width: 2px;
  background: var(--gray-2);
  border-radius: 1px;
  animation: wave 1.2s ease-in-out infinite;
}
.waveform span:nth-child(1) { height: 6px; animation-delay: 0s; }
.waveform span:nth-child(2) { height: 14px; animation-delay: 0.1s; }
.waveform span:nth-child(3) { height: 10px; animation-delay: 0.2s; }
.waveform span:nth-child(4) { height: 18px; animation-delay: 0.15s; }
.waveform span:nth-child(5) { height: 8px; animation-delay: 0.05s; }
.waveform span:nth-child(6) { height: 14px; animation-delay: 0.25s; }
.waveform span:nth-child(7) { height: 6px; animation-delay: 0.1s; }
@keyframes wave {
  0%, 100% { transform: scaleY(0.5); opacity: 0.3; }
  50% { transform: scaleY(1); opacity: 1; }
}
.waveform-static { animation: none; opacity: 0.2; transform: none !important; }

/* ABOUT */
#about {
  padding: 6rem 3rem;
  background: var(--black);
}
.about-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6rem; margin-top: 4rem;
}
.about-photo-placeholder {
  aspect-ratio: 3/4;
  background: var(--gray-4);
  position: relative; overflow: hidden;
  display: flex; align-items: flex-end;
}
.about-photo-overlay {
  position: absolute; inset: 0;
  background-image: repeating-linear-gradient(
    45deg, transparent, transparent 2px,
    rgba(255,255,255,0.015) 2px, rgba(255,255,255,0.015) 4px
  );
}
.photo-label {
  position: relative;
  padding: 1.5rem;
  font-family: var(--mono);
  font-size: 0.6rem;
  color: var(--gray-2);
  letter-spacing: 0.15em;
  text-transform: uppercase;
  z-index: 1;
}
.about-text .section-title { margin-bottom: 2rem; }
.about-text p {
  font-size: 0.9rem;
  color: var(--gray-2);
  line-height: 2;
  margin-bottom: 1.5rem;
}
.about-text p strong { color: var(--white); font-weight: 400; }
.genre-tags {
  display: flex; flex-wrap: wrap; gap: 0.5rem;
  margin-top: 2.5rem;
}
.genre-tag {
  font-family: var(--mono);
  font-size: 0.6rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--black);
  background: var(--white);
  padding: 0.35rem 0.9rem;
}

/* LABELS */
#labels {
  padding: 4rem 3rem;
  background: var(--gray-4);
  border-top: 1px solid rgba(255,255,255,0.06);
  border-bottom: 1px solid rgba(255,255,255,0.06);
}
.labels-row {
  display: flex; align-items: center;
  gap: 4rem; flex-wrap: wrap;
  margin-top: 2rem;
}
.label-item {
  font-family: var(--display);
  font-size: 1.6rem;
  letter-spacing: 0.08em;
  color: var(--gray-3);
  transition: color 0.3s;
}
.label-item:hover { color: var(--white); }

/* BOOKING / CONTACT */
#contact {
  padding: 8rem 3rem;
  background: var(--black);
  min-height: 80vh;
  display: flex; flex-direction: column;
  justify-content: center;
}
.contact-big {
  font-family: var(--display);
  font-size: clamp(4rem, 12vw, 14rem);
  line-height: 0.88;
  letter-spacing: -0.02em;
  color: var(--white);
  margin-bottom: 3rem;
}
.contact-row {
  display: flex; align-items: flex-end;
  justify-content: space-between; flex-wrap: wrap; gap: 2rem;
}
.contact-sub {
  font-size: 0.875rem;
  color: var(--gray-2);
  max-width: 300px;
  line-height: 1.9;
}
.contact-actions { display: flex; flex-direction: column; gap: 1rem; align-items: flex-end; }
.contact-email {
  font-family: var(--mono);
  font-size: 0.9rem;
  letter-spacing: 0.05em;
  color: var(--white);
  text-decoration: none;
  border-bottom: 1px solid var(--gray-3);
  padding-bottom: 3px;
  transition: border-color 0.2s;
}
.contact-email:hover { border-color: var(--white); }
.social-row {
  display: flex; gap: 1.5rem;
}
.social-row a {
  font-family: var(--mono);
  font-size: 0.6rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--gray-2);
  text-decoration: none;
  transition: color 0.2s;
}
.social-row a:hover { color: var(--white); }

/* FOOTER */
footer {
  padding: 2rem 3rem;
  border-top: 1px solid var(--gray-4);
  display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 1rem;
}
footer p {
  font-family: var(--mono);
  font-size: 0.6rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--gray-3);
}

/* Responsive */
@media (max-width: 768px) {
  nav { padding: 1.5rem; }
  .nav-links { display: none; }
  #hero { padding: 0 1.5rem 3rem; }
  section, #releases, #tracks, #about, #labels, #contact { padding: 4rem 1.5rem; }
  .about-layout { grid-template-columns: 1fr; gap: 3rem; }
  .contact-row { flex-direction: column; align-items: flex-start; }
  .contact-actions { align-items: flex-start; }
  .hero-bg-text { display: none; }
  body { cursor: auto; }
  .cursor, .cursor-ring { display: none; }
  .scroll-indicator { display: none; }
  footer { flex-direction: column; }
}
</style>
</head>
<body>

<div class="cursor" id="cur"></div>
<div class="cursor-ring" id="cur-ring"></div>

<!-- NAV -->
<nav>
  <a href="#hero" class="nav-logo">LC — Artist</a>
  <ul class="nav-links">
    <li><a href="#releases">Releases</a></li>
    <li><a href="#tracks">Tracks</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#contact">Booking</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-bg-text" aria-hidden="true">Leito</div>

  <div class="hero-meta reveal">
    DJ · Producer
  </div>
  <h1 class="hero-name reveal d1">Leonardo<br/>Camilo</h1>

  <div class="hero-bottom">
    <p class="hero-bio reveal d2">
      Productor y DJ underground de <strong>Minimal / Deep Tech</strong>,
      <strong>Deep House</strong> y <strong>Dub Techno</strong>.
      Creando sonidos que viajan entre frecuencias, diálogos analógicos y vistas al futuro.
    </p>
    <div class="hero-links reveal d3">
      <a href="https://www.beatport.com/es/artist/leonardo-camilo/718404" target="_blank">Beatport</a>
      <a href="https://ecoulsnd.bandcamp.com/album/future-view" target="_blank">Bandcamp</a>
      <a href="https://soundcloud.com/ecoul_snd/premiere-leonardo-camilo-future-view" target="_blank">SoundCloud</a>
    </div>
  </div>

  <div class="scroll-indicator">Scroll</div>
</section>

<div class="h-line"></div>

<!-- RELEASES -->
<section id="releases">
  <div class="section-head reveal">
    <span class="section-tag">Discografía</span>
    <h2 class="section-title">Releases</h2>
  </div>

  <div class="releases-grid">
    <a href="https://ecoulsnd.bandcamp.com/album/future-view" target="_blank" style="text-decoration:none;">
      <div class="release-card reveal d1">
        <div class="release-year">2024 — ECOUL SND · ECOUL104</div>
        <div class="release-art">
          <div class="release-art-lines"></div>
          <div class="release-art-inner">FV</div>
        </div>
        <div class="release-label">EP · 4 Tracks</div>
        <div class="release-name">Future View</div>
        <div class="release-type">Minimal / Deep Tech · 127 BPM</div>
      </div>
    </a>

    <div class="release-card reveal d2">
      <div class="release-year">2024 — Simply Minimal Vol. 17</div>
      <div class="release-art">
        <div class="release-art-lines"></div>
        <div class="release-art-inner">SM</div>
      </div>
      <div class="release-label">Compilation · Feature</div>
      <div class="release-name">Simply Minimal</div>
      <div class="release-type">Minimal / Deep Tech</div>
    </div>

    <div class="release-card reveal d3">
      <div class="release-year">2024 — Minimal Taurus</div>
      <div class="release-art">
        <div class="release-art-lines"></div>
        <div class="release-art-inner">MT</div>
      </div>
      <div class="release-label">Compilation · Feature</div>
      <div class="release-name">Minimal Taurus</div>
      <div class="release-type">Minimal / Deep Tech</div>
    </div>
  </div>
</section>

<div class="h-line"></div>

<!-- TRACKLIST -->
<section id="tracks">
  <div class="section-head reveal">
    <span class="section-tag">Future View EP — ECOUL104</span>
    <h2 class="section-title">Tracklist</h2>
  </div>

  <div class="tracks-list">
    <div class="track-row reveal d1">
      <span class="track-num">01</span>
      <span class="track-title">Future View</span>
      <span class="track-bpm">127 BPM · G Min</span>
      <span class="track-dur">06:35</span>
    </div>
    <div class="track-row reveal d2">
      <span class="track-num">02</span>
      <span class="track-title">Analog Dialog</span>
      <span class="track-bpm">Minimal / Deep</span>
      <span class="track-dur">07:14</span>
    </div>
    <div class="track-row reveal d3">
      <span class="track-num">03</span>
      <span class="track-title">Floating Attention</span>
      <span class="track-bpm">Minimal / Deep</span>
      <span class="track-dur">09:06</span>
    </div>
    <div class="track-row reveal d4">
      <span class="track-num">04</span>
      <span class="track-title">Inside Frequencies</span>
      <span class="track-bpm">Minimal / Deep</span>
      <span class="track-dur">10:22</span>
    </div>
  </div>

  <div style="margin-top: 3rem; display: flex; align-items: center; gap: 2rem; flex-wrap: wrap;" class="reveal d5">
    <div class="waveform">
      <span></span><span></span><span></span><span></span><span></span><span></span><span></span>
    </div>
    <a href="https://www.beatport.com/es/artist/leonardo-camilo/718404" target="_blank"
       style="font-family: var(--mono); font-size: 0.65rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--white); text-decoration: none; border-bottom: 1px solid var(--gray-3); padding-bottom: 2px;">
      Escuchar en Beatport →
    </a>
    <a href="https://ecoulsnd.bandcamp.com/album/future-view" target="_blank"
       style="font-family: var(--mono); font-size: 0.65rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--gray-2); text-decoration: none; border-bottom: 1px solid var(--gray-3); padding-bottom: 2px;">
      Descargar en Bandcamp →
    </a>
  </div>
</section>

<div class="h-line"></div>

<!-- ABOUT -->
<section id="about">
  <div class="section-head reveal">
    <span class="section-tag">El artista</span>
    <h2 class="section-title">About</h2>
  </div>

  <div class="about-layout">
    <div class="about-photo-placeholder reveal-left d1">
      <div class="about-photo-overlay"></div>
      <div class="photo-label">Leonardo Camilo — Press Photo</div>
    </div>

    <div class="about-text">
      <p class="reveal d2">
        <strong>Leonardo Camilo</strong> es un productor y DJ underground cuya música
        habita en los límites entre el minimal house clásico, el deep tech y el dub techno.
        Sus composiciones construyen paisajes sonoros hipnóticos que invitan a perderse en
        frecuencias analógicas y texturas profundas.
      </p>
      <p class="reveal d3">
        Su EP <strong>Future View</strong> (ECOUL SND, 2024) consolidó su voz en la
        escena underground global, con pistas como <strong>Inside Frequencies</strong>
        (10:22) que demuestran su dominio del viaje largo y contemplativo en el dancefloor.
      </p>
      <p class="reveal d4">
        También conocido como <strong>L.A. / Leonar.do</strong>, su trabajo aparece en
        compilaciones internacionales como Simply Minimal y Minimal Taurus, junto a artistas
        de la escena dominicana y latinoamericana del minimal.
      </p>
      <div class="genre-tags reveal d5">
        <span class="genre-tag">Minimal</span>
        <span class="genre-tag">Deep Tech</span>
        <span class="genre-tag">Dub Techno</span>
        <span class="genre-tag">Deep House</span>
        <span class="genre-tag">Underground</span>
      </div>
    </div>
  </div>
</section>

<!-- LABELS -->
<section id="labels">
  <p class="section-tag reveal">Sellos & Compilaciones</p>
  <div class="labels-row">
    <span class="label-item reveal d1">ECOUL SND</span>
    <span class="label-item reveal d2">Simply Minimal</span>
    <span class="label-item reveal d3">Minimal Taurus</span>
    <span class="label-item reveal d4">Beatport</span>
    <span class="label-item reveal d5">Bandcamp</span>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <h2 class="contact-big reveal">Booking<br/>&amp; Contact</h2>
  <div class="contact-row">
    <p class="contact-sub reveal d2">
      Para bookings, colaboraciones y prensa.
      También disponible para proyectos de producción y remixes.
    </p>
    <div class="contact-actions reveal d3">
      <a href="mailto:lcamilo656@gmail.com" class="contact-email">
        hola@leonardocamilo.com
      </a>
      <div class="social-row">
        <a href="https://www.beatport.com/es/artist/leonardo-camilo/718404" target="_blank">Beatport</a>
        <a href="https://ecoulsnd.bandcamp.com/album/future-view" target="_blank">Bandcamp</a>
        <a href="https://soundcloud.com/ecoul_snd/premiere-leonardo-camilo-future-view" target="_blank">SoundCloud</a>
        <a href="https://www.instagram.com/leonardo_camilo_dj/" target="_blank">Instagram</a>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <p>© 2026 Leonardo Camilo — All rights reserved</p>
  <p>More for the music than anything</p>
</footer>

<script>
// Cursor
const cur = document.getElementById('cur');
const ring = document.getElementById('cur-ring');
let mx = 0, my = 0, rx = 0, ry = 0;
document.addEventListener('mousemove', e => {
  mx = e.clientX; my = e.clientY;
  cur.style.transform = `translate(${mx-3}px,${my-3}px)`;
});
(function animRing() {
  rx += (mx - rx) * 0.1;
  ry += (my - ry) * 0.1;
  ring.style.transform = `translate(${rx-15}px,${ry-15}px)`;
  requestAnimationFrame(animRing);
})();
document.querySelectorAll('a,[class*=track-row],[class*=release-card]').forEach(el => {
  el.addEventListener('mouseenter', () => { ring.style.width='50px'; ring.style.height='50px'; });
  el.addEventListener('mouseleave', () => { ring.style.width='30px'; ring.style.height='30px'; });
});

// Scroll reveal
const obs = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });
document.querySelectorAll('.reveal,.reveal-left').forEach(el => obs.observe(el));

// Hero reveal on load
window.addEventListener('load', () => {
  document.querySelectorAll('#hero .reveal').forEach((el,i) => {
    setTimeout(() => el.classList.add('visible'), 300 + i * 150);
  });
});

// Track row hover: show waveform
document.querySelectorAll('.track-row').forEach(row => {
  row.addEventListener('mouseenter', () => {
    const num = row.querySelector('.track-num');
    if (num) num.style.opacity = '0';
  });
  row.addEventListener('mouseleave', () => {
    const num = row.querySelector('.track-num');
    if (num) num.style.opacity = '0.5';
  });
});
</script>
</body>
</html>
