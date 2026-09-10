<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="Our Projects Studio — создаём книги, лекции, фильмы и цифровые решения." />
  <title>Our Projects Studio</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800&family=Space+Grotesk:wght@400;500;600;700&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --deep-blue: #ffffff;
      --navy:      #0d2b6e;
      --blue:      #1a5cff;
      --cyan:      #00d4ff;
      --glass:     rgba(255, 255, 255, 0.55);
      --glass-border: rgba(13, 43, 110, 0.10);
      --white:     #0a1628;
      --text:      #0a1628;
      --muted:     #5c6b8a;
      --surface-alt: #ddeeff;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'Inter', sans-serif;
      background: #ffffff;
      color: var(--text);
      line-height: 1.6;
      -webkit-font-smoothing: antialiased;
    }

    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: var(--deep-blue); }
    ::-webkit-scrollbar-thumb { background: var(--cyan); border-radius: 3px; }

    /* ═══ NAV ═══ */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 0 5%;
      height: 72px;
      background: rgba(255, 255, 255, 0.72);
      backdrop-filter: blur(20px) saturate(1.4);
      border-bottom: 1px solid rgba(10, 22, 40, 0.04);
    }

    .nav-logo {
      display: flex;
      align-items: center;
      gap: 12px;
      text-decoration: none;
    }

    .nav-logo img {
      height: 42px;
      width: auto;
    }

    .nav-logo span {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 0.9rem;
      font-weight: 600;
      background: linear-gradient(90deg, #0a1628, var(--cyan));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    .nav-links {
      display: flex;
      gap: 32px;
      list-style: none;
    }

    .nav-links a {
      color: rgba(10, 22, 40, 0.55);
      text-decoration: none;
      font-size: 0.72rem;
      font-weight: 600;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      transition: color 0.25s ease;
      position: relative;
    }

    .nav-links a::after {
      content: '';
      position: absolute;
      bottom: -4px;
      left: 0;
      width: 0;
      height: 2px;
      background: var(--cyan);
      transition: width 0.3s ease;
    }

    .nav-links a:hover { color: var(--white); }
    .nav-links a:hover::after { width: 100%; }

    .nav-right {
      display: flex;
      align-items: center;
      gap: 16px;
    }

    .btn-login {
      display: inline-flex;
      align-items: center;
      padding: 8px 20px;
      border-radius: 60px;
      border: 1.5px solid rgba(13, 43, 110, 0.25);
      background: transparent;
      color: var(--navy);
      font-family: 'Inter', sans-serif;
      font-size: 0.72rem;
      font-weight: 700;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      cursor: pointer;
      transition: all 0.25s ease;
      white-space: nowrap;
    }

    .btn-login:hover {
      background: var(--navy);
      color: #fff;
      border-color: var(--navy);
      transform: translateY(-1px);
    }

    .burger {
      display: none;
      flex-direction: column;
      gap: 5px;
      cursor: pointer;
      background: none;
      border: none;
      padding: 4px;
    }
    .burger span {
      display: block;
      width: 24px;
      height: 2px;
      background: var(--white);
      border-radius: 2px;
      transition: 0.3s;
    }

    /* ═══ HERO ═══ */
    #hero {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      background: #ffffff;
      padding: 120px 5% 70px;
      position: relative;
      overflow: hidden;
    }

    #hero::before {
      content: '';
      position: absolute;
      inset: 0;
      background-image: url('https://optim.tildacdn.ink/tild3730-3865-4137-a431-653635333437/-/resize/400x/-/format/webp/_OpS.png.webp');
      background-repeat: no-repeat;
      background-position: center center;
      background-size: min(600px, 80vw);
      opacity: 0.08;
      pointer-events: none;
      z-index: 0;
    }

    #hero::after {
      content: '';
      position: absolute;
      inset: 0;
      background: radial-gradient(ellipse at center, rgba(255,255,255,0.0) 0%, rgba(255,255,255,0.55) 65%, rgba(255,255,255,0.85) 100%);
      pointer-events: none;
      z-index: 0;
    }

    .hero-badge {
      display: inline-block;
      padding: 6px 18px;
      border: 1px solid rgba(13, 43, 110, 0.18);
      border-radius: 100px;
      font-size: 0.65rem;
      font-weight: 600;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--navy);
      margin-bottom: 28px;
      position: relative;
      z-index: 1;
      background: rgba(255,255,255,0.7);
      backdrop-filter: blur(4px);
    }

    .hero-logo { display: none; }

    #hero h1 {
      font-family: 'Space Grotesk', sans-serif;
      font-size: clamp(2.6rem, 6vw, 4.2rem);
      font-weight: 700;
      color: var(--navy);
      letter-spacing: -0.03em;
      line-height: 1.08;
      margin-bottom: 16px;
      position: relative;
      z-index: 1;
    }

    #hero h1 span {
      background: linear-gradient(90deg, var(--blue), var(--cyan));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    #hero p {
      font-size: clamp(0.95rem, 1.3vw, 1.15rem);
      color: var(--muted);
      max-width: 480px;
      margin: 0 auto 40px;
      position: relative;
      z-index: 1;
      font-weight: 400;
    }

    .hero-cta {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      padding: 16px 40px;
      background: linear-gradient(135deg, var(--navy), var(--blue));
      color: #ffffff;
      border-radius: 60px;
      font-size: 0.8rem;
      font-weight: 700;
      letter-spacing: 0.04em;
      text-decoration: none;
      transition: all 0.3s ease;
      position: relative;
      z-index: 1;
      box-shadow: 0 8px 32px rgba(13, 43, 110, 0.25);
    }

    .hero-cta:hover {
      transform: translateY(-3px) scale(1.02);
      box-shadow: 0 12px 48px rgba(13, 43, 110, 0.35);
    }

    .scroll-hint {
      position: absolute;
      bottom: 32px;
      left: 50%;
      transform: translateX(-50%);
      color: rgba(13, 43, 110, 0.45);
      font-size: 0.6rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      z-index: 1;
      animation: floatDown 2.4s ease-in-out infinite;
    }

    @keyframes floatDown {
      0%, 100% { opacity: 0.2; transform: translateX(-50%) translateY(0); }
      50%       { opacity: 0.6; transform: translateX(-50%) translateY(6px); }
    }

    /* ═══ СЕКЦИИ ═══ */
    section { padding: 100px 5%; position: relative; }
    .container { max-width: 1200px; margin: 0 auto; }

    .section-label {
      font-size: 0.65rem;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--cyan);
      margin-bottom: 8px;
    }

    .section-title {
      font-family: 'Space Grotesk', sans-serif;
      font-size: clamp(1.8rem, 3.2vw, 2.8rem);
      font-weight: 700;
      color: var(--white);
      letter-spacing: -0.02em;
      line-height: 1.12;
      margin-bottom: 20px;
    }

    .section-title .highlight {
      background: linear-gradient(90deg, var(--cyan), #4dabff);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    .section-desc {
      color: var(--muted);
      font-size: 0.95rem;
      max-width: 560px;
      font-weight: 300;
    }

    /* ═══ ABOUT ═══ */
    #about {
      background: var(--deep-blue);
      border-top: 1px solid rgba(10, 22, 40, 0.06);
    }

    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 60px;
      align-items: start;
      margin-top: 20px;
    }

    .about-text p {
      color: var(--muted);
      font-size: 0.95rem;
      line-height: 1.8;
      margin-bottom: 18px;
    }
    .about-text p:last-child { margin-bottom: 0; }

    .about-stats {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
    }

    .stat-card {
      background: var(--glass);
      border: 1px solid var(--glass-border);
      border-radius: 12px;
      padding: 28px 24px;
      backdrop-filter: blur(10px);
      transition: border-color 0.3s ease;
    }

    .stat-card:hover { border-color: rgba(0, 212, 255, 0.2); }

    .stat-number {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 2.2rem;
      font-weight: 700;
      background: linear-gradient(135deg, var(--cyan), #4dabff);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      display: block;
    }

    .stat-label {
      font-size: 0.78rem;
      color: var(--muted);
      margin-top: 4px;
    }

    /* ═══ CEO ═══ */
    #ceo {
      background: var(--surface-alt);
      border-top: 1px solid rgba(10, 22, 40, 0.06);
    }

    .ceo-card {
      display: flex;
      align-items: flex-start;
      gap: 48px;
      margin-top: 16px;
      background: var(--glass);
      border: 1px solid var(--glass-border);
      border-radius: 16px;
      padding: 40px;
      backdrop-filter: blur(10px);
      max-width: 820px;
    }

    .ceo-photo {
      flex-shrink: 0;
      width: 180px;
      height: 240px;
      object-fit: cover;
      object-position: top center;
      border-radius: 12px;
      border: 2px solid rgba(0, 212, 255, 0.15);
    }

    .ceo-info .name {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 1.5rem;
      font-weight: 700;
      color: var(--white);
      margin-bottom: 2px;
    }

    .ceo-info .title {
      font-size: 0.72rem;
      font-weight: 600;
      color: var(--cyan);
      text-transform: uppercase;
      letter-spacing: 0.1em;
      margin-bottom: 16px;
    }

    .ceo-info p {
      color: var(--muted);
      font-size: 0.9rem;
      line-height: 1.8;
    }

    /* ═══ DIRECTIONS ═══ */
    #directions {
      background: var(--deep-blue);
      border-top: 1px solid rgba(10, 22, 40, 0.06);
    }

    .directions-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 24px;
      margin-top: 40px;
    }

    .dir-card {
      background: var(--glass);
      border: 1px solid var(--glass-border);
      border-radius: 12px;
      padding: 32px 28px;
      transition: all 0.35s ease;
      backdrop-filter: blur(10px);
      text-align: center;
      cursor: pointer;
      user-select: none;
    }

    .dir-card:hover {
      border-color: rgba(0, 212, 255, 0.2);
      transform: translateY(-6px);
      box-shadow: 0 20px 60px rgba(0, 0, 0, 0.1);
    }

    .dir-card img {
      width: 90px;
      height: 90px;
      object-fit: cover;
      border-radius: 12px;
      margin-bottom: 18px;
      display: block;
      margin-left: auto;
      margin-right: auto;
      border: 1px solid rgba(10, 22, 40, 0.06);
    }

    .dir-card h3 {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 1.1rem;
      font-weight: 600;
      color: var(--white);
      margin-bottom: 10px;
    }

    .dir-card p {
      color: var(--muted);
      font-size: 0.85rem;
      line-height: 1.7;
    }

    /* Некликабельная карточка */
    .dir-card.no-click {
      cursor: default;
    }
    .dir-card.no-click:hover {
      transform: none;
      box-shadow: none;
      border-color: var(--glass-border);
    }

    /* ═══ EVENTS ═══ */
    #events {
      background: var(--surface-alt);
      border-top: 1px solid rgba(10, 22, 40, 0.06);
    }

    .event-card {
      max-width: 640px;
      background: var(--glass);
      border: 1px solid var(--glass-border);
      border-radius: 12px;
      padding: 36px 40px;
      margin-top: 24px;
      backdrop-filter: blur(10px);
      border-left: 3px solid var(--cyan);
    }

    .event-status {
      display: inline-block;
      background: rgba(0, 212, 255, 0.1);
      color: var(--cyan);
      font-size: 0.6rem;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      padding: 4px 14px;
      border-radius: 100px;
      margin-bottom: 16px;
    }

    .event-card h3 {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 1.2rem;
      color: var(--white);
      margin-bottom: 12px;
    }

    .event-card p {
      color: var(--muted);
      font-size: 0.88rem;
      line-height: 1.8;
    }

    .no-events {
      color: rgba(10, 22, 40, 0.2);
      font-size: 0.85rem;
      margin-top: 20px;
    }

    /* ═══ SOCIAL ═══ */
    #social {
      background: var(--deep-blue);
      border-top: 1px solid rgba(10, 22, 40, 0.06);
      text-align: center;
    }

    #social .section-title { margin: 0 auto 8px; }
    #social .section-desc { margin: 0 auto 40px; }

    .social-grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 12px;
    }

    .social-link {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 12px 24px;
      background: var(--glass);
      border: 1px solid var(--glass-border);
      border-radius: 60px;
      text-decoration: none;
      color: rgba(10, 22, 40, 0.6);
      font-weight: 500;
      font-size: 0.8rem;
      transition: all 0.3s ease;
    }

    .social-link:hover {
      border-color: var(--cyan);
      color: var(--white);
      background: rgba(0, 212, 255, 0.06);
      transform: translateY(-2px);
    }

    .social-link svg { flex-shrink: 0; }

    /* ═══ CONTACT ═══ */
    #contact {
      background: var(--surface-alt);
      border-top: 1px solid rgba(10, 22, 40, 0.06);
    }

    .contact-wrapper {
      display: grid;
      grid-template-columns: 1fr;
      max-width: 480px;
      margin-top: 8px;
    }

    .contact-info h3 {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 1.1rem;
      color: var(--white);
      margin-bottom: 24px;
    }

    .contact-item {
      display: flex;
      align-items: center;
      gap: 14px;
      margin-bottom: 18px;
      color: var(--muted);
      font-size: 0.88rem;
    }

    .contact-item a {
      color: inherit;
      text-decoration: none;
      transition: color 0.2s;
    }
    .contact-item a:hover { color: var(--cyan); }

    .contact-icon {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      background: rgba(0, 212, 255, 0.08);
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
      border: 1px solid rgba(0, 212, 255, 0.06);
    }

    .contact-icon svg { color: var(--cyan); }

    /* ═══ FOOTER ═══ */
    footer {
      background: #ffffff;
      padding: 28px 5%;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 12px;
      border-top: 1px solid rgba(10, 22, 40, 0.03);
    }

    footer p {
      color: rgba(10, 22, 40, 0.15);
      font-size: 0.72rem;
    }

    footer a {
      color: rgba(10, 22, 40, 0.15);
      text-decoration: none;
      font-size: 0.72rem;
      transition: color 0.2s;
    }
    footer a:hover { color: var(--cyan); }

    /* ═══ МОДАЛЬНОЕ ОКНО ═══ */
    .modal-overlay {
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background: rgba(10, 22, 40, 0.6);
      backdrop-filter: blur(8px);
      z-index: 9999;
      display: none;
      align-items: center;
      justify-content: center;
      padding: 20px;
    }

    .modal-content {
      background: #ffffff;
      border-radius: 16px;
      max-width: 900px;
      width: 100%;
      max-height: 90vh;
      overflow-y: auto;
      position: relative;
      padding: 40px;
      box-shadow: 0 30px 60px rgba(0,0,0,0.2);
    }

    .modal-close {
      position: absolute;
      top: 20px;
      right: 20px;
      background: rgba(13, 43, 110, 0.05);
      border: none;
      width: 40px;
      height: 40px;
      border-radius: 50%;
      font-size: 24px;
      line-height: 1;
      color: var(--muted);
      cursor: pointer;
      transition: all 0.3s;
    }

    .modal-close:hover { background: var(--cyan); color: #fff; }

    .modal-header {
      margin-bottom: 30px;
    }

    .modal-header h3 {
      font-family: 'Space Grotesk', sans-serif;
      color: var(--navy);
      font-size: 1.8rem;
      margin-bottom: 10px;
    }

    .modal-tabs {
      display: flex;
      gap: 12px;
      margin-bottom: 30px;
      border-bottom: 2px solid var(--surface-alt);
      padding-bottom: 12px;
      flex-wrap: wrap;
    }

    .modal-tab {
      padding: 10px 20px;
      border-radius: 30px;
      border: 1px solid var(--glass-border);
      background: transparent;
      cursor: pointer;
      font-family: 'Inter', sans-serif;
      font-weight: 600;
      color: var(--muted);
      transition: all 0.2s;
    }

    .modal-tab.active {
      background: var(--navy);
      color: #fff;
      border-color: var(--navy);
    }

    .tab-content { display: none; animation: fadeIn 0.4s ease; }
    .tab-content.active { display: block; }

    @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

    .price-group {
      margin-bottom: 24px;
      background: var(--surface-alt);
      border-radius: 12px;
      padding: 20px;
    }

    .price-group h4 {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 1.3rem;
      color: var(--navy);
      margin-bottom: 16px;
      border-bottom: 1px solid rgba(255,255,255,0.6);
      padding-bottom: 8px;
    }

    .price-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px dashed var(--glass-border);
      padding: 12px 0;
      font-size: 0.95rem;
    }

    .price-item:last-child { border-bottom: none; }

    .price-item .item-info { color: var(--muted); flex-grow: 1; margin-right: 20px; }
    .price-item .item-price { font-family: 'Space Grotesk', sans-serif; font-weight: 700; color: var(--white); white-space: nowrap; }

    .price-item ul {
      margin-top: 5px;
      padding-left: 20px;
      font-size: 0.85rem;
      color: var(--text);
    }

    .info-text {
      font-size: 0.9rem;
      color: var(--muted);
      margin-bottom: 24px;
      line-height: 1.6;
    }

    .info-text strong { color: var(--white); }

    .steps-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 16px;
      margin-top: 20px;
    }

    .step-item {
      background: var(--deep-blue);
      border-radius: 8px;
      padding: 16px;
      text-align: center;
    }

    .step-item .step-num { font-family: 'Space Grotesk', sans-serif; font-weight: 700; color: var(--cyan); font-size: 1.4rem; margin-bottom: 5px; }
    .step-item .step-name { font-size: 0.85rem; color: var(--white); font-weight: 600; margin-bottom: 5px; }
    .step-item p { font-size: 0.78rem; color: var(--muted); }

    /* ═══ АДАПТАЦИЯ ═══ */
    @media (max-width: 768px) {
      .nav-links {
        display: none;
        flex-direction: column;
        position: absolute;
        top: 72px;
        left: 0;
        right: 0;
        background: rgba(255, 255, 255, 0.96);
        backdrop-filter: blur(20px);
        padding: 24px 5%;
        gap: 16px;
        border-bottom: 1px solid rgba(10, 22, 40, 0.04);
      }
      .nav-links.open { display: flex; }
      .burger { display: flex; }

      .about-grid { grid-template-columns: 1fr; gap: 40px; }
      .about-stats { grid-template-columns: 1fr 1fr; }

      .directions-grid { grid-template-columns: 1fr; }

      .ceo-card { flex-direction: column; align-items: center; text-align: center; padding: 28px; }
      .ceo-photo { width: 140px; height: 190px; }

      #hero h1 { font-size: clamp(2rem, 8vw, 2.8rem); }
      .hero-logo { width: min(160px, 35vw); }

      .modal-content { padding: 24px; }
      .modal-tabs { flex-direction: column; }
    }

    @media (max-width: 480px) {
      .about-stats { grid-template-columns: 1fr; }
      .social-grid { flex-direction: column; align-items: stretch; }
      .social-link { justify-content: center; }
    }

    /* ═══ ART MODAL ═══ */
    #artModal { display: none; }

    .art-modal-header {
      display: flex;
      align-items: center;
      gap: 16px;
      margin-bottom: 8px;
    }

    .art-modal-header img {
      width: 56px;
      height: 56px;
      object-fit: contain;
    }

    .art-modal-header h3 {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 1.4rem;
      font-weight: 700;
      color: var(--navy);
    }

    .art-modal-header p {
      font-size: 0.85rem;
      color: var(--muted);
      margin-top: 2px;
    }

    .books-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 24px;
      margin-top: 28px;
    }

    .book-card {
      background: var(--surface-alt);
      border-radius: 12px;
      overflow: hidden;
      border: 1px solid var(--glass-border);
      transition: transform 0.25s ease, box-shadow 0.25s ease;
    }

    .book-card:hover {
      transform: translateY(-4px);
      box-shadow: 0 12px 40px rgba(13, 43, 110, 0.12);
    }

    .book-cover {
      width: 100%;
      height: 220px;
      object-fit: cover;
      object-position: top center;
      display: block;
    }

    .book-info {
      padding: 20px;
    }

    .book-info h4 {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 1rem;
      font-weight: 700;
      color: var(--navy);
      margin-bottom: 8px;
      line-height: 1.3;
    }

    .book-info p {
      font-size: 0.8rem;
      color: var(--muted);
      line-height: 1.6;
    }

    /* Art: блок регистрации */
    .art-register-block {
      margin-top: 28px;
      background: var(--surface-alt);
      border-radius: 12px;
      padding: 24px;
      text-align: center;
      border: 1px solid var(--glass-border);
    }

    .art-register-block p {
      font-size: 0.9rem;
      color: var(--muted);
      margin-bottom: 16px;
      line-height: 1.6;
    }

    .btn-register {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 12px 32px;
      border-radius: 60px;
      border: none;
      background: linear-gradient(135deg, var(--navy), var(--blue));
      color: #fff;
      font-family: 'Inter', sans-serif;
      font-size: 0.8rem;
      font-weight: 700;
      letter-spacing: 0.04em;
      cursor: pointer;
      transition: all 0.3s ease;
      box-shadow: 0 8px 24px rgba(13, 43, 110, 0.2);
    }

    .btn-register:hover {
      transform: translateY(-2px);
      box-shadow: 0 12px 36px rgba(13, 43, 110, 0.3);
    }

    @media (max-width: 600px) {
      .books-grid { grid-template-columns: 1fr; }
      .art-modal-header h3 { font-size: 1.1rem; }
    }
  </style>
