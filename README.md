<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>¡Estás invitado! 🍍 Fiesta de Sofía</title>
<meta name="description" content="Invitación a la fiesta de Sofía - 11 de julio en Cabaña #221, Jardines de la Silla">

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@500;600;700&family=Quicksand:wght@400;500;600;700&display=swap" rel="stylesheet">

<style>
/* ===========================================================
   1. VARIABLES Y RESET
   =========================================================== */
:root{
  --deep-sea:#012a4a;
  --mid-sea:#01497c;
  --ocean-blue:#0582ca;
  --turquoise:#2ec4b6;
  --turquoise-light:#8fe9dd;
  --sand:#f4d58d;
  --sand-dark:#dba94f;
  --coral:#ff6f59;
  --coral-dark:#e0503c;
  --sponge-yellow:#ffd23f;
  --sponge-yellow-dark:#f4a300;
  --foam:#eafcff;
  --ink:#013350;

  --font-display:'Fredoka', sans-serif;
  --font-body:'Quicksand', sans-serif;
}

*{ box-sizing:border-box; }
html,body{
  margin:0;
  padding:0;
  width:100%;
  overflow-x:hidden;
  font-family:var(--font-body);
  color:var(--ink);
  -webkit-tap-highlight-color:transparent;
}

/* ===========================================================
   2. ESTRUCTURA GENERAL / FONDO DEL MAR
   =========================================================== */
.page{
  position:relative;
  min-height:100vh;
  overflow:hidden;
}

.ocean-bg{
  position:fixed;
  inset:0;
  z-index:0;
  background:linear-gradient(to bottom,
    var(--turquoise-light) 0%,
    var(--ocean-blue) 32%,
    var(--mid-sea) 62%,
    var(--deep-sea) 100%);
}

/* Rayos de luz que cruzan el agua, efecto "caustic" suave */
.light-rays{
  position:fixed;
  inset:0;
  z-index:1;
  pointer-events:none;
  background:
    linear-gradient(115deg, transparent 30%, rgba(255,255,255,.10) 38%, transparent 46%),
    linear-gradient(115deg, transparent 55%, rgba(255,255,255,.07) 63%, transparent 71%);
  background-size:200% 200%;
  animation:rayos 14s ease-in-out infinite;
  mix-blend-mode:screen;
}
@keyframes rayos{
  0%,100%{ background-position:0% 0%; opacity:.7; }
  50%{ background-position:20% 10%; opacity:1; }
}

/* ===========================================================
   3. BURBUJAS ANIMADAS (capa fija sobre toda la pantalla)
   =========================================================== */
.bubbles-layer{
  position:fixed;
  inset:0;
  z-index:9;
  pointer-events:none;
  overflow:hidden;
}
.bubble{
  position:absolute;
  bottom:-60px;
  border-radius:50%;
  background:radial-gradient(circle at 30% 28%, rgba(255,255,255,.95), rgba(255,255,255,.15) 55%, rgba(255,255,255,.05) 100%);
  border:1px solid rgba(255,255,255,.45);
  box-shadow:inset 0 0 6px rgba(255,255,255,.6);
  opacity:0;
  animation-name:subir;
  animation-timing-function:ease-in;
  animation-fill-mode:forwards;
}
@keyframes subir{
  0%{ transform:translateY(0) translateX(0); opacity:0; }
  8%{ opacity:.85; }
  100%{ transform:translateY(-115vh) translateX(var(--drift,20px)); opacity:0; }
}

/* ===========================================================
   4. ELEMENTOS DECORATIVOS (corales, medusas, estrellas, piña)
   =========================================================== */
.decor-layer{
  position:absolute;
  inset:0;
  height:100%;
  z-index:2;
  pointer-events:none;
}
.decor-layer > *{ position:absolute; }

