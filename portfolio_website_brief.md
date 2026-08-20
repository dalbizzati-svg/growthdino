# Brief + Prompt para Claude Design — Portfolio de Dino Albizzati

Este documento tiene dos partes:
1. **Estructura del sitio** (revisada con los skills de `site-architecture`, `copywriting`, `cro`, `copy-editing`, `ai-seo`, `analytics`)
2. **Prompt final**, listo para pegar en Claude Design, para que genere el sitio en HTML/CSS autocontenido por página, sin build step, para hostear en un hosting gratis con dominio propio.

---

## PARTE 1 — Estructura propuesta (multi-página, como el Notion original)

Cambio pedido explícitamente: páginas dedicadas por case study, igual que la página de Notion (`axiomatic-ellipse-7b9.notion.site`), en vez de acordeón dentro de la home. Estructura final:

```
index.html                          (Home)
├── #about
├── #experience
├── #case-studies (cards con teaser, cada una linkea a su página)
├── #skills
└── #contact

case-studies/
├── passover-2026.html              (Case Study 1)
├── hanukkah-2026.html               (Case Study 2)
├── farmers-market.html              (Case Study 3)
└── super-bowl.html                  (Case Study 4)
```

- **Home** tiene un header sticky con nav (About / Experience / Case Studies / Skills / Contact) + CTA. La sección Case Studies muestra 4 cards (teaser + 1 stat destacado + botón "Read the full case study →") que linkean a su página dedicada.
- **Cada página de case study** repite el mismo header/footer (para no perder la navegación ni el CTA), tiene su propia URL compartible, su propio `<title>`, y su propio botón "← Back to all case studies" arriba y "Book a 15-Minute Intro Call" repetido al final.
- Esto es más fiel al Notion original (que sí tenía páginas propias) y mejor para compartir un caso puntual por link directo a un reclutador.

---

## PARTE 2 — Contenido de origen (Notion) — verificado página por página

Fui a cada página de case study dentro del Notion original y saqué el contenido completo, incluyendo narrativa que no estaba en la versión anterior de este brief (el pivot mid-campaña de Passover, y detalle del creative del Super Bowl). Uso esto como fuente para los prompts de cada página dedicada, más abajo.

### Mapeo de assets: Notion → carpeta local

| Case Study | Asset en Notion | Archivo local | Estado |
|---|---|---|---|
| Passover | Reel de video | `Ads/Passover/ZEITLINS_PASSOVER_REEL03.mp4` | ✅ encontrado |
| Passover | Ads estáticos (cold contacts, mid-campaign, remarketing) | `Ads/Passover/Square_03.jpg`, `Square_04_ad set 2.jpg`, `ads/Square_01.jpg`, `ads/Square_02.jpg`, `ads/IG STORY*.jpg` | ✅ encontrado |
| Passover | Señalética in-store | `Signs/passover_01.jpg`, `passover_02.jpg` | ✅ encontrado |
| Passover | A-frame sidewalk sign | `A-frame/A-FRAME PASSOVER.pdf` | ✅ encontrado |
| Passover | Website Pop Up | `Pop Up/desktop.jpg` + `Pop Up/mobile.jpg` | ✅ encontrado |
| Passover | Menú (PDF fuente) | `Menu/April 1–2 Menu.pdf` | ✅ encontrado (PDF, no la foto con manos) |
| Passover | Foto "manos sosteniendo el menú" | `Prints/passover_menu_hands_photo.jpeg` | ✅ descargado de Notion |
| Passover | Screenshots de email marketing (3) | `Emails/passover_email_1.jpg`, `passover_email_2.jpg`, `passover_email_3.jpg` | ✅ descargados de Notion |
| Hanukkah | Ads (cold contacts, mid-campaign, remarketing) | mismo patrón que Passover — revisar `Ads/HOLIDAYS_ADS/HOLIDAYS/` (sin confirmar que sea Hanukkah específicamente) | ⚠️ confirmar |
| Hanukkah | Email | `Emails/HANUKKAH.png`, `Emails/THE SHOFAR'S CALLING.png` | ✅ encontrado |
| Hanukkah | Website Pop Up | `Pop Up/desktop.jpg` + `Pop Up/mobile.jpg` (mismo asset reusado) | ✅ encontrado |
| Farmers Market | Tarjetas de incentivo (bagel + catering) | `Prints/CARDS_1.jpg`, `Card_02.jpg`, `Card 1_outlined_PRINT_BLEED_.pdf`, `Card 2_outlined_PRINT_BLEED_.pdf` | ✅ encontrado |
| Farmers Market | Video de mercado | `Social Media/We're back at the market...mp4` | ✅ encontrado |
| Farmers Market | A-frame de mercado | `A-frame/Zeitlin's Deli - A-frame for Winter Markets 24x36 in.jpg` | ✅ encontrado |
| Farmers Market | Señalética Bagel Fest | `Signs/Bagel Fest Letter Sized Sign copy.jpg` | ✅ encontrado |
| Farmers Market | Screenshot del flujo QR | — | ⚠️ no existe, no se capturó en su momento |
| Super Bowl | Carrusel de ads | `Ads/Superbowl/SUPERBOWL_ADS_carousel_01.jpg`, `_04.jpg`, `_05.jpg` | ✅ encontrado |
| Super Bowl | Video "Touchdown Ad" | `Ads/Superbowl/SuperBowl_TouchDownAd_V2.mp4` | ✅ encontrado |
| Super Bowl | Website Pop Up | `Pop Up/desktop.jpg` + `Pop Up/mobile.jpg` (mismo asset reusado) | ✅ encontrado |
| Super Bowl | Tarjeta de instrucciones de recalentado (8.5x5.5in) | `Prints/superbowl_reheating_instructions.jpg` | ✅ descargado de Notion |
| Super Bowl | Screenshots de email marketing | — | ⚠️ el bloque "Email Marketing" del Notion original reusa por error el mismo archivo que el email de Passover — no hay un screenshot real y distinto del Super Bowl. Usar `Emails/passover_email_1.jpg` como placeholder genérico de email, o dejar esa sección sin imagen |

