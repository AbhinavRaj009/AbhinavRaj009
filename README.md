<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Abhinav | Cyberpunk Portfolio</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&family=Roboto+Mono:wght@300;400;500&display=swap" rel="stylesheet" />

  <style>
    :root {
      --bg-main: #02040a;
      --bg-panel: rgba(5, 10, 25, 0.95);
      --accent-cyan: #00f0ff;
      --accent-magenta: #ff00ff;
      --accent-green: #39ff14;
      --text-primary: #f5f5f5;
      --text-muted: #b0b0b0;
      --border-neon: rgba(0, 240, 255, 0.4);
      --shadow-neon: 0 0 18px rgba(0, 240, 255, 0.6);
      --shadow-magenta: 0 0 18px rgba(255, 0, 255, 0.6);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      scroll-behavior: smooth;
    }

    body {
      background: radial-gradient(circle at top, #151531 0, #02040a 60%);
      color: var(--text-primary);
      font-family: "Roboto Mono", monospace;
      min-height: 100vh;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    /* ============ NEON NOISE BACKGROUND OVERLAY ============ */
    .noise {
      pointer-events: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      opacity: 0.18;
      background-image: url("https://i.imgur.com/o9fKQ8u.png");
      mix-blend-mode: soft-light;
      z-index: 1;
    }

    /* ============ NAVBAR ============ */
    header {
      position: sticky;
      top: 0;
      z-index: 10;
      backdrop-filter: blur(14px);
      background: linear-gradient(
        90deg,
        rgba(2, 4, 10, 0.95),
        rgba(10, 10, 30, 0.85),
        rgba(2, 4, 10, 0.95)
      );
      border-bottom: 1px solid var(--border-neon);
      box-shadow: 0 0 18px rgba(0, 0, 0, 0.8);
    }

    .nav-container {
      max-width: 1100px;
      margin: 0 auto;
      padding: 0.75rem 1.5rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .nav-brand {
      font-family: "Orbitron", sans-serif;
      font-size: 1.2rem;
      letter-spacing: 3px;
      color: var(--accent-cyan);
      text-shadow: var(--shadow-neon);
    }

    .nav-links {
      display: flex;
      gap: 1.5rem;
      font-size: 0.85rem;
      text-transform: uppercase;
    }

    .nav-links a {
      position: relative;
      color: var(--text-muted);
      letter-spacing: 1px;
    }

    .nav-links a::after {
      content: "";
      position: absolute;
      left: 0;
      bottom: -4px;
      width: 0;
      height: 2px;
      background: linear-gradient(90deg, var(--accent-cyan), var(--accent-magenta));
      box-shadow: var(--shadow-neon);
      transition: width 0.25s ease;
    }

    .nav-links a:hover {
      color: var(--accent-cyan);
    }

    .nav-links a:hover::after {
      width: 100%;
    }

    /* ============ HERO / BANNER ============ */
    main {
      position: relative;
      z-index: 2;
    }

    .hero {
      max-width: 1100px;
      margin: 0 auto;
      padding: 4rem 1.5rem 3rem;
      display: grid;
      grid-template-columns: minmax(0, 3fr) minmax(0, 2fr);
      gap: 3rem;
      align-items: center;
    }

    @media (max-width: 900px) {
      .hero {
        grid-template-columns: 1fr;
        padding-top: 3rem;
      }
    }

    .hero-text small {
      text-transform: uppercase;
      letter-spacing: 3px;
      color: var(--accent-green);
      font-weight: 500;
    }

    .hero-title {
      margin-top: 1rem;
      font-family: "Orbitron", sans-serif;
      font-size: clamp(2.5rem, 4vw, 3.5rem);
      line-height: 1.1;
      text-transform: uppercase;
    }

    .hero-title span.name {
      display: inline-block;
      color: var(--accent-cyan);
      text-shadow: 0 0 10px rgba(0, 240, 255, 0.9), 0 0 25px rgba(0, 240, 255, 0.8);
      animation: neonPulse 2.4s infinite ease-in-out;
    }

    .hero-title span.role {
      color: var(--accent-magenta);
      text-shadow: var(--shadow-magenta);
    }

    .hero-subtitle {
      margin-top: 1rem;
      color: var(--text-muted);
      font-size: 0.95rem;
      max-width: 480px;
      line-height: 1.6;
    }

    .hero-cta {
      margin-top: 1.8rem;
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
    }

    .btn-neon {
      position: relative;
      padding: 0.7rem 1.6rem;
      border-radius: 999px;
      border: 1px solid var(--accent-cyan);
      color: var(--accent-cyan);
      text-transform: uppercase;
      font-size: 0.8rem;
      letter-spacing: 1.5px;
      background: radial-gradient(circle at top left, rgba(0, 240, 255, 0.12), rgba(0, 0, 0, 0.8));
      box-shadow: var(--shadow-neon);
      cursor: pointer;
      overflow: hidden;
      transition: transform 0.18s ease, box-shadow 0.18s ease, border-color 0.18s ease;
    }

    .btn-neon::before {
      content: "";
      position: absolute;
      top: 0;
      left: -120%;
      width: 80%;
      height: 100%;
      background: linear-gradient(120deg, transparent, rgba(255, 255, 255, 0.7), transparent);
      transform: skewX(-20deg);
      transition: transform 0.5s ease;
    }

    .btn-neon:hover::before {
      transform: translateX(250%);
    }

    .btn-neon:hover {
      transform: translateY(-2px);
      box-shadow: 0 0 25px rgba(0, 240, 255, 0.8);
      border-color: var(--accent-magenta);
      color: #ffffff;
    }

    .btn-outline {
      border-color: var(--accent-magenta);
      color: var(--accent-magenta);
      box-shadow: var(--shadow-magenta);
    }

    .hero-tags {
      margin-top: 1.5rem;
      display: flex;
      flex-wrap: wrap;
      gap: 0.6rem;
      font-size: 0.7rem;
    }

    .tag-pill {
      padding: 0.25rem 0.7rem;
      border-radius: 999px;
      border: 1px dashed rgba(255, 255, 255, 0.18);
      color: var(--text-muted);
      background: rgba(5, 10, 25, 0.8);
    }

    .hero-banner {
      position: relative;
      justify-self: center;
    }

    .banner-frame {
      position: relative;
      width: 100%;
      max-width: 360px;
      aspect-ratio: 4/5;
      border-radius: 26px;
      border: 1px solid var(--border-neon);
      background: radial-gradient(circle at 20% 0, rgba(0, 240, 255, 0.22), transparent 60%),
        radial-gradient(circle at 80% 100%, rgba(255, 0, 255, 0.25), transparent 60%),
        #050716;
      box-shadow: 0 0 35px rgba(0, 240, 255, 0.35), 0 0 55px rgba(255, 0, 255, 0.3);
      overflow: hidden;
    }

    .banner-grid {
      position: absolute;
      inset: 0;
      opacity: 0.35;
      background-image: linear-gradient(transparent 95%, rgba(0, 240, 255, 0.2) 96%, transparent 100%),
        linear-gradient(90deg, transparent 95%, rgba(255, 0, 255, 0.2) 96%, transparent 100%);
      background-size: 100% 18px, 18px 100%;
    }

    .banner-content {
      position: relative;
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      padding: 1.5rem;
    }

    .banner-top-label {
      font-size: 0.7rem;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--accent-cyan);
    }

    .banner-main-text {
      margin-top: 1rem;
      font-family: "Orbitron", sans-serif;
      font-size: 1.5rem;
      text-transform: uppercase;
    }

    .banner-main-text span {
      display: block;
    }

    .banner-main-text .primary {
      color: var(--accent-cyan);
      text-shadow: var(--shadow-neon);
    }

    .banner-main-text .secondary {
      color: var(--accent-magenta);
      text-shadow: var(--shadow-magenta);
      font-size: 1.1rem;
    }

    .banner-bottom {
      font-size: 0.78rem;
      color: var(--text-muted);
    }

    .banner-chip-row {
      display: flex;
      gap: 0.5rem;
      flex-wrap: wrap;
      margin-top: 0.5rem;
    }

    .chip {
      padding: 0.2rem 0.6rem;
      border-radius: 999px;
      font-size: 0.65rem;
      border: 1px solid rgba(255, 255, 255, 0.16);
      background: rgba(0, 0, 0, 0.35);
    }

    .floating-orb {
      position: absolute;
      width: 90px;
      height: 90px;
      border-radius: 50%;
      border: 1px solid rgba(0, 240, 255, 0.6);
      box-shadow: var(--shadow-neon);
      top: -40px;
      right: -40px;
      background: radial-gradient(circle, rgba(0, 240, 255, 0.9), transparent 65%);
      opacity: 0.8;
      filter: blur(0.3px);
      animation: floatOrb 5s ease-in-out infinite;
    }

    .floating-orb::after {
      content: "AI/ML";
      position: absolute;
      inset: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: "Orbitron", sans-serif;
      font-size: 0.65rem;
      color: #000;
      text-shadow: none;
    }

    @keyframes floatOrb {
      0% { transform: translate(0, 0); opacity: 0.8; }
      50% { transform: translate(-12px, 10px); opacity: 1; }
      100% { transform: translate(0, 0); opacity: 0.8; }
    }

    @keyframes neonPulse {
      0%, 100% {
        text-shadow: 0 0 8px rgba(0, 240, 255, 0.7), 0 0 25px rgba(0, 240, 255, 0.7);
      }
      50% {
        text-shadow: 0 0 4px rgba(0, 240, 255, 0.4), 0 0 15px rgba(0, 240, 255, 0.5);
      }
    }

    /* ============ SECTION LAYOUT ============ */
    section {
      max-width: 1100px;
      margin: 0 auto;
      padding: 2.5rem 1.5rem;
    }

    .section-heading {
      font-family: "Orbitron", sans-serif;
      text-transform: uppercase;
      letter-spacing: 3px;
      font-size: 1rem;
      color: var(--accent-cyan);
      margin-bottom: 0.75rem;
    }

    .section-subtitle {
      color: var(--text-muted);
      font-size: 0.9rem;
      margin-bottom: 1.8rem;
    }

    .panel {
      background: var(--bg-panel);
      border-radius: 18px;
      border: 1px solid rgba(255, 255, 255, 0.08);
      padding: 1.5rem;
      box-shadow: 0 0 26px rgba(0, 0, 0, 0.7);
    }

    /* ============ ABOUT ============ */
    .about-grid {
      display: grid;
      grid-template-columns: 2fr 1.4fr;
      gap: 2rem;
    }

    @media (max-width: 900px) {
      .about-grid {
        grid-template-columns: 1fr;
      }
    }

    .about-text p {
      font-size: 0.9rem;
      color: var(--text-muted);
      line-height: 1.7;
      margin-bottom: 0.75rem;
    }

    .about-highlight {
      margin-top: 0.75rem;
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      font-size: 0.8rem;
    }

    .metric {
      min-width: 100px;
    }

    .metric span.value {
      display: block;
      font-size: 1.2rem;
      color: var(--accent-green);
    }

    .metric span.label {
      color: var(--text-muted);
      font-size: 0.7rem;
      text-transform: uppercase;
      letter-spacing: 1px;
    }

    .about-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
      margin-top: 0.75rem;
      font-size: 0.7rem;
    }

    .about-tags span {
      padding: 0.25rem 0.6rem;
      border-radius: 999px;
      background: rgba(255, 255, 255, 0.03);
      border: 1px solid rgba(255, 255, 255, 0.08);
      color: var(--text-muted);
    }

    /* ============ PROJECTS ============ */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 1.5rem;
    }

    @media (max-width: 1000px) {
      .projects-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }
    }

    @media (max-width: 700px) {
      .projects-grid {
        grid-template-columns: 1fr;
      }
    }

    .project-card {
      position: relative;
      border-radius: 16px;
      overflow: hidden;
      background: radial-gradient(circle at top, rgba(0, 240, 255, 0.12), rgba(5, 10, 25, 0.95));
      border: 1px solid rgba(0, 240, 255, 0.25);
      box-shadow: 0 0 22px rgba(0, 0, 0, 0.9);
      transition: transform 0.2s ease, box-shadow 0.2s ease, border-color 0.2s ease;
      cursor: pointer;
    }

    .project-card:hover {
      transform: translateY(-6px);
      border-color: var(--accent-magenta);
      box-shadow: 0 0 25px rgba(255, 0, 255, 0.6);
    }

    .project-body {
      padding: 1.1rem 1.1rem 1rem;
    }

    .project-chip {
      font-size: 0.65rem;
      text-transform: uppercase;
      letter-spacing: 1px;
      color: var(--accent-green);
      margin-bottom: 0.4rem;
    }

    .project-title {
      font-size: 0.9rem;
      font-weight: 500;
      margin-bottom: 0.2rem;
      color: var(--accent-cyan);
    }

    .project-desc {
      font-size: 0.8rem;
      color: var(--text-muted);
      margin-bottom: 0.4rem;
      line-height: 1.5;
    }

    .project-tech {
      font-size: 0.7rem;
      color: var(--text-muted);
      margin-bottom: 0.7rem;
    }

    .project-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 0.7rem;
      color: var(--text-muted);
    }

    .project-footer a {
      color: var(--accent-magenta);
      text-decoration: underline;
      text-decoration-style: dotted;
    }

    /* ============ EXPERIENCE & EDUCATION ============ */
    .timeline {
      border-left: 1px dashed rgba(255, 255, 255, 0.2);
      padding-left: 1.3rem;
      margin-left: 0.4rem;
    }

    .timeline-item {
      margin-bottom: 1.5rem;
      position: relative;
    }

    .timeline-dot {
      position: absolute;
      left: -1.4rem;
      top: 0.35rem;
      width: 10px;
      height: 10px;
      border-radius: 50%;
      background: var(--accent-magenta);
      box-shadow: 0 0 12px rgba(255, 0, 255, 0.8);
    }

    .timeline-role {
      font-size: 0.9rem;
      color: var(--accent-cyan);
    }

    .timeline-org {
      font-size: 0.8rem;
      color: var(--text-muted);
    }

    .timeline-meta {
      font-size: 0.7rem;
      color: var(--accent-green);
      margin: 0.15rem 0 0.35rem;
    }

    .timeline-desc {
      font-size: 0.8rem;
      color: var(--text-muted);
      line-height: 1.5;
    }

    /* ============ CONTACT ============ */
    .contact-grid {
      display: grid;
      grid-template-columns: minmax(0, 2fr) minmax(0, 1.3fr);
      gap: 2rem;
    }

    @media (max-width: 900px) {
      .contact-grid {
        grid-template-columns: 1fr;
      }
    }

    .contact-list {
      font-size: 0.85rem;
      color: var(--text-muted);
      display: flex;
      flex-direction: column;
      gap: 0.6rem;
    }

    .contact-list span.label {
      font-size: 0.78rem;
      text-transform: uppercase;
      letter-spacing: 2px;
      color: var(--accent-green);
    }

    .social-links {
      display: flex;
      flex-wrap: wrap;
      gap: 0.7rem;
      margin-top: 0.8rem;
    }

    .social-links a {
      font-size: 0.8rem;
      padding: 0.35rem 0.8rem;
      border-radius: 999px;
      border: 1px solid rgba(255, 255, 255, 0.15);
      background: rgba(0, 0, 0, 0.5);
      color: var(--text-primary);
      transition: border-color 0.2s ease, color 0.2s ease;
    }

    .social-links a:hover {
      border-color: var(--accent-cyan);
      color: var(--accent-cyan);
    }

    .contact-message {
      font-size: 0.85rem;
      color: var(--text-muted);
      line-height: 1.7;
    }

    .footer {
      max-width: 1100px;
      margin: 0 auto;
      padding: 1rem 1.5rem 2.5rem;
      font-size: 0.7rem;
      text-align: center;
      color: var(--text-muted);
    }

    .footer span {
      color: var(--accent-magenta);
    }
  </style>
