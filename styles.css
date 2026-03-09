/* ═══════════════════════════════════════════════════════
   VYVE HEALTH — Global Stylesheet
   Brand: Teal #1B7878 | Dark #0D2B2B | White #FFFFFF
═══════════════════════════════════════════════════════ */

:root {
  --teal:      #1B7878;
  --teal-lt:   #4DAAAA;
  --teal-md:   #B2DEDE;
  --teal-xl:   #E0F2F2;
  --teal-xxl:  #F0FAFA;
  --dark:      #0D2B2B;
  --charcoal:  #1E293B;
  --grey:      #64748B;
  --grey-lt:   #94A3B8;
  --border:    #E2EEF0;
  --light:     #F4FAFA;
  --white:     #FFFFFF;

  --font-head: 'Playfair Display', Georgia, serif;
  --font-body: 'Inter', -apple-system, sans-serif;

  --radius:    12px;
  --radius-lg: 20px;
  --shadow:    0 4px 24px rgba(11,43,43,0.10);
  --shadow-lg: 0 12px 48px rgba(11,43,43,0.16);
  --transition: all 0.3s cubic-bezier(0.4,0,0.2,1);
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; font-size: 16px; }

body {
  font-family: var(--font-body);
  color: var(--charcoal);
  background: var(--white);
  line-height: 1.7;
  -webkit-font-smoothing: antialiased;
}

img { max-width: 100%; display: block; }
a  { color: inherit; text-decoration: none; }
ul { list-style: none; }

/* ── Layout ─────────────────────────────────────────── */
.container { max-width: 1180px; margin: 0 auto; padding: 0 28px; }
.container--narrow { max-width: 820px; margin: 0 auto; padding: 0 28px; }

/* ── Typography ─────────────────────────────────────── */
.display { font-family: var(--font-head); font-size: clamp(2.4rem,5vw,4rem); line-height: 1.15; font-weight: 700; letter-spacing: -0.02em; }
.headline { font-family: var(--font-head); font-size: clamp(1.8rem,3.5vw,2.8rem); line-height: 1.2; font-weight: 700; }
.subhead  { font-family: var(--font-head); font-size: clamp(1.3rem,2.5vw,1.8rem); line-height: 1.3; font-weight: 600; }
.lead     { font-size: clamp(1rem,1.5vw,1.2rem); line-height: 1.75; color: var(--grey); }
.label    { font-size: 0.75rem; font-weight: 700; letter-spacing: 0.12em; text-transform: uppercase; color: var(--teal-lt); }

