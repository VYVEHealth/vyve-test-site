const fs = require('fs');
const path = require('path');
const OUT = '/sessions/vigilant-happy-johnson/vyve-site';

// ── Shared components ─────────────────────────────────────────────────────
const HEAD = (title, desc) => `<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>${title} — VYVE Health</title>
<meta name="description" content="${desc}">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Playfair+Display:ital,wght@0,600;0,700;1,600&display=swap" rel="stylesheet">
<link rel="stylesheet" href="styles.css">
</head>
<body>`;

const NAV = (active) => `
<nav class="nav" id="nav">
  <div class="nav__inner">
    <a href="index.html" class="nav__logo">
      <div class="nav__logo-mark">
        <svg viewBox="0 0 24 24"><path d="M12 2L4 7v10l8 5 8-5V7L12 2z"/><path d="M12 12l-4-2.5M12 12l4-2.5M12 12v5" stroke-linecap="round"/></svg>
      </div>
      <span class="nav__logo-text">VYVE<span> Health</span></span>
    </a>
    <div class="nav__links">
      <a href="index.html" class="nav__link${active==='home'?' active':''}">Home</a>
      <a href="employers.html" class="nav__link employer${active==='employers'?' active':''}">For Employers</a>
      <a href="individuals.html" class="nav__link individual${active==='individuals'?' active':''}">For Individuals</a>
      <a href="science.html" class="nav__link${active==='science'?' active':''}">Our Science</a>
      <a href="about.html" class="nav__link${active==='about'?' active':''}">About</a>
    </div>
    <a href="employers.html#demo" class="btn btn--primary nav__cta">Book a Demo</a>
    <button class="nav__mobile-btn" onclick="document.getElementById('nav').classList.toggle('open')" aria-label="Menu">
      <svg viewBox="0 0 24 24"><line x1="3" y1="6" x2="21" y2="6"/><line x1="3" y1="12" x2="21" y2="12"/><line x1="3" y1="18" x2="21" y2="18"/></svg>
    </button>
  </div>
</nav>`;

const FOOTER = () => `
<footer class="footer">
  <div class="container">
    <div class="footer__grid">
      <div class="footer__brand">
        <a href="index.html" class="nav__logo">
          <div class="nav__logo-mark" style="background:#1B7878">
            <svg viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2"><path d="M12 2L4 7v10l8 5 8-5V7L12 2z"/></svg>
          </div>
          <span class="nav__logo-text" style="color:white">VYVE<span> Health</span></span>
        </a>
        <p class="footer__tagline" style="margin-top:16px">The UK's most complete proactive wellbeing platform — built for organisations, designed for people.</p>
        <p class="footer__tagline" style="margin-top:12px;font-size:0.8rem">Every step you take makes someone's life better.</p>
      </div>
      <div>
        <p class="footer__col-title">For Employers</p>
        <ul class="footer__links">
          <li><a href="employers.html">Overview</a></li>
          <li><a href="employers.html#promise">Enterprise Promise</a></li>
          <li><a href="employers.html#roi">ROI Model</a></li>
          <li><a href="employers.html#ecosystem">Ecosystem</a></li>
          <li><a href="employers.html#demo">Book a Demo</a></li>
        </ul>
      </div>
      <div>
        <p class="footer__col-title">For Individuals</p>
        <ul class="footer__links">
          <li><a href="individuals.html">Overview</a></li>
          <li><a href="individuals.html#personas">Your Persona</a></li>
          <li><a href="individuals.html#community">Community</a></li>
          <li><a href="individuals.html#pillars">10 Pillars</a></li>
          <li><a href="individuals.html#charity">Social Mission</a></li>
        </ul>
      </div>
      <div>
        <p class="footer__col-title">Company</p>
        <ul class="footer__links">
          <li><a href="science.html">Our Science</a></li>
          <li><a href="about.html">About VYVE</a></li>
          <li><a href="about.html#roadmap">Roadmap</a></li>
          <li><a href="mailto:hello@vyvehealth.co.uk">Contact Us</a></li>
          <li><a href="#">Privacy Policy</a></li>
        </ul>
      </div>
    </div>
    <div class="footer__bottom">
      <span class="footer__copy">© 2026 VYVE Health. All rights reserved. Registered in England & Wales.</span>
      <div class="footer__certifications">
        <span class="footer__cert">GDPR Compliant</span>
        <span class="footer__cert">ISO 27001 (Target)</span>
        <span class="footer__cert">CIPD Partner</span>
      </div>
    </div>
  </div>
</footer>
<script>
// Fade-up animations
const obs = new IntersectionObserver((entries) => {
  entries.forEach(e => { if(e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.1 });
document.querySelectorAll('.fade-up, .fade-in').forEach(el => obs.observe(el));

// Count-up animation
function countUp(el) {
  const target = parseFloat(el.dataset.target);
  const prefix = el.dataset.prefix || '';
  const suffix = el.dataset.suffix || '';
  const duration = 1800;
  const steps = 60;
  let count = 0;
  const inc = target / steps;
  const timer = setInterval(() => {
    count = Math.min(count + inc, target);
    el.textContent = prefix + (Number.isInteger(target) ? Math.round(count) : count.toFixed(1)) + suffix;
    if(count >= target) clearInterval(timer);
  }, duration / steps);
}
const cObs = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if(e.isIntersecting) { countUp(e.target); cObs.unobserve(e.target); }
  });
}, { threshold: 0.5 });
document.querySelectorAll('[data-target]').forEach(el => cObs.observe(el));
</script>
</body></html>`;