</head>
<body>

<!-- ═══ NAV ═══ -->
<nav>
  <a href="#hero" class="nav-logo">
    <img src="https://optim.tildacdn.ink/tild3730-3865-4137-a431-653635333437/-/resize/400x/-/format/webp/_OpS.png.webp" alt="Our Projects Studio" />
    <span>Our Projects Studio</span>
  </a>
  <ul class="nav-links" id="navLinks">
    <li><a href="#about">О нас</a></li>
    <li><a href="#ceo">Директор</a></li>
    <li><a href="#directions">Направления</a></li>
    <li><a href="#events">Мероприятия</a></li>
    <li><a href="#social">Соцсети</a></li>
    <li><a href="#contact">Контакты</a></li>
  </ul>
  <div class="nav-right">
    <button class="btn-login" type="button">Войти</button>
    <button class="burger" id="burger" aria-label="Меню">
      <span></span><span></span><span></span>
    </button>
  </div>
</nav>

<!-- ═══ HERO ═══ -->
<section id="hero">
  <div class="hero-badge">Est. 2024</div>

  <h1>Our Projects Studio</h1>
  <p>Сайты, боты, приложения, книги, лекции и сценарии — превращаем идеи в работающие решения.</p>
  <a href="#about" class="hero-cta">
    Узнать больше
    <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="M12 5l7 7-7 7"/></svg>
  </a>
  <div class="scroll-hint">Прокрутите</div>
