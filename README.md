<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EduMedia — Social Media for Schools</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --navy: #0a1628;
    --navy-mid: #132040;
    --gold: #f5c518;
    --gold-light: #ffd84d;
    --cream: #faf8f2;
    --warm-white: #ffffff;
    --text-body: #2d3748;
    --text-muted: #718096;
    --accent-blue: #2563eb;
    --green: #10b981;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--cream);
    color: var(--text-body);
    overflow-x: hidden;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    background: rgba(10,22,40,0.97);
    backdrop-filter: blur(12px);
    padding: 0 5%;
    display: flex; align-items: center; justify-content: space-between;
    height: 68px;
  }
  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem; font-weight: 900;
    color: var(--warm-white);
    letter-spacing: -0.02em;
  }
  .nav-logo span { color: var(--gold); }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    color: rgba(255,255,255,0.75);
    text-decoration: none; font-size: 0.9rem; font-weight: 500;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--gold); }
  .nav-cta {
    background: var(--gold); color: var(--navy);
    padding: 0.55rem 1.4rem; border-radius: 6px;
    font-weight: 600; font-size: 0.9rem; text-decoration: none;
    transition: background 0.2s, transform 0.15s;
  }
  .nav-cta:hover { background: var(--gold-light); transform: translateY(-1px); }

  /* HERO */
  .hero {
    background: var(--navy);
    min-height: 100vh;
    display: flex; align-items: center;
    padding: 68px 5% 0;
    position: relative; overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute; top: -20%; right: -10%;
    width: 700px; height: 700px;
    background: radial-gradient(circle, rgba(245,197,24,0.12) 0%, transparent 65%);
    pointer-events: none;
  }
  .hero::after {
    content: '';
    position: absolute; bottom: -15%; left: -5%;
    width: 500px; height: 500px;
    background: radial-gradient(circle, rgba(37,99,235,0.1) 0%, transparent 65%);
    pointer-events: none;
  }
  .hero-inner {
    max-width: 1200px; margin: 0 auto;
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 4rem; align-items: center;
  }
  .hero-badge {
    display: inline-flex; align-items: center; gap: 0.5rem;
    background: rgba(245,197,24,0.12); border: 1px solid rgba(245,197,24,0.3);
    color: var(--gold); padding: 0.4rem 0.9rem;
    border-radius: 100px; font-size: 0.8rem; font-weight: 600;
    letter-spacing: 0.05em; text-transform: uppercase;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.6s ease forwards;
  }
  .hero-badge::before { content: '★'; font-size: 0.7rem; }
  .hero-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2.8rem, 5vw, 4.2rem);
    font-weight: 900; line-height: 1.08;
    color: var(--warm-white);
    letter-spacing: -0.03em;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.6s 0.1s ease both;
  }
  .hero-title em { color: var(--gold); font-style: normal; }
  .hero-desc {
    color: rgba(255,255,255,0.65);
    font-size: 1.1rem; line-height: 1.7;
    margin-bottom: 2.5rem;
    animation: fadeUp 0.6s 0.2s ease both;
  }
  .hero-actions {
    display: flex; gap: 1rem; flex-wrap: wrap;
    animation: fadeUp 0.6s 0.3s ease both;
  }
  .btn-primary {
    background: var(--gold); color: var(--navy);
    padding: 0.85rem 2rem; border-radius: 8px;
    font-weight: 700; font-size: 0.95rem; text-decoration: none;
    transition: all 0.2s; display: inline-block;
  }
  .btn-primary:hover { background: var(--gold-light); transform: translateY(-2px); box-shadow: 0 8px 24px rgba(245,197,24,0.35); }
  .btn-secondary {
    background: transparent; color: var(--warm-white);
    padding: 0.85rem 2rem; border-radius: 8px;
    font-weight: 600; font-size: 0.95rem; text-decoration: none;
    border: 1.5px solid rgba(255,255,255,0.3);
    transition: all 0.2s; display: inline-block;
  }
  .btn-secondary:hover { border-color: rgba(255,255,255,0.7); background: rgba(255,255,255,0.05); }

  /* HERO STATS CARD */
  .hero-visual {
    animation: fadeUp 0.6s 0.2s ease both;
  }
  .stats-grid {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }
  .stat-card {
    background: rgba(255,255,255,0.05);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 12px; padding: 1.5rem;
    transition: all 0.3s;
  }
  .stat-card:hover { background: rgba(255,255,255,0.08); transform: translateY(-3px); }
  .stat-card.gold { border-color: rgba(245,197,24,0.4); background: rgba(245,197,24,0.07); }
  .stat-number {
    font-family: 'Playfair Display', serif;
    font-size: 2.4rem; font-weight: 900;
    color: var(--warm-white); line-height: 1;
    margin-bottom: 0.4rem;
  }
  .stat-card.gold .stat-number { color: var(--gold); }
  .stat-label { color: rgba(255,255,255,0.5); font-size: 0.85rem; font-weight: 500; }

  /* SERVICES STRIP */
  .services-strip {
    background: var(--gold);
    padding: 1rem 5%;
    display: flex; align-items: center; justify-content: center;
    gap: 3rem; flex-wrap: wrap;
    overflow: hidden;
  }
  .strip-item {
    display: flex; align-items: center; gap: 0.6rem;
    color: var(--navy); font-weight: 700; font-size: 0.9rem;
    text-transform: uppercase; letter-spacing: 0.04em;
    white-space: nowrap;
  }
  .strip-item::before { content: '▶'; font-size: 0.6rem; }

  /* SECTIONS */
  section { padding: 6rem 5%; }
  .container { max-width: 1200px; margin: 0 auto; }
  .section-label {
    font-size: 0.75rem; font-weight: 700;
    text-transform: uppercase; letter-spacing: 0.12em;
    color: var(--gold); margin-bottom: 0.75rem;
  }
  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 3.5vw, 3rem);
    font-weight: 900; line-height: 1.1;
    color: var(--navy); letter-spacing: -0.02em;
    margin-bottom: 1rem;
  }
  .section-desc {
    color: var(--text-muted); font-size: 1.05rem; line-height: 1.7;
    max-width: 580px; margin-bottom: 3rem;
  }

  /* SERVICE CARDS */
  .services-grid {
    display: grid; grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem; margin-top: 3rem;
  }
  .service-card {
    background: var(--warm-white);
    border: 1.5px solid #e8e4d8;
    border-radius: 16px; padding: 2.2rem;
    transition: all 0.3s; position: relative; overflow: hidden;
  }
  .service-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 4px;
    background: var(--navy); transition: background 0.3s;
  }
  .service-card.gold-accent::before { background: var(--gold); }
  .service-card.blue-accent::before { background: var(--accent-blue); }
  .service-card.green-accent::before { background: var(--green); }
  .service-card:hover { transform: translateY(-6px); box-shadow: 0 20px 48px rgba(10,22,40,0.1); }
  .service-icon {
    width: 52px; height: 52px; border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.5rem; margin-bottom: 1.5rem;
    background: var(--cream);
  }
  .service-card h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.3rem; font-weight: 700; margin-bottom: 0.75rem;
    color: var(--navy);
  }
  .service-card p { color: var(--text-muted); line-height: 1.65; font-size: 0.95rem; margin-bottom: 1.2rem; }
  .service-tag {
    display: inline-block; background: var(--cream);
    color: var(--text-muted); font-size: 0.78rem;
    padding: 0.25rem 0.7rem; border-radius: 100px; font-weight: 600;
    margin: 0.2rem 0.2rem 0 0;
  }

  /* PRICING */
  #pricing { background: var(--navy); }
  #pricing .section-title { color: var(--warm-white); }
  #pricing .section-label { color: var(--gold); }
  #pricing .section-desc { color: rgba(255,255,255,0.55); }

  .pricing-tabs {
    display: flex; gap: 0.5rem; margin-bottom: 2.5rem;
    background: rgba(255,255,255,0.06);
    border: 1px solid rgba(255,255,255,0.12);
    border-radius: 10px; padding: 6px;
    width: fit-content;
  }
  .tab-btn {
    padding: 0.6rem 1.4rem; border-radius: 7px;
    border: none; background: transparent;
    color: rgba(255,255,255,0.55); font-family: 'DM Sans', sans-serif;
    font-size: 0.9rem; font-weight: 600; cursor: pointer;
    transition: all 0.2s;
  }
  .tab-btn.active { background: var(--gold); color: var(--navy); }

  .pricing-grid {
    display: grid; grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }
  .price-card {
    background: rgba(255,255,255,0.05);
    border: 1.5px solid rgba(255,255,255,0.12);
    border-radius: 16px; padding: 2.5rem;
    position: relative; transition: all 0.3s;
  }
  .price-card:hover { background: rgba(255,255,255,0.08); transform: translateY(-4px); }
  .price-card.featured {
    background: var(--gold);
    border-color: var(--gold);
  }
  .price-card.featured * { color: var(--navy) !important; }
  .featured-badge {
    position: absolute; top: -14px; left: 50%; transform: translateX(-50%);
    background: var(--navy); color: var(--warm-white) !important;
    font-size: 0.72rem; font-weight: 700; letter-spacing: 0.08em;
    text-transform: uppercase; padding: 0.3rem 1rem; border-radius: 100px;
  }
  .price-card h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.3rem; font-weight: 700; color: var(--warm-white);
    margin-bottom: 0.5rem;
  }
  .price-tag {
    margin: 1.5rem 0;
  }
  .price-amount {
    font-family: 'Playfair Display', serif;
    font-size: 3rem; font-weight: 900; color: var(--warm-white);
    line-height: 1;
  }
  .price-amount sup { font-size: 1.2rem; vertical-align: top; margin-top: 0.5rem; }
  .price-period { color: rgba(255,255,255,0.5); font-size: 0.9rem; font-weight: 500; }
  .price-desc { color: rgba(255,255,255,0.55); font-size: 0.88rem; line-height: 1.6; margin-bottom: 1.5rem; }
  .price-features { list-style: none; margin-bottom: 2rem; }
  .price-features li {
    color: rgba(255,255,255,0.75); font-size: 0.9rem; padding: 0.5rem 0;
    border-bottom: 1px solid rgba(255,255,255,0.08);
    display: flex; align-items: center; gap: 0.6rem;
  }
  .price-features li::before { content: '✓'; color: var(--gold); font-weight: 700; flex-shrink: 0; }
  .price-card.featured .price-features li { color: rgba(10,22,40,0.8); border-bottom-color: rgba(10,22,40,0.12); }
  .price-card.featured .price-features li::before { color: var(--navy); }
  .price-card.featured .price-period { color: rgba(10,22,40,0.6); }
  .price-card.featured .price-desc { color: rgba(10,22,40,0.6); }
  .btn-pricing {
    display: block; text-align: center; text-decoration: none;
    padding: 0.85rem; border-radius: 8px; font-weight: 700;
    font-size: 0.9rem; transition: all 0.2s;
    border: 2px solid rgba(255,255,255,0.25); color: var(--warm-white);
  }
  .btn-pricing:hover { background: rgba(255,255,255,0.1); border-color: rgba(255,255,255,0.5); }
  .price-card.featured .btn-pricing {
    background: var(--navy); border-color: var(--navy); color: var(--warm-white) !important;
  }
  .price-card.featured .btn-pricing:hover { background: var(--navy-mid); }

  .pricing-panels { }
  .pricing-panel { display: none; }
  .pricing-panel.active { display: block; }

  /* PROCESS */
  #process { background: var(--cream); }
  .process-steps {
    display: grid; grid-template-columns: repeat(4, 1fr);
    gap: 2rem; margin-top: 3rem;
    position: relative;
  }
  .process-steps::before {
    content: '';
    position: absolute; top: 28px; left: 8%; right: 8%;
    height: 2px; background: repeating-linear-gradient(90deg, var(--gold) 0, var(--gold) 8px, transparent 8px, transparent 16px);
    z-index: 0;
  }
  .process-step { text-align: center; position: relative; z-index: 1; }
  .step-num {
    width: 56px; height: 56px; border-radius: 50%;
    background: var(--navy); color: var(--gold);
    font-family: 'Playfair Display', serif; font-size: 1.3rem; font-weight: 900;
    display: flex; align-items: center; justify-content: center;
    margin: 0 auto 1.2rem;
    border: 3px solid var(--cream); box-shadow: 0 0 0 3px var(--navy);
  }
  .process-step h4 {
    font-family: 'Playfair Display', serif;
    font-size: 1rem; font-weight: 700; color: var(--navy); margin-bottom: 0.5rem;
  }
  .process-step p { color: var(--text-muted); font-size: 0.88rem; line-height: 1.6; }

  /* TESTIMONIALS */
  #testimonials { background: var(--warm-white); }
  .testimonials-grid {
    display: grid; grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem; margin-top: 3rem;
  }
  .testimonial {
    background: var(--cream);
    border-radius: 14px; padding: 2rem;
    border: 1.5px solid #e8e4d8;
    transition: transform 0.3s;
  }
  .testimonial:hover { transform: translateY(-4px); }
  .stars { color: var(--gold); font-size: 0.9rem; margin-bottom: 1rem; }
  .testimonial blockquote {
    font-size: 0.95rem; line-height: 1.7; color: var(--text-body);
    margin-bottom: 1.5rem; font-style: italic;
  }
  .testimonial-author { display: flex; align-items: center; gap: 0.75rem; }
  .author-avatar {
    width: 44px; height: 44px; border-radius: 50%;
    background: var(--navy); color: var(--gold);
    display: flex; align-items: center; justify-content: center;
    font-weight: 700; font-size: 1rem;
  }
  .author-name { font-weight: 700; font-size: 0.9rem; color: var(--navy); }
  .author-role { font-size: 0.8rem; color: var(--text-muted); }

  /* CTA */
  .cta-section {
    background: var(--navy);
    padding: 6rem 5%;
    text-align: center; position: relative; overflow: hidden;
  }
  .cta-section::before {
    content: '';
    position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%);
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(245,197,24,0.1) 0%, transparent 60%);
    pointer-events: none;
  }
  .cta-section .section-title { color: var(--warm-white); margin-bottom: 1rem; }
  .cta-section .section-desc { color: rgba(255,255,255,0.55); margin: 0 auto 2.5rem; }

  /* FOOTER */
  footer {
    background: #060f1e; padding: 3rem 5%;
    display: flex; align-items: center; justify-content: space-between;
    flex-wrap: wrap; gap: 1rem;
  }
  footer .nav-logo { font-size: 1.2rem; }
  footer p { color: rgba(255,255,255,0.35); font-size: 0.85rem; }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .reveal { opacity: 0; transform: translateY(30px); transition: all 0.7s ease; }
  .reveal.visible { opacity: 1; transform: none; }

  @media (max-width: 900px) {
    .hero-inner, .services-grid, .pricing-grid, .testimonials-grid { grid-template-columns: 1fr; }
    .process-steps { grid-template-columns: 1fr 1fr; }
    .process-steps::before { display: none; }
    .nav-links { display: none; }
    .stats-grid { display: none; }
  }