// ══════════════════════════════════════════════════════════════════════════
// PAGE 1: HOME
// ══════════════════════════════════════════════════════════════════════════
const HOME = HEAD('Proactive Wellbeing Platform', 'VYVE Health — The UK\'s most complete proactive wellbeing platform for employers and individuals.') + NAV('home') + `

<!-- HERO -->
<section class="hero hero--home" style="padding:120px 0 100px">
  <div class="container">
    <div class="hero__grid">
      <div>
        <span class="label fade-up" style="display:block;margin-bottom:20px">The Proactive Wellbeing Revolution</span>
        <h1 class="display fade-up" style="color:white;margin-bottom:24px">Good health<br>shouldn't be<br>reactive.</h1>
        <p class="lead fade-up" style="color:rgba(255,255,255,0.8);margin-bottom:36px;max-width:520px">VYVE Health is the UK's most complete employee wellbeing platform — combining AI-powered personalisation, clinical expertise, and community to make proactive health the default for every working person.</p>
        <div class="hero__btns fade-up">
          <a href="employers.html" class="btn btn--white btn--lg">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="3" width="20" height="14" rx="2"/><path d="M8 21h8M12 17v4"/></svg>
            For Employers
          </a>
          <a href="individuals.html" class="btn btn--outline btn--lg" style="border-color:rgba(255,255,255,0.5);color:white">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="8" r="4"/><path d="M4 20c0-4 3.6-7 8-7s8 3 8 7"/></svg>
            For Individuals
          </a>
        </div>
      </div>
      <div class="hero__image fade-in">
        <img src="images/hero.jpg" alt="VYVE Health — proactive wellbeing" loading="eager"/>
      </div>
    </div>
  </div>
</section>

<!-- STAT STRIP -->
<div class="stat-strip">
  <div class="container">
    <div class="stat-strip__inner">
      <div class="stat-item">
        <div class="stat-item__value"><span data-target="148.9" data-suffix="m">148.9m</span></div>
        <div class="stat-item__label">Working days lost to sickness</div>
        <div class="stat-item__source">ONS 2024</div>
      </div>
      <div class="stat-item">
        <div class="stat-item__value"><span data-target="51" data-prefix="£" data-suffix="bn">£51bn</span></div>
        <div class="stat-item__label">Cost to UK employers per year</div>
        <div class="stat-item__source">Deloitte 2024</div>
      </div>
      <div class="stat-item">
        <div class="stat-item__value" style="color:#FFD700"><span data-target="4.7" data-prefix="£">£4.7</span></div>
        <div class="stat-item__label">Returned per £1 invested in mental health</div>
        <div class="stat-item__source">Deloitte 2024</div>
      </div>
      <div class="stat-item">
        <div class="stat-item__value"><span data-target="9.4">9.4</span></div>
        <div class="stat-item__label">Days absence per employee per year</div>
        <div class="stat-item__source">CIPD 2025 — 12-year record</div>
      </div>
      <div class="stat-item">
        <div class="stat-item__value"><span data-target="37" data-suffix="%">37%</span></div>
        <div class="stat-item__label">Of employers are purely reactive</div>
        <div class="stat-item__source">CIPD 2025</div>
      </div>
    </div>
  </div>
</div>

<!-- TWO PATHS -->
<section class="section">
  <div class="container">
    <div class="section__header">
      <span class="label">Who We Serve</span>
      <h2 class="headline">A platform built for two audiences.<br>One shared mission.</h2>
      <p class="lead">Whether you're an HR leader trying to reduce absence and prove ROI, or an individual looking to take control of your health — VYVE has a home for you.</p>
    </div>
    <div class="cards cards--2" style="gap:32px">
      <div class="card" style="border-left:4px solid var(--teal);padding:40px">
        <div class="card__label">For Employers & HR Leaders</div>
        <h3 class="card__title" style="font-size:1.6rem">Transform your workforce wellbeing. Prove it with data.</h3>
        <p class="card__body" style="margin-bottom:24px">CIPD data shows 37% of employers have no proactive wellbeing strategy. VYVE gives you the platform, the data, and the evidence to change that — with measurable ROI from month one.</p>
        <ul class="check-list" style="margin-bottom:28px">
          <li>Reduce absence with proactive, preventative support</li>
          <li>Real-time employer dashboard and ROI reporting</li>
          <li>The 6 VYVE Enterprise Promises — measurable outcomes</li>
          <li>Works for 50 or 50,000 employees</li>
        </ul>
        <a href="employers.html" class="btn btn--primary">Explore for Employers →</a>
      </div>
      <div class="card" style="border-left:4px solid var(--teal-lt);padding:40px">
        <div class="card__label">For Individuals</div>
        <h3 class="card__title" style="font-size:1.6rem">Your wellbeing, personalised. Your community, waiting.</h3>
        <p class="card__body" style="margin-bottom:24px">Most wellbeing apps are generic. VYVE learns who you are — your stressors, your goals, your life stage — and builds a personalised health journey that actually sticks, supported by community and real experts.</p>
        <ul class="check-list" style="margin-bottom:28px">
          <li>AI-powered personalised wellbeing journey (PAD)</li>
          <li>5 expert mental health pathways to match your needs</li>
          <li>Community sub-groups for shared goals</li>
          <li>Every activity supports a charity you choose</li>
        </ul>
        <a href="individuals.html" class="btn btn--outline">Explore for Individuals →</a>
      </div>
    </div>
  </div>
</section>

<!-- THE PROBLEM -->
<section class="section section--light">
  <div class="container">
    <div class="two-col">
      <div>
        <span class="label">The Problem We're Solving</span>
        <h2 class="subhead" style="color:var(--dark);margin-bottom:16px">Organisations are trying. Most are failing.</h2>
        <p class="lead" style="margin-bottom:20px">UK employers spend millions on wellbeing benefits that barely move the needle. EAPs with 3–6% utilisation. Gym memberships employees forget. One-off workshops that change nothing.</p>
        <p style="color:var(--grey);font-size:0.95rem;line-height:1.75;margin-bottom:24px">The CIPD's 2025 report found that while most organisations have wellbeing programmes, only 51% evaluate their effectiveness, and just 29% train line managers to support mental health. The result: 148.9 million working days lost to sickness in 2024 alone (ONS).</p>
        <p style="color:var(--grey);font-size:0.95rem;line-height:1.75;margin-bottom:28px">Deloitte (2024) estimates poor mental health costs UK employers £51 billion annually — £24 billion of that from presenteeism: employees showing up but unable to function. This is a systemic failure that demands a systemic solution.</p>
        <a href="science.html" class="btn btn--outline">See the Evidence →</a>
      </div>
      <div class="two-col__image">
        <img src="images/problem.jpg" alt="The workplace wellbeing problem" loading="lazy"/>
      </div>
    </div>
  </div>
</section>

<!-- VYVE DIFFERENCE -->
<section class="section">
  <div class="container">
    <div class="section__header">
      <span class="label">The VYVE Difference</span>
      <h2 class="headline">Proactive. Personalised. Proven.</h2>
      <p class="lead">We don't just treat the symptoms. We build the conditions where people thrive.</p>
    </div>
    <div class="cards cards--3" style="gap:24px">
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M12 2L2 7l10 5 10-5-10-5z"/><path d="M2 17l10 5 10-5"/><path d="M2 12l10 5 10-5"/></svg></div>
        <div class="card__label">Intelligence</div>
        <h3 class="card__title">PAD — Your Personal AI Director</h3>
        <p class="card__body">Our AI engine learns your patterns, predicts your needs, and personalises your entire wellbeing experience. Not a chatbot. Not a quiz. A genuine AI coach that evolves with you.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg></div>
        <div class="card__label">Community</div>
        <h3 class="card__title">Sub-Groups, Challenges & Shared Goals</h3>
        <p class="card__body">Group-based wellbeing shows 26% higher adherence than solo programmes. VYVE's community layer — sub-groups, challenges, leaderboards — makes health a shared experience, not a solo struggle.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M22 12h-4l-3 9L9 3l-3 9H2"/></svg></div>
        <div class="card__label">Evidence</div>
        <h3 class="card__title">Data-Driven from Day One</h3>
        <p class="card__body">Employers get a real-time dashboard showing absence patterns, engagement levels, and ROI. Every VYVE feature is grounded in peer-reviewed research and CIPD, Deloitte, and ONS data.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M4.5 6.375a4.125 4.125 0 1 0 8.25 0 4.125 4.125 0 0 0-8.25 0zm9.75 0a4.125 4.125 0 1 0 8.25 0 4.125 4.125 0 0 0-8.25 0zM4.5 18.75a4.125 4.125 0 1 0 8.25 0 4.125 4.125 0 0 0-8.25 0zm9.75 0a4.125 4.125 0 1 0 8.25 0 4.125 4.125 0 0 0-8.25 0z"/></svg></div>
        <div class="card__label">Holistic</div>
        <h3 class="card__title">10 Pillars Across the Whole Person</h3>
        <p class="card__body">Mental health, physical health, financial wellbeing, sleep, social connection, therapy, retreats, education — VYVE addresses every dimension of health, not just the ones that show up on a sick note.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M12 22s-8-4.5-8-11.8A8 8 0 0 1 12 2a8 8 0 0 1 8 8.2c0 7.3-8 11.8-8 11.8z"/></svg></div>
        <div class="card__label">Purpose</div>
        <h3 class="card__title">Every Step Supports a Charity</h3>
        <p class="card__body">Our charity mechanic means employee activity automatically generates charitable donations. Behavioural science confirms: prosocial motivation dramatically increases long-term engagement and programme completion.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z"/></svg></div>
        <div class="card__label">Expertise</div>
        <h3 class="card__title">Clinically Informed, Expertly Delivered</h3>
        <p class="card__body">VYVE's 5 AI-guided mental health personas are built on evidence-based therapeutic frameworks. Every programme is clinically reviewed. Our ambassador network brings world-class practitioners directly to your workforce.</p>
      </div>
    </div>
  </div>
</section>

<!-- SOCIAL MISSION -->
<section class="section section--dark">
  <div class="container">
    <div class="two-col" style="gap:60px">
      <div>
        <span class="label" style="color:var(--teal-lt)">Our Social Mission</span>
        <h2 class="subhead" style="color:white;margin-bottom:18px">Health with purpose.<br>Every step counts.</h2>
        <p style="color:var(--teal-md);font-size:0.95rem;line-height:1.75;margin-bottom:20px">VYVE's charity mechanic is built into the platform DNA. Employee activity — workouts, mindfulness sessions, challenges completed — automatically generates micro-donations to charities chosen by your workforce.</p>
        <p style="color:var(--teal-md);font-size:0.95rem;line-height:1.75;margin-bottom:28px">Behavioural research (Grant & Berry, 2011; Batson, 2011) confirms that combining self-improvement with prosocial purpose creates significantly stronger motivation and persistence than either motivation alone. This isn't just a feel-good feature — it's a clinically informed engagement mechanic.</p>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:16px">
          <div style="background:rgba(255,255,255,0.06);border-radius:10px;padding:20px;text-align:center">
            <div style="font-size:1.8rem;font-weight:700;color:var(--teal-lt)">£1m+</div>
            <div style="font-size:0.82rem;color:var(--teal-md);margin-top:4px">Annual giving target at scale</div>
          </div>
          <div style="background:rgba(255,255,255,0.06);border-radius:10px;padding:20px;text-align:center">
            <div style="font-size:1.8rem;font-weight:700;color:var(--teal-lt)">2.3x</div>
            <div style="font-size:0.82rem;color:var(--teal-md);margin-top:4px">Higher programme completion with prosocial goals</div>
          </div>
        </div>
      </div>
      <div class="two-col__image">
        <img src="images/charity.jpg" alt="VYVE charity mission" loading="lazy"/>
      </div>
    </div>
  </div>
</section>

<!-- QUICK EVIDENCE -->
<section class="section section--light">
  <div class="container">
    <div class="section__header">
      <span class="label">Built on Evidence</span>
      <h2 class="headline">Not a hunch. A body of proof.</h2>
      <p class="lead">Every aspect of VYVE is grounded in independent, peer-reviewed research and the most current UK workplace data available.</p>
    </div>
    <div class="evidence-grid">
      <div class="evidence-card fade-up"><div class="evidence-card__source">Deloitte — 2024</div><div class="evidence-card__stat">£4.70</div><div class="evidence-card__desc">Returned for every £1 invested in mental health at work — rising to £5.30 for proactive, universal interventions like VYVE.</div></div>
      <div class="evidence-card fade-up"><div class="evidence-card__source">ONS — 2024</div><div class="evidence-card__stat">148.9m</div><div class="evidence-card__desc">Working days lost to sickness in 2024. Long-term sickness now represents 32.2% of all economic inactivity in the UK.</div></div>
      <div class="evidence-card fade-up"><div class="evidence-card__source">CIPD — 2025</div><div class="evidence-card__stat">9.4 days</div><div class="evidence-card__desc">Average sickness absence per employee — the highest recorded in 12 years. Mental ill-health is the single biggest cause.</div></div>
      <div class="evidence-card fade-up"><div class="evidence-card__source">McKinsey Health Institute — 2023</div><div class="evidence-card__stat">4x</div><div class="evidence-card__desc">Higher long-term engagement on digital health platforms with community features vs solo-use apps.</div></div>
      <div class="evidence-card fade-up"><div class="evidence-card__source">Sport & Exercise Psychology — 2023</div><div class="evidence-card__stat">26%</div><div class="evidence-card__desc">Higher adherence to physical activity programmes when conducted in groups vs individually.</div></div>
      <div class="evidence-card fade-up"><div class="evidence-card__source">BetterUp — 2024</div><div class="evidence-card__stat">2.3x</div><div class="evidence-card__desc">More likely to complete a wellness programme when goals are set within a community or prosocial context.</div></div>
    </div>
    <div style="text-align:center;margin-top:40px">
      <a href="science.html" class="btn btn--outline">Read the Full Evidence Base →</a>
    </div>
  </div>
</section>

<!-- CTA -->
<section class="cta-section">
  <div class="container">
    <span class="label" style="display:block;margin-bottom:16px">Ready to transform wellbeing?</span>
    <h2 class="display" style="color:white;margin-bottom:20px">Join the movement.</h2>
    <p class="lead" style="color:var(--teal-md);margin-bottom:40px;max-width:560px;margin-left:auto;margin-right:auto">Whether you're an HR leader with 50 employees or 50,000 — or an individual ready to take control of your health — VYVE has a place for you.</p>
    <div class="cta-section__btns">
      <a href="employers.html#demo" class="btn btn--white btn--lg">Book a Demo for Your Organisation</a>
      <a href="individuals.html" class="btn btn--outline btn--lg" style="border-color:rgba(255,255,255,0.5);color:white">Start Your Personal Journey</a>
    </div>
  </div>
</section>
` + FOOTER();