</section>

<!-- ═══ ABOUT ═══ -->
<section id="about">
  <div class="container">
    <div class="section-label">О компании</div>
    <h2 class="section-title">Our Projects Studio</h2>

    <div class="about-grid">
      <div class="about-text">
        <p>
          Our Projects Studio была основана около двух лет назад. Тогда нынешний директор компании начал выпускать рекламные брошюры с надписью «Наши проекты» — и это стало отправной точкой.
        </p>
        <p>
          Сегодня мы занимаемся созданием лекций, написанием книг, съёмкой фильмов и сериалов, а также цифровыми разработками. На этом сайте вы можете следить за активными проектами компании и узнавать о новых направлениях.
        </p>
      </div>
      <div class="about-stats">
        <div class="stat-card">
          <span class="stat-number">6</span>
          <span class="stat-label">Запущенных проектов</span>
        </div>
        <div class="stat-card">
          <span class="stat-number">3</span>
          <span class="stat-label">Направления работы</span>
        </div>
        <div class="stat-card">
          <span class="stat-number">∞</span>
          <span class="stat-label">Идей в разработке</span>
        </div>
        <div class="stat-card">
          <span class="stat-number">2024</span>
          <span class="stat-label">Год основания</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══ CEO ═══ -->
<section id="ceo">
  <div class="container">
    <div class="section-label">Руководство</div>
    <h2 class="section-title">Генеральный директор</h2>

    <div class="ceo-card">
      <img src="https://optim.tildacdn.ink/tild3166-3062-4638-a136-613138656232/-/resize/400x/-/format/webp/z.jpg.webp" alt="Траун — Генеральный директор" class="ceo-photo" />
      <div class="ceo-info">
        <div class="name">Траун</div>
        <div class="title">Генеральный директор</div>
        <p>
          Курирует стратегическое развитие компании, литературные и исследовательские проекты. Автор романов «Войны корпораций» и «14±», архитектор вымышленных вселенных Our Projects Studio. Придерживается принципа, что глубина замысла и качество исполнения — единственные значимые критерии в творчестве.
        </p>
      </div>
    </div>
  </div>