</style>
</head>
<body>

<nav>
  <div class="nav-logo">Edu<span>Media</span></div>
  <ul class="nav-links">
    <li><a href="#services">Services</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#process">Process</a></li>
    <li><a href="#testimonials">Results</a></li>
  </ul>
  <a href="https://calendly.com/joshua-mcclue/free-30-minute-strategy-call" target="_blank" class="nav-cta">Book a Free Call</a>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-inner">
    <div>
      <div class="hero-badge">Built exclusively for K–12 schools</div>
      <h1 class="hero-title">
        Your school's story,<br><em>told brilliantly.</em>
      </h1>
      <p class="hero-desc">
        EduMedia helps schools build vibrant, engaging social media presences — from scroll-stopping content and targeted ads to stunning photography and video. We handle everything so your staff can focus on what matters.
      </p>
      <div class="hero-actions">
        <a href="#pricing" class="btn-primary">See Pricing Plans</a>
        <a href="#services" class="btn-secondary">Explore Services</a>
      </div>
    </div>
    <div class="hero-visual">
      <div class="stats-grid">
        <div class="stat-card gold">
          <div class="stat-number">3.2×</div>
          <div class="stat-label">Avg. engagement increase</div>
        </div>
        <div class="stat-card">
          <div class="stat-number">∞</div>
          <div class="stat-label">Countless stories told</div>
        </div>
        <div class="stat-card">
          <div class="stat-number">94%</div>
          <div class="stat-label">Client retention rate</div>
        </div>
        <div class="stat-card gold">
          <div class="stat-number">48h</div>
          <div class="stat-label">Avg. onboarding time</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- STRIP -->