**Antes de generar el sitio con Claude Design**, si querés que las páginas de case study tengan exactamente las mismas imágenes que el Notion (foto del menú, tarjeta de recalentado, screenshots de email), avisame y las bajo del Notion con el navegador — o me las pasás vos directo.

---

## PARTE 3 — Prompt para pegar en Claude Design

```
Quiero que generes un sitio web personal de portfolio multi-página (HTML/CSS autocontenido por página, sin frameworks externos, sin build step), listo para subir a un hosting gratis (GitHub Pages / Netlify / Vercel) con dominio propio. Debe verse profesional, con identidad visual propia (no un template genérico de "AI generated"), responsive, y no debería necesitar casi ningún ajuste manual después de generado.

Estructura de archivos:
- index.html (home)
- case-studies/passover-2026.html
- case-studies/hanukkah-2026.html
- case-studies/farmers-market.html
- case-studies/super-bowl.html

Todas las páginas comparten el mismo header sticky, footer, y sistema de diseño (misma paleta, tipografía, componentes).

## Quién soy y cómo me posiciono

Nombre: Dino Albizzati
Rol objetivo: Head of Marketing / Growth Marketing Manager, en startups y PyMEs (10–100 personas)
Positioning: Growth marketer con base sólida en copywriting senior — no un especialista de un solo canal, sino alguien que corre ads, escribe la copy, construye los flujos de email, lee la data con honestidad (incluso cuando algo no funciona) y reporta resultados directamente a la dirección. Fluido en inglés y español (nativo, Rioplatense), acostumbrado a operar remoto entre husos horarios.

Tono de la copy: resultados concretos antes que adjetivos. Sin sobreventa. Verdicts directos (ej: "esto funcionó, esto no, y esto es lo que cambié por eso").

## Identidad visual (dirección a proponer)

No uses el ángulo "deli/comida" del caso Zeitlin's como identidad visual del sitio entero — este es un portfolio personal de growth marketer/copywriter, no un sitio de restaurante. Proponé una identidad propia: paleta sobria y con carácter (evitar el genérico azul-violeta-degradé de SaaS), tipografía con personalidad (una serif o display con carácter para títulos + una sans limpia para cuerpo), micro-detalles que refuercen "datos + escritura" (por ejemplo tratamiento tipográfico fuerte para los números/stats, como si fueran titulares). El objetivo es que se vea como el sitio de alguien que entiende de diseño de conversión, no un genérico "mi portfolio". Las fotos de comida de Zeitlin's SÍ pueden aparecer dentro de las páginas de case study individuales (son evidencia real del trabajo), pero no como identidad visual del sitio entero.

## Navegación (header sticky, en todas las páginas)

Header fijo/sticky con: nombre (izquierda, ancla a #top en home, o link a index.html#top desde una página de case study) + nav (About, Experience, Case Studies, Skills, Contact — todos como links a index.html#seccion desde una página de case study) + botón CTA a la derecha ("Book a 15-Minute Intro Call", ancla a index.html#contact). 4-7 ítems máximo en el nav. En mobile, colapsar a menú hamburguesa. En las páginas de case study, agregar además un link "← Back to all case studies" arriba del contenido.

## HOME (index.html)

### 1. HERO
- Eyebrow: "Dino Albizzati"
- Headline: "Full-funnel growth ownership — without a five-person team's price tag."
- Subheadline: "I ran 100% of paid media, email, and analytics solo for a multi-location business, grounded in senior copywriting for Sony, PlayStation, HBO, Volkswagen, and Starwood."
- Fila de stats (4, verificados):
  - $7,472 — Revenue in the highest-grossing campaign (Passover 2026)
  - $150K+ — Raised via equity crowdfunding, 200+ investors (Wefunder campaign)
  - 7.79x — Best Meta Ads ROAS (Hanukkah, $406 budget)
  - 45.29% — Average email open rate (vs. ~20–25% industry benchmark)
- CTA primario: "Book a 15-Minute Intro Call" → ancla a #contact
- CTA secundario: "Download My Resume" → link al PDF del CV

### 2. ABOUT
"Before I ran growth, I wrote copy for Sony, PlayStation, HBO, Volkswagen, and Starwood — five years as a senior copywriter that's still the foundation everything else is built on. I don't just run channels. I write what goes in them.

From there I moved into growth ownership. Two years managing content and paid marketing across multiple client accounts inside a digital agency (CandidLeap, 2022–2024). Freelance growth consulting for B2B and real estate clients along the way. And most recently, two years owning 100% of marketing for Zeitlin's Delicatessen — paid media, email, GA4 attribution, weekly reporting to ownership, creative direction — entirely remote from Argentina. That role also included leading a Wefunder equity crowdfunding round that raised $150K+ from 200+ investors.

I'm not a one-channel specialist. I'm who you bring in to own outcomes end-to-end — including reading the data honestly when something doesn't work, and changing course because of it. (See the Super Bowl case study below — the one that didn't work, and what I did about it.)

I'm currently looking for Head of Marketing / Growth Marketing Manager roles at startups and SMBs (10–100 people), where that kind of ownership is the job — not a nice-to-have."

CTA al cierre de esta sección: repetir "Book a 15-Minute Intro Call"

### 3. EXPERIENCE TIMELINE (orden cronológico inverso)

- **Jun 2024 – Jun 2026 — Zeitlin's Delicatessen (Chicago, IL — Remote) — Marketing Manager**
  100% solo ownership of marketing for a Chicago restaurant and catering business, entirely remote from Argentina. Built GA4 + Meta Pixel analytics infrastructure from scratch with UTM attribution across all channels. Migrated an email list of ~5,000 subscribers from ActiveCampaign to Beehiiv with tag-based segmentation. Led a Wefunder equity crowdfunding campaign that raised $150K+ from 200+ investors. Developed loyalty, discount, and farmers market incentive programs. Managed a BentoBox-to-Toast Catering platform migration and onboarded a Social Media Manager. See case studies below.

- **Jun 2022 – Jun 2024 — CandidLeap (Los Angeles, CA — Remote) — Digital Content & Marketing Specialist**
  Managed digital content and paid marketing for multiple client accounts across industries simultaneously. Executed paid and organic campaigns, SEO content, and email marketing in English and Spanish. Produced creative briefs, ad copy, and social media content aligned with client brand guidelines.

- **2018–2019 y 2020–2022 — SeaVision — Marketing Consultant (freelance, B2B)**
  Content creation for social, paid ads, and email marketing for a B2B client, across two separate freelance engagement periods.

- **2019–2022 — Oppel Inmuebles — Freelance Marketing (real estate)**
  Social media, email marketing, ads, and website work for a real estate client — including full website development.

- **2009–2014 — M8 Digital Marketing Agency (Miami, FL) — Senior Creative Copywriter**
  Led bilingual creative copy for major brand accounts including Sony, PlayStation, HBO, Volkswagen, and Starwood. Produced campaign concepts, scripts, and digital copy across paid, social, and email channels.

- **2000–2006 — Universidad Siglo 21 — Licenciatura en Publicidad**

### 4. CASE STUDIES (preview cards en home, cada una linkea a su página completa)

Formato en la home: 4 cards con teaser (título + 1 resultado destacado + tags tipo "Holiday Campaign / Meta Ads / Email") + botón "Read the full case study →" que linkea a `case-studies/{slug}.html`.

- **Card 1 — Passover 2026: Full-Funnel Holiday Campaign** → `case-studies/passover-2026.html` — Teaser: "$7,472 in a single campaign — Zeitlin's highest-revenue holiday to date."
- **Card 2 — Hanukkah 2026 Meta Ads: Small Budget, High ROAS** → `case-studies/hanukkah-2026.html` — Teaser: "7.79x ROAS on a $406 budget — and the tracking gap I caught along the way."
- **Card 3 — Farmers Market Incentive Program** → `case-studies/farmers-market.html` — Teaser: "Turned 11 one-off market touchpoints into a repeatable acquisition funnel."
- **Card 4 — Super Bowl Campaign: What Didn't Work** → `case-studies/super-bowl.html` — Teaser: "The campaign that failed — and the process change it led to."

CTA al cierre de esta sección: repetir "Book a 15-Minute Intro Call"

### 5. SKILLS & EXPERTISE (agrupar por categoría, mostrar como grid o tags, no como barras de progreso genéricas)

- **Paid media / Growth:** Meta Ads (advanced — media buying, optimization, retargeting), Google Ads (advanced), full-funnel DTC ownership, CRO / A/B testing, campaign management & optimization
- **Analytics / Tracking:** GA4, Meta Pixel, Google Tag Manager, Conversions API, attribution & UTM tracking built from scratch, reporting that translates performance data into recommendations for non-technical stakeholders
- **Email / Lifecycle:** Beehiiv, ActiveCampaign, segmentation, lifecycle sequences (welcome, winback, etc.), platform migrations without list loss (incl. a 5,000-subscriber migration)
- **Landing pages / Web:** Webflow, full website development (Oppel Inmuebles), Figma (wireframing)
- **Copywriting / Creative:** 10+ years senior copywriting (Sony, PlayStation, HBO, Volkswagen, Starwood accounts), conversion copywriting, creative strategy, ad copy, bilingual EN/ES
- **Ops / Platforms:** Toast, BentoBox, ClickUp, Loomly, Canva, platform migrations (BentoBox → Toast Catering)
- **AI / Automation:** daily operational use of Claude, transitioning into Claude Code (terminal), Make (Integromat)

No incluyas (fuera de mi stack real, no los menciones como si los usara): Klaviyo, Shopify page builders, TikTok Ads, Triple Whale, Northbeam, PostHook, Motion, Minea, AdSpy, SQL/analytics profundo (Mixpanel, PostHog).

### 6. CONTACT
- Headline: "Have 15 minutes to talk about your marketing?"
- Botón: "Book a 15-Minute Intro Call"
- Formulario simple (nombre, email, mensaje)
- Datos directos: dalbizzati@gmail.com, +54 9 11 6121-3289, Argentina (remoto)
- Link a LinkedIn: https://www.linkedin.com/in/dinoalbizzati/
- Link de descarga del CV en PDF

---

## PÁGINAS DE CASE STUDY (dedicadas, con el mismo layout que Notion)

Cada página sigue esta estructura, en este orden: título + tags → Context → Problem → What I Did (bullets) → **galería de media** (imágenes/video con caption debajo de cada una, en grid, igual que Notion) → Results and Outcomes (stats grandes tipo titular + bullets de detalle) → narrativa adicional si existe (quote destacado + texto de reflexión) → CTA "Book a 15-Minute Intro Call".

### case-studies/passover-2026.html

**Tags:** Holiday Campaign · Meta Ads · Email · Local/In-person

**Context:** Zeitlin's Delicatessen, NYC-style Jewish deli in Chicago. I ran 100% of marketing solo, remote, across paid media, email, and analytics. Passover is the highest-stakes holiday on the calendar — a single-night ordering deadline (the Seder) with a high-ticket menu.

**Problem:** Passover pre-orders are win-or-lose in a 4-week window, split across a complex catalog (a $280–560 Full Seder Menu plus 20+ à la carte items), with two different fulfillment nights competing for the same production capacity.

**What I did:**
- Built a 13-email sequence (9 to the main list, 4 to a separate investor list) with a deliberate urgency arc — the best-performing send of the entire campaign was "Day 1 Cut-off," a pure deadline email with no new content
- Ran Meta Ads (4 campaigns: conversion, remarketing off-site visitors, test, Bento-lead remarketing) and Google Search Ads in parallel
- Segmented an investor list separately, using warmer, more direct offers — that list's average CTR ran 8x the main list's
- Tracked order velocity by day and by fulfillment date to separate "top-of-funnel priming" from last-3-days conversion, instead of crediting only last-click

**Campaign Media** (grid, imagen + caption debajo de cada una):
- Video: `ZEITLINS_PASSOVER_REEL03.mp4` — sin caption específico, es el reel principal
- Imagen `Square_03.jpg` — caption: "Regular Campaign - Cold Contacts"
- Imagen `Square_04_ad set 2.jpg` — caption: "Mid campaign Creative - Targeted to audiences searching for lower prices / smaller families"
- Imagen de `ads/` (remarketing) — caption: "Remarketing Ad - Visited landing page / didn't purchase"
- Imagen `Pop Up/desktop.jpg` + `Pop Up/mobile.jpg` — caption: "Website Pop Up - One of the main sources of visits to the purchase site."
- Imagen `Prints/passover_menu_hands_photo.jpeg` — caption: "8.5in x 5.5in (half-letter) Menu - Used at the store"
- Imagen `Emails/passover_email_1.jpg` ("The Passover Seder Menu"), `Emails/passover_email_2.jpg` ("Passover for Two"), `Emails/passover_email_3.jpg` ("Last Call for Day 1 & 2") — caption: "Email Marketing"

**Quote destacado (blockquote):** "As the Passover campaign progressed, I adapted the same core creative across different formats — video, static ads, and print — keeping the concept consistent without just repeating the same asset everywhere."

**Texto de reflexión (después de la galería, antes de Results):**
"Midway through, I started worrying that the Full Seder Menu's entry price was too high a bar for a big chunk of the audience. So I added a second track built around lower-priced, à la carte products — accepting that this would compress ROAS, since ad spend on cheaper items eats up close to the full purchase value. It was a deliberate trade-off: reach over efficiency on that specific track.

That bet paid off in an unexpected way. As the deadline approached, FOMO took over — last-minute orders spiked hard in the final days, driven by the urgency messaging in the emails and headlines (see "Day 1 Cut-off"). This wasn't a conceptually creative campaign — no big idea, no clever hook — but it was an effective one, built on reading price sensitivity in real time and adjusting mid-flight instead of waiting for a post-mortem."

**Results and Outcomes** (stats grandes + bullets):
- $7,472 Gross Revenue
- 4.27x ROAS - Meta
- 45.29% average open rate - Email
- $7,472 gross revenue, 44 orders — Zeitlin's highest-revenue holiday campaign to date, up from $4,309 at Purim
- Meta: 4.27x platform ROAS on the main conversion campaign ($274 spend → 4 attributed purchases)
- Email: 45.29% average open rate across 44,246 sends (food/restaurant industry benchmark is ~20–25%)
- Full Seder Menu drove 52.9% of revenue from just 25% of orders — confirmed it as the anchor product, à la carte as the reach layer

CTA de cierre: "Book a 15-Minute Intro Call" + "← Back to all case studies"

---

### case-studies/hanukkah-2026.html

**Tags:** Holiday Campaign · Meta Ads · Email · Local/In-person

**Context:** A 3-week Hanukkah catering push on Meta Ads, run on a genuinely small budget.

**Problem:** Catering products only make sense as paid-acquisition targets above a certain order value — the challenge was proving the channel could work at all on a shoestring spend, and figuring out why it worked so I could repeat it.

**What I did:**
- Ran a single, tightly-targeted Meta conversion campaign for 3 weeks, total spend $405.86
- Cross-checked Meta's platform-reported revenue against a conservative, order-count-based estimate (28 orders × $110 realistic AOV) instead of trusting the platform number blindly
- Identified a GA4 tracking gap mid-campaign — purchases weren't firing as Key Events, meaning multi-channel attribution was invisible — and wrote up the exact fix (purchase event with value/currency/transaction_id, UTM normalization, DebugView validation) as the #1 priority for the following month
- Turned the result into a reusable rule for the business: paid ads only pay off on high-AOV catering, not low-ticket items — and recommended bundling/minimum-order thresholds to protect that going forward

**Campaign Media** (grid, imagen + caption debajo de cada una):
- Imagen `Emails/HANUKKAH.png` — caption: "Email Marketing"
- Imagen `Emails/THE SHOFAR'S CALLING.png` — caption: "Email Marketing"
- Imágenes de `Ads/HOLIDAYS_ADS/HOLIDAYS/` (confirmar con Dino si son las correctas) — caption: "Regular Campaign - Cold Contacts" / "Mid campaign Creative - Targeted to audiences searching for lower prices / smaller families" / "Remarketing Ad - Visited landing page / didn't purchase"
- Imagen `Pop Up/desktop.jpg` + `Pop Up/mobile.jpg` — caption: "Website Pop Up"