/* ── Buttons ────────────────────────────────────────── */
.btn {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 14px 28px; border-radius: 8px;
  font-size: 0.95rem; font-weight: 600; cursor: pointer;
  transition: var(--transition); white-space: nowrap; border: 2px solid transparent;
}
.btn--primary   { background: var(--teal); color: var(--white); }
.btn--primary:hover { background: #155f5f; transform: translateY(-1px); box-shadow: var(--shadow); }
.btn--outline   { border-color: var(--teal); color: var(--teal); background: transparent; }
.btn--outline:hover { background: var(--teal-xxl); }
.btn--white     { background: var(--white); color: var(--teal); }
.btn--white:hover { background: var(--teal-xl); }
.btn--dark      { background: var(--dark); color: var(--white); }
.btn--dark:hover { background: #1a4040; transform: translateY(-1px); box-shadow: var(--shadow); }
.btn--lg { padding: 18px 36px; font-size: 1.05rem; border-radius: 10px; }
.btn svg { width: 18px; height: 18px; flex-shrink: 0; }

/* ── Navigation ─────────────────────────────────────── */
.nav {
  position: sticky; top: 0; z-index: 100;
  background: rgba(255,255,255,0.97);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid var(--border);
}
.nav__inner {
  display: flex; align-items: center; justify-content: space-between;
  padding: 0 28px; max-width: 1180px; margin: 0 auto; height: 72px;
}
.nav__logo { display: flex; align-items: center; gap: 10px; }
.nav__logo-mark {
  width: 36px; height: 36px; background: var(--teal); border-radius: 8px;
  display: flex; align-items: center; justify-content: center;
}
.nav__logo-mark svg { width: 20px; height: 20px; fill: white; }
.nav__logo-text { font-family: var(--font-head); font-size: 1.4rem; font-weight: 700; color: var(--dark); }
.nav__logo-text span { color: var(--teal); }
.nav__links { display: flex; align-items: center; gap: 6px; }
.nav__link {
  padding: 8px 14px; border-radius: 6px; font-size: 0.9rem; font-weight: 500;
  color: var(--charcoal); transition: var(--transition);
}
.nav__link:hover { background: var(--teal-xl); color: var(--teal); }
.nav__link.active { color: var(--teal); background: var(--teal-xxl); }
.nav__link.employer { color: var(--teal); font-weight: 600; }
.nav__link.individual { color: var(--charcoal); font-weight: 600; }
.nav__cta { margin-left: 8px; }
.nav__mobile-btn { display: none; background: none; border: none; cursor: pointer; padding: 8px; }
.nav__mobile-btn svg { width: 24px; height: 24px; stroke: var(--dark); fill: none; stroke-width: 2; }

/* ── Page Hero Variants ─────────────────────────────── */
.hero { padding: 100px 0 80px; }
.hero--home { background: linear-gradient(135deg, var(--dark) 0%, #0f3838 60%, var(--teal) 100%); }
.hero--employer { background: linear-gradient(135deg, var(--dark) 0%, #0a2828 50%, #1a5050 100%); }
.hero--individual { background: linear-gradient(135deg, #0f3535 0%, var(--teal) 60%, #2d9090 100%); }
.hero--about { background: linear-gradient(135deg, var(--dark) 0%, #0e3030 70%, var(--teal) 100%); }

.hero .label { margin-bottom: 20px; display: block; color: var(--teal-md); }
.hero .display { color: var(--white); margin-bottom: 24px; }
.hero .lead { color: rgba(255,255,255,0.8); margin-bottom: 36px; max-width: 580px; }

.hero__btns { display: flex; gap: 14px; flex-wrap: wrap; }
.hero__grid { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center; }
.hero__image { border-radius: var(--radius-lg); overflow: hidden; box-shadow: var(--shadow-lg); }
.hero__image img { width: 100%; height: 380px; object-fit: cover; }

/* ── Stat Strips ────────────────────────────────────── */
.stat-strip { background: var(--teal); padding: 28px 0; }
.stat-strip__inner { display: flex; justify-content: space-around; align-items: center; flex-wrap: wrap; gap: 20px; }
.stat-item { text-align: center; }
.stat-item__value { font-family: var(--font-head); font-size: 2.2rem; font-weight: 700; color: var(--white); line-height: 1; }
.stat-item__label { font-size: 0.82rem; color: var(--teal-md); margin-top: 4px; font-weight: 500; }
.stat-item__source { font-size: 0.7rem; color: rgba(255,255,255,0.5); margin-top: 2px; }

/* ── Sections ───────────────────────────────────────── */
.section { padding: 90px 0; }
.section--light { background: var(--light); }
.section--teal-xl { background: var(--teal-xxl); }
.section--dark { background: var(--dark); }
.section__header { text-align: center; margin-bottom: 56px; }
.section__header .label { display: block; margin-bottom: 14px; }
.section__header .headline { color: var(--dark); margin-bottom: 16px; }
.section__header .lead { max-width: 640px; margin: 0 auto; }
.section--dark .section__header .headline { color: var(--white); }
.section--dark .section__header .lead { color: var(--teal-md); }

/* ── Cards ──────────────────────────────────────────── */
.cards { display: grid; gap: 24px; }
.cards--2 { grid-template-columns: repeat(2, 1fr); }
.cards--3 { grid-template-columns: repeat(3, 1fr); }
.cards--4 { grid-template-columns: repeat(4, 1fr); }

.card {
  background: var(--white); border-radius: var(--radius-lg);
  padding: 32px; border: 1px solid var(--border);
  transition: var(--transition);
}
.card:hover { transform: translateY(-4px); box-shadow: var(--shadow-lg); border-color: var(--teal-md); }
.card__icon {
  width: 52px; height: 52px; border-radius: 12px;
  background: var(--teal-xl); display: flex; align-items: center; justify-content: center;
  margin-bottom: 20px; flex-shrink: 0;
}
.card__icon svg { width: 26px; height: 26px; stroke: var(--teal); fill: none; stroke-width: 2; }
.card__label { font-size: 0.72rem; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; color: var(--teal-lt); margin-bottom: 8px; }
.card__title { font-family: var(--font-head); font-size: 1.2rem; font-weight: 700; color: var(--dark); margin-bottom: 12px; line-height: 1.3; }
.card__body  { font-size: 0.92rem; color: var(--grey); line-height: 1.7; }
.card--teal  { background: var(--teal); border-color: var(--teal); }
.card--teal .card__title { color: var(--white); }
.card--teal .card__body  { color: var(--teal-md); }
.card--teal .card__icon  { background: rgba(255,255,255,0.15); }
.card--teal .card__icon svg { stroke: var(--white); }
.card--dark  { background: var(--dark); border-color: var(--dark); }
.card--dark .card__title { color: var(--white); }
.card--dark .card__body  { color: var(--teal-md); }
.card--dark .card__icon  { background: rgba(255,255,255,0.1); }
.card--dark .card__icon svg { stroke: var(--teal-lt); }

/* ── Promise Blocks ─────────────────────────────────── */
.promise { display: flex; gap: 20px; align-items: flex-start; padding: 28px; background: var(--white); border-radius: var(--radius); border: 1px solid var(--border); transition: var(--transition); }
.promise:hover { border-color: var(--teal); box-shadow: var(--shadow); }
.promise__num { width: 44px; height: 44px; min-width: 44px; border-radius: 10px; background: var(--teal); color: var(--white); font-weight: 700; font-size: 1rem; display: flex; align-items: center; justify-content: center; }
.promise__title { font-weight: 700; color: var(--dark); font-size: 1.05rem; margin-bottom: 6px; }
.promise__body  { font-size: 0.9rem; color: var(--grey); line-height: 1.65; }
.promise__tag   { display: inline-block; margin-top: 10px; padding: 4px 10px; border-radius: 20px; background: var(--teal-xl); color: var(--teal); font-size: 0.75rem; font-weight: 600; }

/* ── Two-col layouts ────────────────────────────────── */
.two-col { display: grid; grid-template-columns: 1fr 1fr; gap: 72px; align-items: center; }
.two-col--flip .two-col__image { order: -1; }
.two-col__image { border-radius: var(--radius-lg); overflow: hidden; box-shadow: var(--shadow-lg); }
.two-col__image img { width: 100%; height: 400px; object-fit: cover; }
.two-col .label { display: block; margin-bottom: 14px; }
.two-col .subhead { color: var(--dark); margin-bottom: 16px; }
.two-col .lead { margin-bottom: 24px; }

/* ── Persona Cards ──────────────────────────────────── */
.persona {
  border-radius: var(--radius-lg); padding: 32px;
  border: 2px solid var(--border); transition: var(--transition);
  position: relative; overflow: hidden;
}
.persona::before {
  content: ''; position: absolute; top: 0; left: 0; right: 0; height: 4px;
}
.persona:hover { transform: translateY(-4px); box-shadow: var(--shadow-lg); }
.persona.nova::before  { background: #E74C3C; }
.persona.river::before { background: #3498DB; }
.persona.spark::before { background: #F39C12; }
.persona.sage::before  { background: #27AE60; }
.persona.haven::before { background: #8E44AD; }
.persona__emoji { font-size: 2.4rem; margin-bottom: 14px; }
.persona__name  { font-family: var(--font-head); font-size: 1.5rem; font-weight: 700; margin-bottom: 4px; }
.persona.nova  .persona__name { color: #E74C3C; }
.persona.river .persona__name { color: #3498DB; }
.persona.spark .persona__name { color: #F39C12; }
.persona.sage  .persona__name { color: #27AE60; }
.persona.haven .persona__name { color: #8E44AD; }
.persona__tag  { font-size: 0.78rem; font-weight: 600; color: var(--grey); text-transform: uppercase; letter-spacing: 0.08em; margin-bottom: 14px; }
.persona__desc { font-size: 0.92rem; color: var(--charcoal); line-height: 1.7; }

/* ── Data Table ─────────────────────────────────────── */
.data-table { width: 100%; border-collapse: collapse; font-size: 0.9rem; }
.data-table th { background: var(--teal); color: var(--white); padding: 14px 18px; text-align: left; font-weight: 600; font-size: 0.85rem; }
.data-table td { padding: 13px 18px; border-bottom: 1px solid var(--border); vertical-align: top; }
.data-table tr:nth-child(even) td { background: var(--light); }
.data-table tr:hover td { background: var(--teal-xxl); }
.data-table .highlight { color: var(--teal); font-weight: 700; }
.data-table th:first-child { border-radius: 8px 0 0 0; }
.data-table th:last-child  { border-radius: 0 8px 0 0; }

/* ── ROI Block ──────────────────────────────────────── */
.roi-block {
  background: var(--dark); border-radius: var(--radius-lg); padding: 48px;
  display: grid; grid-template-columns: 1fr 1fr; gap: 40px; align-items: start;
}
.roi-block__stat { text-align: center; padding: 28px; background: rgba(255,255,255,0.06); border-radius: var(--radius); }
.roi-block__stat-value { font-family: var(--font-head); font-size: 3rem; font-weight: 700; color: var(--teal-lt); line-height: 1; }
.roi-block__stat-label { font-size: 0.9rem; color: var(--teal-md); margin-top: 8px; }
.roi-block__content .subhead { color: var(--white); margin-bottom: 16px; }
.roi-block__content p { color: var(--teal-md); font-size: 0.95rem; line-height: 1.75; }
.roi-stats { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; margin-top: 24px; }

/* ── Pillars Grid ───────────────────────────────────── */
.pillar {
  display: flex; gap: 16px; align-items: flex-start;
  padding: 20px; border-radius: var(--radius); background: var(--white);
  border: 1px solid var(--border); transition: var(--transition);
}
.pillar:hover { border-color: var(--teal); background: var(--teal-xxl); }
.pillar__num {
  min-width: 36px; height: 36px; background: var(--teal-xl);
  border-radius: 8px; display: flex; align-items: center; justify-content: center;
  font-weight: 700; font-size: 0.9rem; color: var(--teal);
}
.pillar__title { font-weight: 700; color: var(--dark); font-size: 0.95rem; margin-bottom: 4px; }
.pillar__desc  { font-size: 0.85rem; color: var(--grey); line-height: 1.6; }

/* ── Journey Steps ──────────────────────────────────── */
.journey { display: flex; flex-direction: column; gap: 0; }
.journey-step {
  display: grid; grid-template-columns: 56px 1fr; gap: 24px;
  position: relative; padding-bottom: 32px;
}
.journey-step:last-child { padding-bottom: 0; }
.journey-step__line {
  display: flex; flex-direction: column; align-items: center;
}
.journey-step__dot {
  width: 48px; height: 48px; border-radius: 50%; background: var(--teal);
  display: flex; align-items: center; justify-content: center;
  font-weight: 700; color: var(--white); font-size: 0.95rem; flex-shrink: 0;
}
.journey-step__connector {
  width: 2px; background: var(--teal-md); flex: 1; margin-top: 4px; min-height: 24px;
}
.journey-step:last-child .journey-step__connector { display: none; }
.journey-step__content { padding-top: 10px; }
.journey-step__title { font-weight: 700; color: var(--dark); font-size: 1.05rem; margin-bottom: 6px; }
.journey-step__body  { font-size: 0.9rem; color: var(--grey); line-height: 1.65; }

/* ── Charity block ──────────────────────────────────── */
.charity {
  background: var(--teal-xxl); border: 1px solid var(--teal-md);
  border-radius: var(--radius-lg); padding: 40px; text-align: center;
}
.charity__icon { font-size: 3rem; margin-bottom: 16px; }
.charity__title { font-family: var(--font-head); font-size: 1.6rem; color: var(--dark); margin-bottom: 12px; }
.charity__body  { color: var(--grey); max-width: 600px; margin: 0 auto 24px; }

/* ── Phase Roadmap ──────────────────────────────────── */
.phases { display: grid; grid-template-columns: repeat(4, 1fr); gap: 0; }
.phase {
  padding: 32px 24px; border: 1px solid var(--border);
  position: relative; transition: var(--transition);
}
.phase:first-child { border-radius: var(--radius) 0 0 var(--radius); }
.phase:last-child  { border-radius: 0 var(--radius) var(--radius) 0; }
.phase:hover { background: var(--teal-xxl); border-color: var(--teal); z-index: 1; }
.phase__tag  { display: inline-block; padding: 4px 12px; border-radius: 20px; font-size: 0.72rem; font-weight: 700; text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: 16px; }
.phase.v1 .phase__tag { background: var(--teal-xl); color: var(--teal); }
.phase.v2 .phase__tag { background: #FEF3C7; color: #92400E; }
.phase.v3 .phase__tag { background: #EDE9FE; color: #5B21B6; }
.phase.v4 .phase__tag { background: var(--dark); color: var(--teal-lt); }
.phase__title { font-family: var(--font-head); font-size: 1.2rem; color: var(--dark); margin-bottom: 6px; }
.phase__date  { font-size: 0.8rem; color: var(--teal); font-weight: 600; margin-bottom: 14px; }
.phase__list li { font-size: 0.85rem; color: var(--grey); margin-bottom: 6px; padding-left: 16px; position: relative; }
.phase__list li::before { content: '→'; position: absolute; left: 0; color: var(--teal-lt); font-size: 0.75rem; }

/* ── Quote / Callout ────────────────────────────────── */
.callout {
  background: var(--dark); border-radius: var(--radius-lg); padding: 48px;
  text-align: center; position: relative; overflow: hidden;
}
.callout::before {
  content: '"'; position: absolute; top: -20px; left: 30px;
  font-size: 14rem; color: rgba(27,120,120,0.15); font-family: Georgia, serif; line-height: 1;
}
.callout__quote { font-family: var(--font-head); font-size: clamp(1.1rem,2vw,1.5rem); color: var(--white); line-height: 1.6; position: relative; z-index: 1; }
.callout__attr  { margin-top: 20px; font-size: 0.85rem; color: var(--teal-md); }

/* ── Comparison table ───────────────────────────────── */
.compare { display: grid; grid-template-columns: 1fr 1fr; gap: 0; border-radius: var(--radius-lg); overflow: hidden; border: 1px solid var(--border); }
.compare__col { padding: 0; }
.compare__head { padding: 24px 28px; font-weight: 700; font-size: 1rem; }
.compare__head.old { background: #FEF2F2; color: #991B1B; }
.compare__head.new { background: var(--teal); color: var(--white); }
.compare__item { padding: 14px 28px; border-top: 1px solid var(--border); font-size: 0.9rem; display: flex; align-items: flex-start; gap: 10px; }
.compare__item.old { color: var(--charcoal); }
.compare__item.new { background: var(--teal-xxl); color: var(--dark); font-weight: 500; }
.compare__item svg { width: 18px; height: 18px; flex-shrink: 0; margin-top: 1px; }

/* ── Evidence pillars ───────────────────────────────── */
.evidence-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; }
.evidence-card {
  background: var(--white); border-radius: var(--radius); border: 1px solid var(--border);
  padding: 28px; transition: var(--transition);
}
.evidence-card:hover { border-color: var(--teal); }
.evidence-card__source { font-size: 0.72rem; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; color: var(--teal-lt); margin-bottom: 10px; }
.evidence-card__stat { font-family: var(--font-head); font-size: 2rem; font-weight: 700; color: var(--teal); margin-bottom: 8px; line-height: 1; }
.evidence-card__desc { font-size: 0.88rem; color: var(--grey); line-height: 1.6; }

/* ── CTA section ────────────────────────────────────── */
.cta-section { background: linear-gradient(135deg, var(--dark) 0%, #0f3838 100%); padding: 100px 0; text-align: center; }
.cta-section .display { color: var(--white); margin-bottom: 20px; }
.cta-section .lead { color: var(--teal-md); margin-bottom: 40px; max-width: 560px; margin-left: auto; margin-right: auto; }
.cta-section__btns { display: flex; justify-content: center; gap: 16px; flex-wrap: wrap; }
.cta-divider { display: flex; align-items: center; gap: 16px; margin: 16px 0; color: rgba(255,255,255,0.3); font-size: 0.85rem; }
.cta-divider::before, .cta-divider::after { content: ''; flex: 1; height: 1px; background: rgba(255,255,255,0.15); }

/* ── Footer ─────────────────────────────────────────── */
.footer { background: #071818; padding: 72px 0 36px; }
.footer__grid { display: grid; grid-template-columns: 2fr 1fr 1fr 1fr; gap: 48px; margin-bottom: 48px; }
.footer__brand .nav__logo-text { color: var(--white); font-size: 1.5rem; }
.footer__tagline { color: var(--grey-lt); font-size: 0.9rem; margin-top: 12px; line-height: 1.7; }
.footer__col-title { font-size: 0.75rem; font-weight: 700; letter-spacing: 0.12em; text-transform: uppercase; color: var(--teal-lt); margin-bottom: 16px; }
.footer__links li { margin-bottom: 10px; }
.footer__links a { color: var(--grey-lt); font-size: 0.9rem; transition: var(--transition); }
.footer__links a:hover { color: var(--teal-lt); }
.footer__bottom { border-top: 1px solid rgba(255,255,255,0.08); padding-top: 28px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 12px; }
.footer__copy { font-size: 0.82rem; color: var(--grey); }
.footer__certifications { display: flex; gap: 12px; }
.footer__cert { padding: 6px 12px; border: 1px solid rgba(255,255,255,0.12); border-radius: 6px; font-size: 0.72rem; font-weight: 600; color: var(--grey-lt); }

/* ── Breadcrumb ─────────────────────────────────────── */
.breadcrumb { padding: 12px 0; border-bottom: 1px solid var(--border); background: var(--white); }
.breadcrumb__inner { display: flex; gap: 8px; align-items: center; font-size: 0.82rem; color: var(--grey); }
.breadcrumb__inner a { color: var(--teal); transition: var(--transition); }
.breadcrumb__inner a:hover { color: var(--teal-lt); }
.breadcrumb__sep { color: var(--border); }

/* ── Tag ────────────────────────────────────────────── */
.tag { display: inline-block; padding: 5px 12px; border-radius: 20px; font-size: 0.78rem; font-weight: 600; }
.tag--teal     { background: var(--teal-xl); color: var(--teal); }
.tag--green    { background: #DCFCE7; color: #166534; }
.tag--amber    { background: #FEF3C7; color: #92400E; }
.tag--purple   { background: #EDE9FE; color: #5B21B6; }

/* ── Inline icon list ───────────────────────────────── */
.check-list { display: flex; flex-direction: column; gap: 12px; }
.check-list li { display: flex; gap: 12px; align-items: flex-start; font-size: 0.95rem; color: var(--charcoal); }
.check-list li::before { content: ''; width: 20px; height: 20px; min-width: 20px; background: var(--teal-xl); border-radius: 50%; background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%231B7878' stroke-width='2.5'%3E%3Cpolyline points='20,6 9,17 4,12'/%3E%3C/svg%3E"); background-size: 13px; background-position: center; background-repeat: no-repeat; margin-top: 2px; }

/* ── Animations ─────────────────────────────────────── */
.fade-up { opacity: 0; transform: translateY(24px); transition: opacity 0.6s ease, transform 0.6s ease; }
.fade-up.visible { opacity: 1; transform: translateY(0); }
.fade-in { opacity: 0; transition: opacity 0.7s ease; }
.fade-in.visible { opacity: 1; }

/* ── Responsive ─────────────────────────────────────── */
@media (max-width: 1024px) {
  .cards--4 { grid-template-columns: repeat(2, 1fr); }
  .phases { grid-template-columns: repeat(2, 1fr); }
  .footer__grid { grid-template-columns: 1fr 1fr; }
}
@media (max-width: 768px) {
  .hero { padding: 72px 0 60px; }
  .hero__grid, .two-col { grid-template-columns: 1fr; }
  .two-col__image { display: none; }
  .hero__image { display: none; }
  .cards--2, .cards--3 { grid-template-columns: 1fr; }
  .roi-block { grid-template-columns: 1fr; padding: 32px 24px; }
  .compare { grid-template-columns: 1fr; }
  .evidence-grid { grid-template-columns: 1fr; }
  .phases { grid-template-columns: 1fr; }
  .nav__links { display: none; }
  .nav__mobile-btn { display: flex; }
  .nav__cta { display: none; }
  .footer__grid { grid-template-columns: 1fr; gap: 32px; }
  .stat-strip__inner { gap: 28px; }
  .breadcrumb { display: none; }
  .section { padding: 64px 0; }
}
@media (max-width: 480px) {
  .display { font-size: 2rem; }
  .hero__btns { flex-direction: column; }
  .btn--lg { width: 100%; justify-content: center; }
}

/* ── Mobile nav open state ──────────────────────────── */
.nav.open .nav__links {
  display: flex; flex-direction: column;
  position: absolute; top: 72px; left: 0; right: 0;
  background: var(--white); border-bottom: 1px solid var(--border);
  padding: 16px 28px; gap: 4px; z-index: 99;
}
.nav.open .nav__cta { display: block; padding: 12px 28px 16px; border-top: 1px solid var(--border); position: absolute; bottom: 0; width: 100%; }
