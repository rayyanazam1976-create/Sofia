<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Sofia — With All My Heart</title>
<script src="https://cdn.tailwindcss.com"></script>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400;1,600&family=Playfair+Display:ital,wght@0,400;0,700;1,400;1,700&family=Crimson+Pro:ital,wght@0,300;0,400;1,300;1,400&display=swap" rel="stylesheet">

<style>
  :root {
    --blush: #f4c2c2;
    --rose-gold: #b76e79;
    --deep-rose: #8b3a4a;
    --burgundy: #5c1a2e;
    --cream: #fdf6f0;
    --petal: #fce8e8;
    --gold: #c9a96e;
    --warm-white: #fffaf7;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Crimson Pro', serif;
    background: var(--cream);
    color: var(--burgundy);
    overflow-x: hidden;
    cursor: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='24' height='24' viewBox='0 0 24 24'%3E%3Cpath fill='%23b76e79' d='M12 21.593c-5.63-5.539-11-10.297-11-14.402 0-3.791 3.068-5.191 5.281-5.191 1.312 0 4.151.501 5.719 4.457 1.59-3.968 4.464-4.447 5.726-4.447 2.54 0 5.274 1.621 5.274 5.181 0 4.069-5.136 8.625-11 14.402z'/%3E%3C/svg%3E"), auto;
  }

  /* ─── Pages ─── */
  .page {
    position: fixed;
    inset: 0;
    opacity: 0;
    pointer-events: none;
    transform: translateY(40px);
    transition: opacity 0.9s cubic-bezier(.4,0,.2,1), transform 0.9s cubic-bezier(.4,0,.2,1);
    overflow-y: auto;
    overflow-x: hidden;
  }
  .page.active {
    opacity: 1;
    pointer-events: all;
    transform: translateY(0);
    z-index: 10;
  }
  .page.exit {
    opacity: 0;
    transform: translateY(-40px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }

  /* ─── Background petals ─── */
  .petal-bg {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 0;
    overflow: hidden;
  }
  .petal {
    position: absolute;
    width: 12px;
    height: 12px;
    background: radial-gradient(circle at 30% 30%, #fce8e8, #f4c2c2);
    border-radius: 50% 0 50% 0;
    animation: petalFall linear infinite;
    opacity: 0;
  }
  @keyframes petalFall {
    0%   { transform: translateY(-20px) rotate(0deg); opacity: 0; }
    10%  { opacity: 0.6; }
    90%  { opacity: 0.4; }
    100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
  }

  /* ─── Typography ─── */
  .font-display { font-family: 'Playfair Display', serif; }
  .font-serif   { font-family: 'Cormorant Garamond', serif; }
  .font-body    { font-family: 'Crimson Pro', serif; }

  /* ─── Ornamental divider ─── */
  .ornament {
    display: flex;
    align-items: center;
    gap: 12px;
    color: var(--rose-gold);
  }
  .ornament::before, .ornament::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--rose-gold), transparent);
  }

  /* ─── Cards ─── */
  .memory-card {
    background: linear-gradient(135deg, rgba(255,255,255,0.9), rgba(252,232,232,0.6));
    border: 1px solid rgba(183,110,121,0.2);
    border-radius: 20px;
    padding: 28px;
    backdrop-filter: blur(8px);
    box-shadow: 0 8px 32px rgba(140,58,74,0.1);
    transition: transform 0.4s ease, box-shadow 0.4s ease;
    position: relative;
    overflow: hidden;
  }
  .memory-card::before {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(circle at center, rgba(201,169,110,0.08) 0%, transparent 60%);
    pointer-events: none;
  }
  .memory-card:hover {
    transform: translateY(-6px) rotate(0.5deg);
    box-shadow: 0 20px 48px rgba(140,58,74,0.18);
  }

  /* ─── Nav ─── */
  .nav-dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: rgba(183,110,121,0.3);
    border: 1.5px solid var(--rose-gold);
    transition: all 0.4s ease;
    cursor: pointer;
  }
  .nav-dot.active {
    background: var(--rose-gold);
    transform: scale(1.4);
  }

  /* ─── Buttons ─── */
  .btn-primary {
    background: linear-gradient(135deg, var(--rose-gold), var(--deep-rose));
    color: white;
    border: none;
    padding: 14px 36px;
    border-radius: 50px;
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.1rem;
    font-weight: 600;
    letter-spacing: 1px;
    cursor: pointer;
    transition: all 0.4s ease;
    box-shadow: 0 4px 20px rgba(140,58,74,0.3);
    position: relative;
    overflow: hidden;
  }
  .btn-primary::before {
    content: '';
    position: absolute;
    top: 0; left: -100%;
    width: 100%; height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
    transition: left 0.5s ease;
  }
  .btn-primary:hover::before { left: 100%; }
  .btn-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 32px rgba(140,58,74,0.45);
  }

  .btn-secondary {
    background: transparent;
    color: var(--deep-rose);
    border: 1.5px solid var(--rose-gold);
    padding: 13px 34px;
    border-radius: 50px;
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.1rem;
    font-weight: 600;
    letter-spacing: 1px;
    cursor: pointer;
    transition: all 0.4s ease;
  }
  .btn-secondary:hover {
    background: rgba(183,110,121,0.1);
    transform: translateY(-2px);
  }

  /* ─── Inputs ─── */
  .romantic-input {
    width: 100%;
    background: rgba(255,255,255,0.7);
    border: none;
    border-bottom: 2px solid var(--blush);
    padding: 12px 4px;
    font-family: 'Crimson Pro', serif;
    font-size: 1.05rem;
    color: var(--burgundy);
    outline: none;
    transition: border-color 0.3s ease;
    backdrop-filter: blur(4px);
    resize: none;
  }
  .romantic-input:focus {
    border-bottom-color: var(--rose-gold);
  }
  .romantic-input::placeholder {
    color: rgba(140,58,74,0.35);
    font-style: italic;
  }

  /* ─── Heart pulse ─── */
  @keyframes heartbeat {
    0%, 100% { transform: scale(1); }
    14% { transform: scale(1.15); }
    28% { transform: scale(1); }
    42% { transform: scale(1.08); }
    70% { transform: scale(1); }
  }
  .heart-pulse { animation: heartbeat 2.4s ease-in-out infinite; }

  /* ─── Fade in stagger ─── */
  .stagger-child {
    opacity: 0;
    transform: translateY(24px);
    animation: staggerIn 0.7s forwards;
  }
  @keyframes staggerIn {
    to { opacity: 1; transform: translateY(0); }
  }

  /* ─── Progress bar ─── */
  #progress-bar {
    position: fixed;
    top: 0; left: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--blush), var(--rose-gold), var(--gold));
    transition: width 0.6s ease;
    z-index: 100;
  }

  /* ─── Music button ─── */
  #music-btn {
    position: fixed;
    bottom: 24px;
    left: 24px;
    z-index: 200;
    width: 48px; height: 48px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--rose-gold), var(--deep-rose));
    border: none;
    cursor: pointer;
    display: flex; align-items: center; justify-content: center;
    box-shadow: 0 4px 16px rgba(140,58,74,0.35);
    transition: transform 0.3s ease;
    color: white;
    font-size: 18px;
  }
  #music-btn:hover { transform: scale(1.1); }

  /* ─── Page 1 hero ─── */
  .hero-bg {
    background: linear-gradient(160deg, #fff5f5 0%, #fce8e8 40%, #f8d7d7 70%, #f0c0c0 100%);
    min-height: 100vh;
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 40px 20px;
  }

  .rose-circle {
    width: 280px;
    height: 280px;
    border-radius: 50%;
    background: linear-gradient(135deg, rgba(244,194,194,0.5), rgba(183,110,121,0.2));
    border: 2px solid rgba(183,110,121,0.3);
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    box-shadow: 0 0 60px rgba(183,110,121,0.2), inset 0 0 40px rgba(255,255,255,0.4);
    overflow: hidden;
  }
  .rose-circle::after {
    content: '';
    position: absolute;
    inset: -6px;
    border-radius: 50%;
    border: 1px solid rgba(201,169,110,0.3);
  }
  .photo-placeholder {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: var(--rose-gold);
    font-size: 3rem;
    gap: 8px;
  }
  .photo-placeholder small {
    font-family: 'Crimson Pro', serif;
    font-size: 0.75rem;
    color: var(--rose-gold);
    opacity: 0.7;
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  /* ─── Floating hearts ─── */
  .floating-heart {
    position: absolute;
    pointer-events: none;
    animation: floatUp 4s ease-in-out infinite;
    opacity: 0.15;
  }
  @keyframes floatUp {
    0%, 100% { transform: translateY(0) rotate(-5deg); opacity: 0.15; }
    50% { transform: translateY(-20px) rotate(5deg); opacity: 0.3; }
  }

  /* ─── Timeline ─── */
  .timeline-line {
    position: absolute;
    left: 50%;
    top: 0; bottom: 0;
    width: 1px;
    background: linear-gradient(to bottom, transparent, var(--blush), var(--rose-gold), var(--blush), transparent);
    transform: translateX(-50%);
  }
  .timeline-dot {
    width: 14px; height: 14px;
    border-radius: 50%;
    background: var(--rose-gold);
    border: 3px solid var(--cream);
    box-shadow: 0 0 0 2px var(--rose-gold);
    flex-shrink: 0;
  }

  /* ─── Love reasons ─── */
  .love-item {
    display: flex;
    align-items: flex-start;
    gap: 16px;
    padding: 20px;
    border-radius: 16px;
    transition: background 0.3s ease;
  }
  .love-item:hover {
    background: rgba(244,194,194,0.2);
  }

  /* ─── Promise items ─── */
  .promise-item {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 18px 24px;
    background: rgba(255,255,255,0.7);
    border-left: 3px solid var(--rose-gold);
    border-radius: 0 16px 16px 0;
    margin-bottom: 12px;
    font-size: 1.05rem;
    transition: transform 0.3s ease;
  }
  .promise-item:hover { transform: translateX(6px); }

  /* ─── Celebration overlay ─── */
  #celebration, #gentle-msg {
    display: none;
    position: fixed;
    inset: 0;
    z-index: 300;
    align-items: center;
    justify-content: center;
    backdrop-filter: blur(10px);
  }
  #celebration { background: rgba(252,232,232,0.95); }
  #gentle-msg   { background: rgba(253,246,240,0.95); }

  /* ─── Confetti ─── */
  .confetti-piece {
    position: fixed;
    width: 10px; height: 10px;
    opacity: 0;
    animation: confettiFall 3s ease-in forwards;
    border-radius: 2px;
  }
  @keyframes confettiFall {
    0%   { transform: translateY(-10px) rotate(0deg); opacity: 1; }
    100% { transform: translateY(110vh) rotate(720deg); opacity: 0; }
  }

  /* ─── Scrollbar ─── */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--cream); }
  ::-webkit-scrollbar-thumb {
    background: linear-gradient(var(--blush), var(--rose-gold));
    border-radius: 3px;
  }

  /* ─── Responsive ─── */
  @media (max-width: 640px) {
    .timeline-line { left: 20px; }
    .timeline-item-left, .timeline-item-right { margin-left: 40px !important; margin-right: 0 !important; }
    .rose-circle { width: 220px; height: 220px; }
  }

  /* ─── Page scroll ─── */
  .page-scroll { height: 100vh; overflow-y: auto; overflow-x: hidden; }

  /* pulse ring */
  @keyframes pulseRing {
    0%   { box-shadow: 0 0 0 0 rgba(183,110,121,0.4); }
    70%  { box-shadow: 0 0 0 20px rgba(183,110,121,0); }
    100% { box-shadow: 0 0 0 0 rgba(183,110,121,0); }
  }
  .pulse-ring { animation: pulseRing 2s ease-out infinite; }