/* --- Piña de Bob Esponja (casa) --- */
.pineapple-house{
  top:5%;
  right:4%;
  width:clamp(80px,16vw,150px);
  filter:drop-shadow(0 14px 18px rgba(0,0,0,.25));
  animation:flotar 7s ease-in-out infinite;
}
.pineapple-house .leaves{
  position:relative;
  height:42%;
}
.pineapple-house .leaf{
  position:absolute;
  bottom:0;
  left:50%;
  width:32%;
  height:100%;
  background:linear-gradient(180deg,#4ec97a,#1f9e55);
  clip-path:polygon(50% 0%, 100% 100%, 0% 100%);
  transform-origin:bottom center;
}
.pineapple-house .l1{ transform:translateX(-50%) rotate(-45deg); }
.pineapple-house .l2{ transform:translateX(-50%) rotate(-22deg); height:115%; }
.pineapple-house .l3{ transform:translateX(-50%) rotate(0deg); height:130%; }
.pineapple-house .l4{ transform:translateX(-50%) rotate(22deg); height:115%; }
.pineapple-house .l5{ transform:translateX(-50%) rotate(45deg); }

.pineapple-house .body-shape{
  position:relative;
  width:100%;
  height:62%;
  margin-top:-6%;
  border-radius:50% 50% 46% 46% / 62% 62% 42% 42%;
  background:
    repeating-linear-gradient(45deg, rgba(0,0,0,.14) 0 3px, transparent 3px 13px),
    repeating-linear-gradient(-45deg, rgba(0,0,0,.14) 0 3px, transparent 3px 13px),
    linear-gradient(180deg, var(--sponge-yellow) 0%, var(--sponge-yellow-dark) 100%);
  box-shadow:inset 0 -10px 16px rgba(0,0,0,.18), inset 0 8px 10px rgba(255,255,255,.25);
}
.pineapple-house .window{
  position:absolute;
  top:22%; left:50%;
  width:26%; aspect-ratio:1;
  transform:translateX(-50%);
  background:#cdeff5;
  border:3px solid #fff;
  border-radius:50%;
  box-shadow:0 0 0 2px rgba(0,0,0,.15);
}
.pineapple-house .window::before,
.pineapple-house .window::after{
  content:'';
  position:absolute;
  background:#fff;
}
.pineapple-house .window::before{ top:0;bottom:0;left:48%;width:8%; }
.pineapple-house .window::after{ left:0;right:0;top:48%;height:8%; }
.pineapple-house .door{
  position:absolute;
  bottom:0; left:50%;
  width:22%; height:34%;
  transform:translateX(-50%);
  background:#a85b2e;
  border-radius:50% 50% 0 0;
  border:2px solid rgba(0,0,0,.2);
}

/* --- Corales --- */
.coral{ width:90px; height:90px; animation:flotar 6s ease-in-out infinite, balancear 5s ease-in-out infinite; }
.coral .rama{
  position:absolute;
  bottom:0;
  width:16px;
  border-radius:40px 40px 12px 12px;
  background:linear-gradient(180deg, var(--coral), var(--coral-dark));
  box-shadow:inset -3px 0 4px rgba(255,255,255,.25);
}
.coral-a{ bottom:14%; left:2%; }
.coral-a .r1{ left:10%; height:70px; transform:rotate(-12deg); }
.coral-a .r2{ left:38%; height:90px; }
.coral-a .r3{ left:62%; height:65px; transform:rotate(14deg); }

.coral-b{ bottom:8%; right:4%; width:80px; }
.coral-b .r1{ left:5%; height:60px; transform:rotate(-16deg); background:linear-gradient(180deg,var(--sponge-yellow),var(--sponge-yellow-dark)); }
.coral-b .r2{ left:34%; height:80px; }
.coral-b .r3{ left:60%; height:55px; transform:rotate(18deg); background:linear-gradient(180deg,var(--turquoise-light),var(--turquoise)); }

.coral-c{ bottom:2%; left:22%; width:60px; }
.coral-c .r1{ left:12%; height:46px; transform:rotate(-10deg); background:linear-gradient(180deg,var(--turquoise-light),var(--turquoise)); }
.coral-c .r2{ left:40%; height:58px; }

@keyframes balancear{
  0%,100%{ transform:rotate(-2deg); }
  50%{ transform:rotate(2deg); }
}

/* --- Medusas --- */
.jellyfish{ width:60px; animation:flotarMedusa 7s ease-in-out infinite; }
.jellyfish .cupula{
  width:100%; height:75%;
  border-radius:50% 50% 45% 45%;
  background:radial-gradient(circle at 35% 30%, rgba(255,255,255,.85), rgba(143,233,221,.55) 55%, rgba(46,196,182,.35) 100%);
  box-shadow:0 0 18px rgba(143,233,221,.55);
}
.jellyfish .tentaculos{ display:flex; justify-content:center; gap:5px; margin-top:-4px; }
.jellyfish .tentaculo{
  width:4px; height:30px;
  border-radius:0 0 6px 6px;
  background:linear-gradient(180deg, rgba(143,233,221,.7), rgba(143,233,221,.05));
  transform-origin:top center;
  animation:tentaculoOnda 2.6s ease-in-out infinite;
}
.jellyfish .tentaculo:nth-child(2){ animation-delay:.2s; height:38px; }
.jellyfish .tentaculo:nth-child(3){ animation-delay:.4s; height:26px; }
.jellyfish .tentaculo:nth-child(4){ animation-delay:.6s; height:34px; }
.jellyfish .tentaculo:nth-child(5){ animation-delay:.8s; }

.jelly-a{ top:16%; left:6%; }
.jelly-b{ top:42%; right:8%; width:48px; animation-duration:9s; }

@keyframes tentaculoOnda{
  0%,100%{ transform:rotate(-8deg); }
  50%{ transform:rotate(8deg); }
}
@keyframes flotarMedusa{
  0%,100%{ transform:translateY(0); }
  50%{ transform:translateY(18px); }
}

/* --- Estrellas de mar --- */
.starfish{
  width:42px; height:42px;
  background:linear-gradient(160deg, var(--sponge-yellow), var(--coral));
  clip-path:polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
  box-shadow:0 6px 10px rgba(0,0,0,.2);
  animation:flotar 5s ease-in-out infinite, girar 9s linear infinite;
}
.star-a{ bottom:10%; left:42%; width:34px; height:34px; }
.star-b{ bottom:18%; right:22%; }
.star-c{ top:64%; left:4%; width:28px; height:28px; animation-duration:6s; }

@keyframes flotar{
  0%,100%{ transform:translateY(0); }
  50%{ transform:translateY(-14px); }
}
@keyframes girar{
  0%{ transform:rotate(0deg); }
  100%{ transform:rotate(360deg); }
}

/* ===========================================================
   5. ARENA EN LA PARTE INFERIOR
   =========================================================== */
.sand{
  position:fixed;
  left:0; right:0; bottom:0;
  z-index:3;
  pointer-events:none;
  width:100%;
}
.sand svg{ display:block; width:100%; height:auto; }
.sand-fill{
  height:clamp(60px,12vh,110px);
  background:
    radial-gradient(circle at 12% 30%, rgba(0,0,0,.06) 0 3px, transparent 4px) 0 0/40px 40px,
    radial-gradient(circle at 70% 60%, rgba(0,0,0,.06) 0 3px, transparent 4px) 0 0/55px 55px,
    linear-gradient(180deg, var(--sand) 0%, var(--sand-dark) 100%);
  margin-top:-2px;
}

/* ===========================================================
   6. CONTENIDO PRINCIPAL
   =========================================================== */
.container{
  position:relative;
  z-index:5;
  display:flex;
  flex-direction:column;
  align-items:center;
  width:100%;
  min-height:100vh;
  padding:clamp(1.5rem,5vw,3rem) clamp(1rem,5vw,2rem) clamp(11rem,18vh,14rem);
  gap:2rem;
}

/* --- Tarjeta de invitación (glassmorphism) --- */
.invitation-card{
  position:relative;
  width:100%;
  max-width:560px;
  margin-top:clamp(1rem,6vh,3rem);
  padding:clamp(1.8rem,5vw,3rem) clamp(1.4rem,5vw,2.6rem);
  text-align:center;
  background:linear-gradient(160deg, rgba(255,255,255,.38), rgba(255,255,255,.12));
  border:1px solid rgba(255,255,255,.5);
  border-radius:28px;
  box-shadow:0 25px 60px rgba(1,42,74,.45), inset 0 1px 0 rgba(255,255,255,.55);
  backdrop-filter:blur(18px) saturate(160%);
  -webkit-backdrop-filter:blur(18px) saturate(160%);
  opacity:0;
  transform:translateY(40px) scale(.96);
  animation:aparecer 1s cubic-bezier(.22,1,.36,1) .15s forwards;
}

@keyframes aparecer{
  to{ opacity:1; transform:translateY(0) scale(1); }
}

.eyebrow{
  display:inline-block;
  margin:0 0 .9rem;
  padding:.35rem 1rem;
  font-family:var(--font-display);
  font-size:.78rem;
  letter-spacing:.06em;
  text-transform:uppercase;
  color:var(--ink);
  background:rgba(255,255,255,.55);
  border-radius:999px;
  box-shadow:0 4px 10px rgba(1,42,74,.15);
}

.title{
  margin:0 0 .5rem;
  font-family:var(--font-display);
  font-weight:700;
  font-size:clamp(1.9rem,6vw,2.7rem);
  color:var(--ink);
  text-shadow:0 2px 0 rgba(255,255,255,.5), 0 0 22px rgba(46,196,182,.35);
}

.subtitle{
  margin:0 0 1.6rem;
  font-size:clamp(1rem,3vw,1.15rem);
  font-weight:600;
  color:var(--mid-sea);
}

/* --- Detalles del evento --- */
.details{
  display:flex;
  flex-direction:column;
  gap:1rem;
  text-align:left;
  margin-bottom:1.6rem;
}
.detail-item{
  display:flex;
  align-items:flex-start;
  gap:.85rem;
  opacity:0;
  transform:translateY(16px);
  animation:aparecer .7s ease forwards;
  animation-delay:calc(var(--d) * .15s + .55s);
}
.detail-item .icon{
  flex:0 0 auto;
  display:flex;
  align-items:center;
  justify-content:center;
  width:2.6rem; height:2.6rem;
  font-size:1.3rem;
  border-radius:50%;
  background:rgba(255,255,255,.5);
  box-shadow:inset 0 0 0 1px rgba(255,255,255,.6);
}
.detail-item .label{
  display:block;
  font-family:var(--font-display);
  font-size:.72rem;
  letter-spacing:.05em;
  text-transform:uppercase;
  color:var(--coral-dark);
}
.detail-item .value{
  display:block;
  font-size:clamp(.95rem,2.6vw,1.05rem);
  font-weight:600;
  color:var(--ink);
  line-height:1.4;
}

.host{
  margin:0 0 1.8rem;
  font-family:var(--font-display);
  font-size:1.1rem;
  color:var(--coral-dark);
}

/* --- Botones --- */
.actions{
  display:flex;
  flex-direction:column;
  gap:.9rem;
}
.btn{
  position:relative;
  overflow:hidden;
  display:flex;
  align-items:center;
  justify-content:center;
  gap:.6rem;
  width:100%;
  padding:1rem 1.4rem;
  border:none;
  border-radius:16px;
  font-family:var(--font-display);
  font-weight:600;
  font-size:clamp(.98rem,2.6vw,1.1rem);
  text-decoration:none;
  cursor:pointer;
  transition:transform .15s ease, box-shadow .25s ease;
}
.btn .btn-icon{ font-size:1.2rem; }

/* Botón de ubicación: grande, con brillo al pasar el cursor */
.btn-location{
  color:#1f2b1f;
  background:linear-gradient(135deg, var(--sponge-yellow), var(--coral));
  box-shadow:0 12px 26px rgba(244,163,0,.45);
}
.btn-location::before{
  content:'';
  position:absolute;
  top:0; left:-75%;
  width:50%; height:100%;
  background:linear-gradient(120deg, transparent, rgba(255,255,255,.75), transparent);
  transform:skewX(-25deg);
  transition:left .65s ease;
}
.btn-location:hover::before{ left:125%; }
.btn-location:hover{
  transform:translateY(-3px);
  box-shadow:0 16px 34px rgba(244,163,0,.6), 0 0 28px rgba(255,210,63,.55);
}
.btn-location:active{
  transform:translateY(0) scale(.96);
  box-shadow:0 6px 14px rgba(244,163,0,.45);
}

/* Botón RSVP */
.btn-rsvp{
  color:var(--ink);
  background:rgba(255,255,255,.35);
  border:2px solid var(--turquoise);
}
.btn-rsvp:hover{
  background:rgba(255,255,255,.55);
  transform:translateY(-2px);
}
.btn-rsvp:active{ transform:scale(.96); }
.btn-rsvp.confirmado{
  background:linear-gradient(135deg, var(--turquoise), var(--turquoise-light));
  border-color:transparent;
  color:#03392f;
  animation:confirmarPop .45s ease;
}
@keyframes confirmarPop{
  0%{ transform:scale(.9); }
  50%{ transform:scale(1.05); }
  100%{ transform:scale(1); }
}

.rsvp-msg{
  min-height:1.4rem;
  margin:.9rem 0 0;
  font-weight:700;
  color:#01664f;
}

/* --- Mensaje final --- */
.final-message{
  position:relative;
  max-width:480px;
  margin:0 auto;
  padding:0 1rem;
  text-align:center;
  font-family:var(--font-display);
  font-size:clamp(1.05rem,3.4vw,1.4rem);
  color:var(--foam);
  text-shadow:0 2px 10px rgba(0,0,0,.35);
  opacity:0;
  transform:translateY(20px);
  animation:aparecer .8s ease 1.1s forwards;
}

/* ===========================================================
   7. PARTÍCULAS DE CONFIRMACIÓN (RSVP)
   =========================================================== */
.party-bubble{
  position:fixed;
  border-radius:50%;
  pointer-events:none;
  z-index:50;
  animation:partyPop .85s ease-out forwards;
}
@keyframes partyPop{
  0%{ transform:translate(0,0) scale(1); opacity:1; }
  100%{ transform:translate(var(--tx,0), var(--ty,-60px)) scale(0); opacity:0; }
}

/* ===========================================================
   8. RESPONSIVE
   =========================================================== */
@media (max-width:520px){
  .pineapple-house{ width:clamp(64px,22vw,100px); top:3%; right:3%; opacity:.9; }
  .jelly-b, .coral-c, .star-c{ display:none; }
  .coral, .jellyfish{ transform:scale(.85); }
  .invitation-card{ border-radius:22px; }
}

@media (min-width:1024px){
  .invitation-card{ max-width:620px; }
  .container{ gap:2.5rem; }
}

/* Respeta la preferencia de "menos movimiento" del usuario */
@media (prefers-reduced-motion: reduce){
  *, *::before, *::after{
    animation-duration:.001ms !important;
    animation-iteration-count:1 !important;
    transition-duration:.001ms !important;
  }
}

/* Foco visible para accesibilidad con teclado */
a:focus-visible, button:focus-visible{
  outline:3px solid var(--foam);
  outline-offset:3px;
}
</style>
</head>
<body>

<div class="page">

  <!-- Fondo del mar -->
  <div class="ocean-bg" aria-hidden="true"></div>
  <div class="light-rays" aria-hidden="true"></div>

  <!-- Elementos decorativos: piña, corales, medusas, estrellas -->
  <div class="decor-layer" aria-hidden="true">

    <div class="pineapple-house">
      <div class="leaves">
        <span class="leaf l1"></span>
        <span class="leaf l2"></span>
        <span class="leaf l3"></span>
        <span class="leaf l4"></span>
        <span class="leaf l5"></span>
      </div>
      <div class="body-shape">
        <div class="window"></div>
        <div class="door"></div>
      </div>
    </div>

    <div class="coral coral-a">
      <span class="rama r1"></span><span class="rama r2"></span><span class="rama r3"></span>
    </div>
    <div class="coral coral-b">
      <span class="rama r1"></span><span class="rama r2"></span><span class="rama r3"></span>
    </div>
    <div class="coral coral-c">
      <span class="rama r1"></span><span class="rama r2"></span>
    </div>

    <div class="jellyfish jelly-a">
      <div class="cupula"></div>
      <div class="tentaculos">
        <span class="tentaculo"></span><span class="tentaculo"></span><span class="tentaculo"></span>
        <span class="tentaculo"></span><span class="tentaculo"></span>
      </div>
    </div>
    <div class="jellyfish jelly-b">
      <div class="cupula"></div>
      <div class="tentaculos">
        <span class="tentaculo"></span><span class="tentaculo"></span><span class="tentaculo"></span>
        <span class="tentaculo"></span>
      </div>
    </div>

    <div class="starfish star-a"></div>
    <div class="starfish star-b"></div>
    <div class="starfish star-c"></div>
  </div>

  <!-- Capa de burbujas (se llena dinámicamente con JavaScript) -->
  <div class="bubbles-layer" id="bubblesLayer" aria-hidden="true"></div>

  <!-- Contenido principal -->
  <main class="container">

    <section class="invitation-card" id="invitationCard">
      <span class="eyebrow">🐚 Fondo de Bikini te invita 🐚</span>
      <h1 class="title">¡Estás invitado(a)!</h1>
      <p class="subtitle">Te invito a celebrar mi fiesta.</p>

      <div class="details">
        <div class="detail-item" style="--d:1">
          <span class="icon">📅</span>
          <div>
            <span class="label">Fecha</span>
            <span class="value">11 de julio</span>
          </div>
        </div>

        <div class="detail-item" style="--d:2">
          <span class="icon">🕑</span>
          <div>
            <span class="label">Hora</span>
            <span class="value">2:00 p.m. a 11:00 p.m.</span>
          </div>
        </div>

        <div class="detail-item" style="--d:3">
          <span class="icon">📍</span>
          <div>
            <span class="label">Lugar</span>
            <span class="value">Cabaña #221, Jardines de la Silla</span>
          </div>
        </div>

        <div class="detail-item" style="--d:4">
          <span class="icon">🎁</span>
          <div>
            <span class="label">Detalle</span>
            <span class="value">Puedes traer un regalo si lo deseas, pero tu presencia es lo más importante.</span>
          </div>
        </div>
      </div>

      <p class="host">Con cariño, <strong>Sofía</strong> 🌟</p>

      <div class="actions">
        <a class="btn btn-location"
           href="https://maps.app.goo.gl/pi2tL57K74bA7LVv7?g_st=aw"
           target="_blank"
           rel="noopener noreferrer">
          <span class="btn-icon">📍</span> Abrir ubicación en Google Maps
        </a>

        <button class="btn btn-rsvp" id="rsvpBtn" type="button">
          <span class="btn-icon">✅</span> Confirmar asistencia
        </button>
      </div>

      <p class="rsvp-msg" id="rsvpMsg" aria-live="polite"></p>
    </section>

    <p class="final-message">¡Te esperamos para pasar un día increíble en Fondo de Bikini! 🌊🍍</p>

  </main>

  <!-- Arena en la parte inferior