// ══════════════════════════════════════════════════════════════════════════
// PAGE 2: EMPLOYERS
// ══════════════════════════════════════════════════════════════════════════
const EMPLOYERS = HEAD('For Employers', 'VYVE Health for employers — reduce absence, prove ROI, and transform your workforce wellbeing with the UK\'s most advanced proactive platform.') + NAV('employers') + `

<div class="breadcrumb">
  <div class="container">
    <div class="breadcrumb__inner">
      <a href="index.html">Home</a><span class="breadcrumb__sep">/</span>
      <span>For Employers</span>
    </div>
  </div>
</div>

<!-- HERO -->
<section class="hero hero--employer" style="padding:110px 0 90px">
  <div class="container">
    <div class="hero__grid">
      <div>
        <span class="label" style="color:var(--teal-md)">For HR Leaders & Employers</span>
        <h1 class="display" style="color:white;margin-bottom:24px">Transform your workforce wellbeing.<br>Prove it with data.</h1>
        <p class="lead" style="color:rgba(255,255,255,0.82);margin-bottom:36px;max-width:540px">VYVE gives you the platform, the clinical expertise, and the real-time evidence to shift from reactive crisis management to proactive wellbeing — with measurable ROI from day one.</p>
        <div class="hero__btns">
          <a href="#demo" class="btn btn--white btn--lg">Book a Demo</a>
          <a href="#roi" class="btn btn--outline btn--lg" style="border-color:rgba(255,255,255,0.5);color:white">See the ROI Model</a>
        </div>
      </div>
      <div class="hero__image fade-in">
        <img src="images/app-showcase.jpg" alt="VYVE employer dashboard" loading="eager"/>
      </div>
    </div>
  </div>
</section>

<!-- STAT STRIP -->
<div class="stat-strip">
  <div class="container">
    <div class="stat-strip__inner">
      <div class="stat-item"><div class="stat-item__value"><span data-target="51" data-prefix="£" data-suffix="bn">£51bn</span></div><div class="stat-item__label">Annual cost to UK employers</div><div class="stat-item__source">Deloitte 2024</div></div>
      <div class="stat-item"><div class="stat-item__value"><span data-target="37" data-suffix="%">37%</span></div><div class="stat-item__label">Purely reactive employers</div><div class="stat-item__source">CIPD 2025</div></div>
      <div class="stat-item"><div class="stat-item__value" style="color:#FFD700"><span data-target="5.3" data-prefix="£">£5.3</span></div><div class="stat-item__label">ROI per £1 — proactive interventions</div><div class="stat-item__source">Deloitte 2024</div></div>
      <div class="stat-item"><div class="stat-item__value"><span data-target="9.4">9.4</span></div><div class="stat-item__label">Days absence per person per year</div><div class="stat-item__source">CIPD 2025</div></div>
      <div class="stat-item"><div class="stat-item__value"><span data-target="3" data-suffix="%">3%</span></div><div class="stat-item__label">Typical EAP utilisation rate</div><div class="stat-item__source">Industry benchmark</div></div>
    </div>
  </div>
</div>

<!-- WHAT ORGS ARE DOING -->
<section class="section">
  <div class="container">
    <div class="two-col">
      <div>
        <span class="label">The Current Landscape</span>
        <h2 class="subhead" style="color:var(--dark);margin-bottom:16px">Organisations are investing. The problem isn't effort — it's architecture.</h2>
        <p class="lead" style="margin-bottom:20px">The CIPD 2025 report reveals that most UK employers offer wellbeing benefits. But they're fragmented, reactive, and failing to demonstrate measurable impact.</p>
        <p style="font-size:0.95rem;color:var(--grey);line-height:1.75;margin-bottom:20px">EAPs — the most commonly provided benefit — achieve just 3–6% utilisation. Gym memberships go unused. Stress management workshops are forgotten within 30 days. Mental health first aiders are under-resourced and dealing with structural problems with individual tools.</p>
        <p style="font-size:0.95rem;color:var(--grey);line-height:1.75;margin-bottom:28px">The result: 148.9 million working days lost to sickness in 2024 (ONS), with presenteeism costing a further £24 billion (Deloitte). The investment is there. The architecture is wrong.</p>
      </div>
      <div>
        <h3 style="font-size:1rem;color:var(--dark);font-weight:700;margin-bottom:16px">What most employers are providing — and why it's not working</h3>
        <table class="data-table">
          <thead><tr><th>Benefit</th><th>Prevalence</th><th>Critical Gap</th></tr></thead>
          <tbody>
            <tr><td class="highlight">Employee Assistance Programmes</td><td>~75%</td><td>3–6% utilisation; no community layer</td></tr>
            <tr><td class="highlight">Counselling access</td><td>~55%</td><td>Wait times; reactive by design</td></tr>
            <tr><td class="highlight">Gym memberships</td><td>~48%</td><td>Physical only; no mental health component</td></tr>
            <tr><td class="highlight">Stress management training</td><td>~43%</td><td>One-off; no sustained behaviour change</td></tr>
            <tr><td class="highlight">Mental health first aiders</td><td>~41%</td><td>Under-resourced; stigma barriers</td></tr>
            <tr><td class="highlight">Meditation apps</td><td>~36%</td><td>Low engagement after Week 2; generic</td></tr>
            <tr><td class="highlight">Manager MH training</td><td>~29%</td><td>Inconsistent; no follow-through</td></tr>
          </tbody>
        </table>
        <p style="font-size:0.75rem;color:var(--grey-lt);margin-top:8px">Source: CIPD Health & Wellbeing at Work 2025</p>
      </div>
    </div>
  </div>
</section>

<!-- ENTERPRISE PROMISE -->
<section class="section section--light" id="promise">
  <div class="container">
    <div class="section__header">
      <span class="label">The VYVE Enterprise Promise</span>
      <h2 class="headline">Six measurable commitments. Not aspirations — outcomes.</h2>
      <p class="lead">Every VYVE employer contract is backed by our six Enterprise Promises. These are contractually-supported outcomes, measured by the data infrastructure built into the platform from day one.</p>
    </div>
    <div class="cards cards--2" style="gap:20px">
      <div class="promise fade-up">
        <div class="promise__num">1</div>
        <div><div class="promise__title">Reduce Absence</div><div class="promise__body">Measurable reduction in sickness absence days within 12 months of full deployment. Modelled against your baseline using CIPD and Deloitte benchmarks.</div><span class="promise__tag">Measured via Looker dashboard vs. baseline</span></div>
      </div>
      <div class="promise fade-up">
        <div class="promise__num">2</div>
        <div><div class="promise__title">Improve Engagement</div><div class="promise__body">Demonstrable improvement in employee engagement scores, eNPS, and platform engagement data — from quarterly pulse surveys and real-time activity tracking.</div><span class="promise__tag">Quarterly pulse surveys + platform data</span></div>
      </div>
      <div class="promise fade-up">
        <div class="promise__num">3</div>
        <div><div class="promise__title">Prove ROI</div><div class="promise__body">Clear, quantified return on investment — minimum 3x ROI modelled for every client, combining absence cost savings, productivity uplift, and turnover reduction.</div><span class="promise__tag">Absence savings + productivity + turnover</span></div>
      </div>
      <div class="promise fade-up">
        <div class="promise__num">4</div>
        <div><div class="promise__title">Support Line Managers</div><div class="promise__body">Managers receive early warning signals, communication guides, and training resources to identify and support struggling employees — before a crisis occurs.</div><span class="promise__tag">Manager toolkit usage + conversations completed</span></div>
      </div>
      <div class="promise fade-up">
        <div class="promise__num">5</div>
        <div><div class="promise__title">Close the Reactive Gap</div><div class="promise__body">Systematic shift from reactive crisis management to proactive wellbeing — measured by the proportion of employees accessing support before reaching crisis point.</div><span class="promise__tag">% employees accessing support proactively</span></div>
      </div>
      <div class="promise fade-up">
        <div class="promise__num">6</div>
        <div><div class="promise__title">Scale to Any Workforce</div><div class="promise__body">Works equally for 50 or 50,000 employees — remote, hybrid, or on-site. No minimum viable headcount. Fully configurable to your sector, demographics, and wellbeing priorities.</div><span class="promise__tag">Deployment across all workforce types</span></div>
      </div>
    </div>
  </div>
</section>

<!-- ROI MODEL -->
<section class="section" id="roi">
  <div class="container">
    <div class="section__header">
      <span class="label">The Investment Case</span>
      <h2 class="headline">The numbers are not close.</h2>
      <p class="lead">Deloitte (2024) found that proactive, universal wellbeing interventions return £5.30 for every £1 invested. The following model shows what this means for a 500-person organisation.</p>
    </div>
    <div class="roi-block">
      <div class="roi-block__content">
        <h3 class="subhead" style="color:white;margin-bottom:16px">Why the ROI case is compelling</h3>
        <p style="color:var(--teal-md);font-size:0.95rem;line-height:1.75;margin-bottom:16px">The Deloitte Mental Health and Employers (2024) analysis examined 56 case studies and found that proactive mental health interventions return £5.30 per £1 invested — driven by reduced absence, lower turnover, and productivity gains.</p>
        <p style="color:var(--teal-md);font-size:0.95rem;line-height:1.75;">VYVE's platform is designed specifically to deliver these proactive, universal outcomes — not the reactive point-in-time interventions that return a lower £4.10 per £1.</p>
        <div class="roi-stats">
          <div class="roi-block__stat"><div class="roi-block__stat-value">£5.30</div><div class="roi-block__stat-label">per £1 — proactive interventions (Deloitte)</div></div>
          <div class="roi-block__stat"><div class="roi-block__stat-value">£24bn</div><div class="roi-block__stat-label">annual cost of presenteeism to UK employers</div></div>
          <div class="roi-block__stat"><div class="roi-block__stat-value">54%</div><div class="roi-block__stat-label">of employees reported improved sleep/stress with apps</div></div>
          <div class="roi-block__stat"><div class="roi-block__stat-value">39%</div><div class="roi-block__stat-label">reported improved productivity after MH support</div></div>
        </div>
      </div>
      <div>
        <h4 style="color:var(--teal-lt);font-size:0.85rem;font-weight:700;margin-bottom:16px;text-transform:uppercase;letter-spacing:0.08em">500-Person Organisation Model</h4>
        <table class="data-table" style="font-size:0.82rem">
          <thead><tr><th>Metric</th><th>Conservative</th><th style="background:#155f5f">VYVE Target</th></tr></thead>
          <tbody style="background:rgba(255,255,255,0.03);color:var(--teal-md)">
            <tr style="border-color:rgba(255,255,255,0.08)"><td style="border-color:rgba(255,255,255,0.08)">Absence reduction</td><td style="border-color:rgba(255,255,255,0.08)">0.5 days/yr</td><td style="background:rgba(27,120,120,0.3);color:white;border-color:rgba(255,255,255,0.08)"><strong>1.5 days/yr</strong></td></tr>
            <tr style="border-color:rgba(255,255,255,0.08)"><td style="border-color:rgba(255,255,255,0.08)">Presenteeism reduction</td><td style="border-color:rgba(255,255,255,0.08)">3% gain</td><td style="background:rgba(27,120,120,0.3);color:white;border-color:rgba(255,255,255,0.08)"><strong>6% gain</strong></td></tr>
            <tr style="border-color:rgba(255,255,255,0.08)"><td style="border-color:rgba(255,255,255,0.08)">Turnover improvement</td><td style="border-color:rgba(255,255,255,0.08)">0.5%</td><td style="background:rgba(27,120,120,0.3);color:white;border-color:rgba(255,255,255,0.08)"><strong>1.5%</strong></td></tr>
            <tr style="border-color:rgba(255,255,255,0.08)"><td style="border-color:rgba(255,255,255,0.08)">Total value p.a.</td><td style="border-color:rgba(255,255,255,0.08)">~£185,000</td><td style="background:rgba(27,120,120,0.3);color:white;border-color:rgba(255,255,255,0.08)"><strong>~£430,000</strong></td></tr>
            <tr style="border-color:rgba(255,255,255,0.08)"><td style="border-color:rgba(255,255,255,0.08)">VYVE investment p.a.</td><td style="border-color:rgba(255,255,255,0.08)" colspan="2" style="text-align:center">~£60,000</td></tr>
            <tr style="border-color:rgba(255,255,255,0.08)"><td style="border-color:rgba(255,255,255,0.08);font-weight:700;color:white">Net ROI multiple</td><td style="border-color:rgba(255,255,255,0.08);color:var(--teal-lt)">~3.1x</td><td style="background:rgba(27,120,120,0.5);color:var(--teal-lt);font-weight:700;border-color:rgba(255,255,255,0.08)"><strong>~7.2x</strong></td></tr>
          </tbody>
        </table>
        <p style="font-size:0.72rem;color:rgba(255,255,255,0.35);margin-top:8px">* Modelled using Deloitte Mental Health and Employers (2024) benchmarks and ONS wage data</p>
      </div>
    </div>
  </div>
</section>

<!-- ECOSYSTEM -->
<section class="section section--light" id="ecosystem">
  <div class="container">
    <div class="section__header">
      <span class="label">Where VYVE Fits</span>
      <h2 class="headline">Not a replacement. An upgrade.</h2>
      <p class="lead">VYVE doesn't require you to rip out your existing benefits. It sits alongside your EAP, adds the proactive layer that EAPs cannot provide, and integrates with your HRIS for seamless data flow.</p>
    </div>
    <div class="compare fade-up">
      <div class="compare__col">
        <div class="compare__head old">❌ Traditional Wellbeing Approach</div>
        <div class="compare__item old"><svg viewBox="0 0 24 24" fill="none" stroke="#DC2626" stroke-width="2"><circle cx="12" cy="12" r="10"/><path d="M15 9l-6 6M9 9l6 6"/></svg>EAP with 3–6% utilisation — invisible to most employees</div>
        <div class="compare__item old"><svg viewBox="0 0 24 24" fill="none" stroke="#DC2626" stroke-width="2"><circle cx="12" cy="12" r="10"/><path d="M15 9l-6 6M9 9l6 6"/></svg>Annual wellbeing survey as the only data point</div>
        <div class="compare__item old"><svg viewBox="0 0 24 24" fill="none" stroke="#DC2626" stroke-width="2"><circle cx="12" cy="12" r="10"/><path d="M15 9l-6 6M9 9l6 6"/></svg>Reactive: waiting for crisis before acting</div>
        <div class="compare__item old"><svg viewBox="0 0 24 24" fill="none" stroke="#DC2626" stroke-width="2"><circle cx="12" cy="12" r="10"/><path d="M15 9l-6 6M9 9l6 6"/></svg>No community; no shared goals; no engagement mechanic</div>
        <div class="compare__item old"><svg viewBox="0 0 24 24" fill="none" stroke="#DC2626" stroke-width="2"><circle cx="12" cy="12" r="10"/><path d="M15 9l-6 6M9 9l6 6"/></svg>Generic programmes — same for everyone</div>
        <div class="compare__item old"><svg viewBox="0 0 24 24" fill="none" stroke="#DC2626" stroke-width="2"><circle cx="12" cy="12" r="10"/><path d="M15 9l-6 6M9 9l6 6"/></svg>No ROI visibility — wellbeing as a cost, not an investment</div>
      </div>
      <div class="compare__col">
        <div class="compare__head new">✓ The VYVE Approach</div>
        <div class="compare__item new"><svg viewBox="0 0 24 24" fill="none" stroke="#1B7878" stroke-width="2"><polyline points="20,6 9,17 4,12"/></svg>Always-on platform with 60%+ engagement — employees actually use it</div>
        <div class="compare__item new"><svg viewBox="0 0 24 24" fill="none" stroke="#1B7878" stroke-width="2"><polyline points="20,6 9,17 4,12"/></svg>Real-time dashboard: absence trends, engagement, and ROI</div>
        <div class="compare__item new"><svg viewBox="0 0 24 24" fill="none" stroke="#1B7878" stroke-width="2"><polyline points="20,6 9,17 4,12"/></svg>Proactive: AI identifies risk signals before absence occurs</div>
        <div class="compare__item new"><svg viewBox="0 0 24 24" fill="none" stroke="#1B7878" stroke-width="2"><polyline points="20,6 9,17 4,12"/></svg>Community sub-groups, team challenges, shared goals</div>
        <div class="compare__item new"><svg viewBox="0 0 24 24" fill="none" stroke="#1B7878" stroke-width="2"><polyline points="20,6 9,17 4,12"/></svg>AI-personalised pathways for each employee's unique needs</div>
        <div class="compare__item new"><svg viewBox="0 0 24 24" fill="none" stroke="#1B7878" stroke-width="2"><polyline points="20,6 9,17 4,12"/></svg>Minimum 3x ROI modelled and tracked for every client</div>
      </div>
    </div>
    <div style="margin-top:40px">
      <div class="callout">
        <p class="callout__quote">"VYVE is not positioned to replace EAPs entirely — many employers have contractual obligations. Instead, VYVE integrates alongside existing EAPs, dramatically increasing reach and engagement while providing the proactive layer that EAPs cannot deliver."</p>
        <p class="callout__attr">— VYVE Health, Future State Vision v3</p>
      </div>
    </div>
  </div>
</section>

<!-- WHAT YOU GET -->
<section class="section">
  <div class="container">
    <div class="section__header">
      <span class="label">What Employers Get</span>
      <h2 class="headline">Everything you need. Nothing you don't.</h2>
    </div>
    <div class="cards cards--3" style="gap:24px">
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><rect x="2" y="3" width="20" height="14" rx="2"/><path d="M8 21h8M12 17v4"/></svg></div>
        <div class="card__label">Employer Dashboard</div>
        <h3 class="card__title">Real-Time Wellbeing Intelligence</h3>
        <p class="card__body">Live absence patterns, platform engagement, department-level trends, and ROI tracking — all in one place. No more waiting for the annual survey to find out how your people are doing.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87M16 3.13a4 4 0 0 1 0 7.75"/></svg></div>
        <div class="card__label">Manager Toolkit</div>
        <h3 class="card__title">Early Warning & Manager Support</h3>
        <p class="card__body">Managers receive AI-driven early warning signals when team members show risk patterns. Guided conversation scripts, mental health resources, and escalation pathways — built into the platform.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M12 22s-8-4.5-8-11.8A8 8 0 0 1 12 2a8 8 0 0 1 8 8.2c0 7.3-8 11.8-8 11.8z"/></svg></div>
        <div class="card__label">Social Mission</div>
        <h3 class="card__title">Charity Mechanic — Built In</h3>
        <p class="card__body">Employee activity automatically generates charitable donations — managed entirely by the platform. Employees vote on causes quarterly. A powerful employer brand story, delivered at zero additional overhead.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z"/></svg></div>
        <div class="card__label">Personalisation at Scale</div>
        <h3 class="card__title">PAD — AI Director for Every Employee</h3>
        <p class="card__body">Every employee gets their own AI-powered wellbeing director. PAD personalises programmes, tracks progress, nudges habits, and coordinates the entire employee wellbeing journey — at any workforce size.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"/></svg></div>
        <div class="card__label">Integration</div>
        <h3 class="card__title">HRIS & EAP Integration</h3>
        <p class="card__body">VYVE connects to your existing HR systems (Workday, BambooHR, SAP) and works alongside your current EAP. Single sign-on, automated onboarding, and data flows that eliminate admin overhead.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M22 12h-4l-3 9L9 3l-3 9H2"/></svg></div>
        <div class="card__label">Scalability</div>
        <h3 class="card__title">From 50 to 50,000 Employees</h3>
        <p class="card__body">VYVE is built to scale without degradation. Whether you're a growing SME or a large enterprise, the platform, data infrastructure, and support model adapts. No minimum headcount. No compromise on quality.</p>
      </div>
    </div>
  </div>
</section>

<!-- ROADMAP PREVIEW -->
<section class="section section--light">
  <div class="container">
    <div class="section__header">
      <span class="label">Built for the Long Term</span>
      <h2 class="headline">A platform that grows with your organisation.</h2>
      <p class="lead">VYVE follows a clear four-phase roadmap — each phase building on the last to deliver more intelligence, more integration, and more impact.</p>
    </div>
    <div class="phases fade-up">
      <div class="phase v1">
        <span class="phase__tag">V1 — Now</span>
        <div class="phase__title">Foundation</div>
        <div class="phase__date">Now — Q3 2026</div>
        <ul class="phase__list">
          <li>Full platform deployment</li>
          <li>PAD AI personalisation</li>
          <li>Employer dashboard</li>
          <li>Charity mechanic live</li>
          <li>Community groups</li>
          <li>10+ wellbeing programmes</li>
        </ul>
      </div>
      <div class="phase v2">
        <span class="phase__tag">V2 — 2027</span>
        <div class="phase__title">Expansion</div>
        <div class="phase__date">Q4 2026 — Q2 2027</div>
        <ul class="phase__list">
          <li>Full sub-groups module</li>
          <li>HRIS integrations</li>
          <li>Wearable device sync</li>
          <li>Predictive absence modelling</li>
          <li>1-2-1 therapy marketplace</li>
          <li>Ambassador programme</li>
        </ul>
      </div>
      <div class="phase v3">
        <span class="phase__tag">V3 — 2028</span>
        <div class="phase__title">Deepening</div>
        <div class="phase__date">Q3 2027 — Q4 2028</div>
        <ul class="phase__list">
          <li>Proprietary VYVE AI model</li>
          <li>Cross-company communities</li>
          <li>CPD-accredited programmes</li>
          <li>Health retreats</li>
          <li>Enterprise API (white-label)</li>
          <li>VYVE merch sub-brand</li>
        </ul>
      </div>
      <div class="phase v4">
        <span class="phase__tag">V4 — 2029+</span>
        <div class="phase__title">End State</div>
        <div class="phase__date">2029 onwards</div>
        <ul class="phase__list">
          <li>500,000+ employees on platform</li>
          <li>Consumer lifestyle brand</li>
          <li>International expansion</li>
          <li>Clinical-grade AI tools</li>
          <li>Pension & insurance integrations</li>
          <li>VYVE Foundation (charity arm)</li>
        </ul>
      </div>
    </div>
  </div>
</section>

<!-- DEMO CTA -->
<section class="cta-section" id="demo">
  <div class="container">
    <span class="label" style="display:block;margin-bottom:16px">Ready to see it in action?</span>
    <h2 class="display" style="color:white;margin-bottom:20px">Book your demo today.</h2>
    <p class="lead" style="color:var(--teal-md);margin-bottom:16px;max-width:560px;margin-left:auto;margin-right:auto">We'll walk you through the platform, model the ROI for your specific workforce, and show you exactly how VYVE would work within your existing wellbeing strategy.</p>
    <p style="color:rgba(255,255,255,0.5);font-size:0.85rem;margin-bottom:36px">No commitment. No hard sell. Just an honest conversation about what's possible.</p>
    <div class="cta-section__btns">
      <a href="mailto:hello@vyvehealth.co.uk?subject=Demo Request" class="btn btn--white btn--lg">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
        Email Us for a Demo
      </a>
      <a href="science.html" class="btn btn--outline btn--lg" style="border-color:rgba(255,255,255,0.5);color:white">Read the Evidence →</a>
    </div>
  </div>
</section>
` + FOOTER();

