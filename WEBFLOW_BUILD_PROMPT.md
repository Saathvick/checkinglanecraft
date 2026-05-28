# Webflow Build Instructions — Lanecraft Lab

## YOUR GOAL
Replicate the file `index.html` in this folder **exactly** as a native Webflow design.
Same layout, same colors, same fonts, same spacing, same animations — fully editable in Webflow Designer.

**Webflow Site ID:** `6a17f451e4861134f55748a8`  
**API Token is already configured** via the Webflow MCP (connected via npx webflow-mcp-server).

## STEP 1 — READ EVERYTHING FIRST
Before touching Webflow, read these files completely:
1. `index.html` — the full source of truth for layout, content, classes, and styles
2. `assets/` folder — all images already exist with these clean names:
   - `hero-golden-palm.jpeg` — hero background
   - `ocean-foam.jpeg` — services intro background
   - `press-badge.jpg` — featured press image
   - `service-stakeholder.jpg`, `service-earned-media.jpg`, `service-media-voice.jpg`
   - `service-systems.jpg`, `service-governance.jpg`, `service-sustainability.jpeg`
   - `team-nish.jpg`, `team-brentan.jpeg`
   - `logo-pg.png`, `logo-lee-strasberg.png`, `logo-thegist.png`

## STEP 2 — DESIGN SYSTEM (apply these to every element)

### Colors (create as Webflow variables)
- `--navy`: #0A192F (primary dark, nav/hero/dark sections)
- `--gold`: #C9A96E (accent, CTAs, labels, borders)
- `--gold-light`: #d4b87f (hover state of gold)
- `--white`: #FFFFFF
- `--off-white`: #F7F5F0 (alternate section backgrounds)
- `--gray`: #6B7280 (muted text)
- `--light-gray`: #F3F4F6 (placeholders, cards)
- `--body-text`: #4B5563 (paragraph text)

### Typography (add both fonts via Webflow Font settings)
- **Newsreader** (Google Font) — all headings, hero title, quotes, logo, press headlines
- **Inter** (Google Font) — all body text, nav links, labels, buttons, form fields

### Font sizes
- Hero title: clamp(40px, 6.5vw, 82px), weight 600, Newsreader
- Section titles: clamp(30px, 4vw, 52px), weight 600, Newsreader
- Section labels: 11px, weight 600, letter-spacing 0.2em, uppercase, gold color
- Body text: 16px, line-height 1.82, Inter
- Nav links: 11px, weight 500, letter-spacing 0.13em, uppercase
- Card titles: 22px, Newsreader, weight 600
- Testimonial text: 16px, Newsreader, italic

---

## STEP 3 — BUILD SECTION BY SECTION