<div class="services-strip">
  <div class="strip-item">Social Media Management</div>
  <div class="strip-item">Paid Advertising</div>
  <div class="strip-item">Photography & Video</div>
  <div class="strip-item">AI Website Chat</div>
  <div class="strip-item">Bespoke Packages</div>
  <div class="strip-item">Analytics & Reporting</div>
</div>

<!-- SERVICES -->
<section id="services">
  <div class="container">
    <div class="section-label">What We Do</div>
    <h2 class="section-title">Three pillars of your school's digital presence</h2>
    <p class="section-desc">Every school is different. That's why we offer modular services you can mix, match, and scale as your needs evolve.</p>
    <div class="services-grid reveal">
      <div class="service-card gold-accent">
        <div class="service-icon">📣</div>
        <h3>Social Media Management</h3>
        <p>Full-service management of your school's social channels — strategy, content creation, scheduling, community engagement, and monthly performance reports.</p>
        <span class="service-tag">Instagram</span>
        <span class="service-tag">Facebook</span>
        <span class="service-tag">X/Twitter</span>
        <span class="service-tag">TikTok</span>
        <span class="service-tag">LinkedIn</span>
      </div>
      <div class="service-card blue-accent">
        <div class="service-icon">🎯</div>
        <h3>Paid Advertising</h3>
        <p>Strategic, data-driven ad campaigns targeting prospective families in your catchment area — boosting enrollment inquiries, open day attendance, and brand awareness.</p>
        <span class="service-tag">Meta Ads</span>
        <span class="service-tag">Google Ads</span>
        <span class="service-tag">Geo-targeting</span>
        <span class="service-tag">Retargeting</span>
      </div>
      <div class="service-card green-accent">
        <div class="service-icon">📸</div>
        <h3>Photography & Video</h3>
        <p>Professional on-site visits capturing your school's culture, events, student life, and facilities — delivered as a library of ready-to-use social assets.</p>
        <span class="service-tag">Event Coverage</span>
        <span class="service-tag">Reels & Shorts</span>
        <span class="service-tag">Staff Portraits</span>
        <span class="service-tag">Drone Aerial</span>
      </div>
    </div>
  </div>