// ══════════════════════════════════════════════════════════════════════════
// PAGE 3: INDIVIDUALS
// ══════════════════════════════════════════════════════════════════════════
const INDIVIDUALS = HEAD('For Individuals', 'VYVE Health for individuals — personalised wellbeing, AI guidance, expert community, and a platform that makes good health the default.') + NAV('individuals') + `

<div class="breadcrumb">
  <div class="container">
    <div class="breadcrumb__inner">
      <a href="index.html">Home</a><span class="breadcrumb__sep">/</span>
      <span>For Individuals</span>
    </div>
  </div>
</div>

<!-- HERO -->
<section class="hero hero--individual" style="padding:110px 0 90px">
  <div class="container">
    <div class="hero__grid">
      <div>
        <span class="label" style="color:rgba(255,255,255,0.7)">For Individuals</span>
        <h1 class="display" style="color:white;margin-bottom:24px">Your wellbeing,<br>personalised.<br>Your community,<br>waiting.</h1>
        <p class="lead" style="color:rgba(255,255,255,0.85);margin-bottom:36px;max-width:520px">Most wellbeing apps are built for everyone — which means they're built for no one. VYVE learns who you are, what you're dealing with, and what you actually need — then builds a health journey around you.</p>
        <div class="hero__btns">
          <a href="#personas" class="btn btn--white btn--lg">Find Your Pathway</a>
          <a href="#community" class="btn btn--outline btn--lg" style="border-color:rgba(255,255,255,0.5);color:white">Explore Community</a>
        </div>
      </div>
      <div class="hero__image fade-in">
        <img src="images/journey.jpg" alt="VYVE individual journey" loading="eager"/>
      </div>
    </div>
  </div>
</section>

<!-- INTRO -->
<section class="section">
  <div class="container">
    <div class="two-col">
      <div>
        <span class="label">Meet PAD — Your Personal AI Director</span>
        <h2 class="subhead" style="color:var(--dark);margin-bottom:16px">Not a chatbot. Not a quiz. Your genuine AI health coach.</h2>
        <p class="lead" style="margin-bottom:20px">PAD (Personal AI Director) is the intelligence layer behind your VYVE experience. It learns your patterns, understands your context, and proactively shapes your wellbeing journey — every day.</p>
        <ul class="check-list" style="margin-bottom:28px">
          <li>Conducts a conversational wellbeing check-in when you join — no forms, no questionnaires</li>
          <li>Learns your patterns over time and adapts your programme accordingly</li>
          <li>Identifies early stress signals and suggests support before things escalate</li>
          <li>Coordinates across all 10 wellbeing pillars — connecting physical, mental, financial, and social health</li>
          <li>Gets smarter with every interaction — the longer you're on VYVE, the more personalised it becomes</li>
        </ul>
        <p style="font-size:0.88rem;color:var(--grey);font-style:italic">VYVE's AI is designed to augment — never replace — human expertise. PAD connects you to real practitioners, real coaches, and real community when you need them.</p>
      </div>
      <div class="two-col__image">
        <img src="images/app-showcase.jpg" alt="PAD AI Director" loading="lazy"/>
      </div>
    </div>
  </div>
</section>

<!-- PERSONAS -->
<section class="section section--light" id="personas">
  <div class="container">
    <div class="section__header">
      <span class="label">Your Mental Health Pathway</span>
      <h2 class="headline">Five expert pathways. One is yours.</h2>
      <p class="lead">VYVE's five AI-guided mental health personas are built on evidence-based therapeutic frameworks. PAD identifies which pathway fits your current state — and guides you through it with precision.</p>
    </div>
    <div class="cards cards--3" style="gap:24px">
      <div class="persona nova fade-up">
        <div class="persona__emoji">🔥</div>
        <div class="persona__name">NOVA</div>
        <div class="persona__tag">Burnout & Energy Management</div>
        <p class="persona__desc">For those running on empty. NOVA helps you identify the root causes of burnout, rebuild sustainable energy, and redesign how you work and recover. Evidence-based techniques from CBT and ACT frameworks.</p>
      </div>
      <div class="persona river fade-up">
        <div class="persona__emoji">🌊</div>
        <div class="persona__name">RIVER</div>
        <div class="persona__tag">Anxiety & Stress</div>
        <p class="persona__desc">When the current feels overwhelming. RIVER provides structured support for anxiety and chronic stress — breathing techniques, cognitive reframing, graded exposure, and daily regulation practices.</p>
      </div>
      <div class="persona spark fade-up">
        <div class="persona__emoji">⚡</div>
        <div class="persona__name">SPARK</div>
        <div class="persona__tag">Motivation & Purpose</div>
        <p class="persona__desc">For those who've lost their why. SPARK reignites motivation and purpose through values clarification, goal-setting frameworks, behavioural activation, and positive identity work.</p>
      </div>
      <div class="persona sage fade-up">
        <div class="persona__emoji">🌿</div>
        <div class="persona__name">SAGE</div>
        <div class="persona__tag">Life Transitions & Financial Stress</div>
        <p class="persona__desc">For the big changes — career shifts, parenthood, financial pressure, redundancy. SAGE combines practical tools with emotional support to navigate transitions with resilience and clarity.</p>
      </div>
      <div class="persona haven fade-up">
        <div class="persona__emoji">🏠</div>
        <div class="persona__name">HAVEN</div>
        <div class="persona__tag">Trauma, Grief & Crisis Support</div>
        <p class="persona__desc">A safe space for the hardest times. HAVEN provides trauma-informed, clinically-validated support for grief, loss, and crisis — with seamless escalation to accredited therapists when needed.</p>
      </div>
      <div class="card fade-up" style="display:flex;flex-direction:column;justify-content:center;align-items:center;background:var(--teal-xxl);border:2px dashed var(--teal-md);text-align:center">
        <div style="font-size:2rem;margin-bottom:12px">🤖</div>
        <h3 class="card__title" style="font-size:1rem;margin-bottom:8px">Not sure which is yours?</h3>
        <p class="card__body" style="font-size:0.85rem;margin-bottom:16px">PAD conducts a gentle, conversational check-in and guides you to the right pathway — then adapts as your needs evolve.</p>
        <a href="#cta" class="btn btn--primary" style="font-size:0.85rem;padding:10px 20px">Start Your Check-In</a>
      </div>
    </div>
  </div>
</section>

<!-- COMMUNITY SUB-GROUPS -->
<section class="section" id="community">
  <div class="container">
    <div class="section__header">
      <span class="label">Community Sub-Groups</span>
      <h2 class="headline">Health is better together.</h2>
      <p class="lead">Research shows group-based wellbeing achieves 26% higher adherence than solo programmes. VYVE's sub-group communities let you connect, train, and grow with people who share your goals.</p>
    </div>
    <div class="two-col" style="gap:60px">
      <div>
        <h3 class="subhead" style="font-size:1.3rem;margin-bottom:20px">Create or join your community</h3>
        <p style="color:var(--grey);font-size:0.95rem;line-height:1.75;margin-bottom:20px">Sub-groups are self-organising communities within VYVE. Any member can create a group — whether it's a lunchtime running club, a weight loss challenge, a menopause support group, or a shared meditation practice.</p>
        <div class="cards cards--2" style="gap:12px;margin-bottom:24px">
          <div style="background:var(--teal-xxl);border-radius:10px;padding:16px">
            <div style="font-size:1.2rem;margin-bottom:8px">🏃</div>
            <div style="font-weight:700;font-size:0.9rem;color:var(--dark);margin-bottom:4px">Marathon Runners</div>
            <div style="font-size:0.8rem;color:var(--grey)">Shared training plans, route sharing, race prep</div>
          </div>
          <div style="background:var(--teal-xxl);border-radius:10px;padding:16px">
            <div style="font-size:1.2rem;margin-bottom:8px">💪</div>
            <div style="font-weight:700;font-size:0.9rem;color:var(--dark);margin-bottom:4px">Strength & Fitness</div>
            <div style="font-size:0.8rem;color:var(--grey)">Weekly workouts, progress tracking, form tips</div>
          </div>
          <div style="background:var(--teal-xxl);border-radius:10px;padding:16px">
            <div style="font-size:1.2rem;margin-bottom:8px">🧘</div>
            <div style="font-weight:700;font-size:0.9rem;color:var(--dark);margin-bottom:4px">Mindful Mondays</div>
            <div style="font-size:0.8rem;color:var(--grey)">Weekly meditation, stress check-ins, breathing</div>
          </div>
          <div style="background:var(--teal-xxl);border-radius:10px;padding:16px">
            <div style="font-size:1.2rem;margin-bottom:8px">🌸</div>
            <div style="font-weight:700;font-size:0.9rem;color:var(--dark);margin-bottom:4px">Menopause Movers</div>
            <div style="font-size:0.8rem;color:var(--grey)">Peer support, expert Q&As, lifestyle guidance</div>
          </div>
        </div>
        <a href="#cta" class="btn btn--primary">Find Your Community →</a>
      </div>
      <div>
        <h3 style="font-size:1rem;font-weight:700;color:var(--dark);margin-bottom:16px">What sub-groups give you</h3>
        <div style="display:flex;flex-direction:column;gap:12px">
          ${[
            ["Community Feed", "Share wins, struggles, photos, and progress with your group. Real humans. Real encouragement."],
            ["Shared Challenges", "Set collective goals — steps targets, weekly workout streaks, weight milestones — and track them together."],
            ["Group Training Plans", "Coaches and admins can assign VYVE programmes to the whole group. Everyone follows the same plan — accountability built in."],
            ["Group Events", "Schedule virtual and in-person events: group runs, fitness classes, coffee meetups, charity walks."],
            ["Leaderboards", "Optional friendly competition — members can opt in to see how they rank within their community."],
            ["Charity Voting", "Groups nominate charities for VYVE's quarterly giving vote — adding a layer of shared purpose."],
          ].map(([t,d]) => `<div style="display:flex;gap:14px;padding:14px;background:var(--light);border-radius:10px;border:1px solid var(--border)">
            <div style="width:8px;min-width:8px;background:var(--teal);border-radius:4px;margin:2px 0"></div>
            <div><div style="font-weight:700;color:var(--dark);font-size:0.92rem;margin-bottom:4px">${t}</div><div style="font-size:0.85rem;color:var(--grey)">${d}</div></div>
          </div>`).join('')}
        </div>
      </div>
    </div>
    <div style="margin-top:48px;background:var(--teal-xxl);border:1px solid var(--teal-md);border-radius:16px;padding:32px">
      <div style="display:flex;gap:40px;flex-wrap:wrap;justify-content:space-around;text-align:center">
        <div><div style="font-size:2rem;font-weight:700;color:var(--teal)">26%</div><div style="font-size:0.85rem;color:var(--grey);margin-top:4px">Higher adherence in group programmes</div><div style="font-size:0.72rem;color:var(--grey-lt)">Journal of Sport & Exercise Psychology, 2023</div></div>
        <div><div style="font-size:2rem;font-weight:700;color:var(--teal)">4x</div><div style="font-size:0.85rem;color:var(--grey);margin-top:4px">Higher engagement with community features</div><div style="font-size:0.72rem;color:var(--grey-lt)">McKinsey Health Institute, 2023</div></div>
        <div><div style="font-size:2rem;font-weight:700;color:var(--teal)">2.3x</div><div style="font-size:0.85rem;color:var(--grey);margin-top:4px">More likely to complete with community goals</div><div style="font-size:0.72rem;color:var(--grey-lt)">BetterUp, 2024</div></div>
      </div>
    </div>
  </div>
</section>

<!-- 10 PILLARS -->
<section class="section section--light" id="pillars">
  <div class="container">
    <div class="section__header">
      <span class="label">The 10 Pillars</span>
      <h2 class="headline">Every dimension of your health. One platform.</h2>
      <p class="lead">VYVE doesn't just look after your mind. It addresses every pillar of a healthy, fulfilling life — building out progressively as the platform evolves.</p>
    </div>
    <div style="display:grid;grid-template-columns:repeat(2,1fr);gap:14px" class="fade-up">
      ${[
        ["1", "Agentic AI — PAD", "Your Personal AI Director — always-on, learning, adapting, and proactively supporting your wellbeing journey."],
        ["2", "Mental Health Personas", "Five clinically-informed pathways: NOVA, RIVER, SPARK, SAGE, HAVEN — matched to your current needs."],
        ["3", "VYVE Podcast & Content", "Expert interviews, evidence-based guides, lived experience stories — building a culture of health literacy."],
        ["4", "Ambassadors & Experts", "Live sessions, Q&As, and events from a curated network of practitioners, athletes, and coaches."],
        ["5", "Brand Partnerships", "Exclusive access to partner brands in nutrition, sleep tech, wearables, and wellness — adding real-world value."],
        ["6", "Educational Programmes", "CPD-accredited programmes in mental health, leadership, nutrition, and financial wellbeing."],
        ["7", "Health Retreats", "Annual retreat experiences — deepening community bonds and creating moments of genuine transformation."],
        ["8", "Tailored Health Programmes", "Science-backed cohort programmes: menopause support, new parent return-to-work, neurodiversity at work, and more."],
        ["9", "1-2-1 Therapy", "Seamless in-app referral to accredited therapists and coaches — destigmatised, integrated, and accessible."],
        ["10", "In-Person Events", "Community fitness challenges, charity runs, workshops, and socials — bridging digital engagement with real connection."],
      ].map(([n,t,d]) => `<div class="pillar"><div class="pillar__num">${n}</div><div><div class="pillar__title">${t}</div><div class="pillar__desc">${d}</div></div></div>`).join('')}
    </div>
  </div>
</section>

<!-- YOUR JOURNEY -->
<section class="section">
  <div class="container">
    <div class="two-col">
      <div>
        <span class="label">Your VYVE Journey</span>
        <h2 class="subhead" style="color:var(--dark);margin-bottom:24px">From new member to movement.</h2>
        <div class="journey">
          <div class="journey-step"><div class="journey-step__line"><div class="journey-step__dot">1</div><div class="journey-step__connector"></div></div><div class="journey-step__content"><div class="journey-step__title">Personalised Check-In</div><div class="journey-step__body">PAD conducts a brief conversational assessment — not a form. It learns your current state, goals, and preferences. You're guided to your persona within minutes.</div></div></div>
          <div class="journey-step"><div class="journey-step__line"><div class="journey-step__dot">2</div><div class="journey-step__connector"></div></div><div class="journey-step__content"><div class="journey-step__title">Your Pathway Begins</div><div class="journey-step__body">You start a structured 12-week programme — daily micro-sessions, weekly goals, expert content. Your employer can see aggregate trends; your personal data stays yours.</div></div></div>
          <div class="journey-step"><div class="journey-step__line"><div class="journey-step__dot">3</div><div class="journey-step__connector"></div></div><div class="journey-step__content"><div class="journey-step__title">Community Discovery</div><div class="journey-step__body">At Day 7, PAD suggests sub-groups that match your interests. You join your first community. The social layer kicks in — and engagement multiplies.</div></div></div>
          <div class="journey-step"><div class="journey-step__line"><div class="journey-step__dot">4</div><div class="journey-step__connector"></div></div><div class="journey-step__content"><div class="journey-step__title">The Habit Lock-In</div><div class="journey-step__body">By Day 21, you have a VYVE routine. Streaks, community recognition, and the charity mechanic reinforce daily engagement. Your activity is visibly making a difference.</div></div></div>
          <div class="journey-step"><div class="journey-step__line"><div class="journey-step__dot">5</div><div class="journey-step__connector"></div></div><div class="journey-step__content"><div class="journey-step__title">Deepening & Exploring</div><div class="journey-step__body">By Month 3, you're exploring the full platform — podcasts, ambassador sessions, therapy if needed. You might start managing your own sub-group.</div></div></div>
          <div class="journey-step"><div class="journey-step__line"><div class="journey-step__dot">6</div><div class="journey-step__connector"></div></div><div class="journey-step__content"><div class="journey-step__title">You Are the Movement</div><div class="journey-step__body">VYVE is no longer a 'work benefit'. It's part of your identity. You follow the content, wear the merch, attend events, and bring others along.</div></div></div>
        </div>
      </div>
      <div class="two-col__image">
        <img src="images/story.jpg" alt="Your VYVE journey" loading="lazy"/>
      </div>
    </div>
  </div>
</section>

<!-- CHARITY -->
<section class="section section--light" id="charity">
  <div class="container">
    <div class="charity">
      <div class="charity__icon">💚</div>
      <h2 class="charity__title">Your health helps others too.</h2>
      <p class="charity__body">Every workout, mindfulness session, and goal you complete on VYVE automatically generates a charitable donation — managed entirely by the platform. Every quarter, your community votes on which charity receives the pooled fund.</p>
      <div style="display:flex;justify-content:center;gap:32px;flex-wrap:wrap;margin-bottom:28px">
        <div style="text-align:center"><div style="font-size:2rem;font-weight:700;color:var(--teal)">2.3x</div><div style="font-size:0.82rem;color:var(--grey);margin-top:4px">Higher completion with prosocial goals</div></div>
        <div style="text-align:center"><div style="font-size:2rem;font-weight:700;color:var(--teal)">£1m+</div><div style="font-size:0.82rem;color:var(--grey);margin-top:4px">Annual giving target at scale</div></div>
        <div style="text-align:center"><div style="font-size:2rem;font-weight:700;color:var(--teal)">100%</div><div style="font-size:0.82rem;color:var(--grey);margin-top:4px">Automated — no admin, no manual effort</div></div>
      </div>
      <p style="font-size:0.85rem;color:var(--grey);max-width:500px;margin:0 auto">Research by Grant & Berry (2011) and Batson (2011) confirms: combining personal wellbeing goals with a prosocial purpose creates significantly stronger motivation and long-term habit formation than either alone.</p>
    </div>
  </div>
</section>

<!-- CTA -->
<section class="cta-section" id="cta">
  <div class="container">
    <span class="label" style="display:block;margin-bottom:16px">Start your journey</span>
    <h2 class="display" style="color:white;margin-bottom:20px">Your health.<br>Your community.<br>Your way.</h2>
    <p class="lead" style="color:var(--teal-md);margin-bottom:36px;max-width:520px;margin-left:auto;margin-right:auto">VYVE is available through your employer. If your organisation isn't yet a VYVE partner, tell them — or get in touch with us directly and we'll make it happen.</p>
    <div class="cta-section__btns">
      <a href="mailto:hello@vyvehealth.co.uk?subject=Individual Enquiry" class="btn btn--white btn--lg">Get in Touch</a>
      <a href="employers.html#demo" class="btn btn--outline btn--lg" style="border-color:rgba(255,255,255,0.5);color:white">Refer Your Employer →</a>
    </div>
  </div>
</section>
` + FOOTER();