**Results and Outcomes** (stats grandes + bullets):
- $14.50 Cost per conversion
- 7.79x ROAS - Meta
- 7.79x ROAS on Meta's platform numbers, 7.59x on a conservative AOV-adjusted estimate — both held up under scrutiny
- $14.50 cost per conversion, 28 purchases, $405.86 total spend
- Delivered not just a "campaign that worked" but a diagnosed measurement gap and a documented fix plan — the kind of finding that compounds across every future campaign, not just this one

CTA de cierre: "Book a 15-Minute Intro Call" + "← Back to all case studies"

---

### case-studies/farmers-market.html

**Tags:** Acquisition · Local/In-person · Email

**Nota:** este case study no tenía página propia en el Notion original (se agregó al doc local después) — mantiene la misma estructura que los otros tres para consistencia.

**Context:** Zeitlin's had no structured presence or follow-up system across the 11 farmers markets it attends around Chicago — foot traffic at markets wasn't converting into repeat customers or email subscribers.

**Problem:** Farmers markets are one-off touchpoints. Without a system, every market interaction ends when the customer walks away — no capture, no follow-up, no path back to the store.

**What I did:**
- Designed a physical incentive card (bagel card + catering card) handed out at markets, tied to a QR-code email capture flow at the point of sale — turning a one-time market visit into a trackable contact
- Built a 5-email post-visit sequence in Beehiiv specifically for farmers-market-acquired contacts, distinct from the general list, to convert market foot traffic into store/catering customers
- Documented the rollout across all 11 active markets, so the program could run consistently regardless of which staff member worked a given market