</section>

<!-- PRICING -->
<section id="pricing">
  <div class="container">
    <div class="section-label">Transparent Pricing</div>
    <h2 class="section-title">Simple plans. No surprises.</h2>
    <p class="section-desc">All plans are month-to-month with no lock-in contracts. School-year billing discounts available.</p>

    <div class="pricing-tabs">
      <button class="tab-btn active" onclick="showTab('social')">Social Media</button>
      <button class="tab-btn" onclick="showTab('ads')">Paid Ads</button>
      <button class="tab-btn" onclick="showTab('photo')">Photo & Video</button>
      <button class="tab-btn" onclick="showTab('bespoke')">Bespoke Package</button>
    </div>

    <div class="pricing-panels">

      <!-- SOCIAL MEDIA -->
      <div class="pricing-panel active" id="tab-social">
        <div class="pricing-grid">
          <div class="price-card">
            <h3>Starter</h3>
            <p class="price-desc">Perfect for smaller schools just getting started with social media.</p>
            <div class="price-tag">
              <div class="price-amount"><sup>$</sup>399</div>
              <div class="price-period">/ month</div>
            </div>
            <ul class="price-features">
              <li>2 platforms (e.g. Facebook + Instagram)</li>
              <li>12 posts per month</li>
              <li>Monthly strategy call</li>
              <li>Basic analytics report</li>
              <li>Community management (M–F)</li>
              <li>Canva-based graphics</li>
            </ul>
            <a href="#" class="btn-pricing">Get Started</a>
          </div>
          <div class="price-card featured">
            <div class="featured-badge">Most Popular</div>
            <h3>Growth</h3>
            <p class="price-desc">Our most popular plan for schools serious about community engagement.</p>
            <div class="price-tag">
              <div class="price-amount"><sup>$</sup>899</div>
              <div class="price-period">/ month</div>
            </div>
            <ul class="price-features">
              <li>4 platforms including TikTok</li>
              <li>24 posts per month</li>
              <li>Bi-weekly strategy calls</li>
              <li>Full analytics dashboard</li>
              <li>Community management (7 days)</li>
              <li>Custom branded graphics</li>
              <li>1 Reel/Short per month included</li>
              <li>Competitor benchmarking</li>
            </ul>
            <a href="#" class="btn-pricing">Get Started</a>
          </div>
          <div class="price-card">
            <h3>Premium</h3>
            <p class="price-desc">Full-service management for flagship schools and multi-campus groups.</p>
            <div class="price-tag">
              <div class="price-amount"><sup>$</sup>1,699</div>
              <div class="price-period">/ month</div>
            </div>
            <ul class="price-features">
              <li>All platforms + LinkedIn</li>
              <li>Unlimited posts</li>
              <li>Dedicated account manager</li>
              <li>Weekly reporting & calls</li>
              <li>24/7 community management</li>
              <li>4 Reels/Shorts per month</li>
              <li>Crisis communications support</li>
              <li>Multi-campus management</li>
            </ul>
            <a href="#" class="btn-pricing">Get Started</a>
          </div>
        </div>
      </div>

      <!-- PAID ADS -->
      <div class="pricing-panel" id="tab-ads">
        <div class="pricing-grid">
          <div class="price-card">
            <h3>Launch</h3>
            <p class="price-desc">Get your first enrollment-focused campaigns live quickly.</p>
            <div class="price-tag">
              <div class="price-amount"><sup>$</sup>499</div>
              <div class="price-period">/ month + ad spend</div>
            </div>
            <ul class="price-features">
              <li>Up to $1,500/mo ad spend managed</li>
              <li>1 campaign (Meta or Google)</li>
              <li>Audience research & setup</li>
              <li>3 ad creatives</li>
              <li>Monthly performance report</li>
              <li>Enrollment inquiry tracking</li>
            </ul>
            <a href="#" class="btn-pricing">Get Started</a>
          </div>
          <div class="price-card featured">
            <div class="featured-badge">Best Value</div>
            <h3>Accelerate</h3>
            <p class="price-desc">Multi-channel campaigns for schools with serious enrollment goals.</p>
            <div class="price-tag">
              <div class="price-amount"><sup>$</sup>999</div>
              <div class="price-period">/ month + ad spend</div>
            </div>
            <ul class="price-features">
              <li>Up to $5,000/mo ad spend managed</li>
              <li>Meta + Google campaigns</li>
              <li>Geo-targeting & radius ads</li>
              <li>8 ad creatives + A/B testing</li>
              <li>Weekly optimization & reporting</li>
              <li>Retargeting audiences</li>
              <li>Landing page recommendations</li>
            </ul>
            <a href="#" class="btn-pricing">Get Started</a>
          </div>
          <div class="price-card">
            <h3>Dominate</h3>
            <p class="price-desc">Maximum reach for private schools and growing school groups.</p>
            <div class="price-tag">
              <div class="price-amount"><sup>$</sup>1,599</div>
              <div class="price-period">/ month + ad spend</div>
            </div>
            <ul class="price-features">
              <li>Unlimited ad spend managed</li>
              <li>All channels + YouTube</li>
              <li>Custom audience modelling</li>
              <li>Unlimited creatives</li>
              <li>Real-time reporting dashboard</li>
              <li>Full funnel strategy</li>
              <li>Dedicated paid media specialist</li>
            </ul>
            <a href="#" class="btn-pricing">Get Started</a>
          </div>
        </div>
      </div>

      <!-- PHOTO & VIDEO -->
      <div class="pricing-panel" id="tab-photo">
        <div class="pricing-grid">
          <div class="price-card">
            <h3>Essentials</h3>
            <p class="price-desc">A single professional visit to build your core content library.</p>
            <div class="price-tag">
              <div class="price-amount"><sup>$</sup>799</div>
              <div class="price-period">one-time</div>
            </div>
            <ul class="price-features">
              <li>Half-day on-site shoot (3–4 hrs)</li>
              <li>50+ edited photos delivered</li>
              <li>2 short-form video clips (60 sec)</li>
              <li>Social-optimised crop variants</li>
              <li>Online gallery delivery</li>
              <li>14-day turnaround</li>
            </ul>
            <a href="#" class="btn-pricing">Book Now</a>
          </div>
          <div class="price-card featured">
            <div class="featured-badge">Most Popular</div>
            <h3>Showcase</h3>
            <p class="price-desc">Regular content creation that keeps your channels looking fresh all year.</p>
            <div class="price-tag">
              <div class="price-amount"><sup>$</sup>1,499</div>
              <div class="price-period">× 3 per year <span style="display:block;font-size:0.8rem;opacity:0.7;">($3,999 upfront)</span></div>
            </div>
            <ul class="price-features">
              <li>Full-day shoot per term</li>
              <li>150+ edited photos per visit</li>
              <li>6 Reels/Short-form videos</li>
              <li>1 long-form brand video (2–3 min)</li>
              <li>Drone aerial footage</li>
              <li>Priority 7-day turnaround</li>
              <li>Licensed music & captions</li>
            </ul>
            <a href="#" class="btn-pricing">Book Now</a>
          </div>
          <div class="price-card">
            <h3>Flagship</h3>
            <p class="price-desc">Complete visual storytelling package for schools that demand the best.</p>
            <div class="price-tag">
              <div class="price-amount"><sup>$</sup>6,999</div>
              <div class="price-period">/ year</div>
            </div>
            <ul class="price-features">
              <li>Monthly on-site visits</li>
              <li>Unlimited edited photos</li>
              <li>Monthly Reels + highlight packages</li>
              <li>Annual school brand video</li>
              <li>Event & sports coverage</li>
              <li>Staff & leadership portraits</li>
              <li>48-hr rush delivery available</li>
            </ul>
            <a href="#" class="btn-pricing">Book Now</a>
          </div>
        </div>
      </div>

      <!-- BESPOKE -->
      <div class="pricing-panel" id="tab-bespoke">
        <div style="background: rgba(255,255,255,0.05); border: 1.5px solid rgba(245,197,24,0.3); border-radius: 20px; padding: 3.5rem; text-align: center; max-width: 780px; margin: 0 auto;">
          <div style="display:inline-flex;align-items:center;gap:0.5rem;background:rgba(245,197,24,0.15);border:1px solid rgba(245,197,24,0.4);color:var(--gold);padding:0.4rem 1rem;border-radius:100px;font-size:0.78rem;font-weight:700;letter-spacing:0.08em;text-transform:uppercase;margin-bottom:1.5rem;">✦ Fully Custom</div>
          <h3 style="font-family:'Playfair Display',serif;font-size:2.2rem;font-weight:900;color:var(--warm-white);margin-bottom:1rem;">Bespoke Package</h3>
          <p style="color:rgba(255,255,255,0.6);font-size:1.05rem;line-height:1.7;margin-bottom:2.5rem;max-width:560px;margin-left:auto;margin-right:auto;">No two schools are the same. Our bespoke package combines any mix of our services into a single tailored solution — designed around your goals, your budget, and your community.</p>
          <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:1rem;margin-bottom:2.5rem;text-align:left;">
            <div style="background:rgba(255,255,255,0.06);border-radius:12px;padding:1.2rem;">
              <div style="font-size:1.4rem;margin-bottom:0.5rem;">📣</div>
              <div style="color:var(--warm-white);font-weight:600;font-size:0.9rem;margin-bottom:0.3rem;">Social Media</div>
              <div style="color:rgba(255,255,255,0.45);font-size:0.82rem;">Custom platform mix & posting schedule</div>
            </div>
            <div style="background:rgba(255,255,255,0.06);border-radius:12px;padding:1.2rem;">
              <div style="font-size:1.4rem;margin-bottom:0.5rem;">🎯</div>
              <div style="color:var(--warm-white);font-weight:600;font-size:0.9rem;margin-bottom:0.3rem;">Paid Advertising</div>
              <div style="color:rgba(255,255,255,0.45);font-size:0.82rem;">Targeted campaigns across all channels</div>
            </div>
            <div style="background:rgba(255,255,255,0.06);border-radius:12px;padding:1.2rem;">
              <div style="font-size:1.4rem;margin-bottom:0.5rem;">📸</div>
              <div style="color:var(--warm-white);font-weight:600;font-size:0.9rem;margin-bottom:0.3rem;">Photo & Video</div>
              <div style="color:rgba(255,255,255,0.45);font-size:0.82rem;">On-site shoots tailored to your calendar</div>
            </div>
            <div style="background:rgba(255,255,255,0.06);border-radius:12px;padding:1.2rem;">
              <div style="font-size:1.4rem;margin-bottom:0.5rem;">🤖</div>
              <div style="color:var(--warm-white);font-weight:600;font-size:0.9rem;margin-bottom:0.3rem;">AI Website Chat</div>
              <div style="color:rgba(255,255,255,0.45);font-size:0.82rem;">Smart chatbot for prospective family enquiries</div>
            </div>
            <div style="background:rgba(255,255,255,0.06);border-radius:12px;padding:1.2rem;">
              <div style="font-size:1.4rem;margin-bottom:0.5rem;">📊</div>
              <div style="color:var(--warm-white);font-weight:600;font-size:0.9rem;margin-bottom:0.3rem;">Advanced Analytics</div>
              <div style="color:rgba(255,255,255,0.45);font-size:0.82rem;">Custom dashboards & enrolment tracking</div>
            </div>
            <div style="background:rgba(255,255,255,0.06);border-radius:12px;padding:1.2rem;">
              <div style="font-size:1.4rem;margin-bottom:0.5rem;">🎨</div>
              <div style="color:var(--warm-white);font-weight:600;font-size:0.9rem;margin-bottom:0.3rem;">Brand Strategy</div>
              <div style="color:rgba(255,255,255,0.45);font-size:0.82rem;">Visual identity & tone-of-voice guidelines</div>
            </div>
          </div>
          <div style="background:rgba(245,197,24,0.1);border:1px solid rgba(245,197,24,0.25);border-radius:12px;padding:1.5rem;margin-bottom:2rem;">
            <div style="font-family:'Playfair Display',serif;font-size:2rem;font-weight:900;color:var(--gold);">Price on Request</div>
            <div style="color:rgba(255,255,255,0.5);font-size:0.9rem;margin-top:0.3rem;">Custom quotes delivered within 24 hours</div>
          </div>
          <a href="https://calendly.com/joshua-mcclue/free-30-minute-strategy-call" target="_blank" style="display:inline-block;background:var(--gold);color:var(--navy);padding:0.9rem 2.5rem;border-radius:8px;font-weight:700;font-size:0.95rem;text-decoration:none;transition:all 0.2s;">Book a Free Consultation</a>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- PROCESS -->