// ══════════════════════════════════════════════════════════════════════════
// PAGE 4: SCIENCE
// ══════════════════════════════════════════════════════════════════════════
const SCIENCE = HEAD('Our Science', 'VYVE Health is grounded in independent research — Deloitte, CIPD, ONS, and peer-reviewed behavioural science. See the evidence.') + NAV('science') + `

<div class="breadcrumb">
  <div class="container">
    <div class="breadcrumb__inner">
      <a href="index.html">Home</a><span class="breadcrumb__sep">/</span>
      <span>Our Science</span>
    </div>
  </div>
</div>

<section class="hero hero--about" style="padding:100px 0 80px">
  <div class="container container--narrow" style="text-align:center">
    <span class="label" style="color:var(--teal-md)">Our Science</span>
    <h1 class="display" style="color:white;margin-bottom:24px">Not a hunch.<br>A body of proof.</h1>
    <p class="lead" style="color:rgba(255,255,255,0.82);max-width:600px;margin:0 auto">Every aspect of VYVE is grounded in peer-reviewed research and the most current UK workplace data available. Here is the evidence that shapes everything we build.</p>
  </div>
</section>

<!-- THREE TIER MODEL -->
<section class="section">
  <div class="container">
    <div class="section__header">
      <span class="label">The Three-Tier Evidence Model</span>
      <h2 class="headline">The problem. The perception. The proof.</h2>
      <p class="lead">Our evidence base is structured around three tiers — establishing the scale of the problem, understanding what employees think and need, and proving what happens when they get it.</p>
    </div>
    <div class="cards cards--3" style="gap:24px">
      <div class="card card--dark fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z"/><line x1="12" y1="9" x2="12" y2="13"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg></div>
        <div class="card__label">Tier 1</div>
        <h3 class="card__title">The Scale of the Crisis</h3>
        <p class="card__body">Independent data from CIPD, ONS, and Deloitte confirms the UK workplace wellbeing crisis is structural, urgent, and costing employers billions. This is the foundation of the VYVE case.</p>
      </div>
      <div class="card card--teal fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87M16 3.13a4 4 0 0 1 0 7.75"/></svg></div>
        <div class="card__label">Tier 2</div>
        <h3 class="card__title">User Perception & Needs</h3>
        <p class="card__body">Research reveals what employees actually value: personalisation, community, shared purpose, and measurable progress. Generic apps and reactive EAPs fail on every dimension.</p>
      </div>
      <div class="card fade-up" style="border-color:var(--teal)">
        <div class="card__icon"><svg viewBox="0 0 24 24"><polyline points="22,12 18,12 15,21 9,3 6,12 2,12"/></svg></div>
        <div class="card__label">Tier 3</div>
        <h3 class="card__title">Behavioural Evidence</h3>
        <p class="card__body">What actually happens when people get access to good, community-powered wellbeing support — engagement rates, programme completion, ROI outcomes, and long-term behaviour change.</p>
      </div>
    </div>
  </div>
</section>

<!-- FULL EVIDENCE TABLE -->
<section class="section section--light">
  <div class="container">
    <div class="section__header">
      <span class="label">Tier 1 — The Crisis</span>
      <h2 class="headline">The UK workplace wellbeing data</h2>
    </div>
    <div style="overflow-x:auto">
    <table class="data-table" style="width:100%">
      <thead><tr><th>Source</th><th>Finding</th><th>Implication for VYVE</th><th>Year</th></tr></thead>
      <tbody>
        <tr><td class="highlight">CIPD</td><td>9.4 days average absence per employee — highest in 12 years</td><td>Record absence = record opportunity for proactive intervention</td><td>2025</td></tr>
        <tr><td class="highlight">CIPD</td><td>41% cite mental ill-health as their top cause of long-term absence</td><td>Mental health is the primary battlefield — VYVE addresses this directly</td><td>2025</td></tr>
        <tr><td class="highlight">CIPD</td><td>37% of employers are purely reactive — no proactive wellbeing strategy</td><td>63% of the market is underserved — a clear commercial opportunity</td><td>2025</td></tr>
        <tr><td class="highlight">CIPD</td><td>Only 29% of employers train managers to support mental health</td><td>VYVE's manager toolkit addresses a critical structural gap</td><td>2025</td></tr>
        <tr><td class="highlight">CIPD</td><td>2.8 million people economically inactive due to long-term sickness</td><td>Scale of the problem extends beyond individual employers</td><td>2025</td></tr>
        <tr><td class="highlight">ONS</td><td>148.9 million working days lost to sickness in 2024</td><td>Equivalent to every UK worker losing 4.4 days — a national productivity crisis</td><td>2024</td></tr>
        <tr><td class="highlight">ONS</td><td>Long-term sickness = 32.2% of all economic inactivity</td><td>Prevention is economically critical — not just compassionate</td><td>2024</td></tr>
        <tr><td class="highlight">Deloitte</td><td>Poor mental health costs UK employers £51 billion annually</td><td>VYVE's ROI case is straightforward — even 1% improvement = £510m saved</td><td>2024</td></tr>
        <tr><td class="highlight">Deloitte</td><td>Presenteeism costs UK employers £24 billion per year</td><td>Presenteeism is invisible — only data-driven platforms like VYVE can address it</td><td>2024</td></tr>
        <tr><td class="highlight">Deloitte</td><td>£4.70 returned per £1 invested in mental health at work</td><td>Wellbeing investment is not a cost — it's among the highest-ROI activities available</td><td>2024</td></tr>
        <tr><td class="highlight">Deloitte</td><td>Proactive/universal interventions return £5.30 per £1 vs £4.10 for reactive</td><td>VYVE's proactive architecture delivers 29% better ROI than reactive alternatives</td><td>2024</td></tr>
      </tbody>
    </table>
    </div>
  </div>
</section>

<section class="section">
  <div class="container">
    <div class="section__header">
      <span class="label">Tier 2 & 3 — What Works</span>
      <h2 class="headline">The behavioural science behind VYVE</h2>
    </div>
    <div style="overflow-x:auto">
    <table class="data-table" style="width:100%">
      <thead><tr><th>Source</th><th>Finding</th><th>How VYVE Uses This</th></tr></thead>
      <tbody>
        <tr><td class="highlight">McKinsey Health Institute (2023)</td><td>Digital health platforms with community features generate 4x higher long-term engagement vs solo apps</td><td>Community sub-groups and shared challenges are core to VYVE's architecture</td></tr>
        <tr><td class="highlight">Journal of Sport & Exercise Psychology (2023)</td><td>Group-based physical activity shows 26% higher adherence than individual programmes</td><td>VYVE sub-groups enable group exercise communities with shared training plans</td></tr>
        <tr><td class="highlight">Beauchamp et al. (2020)</td><td>Belonging to an exercise group strengthens exercise identity — the factor most predictive of long-term behaviour change</td><td>Sub-groups are designed to foster belonging and identity, not just accountability</td></tr>
        <tr><td class="highlight">BetterUp (2024)</td><td>Employees who set goals within a community context are 2.3x more likely to complete a programme</td><td>All VYVE challenges can be set with community and prosocial context</td></tr>
        <tr><td class="highlight">Grant & Berry (2011)</td><td>Intrinsic prosocial motivation enhances persistence and performance — outperforming purely self-interested motivation</td><td>VYVE's charity mechanic creates a prosocial layer on every health behaviour</td></tr>
        <tr><td class="highlight">Batson (2011)</td><td>Co-existence of self-interest and altruistic motivation is normal and healthy — most sustainable combination</td><td>VYVE is intentionally dual-motivational: personal benefit AND social contribution</td></tr>
        <tr><td class="highlight">CIPD (2025)</td><td>54% of employees using wellbeing apps reported improved sleep or stress management</td><td>Validated by the same evidence base that confirms the absence crisis</td></tr>
        <tr><td class="highlight">CIPD (2025)</td><td>39% of employees reported improved productivity after accessing mental health support</td><td>VYVE's ROI model is calibrated against this evidence</td></tr>
        <tr><td class="highlight">Oja et al. (2015)</td><td>Running clubs and exercise communities linked to improved social cohesion, belonging, and mental wellbeing</td><td>VYVE in-person events and sub-group runs are grounded in this evidence</td></tr>
      </tbody>
    </table>
    </div>
  </div>
</section>

<!-- CLINICAL FRAMEWORK -->
<section class="section section--light">
  <div class="container">
    <div class="section__header">
      <span class="label">Our Clinical Framework</span>
      <h2 class="headline">Built on evidence-based therapeutic approaches</h2>
    </div>
    <div class="cards cards--3" style="gap:24px">
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M9 3H5a2 2 0 0 0-2 2v4m6-6h10a2 2 0 0 1 2 2v4M9 3v18m0 0h10a2 2 0 0 0 2-2V9M9 21H5a2 2 0 0 1-2-2V9m0 0h18"/></svg></div>
        <h3 class="card__title">Cognitive Behavioural Therapy (CBT)</h3>
        <p class="card__body">CBT is the gold-standard, NICE-recommended approach for anxiety, depression, and stress. VYVE's NOVA and RIVER personas are informed by CBT principles — cognitive reframing, thought records, and behavioural experiments delivered in accessible, daily formats.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg></div>
        <h3 class="card__title">Acceptance & Commitment Therapy (ACT)</h3>
        <p class="card__body">ACT focuses on psychological flexibility — accepting difficult thoughts and feelings while committing to values-driven action. VYVE's SPARK persona draws heavily on ACT for motivation, purpose, and long-term behaviour change.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/></svg></div>
        <h3 class="card__title">Trauma-Informed Care</h3>
        <p class="card__body">HAVEN, our crisis and grief support pathway, is built on trauma-informed principles — safety, trustworthiness, choice, collaboration, and empowerment. Seamless escalation pathways to qualified therapists are built into the architecture.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M12 22s-8-4.5-8-11.8A8 8 0 0 1 12 2a8 8 0 0 1 8 8.2c0 7.3-8 11.8-8 11.8z"/></svg></div>
        <h3 class="card__title">Behaviour Change Science</h3>
        <p class="card__body">VYVE's habit-formation architecture draws on BJ Fogg's Tiny Habits framework, implementation intentions research, and the COM-B model of behaviour change — ensuring that engagement becomes habitual, not effortful.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87M16 3.13a4 4 0 0 1 0 7.75"/></svg></div>
        <h3 class="card__title">Social Identity Theory</h3>
        <p class="card__body">Tajfel & Turner's social identity theory explains why community matters: belonging to a group creates identity, and identity drives behaviour. VYVE's sub-group architecture is designed to create genuine health identities — not just temporary challenges.</p>
      </div>
      <div class="card fade-up">
        <div class="card__icon"><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg></div>
        <h3 class="card__title">Positive Psychology</h3>
        <p class="card__body">Seligman's PERMA model — Positive Emotion, Engagement, Relationships, Meaning, Achievement — is embedded in VYVE's programme design. Wellbeing is not the absence of illness; it is the presence of flourishing.</p>
      </div>
    </div>
  </div>
</section>

<!-- CALLOUT -->
<section class="section section--dark">
  <div class="container container--narrow">
    <div class="callout">
      <p class="callout__quote">"The most effective wellbeing interventions combine personalisation, community belonging, prosocial purpose, and evidence-based clinical frameworks. VYVE is the first platform to bring all of these together in a single, accessible, always-on product."</p>
      <p class="callout__attr">— VYVE Health, Future State Vision v3 (2026)</p>
    </div>
  </div>
</section>

<section class="cta-section">
  <div class="container">
    <h2 class="display" style="color:white;margin-bottom:20px">See the evidence in action.</h2>
    <p class="lead" style="color:var(--teal-md);margin-bottom:36px;max-width:520px;margin-left:auto;margin-right:auto">Book a demo and we'll walk you through how VYVE's evidence-based design translates into measurable outcomes for your organisation.</p>
    <div class="cta-section__btns">
      <a href="employers.html#demo" class="btn btn--white btn--lg">Book a Demo</a>
      <a href="about.html" class="btn btn--outline btn--lg" style="border-color:rgba(255,255,255,0.5);color:white">Our Story →</a>
    </div>
  </div>
</section>
` + FOOTER();