</section>

<!-- ═══ DIRECTIONS ═══ -->
<section id="directions">
  <div class="container">
    <div class="section-label">Направления</div>
    <h2 class="section-title">Чем мы занимаемся</h2>

    <div class="directions-grid">

      <div class="dir-card" onclick="openArtModal()">
        <img src="https://optim.tildacdn.ink/tild3038-3735-4964-a566-376133316330/-/format/webp/image_1.jpeg.webp" alt="Our Projects Art" />
        <h3>Our Projects Art</h3>
        <p>Творческое направление, где рождаются истории. Книги, комиксы, сериалы, сценарии. Мы создаём миры, в которые хочется возвращаться.</p>
      </div>

      <div class="dir-card" onclick="openBusinessModal()">
        <img src="https://optim.tildacdn.ink/tild6533-3030-4131-b832-343763643733/-/resize/400x/-/format/webp/image_6a6bbb06347fc.jpeg.webp" alt="Our Projects Business" />
        <h3>Our Projects Business</h3>
        <p>Разрабатываем веб-приложения, Telegram-ботов, сайты-лендинги. Проводим викторины и квесты на заказ для бизнеса.</p>
      </div>

      <div class="dir-card no-click">
        <img src="https://optim.tildacdn.ink/tild6639-3739-4363-b533-393266613833/-/resize/400x/-/format/webp/photo_2026-09-03_21-.jpg.webp" alt="Our Projects Learn" />
        <h3>Our Projects Learn</h3>
        <p>Образовательное направление. В разработке — платформа для изучения иностранных языков. Система, которая помогает учиться эффективно.</p>
      </div>

    </div>
  </div>