**Campaign Media** (grid, imagen + caption debajo de cada una):
- Video `Social Media/We're back at the market...mp4` — caption: "Farmers market presence"
- Imagen `Prints/CARDS_1.jpg` — caption: "Bagel + catering incentive card"
- Imagen `Prints/Card_02.jpg` — caption: "Incentive card, alternate design"
- Imagen `A-frame/Zeitlin's Deli - A-frame for Winter Markets 24x36 in.jpg` — caption: "A-frame sign for winter markets"
- Imagen `Signs/Bagel Fest Letter Sized Sign copy.jpg` — caption: "Market signage"

**Results and Outcomes:**
- Took a channel that had zero structured follow-up and turned it into a repeatable acquisition funnel with its own creative, tracking mechanism (QR), and nurture sequence
- Program became one of the standing systems referenced in monthly reporting, not a one-off campaign — built once, ran every week

CTA de cierre: "Book a 15-Minute Intro Call" + "← Back to all case studies"

---

### case-studies/super-bowl.html

**Tags:** Meta Ads · Email · Local/In-person · Postmortem

**Lead con esta línea antes del título o como subtítulo:** "This is the one to show when someone asks 'tell me about a campaign that failed.'"

**Context:** February 2026, alongside Fat Tuesday and Purim. Super Bowl felt like an obvious seasonal moment to capture — big cultural event, high attention, easy creative angle.