</style>
</head>
<body>

<!-- Progress bar -->
<div id="progress-bar" style="width:16.66%"></div>

<!-- Falling petals -->
<div class="petal-bg" id="petals"></div>

<!-- Music button -->
<button id="music-btn" title="Play/Pause music" onclick="toggleMusic()">♪</button>

<!-- Background music (looping piano tone via Web Audio) -->
<audio id="bg-music" loop>
  <!-- Uses a free royalty-free piano ambience -->
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3" type="audio/mpeg">
</audio>

<!-- Navigation dots -->
<div style="position:fixed;right:20px;top:50%;transform:translateY(-50%);z-index:100;display:flex;flex-direction:column;gap:10px;" id="nav-dots">
  <div class="nav-dot active" onclick="goToPage(0)" title="Home"></div>
  <div class="nav-dot" onclick="goToPage(1)" title="Our Story"></div>
  <div class="nav-dot" onclick="goToPage(2)" title="Why I Love You"></div>
  <div class="nav-dot" onclick="goToPage(3)" title="My Apology"></div>
  <div class="nav-dot" onclick="goToPage(4)" title="Questions"></div>
  <div class="nav-dot" onclick="goToPage(5)" title="My Promise"></div>
</div>

<!-- ════════════════════════════════════
     PAGE 1 — HERO