</section>

<!-- ═══ EVENTS ═══ -->
<section id="events">
  <div class="container">
    <div class="section-label">Мероприятия</div>
    <h2 class="section-title">Наши события</h2>

    <div class="event-card">
      <div class="event-status">✓ Завершено</div>
      <h3>Our Projects Celebration 2026</h3>
      <p>Два вечера живой музыки, лекций по вселенным, музейных экспонатов и анонсов новых книг. Мероприятие прошло 5 и 12 сентября 2026 года.</p>
    </div>

    <p class="no-events">Ближайших мероприятий пока нет. Следите за обновлениями в соцсетях.</p>
  </div>
</section>

<!-- ═══ SOCIAL ═══ -->
<section id="social">
  <div class="container">
    <div class="section-label">Социальные сети</div>
    <h2 class="section-title">Мы в сети</h2>
    <p class="section-desc">Присоединяйтесь — там новости выходят быстрее всего.</p>

    <div class="social-grid">
      <a href="https://t.me/OurprojectsStudio" target="_blank" rel="noopener" class="social-link">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m22 2-7 20-4-9-9-4Z"/><path d="M22 2 11 13"/></svg>
        Telegram
      </a>
      <a href="https://vk.com/ourprojectsstudio" target="_blank" rel="noopener" class="social-link">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M15.07 2H8.93C3.33 2 2 3.33 2 8.93v6.14C2 20.67 3.33 22 8.93 22h6.14C20.67 22 22 20.67 22 15.07V8.93C22 3.33 20.67 2 15.07 2zm3.08 13.96h-1.57c-.59 0-.77-.47-1.84-1.55--.93-.9-1.34-.96-1.57-.96-.32 0-.41.09-.41.54v1.41c0 .38-.12.61-1.12.61-1.65 0-3.48-.99-4.77-2.85C5.71 11.46 5 9.61 5 9.23c0-.23.09-.45.54-.45h1.57c.41 0 .56.18.72.61.79 2.28 2.12 4.28 2.67 4.28.21 0 .3-.09.3-.59V11.1c-.06-1.07-.63-1.16-.63-1.54 0-.18.15-.36.39-.36h2.47c.34 0 .46.18.46.57v3.06c0 .34.15.46.25.46.21 0 .38-.12.76-.5 1.17-1.31 2.01-3.33 2.01-3.33.11-.23.3-.45.71-.45h1.57c.47 0 .58.24.47.57-.2.93-2.12 3.64-2.12 3.64-.17.27-.23.39 0 .69.17.23.72.7 1.09 1.12.67.76 1.19 1.4 1.33 1.84.14.43-.09.65-.53.65z"/></svg>
        ВКонтакте
      </a>
      <a href="https://max.ru/channel_Ourprojectsstudio" target="_blank" rel="noopener" class="social-link">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M8 12h8M12 8v8"/></svg>
        Max
      </a>
      <a href="https://www.instagram.com/ourprojectsstudio" target="_blank" rel="noopener" class="social-link">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r="1" fill="currentColor" stroke="none"/></svg>
        Instagram
      </a>
      <a href="https://x.com/OprojStud" target="_blank" rel="noopener" class="social-link">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.746l7.73-8.835L1.254 2.25H8.08l4.253 5.622zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
        X (Twitter)
      </a>
    </div>
  </div>