**Problem — found only after running it:** The campaign underperformed badly relative to the same month's other campaigns, despite clean execution.

**What the data actually showed:**
- Meta spend ~$52, 1 purchase, vs. Fat Tuesday's 8 purchases on $141 and Purim's 11 purchases on $237 in the same window
- The ad itself worked fine as an ad: CTR 2.01%, CPC $0.72 — both solid numbers. People clicked. They just didn't buy.
- Email performance told the same story: the Super Bowl sends had the highest unsubscribe count of the month (68 combined across two sends) alongside below-average click rates

**Campaign Media** (grid, imagen + caption debajo de cada una):
- Imagen `Ads/Superbowl/SUPERBOWL_ADS_carousel_01.jpg` — caption: "Regular Campaign - Cold Contacts"
- Imagen `Ads/Superbowl/SUPERBOWL_ADS_carousel_04.jpg` — caption: "Carousel card"
- Imagen `Ads/Superbowl/SUPERBOWL_ADS_carousel_05.jpg` — caption: "Carousel card, A/B version"
- Video `Ads/Superbowl/SuperBowl_TouchDownAd_V2.mp4` — sin caption específico
- Imagen `Pop Up/desktop.jpg` + `Pop Up/mobile.jpg` — caption: "Website Pop Up - One of the main sources of visits to the purchase site."
- Imagen `Prints/superbowl_reheating_instructions.jpg` — caption: "8.5in x 5.5in (half-letter) Reheating instructions"
- **Nota sobre "Email Marketing":** el Notion original reusa por error el mismo archivo del email de Passover en esta página — no hay un screenshot real del email del Super Bowl. Opción A: omitir esa sub-sección en esta página. Opción B (recomendada): mencionar en el texto que los sends de email tuvieron el mayor unsubscribe count del mes (68 combinados) sin mostrar imagen, ya que no hay asset real que lo respalde.