<section id="process">
  <div class="container">
    <div class="section-label">How It Works</div>
    <h2 class="section-title">Up and running in days, not weeks</h2>
    <p class="section-desc">We've streamlined onboarding so your school sees results fast — with zero disruption to your staff.</p>
    <div class="process-steps reveal">
      <div class="process-step">
        <div class="step-num">1</div>
        <h4>Discovery Call</h4>
        <p>We learn about your school's goals, brand voice, and target audience in a 30-min session.</p>
      </div>
      <div class="process-step">
        <div class="step-num">2</div>
        <h4>Strategy & Setup</h4>
        <p>We build a tailored content strategy, set up tools, and prepare your first content calendar.</p>
      </div>
      <div class="process-step">
        <div class="step-num">3</div>
        <h4>Approval & Launch</h4>
        <p>You review and approve content before anything goes live — always in the loop, never overwhelmed.</p>
      </div>
      <div class="process-step">
        <div class="step-num">4</div>
        <h4>Grow & Optimise</h4>
        <p>We monitor, report, and continuously improve performance every single month.</p>
      </div>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section id="testimonials">
  <div class="container">
    <div class="section-label">Real Results</div>
    <h2 class="section-title">What school leaders are saying</h2>
    <div style="text-align:center; padding: 4rem 2rem; background: var(--warm-white); border-radius: 20px; border: 1.5px solid #e8e4d8; margin-top: 2rem;">
      <div style="font-size: 3rem; margin-bottom: 1rem;">⭐</div>
      <h3 style="font-family: 'Playfair Display', serif; font-size: 1.8rem; color: var(--navy); margin-bottom: 0.75rem;">Reviews Coming Soon</h3>
      <p style="color: var(--text-muted); font-size: 1rem; max-width: 440px; margin: 0 auto 2rem;">We're just getting started — and we can't wait to share what our first school partners have to say.</p>
      <a href="https://calendly.com/joshua-mcclue/free-30-minute-strategy-call" target="_blank" class="btn-primary">Be Our First Success Story</a>
    </div>
  </div>
</section>

<!-- CTA -->
<div class="cta-section">
  <div class="container">
    <div class="section-label" style="color: var(--gold);">Get Started Today</div>
    <h2 class="section-title">Ready to tell your school's story?</h2>
    <p class="section-desc">Book a free 30-minute strategy session. No commitment, no pushy sales — just honest advice on what will move the needle for your school.</p>
    <a href="https://calendly.com/joshua-mcclue/free-30-minute-strategy-call" target="_blank" class="btn-primary" style="font-size: 1rem; padding: 1rem 2.5rem;">Book Your Free Strategy Call</a>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <div class="nav-logo">Edu<span>Media</span></div>
  <p>© 2025 EduMedia. Social media management for K–12 schools.</p>
  <p style="color: rgba(255,255,255,0.25);">Privacy Policy · Terms of Service</p>
</footer>

<script>
  // Pricing tabs
  function showTab(tab) {
    document.querySelectorAll('.pricing-panel').forEach(p => p.classList.remove('active'));
    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    document.getElementById('tab-' + tab).classList.add('active');
    event.target.classList.add('active');
  }

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries) => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); }});
  }, { threshold: 0.1 });
  reveals.forEach(r => io.observe(r));
</script>
</body>
</html>