</section>

<!-- ═══ CONTACT ═══ -->
<section id="contact">
  <div class="container">
    <div class="section-label">Связаться</div>
    <h2 class="section-title">Напишите нам</h2>

    <div class="contact-wrapper">

      <div class="contact-info">
        <h3>Контакты</h3>

        <div class="contact-item">
          <div class="contact-icon">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 12 19.79 19.79 0 0 1 1.61 3.38 2 2 0 0 1 3.6 1.18h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L7.91 8.75a16 16 0 0 0 7.34 7.34l.95-.95a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/></svg>
          </div>
          <a href="tel:+79996755611">+7 999 675-56-11</a>
        </div>

        <div class="contact-item">
          <div class="contact-icon">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
          </div>
          <a href="mailto:Ourprojectsstudio2023@gmail.com">Ourprojectsstudio2023@gmail.com</a>
        </div>

        <div class="contact-item">
          <div class="contact-icon">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m22 2-7 20-4-9-9-4Z"/><path d="M22 2 11 13"/></svg>
          </div>
          <a href="https://t.me/OurprojectsStudio" target="_blank" rel="noopener">Telegram-канал</a>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- ═══ FOOTER ═══ -->
<footer>
  <p>© 2024–2026 Our Projects Studio</p>
  <a href="mailto:Ourprojectsstudio2023@gmail.com">Ourprojectsstudio2023@gmail.com</a>
</footer>