**What I concluded and did:**
This wasn't an execution problem, it was an offer-audience mismatch — Super Bowl isn't culturally relevant to Zeitlin's identity-driven Jewish-deli audience, the way Fat Tuesday and Purim are. "Sports-themed campaigns are not recommended for this audience" went directly into the following month's strategy doc as a standing rule, not just a note. I used it to push a process change with ownership: marketing should act as a first filter on new catering offers — validating audience fit before an offer is finalized and handed over for execution, not after. I named the Super Bowl campaign explicitly as the reference case when making that recommendation to the owners. Campaigns built around what the audience actually identifies with (Purim, Fat Tuesday) consistently outperform campaigns built around assumed demand (Super Bowl) — a principle that shaped how I scoped every campaign afterward, including Passover.

**Why this belongs in the portfolio (destacar como blockquote o caja):** "Anyone can show a win. This shows the read — catching a mismatch the data didn't hand me for free (the ad metrics looked fine), tracing it to the real cause, and turning it into a process change instead of a shrug."

CTA de cierre: "Book a 15-Minute Intro Call" + "← Back to all case studies"

---

## SEO / AI-SEO (schema + básicos, sin roadmap corporativo — sitio chico)
- Agregar JSON-LD `Person` en el `<head>` de index.html con: name "Dino Albizzati", jobTitle "Growth Marketing Manager", email, url de LinkedIn, sameAs (LinkedIn), knowsAbout (paid media, email marketing, copywriting, GA4, growth marketing)
- Agregar JSON-LD `Article` en cada página de case study (headline, datePublished aproximado, author: Dino Albizzati)
- HTML semántico en todas las páginas: `<main>`, `<nav>`, `<section>`, jerarquía de headings correcta (un solo `<h1>` por página)
- `<title>` y meta description propios por página (ej: para Passover, "Passover 2026 Case Study — Dino Albizzati") y OpenGraph tags básicos (og:title, og:description, og:image)
- Mostrar "Last updated: [mes/año]" cerca del footer de cada página
- No hace falta `llms.txt` ni archivos machine-readable adicionales — sitio personal, no producto con pricing/catálogo
- No bloquear bots de IA en robots.txt