════════════════════════════════════ -->
<div class="page active" id="page-0">
  <div class="hero-bg page-scroll">
    <!-- Floating decorative hearts -->
    <span class="floating-heart" style="top:10%;left:8%;font-size:2rem;">🌸</span>
    <span class="floating-heart" style="top:20%;right:10%;font-size:1.4rem;animation-delay:-1.5s;">🌹</span>
    <span class="floating-heart" style="bottom:15%;left:12%;font-size:1.2rem;animation-delay:-2s;">✿</span>
    <span class="floating-heart" style="bottom:20%;right:8%;font-size:1.8rem;animation-delay:-0.8s;">🌺</span>

    <div class="text-center z-10 flex flex-col items-center gap-8 py-16" style="max-width:680px;margin:0 auto;">

      <!-- Photo circle -->
      <div class="rose-circle heart-pulse pulse-ring" style="animation-delay:0s;">
        <!-- ★ REPLACE this div with <img src="sofia-photo.jpg" style="width:100%;height:100%;object-fit:cover;border-radius:50%;"> -->
        <div class="photo-placeholder">
          <span>🌹</span>
          <small>Place Sofia's photo here</small>
        </div>
      </div>

      <!-- Name -->
      <div class="stagger-child" style="animation-delay:0.2s;">
        <p class="font-serif text-sm tracking-widest uppercase" style="color:var(--rose-gold);letter-spacing:5px;">For the love of my life</p>
        <h1 class="font-display text-7xl md:text-8xl font-bold italic" style="color:var(--burgundy);text-shadow:0 2px 20px rgba(140,58,74,0.15);line-height:1.1;">Sofia</h1>
        <div class="ornament mt-2"><span style="font-size:1.4rem;color:var(--rose-gold);">♥</span></div>
      </div>

      <!-- Opening message -->
      <div class="stagger-child" style="animation-delay:0.5s;padding:32px 28px;background:rgba(255,255,255,0.65);border-radius:24px;border:1px solid rgba(183,110,121,0.18);backdrop-filter:blur(12px);box-shadow:0 8px 32px rgba(140,58,74,0.08);">
        <p class="font-serif text-xl md:text-2xl italic" style="color:var(--deep-rose);line-height:1.8;font-weight:300;">
          My dearest Sofia,
        </p>
        <p class="font-body text-lg mt-4" style="color:var(--burgundy);line-height:1.9;font-size:1.1rem;">
          Some feelings are too immense for a single word, too deep for a single breath. What I feel for you, what I have <em>always</em> felt for you, belongs to that category. I built this little world of words and memories just for you — because you deserve more than a sorry whispered in the dark. You deserve a sunrise made of everything I never said.
        </p>
        <p class="font-serif text-lg italic mt-4" style="color:var(--rose-gold);">
          Please, take my hand. Walk through this with me. ♥
        </p>
      </div>

      <!-- Signature -->
      <p class="stagger-child font-display italic text-2xl" style="color:var(--rose-gold);animation-delay:0.8s;">— Rayyan</p>

      <!-- CTA -->
      <button class="btn-primary stagger-child" style="animation-delay:1s;" onclick="goToPage(1)">
        Begin Our Journey &nbsp;→
      </button>

    </div>
  </div>