</head>

<body>
  <div class="noise"></div>

  <!-- ========== NAVBAR ========== -->
  <header>
    <div class="nav-container">
      <div class="nav-brand">ABHINAV_</div>
      <nav class="nav-links">
        <a href="#about">About</a>
        <a href="#projects">Projects</a>
        <a href="#experience">Experience</a>
        <a href="#contact">Contact</a>
      </nav>
    </div>
  </header>

  <!-- ========== HERO / BANNER ========== -->
  <main>
    <section class="hero" id="top">
      <div class="hero-text">
        <small>CYBERPUNK • AI • FULL-STACK</small>
        <h1 class="hero-title">
          <span class="name">ABHINAV</span><br />
          <span class="role">AI/ML & Full-Stack Engineer</span>
        </h1>
        <p class="hero-subtitle">
          I design and build intelligent, data-driven systems — from real-time automation pipelines
          to full-stack applications with clean, scalable architecture. I love blending
          <strong>AI/ML</strong>, <strong>backend engineering</strong>, and <strong>modern UI</strong>
          into one cohesive experience.
        </p>

        <div class="hero-cta"> 
          <a href="#projects" class="btn-neon">View Projects</a>
          <a href="#contact" class="btn-neon btn-outline">Contact Me</a>
        </div>

        <div class="hero-tags">
          <span class="tag-pill">Java • Python • C</span>
          <span class="tag-pill">React • Node • FastAPI</span>
          <span class="tag-pill">TensorFlow • OpenCV • Mediapipe</span>
          <span class="tag-pill">MongoDB • PostgreSQL</span>
        </div>
      </div>

      <div class="hero-banner">
        <div class="banner-frame">
          <div class="banner-grid"></div>
          <div class="banner-content">
            <div>
              <div class="banner-top-label">SYSTEM PROFILE</div>
              <div class="banner-main-text">
                <span class="primary">ABHINAV</span>
                <span class="secondary">CSE • AI/ML</span>
              </div>
            </div>

            <div class="banner-bottom">
              Building:
              <div class="banner-chip-row">
                <span class="chip">AI Pipelines</span>
                <span class="chip">Fintech Automation</span>
                <span class="chip">Microservices</span>
                <span class="chip">Gesture Interfaces</span>
              </div>
              <div style="margin-top:0.8rem; font-size:0.7rem; color:var(--accent-cyan);">
                STATUS: <span style="color:var(--accent-green);">AVAILABLE FOR HIRE</span>
              </div>
            </div>
          </div>
        </div>
        <div class="floating-orb"></div>
      </div>
    </section>

    <!-- ========== ABOUT ========== -->
    <section id="about">
      <div class="section-heading">ABOUT</div>
      <div class="section-subtitle">
        CSE graduate with AI/ML specialization, crafting intelligent solutions that solve real-world problems.
      </div>
      <div class="panel about-grid">
        <div class="about-text">
          <p>
            I’m a Computer Science & Engineering graduate with a specialization in
            <strong>Artificial Intelligence & Machine Learning</strong>. I enjoy turning ideas into
            production-ready systems — from backend APIs and automation pipelines to ML-powered
            features and experimental prototypes.
          </p>
          <p>
            Recently, I have worked on projects like <strong>gesture-based brightness control</strong>,
            <strong>credential microservices with Kubernetes</strong>, and a
            <strong>fintech data pipeline</strong> that integrates market data with AI insights.
          </p>
          <p>
            I write clean, maintainable code, and love learning new tools that help me build faster and better.
          </p>

          <div class="about-highlight">
            <div class="metric">
              <span class="value">B.Tech</span>
              <span class="label">CSE (AI/ML)</span>
            </div>
            <div class="metric">
              <span class="value">5★</span>
              <span class="label">HackerRank</span>
            </div>
            <div class="metric">
              <span class="value">Finalist</span>
              <span class="label">Graph-E-Thon</span>
            </div>
          </div>

          <div class="about-tags">
            <span>Deep Learning (Udemy)</span>
            <span>ML with Python (Udemy)</span>
            <span>Infosys AI Summer Training</span>
          </div>
        </div>

        <div>
          <div class="panel" style="background:rgba(5,10,25,0.95); border-style:dashed;">
            <div style="font-size:0.78rem; letter-spacing:2px; text-transform:uppercase; color:var(--accent-green); margin-bottom:0.6rem;">
              CURRENT FOCUS
            </div>
            <ul style="list-style:none; font-size:0.82rem; color:var(--text-muted); display:flex; flex-direction:column; gap:0.4rem;">
              <li>➤ AI-driven automation & analytics</li>
              <li>➤ Scalable backend design with Node / FastAPI</li>
              <li>➤ Clean architecture & testing best practices</li>
              <li>➤ Real-time data pipelines for fintech & tools</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- ========== PROJECTS ========== -->
    <section id="projects">
      <div class="section-heading">PROJECTS</div>
      <div class="section-subtitle">
        A snapshot of systems I’ve built — blending AI, backend engineering, and modern interfaces.
      </div>
      <div class="projects-grid">

        <!-- Project 1 -->
        <article class="project-card">
          <div class="project-body">
            <div class="project-chip">AI • ACCESSIBILITY</div>
            <div class="project-title">Brightness Control using Hand Gestures</div>
            <div class="project-desc">
              Gesture-based system that controls brightness and volume using hand movement — designed
              to improve accessibility for elderly and differently-abled users.
            </div>
            <div class="project-tech">
              OpenCV • Mediapipe • Python
            </div>
            <div class="project-footer">
              <span>Human-Computer Interaction</span>
              <a href="#" target="_blank" rel="noreferrer">View on GitHub →</a>
            </div>
          </div>
        </article>

        <!-- Project 2 -->
        <article class="project-card">
          <div class="project-body">
            <div class="project-chip">MICROSERVICES</div>
            <div class="project-title">Kube-Credential</div>
            <div class="project-desc">
              Microservice-based credential issuance & verification system with SHA-256 based identity,
              built for containerized, cloud-native environments.
            </div>
            <div class="project-tech">
              Node.js • React • Docker • Kubernetes
            </div>
            <div class="project-footer">
              <span>Secure Identity Layer</span>
              <a href="#" target="_blank" rel="noreferrer">View on GitHub →</a>
            </div>
          </div>
        </article>

        <!-- Project 3 -->
        <article class="project-card">
          <div class="project-body">
            <div class="project-chip">FINTECH • AI</div>
            <div class="project-title">FINTECH Market Intelligence</div>
            <div class="project-desc">
              Automated market data pipeline that integrates external APIs, PostgreSQL, and GPT-powered
              insights — deployed with scheduled runs for daily analytics.
            </div>
            <div class="project-tech">
              FastAPI • PostgreSQL • SQLAlchemy • GPT
            </div>
            <div class="project-footer">
              <span>Data + AI Pipeline</span>
              <a href="#" target="_blank" rel="noreferrer">View on GitHub →</a>
            </div>
          </div>
        </article>

      </div>
    </section>

    <!-- ========== EXPERIENCE ========== -->
    <section id="experience">
      <div class="section-heading">EXPERIENCE & EDUCATION</div>
      <div class="section-subtitle">
        Hands-on exposure to real-world projects, research-oriented AI content, and solid academic grounding.
      </div>

      <div class="panel">
        <div class="timeline">
          <!-- Experience 1 -->
          <div class="timeline-item">
            <div class="timeline-dot"></div>
            <div class="timeline-role">Web Developer Intern</div>
            <div class="timeline-org">Jamuna Foundation</div>
            <div class="timeline-meta">Project Management Tool • React • Node • MongoDB</div>
            <div class="timeline-desc">
              Built a project management tool for community initiatives — enabling better task
              organization, progress tracking, and team collaboration for social impact projects.
            </div>
          </div>

          <!-- Experience 2 -->
          <div class="timeline-item">
            <div class="timeline-dot"></div>
            <div class="timeline-role">AI/ML Intern</div>
            <div class="timeline-org">Earth5R</div>
            <div class="timeline-meta">AI for Sustainability • Technical Writing</div>
            <div class="timeline-desc">
              Contributed research-based content on AI/ML applications for environmental sustainability,
              simplifying complex ML concepts into engaging, reader-friendly articles.
            </div>
          </div>

          <!-- Education -->
          <div class="timeline-item">
            <div class="timeline-dot"></div>
            <div class="timeline-role">B.Tech — Computer Science & Engineering</div>
            <div class="timeline-org">Pranveer Singh Institute of Technology, Kanpur</div>
            <div class="timeline-meta">Specialization: Artificial Intelligence / Machine Learning</div>
            <div class="timeline-desc">
              Built a strong foundation in algorithms, data structures, operating systems, DBMS,
              cloud computing, and advanced AI/ML coursework.
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ========== CONTACT ========== -->
    <section id="contact">
      <div class="section-heading">CONTACT</div>
      <div class="section-subtitle">
        Let’s collaborate on intelligent systems, backend services, or AI-powered products.
      </div>

      <div class="panel contact-grid">
        <div>
          <div class="contact-message">
            Whether it’s a <strong>full-time opportunity</strong>, an internship, or a
            <strong>collaborative project</strong>, I’m excited to work on problems that matter —
            especially in AI, fintech, tools, and automation.
          </div>

          <div class="contact-list" style="margin-top:1.5rem;">
            <div>
              <span class="label">Email</span><br />
              <a href="mailto:abhinavraj528@gmail.com">abhinavraj528@gmail.com</a>
            </div>
            <div>
              <span class="label">Location</span><br />
              Lucknow, India
            </div>
            <div>
              <span class="label">Available For</span><br />
              Full-time • Internship • Remote / Hybrid
            </div>
          </div>
        </div>

        <div>
          <div class="social-links">
            <a href="#" target="_blank" rel="noreferrer">GitHub</a>
            <a href="#" target="_blank" rel="noreferrer">LinkedIn</a>
            <a href="#" target="_blank" rel="noreferrer">HackerRank</a>
            <a href="#" target="_blank" rel="noreferrer">Email Me</a>
          </div>
          <p style="font-size:0.8rem; color:var(--text-muted); margin-top:1.3rem;">
            Tip: once deployed, you can put this link on your resume and GitHub profile so recruiters
            instantly see your work with a strong visual impression.
          </p>
        </div>
      </div>
    </section>

    <div class="footer">
      © <span>ABHINAV</span> • Crafted with dark mode, neon, and way too much caffeine.
    </div>
  </main>
</body>
</html>