### SECTION 1: NAVBAR (fixed, position: fixed, top: 0, z-index: 100)
- Background: rgba(10,25,47,0.96), backdrop-filter: blur(8px)
- Bottom border: 1px solid rgba(201,169,110,0.12)
- Max-width container: 1280px, padding: 18px 48px
- **Logo** left: "LANECRAFT LAB" — Newsreader, 19px, weight 500, white, letter-spacing 0.1em, uppercase
- **Nav links** right: Services | Clients | Press | Team | Careers — 11px, Inter, white 72% opacity, uppercase, letter-spacing 0.13em. Hover: gold color
- **CTA button** far right: "PARTNER WITH US" — background gold (#C9A96E), navy text, 10px 22px padding, 11px font, weight 600
- On scroll: add box-shadow 0 2px 24px rgba(0,0,0,0.35)
- Mobile: hamburger menu, links collapse into dropdown

### SECTION 2: HERO (height: 100vh, min-height: 680px)
- **Background image**: `assets/hero-golden-palm.jpeg`, cover, center
- **Ken Burns animation**: scale from 1.0 → 1.09 over 22 seconds, ease-in-out, infinite alternate (use Webflow Interaction: element trigger on page load, scale transform loop)
- **Gradient overlay** on top of image: linear-gradient(to bottom, rgba(10,25,47,0.52) 0%, rgba(10,25,47,0.28) 45%, rgba(10,25,47,0.72) 100%)
- **Content** centered vertically and horizontally:
  - Eyebrow text: "STRATEGIC COMMUNICATIONS & PR" — 11px, gold, letter-spacing 0.22em, uppercase. Fade up on load (0.3s delay)
  - H1: "Everyone has a unique story to tell." — Newsreader, clamp(40px,6.5vw,82px), white, weight 600, line-height 1.08, letter-spacing -0.025em. Fade up (0.5s delay)
  - Subtext: "A story that helps millions of other people when it lands in the right channels. We help B2B and B2C brands strengthen their bottom lines by ensuring their stories reach the right audiences." — 18px, white 80%, Inter, weight 300, max-width 660px. Fade up (0.7s delay)
  - CTA button: "PARTNER WITH US" — gold background, navy text, 16px 48px padding, 12px font, weight 600, letter-spacing 0.16em. Fade up (0.9s delay). Hover: translateY(-2px), shadow
- **Scroll indicator** bottom center: thin gold line pulsing + "SCROLL" text in tiny uppercase

### SECTION 3: FEATURED PRESS (background: #0A192F, padding: 80px 48px)
- 2-column grid: 320px image | 1fr text, gap 64px, max-width 1280px centered
- Left: `assets/press-badge.jpg` — full width image, border-radius 3px
- Right:
  - Label: "FEATURED PRESS" — 11px, gold, uppercase, letter-spacing 0.2em
  - Headline (italic): "From Wall Street Journal to Strategic Advisor: How Nish Amarnath Built Lanecraft Lab on the Power of Story Architecture" — Newsreader, clamp(20px,2.8vw,34px), white, font-style italic, font-weight 500
  - Publication: "— Published by Founded by Women · October 2025" — 13px, white 42% opacity

### SECTION 4: PRESS LOGO STRIP (background: #F7F5F0, padding: 56px 0)
- Label centered: "MEDIA OUTLETS WHERE OUR CLIENTS & WORK HAVE BEEN FEATURED" — 11px, gray, uppercase, letter-spacing 0.2em
- **Infinite scrolling marquee** (use Webflow Interaction or CSS animation):
  - Logos displayed as styled text (Newsreader font): The Wall Street Journal (italic) · CNBC · Forbes · BW BusinessWorld · THE STREET (Inter, small caps) · Golf Digest (italic) · Morning Brew · TheGIST (use `assets/logo-thegist.png` image, height 28px)
  - Duplicated for seamless loop
  - Speed: 28s for full loop, linear
  - Fade edges: left/right gradient fade from off-white to transparent (use pseudo-elements or overlay divs)
  - Hover: pause animation

### SECTION 5: SERVICES (background: white)
**Part A — Intro (padding: 100px 48px 64px)**
- 2-column grid: 1fr | 1fr, gap 80px, max-width 1280px, items center
- Left: `assets/ocean-foam.jpeg` — height 420px, object-fit cover, hover: slow scale 1.05 (8s transition)
- Right:
  - Label: "WHAT WE DO" — 11px, gold, uppercase
  - Big italic quote: "We launch the argument before we pitch the story." — Newsreader, clamp(26px,3.2vw,42px), navy, weight 600, italic, letter-spacing -0.02em
  - Body: "Visibility is not a press release..." — 16px, #4B5563, line-height 1.82
  - Body 2: "Lanecraft Lab works with companies navigating launches..." — same style

**Part B — Service Cards Grid (3 columns, gap 3px, padding: 0 48px 100px)**
Each card is 440px tall, overflow hidden, with:
- Background image (cover, center) — hover: scale to 1.07 over 0.7s
- Dark gradient overlay (bottom-heavy) — hover: darken overlay to 97%
- Content at bottom: number (gold, 11px uppercase), title (Newsreader 22px white), description (14px white 76% — hidden by default, revealed on hover with max-height transition)

Cards:
1. `service-stakeholder.jpg` | 01 | Stakeholder Engagement & Positioning | "We develop evidence-based market-facing arguments, so that our clients' customers, investors, lenders, partners, influencers, and the media understand what makes a company worth paying attention to."
2. `service-earned-media.jpg` | 02 | Earned Media Visibility | "Journalists and podcasters are always looking for sources and interviewees like you. We position our clients as credible, compelling voices in the channels that matter most."
3. `service-media-voice.jpg` | 03 | Media & Public Voice Strategy | "Op-eds and bylined articles in Tier-1, trade, and niche media. Award submissions. Speaker and panel applications. Social and digital visibility. Media interview briefings. Podcast appearance briefs."
4. `service-systems.jpg` | 04 | Processes & Systems Optimization | "Diagnostic and advisory support to strengthen internal systems, identify revenue leakages, and reduce inefficiencies. Process mapping, performance benchmarking, KPI frameworks, and operational workflow audits."
5. `service-governance.jpg` | 05 | Corporate Governance | "Advisory support for building resilient governance frameworks, including CEO succession planning, best practices for board appointments, executive search, operational risk identification, and mitigation strategies."
6. `service-sustainability.jpeg` | 06 | Sustainability & Energy Efficiency | "Energy efficiency assessments, ESG-aligned operational frameworks, carbon footprint reduction strategies, resource optimization, and alignment with regulatory, lender, and investor-driven sustainability goals."

### SECTION 6: CLIENTS (background: #F7F5F0)
**Part A — Featured Engagements header (padding: 100px 48px 56px, text-center)**
- Label: "OUR CLIENTS" — gold, uppercase
- H2: "Featured Engagements" — Newsreader, navy

**Part B — Featured Client Tiles (3-column grid, gap 24px, padding: 0 48px 80px)**
Each tile: white background, hover: translateY(-5px) + box-shadow

Tile structure:
- Header (navy background, min-height 96px, flex center): logo image OR text in white Newsreader
- Body (padding 28px): description text + video embed(s)

Tile 1 — Performance Golf:
- Header: `assets/logo-pg.png` (filter: brightness(0) invert(1), max-height 44px)
- Body: "Founder visibility, product positioning, and earned media strategy for a fast-growing golf training and equipment company."
- YouTube embed 1: https://www.youtube.com/embed/1zTLn4pfSuo?start=462
- YouTube embed 2: https://www.youtube.com/embed/8tq6hAM_2sE?start=6

Tile 2 — Aunt Flow:
- Header: "Aunt Flow" in white Newsreader 22px
- Body: "Public-sector, facilities, healthcare, retail, workplace, and stadium-facing communications for a menstrual product access company changing restroom standards."
- YouTube embed: https://www.youtube.com/embed/DMNi4K4zXEU

Tile 3 — Lee Strasberg:
- Header: `assets/logo-lee-strasberg.png` (filter: brightness(0) invert(1), max-height 44px)
- Body: "Editorial development and reflective spotlight for the world premiere of Apples for August..."
- Quote block (left gold border 3px, off-white bg, italic Newsreader text): "Apples for August invites us into a space where longing coexists with a quieter light..."

**Part C — All Clients (background: #0A192F, padding: 80px 48px)**
- Title: "All Clients" — Newsreader, clamp(26px,3.5vw,42px), white, weight 600, border-bottom 1px gold/28% opacity
- 7 client rows, each: 2-column grid (260px | 1fr), padding 48px 0, border-bottom 1px white/7% opacity
- Left col: number (gold, 11px), name (Newsreader 21px white), sector (12px white 38%)
- Right col: h4 labels (gold, 11px, uppercase), paragraph text (15px, white 68%), bullet lists (gold dash prefix), outcome tags (gold bg 14%, gold text)

All 7 clients with full content from the document (Performance Golf, Aunt Flow, A.R.T/New York Theatres, Energy Infrastructure Leader, Narrative Repositioning, Digital Asset Deployment, Strategic Venture Launch)

### SECTION 7: TESTIMONIALS (background: #0A192F, padding: 100px 48px)
- Label: "WHAT CLIENTS & THE MEDIA ARE SAYING" — gold, uppercase
- H2: "The work speaks for itself." — Newsreader, white
- 3-column grid of cards (gap 20px):
  - Card: rgba(255,255,255,0.048) bg, 1px gold/14% border, padding 36px
  - Hover: bg darkens slightly, translateY(-4px)
  - Opening quote mark: Newsreader 36px, gold
  - Quote text: Newsreader 16px, italic, white 84%
  - Author: 11px, gold, uppercase, letter-spacing 0.12em
  - Role/date: 12px, white 38%

5 testimonials (full text from document):
1. Quratulain Tejani, Reporter EQDerivatives, Aug 2 2025
2. Kevin J. Burke, NYPD Lieutenant (Ret.), July 8 2025
3. Anushka Kar, Playwright Producer & Actor, June 16 2025
4. Rachel Curtis LCSW, Oct 17 2025
5. Vasant Laplam, Journalist, June 9 2025

### SECTION 8: LEADERSHIP (background: white, padding: 100px 48px)
**Team Grid (3 columns, gap 40px)**
- Label: "OUR LEADERSHIP" — gold, uppercase
- H2: "The Team" — navy, Newsreader

Each team card:
- Photo: aspect-ratio 3/4, object-fit cover, object-position top, filter grayscale(15%), hover: grayscale(0)
- Name: Newsreader 22px, navy, weight 600
- Role: 11px, gold, uppercase, letter-spacing 0.1em
- Bio: 14px, #4B5563, line-height 1.76

Team:
1. Nish Amarnath — `assets/team-nish.jpg` — Founder & Principal — "With early roots in management consulting..."
2. Brentan Debysingh — `assets/team-brentan.jpeg` — Media Relations & Editorial Associate — "Brentan brings over a decade of experience in sports marketing..."
3. Vasant Laplam — placeholder (initial "V" centered) — Content & Communications Strategist — "Media engagement for our clients involves thinking like a journalist..."

**Advisory Committee (margin-top 96px, border-top 1px light-gray)**
- Label: "ADVISORY COMMITTEE" — gold
- H2: "Our Advisors" — navy
- Intro text: "Lanecraft Lab is building a circle of advisors..." — 16px, #4B5563
- 3-column grid of advisor cards:
  - Left border: 3px solid gold
  - Background: #F7F5F0
  - Padding: 28px

3 advisors:
1. Jonathan Ward — International Affairs & Trade Advisor, Chair Wisconsin World Affairs Council
2. David Trask — National Director ARC Facilities, Host Facility Voices Podcast
3. Dr. Jason Baker — Assistant Professor of Medicine, Cornell Medical College

### SECTION 9: WORK WITH US (background: #F7F5F0, padding: 100px 48px)
- Centered, max-width 760px
- Label: "CAREERS" — gold, uppercase, centered
- H2: "Work With Us" — navy, Newsreader, centered
- Body text (2 paragraphs from document)
- Link: "GET IN TOUCH" — navy text, gold underline border-bottom 2px, uppercase, letter-spacing 0.16em, hover: gold text

### SECTION 10: CONTACT (background: #0A192F, padding: 100px 48px)
- 2-column grid: 1fr | 1.6fr, gap 80px, max-width 1280px
- Left: Label "CONTACT US" (gold), H2 "Bring Us the Brief." (white Newsreader), 2 paragraphs (white 62%)
- Right: Form with fields:
  - First Name + Last Name (2-column row)
  - Company/Organization
  - Email Address
  - Service Area (dropdown: 7 options)
  - Goals textarea (height 136px)
  - Submit button: "SEND INQUIRY" — gold bg, navy text, 15px 42px padding

Form field styles: rgba(255,255,255,0.055) bg, 1px rgba(255,255,255,0.11) border, white text, focus: gold border

### SECTION 11: FOOTER (background: #05101f, padding: 44px 48px)
- 3-column flex row: logo left | nav links center | copyright right
- Logo: "LANECRAFT LAB" — Newsreader, white 50%, uppercase
- Nav: Services | Clients | Team | Contact — 11px, white 35%, uppercase, hover: gold
- Copyright: "© 2025 Lanecraft Lab. All rights reserved." — 12px, white 25%

---

## STEP 4 — ANIMATIONS (set via Webflow Interactions)

### Hero Ken Burns (Page Load trigger)
- Target: hero background div
- Action: Scale from 1.0 → 1.09
- Duration: 22,000ms, Easing: ease-in-out
- Loop: yes, alternating direction

### Scroll Reveal (Scroll Into View trigger, apply to each section card/element)
- Initial state: opacity 0, translateY 28px
- Final state: opacity 1, translateY 0
- Duration: 720ms, Easing: ease
- Elements: all service cards, client tiles, client rows, testimonial cards, team cards, advisor cards

### Hero elements fade-up on page load
- Eyebrow: opacity 0 → 1 + translateY 22px → 0, 800ms, delay 300ms
- H1: same, delay 500ms
- Subtext: same, delay 700ms
- CTA button: same, delay 900ms

### Marquee (Logo Strip continuous scroll)
- Use CSS animation via Webflow's custom CSS embed within the section
- Or use Webflow's animation to move the track div continuously left

### Service Cards hover
- On hover: background image scales to 1.07 (700ms ease), overlay darkens, description text max-height expands
- Set via Webflow Hover Interactions

### Nav on scroll
- When page scrolls past 60px: add box-shadow to navbar
- Use Webflow scroll-triggered interaction on body

---

## STEP 5 — VERIFY ACCURACY
After building each section, take a screenshot and compare with `referances/site-fullpage.png`. Check:
- Colors match exactly (use the hex values above)
- Font families correct (Newsreader for headings, Inter for body)
- Spacing and padding match
- Gold accent appears on all labels, borders, CTAs
- Dark navy sections alternate with white/off-white sections correctly

Build section by section, confirm each one before moving to the next.