</div>


<!-- ════════════════════════════════════
     PAGE 2 — OUR BEAUTIFUL STORY
════════════════════════════════════ -->
<div class="page" id="page-1">
  <div class="page-scroll" style="background:linear-gradient(180deg,#fff8f8,#fce8e8 30%,#fff5f0 70%,#fdf6f0);">
    <div style="max-width:780px;margin:0 auto;padding:60px 24px 100px;">

      <div class="text-center mb-12">
        <p class="font-serif italic text-sm tracking-widest uppercase" style="color:var(--rose-gold);letter-spacing:4px;">Chapter Two</p>
        <h2 class="font-display text-5xl md:text-6xl font-bold" style="color:var(--burgundy);">Our Beautiful Story</h2>
        <div class="ornament mt-4"><span style="color:var(--rose-gold);">✦ ♥ ✦</span></div>
        <p class="font-body text-lg mt-4" style="color:var(--deep-rose);line-height:1.8;max-width:520px;margin:16px auto 0;">
          Every love story is beautiful, but ours is my favourite. Here are the chapters of my heart — written in the ink of our shared days.
        </p>
      </div>

      <!-- Timeline -->
      <div class="relative">
        <div class="timeline-line hidden md:block"></div>

        <!-- Memory 1 -->
        <div class="flex md:justify-end mb-10 timeline-item-left" style="margin-right:0;md:margin-right:calc(50% + 20px)">
          <div class="memory-card" style="max-width:340px;">
            <div class="flex items-center gap-3 mb-3">
              <span style="font-size:1.6rem;">🌸</span>
              <div>
                <p class="font-display font-bold text-lg" style="color:var(--deep-rose);">The Very First Glance</p>
                <p class="text-xs tracking-wider uppercase" style="color:var(--rose-gold);letter-spacing:2px;">The Beginning</p>
              </div>
            </div>
            <!-- ★ CUSTOMIZE: Replace with your real story -->
            <p class="font-body" style="line-height:1.8;color:var(--burgundy);">
              I still remember the exact moment I saw you for the first time. The world didn't slow down — it stopped entirely. Everything was still. You were the only thing in motion, and somehow, that motion became the rhythm my heart has kept ever since.
            </p>
          </div>
        </div>

        <!-- Memory 2 -->
        <div class="flex md:justify-start mb-10 timeline-item-right" style="margin-left:0;md:margin-left:calc(50% + 20px)">
          <div class="memory-card" style="max-width:340px;">
            <div class="flex items-center gap-3 mb-3">
              <span style="font-size:1.6rem;">💌</span>
              <div>
                <p class="font-display font-bold text-lg" style="color:var(--deep-rose);">Our First Conversation</p>
                <p class="text-xs tracking-wider uppercase" style="color:var(--rose-gold);letter-spacing:2px;">The Spark</p>
              </div>
            </div>
            <p class="font-body" style="line-height:1.8;color:var(--burgundy);">
              Those first words we exchanged — I replayed them a thousand times afterward. I was nervous in a way I had never been before. You made me feel both terrified and completely at home, all at once. Only you have that power.
            </p>
          </div>
        </div>

        <!-- Memory 3 -->
        <div class="flex md:justify-end mb-10" style="md:margin-right:calc(50% + 20px)">
          <div class="memory-card" style="max-width:340px;">
            <div class="flex items-center gap-3 mb-3">
              <span style="font-size:1.6rem;">🌙</span>
              <div>
                <p class="font-display font-bold text-lg" style="color:var(--deep-rose);">Nights That Felt Like Forever</p>
                <p class="text-xs tracking-wider uppercase" style="color:var(--rose-gold);letter-spacing:2px;">The Magic</p>
              </div>
            </div>
            <p class="font-body" style="line-height:1.8;color:var(--burgundy);">
              Do you remember those long, unhurried evenings we shared — talking about everything and nothing? Those were the nights I realised I didn't just want you in my days. I wanted you in every quiet, ordinary,