<!-- ═══ BUSINESS МОДАЛЬНОЕ ОКНО ═══ -->
<div class="modal-overlay" id="businessModal">
  <div class="modal-content">
    <button class="modal-close" onclick="closeBusinessModal()">×</button>
    <div class="modal-header">
      <h3>Our Projects Business</h3>
      <p style="color: var(--muted);">Цифровые инструменты, викторины и квесты для вашего бизнеса.</p>
    </div>

    <div class="modal-tabs">
      <button class="modal-tab active" onclick="switchBusinessTab(event, 'services')">Услуги для бизнеса</button>
      <button class="modal-tab" onclick="switchBusinessTab(event, 'quizzes')">Викторины и квесты</button>
    </div>

    <!-- Вкладка: Услуги -->
    <div id="services" class="tab-content active">
      <div class="info-text">
        <strong>Что мы делаем:</strong> Разрабатываем цифровые инструменты для бизнеса: сайты, боты, приложения.<br>
        Два формата работы: отдельные услуги и пакеты с абонементом.
      </div>

      <div class="price-group">
        <h4>Отдельные услуги</h4>
        <div class="price-item">
          <div class="item-info">Сайт-лендинг</div>
          <div class="item-price">5 000 ₽</div>
        </div>
        <div class="price-item">
          <div class="item-info">Telegram-бот</div>
          <div class="item-price">6 000 ₽</div>
        </div>
        <div class="price-item">
          <div class="item-info">Веб-приложение</div>
          <div class="item-price">9 000 ₽</div>
        </div>
        <div class="info-text" style="margin-top: 10px; font-size: 0.85rem;">
          Для отдельных услуг доступна подписка на поддержку — <strong>1 500 ₽/мес</strong> (оперативная поддержка, мелкие доработки, хостинг и техобслуживание).
        </div>
      </div>

      <div class="price-group">
        <h4>Пакеты</h4>
        <div class="info-text" style="margin-top: 0; font-size: 0.85rem;">
          Для покупки пакета нужен абонемент — он открывает доступ ко всем пакетам на 12 месяцев без повторной оплаты, даёт приоритетное обслуживание, сокращённые сроки ответа и сопровождение весь срок действия.
        </div>

        <div class="price-item">
          <div class="item-info">
            <strong>«Старт»</strong> — 4 500 ₽ + абонемент 1 500 ₽<br>
            <span style="font-size: 0.85rem;">Один продукт на выбор: лендинг, бот или веб-приложение.</span>
          </div>
        </div>

        <div class="price-item">
          <div class="item-info">
            <strong>«Комплект»</strong> — 8 500 ₽ + абонемент 2 000 ₽<br>
            <span style="font-size: 0.85rem;">Два продукта на выбор из трёх. Без синхронизации данных между ними.</span>
          </div>
        </div>

        <div class="price-item">
          <div class="item-info">
            <strong>«Синхро»</strong> — 9 500 ₽ + абонемент 2 000 ₽<br>
            <span style="font-size: 0.85rem;">Два продукта на выбор из трёх, с полной синхронизацией данных между ними (например, заявка с лендинга сразу попадает в бота и админку без ручного переноса).</span>
          </div>
        </div>

        <div class="price-item">
          <div class="item-info">
            <strong>«Комплект Плюс»</strong> — 12 500 ₽ + абонемент 2 500 ₽<br>
            <span style="font-size: 0.85rem;">Все три продукта: лендинг, бот и веб-приложение. Без синхронизации.</span>
          </div>
        </div>

        <div class="price-item">
          <div class="item-info">
            <strong>«Синхро Плюс»</strong> — 14 000 ₽ + абонемент 2 500 ₽<br>
            <span style="font-size: 0.85rem;">Все три продукта с полной синхронизацией данных между ними.</span>
          </div>
        </div>

        <div class="info-text" style="margin-top: 15px; font-size: 0.85rem;">
          <strong>Важно:</strong> Абонемент оплачивается один раз на 12 месяцев. При покупке второго и последующих пакетов в течение этого срока — скидка 15% на пакет, абонемент повторно не оплачивается.
        </div>
      </div>

      <div class="price-group">
        <h4>Приёмка и доработки</h4>
        <div class="info-text" style="margin-top: 0; font-size: 0.9rem;">
          Разработка ведётся по утверждённому техническому заданию (ТЗ). В стоимость входит: реализация функционала по ТЗ, устранение ошибок, доводка до соответствия ТЗ.<br><br>
          Всё, что выходит за рамки ТЗ, оплачивается отдельно — полный прайс на доработки (интеграции, доп. отчёты, поля в базе, дизайн-правки и т.д.) вышлю по запросу. При заказе от трёх доработок сразу — скидка 10% на сумму.
        </div>
      </div>

      <div class="price-group">
        <h4>Цены фиксированные</h4>
        <div class="info-text" style="margin-top: 0; font-size: 0.9rem;">
          Стоимость не зависит от сложности реализации — количество интеграций, страниц и объёма данных уже включено в цену продукта.
        </div>
      </div>

    </div>

    <!-- Вкладка: Викторины и квесты -->
    <div id="quizzes" class="tab-content">
      <div class="info-text">
        Создаём уникальные викторины и квесты специально под вашу аудиторию, тематику и формат мероприятия.<br>
        От простой викторины до полноценного игрового расследования — разработаем концепцию, вопросы, задания и презентацию, проведём тестирование и подготовим проект к запуску.
      </div>

      <div class="price-group">
        <h4>Авторские викторины</h4>
        <div class="price-item">
          <div class="item-info">
            <strong>Классик</strong> — 1 000 ₽<br>
            <span style="font-size: 0.85rem;">Стандартный формат для лёгкого и увлекательного прохождения.</span>
            <ul>
              <li>До 15 вопросов</li>
              <li>До 20 слайдов</li>
            </ul>
          </div>
        </div>
        <div class="price-item">
          <div class="item-info">
            <strong>Профи</strong> — 1 500 ₽<br>
            <span style="font-size: 0.85rem;">Более сложная и насыщенная викторина с расширенными возможностями.</span>
            <ul>
              <li>До 30 вопросов</li>
              <li>До 35 слайдов</li>
              <li>Дополнительные вопросы и варианты ответов</li>
            </ul>
          </div>
        </div>
        <div class="price-item">
          <div class="item-info">
            <strong>Эксклюзив</strong> — 2 000 ₽<br>
            <span style="font-size: 0.85rem;">Полностью индивидуальная викторина с уникальным содержанием и дизайном.</span>
            <ul>
              <li>До 50 вопросов</li>
              <li>До 55 слайдов</li>
              <li>Индивидуальная концепция и оформление</li>
            </ul>
          </div>
        </div>
      </div>

      <div class="price-group">
        <h4>Квесты</h4>
        <div class="info-text" style="margin-top: 0; font-size: 0.85rem;">Выберите подходящий уровень сложности и отправляйтесь в собственное приключение.</div>
        <div class="price-item">
          <div class="item-info">
            <strong>Короткий квест</strong> — 1 500 ₽<br>
            <span style="font-size: 0.85rem;">Компактный формат для небольшого мероприятия.</span>
            <ul><li>До 10 заданий</li></ul>
          </div>
        </div>
        <div class="price-item">
          <div class="item-info">
            <strong>Квест средней сложности</strong> — 2 000 ₽<br>
            <span style="font-size: 0.85rem;">Более продолжительное приключение с большим количеством заданий.</span>
            <ul><li>До 25 заданий</li></ul>
          </div>
        </div>
        <div class="price-item">
          <div class="item-info">
            <strong>Комплексное расследование</strong> — 2 500 ₽<br>
            <span style="font-size: 0.85rem;">Масштабный квест с насыщенным сюжетом и большим количеством заданий.</span>
            <ul><li>До 40 заданий</li></ul>
          </div>
        </div>
      </div>

      <div class="price-group">
        <h4>Проведение с личным участием автора</h4>
        <div class="info-text" style="margin-top: 0; font-size: 0.9rem;">
          Хотите не только получить готовую игру, но и провести её вместе с автором?<br>
          Мы проведём викторину или квест, адаптировав программу под вашу аудиторию и тематику.
        </div>
        <div class="price-item">
          <div class="item-info">Викторина</div>
          <div class="item-price">2 000 ₽/час</div>
        </div>
        <div class="price-item">
          <div class="item-info">Квест</div>
          <div class="item-price">3 000 ₽/час</div>
        </div>
        <div class="info-text" style="margin-top: 10px; font-size: 0.85rem;">
          Дополнительное продление на месте, не согласованное заранее, — 700 ₽/час (при задержке от 15 минут).
        </div>
      </div>

      <div class="price-group">
        <h4>Как проходит работа</h4>
        <div class="steps-grid">
          <div class="step-item"><div class="step-num">01</div><div class="step-name">Заявка</div><p>Расскажите нам о своей идее и пожеланиях.</p></div>
          <div class="step-item"><div class="step-num">02</div><div class="step-name">Обсуждение</div><p>Согласовываем формат, содержание, сроки и стоимость.</p></div>
          <div class="step-item"><div class="step-num">03</div><div class="step-name">Предоплата</div><p>Перед началом работы вносится 50% стоимости заказа.</p></div>
          <div class="step-item"><div class="step-num">04</div><div class="step-name">Разработка концепции</div><p>Создаём концепцию, определяем формат и содержание игры.</p></div>
          <div class="step-item"><div class="step-num">05</div><div class="step-name">Создание контента</div><p>Разрабатываем вопросы, задания и, при необходимости, презентацию.</p></div>
          <div class="step-item"><div class="step-num">06</div><div class="step-name">Тестирование</div><p>Проверяем готовую игру и исправляем возможные ошибки.</p></div>
          <div class="step-item"><div class="step-num">07</div><div class="step-name">Запуск</div><p>Передаём и запускаем проект в соответствии с согласованными условиями.</p></div>
          <div class="step-item"><div class="step-num">08</div><div class="step-name">Финальная оплата</div><p>После выполнения заказа оплачивается оставшаяся часть стоимости.</p></div>
          <div class="step-item"><div class="step-num">09</div><div class="step-name">Поддержка</div><p>При необходимости предоставляем техническую поддержку и выполняем дополнительные доработки.</p></div>
        </div>
        <div class="info-text" style="margin-top: 20px; text-align: center; font-weight: 600;">
          Создадим игру, которую захочется пройти до конца.
        </div>
      </div>
    </div>

  </div>
