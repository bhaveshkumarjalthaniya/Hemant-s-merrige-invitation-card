```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <title>Shubh Vivah — Hemant &amp; Kiran | March 2027</title>

  <!-- Google Fonts for Royal English & Traditional Hindi Typography -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cinzel+Decorative:wght@700;900&family=Playfair+Display:ital,wght@0,500;0,700;1,500&family=Poppins:wght@300;400;500;600&family=Rozha+One&family=Tiro+Devanagari+Hindi:ital@0;1&display=swap" rel="stylesheet" />

  <style>
    /* ==========================================================================
       1. CSS VARIABLES & ROYAL RAJASTHANI PALETTE
       ========================================================================== */
    :root {
      --maroon-dark: #380303;
      --maroon-deep: #540808;
      --royal-red: #8B0000;
      --crimson-accent: #B21818;
      --gold-primary: #D4AF37;
      --gold-bright: #FFD700;
      --gold-soft: #F3E5AB;
      --cream-bg: #FDFBF7;
      --cream-card: #FFFDF8;
      --parchment: #F9F2E2;
      --marigold: #FF8C00;
      --text-dark: #2C0B0E;
      --text-muted: #5C2C30;

      --font-en-display: 'Cinzel Decorative', serif;
      --font-en-serif: 'Playfair Display', serif;
      --font-en-sans: 'Poppins', sans-serif;
      --font-hi-display: 'Rozha One', serif;
      --font-hi-body: 'Tiro Devanagari Hindi', serif;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      -webkit-tap-highlight-color: transparent;
    }

    html, body {
      width: 100%;
      min-height: 100vh;
      min-height: 100dvh;
      overflow-x: hidden;
      background: radial-gradient(circle at top, #6b0b0b 0%, #3d0404 55%, #220101 100%);
      color: var(--text-dark);
      font-family: var(--font-en-sans);
    }

    /* Language-specific font switching */
    body.lang-hi {
      font-family: var(--font-hi-body);
    }

    /* ==========================================================================
       2. AMBIENT GOLDEN PARTICLES & ROYAL MANDALA BACKDROP
       ========================================================================== */
    #shimmer-canvas {
      position: fixed;
      inset: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 1;
    }

    .bg-mandala {
      position: fixed;
      width: 460px;
      height: 460px;
      opacity: 0.12;
      pointer-events: none;
      z-index: 0;
      animation: slowSpin 90s linear infinite;
    }
    .bg-mandala.top-left {
      top: -180px;
      left: -180px;
    }
    .bg-mandala.bottom-right {
      bottom: -180px;
      right: -180px;
      animation-direction: reverse;
    }

    @keyframes slowSpin {
      from { transform: rotate(0deg); }
      to { transform: rotate(360deg); }
    }

    /* ==========================================================================
       3. TOP BAR CONTROLS (AUDIO & EDIT GUEST)
       ========================================================================== */
    .top-utility-bar {
      position: fixed;
      top: 12px;
      left: 0;
      right: 0;
      z-index: 50;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0 16px;
      pointer-events: none;
    }

    .pill-btn {
      pointer-events: auto;
      display: inline-flex;
      align-items: center;
      gap: 7px;
      padding: 8px 14px;
      border-radius: 999px;
      border: 1.5px solid var(--gold-primary);
      background: rgba(56, 3, 3, 0.88);
      backdrop-filter: blur(8px);
      color: var(--gold-soft);
      font-size: 0.8rem;
      font-weight: 500;
      cursor: pointer;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.45);
      transition: all 0.25s ease;
    }

    .pill-btn:hover, .pill-btn:active {
      background: var(--gold-primary);
      color: var(--maroon-dark);
      transform: translateY(-1px);
    }

    .pill-btn svg {
      width: 16px;
      height: 16px;
      flex-shrink: 0;
    }

    .hidden {
      display: none !important;
    }

    /* ==========================================================================
       4. SCREEN 1: ROYAL WELCOME GATE (GUEST FORM)
       ========================================================================== */
    .welcome-screen {
      position: relative;
      z-index: 10;
      min-height: 100vh;
      min-height: 100dvh;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 64px 16px 28px;
      transition: opacity 0.6s ease, transform 0.6s ease;
    }

    .welcome-screen.fade-out {
      opacity: 0;
      transform: scale(0.95);
      pointer-events: none;
    }

    .jharokha-gate {
      position: relative;
      width: 100%;
      max-width: 460px;
      background: linear-gradient(180deg, #FFFDF8 0%, #FBF3E4 100%);
      border: 3px solid var(--gold-primary);
      border-radius: 220px 220px 24px 24px;
      padding: 42px 26px 32px;
      box-shadow:
        0 25px 60px rgba(0, 0, 0, 0.65),
        inset 0 0 0 6px var(--maroon-deep),
        inset 0 0 0 8px var(--gold-primary);
      text-align: center;
      overflow: hidden;
    }

    /* Decorative Toran at top of Gate */
    .gate-toran {
      width: 100%;
      max-width: 340px;
      margin: -10px auto 6px;
      display: block;
    }

    .gate-shloka {
      font-family: var(--font-hi-body);
      color: var(--royal-red);
      font-size: 0.95rem;
      font-weight: 600;
      letter-spacing: 0.5px;
      margin-bottom: 4px;
    }

    .gate-title {
      font-family: var(--font-en-display);
      font-size: 1.65rem;
      color: var(--maroon-deep);
      line-height: 1.2;
      margin-bottom: 4px;
      text-shadow: 0 1px 0 rgba(212, 175, 55, 0.4);
    }

    .gate-couple {
      font-family: var(--font-en-serif);
      font-size: 1.35rem;
      font-weight: 700;
      color: var(--crimson-accent);
      margin-bottom: 2px;
    }

    .gate-sub {
      font-size: 0.82rem;
      color: var(--text-muted);
      margin-bottom: 20px;
      letter-spacing: 1px;
      text-transform: uppercase;
    }

    .form-group {
      text-align: left;
      margin-bottom: 16px;
    }

    .form-label {
      display: block;
      font-size: 0.85rem;
      font-weight: 600;
      color: var(--maroon-deep);
      margin-bottom: 6px;
    }

    .royal-input {
      width: 100%;
      padding: 12px 15px;
      border-radius: 12px;
      border: 1.8px solid var(--gold-primary);
      background: #FFFFFF;
      font-size: 1rem;
      color: var(--text-dark);
      font-family: inherit;
      outline: none;
      transition: box-shadow 0.25s ease, border-color 0.25s ease;
    }

    .royal-input:focus {
      border-color: var(--royal-red);
      box-shadow: 0 0 0 3px rgba(212, 175, 55, 0.35);
    }

    .error-msg {
      color: #C62828;
      font-size: 0.78rem;
      margin-top: 5px;
      display: none;
      font-weight: 500;
    }

    .error-msg.visible {
      display: block;
    }

    /* Option Pill Selectors (Gender & Language) */
    .option-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
    }

    .option-card {
      position: relative;
      cursor: pointer;
    }

    .option-card input {
      position: absolute;
      opacity: 0;
      pointer-events: none;
    }

    .option-tile {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
      padding: 11px 10px;
      border-radius: 12px;
      border: 1.8px solid rgba(212, 175, 55, 0.7);
      background: #FFFFFF;
      color: var(--maroon-deep);
      font-weight: 600;
      font-size: 0.92rem;
      transition: all 0.22s ease;
      user-select: none;
    }

    .option-card input:checked + .option-tile {
      background: linear-gradient(135deg, var(--royal-red), var(--maroon-deep));
      color: var(--gold-bright);
      border-color: var(--gold-bright);
      box-shadow: 0 6px 16px rgba(139, 0, 0, 0.3);
      transform: translateY(-1px);
    }

    .open-invite-btn {
      width: 100%;
      margin-top: 10px;
      padding: 14px 20px;
      border: 2px solid var(--gold-bright);
      border-radius: 999px;
      background: linear-gradient(135deg, #9b0a0a 0%, #5c0404 100%);
      color: var(--gold-bright);
      font-family: var(--font-en-serif);
      font-size: 1.08rem;
      font-weight: 700;
      letter-spacing: 0.6px;
      cursor: pointer;
      box-shadow: 0 10px 25px rgba(92, 4, 4, 0.45);
      transition: all 0.3s ease;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }

    .open-invite-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 14px 30px rgba(212, 175, 55, 0.35);
      background: linear-gradient(135deg, #b30e0e 0%, #6d0606 100%);
    }

    /* ==========================================================================
       5. SCREEN 2: 3D BOOK INVITATION STAGE
       ========================================================================== */
    .book-stage {
      position: relative;
      z-index: 10;
      min-height: 100vh;
      min-height: 100dvh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 60px 14px 24px;
      perspective: 2200px;
    }

    /* 360 Rotation Wrapper */
    .book-rotator {
      width: 100%;
      max-width: 520px;
      transform-style: preserve-3d;
      transition: transform 1.4s cubic-bezier(0.34, 1.36, 0.64, 1);
    }

    .book-rotator.spin-360 {
      transform: rotateY(360deg);
    }

    /* Invitation Book Container */
    .invitation-book {
      position: relative;
      width: 100%;
      height: 640px;
      max-height: 75dvh;
      transform-style: preserve-3d;
      border-radius: 20px;
      box-shadow:
        0 28px 65px rgba(0, 0, 0, 0.72),
        0 0 0 3px var(--gold-primary);
      background: var(--cream-card);
    }

    /* Spine accent on left edge */
    .invitation-book::before {
      content: "";
      position: absolute;
      top: 0;
      bottom: 0;
      left: 0;
      width: 14px;
      background: linear-gradient(90deg, rgba(56, 3, 3, 0.32), rgba(212, 175, 55, 0.18), transparent);
      border-radius: 20px 0 0 20px;
      z-index: 30;
      pointer-events: none;
    }

    /* Individual Book Pages */
    .book-page {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      border-radius: 20px;
      background: radial-gradient(circle at center, #FFFDF9 0%, #FAF0DC 100%);
      transform-origin: left center;
      transform-style: preserve-3d;
      transition: transform 0.95s cubic-bezier(0.645, 0.045, 0.355, 1), opacity 0.4s ease;
      box-shadow: inset 0 0 0 6px var(--maroon-deep), inset 0 0 0 8px var(--gold-primary);
      overflow: hidden;
      backface-visibility: hidden;
    }

    /* Flipped state turns page to the left like a real book */
    .book-page.flipped {
      transform: rotateY(-172deg);
      opacity: 0;
      pointer-events: none;
    }

    /* Z-index stacking for 4 pages */
    #page-1 { z-index: 4; }
    #page-2 { z-index: 3; }
    #page-3 { z-index: 2; }
    #page-4 { z-index: 1; }

    /* Inner scrollable area inside ornate frame */
    .page-inner {
      position: relative;
      height: 100%;
      padding: 22px 20px 26px;
      overflow-y: auto;
      scrollbar-width: thin;
      scrollbar-color: var(--gold-primary) transparent;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
    }

    .page-inner::-webkit-scrollbar {
      width: 5px;
    }
    .page-inner::-webkit-scrollbar-thumb {
      background: var(--gold-primary);
      border-radius: 10px;
    }

    /* Corner Ornaments inside each page */
    .corner-ornament {
      position: absolute;
      width: 44px;
      height: 44px;
      pointer-events: none;
      opacity: 0.85;
    }
    .corner-tl { top: 10px; left: 10px; }
    .corner-tr { top: 10px; right: 10px; transform: scaleX(-1); }
    .corner-bl { bottom: 10px; left: 10px; transform: scaleY(-1); }
    .corner-br { bottom: 10px; right: 10px; transform: scale(-1, -1); }

    /* ==========================================================================
       6. PAGE-SPECIFIC ROYAL STYLING
       ========================================================================== */
    .sanskrit-mantra {
      font-family: var(--font-hi-body);
      font-size: 0.9rem;
      color: var(--royal-red);
      font-weight: 600;
      margin-top: 2px;
    }

    .ganesh-emblem {
      width: 78px;
      height: 78px;
      margin: 6px auto 4px;
      filter: drop-shadow(0 4px 8px rgba(139, 0, 0, 0.22));
    }

    .page-heading {
      font-family: var(--font-en-display);
      font-size: 1.45rem;
      color: var(--maroon-deep);
      letter-spacing: 0.6px;
      margin: 4px 0;
    }

    body.lang-hi .page-heading {
      font-family: var(--font-hi-display);
      font-size: 1.7rem;
      font-weight: 400;
    }

    .gold-divider {
      width: 190px;
      height: 18px;
      margin: 4px auto 10px;
      flex-shrink: 0;
    }

    /* Personalized Guest Banner */
    .guest-honor-box {
      width: 100%;
      background: linear-gradient(135deg, rgba(139, 0, 0, 0.08), rgba(212, 175, 55, 0.18));
      border: 1.5px solid var(--gold-primary);
      border-radius: 14px;
      padding: 10px 14px;
      margin: 6px 0 12px;
    }

    .guest-honor-label {
      font-size: 0.75rem;
      text-transform: uppercase;
      letter-spacing: 1.2px;
      color: var(--text-muted);
      font-weight: 600;
    }

    body.lang-hi .guest-honor-label {
      text-transform: none;
      letter-spacing: 0.3px;
      font-size: 0.85rem;
    }

    .guest-honor-name {
      font-family: var(--font-en-serif);
      font-size: 1.3rem;
      font-weight: 700;
      color: var(--royal-red);
      margin-top: 2px;
    }

    body.lang-hi .guest-honor-name {
      font-family: var(--font-hi-display);
      font-size: 1.45rem;
      font-weight: 400;
    }

    /* Couple Monogram & Names */
    .couple-showcase {
      margin: 6px 0 10px;
    }

    .couple-names {
      font-family: var(--font-en-display);
      font-size: 1.95rem;
      color: var(--royal-red);
      line-height: 1.2;
      text-shadow: 0 2px 0 rgba(212, 175, 55, 0.35);
    }

    body.lang-hi .couple-names {
      font-family: var(--font-hi-display);
      font-size: 2.2rem;
    }

    .weds-badge {
      display: inline-block;
      margin: 4px 0;
      padding: 2px 14px;
      border-radius: 999px;
      background: var(--maroon-deep);
      color: var(--gold-bright);
      font-size: 0.78rem;
      letter-spacing: 1.5px;
      text-transform: uppercase;
    }

    body.lang-hi .weds-badge {
      font-family: var(--font-hi-body);
      text-transform: none;
      letter-spacing: 0.5px;
      font-size: 0.9rem;
    }

    .invitation-body-text {
      font-size: 0.92rem;
      line-height: 1.65;
      color: var(--text-dark);
      max-width: 410px;
      margin: 4px auto 12px;
    }

    body.lang-hi .invitation-body-text {
      font-size: 1rem;
      line-height: 1.72;
    }

    .date-pill-highlight {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 8px 18px;
      border-radius: 999px;
      background: linear-gradient(135deg, var(--maroon-deep), var(--royal-red));
      color: var(--gold-bright);
      border: 1.5px solid var(--gold-bright);
      font-weight: 600;
      font-size: 0.92rem;
      margin-top: auto;
      box-shadow: 0 6px 16px rgba(84, 8, 8, 0.25);
    }

    /* Page 2: 9 Ceremonies Timeline List */
    .ceremonies-list {
      width: 100%;
      display: flex;
      flex-direction: column;
      gap: 8px;
      text-align: left;
      margin-top: 4px;
    }

    .ceremony-item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      padding: 9px 12px;
      border-radius: 12px;
      background: #FFFFFF;
      border: 1px solid rgba(212, 175, 55, 0.65);
      border-left: 4px solid var(--royal-red);
      box-shadow: 0 3px 10px rgba(84, 8, 8, 0.06);
    }

    .ceremony-left {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .ceremony-num {
      width: 24px;
      height: 24px;
      border-radius: 50%;
      background: var(--maroon-deep);
      color: var(--gold-bright);
      font-size: 0.74rem;
      font-weight: 700;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
    }

    .ceremony-title {
      font-weight: 700;
      font-size: 0.92rem;
      color: var(--maroon-deep);
    }

    body.lang-hi .ceremony-title {
      font-size: 1rem;
    }

    .ceremony-time {
      text-align: right;
      font-size: 0.76rem;
      font-weight: 600;
      color: var(--royal-red);
      background: rgba(212, 175, 55, 0.16);
      padding: 4px 8px;
      border-radius: 8px;
      white-space: nowrap;
    }

    /* Page 3: Venue Card & Map Button */
    .venue-palace-card {
      width: 100%;
      background: #FFFFFF;
      border: 1.8px solid var(--gold-primary);
      border-radius: 16px;
      padding: 16px 14px;
      margin: 6px 0 12px;
      box-shadow: 0 8px 20px rgba(84, 8, 8, 0.08);
    }

    .venue-pin-icon {
      width: 44px;
      height: 44px;
      margin: 0 auto 6px;
      color: var(--royal-red);
    }

    .venue-title {
      font-family: var(--font-en-serif);
      font-size: 1.15rem;
      font-weight: 700;
      color: var(--maroon-deep);
      margin-bottom: 6px;
    }

    body.lang-hi .venue-title {
      font-family: var(--font-hi-display);
      font-size: 1.3rem;
      font-weight: 400;
    }

    .venue-address {
      font-size: 0.9rem;
      line-height: 1.55;
      color: var(--text-dark);
      font-weight: 500;
    }

    .map-btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      margin-top: 12px;
      padding: 10px 18px;
      border-radius: 999px;
      background: linear-gradient(135deg, var(--royal-red), var(--maroon-deep));
      color: var(--gold-bright);
      text-decoration: none;
      font-size: 0.86rem;
      font-weight: 600;
      border: 1.5px solid var(--gold-primary);
      box-shadow: 0 5px 14px rgba(139, 0, 0, 0.28);
      transition: transform 0.2s ease;
    }

    .map-btn:hover {
      transform: translateY(-2px);
    }

    /* Page 4: Final Blessings */
    .blessing-frame {
      width: 100%;
      background: linear-gradient(180deg, rgba(255,255,255,0.9), rgba(253, 244, 224, 0.95));
      border: 1.5px dashed var(--gold-primary);
      border-radius: 16px;
      padding: 16px 14px;
      margin: 6px 0 12px;
    }

    .family-signature {
      margin-top: auto;
      padding-top: 10px;
      border-top: 1px solid rgba(212, 175, 55, 0.5);
      width: 100%;
    }

    .with-love-label {
      font-size: 0.82rem;
      color: var(--text-muted);
      font-style: italic;
    }

    .family-name-text {
      font-family: var(--font-en-serif);
      font-size: 1.15rem;
      font-weight: 700;
      color: var(--royal-red);
      margin-top: 2px;
    }

    body.lang-hi .family-name-text {
      font-family: var(--font-hi-display);
      font-size: 1.3rem;
      font-weight: 400;
    }

    /* ==========================================================================
       7. BOTTOM NAVIGATION & 360° ROTATE CONTROLS
       ========================================================================== */
    .book-controls {
      width: 100%;
      max-width: 520px;
      margin-top: 16px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 8px;
      z-index: 20;
    }

    .nav-btn {
      flex: 1;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
      padding: 11px 14px;
      border-radius: 14px;
      border: 1.5px solid var(--gold-primary);
      background: linear-gradient(180deg, #6b0808, #3d0303);
      color: var(--gold-bright);
      font-weight: 600;
      font-size: 0.86rem;
      cursor: pointer;
      box-shadow: 0 6px 18px rgba(0, 0, 0, 0.45);
      transition: all 0.2s ease;
    }

    .nav-btn:disabled {
      opacity: 0.42;
      cursor: not-allowed;
      transform: none;
    }

    .nav-btn:not(:disabled):hover {
      background: var(--gold-primary);
      color: var(--maroon-dark);
      transform: translateY(-2px);
    }

    .center-controls {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 6px;
    }

    .page-indicator {
      padding: 4px 14px;
      border-radius: 999px;
      background: rgba(253, 251, 247, 0.95);
      color: var(--maroon-deep);
      font-weight: 700;
      font-size: 0.84rem;
      border: 1.5px solid var(--gold-primary);
      box-shadow: 0 4px 12px rgba(0,0,0,0.3);
    }

    .rotate-360-btn {
      display: inline-flex;
      align-items: center;
      gap: 5px;
      padding: 6px 12px;
      border-radius: 999px;
      border: 1px solid var(--gold-bright);
      background: rgba(139, 0, 0, 0.9);
      color: var(--gold-soft);
      font-size: 0.76rem;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.25s ease;
    }

    .rotate-360-btn:hover {
      background: var(--gold-bright);
      color: var(--maroon-dark);
    }

    /* Responsive adjustments for smaller phones */
    @media (max-width: 400px) {
      .jharokha-gate {
        padding: 34px 18px 24px;
        border-radius: 170px 170px 20px 20px;
      }
      .gate-title { font-size: 1.4rem; }
      .couple-names { font-size: 1.65rem; }
      body.lang-hi .couple-names { font-size: 1.9rem; }
      .invitation-book { height: 600px; }
      .ceremony-item { flex-direction: column; align-items: flex-start; gap: 4px; }
      .ceremony-time { align-self: flex-end; }
    }
  </style>
</head>
<body class="lang-en">

  <!-- Ambient Golden Shimmer Particle Canvas -->
  <canvas id="shimmer-canvas"></canvas>

  <!-- Rotating Royal Mandala Watermarks -->
  <svg class="bg-mandala top-left" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
    <circle cx="100" cy="100" r="92" stroke="#FFD700" stroke-width="1.5" stroke-dasharray="4 4"/>
    <circle cx="100" cy="100" r="74" stroke="#D4AF37" stroke-width="2"/>
    <circle cx="100" cy="100" r="52" stroke="#FFD700" stroke-width="1.5"/>
    <circle cx="100" cy="100" r="28" stroke="#D4AF37" stroke-width="2"/>
    <g stroke="#FFD700" stroke-width="1.2">
      <path d="M100 8 L112 45 L100 35 L88 45 Z"/>
      <path d="M100 192 L112 155 L100 165 L88 155 Z"/>
      <path d="M8 100 L45 88 L35 100 L45 112 Z"/>
      <path d="M192 100 L155 88 L165 100 L155 112 Z"/>
      <path d="M35 35 L68 52 L55 55 L52 68 Z"/>
      <path d="M165 165 L132 148 L145 145 L148 132 Z"/>
      <path d="M165 35 L148 68 L145 55 L132 52 Z"/>
      <path d="M35 165 L52 132 L55 145 L68 148 Z"/>
    </g>
  </svg>

  <svg class="bg-mandala bottom-right" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
    <circle cx="100" cy="100" r="92" stroke="#FFD700" stroke-width="1.5" stroke-dasharray="4 4"/>
    <circle cx="100" cy="100" r="74" stroke="#D4AF37" stroke-width="2"/>
    <circle cx="100" cy="100" r="52" stroke="#FFD700" stroke-width="1.5"/>
    <g stroke="#FFD700" stroke-width="1.2">
      <polygon points="100,15 120,80 185,100 120,120 100,185 80,120 15,100 80,80"/>
      <polygon points="40,40 100,68 160,40 132,100 160,160 100,132 40,160 68,100"/>
    </g>
  </svg>

  <!-- Top Utility Bar: Edit Guest Info & Instrumental Music Toggle -->
  <header class="top-utility-bar">
    <button id="edit-guest-btn" class="pill-btn hidden" type="button" aria-label="Change Guest Details">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"/>
        <path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"/>
      </svg>
      <span id="edit-btn-text">Change Guest</span>
    </button>

    <button id="music-toggle-btn" class="pill-btn" type="button" aria-label="Toggle Wedding Music" style="margin-left: auto;">
      <svg id="music-icon-off" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M11 5L6 9H2v6h4l5 4V5z"/>
        <line x1="23" y1="9" x2="17" y2="15"/>
        <line x1="17" y1="9" x2="23" y2="15"/>
      </svg>
      <svg id="music-icon-on" class="hidden" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M11 5L6 9H2v6h4l5 4V5z"/>
        <path d="M15.54 8.46a5 5 0 0 1 0 7.07"/>
        <path d="M19.07 4.93a10 10 0 0 1 0 14.14"/>
      </svg>
      <span id="music-btn-text">Play Shehnai</span>
    </button>
  </header>

  <!-- ========================================================================
       SCREEN 1: GUEST WELCOME GATE (ONLY 3 REQUIRED FIELDS)
       ======================================================================== -->
  <main id="welcome-screen" class="welcome-screen">
    <section class="jharokha-gate" aria-label="Wedding Invitation Welcome">
      <!-- Decorative Marigold & Mango Leaf Toran -->
      <svg class="gate-toran" viewBox="0 0 360 58" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M10 8 Q90 36 180 12 Q270 36 350 8" stroke="#D4AF37" stroke-width="3" fill="none"/>
        <!-- Mango leaves & marigold flowers -->
        <g fill="#2E7D32">
          <path d="M45 18 Q40 36 45 44 Q50 36 45 18Z"/>
          <path d="M90 24 Q85 42 90 50 Q95 42 90 24Z"/>
          <path d="M135 19 Q130 37 135 45 Q140 37 135 19Z"/>
          <path d="M225 19 Q220 37 225 45 Q230 37 225 19Z"/>
          <path d="M270 24 Q265 42 270 50 Q275 42 270 24Z"/>
          <path d="M315 18 Q310 36 315 44 Q320 36 315 18Z"/>
        </g>
        <circle cx="68" cy="22" r="7" fill="#FF8C00"/>
        <circle cx="68" cy="22" r="3" fill="#FFD700"/>
        <circle cx="112" cy="23" r="7" fill="#FF5722"/>
        <circle cx="112" cy="23" r="3" fill="#FFD700"/>
        <circle cx="180" cy="18" r="10" fill="#8B0000" stroke="#FFD700" stroke-width="2"/>
        <circle cx="180" cy="18" r="4" fill="#FFD700"/>
        <circle cx="248" cy="23" r="7" fill="#FF5722"/>
        <circle cx="248" cy="23" r="3" fill="#FFD700"/>
        <circle cx="292" cy="22" r="7" fill="#FF8C00"/>
        <circle cx="292" cy="22" r="3" fill="#FFD700"/>
      </svg>

      <p class="gate-shloka">॥ श्री गणेशाय नमः ॥</p>
      <h1 class="gate-title">Shubh Vivah</h1>
      <p class="gate-couple">Hemant &amp; Kiran</p>
      <p class="gate-sub">March 2027 • Jaipur, Rajasthan</p>

      <form id="guest-form" novalidate>
        <!-- Field 1: Guest Name -->
        <div class="form-group">
          <label for="guest-name" class="form-label">1. Guest Name / अतिथि का नाम</label>
          <input
            type="text"
            id="guest-name"
            class="royal-input"
            placeholder="Enter your name / अपना नाम लिखें"
            maxlength="40"
            autocomplete="name"
            required
          />
          <p id="name-error" class="error-msg">Please enter your name / कृपया अपना नाम दर्ज करें।</p>
        </div>

        <!-- Field 2: Gender -->
        <div class="form-group">
          <span class="form-label">2. Gender / लिंग</span>
          <div class="option-grid">
            <label class="option-card">
              <input type="radio" name="gender" value="male" checked />
              <span class="option-tile">♂ Male / पुरुष</span>
            </label>
            <label class="option-card">
              <input type="radio" name="gender" value="female" />
              <span class="option-tile">♀ Female / महिला</span>
            </label>
          </div>
        </div>

        <!-- Field 3: Language -->
        <div class="form-group">
          <span class="form-label">3. Invitation Language / भाषा</span>
          <div class="option-grid">
            <label class="option-card">
              <input type="radio" name="language" value="hi" checked />
              <span class="option-tile">हिन्दी (Hindi)</span>
            </label>
            <label class="option-card">
              <input type="radio" name="language" value="en" />
              <span class="option-tile">English</span>
            </label>
          </div>
        </div>

        <button type="submit" class="open-invite-btn">
          <span>✨ Open Invitation / निमंत्रण खोलें ✨</span>
        </button>
      </form>
    </section>
  </main>

  <!-- ========================================================================
       SCREEN 2: 4-PAGE BOOK-STYLE WEDDING INVITATION
       ======================================================================== -->
  <section id="book-stage" class="book-stage hidden" aria-label="Digital Wedding Invitation Book">
    <div id="book-rotator" class="book-rotator">
      <div id="invitation-book" class="invitation-book">

        <!-- ==================== PAGE 1: WEDDING WELCOME ==================== -->
        <article id="page-1" class="book-page">
          <div class="page-inner">
            <!-- Ornate Corner SVGs -->
            <svg class="corner-ornament corner-tl" viewBox="0 0 60 60" fill="none">
              <path d="M4 56V16C4 9.37 9.37 4 16 4H56" stroke="#D4AF37" stroke-width="2.5"/>
              <path d="M12 46V20C12 15.58 15.58 12 20 12H46" stroke="#8B0000" stroke-width="1.5"/>
              <circle cx="14" cy="14" r="4" fill="#D4AF37"/>
            </svg>
            <svg class="corner-ornament corner-tr" viewBox="0 0 60 60" fill="none">
              <path d="M4 56V16C4 9.37 9.37 4 16 4H56" stroke="#D4AF37" stroke-width="2.5"/>
              <path d="M12 46V20C12 15.58 15.58 12 20 12H46" stroke="#8B0000" stroke-width="1.5"/>
              <circle cx="14" cy="14" r="4" fill="#D4AF37"/>
            </svg>
            <svg class="corner-ornament corner-bl" viewBox="0 0 60 60" fill="none">
              <path d="M4 56V16C4 9.37 9.37 4 16 4H56" stroke="#D4AF37" stroke-width="2.5"/>
              <path d="M12 46V20C12 15.58 15.58 12 20 12H46" stroke="#8B0000" stroke-width="1.5"/>
              <circle cx="14" cy="14" r="4" fill="#D4AF37"/>
            </svg>
            <svg class="corner-ornament corner-br" viewBox="0 0 60 60" fill="none">
              <path d="M4 56V16C4 9.37 9.37 4 16 4H56" stroke="#D4AF37" stroke-width="2.5"/>
              <path d="M12 46V20C12 15.58 15.58 12 20 12H46" stroke="#8B0000" stroke-width="1.5"/>
              <circle cx="14" cy="14" r="4" fill="#D4AF37"/>
            </svg>

            <p class="sanskrit-mantra">॥ वक्रतुण्ड महाकाय सूर्यकोटि समप्रभ ॥</p>

            <!-- Traditional Artistic Lord Ganesh Emblem -->
            <svg class="ganesh-emblem" viewBox="0 0 120 120" fill="none" xmlns="http://www.w3.org/2000/svg">
              <circle cx="60" cy="60" r="54" fill="#FFF8E7" stroke="#D4AF37" stroke-width="3"/>
              <circle cx="60" cy="60" r="47" stroke="#8B0000" stroke-width="1.2" stroke-dasharray="3 3"/>
              <!-- Mukut (Crown) -->
              <path d="M45 36 L60 16 L75 36 Z" fill="#D4AF37" stroke="#8B0000" stroke-width="1.5"/>
              <circle cx="60" cy="27" r="3" fill="#8B0000"/>
              <!-- Ears -->
              <path d="M42 42 C25 36, 24 62, 42 60" fill="#F6D365" stroke="#8B0000" stroke-width="1.8"/>
              <path d="M78 42 C95 36, 96 62, 78 60" fill="#F6D365" stroke="#8B0000" stroke-width="1.8"/>
              <!-- Head & Trunk -->
              <path d="M42 40 C42 30, 78 30, 78 40 C80 54, 72 64, 64 66 C63 76, 68 84, 76 82 C80 81, 80 88, 72 90 C58 92, 54 78, 55 66 C46 64, 40 54, 42 40 Z" fill="#FF9933" stroke="#8B0000" stroke-width="2"/>
              <!-- Tilak & Eyes -->
              <path d="M60 36 V45" stroke="#8B0000" stroke-width="2.2" stroke-linecap="round"/>
              <circle cx="51" cy="48" r="2.2" fill="#2C0B0E"/>
              <circle cx="69" cy="48" r="2.2" fill="#2C0B0E"/>
              <!-- Lotus Base -->
              <path d="M36 96 Q60 86 84 96 Q60 106 36 96 Z" fill="#8B0000"/>
            </svg>

            <h2 id="p1-heading" class="page-heading">Royal Wedding Invitation</h2>

            <!-- Personalized Guest Greeting Box -->
            <div class="guest-honor-box">
              <div id="p1-guest-label" class="guest-honor-label">Cordially Inviting</div>
              <div id="p1-guest-greeting" class="guest-honor-name">Mr. Guest</div>
            </div>

            <!-- Couple Names -->
            <div class="couple-showcase">
              <div id="p1-groom" class="couple-names">Hemant</div>
              <div id="p1-weds" class="weds-badge">Weds</div>
              <div id="p1-bride" class="couple-names">Kiran</div>
            </div>

            <svg class="gold-divider" viewBox="0 0 220 20" fill="none">
              <line x1="10" y1="10" x2="90" y2="10" stroke="#D4AF37" stroke-width="1.5"/>
              <polygon points="110,3 118,10 110,17 102,10" fill="#8B0000" stroke="#D4AF37" stroke-width="1.5"/>
              <line x1="130" y1="10" x2="210" y2="10" stroke="#D4AF37" stroke-width="1.5"/>
            </svg>

            <p id="p1-message" class="invitation-body-text">
              With the heavenly blessings of Lord Ganesha and our beloved elders, we joyfully invite you and your family to grace the auspicious wedding ceremony of Hemant &amp; Kiran.
            </p>

            <div id="p1-date-pill" class="date-pill-highlight">
              <span>🪷 March 10 – 13, 2027 • Jaipur</span>
            </div>
          </div>
        </article>

        <!-- ==================== PAGE 2: WEDDING FUNCTIONS ==================== -->
        <article id="page-2" class="book-page">
          <div class="page-inner">
            <h2 id="p2-heading" class="page-heading">Wedding Ceremonies</h2>
            <p id="p2-sub" class="sanskrit-mantra">March 2027 • Auspicious Celebrations</p>

            <svg class="gold-divider" viewBox="0 0 220 20" fill="none">
              <line x1="10" y1="10" x2="90" y2="10" stroke="#D4AF37" stroke-width="1.5"/>
              <polygon points="110,3 118,10 110,17 102,10" fill="#8B0000" stroke="#D4AF37" stroke-width="1.5"/>
              <line x1="130" y1="10" x2="210" y2="10" stroke="#D4AF37" stroke-width="1.5"/>
            </svg>

            <div id="ceremonies-container" class="ceremonies-list">
              <!-- Populated dynamically in Hindi or English via script.js -->
            </div>
          </div>
        </article>

        <!-- ==================== PAGE 3: VENUE & INVITATION ==================== -->
        <article id="page-3" class="book-page">
          <div class="page-inner">
            <h2 id="p3-heading" class="page-heading">Venue &amp; Invitation</h2>
            <p id="p3-sub" class="sanskrit-mantra">Pink City • Jaipur, Rajasthan</p>

            <svg class="gold-divider" viewBox="0 0 220 20" fill="none">
              <line x1="10" y1="10" x2="90" y2="10" stroke="#D4AF37" stroke-width="1.5"/>
              <polygon points="110,3 118,10 110,17 102,10" fill="#8B0000" stroke="#D4AF37" stroke-width="1.5"/>
              <line x1="130" y1="10" x2="210" y2="10" stroke="#D4AF37" stroke-width="1.5"/>
            </svg>

            <div class="venue-palace-card">
              <!-- Rajasthani Temple / Mandap Dome SVG -->
              <svg class="venue-pin-icon" viewBox="0 0 64 64" fill="none">
                <path d="M32 6 L36 16 H28 L32 6 Z" fill="#D4AF37"/>
                <path d="M18 26 C18 16, 46 16, 46 26 H18 Z" fill="#8B0000" stroke="#D4AF37" stroke-width="2"/>
                <rect x="14" y="26" width="36" height="4" rx="2" fill="#D4AF37"/>
                <path d="M18 30 V52 M27 30 V52 M37 30 V52 M46 30 V52" stroke="#8B0000" stroke-width="3"/>
                <rect x="10" y="52" width="44" height="5" rx="2" fill="#540808"/>
              </svg>

              <h3 id="p3-venue-title" class="venue-title">Wedding Venue</h3>
              <p id="p3-address" class="venue-address">
                Regaron Ka Mohalla,<br />
                Near Ramdevji Temple,<br />
                Bindayaka, Jaipur, Rajasthan, India
              </p>

              <a
                id="p3-map-link"
                class="map-btn"
                href="https://www.google.com/maps/search/?api=1&query=Bindayaka+Jaipur+Rajasthan"
                target="_blank"
                rel="noopener noreferrer"
              >
                <span>📍 View Location on Google Maps</span>
              </a>
            </div>

            <p id="p3-message" class="invitation-body-text">
              Your presence will add immense joy and grace to our celebrations. We warmly request all our beloved relatives and friends to attend the wedding festivities in Bindayaka, Jaipur and shower your heartfelt blessings upon Hemant &amp; Kiran.
            </p>
          </div>
        </article>

        <!-- ==================== PAGE 4: FINAL BLESSINGS ==================== -->
        <article id="page-4" class="book-page">
          <div class="page-inner">
            <!-- Lotus & Kalash Blessing SVG -->
            <svg class="ganesh-emblem" viewBox="0 0 120 120" fill="none">
              <circle cx="60" cy="60" r="52" fill="#FFF8E7" stroke="#D4AF37" stroke-width="2.5"/>
              <!-- Sacred Kalash -->
              <path d="M44 48 H76 L72 56 C82 64, 80 86, 60 88 C40 86, 38 64, 48 56 L44 48 Z" fill="#D4AF37" stroke="#8B0000" stroke-width="2"/>
              <!-- Coconut & Mango Leaves -->
              <circle cx="60" cy="43" r="10" fill="#8D5524" stroke="#540808" stroke-width="1.5"/>
              <path d="M48 45 Q34 34 32 46 Q42 48 48 45 Z" fill="#2E7D32"/>
              <path d="M72 45 Q86 34 88 46 Q78 48 72 45 Z" fill="#2E7D32"/>
              <path d="M55 35 Q60 22 65 35 Z" fill="#2E7D32"/>
              <!-- Swastik / Sacred Dot -->
              <circle cx="60" cy="70" r="4" fill="#8B0000"/>
            </svg>

            <h2 id="p4-heading" class="page-heading">Heartfelt Blessings</h2>

            <svg class="gold-divider" viewBox="0 0 220 20" fill="none">
              <line x1="10" y1="10" x2="90" y2="10" stroke="#D4AF37" stroke-width="1.5"/>
              <polygon points="110,3 118,10 110,17 102,10" fill="#8B0000" stroke="#D4AF37" stroke-width="1.5"/>
              <line x1="130" y1="10" x2="210" y2="10" stroke="#D4AF37" stroke-width="1.5"/>
            </svg>

            <div class="blessing-frame">
              <p id="p4-blessing-text" class="invitation-body-text" style="margin-bottom: 10px;">
                May the sacred bond of Hemant &amp; Kiran be blessed with eternal love, harmony, prosperity, and lifelong happiness.
              </p>
              <p id="p4-preetibhoj-text" class="invitation-body-text" style="font-weight: 600; color: var(--royal-red); margin-bottom: 0;">
                We cordially await the pleasure of your company at the celebrations and Preetibhoj (Wedding Feast) on 13th March 2027.
              </p>
            </div>

            <div class="family-signature">
              <div id="p4-with-love" class="with-love-label">With Love &amp; Warm Regards,</div>
              <div id="p4-family-name" class="family-name-text">Hemant &amp; Kiran's Family</div>
            </div>
          </div>
        </article>

      </div>
    </div>

    <!-- Bottom Interactive Book Navigation Controls -->
    <nav class="book-controls" aria-label="Invitation Page Navigation">
      <button id="prev-btn" class="nav-btn" type="button">
        <span>◀</span>
        <span id="prev-label">Previous</span>
      </button>

      <div class="center-controls">
        <div id="page-indicator" class="page-indicator">1 / 4</div>
        <button id="rotate-360-btn" class="rotate-360-btn" type="button">
          <span>🔄</span>
          <span id="rotate-label">360° Rotate</span>
        </button>
      </div>

      <button id="next-btn" class="nav-btn" type="button">
        <span id="next-label">Next</span>
        <span>▶</span>
      </button>
    </nav>
  </section>

  <script>
    /* ==========================================================================
       1. BILINGUAL CONTENT DICTIONARY (HINDI & ENGLISH)
       ========================================================================== */
    const TRANSLATIONS = {
      en: {
        editBtn: "Change Guest",
        musicPlay: "Play Shehnai",
        musicPause: "Mute Music",
        prevBtn: "Previous",
        nextBtn: "Next",
        rotateBtn: "360° Rotate",
        p1Heading: "Royal Wedding Invitation",
        p1GuestLabel: "Cordially Inviting",
        groom: "Hemant",
        weds: "Weds",
        bride: "Kiran",
        p1Message:
          "With the heavenly blessings of Lord Ganesha and our beloved elders, we joyfully invite you and your family to grace the auspicious wedding ceremony of Hemant & Kiran.",
        p1DatePill: "🪷 March 10 – 13, 2027 • Jaipur",
        p2Heading: "Wedding Ceremonies",
        p2Sub: "March 2027 • Auspicious Celebrations",
        ceremonies: [
          { name: "Ganesh Sthapana", time: "10 Mar 2027 • 9:15 AM" },
          { name: "Mehndi Ceremony", time: "10 Mar 2027 • 4:00 PM" },
          { name: "Haldi Ceremony", time: "11 Mar 2027 • 10:30 AM" },
          { name: "Mahila Sangeet", time: "11 Mar 2027 • 7:30 PM" },
          { name: "Baraat", time: "12 Mar 2027 • 6:00 PM" },
          { name: "Varmala", time: "12 Mar 2027 • 8:30 PM" },
          { name: "Saat Phere", time: "12 Mar 2027 • 11:15 PM" },
          { name: "Preetibhoj", time: "13 Mar 2027 • 12:30 PM" },
          { name: "Vidai", time: "13 Mar 2027 • 4:30 PM" }
        ],
        p3Heading: "Venue & Invitation",
        p3Sub: "Pink City • Jaipur, Rajasthan",
        p3VenueTitle: "Wedding Venue",
        p3Address:
          "Regaron Ka Mohalla,<br />Near Ramdevji Temple,<br />Bindayaka, Jaipur, Rajasthan, India",
        p3MapLink: "📍 View Location on Google Maps",
        p3Message:
          "Your presence will add immense joy and grace to our celebrations. We warmly request all our beloved relatives and friends to attend the wedding festivities in Bindayaka, Jaipur and shower your heartfelt blessings upon Hemant & Kiran.",
        p4Heading: "Heartfelt Blessings",
        p4Blessing:
          "May the sacred bond of Hemant & Kiran be blessed with eternal love, harmony, prosperity, and lifelong happiness.",
        p4Preetibhoj:
          "We cordially await the pleasure of your company at the celebrations and Preetibhoj (Wedding Feast) on 13th March 2027.",
        p4WithLove: "With Love –",
        p4Family: "Hemant & Kiran's Family"
      },
      hi: {
        editBtn: "अतिथि बदलें",
        musicPlay: "शहनाई चलाएं",
        musicPause: "संगीत बंद करें",
        prevBtn: "पिछला",
        nextBtn: "अगला",
        rotateBtn: "360° घुमाएं",
        p1Heading: "शुभ विवाह निमंत्रण",
        p1GuestLabel: "सादर आमंत्रित",
        groom: "हेमंत",
        weds: "संग",
        bride: "किरण",
        p1Message:
          "विघ्नहर्ता श्री गणेश जी की असीम कृपा एवं हमारे पूज्य बुजुर्गों के शुभाशीर्वाद से, हम आपको और आपके समस्त परिवार को हेमंत एवं किरण के पावन परिणय उत्सव में सपरिवार सादर आमंत्रित करते हैं।",
        p1DatePill: "🪷 10 – 13 मार्च 2027 • जयपुर",
        p2Heading: "मांगलिक कार्यक्रम",
        p2Sub: "मार्च 2027 • शुभ विवाह समारोह",
        ceremonies: [
          { name: "गणेश स्थापना", time: "10 मार्च 2027 • प्रातः 9:15 बजे" },
          { name: "मेहंदी समारोह", time: "10 मार्च 2027 • सायं 4:00 बजे" },
          { name: "हल्दी समारोह", time: "11 मार्च 2027 • प्रातः 10:30 बजे" },
          { name: "महिला संगीत", time: "11 मार्च 2027 • रात्रि 7:30 बजे" },
          { name: "बारात", time: "12 मार्च 2027 • सायं 6:00 बजे" },
          { name: "वरमाला", time: "12 मार्च 2027 • रात्रि 8:30 बजे" },
          { name: "सात फेरे", time: "12 मार्च 2027 • रात्रि 11:15 बजे" },
          { name: "प्रीतिभोज", time: "13 मार्च 2027 • दोपहर 12:30 बजे" },
          { name: "विदाई", time: "13 मार्च 2027 • सायं 4:30 बजे" }
        ],
        p3Heading: "विवाह स्थल एवं निमंत्रण",
        p3Sub: "गुलाबी नगरी • जयपुर, राजस्थान",
        p3VenueTitle: "मांगलिक स्थल",
        p3Address:
          "रेगरों का मोहल्ला,<br />रामदेवजी मंदिर के पास,<br />बिन्दायका, जयपुर, राजस्थान, भारत",
        p3MapLink: "📍 गूगल मैप पर स्थान देखें",
        p3Message:
          "आपकी गरिमामयी उपस्थिति हमारे इस मंगल उत्सव की शोभा बढ़ाएगी। सभी स्नेही परिजनों एवं मित्रों से विनम्र निवेदन है कि बिन्दायका, जयपुर में पधारकर वर-वधू को अपना स्नेहिल आशीर्वाद प्रदान करें।",
        p4Heading: "स्नेहिल आशीर्वाद",
        p4Blessing:
          "ईश्वर से प्रार्थना है कि हेमंत और किरण का यह पावन बंधन सदैव प्रेम, सौहार्द, समृद्धि और खुशियों से महकता रहे।",
        p4Preetibhoj:
          "13 मार्च 2027 को आयोजित शुभ समारोह एवं प्रीतिभोज में आपके सपरिवार आगमन की हमें सादर प्रतीक्षा रहेगी।",
        p4WithLove: "सस्नेह –",
        p4Family: "हेमंत एवं किरण का समस्त परिवार"
      }
    };

    /* ==========================================================================
       2. APPLICATION STATE & DOM REFERENCES
       ========================================================================== */
    const state = {
      guestName: "",
      gender: "male",
      language: "hi",
      currentPage: 1,
      totalPages: 4,
      isSpinning: false
    };

    const welcomeScreen = document.getElementById("welcome-screen");
    const bookStage = document.getElementById("book-stage");
    const guestForm = document.getElementById("guest-form");
    const guestNameInput = document.getElementById("guest-name");
    const nameError = document.getElementById("name-error");
    const editGuestBtn = document.getElementById("edit-guest-btn");

    const prevBtn = document.getElementById("prev-btn");
    const nextBtn = document.getElementById("next-btn");
    const pageIndicator = document.getElementById("page-indicator");
    const rotate360Btn = document.getElementById("rotate-360-btn");
    const bookRotator = document.getElementById("book-rotator");
    const invitationBook = document.getElementById("invitation-book");

    /* ==========================================================================
       3. PERSONALIZED GREETING & LANGUAGE RENDERING
       ========================================================================== */
    function buildPersonalizedGreeting(name, gender, lang) {
      const cleanName = name.trim();
      if (lang === "hi") {
        return gender === "female"
          ? `श्रीमती ${cleanName} जी`
          : `श्रीमान ${cleanName} जी`;
      } else {
        return gender === "female"
          ? `Mrs. ${cleanName}`
          : `Mr. ${cleanName}`;
      }
    }

    function applyLanguageAndGuestData() {
      const t = TRANSLATIONS[state.language];

      // Toggle body language class for Devanagari vs Serif fonts
      document.body.classList.remove("lang-en", "lang-hi");
      document.body.classList.add(`lang-${state.language}`);

      // Top & Bottom Navigation Labels
      document.getElementById("edit-btn-text").textContent = t.editBtn;
      document.getElementById("prev-label").textContent = t.prevBtn;
      document.getElementById("next-label").textContent = t.nextBtn;
      document.getElementById("rotate-label").textContent = t.rotateBtn;
      updateMusicButtonText();

      // Page 1 Content
      document.getElementById("p1-heading").textContent = t.p1Heading;
      document.getElementById("p1-guest-label").textContent = t.p1GuestLabel;
      document.getElementById("p1-guest-greeting").textContent = buildPersonalizedGreeting(
        state.guestName,
        state.gender,
        state.language
      );
      document.getElementById("p1-groom").textContent = t.groom;
      document.getElementById("p1-weds").textContent = t.weds;
      document.getElementById("p1-bride").textContent = t.bride;
      document.getElementById("p1-message").textContent = t.p1Message;
      document.getElementById("p1-date-pill").innerHTML = `<span>${t.p1DatePill}</span>`;

      // Page 2 Content (All 9 Ceremonies)
      document.getElementById("p2-heading").textContent = t.p2Heading;
      document.getElementById("p2-sub").textContent = t.p2Sub;

      const ceremoniesContainer = document.getElementById("ceremonies-container");
      ceremoniesContainer.innerHTML = "";
      t.ceremonies.forEach((item, index) => {
        const row = document.createElement("div");
        row.className = "ceremony-item";
        row.innerHTML = `
          <div class="ceremony-left">
            <span class="ceremony-num">${index + 1}</span>
            <span class="ceremony-title">${item.name}</span>
          </div>
          <span class="ceremony-time">${item.time}</span>
        `;
        ceremoniesContainer.appendChild(row);
      });

      // Page 3 Content
      document.getElementById("p3-heading").textContent = t.p3Heading;
      document.getElementById("p3-sub").textContent = t.p3Sub;
      document.getElementById("p3-venue-title").textContent = t.p3VenueTitle;
      document.getElementById("p3-address").innerHTML = t.p3Address;
      document.getElementById("p3-map-link").innerHTML = `<span>${t.p3MapLink}</span>`;
      document.getElementById("p3-message").textContent = t.p3Message;

      // Page 4 Content
      document.getElementById("p4-heading").textContent = t.p4Heading;
      document.getElementById("p4-blessing-text").textContent = t.p4Blessing;
      document.getElementById("p4-preetibhoj-text").textContent = t.p4Preetibhoj;
      document.getElementById("p4-with-love").textContent = t.p4WithLove;
      document.getElementById("p4-family-name").textContent = t.p4Family;
    }

    /* ==========================================================================
       4. FORM VALIDATION & TRANSITION TO INVITATION BOOK
       ========================================================================== */
    guestForm.addEventListener("submit", (e) => {
      e.preventDefault();
      const rawName = guestNameInput.value.trim();

      if (!rawName) {
        nameError.classList.add("visible");
        guestNameInput.focus();
        return;
      }

      nameError.classList.remove("visible");
      state.guestName = rawName;
      state.gender = document.querySelector('input[name="gender"]:checked').value;
      state.language = document.querySelector('input[name="language"]:checked').value;

      applyLanguageAndGuestData();

      // Start gentle instrumental music automatically on user interaction if not already playing
      if (!audioState.isPlaying) {
        startInstrumentalMusic();
      }

      // Smoothly transition from welcome gate to 4-page book
      welcomeScreen.classList.add("fade-out");
      setTimeout(() => {
        welcomeScreen.classList.add("hidden");
        bookStage.classList.remove("hidden");
        editGuestBtn.classList.remove("hidden");
        goToPage(1);
      }, 450);
    });

    guestNameInput.addEventListener("input", () => {
      if (guestNameInput.value.trim()) {
        nameError.classList.remove("visible");
      }
    });

    editGuestBtn.addEventListener("click", () => {
      bookStage.classList.add("hidden");
      editGuestBtn.classList.add("hidden");
      welcomeScreen.classList.remove("hidden", "fade-out");
    });

    /* ==========================================================================
       5. 3D BOOK PAGE FLIPPING, 360° ROTATION & TOUCH SWIPE NAVIGATION
       ========================================================================== */
    function goToPage(pageNumber) {
      if (pageNumber < 1 || pageNumber > state.totalPages) return;
      state.currentPage = pageNumber;

      for (let i = 1; i <= state.totalPages; i++) {
        const pageEl = document.getElementById(`page-${i}`);
        if (i < state.currentPage) {
          pageEl.classList.add("flipped");
        } else {
          pageEl.classList.remove("flipped");
        }
      }

      // Update Indicator & Button States
      pageIndicator.textContent = `${state.currentPage} / ${state.totalPages}`;
      prevBtn.disabled = state.currentPage === 1;
      nextBtn.disabled = state.currentPage === state.totalPages;
    }

    prevBtn.addEventListener("click", () => goToPage(state.currentPage - 1));
    nextBtn.addEventListener("click", () => goToPage(state.currentPage + 1));

    // 360° 3D Book Rotation Button
    rotate360Btn.addEventListener("click", () => {
      if (state.isSpinning) return;
      state.isSpinning = true;
      bookRotator.classList.add("spin-360");

      setTimeout(() => {
        bookRotator.style.transition = "none";
        bookRotator.classList.remove("spin-360");
        // Force browser reflow so resetting transform doesn't animate backward
        void bookRotator.offsetWidth;
        bookRotator.style.transition = "";
        state.isSpinning = false;
      }, 1450);
    });

    // Touch Swipe Support for Mobile Page Flipping
    let touchStartX = 0;
    let touchStartY = 0;

    invitationBook.addEventListener(
      "touchstart",
      (e) => {
        touchStartX = e.changedTouches[0].screenX;
        touchStartY = e.changedTouches[0].screenY;
      },
      { passive: true }
    );

    invitationBook.addEventListener(
      "touchend",
      (e) => {
        const deltaX = e.changedTouches[0].screenX - touchStartX;
        const deltaY = e.changedTouches[0].screenY - touchStartY;

        // Trigger horizontal swipe only if stronger than vertical scroll
        if (Math.abs(deltaX) > 48 && Math.abs(deltaX) > Math.abs(deltaY)) {
          if (deltaX < 0) {
            goToPage(state.currentPage + 1);
          } else {
            goToPage(state.currentPage - 1);
          }
        }
      },
      { passive: true }
    );

    // Keyboard Arrow Navigation
    document.addEventListener("keydown", (e) => {
      if (bookStage.classList.contains("hidden")) return;
      if (e.key === "ArrowRight") goToPage(state.currentPage + 1);
      if (e.key === "ArrowLeft") goToPage(state.currentPage - 1);
    });

    /* ==========================================================================
       6. SYNTHESIZED TRADITIONAL INDIAN WEDDING MELODY (WEB AUDIO API)
       ========================================================================== */
    const audioState = {
      ctx: null,
      isPlaying: false,
      timerId: null,
      step: 0
    };

    // Raag Yaman / auspicious Indian wedding melody frequencies (Hz)
    const WEDDING_MELODY = [
      261.63, 293.66, 329.63, 369.99, 392.00, 440.00, 493.88, 523.25,
      493.88, 440.00, 392.00, 369.99, 329.63, 293.66, 329.63, 261.63
    ];

    const musicToggleBtn = document.getElementById("music-toggle-btn");
    const musicIconOn = document.getElementById("music-icon-on");
    const musicIconOff = document.getElementById("music-icon-off");
    const musicBtnText = document.getElementById("music-btn-text");

    function updateMusicButtonText() {
      const t = TRANSLATIONS[state.language];
      musicBtnText.textContent = audioState.isPlaying ? t.musicPause : t.musicPlay;
    }

    function playShehnaiNote(freq) {
      if (!audioState.ctx) return;
      const now = audioState.ctx.currentTime;

      const osc = audioState.ctx.createOscillator();
      const harmonic = audioState.ctx.createOscillator();
      const gain = audioState.ctx.createGain();

      osc.type = "triangle";
      harmonic.type = "sine";

      osc.frequency.setValueAtTime(freq, now);
      harmonic.frequency.setValueAtTime(freq * 2, now);

      gain.gain.setValueAtTime(0.0001, now);
      gain.gain.exponentialRampToValueAtTime(0.045, now + 0.12);
      gain.gain.exponentialRampToValueAtTime(0.0001, now + 0.62);

      osc.connect(gain);
      harmonic.connect(gain);
      gain.connect(audioState.ctx.destination);

      osc.start(now);
      harmonic.start(now);
      osc.stop(now + 0.65);
      harmonic.stop(now + 0.65);
    }

    function startInstrumentalMusic() {
      try {
        if (!audioState.ctx) {
          const AudioContextClass = window.AudioContext || window.webkitAudioContext;
          audioState.ctx = new AudioContextClass();
        }
        if (audioState.ctx.state === "suspended") {
          audioState.ctx.resume();
        }

        audioState.isPlaying = true;
        musicIconOff.classList.add("hidden");
        musicIconOn.classList.remove("hidden");
        updateMusicButtonText();

        playShehnaiNote(WEDDING_MELODY[audioState.step % WEDDING_MELODY.length]);
        audioState.step++;

        audioState.timerId = setInterval(() => {
          if (!audioState.isPlaying) return;
          playShehnaiNote(WEDDING_MELODY[audioState.step % WEDDING_MELODY.length]);
          audioState.step++;
        }, 650);
      } catch (err) {
        console.warn("Audio playback unavailable:", err);
      }
    }

    function stopInstrumentalMusic() {
      audioState.isPlaying = false;
      clearInterval(audioState.timerId);
      musicIconOn.classList.add("hidden");
      musicIconOff.classList.remove("hidden");
      updateMusicButtonText();
    }

    musicToggleBtn.addEventListener("click", () => {
      if (audioState.isPlaying) {
        stopInstrumentalMusic();
      } else {
        startInstrumentalMusic();
      }
    });

    /* ==========================================================================
       7. FLOATING GOLDEN SHIMMER PARTICLES CANVAS
       ========================================================================== */
    const canvas = document.getElementById("shimmer-canvas");
    const ctx = canvas.getContext("2d");
    let particles = [];

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }

    function createParticles() {
      const count = Math.min(55, Math.floor((window.innerWidth * window.innerHeight) / 18000));
      particles = Array.from({ length: count }, () => ({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        r: Math.random() * 2.4 + 0.8,
        speedY: Math.random() * 0.45 + 0.15,
        speedX: (Math.random() - 0.5) * 0.25,
        alpha: Math.random() * 0.7 + 0.2,
        pulse: Math.random() * Math.PI * 2
      }));
    }

    function animateParticles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      particles.forEach((p) => {
        p.y -= p.speedY;
        p.x += p.speedX;
        p.pulse += 0.03;

        if (p.y < -10) {
          p.y = canvas.height + 10;
          p.x = Math.random() * canvas.width;
        }

        const currentAlpha = p.alpha * (0.65 + 0.35 * Math.sin(p.pulse));
        ctx.beginPath();
        ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
        ctx.fillStyle = `rgba(255, 215, 0, ${currentAlpha.toFixed(2)})`;
        ctx.fill();
      });

      requestAnimationFrame(animateParticles);
    }

    window.addEventListener("resize", () => {
      resizeCanvas();
      createParticles();
    });

    window.addEventListener("load", () => {
      resizeCanvas();
      createParticles();
      animateParticles();
    });
  </script>
</body>
</html>
```
