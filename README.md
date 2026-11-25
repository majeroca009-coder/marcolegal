<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#f6f8f5">
  <title>SST Venezuela | Seguridad y Salud Laboral</title>
  <meta name="description" content="Soluciones de Seguridad y Salud en el Trabajo para empresas en Venezuela. Prevención, formación y acompañamiento SST.">
  <style>
    :root {
      --ink: #17251f;
      --muted: #64736b;
      --green: #147d52;
      --green-dark: #0c5538;
      --mint: #e8f4ec;
      --lime: #d3ef85;
      --paper: #f6f8f5;
      --white: #fff;
      --line: #e3e9e3;
      --shadow: 0 18px 50px rgba(24, 55, 39, .09);
      --radius: 22px;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      color: var(--ink);
      background: var(--paper);
      font: 16px/1.6 Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", sans-serif;
    }
    a { color: inherit; text-decoration: none; }
    button { font: inherit; }
    .wrap { width: min(1160px, calc(100% - 40px)); margin-inline: auto; }

    .topline {
      background: var(--green-dark);
      color: #eaf5ed;
      font-size: 13px;
      padding: 8px 0;
    }
    .topline .wrap {
      display: flex;
      justify-content: space-between;
      gap: 16px;
      align-items: center;
    }
    .topline span { opacity: .9; }

    header {
      position: sticky;
      top: 0;
      z-index: 10;
      background: rgba(246, 248, 245, .91);
      backdrop-filter: blur(14px);
      border-bottom: 1px solid rgba(227, 233, 227, .8);
    }
    .nav {
      min-height: 78px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 24px;
    }
    .brand {
      display: inline-flex;
      align-items: center;
      gap: 11px;
      font-weight: 850;
      letter-spacing: -.04em;
      line-height: 1.1;
      white-space: nowrap;
    }
    .brand-mark {
      width: 42px;
      height: 42px;
      display: grid;
      place-items: center;
      color: white;
      background: var(--green);
      border-radius: 14px;
      box-shadow: 0 7px 18px rgba(20, 125, 82, .22);
    }
    .brand-mark svg { width: 25px; height: 25px; }
    .brand small {
      display: block;
      margin-top: 4px;
      color: var(--muted);
      font-size: 10px;
      font-weight: 650;
      letter-spacing: .12em;
      text-transform: uppercase;
    }
    .links {
      display: flex;
      align-items: center;
      gap: 30px;
      color: #435249;
      font-size: 14px;
      font-weight: 650;
    }
    .links a:hover { color: var(--green); }
    .button {
      display: inline-flex;
      min-height: 46px;
      align-items: center;
      justify-content: center;
      gap: 9px;
      padding: 0 19px;
      border: 0;
      border-radius: 999px;
      background: var(--green);
      color: white;
      font-size: 14px;
      font-weight: 750;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(20, 125, 82, .18);
      transition: transform .18s ease, background .18s ease, box-shadow .18s ease;
    }
    .button:hover {
      transform: translateY(-2px);
      background: var(--green-dark);
      box-shadow: 0 12px 25px rgba(20, 125, 82, .24);
    }
    .button svg { width: 17px; height: 17px; }
    .menu-button {
      display: none;
      width: 44px;
      height: 44px;
      border: 1px solid var(--line);
      border-radius: 13px;
      background: white;
      color: var(--ink);
      cursor: pointer;
    }

    .hero {
      position: relative;
      overflow: hidden;
      padding: 82px 0 74px;
      background:
        radial-gradient(ellipse at 82% 18%, rgba(211, 239, 133, .45), transparent 30%),
        radial-gradient(ellipse at 100% 100%, rgba(20, 125, 82, .10), transparent 35%),
        var(--paper);
    }
    .hero-grid {
      display: grid;
      grid-template-columns: 1.02fr .98fr;
      gap: 56px;
      align-items: center;
    }
    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 7px 12px;
      border: 1px solid #d6e7d9;
      border-radius: 999px;
      background: rgba(255,255,255,.7);
      color: var(--green-dark);
      font-size: 12px;
      font-weight: 750;
      letter-spacing: .06em;
      text-transform: uppercase;
    }
    .eyebrow i {
      width: 7px;
      height: 7px;
      border-radius: 50%;
      background: #64b879;
      box-shadow: 0 0 0 4px #e4f2df;
    }
    h1 {
      max-width: 650px;
      margin: 22px 0 18px;
      font-size: clamp(42px, 5.7vw, 72px);
      line-height: .99;
      letter-spacing: -.065em;
    }
    h1 span { color: var(--green); }
    .hero-copy {
      max-width: 530px;
      margin: 0;
      color: var(--muted);
      font-size: 17px;
      line-height: 1.75;
    }
    .hero-actions {
      display: flex;
      align-items: center;
      gap: 18px;
      flex-wrap: wrap;
      margin-top: 30px;
    }
    .text-link {
      display: inline-flex;
      gap: 8px;
      align-items: center;
      color: var(--ink);
      font-size: 14px;
      font-weight: 750;
    }
    .text-link:hover { color: var(--green); }
    .text-link svg { width: 18px; height: 18px; }
    .trust {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-top: 35px;
      color: var(--muted);
      font-size: 12px;
    }
    .trust-avatars { display: flex; padding-left: 4px; }
    .trust-avatars span {
      width: 30px;
      height: 30px;
      display: grid;
      place-items: center;
      margin-left: -5px;
      border: 2px solid var(--paper);
      border-radius: 50%;
      background: #d9e8d9;
      color: var(--green-dark);
      font-size: 10px;
      font-weight: 800;
    }
    .trust-avatars span:nth-child(2) { background: #f1dfbf; }
    .trust-avatars span:nth-child(3) { background: #d9e1ef; }

    .hero-visual {
      position: relative;
      min-height: 465px;
      display: grid;
      place-items: center;
    }
    .visual-bg {
      position: absolute;
      inset: 20px 10px 12px 28px;
      border-radius: 46% 54% 40% 60% / 47% 42% 58% 53%;
      background: #dcebdc;
      transform: rotate(-5deg);
    }
    .visual-card {
      position: relative;
      width: min(100%, 465px);
      overflow: hidden;
      border: 8px solid rgba(255,255,255,.75);
      border-radius: 34px;
      background: linear-gradient(155deg, #1d7653, #10452f);
      box-shadow: 0 32px 70px rgba(17, 66, 45, .2);
      transform: rotate(2deg);
    }
    .visual-card svg { display: block; width: 100%; height: auto; }
    .float-card {
      position: absolute;
      z-index: 2;
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 14px 17px;
      border: 1px solid rgba(255,255,255,.8);
      border-radius: 17px;
      background: rgba(255,255,255,.94);
      box-shadow: var(--shadow);
    }
    .float-card.one { top: 54px; left: 0; }
    .float-card.two { right: -2px; bottom: 46px; }
    .float-icon {
      width: 41px;
      height: 41px;
      display: grid;
      place-items: center;
      flex: 0 0 auto;
      border-radius: 13px;
      background: var(--mint);
      color: var(--green);
    }
    .float-icon svg { width: 21px; height: 21px; }
    .float-card b { display: block; font-size: 13px; }
    .float-card small { display: block; color: var(--muted); font-size: 11px; }

    .proof {
      padding: 22px 0;
      border-top: 1px solid var(--line);
      border-bottom: 1px solid var(--line);
      background: rgba(255,255,255,.45);
    }
    .proof-row {
      display: flex;
      justify-content: space-between;
      gap: 20px;
      align-items: center;
      flex-wrap: wrap;
    }
    .proof-label {
      color: var(--muted);
      font-size: 12px;
      font-weight: 700;
      letter-spacing: .08em;
      text-transform: uppercase;
    }
    .proof-items { display: flex; gap: 32px; flex-wrap: wrap; }
    .proof-items span {
      display: flex;
      align-items: center;
      gap: 8px;
      color: #46564c;
      font-size: 13px;
      font-weight: 700;
    }
    .proof-items svg { width: 17px; height: 17px; color: var(--green); }

    section { scroll-margin-top: 95px; }
    .section { padding: 90px 0; }
    .section-head {
      max-width: 650px;
      margin: 0 auto 42px;
      text-align: center;
    }
    .section-head .eyebrow { margin-bottom: 15px; }
    h2 {
      margin: 0 0 13px;
      font-size: clamp(31px, 4vw, 48px);
      line-height: 1.08;
      letter-spacing: -.05em;
    }
    .section-head p { margin: 0; color: var(--muted); }
    .services {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 16px;
    }
    .service {
      min-height: 245px;
      padding: 23px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: white;
      box-shadow: 0 8px 24px rgba(24,55,39,.035);
      transition: transform .2s ease, box-shadow .2s ease, border-color .2s ease;
    }
    .service:hover {
      transform: translateY(-5px);
      border-color: #b7d6bd;
      box-shadow: var(--shadow);
    }
    .service-icon {
      width: 48px;
      height: 48px;
      display: grid;
      place-items: center;
      margin-bottom: 24px;
      border-radius: 15px;
      background: var(--mint);
      color: var(--green);
    }
    .service-icon svg { width: 24px; height: 24px; }
    .service h3 { margin: 0 0 8px; font-size: 17px; letter-spacing: -.02em; }
    .service p { margin: 0; color: var(--muted); font-size: 13px; line-height: 1.7; }
    .service .more {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      margin-top: 18px;
      color: var(--green);
      font-size: 12px;
      font-weight: 800;
    }

    .about {
      padding: 72px 0;
      background: #143f2d;
      color: white;
    }
    .about-grid {
      display: grid;
      grid-template-columns: .9fr 1.1fr;
      gap: 75px;
      align-items: center;
    }
    .about h2 { max-width: 470px; }
    .about p { color: rgba(255,255,255,.73); }
    .about .eyebrow {
      border-color: rgba(255,255,255,.18);
      background: rgba(255,255,255,.08);
      color: #d9f0df;
    }
    .about-list { display: grid; gap: 15px; }
    .about-item {
      display: flex;
      gap: 14px;
      align-items: flex-start;
      padding: 17px;
      border: 1px solid rgba(255,255,255,.13);
      border-radius: 16px;
      background: rgba(255,255,255,.055);
    }
    .check {
      width: 28px;
      height: 28px;
      display: grid;
      place-items: center;
      flex: 0 0 auto;
      border-radius: 50%;
      background: var(--lime);
      color: var(--green-dark);
    }
    .check svg { width: 16px; height: 16px; }
    .about-item b { display: block; margin-bottom: 3px; font-size: 14px; }
    .about-item span { color: rgba(255,255,255,.7); font-size: 12px; }

    .steps {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 20px;
      counter-reset: step;
    }
    .step {
      position: relative;
      padding: 25px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: white;
    }
    .step::before {
      counter-increment: step;
      content: "0" counter(step);
      display: block;
      margin-bottom: 24px;
      color: var(--green);
      font-size: 13px;
      font-weight: 850;
      letter-spacing: .1em;
    }
    .step h3 { margin: 0 0 8px; font-size: 18px; }
    .step p { margin: 0; color: var(--muted); font-size: 13px; }

    .contact {
      padding: 85px 0;
      background:
        radial-gradient(ellipse at 90% 15%, rgba(211,239,133,.25), transparent 32%),
        #eaf2e9;
    }
    .contact-grid {
      display: grid;
      grid-template-columns: .9fr 1.1fr;
      gap: 55px;
      align-items: start;
    }
    .contact-copy h2 { margin-top: 17px; }
    .contact-copy p { color: var(--muted); }
    .contact-note {
      display: flex;
      gap: 12px;
      align-items: flex-start;
      margin-top: 28px;
      color: #46564c;
      font-size: 13px;
    }
    .contact-note svg { width: 21px; height: 21px; flex: 0 0 auto; color: var(--green); }
    .form-card {
      padding: 28px;
      border: 1px solid rgba(227,233,227,.9);
      border-radius: 24px;
      background: white;
      box-shadow: var(--shadow);
    }
    .form-card h3 { margin: 0 0 20px; font-size: 20px; }
    .form-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; }
    label {
      display: grid;
      gap: 6px;
      color: #49584e;
      font-size: 12px;
      font-weight: 700;
    }
    label.full { grid-column: 1 / -1; }
    input, select, textarea {
      width: 100%;
      min-height: 45px;
      padding: 11px 12px;
      border: 1px solid #dce5dc;
      border-radius: 11px;
      background: #fbfcfa;
      color: var(--ink);
      font: inherit;
      font-size: 14px;
    }
    textarea { min-height: 100px; resize: vertical; }
    input:focus, select:focus, textarea:focus {
      outline: 3px solid rgba(20,125,82,.15);
      border-color: var(--green);
    }
    .form-card .button { width: 100%; margin-top: 17px; }
    .form-small { margin: 12px 0 0; color: var(--muted); font-size: 11px; text-align: center; }

    footer {
      padding: 28px 0;
      background: #102f22;
      color: white;
    }
    .foot-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 22px;
      flex-wrap: wrap;
    }
    footer .brand small { color: rgba(255,255,255,.6); }
    footer p { margin: 0; color: rgba(255,255,255,.65); font-size: 12px; }
    .foot-links { display: flex; gap: 18px; color: rgba(255,255,255,.76); font-size: 12px; }
    .foot-links a:hover { color: var(--lime); }

    @media (max-width: 900px) {
      .hero-grid { gap: 25px; }
      .hero-visual { min-height: 380px; }
      .services { grid-template-columns: repeat(2, 1fr); }
      .about-grid { gap: 35px; }
    }
    @media (max-width: 680px) {
      .wrap { width: min(100% - 30px, 540px); }
      .topline .wrap { justify-content: center; text-align: center; }
      .topline span:last-child { display: none; }
      .nav { min-height: 68px; }
      .menu-button { display: grid; place-items: center; }
      .nav-cta { display: none; }
      .links {
        position: absolute;
        top: 67px;
        left: 0;
        right: 0;
        display: none;
        padding: 17px 20px 22px;
        border-bottom: 1px solid var(--line);
        background: var(--paper);
        box-shadow: 0 14px 20px rgba(20,45,30,.07);
      }
      .links.open { display: grid; gap: 16px; }
      .hero { padding: 54px 0 48px; }
      .hero-grid, .about-grid, .contact-grid { grid-template-columns: 1fr; }
      .hero-grid { gap: 18px; }
      h1 { font-size: clamp(43px, 13vw, 62px); }
      .hero-copy { font-size: 15px; }
      .hero-visual { min-height: 340px; margin-top: 8px; }
      .visual-card { width: min(90%, 400px); }
      .float-card.one { top: 24px; left: -3px; }
      .float-card.two { right: -4px; bottom: 20px; }
      .proof-row { justify-content: center; text-align: center; }
      .proof-items { justify-content: center; gap: 14px 21px; }
      .section { padding: 66px 0; }
      .section-head { margin-bottom: 28px; }
      .services { gap: 11px; }
      .service { min-height: 0; padding: 18px; }
      .service-icon { margin-bottom: 18px; }
      .about { padding: 60px 0; }
      .steps { grid-template-columns: 1fr; }
      .step { padding: 20px; }
      .step::before { margin-bottom: 12px; }
      .contact { padding: 64px 0; }
      .contact-grid { gap: 25px; }
      .form-card { padding: 20px; }
      .foot-row { align-items: flex-start; }
    }
    @media (max-width: 420px) {
      .services { grid-template-columns: 1fr; }
      .form-grid { grid-template-columns: 1fr; }
      label.full { grid-column: auto; }
      .hero-actions { align-items: flex-start; flex-direction: column; }
      .float-card { padding: 10px 12px; }
      .float-card.two { right: -5px; }
    }
    @media (prefers-reduced-motion: reduce) {
      html { scroll-behavior: auto; }
      *, *::before, *::after {
        transition-duration: .01ms !important;
        animation-duration: .01ms !important;
      }
    }
  </style>
</head>
<body>
  <div class="topline">
    <div class="wrap">
      <span>Seguridad y Salud Laboral · Venezuela</span>
      <span>Prevención que cuida a las personas y fortalece a las empresas</span>
    </div>
  </div>

  <header>
    <div class="wrap nav">
      <a class="brand" href="#inicio" aria-label="SST Venezuela, inicio">
        <span class="brand-mark" aria-hidden="true">
          <svg viewBox="0 0 24 24" fill="none">
            <path d="M12 2.5 20 5v6.2c0 5.1-3.4 8.6-8 10.3-4.6-1.7-8-5.2-8-10.3V5l8-2.5Z" stroke="currentColor" stroke-width="1.7"/>
            <path d="m8.3 12.2 2.4 2.4 5-5.2" stroke="#d3ef85" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </span>
        <span>SST VENEZUELA<small>Seguridad y Salud Laboral</small></span>
      </a>

      <nav class="links" id="navlinks" aria-label="Navegación principal">
        <a href="#servicios">Servicios</a>
        <a href="#nosotros">Nosotros</a>
        <a href="#proceso">Cómo trabajamos</a>
        <a href="#contacto">Contacto</a>
      </nav>

      <a class="button nav-cta" href="#contacto">
        Solicitar información
        <svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M5 12h14m-6-6 6 6-6 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
      </a>

      <button class="menu-button" id="menuButton" aria-label="Abrir menú" aria-expanded="false" aria-controls="navlinks">
        <svg viewBox="0 0 24 24" width="21" height="21" fill="none" aria-hidden="true"><path d="M4 7h16M4 12h16M4 17h16" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg>
      </button>
    </div>
  </header>

  <main>
    <section class="hero" id="inicio">
      <div class="wrap hero-grid">
        <div>
          <div class="eyebrow"><i></i> Cuidamos a quienes hacen crecer tu empresa</div>
          <h1>Un trabajo más seguro. <span>Un equipo más fuerte.</span></h1>
          <p class="hero-copy">
            Acompañamos a empresas en la gestión de Seguridad y Salud en el Trabajo:
            prevención de riesgos, formación y apoyo para construir espacios laborales más seguros.
          </p>
          <div class="hero-actions">
            <a class="button" href="#contacto">
              Hablemos de tu empresa
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M5 12h14m-6-6 6 6-6 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
            </a>
            <a class="text-link" href="#servicios">
              Conoce los servicios
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M12 5v14m-6-6 6 6 6-6" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/></svg>
            </a>
          </div>
          <div class="trust">
            <div class="trust-avatars" aria-hidden="true"><span>S</span><span>+</span><span>✓</span></div>
            <span>Prevención práctica, formación y acompañamiento cercano.</span>
          </div>
        </div>

        <div class="hero-visual" aria-label="Ilustración de seguridad laboral">
          <div class="visual-bg"></div>
          <div class="float-card one">
            <span class="float-icon">
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M12 3 20 6v5.5c0 4.7-3.2 8-8 9.5-4.8-1.5-8-4.8-8-9.5V6l8-3Z" stroke="currentColor" stroke-width="1.7"/><path d="m8.5 12 2.2 2.2 4.8-5" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/></svg>
            </span>
            <span><b>Prevenir es avanzar</b><small>La seguridad empieza cada día</small></span>
          </div>
          <div class="visual-card">
            <svg viewBox="0 0 520 470" role="img" aria-label="Personas con equipos de protección trabajando de forma segura">
              <defs>
                <linearGradient id="bg" x1="0" y1="0" x2="1" y2="1">
                  <stop offset="0" stop-color="#27865f"/><stop offset="1" stop-color="#0e5238"/>
                </linearGradient>
                <linearGradient id="vest" x1="0" y1="0" x2="0" y2="1">
                  <stop offset="0" stop-color="#e7f27b"/><stop offset="1" stop-color="#bbd956"/>
                </linearGradient>
              </defs>
              <rect width="520" height="470" fill="url(#bg)"/>
              <circle cx="414" cy="92" r="118" fill="#6fb786" opacity=".22"/>
              <circle cx="80" cy="385" r="148" fill="#063e2b" opacity=".26"/>
              <path d="M0 370c105-30 177 18 273-8 92-25 159-17 247 8v100H0V370Z" fill="#0b482f" opacity=".65"/>
              <!-- edificio y ventanas -->
              <path d="M330 80h128v257H330z" fill="#d2e8d6" opacity=".13"/>
              <path d="M351 108h28v29h-28zm52 0h28v29h-28zm-52 51h28v29h-28zm52 0h28v29h-28zm-52 51h28v29h-28zm52 0h28v29h-28z" fill="#d2e8d6" opacity=".45"/>
              <!-- trabajador izquierdo -->
              <g transform="translate(165 108)">
                <path d="M-42 124q42-27 84 0l28 165h-140z" fill="url(#vest)"/>
                <path d="m-23 125 23 62 23-62" fill="#1c6548"/>
                <path d="m-42 145-46 93 17 10 56-75m57-28 46 93-17 10-56-75" fill="#efb17f"/>
                <path d="M-39 288h49v72h-49zm51 0h49v72H12z" fill="#233d36"/>
                <path d="M-48 355h62v13h-68zm55 0h65v13H7z" fill="#172a25"/>
                <rect x="-13" y="91" width="26" height="31" rx="8" fill="#bb8059"/>
                <ellipse cy="59" rx="39" ry="45" fill="#d69a70"/>
                <path d="M-42 51a42 42 0 0 1 84 0z" fill="#f3c94f"/>
                <rect x="-47" y="48" width="94" height="11" rx="5" fill="#f3c94f"/>
                <path d="M-20 66h5m29 0h5" stroke="#583b2d" stroke-width="4" stroke-linecap="round"/>
                <path d="M-10 82q10 8 20 0" fill="none" stroke="#8b5136" stroke-width="3" stroke-linecap="round"/>
                <path d="M-22 174h44" stroke="#fff" stroke-width="9" opacity=".85"/>
              </g>
              <!-- trabajadora derecha -->
              <g transform="translate(295 153) scale(.82)">
                <path d="M-42 124q42-27 84 0l28 165h-140z" fill="#f0a94f"/>
                <path d="m-23 125 23 62 23-62" fill="#1c6548"/>
                <path d="m-42 145-46 93 17 10 56-75m57-28 46 93-17 10-56-75" fill="#d99a70"/>
                <path d="M-39 288h49v72h-49zm51 0h49v72H12z" fill="#27443a"/>
                <path d="M-48 355h62v13h-68zm55 0h65v13H7z" fill="#172a25"/>
                <rect x="-13" y="91" width="26" height="31" rx="8" fill="#a96c49"/>
                <ellipse cy="59" rx="39" ry="45" fill="#c88761"/>
                <path d="M-42 51a42 42 0 0 1 84 0z" fill="#f3c94f"/>
                <rect x="-47" y="48" width="94" height="11" rx="5" fill="#f3c94f"/>
                <path d="M-20 66h5m29 0h5" stroke="#583b2d" stroke-width="4" stroke-linecap="round"/>
                <path d="M-10 82q10 8 20 0" fill="none" stroke="#8b5136" stroke-width="3" stroke-linecap="round"/>
                <path d="M-22 174h44" stroke="#fff" stroke-width="9" opacity=".85"/>
              </g>
              <!-- señal de seguridad -->
              <g transform="translate(423 280)">
                <path d="M0-40 38 28h-76z" fill="#f3c94f"/>
                <path d="M0-19v24m0 12v2" stroke="#344336" stroke-width="6" stroke-linecap="round"/>
              </g>
              <!-- hojas decorativas -->
              <path d="M30 304q18-48 52-55-3 40-52 55Zm27 18q-8-47 15-74 17 36-15 74Zm366 29q9-43 43-59-3 38-43 59Z" fill="#a7d187" opacity=".65"/>
            </svg>
          </div>
          <div class="float-card two">
            <span class="float-icon">
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M4 18V9l8-5 8 5v9M2 20h20M8 14l2.5 2.5L16 11" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round"/></svg>
            </span>
            <span><b>Bienestar en el trabajo</b><small>Personas seguras, equipos fuertes</small></span>
          </div>
        </div>
      </div>
    </section>

    <div class="proof">
      <div class="wrap proof-row">
        <span class="proof-label">Acompañamiento integral SST</span>
        <div class="proof-items">
          <span><svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="m5 12 4 4L19 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>Prevención</span>
          <span><svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="m5 12 4 4L19 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>Formación</span>
          <span><svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="m5 12 4 4L19 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>Gestión de riesgos</span>
          <span><svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="m5 12 4 4L19 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>Salud laboral</span>
        </div>
      </div>
    </div>

    <section class="section" id="servicios">
      <div class="wrap">
        <div class="section-head">
          <div class="eyebrow"><i></i> Lo que hacemos</div>
          <h2>Seguridad laboral, más sencilla y cercana</h2>
          <p>Te ayudamos a organizar la prevención y a promover una cultura de cuidado en cada área de tu empresa.</p>
        </div>
        <div class="services">
          <article class="service">
            <div class="service-icon"><svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M3 20h18M5 20V8l7-4 7 4v12M9 20v-6h6v6M8 9h.01M12 9h.01M16 9h.01" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round"/></svg></div>
            <h3>Gestión de riesgos</h3>
            <p>Identificación de peligros y apoyo para definir medidas de prevención y control.</p>
            <a class="more" href="#contacto">Conocer más <span>→</span></a>
          </article>
          <article class="service">
            <div class="service-icon"><svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2Z" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round"/><path d="m9 10 2 2 4-4" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round"/></svg></div>
            <h3>Formación SST</h3>
            <p>Capacitación para fortalecer conocimientos, hábitos seguros y participación.</p>
            <a class="more" href="#contacto">Conocer más <span>→</span></a>
          </article>
          <article class="service">
            <div class="service-icon"><svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M12 21s8-4 8-11V5l-8-3-8 3v5c0 7 8 11 8 11Z" stroke="currentColor" stroke-width="1.7" stroke-linejoin="round"/><path d="m9 12 2 2 4-4" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/></svg></div>
            <h3>Programa de prevención</h3>
            <p>Planificación de acciones, seguimiento y mejora continua en seguridad y salud.</p>
            <a class="more" href="#contacto">Conocer más <span>→</span></a>
          </article>
          <article class="service">
            <div class="service-icon"><svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M20.8 4.6a5.5 5.5 0 0 0-7.8 0L12 5.7l-1.1-1.1a5.5 5.5 0 0 0-7.8 7.8l1.1 1.1L12 21l7.8-7.5 1.1-1.1a5.5 5.5 0 0 0-.1-7.8Z" stroke="currentColor" stroke-width="1.7" stroke-linejoin="round"/><path d="M5 12h3l1.5-3 3 6 1.5-3H19" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round"/></svg></div>
            <h3>Bienestar laboral</h3>
            <p>Promoción de condiciones de trabajo saludables y atención al bienestar del equipo.</p>
            <a class="more" href="#contacto">Conocer más <span>→</span></a>
          </article>
        </div>
      </div>
    </section>

    <section class="about" id="nosotros">
      <div class="wrap about-grid">
        <div>
          <div class="eyebrow"><i></i> Nuestra forma de trabajar</div>
          <h2>La prevención funciona cuando todos participan</h2>
          <p>
            La seguridad laboral no es solo un documento: se construye con información clara,
            acciones posibles y seguimiento constante, con las personas en el centro.
          </p>
          <a class="button" href="#contacto" style="background:var(--lime);color:#163d2b;box-shadow:none">
            Conversemos
            <svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M5 12h14m-6-6 6 6-6 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
          </a>
        </div>
        <div class="about-list">
          <div class="about-item">
            <span class="check"><svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="m5 12 4 4L19 6" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/></svg></span>
            <span><b>Enfoque práctico</b><span>Recomendaciones claras, vinculadas con la realidad de cada lugar de trabajo.</span></span>
          </div>
          <div class="about-item">
            <span class="check"><svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="m5 12 4 4L19 6" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/></svg></span>
            <span><b>Participación del equipo</b><span>Impulsamos la comunicación y el compromiso con la prevención.</span></span>
          </div>
          <div class="about-item">
            <span class="check"><svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="m5 12 4 4L19 6" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/></svg></span>
            <span><b>Acompañamiento continuo</b><span>Apoyo para organizar acciones, revisar avances y seguir mejorando.</span></span>
          </div>
        </div>
      </div>
    </section>

    <section class="section" id="proceso">
      <div class="wrap">
        <div class="section-head">
          <div class="eyebrow"><i></i> Un camino claro</div>
          <h2>Empezar es más fácil de lo que parece</h2>
          <p>Trabajamos contigo para entender tus necesidades y dar pasos concretos hacia un entorno laboral más seguro.</p>
        </div>
        <div class="steps">
          <article class="step">
            <h3>Conocemos tu realidad</h3>
            <p>Conversamos sobre tu empresa, sus actividades y los retos de seguridad y salud que quieres atender.</p>
          </article>
          <article class="step">
            <h3>Organizamos prioridades</h3>
            <p>Identificamos oportunidades de mejora y acordamos acciones prácticas junto con tu equipo.</p>
          </article>
          <article class="step">
            <h3>Te acompañamos</h3>
            <p>Apoyamos la implementación y el seguimiento para que la prevención avance de forma sostenida.</p>
          </article>
        </div>
      </div>
    </section>

    <section class="contact" id="contacto">
      <div class="wrap contact-grid">
        <div class="contact-copy">
          <div class="eyebrow"><i></i> Hablemos</div>
          <h2>Tu equipo merece trabajar con seguridad</h2>
          <p>Cuéntanos qué necesita tu empresa y nos pondremos en contacto para conversar sobre las opciones de acompañamiento.</p>
          <div class="contact-note">
            <svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M12 22s8-4 8-11V5l-8-3-8 3v6c0 7 8 11 8 11Z" stroke="currentColor" stroke-width="1.7"/><path d="m9 12 2 2 4-4" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round"/></svg>
            <span>La información de este sitio es general y no sustituye una evaluación profesional de las condiciones de trabajo ni asesoría legal.</span>
          </div>
        </div>
        <div class="form-card">
          <h3>Solicita información</h3>
          <form id="contactForm">
            <div class="form-grid">
              <label>Tu nombre
                <input name="nombre" autocomplete="name" placeholder="Nombre y apellido" required>
              </label>
              <label>Empresa
                <input name="empresa" autocomplete="organization" placeholder="Nombre de la empresa">
              </label>
              <label>Correo electrónico
                <input name="correo" type="email" autocomplete="email" placeholder="nombre@empresa.com" required>
              </label>
              <label>Teléfono
                <input name="telefono" type="tel" autocomplete="tel" placeholder="+58">
              </label>
              <label class="full">¿En qué podemos ayudarte?
                <select name="servicio">
                  <option value="">Selecciona una opción</option>
                  <option>Gestión de riesgos</option>
                  <option>Formación en Seguridad y Salud Laboral</option>
                  <option>Programa de prevención</option>
                  <option>Bienestar laboral</option>
                  <option>Otro tipo de consulta</option>
                </select>
              </label>
              <label class="full">Mensaje
                <textarea name="mensaje" placeholder="Cuéntanos brevemente qué necesitas"></textarea>
              </label>
            </div>
            <button class="button" type="submit">
              Preparar mensaje
              <svg viewBox="0 0 24 24" fill="none" aria-hidden="true"><path d="M22 2 11 13" stroke="currentColor" stroke-width="2" stroke-linecap="round"/><path d="m22 2-7 20-4-9-9-4 20-7Z" stroke="currentColor" stroke-width="1.7" stroke-linejoin="round"/></svg>
            </button>
            <p class="form-small">El botón abrirá tu aplicación de correo para enviar la consulta.</p>
          </form>
        </div>
      </div>
    </section>
  </main>

  <footer>
    <div class="wrap foot-row">
      <a class="brand" href="#inicio">
        <span class="brand-mark" aria-hidden="true">
          <svg viewBox="0 0 24 24" fill="none"><path d="M12 2.5 20 5v6.2c0 5.1-3.4 8.6-8 10.3-4.6-1.7-8-5.2-8-10.3V5l8-2.5Z" stroke="currentColor" stroke-width="1.7"/><path d="m8.3 12.2 2.4 2.4 5-5.2" stroke="#d3ef85" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
        </span>
        <span>SST VENEZUELA<small>Seguridad y Salud Laboral</small></span>
      </a>
      <p>© <span id="year"></span> SST Venezuela. Cuidar también es prevenir.</p>
      <div class="foot-links">
        <a href="#servicios">Servicios</a>
        <a href="#contacto">Contacto</a>
        <a href="#inicio">Volver arriba ↑</a>
      </div>
    </div>
  </footer>

  <script>
    const menuButton = document.getElementById('menuButton');
    const navlinks = document.getElementById('navlinks');

    menuButton.addEventListener('click', () => {
      const open = navlinks.classList.toggle('open');
      menuButton.setAttribute('aria-expanded', String(open));
      menuButton.setAttribute('aria-label', open ? 'Cerrar menú' : 'Abrir menú');
    });

    navlinks.querySelectorAll('a').forEach(link => {
      link.addEventListener('click', () => {
        navlinks.classList.remove('open');
        menuButton.setAttribute('aria-expanded', 'false');
        menuButton.setAttribute('aria-label', 'Abrir menú');
      });
    });

    document.getElementById('year').textContent = new Date().getFullYear();

    document.getElementById('contactForm').addEventListener('submit', event => {
      event.preventDefault();
      const data = new FormData(event.currentTarget);
      const subject = encodeURIComponent('Consulta desde la web de SST Venezuela');
      const body = encodeURIComponent(
        'Nombre: ' + (data.get('nombre') || '') + '\\n' +
        'Empresa: ' + (data.get('empresa') || '') + '\\n' +
        'Correo: ' + (data.get('correo') || '') + '\\n' +
        'Teléfono: ' + (data.get('telefono') || '') + '\\n' +
        'Servicio: ' + (data.get('servicio') || '') + '\\n\\n' +
        'Mensaje:\\n' + (data.get('mensaje') || '')
      );
      // Sustituye el correo de ejemplo por el correo real de contacto.
      window.location.href = 'mailto:contacto@sstvenezuela.com?subject=' + subject + '&body=' + body;
    });
  </script>
</body>
</html>