## Analytics (mínimo, sin backend)
- Instalar GA4 vía `gtag.js` embebido directo en el `<head>` de TODAS las páginas (mismo Measurement ID)
- Trackear estos eventos custom, nombrados en formato objeto_acción:
  - `cta_hero_clicked` — click en el CTA primario del hero (home)
  - `resume_downloaded` — click en "Download My Resume"
  - `case_study_card_clicked` — click en una card de case study en la home (property `case_study_name`)
  - `case_study_media_viewed` — al hacer click/play en un video de una página de case study (property `case_study_name`, `media_type`)
  - `contact_form_submitted` — al enviar el formulario de contacto
- Dejar un placeholder claro en el código para el Measurement ID de GA4 (`G-XXXXXXXXXX`) en todas las páginas

## Requisitos técnicos
- Multi-página: index.html + 4 archivos en /case-studies/, cada uno un HTML autocontenido (CSS compartido puede ir en un solo archivo `styles.css` referenciado por todas las páginas, o inline repetido — lo que genere menos fricción para "casi ningún ajuste manual")
- Header sticky con nav + CTA, igual en todas las páginas, colapsa a menú hamburguesa en mobile
- Totalmente responsive (mobile-first)
- Galería de media en cada case study: grid responsive, imagen/video + caption debajo, sin necesidad de acordeón porque cada case study ya tiene su propia página completa
- Sin JavaScript salvo lo mínimo necesario para el menú mobile, el formulario de contacto, el tracking de eventos GA4, y reproducción de video
- El formulario de contacto puede ser un simple mailto: o dejar el markup listo para conectar a Formspree/similar después
- El botón "Download My Resume" debe apuntar a un archivo PDF que subiré yo al mismo hosting (dejar el href apuntando a "./Dino_Albizzati_CV.pdf" desde home, "../Dino_Albizzati_CV.pdf" desde las páginas de case study)
- Los archivos reales ya están organizados en este mismo repo, con estas rutas exactas — usalas tal cual en los `src`/`href` del HTML, no inventes otras:
  - CV: `Dino_Albizzati_CV.pdf` (raíz del repo)
  - Passover: `assets/passover/reel.mp4`, `ad-cold-contacts.jpg`, `ad-mid-campaign.jpg`, `ad-remarketing.jpg`, `menu-photo.jpg`, `email-1.jpg`, `email-2.jpg`, `email-3.jpg`
  - Hanukkah: `assets/hanukkah/email-hanukkah.png`, `email-shofar.png`, `ad-holiday-1.png`, `ad-holiday-2.png`
  - Farmers Market: `assets/farmers-market/market-video.mp4`, `incentive-card-1.jpg`, `incentive-card-2.jpg`, `a-frame.jpg`, `bagel-fest-sign.jpg`
  - Super Bowl: `assets/super-bowl/touchdown-ad.mp4`, `carousel-1.jpg`, `carousel-2.jpg`, `carousel-3.jpg`, `reheating-instructions.jpg`
  - Compartido (las 4 páginas de case study lo usan): `assets/shared/website-popup-desktop.jpg`, `website-popup-mobile.jpg`
  - Desde `index.html` las rutas son relativas a la raíz (ej. `assets/passover/reel.mp4`); desde `case-studies/*.html` hay que subir un nivel (ej. `../assets/passover/reel.mp4`, `../Dino_Albizzati_CV.pdf`)
- No incluyas ningún elemento con marca de "Zeitlin's" como identidad del sitio entero — Zeitlin's es un cliente dentro del portfolio, no el tema visual del sitio
- No menciones a Hammerhead en ningún lugar del sitio — no es cliente de Dino
```

---

*Nota: los assets visuales de las campañas de Zeitlin's (ads, emails, prints) están en `~/Proyectos/Carpeta/Ads/`, `Emails/`, `Prints/`, `Social Media/`, `Pop Up/`, `Menu/`, `A-frame/`, `Signs/`. El CV en PDF está en `/Users/dinoalbizzati/Downloads/Dino_Albizzati_CV.pdf` — copiarlo a la carpeta del sitio antes de publicar, con nombre `Dino_Albizzati_CV.pdf`. Ver la tabla de mapeo de assets en la Parte 2 para lo que falta exportar desde Notion (foto del menú con manos, tarjeta de recalentado del Super Bowl, y los screenshots de email de Passover y Super Bowl).*