</div>

<!-- ═══ ART МОДАЛЬНОЕ ОКНО ═══ -->
<div class="modal-overlay" id="artModal">
  <div class="modal-content">
    <button class="modal-close" onclick="closeArtModal()">×</button>

    <div class="art-modal-header">
      <img src="https://optim.tildacdn.ink/tild3038-3735-4964-a566-376133316330/-/format/webp/image_1.jpeg.webp" alt="Our Projects Art" />
      <div>
        <h3>Our Projects Art</h3>
        <p>Книги, комиксы, сериалы, сценарии — миры, в которые хочется возвращаться.</p>
      </div>
    </div>

    <!-- Три палки (табы) для Art -->
    <div class="modal-tabs">
      <button class="modal-tab active" onclick="switchArtTab(event, 'art-books')">Книги</button>
      <button class="modal-tab" onclick="switchArtTab(event, 'art-series')">Сериалы</button>
    </div>

    <!-- Вкладка: Книги -->
    <div id="art-books" class="tab-content active">
      <div class="books-grid">

        <!-- Книга 1 -->
        <div class="book-card">
          <img
            class="book-cover"
            src="https://optim.tildacdn.ink/tild3536-6330-4665-b863-636630333765/-/resize/400x/-/format/webp/1000042150.jpg.webp"
            alt="14±: История первой любви. Три слова"
          />
          <div class="book-info">
            <h4>14±: История первой любви. Три слова</h4>
            <p>Роман о первой любви, взрослении и тех трёх словах, которые меняют всё. История о том, как хрупкие чувства сталкиваются с суровой реальностью, и о выборе, который определяет дальнейший путь.</p>
          </div>
        </div>

        <!-- Книга 2 -->
        <div class="book-card">
          <img
            class="book-cover"
            src="https://optim.tildacdn.ink/tild6633-6432-4431-a466-303261373330/-/resize/688x/-/format/webp/-.jpg.webp"
            alt="Войны корпораций ● Искра возмездия"
          />
          <div class="book-info">
            <h4>Войны корпораций ● Искра возмездия</h4>
            <p>Мир корпоративных войн, где одна искра способна изменить расстановку сил навсегда. Напряжённый сюжет о власти, предательстве и возмездии в недалёком будущем.</p>
          </div>
        </div>

      </div>

      <!-- Блок: регистрация для чтения -->
      <div class="art-register-block">
        <p>
          Чтобы прочитать книги полностью, необходимо зарегистрироваться.
        </p>
        <button class="btn-register" type="button" onclick="openRegisterModal()">
          Зарегистрироваться
        </button>
      </div>
    </div>

    <!-- Вкладка: Сериалы -->
    <div id="art-series" class="tab-content">
      <div class="info-text" style="margin-top: 20px;">
        В разработке — сериалы по вселенным Our Projects Studio. Следите за анонсами в наших социальных сетях.
      </div>
    </div>

  </div>
</div>

<script>
  // Burger
  const burger = document.getElementById('burger');
  const navLinks = document.getElementById('navLinks');
  if (burger && navLinks) {
    burger.addEventListener('click', () => navLinks.classList.toggle('open'));
    navLinks.querySelectorAll('a').forEach(a =>
      a.addEventListener('click', () => navLinks.classList.remove('open'))
    );
  }

  // Универсальные функции открытия/закрытия
  function showModal(id) {
    const m = document.getElementById(id);
    if (!m) return;
    m.style.display = 'flex';
    document.body.style.overflow = 'hidden';
  }

  function hideModal(id) {
    const m = document.getElementById(id);
    if (!m) return;
    m.style.display = 'none';
    document.body.style.overflow = '';
  }

  // === BUSINESS ===
  function openBusinessModal() { showModal('businessModal'); }
  function closeBusinessModal() { hideModal('businessModal'); }

  // === ART ===
  function openArtModal() { showModal('artModal'); }
  function closeArtModal() { hideModal('artModal'); }

  // Заглушка регистрации
  function openRegisterModal() {
    alert('Окно регистрации скоро появится');
  }

  // Закрытие по клику на фон
  ['businessModal', 'artModal'].forEach(id => {
    const m = document.getElementById(id);
    if (!m) return;
    m.addEventListener('click', (e) => {
      if (e.target === m) hideModal(id);
    });
  });

  // Универсальное переключение табов
  function switchTabGeneric(containerId, tabId, btn) {
    const parent = document.getElementById(containerId);
    if (!parent) return;

    parent.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));
    const target = parent.querySelector('#' + tabId);
    if (target) target.classList.add('active');

    const tabs = btn.closest('.modal-tabs');
    if (tabs) {
      tabs.querySelectorAll('.modal-tab').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
    }
  }

  function switchBusinessTab(event, tabId) {
    switchTabGeneric('businessModal', tabId, event.currentTarget);
  }

  function switchArtTab(event, tabId) {
    switchTabGeneric('artModal', tabId, event.currentTarget);
  }
</script>

</body>
</html>