// ══════════════════════════════════════════════════════════════════════════
// PAGE 5: ABOUT
// ══════════════════════════════════════════════════════════════════════════
const ABOUT = HEAD('About VYVE Health', 'VYVE Health — our story, vision, and mission to become the world\'s most complete proactive wellbeing platform.') + NAV('about') + `

<div class="breadcrumb">
  <div class="container">
    <div class="breadcrumb__inner">
      <a href="index.html">Home</a><span class="breadcrumb__sep">/</span>
      <span>About</span>
    </div>
  </div>
</div>

<section class="hero hero--about" style="padding:110px 0 90px">
  <div class="container">
    <div class="hero__grid">
      <div>
        <span class="label" style="color:var(--teal-md)">About VYVE Health</span>
        <h1 class="display" style="color:white;margin-bottom:24px">From platform<br>to movement.</h1>
        <p class="lead" style="color:rgba(255,255,255,0.85);margin-bottom:36px;max-width:540px">VYVE was built on a simple premise: good health at work shouldn't be a privilege, a policy, or a postcode lottery. It should be the default. We're building the platform that makes that possible.</p>
      </div>
      <div class="hero__image fade-in">
        <img src="images/story.jpg" alt="The VYVE story" loading="eager"/>
      </div>
    </div>
  </div>
</section>

<!-- VISION -->
<section class="section">
  <div class="container">
    <div class="two-col">
      <div>
        <span class="label">Our Vision</span>
        <h2 class="subhead" style="color:var(--dark);margin-bottom:16px">We're not building another wellbeing app. We're building a movement.</h2>
        <p class="lead" style="margin-bottom:20px">The UK workplace wellbeing crisis is not a niche problem. It costs employers £51 billion annually. It has stolen 148.9 million working days. It has pushed 2.8 million people out of the workforce entirely. And 37% of employers still have no proactive strategy to address it.</p>
        <p style="color:var(--grey);font-size:0.95rem;line-height:1.75;margin-bottom:20px">VYVE was founded to fix this. Not by adding another EAP to the pile. Not with a meditation app and a gym discount. But with a complete, intelligence-driven, community-powered platform that addresses the whole person — and gives organisations the evidence to justify and demonstrate ongoing investment.</p>
        <p style="color:var(--grey);font-size:0.95rem;line-height:1.75;margin-bottom:28px">Our north star: make good health the default for every working person in the UK. Then the world.</p>
      </div>
      <div class="two-col__image">
        <img src="images/hero.jpg" alt="The VYVE vision" loading="lazy"/>
      </div>
    </div>
  </div>
</section>

<!-- VALUES -->
<section class="section section--light">
  <div class="container">
    <div class="section__header">
      <span class="label">What We Stand For</span>
      <h2 class="headline">Our principles are non-negotiable.</h2>
    </div>
    <div class="cards cards--2" style="gap:24px">
      <div class="card fade-up"><div class="card__icon"><svg viewBox="0 0 24 24"><path d="M9 3H5a2 2 0 0 0-2 2v4m6-6h10a2 2 0 0 1 2 2v4M9 3v18m0 0h10a2 2 0 0 0 2-2V9M9 21H5a2 2 0 0 1-2-2V9m0 0h18"/></svg></div><div class="card__label">Principle 1</div><h3 class="card__title">Evidence Over Hype</h3><p class="card__body">Every feature VYVE builds is grounded in peer-reviewed research, clinical evidence, and real-world outcome data. We don't promise what we can't prove. We don't measure what we can't improve.</p></div>
      <div class="card fade-up"><div class="card__icon"><svg viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87M16 3.13a4 4 0 0 1 0 7.75"/></svg></div><div class="card__label">Principle 2</div><h3 class="card__title">Community is the Product</h3><p class="card__body">Technology is the vehicle. Community is the engine. The most powerful wellbeing outcomes come from belonging — to a group, a purpose, a shared identity. VYVE is built around this truth.</p></div>
      <div class="card fade-up"><div class="card__icon"><svg viewBox="0 0 24 24"><path d="M12 22s-8-4.5-8-11.8A8 8 0 0 1 12 2a8 8 0 0 1 8 8.2c0 7.3-8 11.8-8 11.8z"/></svg></div><div class="card__label">Principle 3</div><h3 class="card__title">Health with Purpose</h3><p class="card__body">Individual health goals are powerful. Health goals connected to something larger are transformative. VYVE's charity mechanic ensures that every step, every session, every win — contributes to a world beyond the individual.</p></div>
      <div class="card fade-up"><div class="card__icon"><svg viewBox="0 0 24 24"><path d="M12 2L2 7l10 5 10-5-10-5z"/><path d="M2 17l10 5 10-5"/><path d="M2 12l10 5 10-5"/></svg></div><div class="card__label">Principle 4</div><h3 class="card__title">Proactive, Always</h3><p class="card__body">Reactive wellbeing — treating the crisis after it arrives — is insufficient and inefficient. VYVE is built from the ground up to prevent, predict, and act before problems escalate. Proactive is not a mode. It's our architecture.</p></div>
    </div>
  </div>
</section>

<!-- ROADMAP -->
<section class="section" id="roadmap">
  <div class="container">
    <div class="section__header">
      <span class="label">Our Roadmap</span>
      <h2 class="headline">Four phases to end-state.</h2>
      <p class="lead">VYVE's evolution follows a disciplined, evidence-gated roadmap. Each phase must meet specific unlock criteria before the next begins — ensuring quality, safety, and commercial sustainability at every stage.</p>
    </div>
    <div style="display:flex;flex-direction:column;gap:24px">
      ${[
        ["V1","v1","Foundation","Now — Q3 2026","We are here","Building the core product, proving the model, onboarding pilot employers, and capturing the data that will inform V2. The V1 platform is commercially deployable today — a full native app with PAD AI, employer dashboard, charity mechanic, community groups, and 10+ wellbeing programmes.",
          ["5+ pilot employer clients onboarded","£150k+ ARR achieved","3+ months engagement data captured","Charity mechanic operational","NPS >40"]],
        ["V2","v2","Expansion","Q4 2026 — Q2 2027","Coming next","Deepening the community layer, adding HRIS integrations and wearable sync, launching the therapy marketplace, onboarding ambassadors, and beginning the merch journey. V2 transforms VYVE from a platform to an ecosystem.",
          ["25+ employer clients","£600k+ ARR","HRIS integrations live","Therapy marketplace operational","ISO 27001 achieved"]],
        ["V3","v3","Deepening","Q3 2027 — Q4 2028","The intelligence phase","Our proprietary AI model replaces third-party AI. Cross-company communities emerge. CPD-accredited programmes launch. Health retreats begin. VYVE becomes an intelligence layer embedded in organisational infrastructure.",
          ["100+ employer clients","£3m+ ARR","Proprietary VYVE AI in production","Cross-company communities live","Series A funding secured"]],
        ["V4","v4","End State","2029+","The movement","VYVE at full scale. A category-defining UK platform with consumer brand alongside B2B core. International expansion. Clinical-grade AI tools. VYVE Foundation making £1m+ in annual charitable donations. The movement is real.",
          ["500+ employer clients","£15m+ ARR","Consumer brand revenue stream","International markets live","VYVE Foundation established"]],
      ].map(([v,cls,title,date,badge,desc,crit]) => `
      <div style="background:var(--light);border-radius:16px;padding:36px;border:1px solid var(--border)">
        <div style="display:flex;gap:20px;align-items:flex-start;flex-wrap:wrap">
          <div style="min-width:120px">
            <span class="phase__tag phase ${cls}">${v} — ${title}</span>
            <div style="font-size:0.8rem;color:var(--grey);margin-top:8px">${date}</div>
            <span class="tag tag--teal" style="margin-top:8px;display:inline-block">${badge}</span>
          </div>
          <div style="flex:1">
            <p style="color:var(--charcoal);font-size:0.95rem;line-height:1.75;margin-bottom:16px">${desc}</p>
            <div style="display:flex;gap:8px;flex-wrap:wrap">
              ${crit.map(c => `<span class="tag tag--teal" style="font-size:0.75rem">${c}</span>`).join('')}
            </div>
          </div>
        </div>
      </div>`).join('')}
    </div>
  </div>
</section>

<!-- MERCH / MOVEMENT -->
<section class="section section--light">
  <div class="container">
    <div class="two-col">
      <div>
        <span class="label">The VYVE Movement</span>
        <h2 class="subhead" style="color:var(--dark);margin-bottom:16px">Becoming the next Gymshark.</h2>
        <p class="lead" style="margin-bottom:20px">Gymshark built a £1 billion brand not by selling gym wear — but by building a community that made fitness a social identity. By 2024, Gymshark generated £607 million in revenue, driven by community, creators, and a movement that made their customers advocates.</p>
        <p style="color:var(--grey);font-size:0.95rem;line-height:1.75;margin-bottom:20px">VYVE has the same infrastructure: a captive, engaged community built around shared health identity, purpose, and progress. Branded merchandise is the physical manifestation of that identity — and a significant commercial opportunity.</p>
        <p style="color:var(--grey);font-size:0.95rem;line-height:1.75;margin-bottom:28px">In Phase 2, VYVE launches a partner-model merch range. In Phase 3, VYVE launches its own sub-brand. Achievement-unlocked products, ambassador collections, limited campaign drops — building the next great health lifestyle brand.</p>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:16px">
          <div style="background:var(--teal-xxl);border-radius:10px;padding:20px;text-align:center"><div style="font-size:1.6rem;font-weight:700;color:var(--teal)">£607m</div><div style="font-size:0.8rem;color:var(--grey);margin-top:4px">Gymshark revenue FY24</div></div>
          <div style="background:var(--teal-xxl);border-radius:10px;padding:20px;text-align:center"><div style="font-size:1.6rem;font-weight:700;color:var(--teal)">65.7m</div><div style="font-size:0.8rem;color:var(--grey);margin-top:4px">Engagements on #Gymshark66 campaign</div></div>
        </div>
      </div>
      <div class="two-col__image">
        <img src="images/app-showcase.jpg" alt="VYVE merch and movement" loading="lazy"/>
      </div>
    </div>
  </div>
</section>

<!-- FINAL QUOTE -->
<section class="section section--dark">
  <div class="container container--narrow">
    <div class="callout">
      <p class="callout__quote">"Every step you take makes someone's life better. Every employer who invests in VYVE invests in a future where work and health are not in conflict. That's not a product vision. That's a movement."</p>
      <p class="callout__attr">— VYVE Health Founding Vision</p>
    </div>
  </div>
</section>

<section class="cta-section">
  <div class="container">
    <h2 class="display" style="color:white;margin-bottom:20px">Be part of what's next.</h2>
    <p class="lead" style="color:var(--teal-md);margin-bottom:36px;max-width:520px;margin-left:auto;margin-right:auto">Whether you want to partner, invest, join the team, or simply bring VYVE to your organisation — we want to hear from you.</p>
    <div class="cta-section__btns">
      <a href="employers.html#demo" class="btn btn--white btn--lg">Partner with VYVE</a>
      <a href="mailto:hello@vyvehealth.co.uk" class="btn btn--outline btn--lg" style="border-color:rgba(255,255,255,0.5);color:white">Get in Touch</a>
    </div>
  </div>
</section>
` + FOOTER();

// ── Write all files ────────────────────────────────────────────────────────
const pages = [
  ['index.html', HOME],
  ['employers.html', EMPLOYERS],
  ['individuals.html', INDIVIDUALS],
  ['science.html', SCIENCE],
  ['about.html', ABOUT],
];
pages.forEach(([name, html]) => {
  fs.writeFileSync(path.join(OUT, name), html);
  console.log('Written:', name, `(${(html.length/1024).toFixed(1)}KB)`);
});
console.log('Done!');
