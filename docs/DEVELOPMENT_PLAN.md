# WebSummit 2025 Landing Page - Development Plan

## 📋 Document Overview

**Project:** Serhiy Prytula Charity Foundation - WebSummit 2025 Landing Page
**Version:** 2.0 - Updated based on Desktop.png and Mobile.png
**Date:** 2025-01-10 (Updated: 2025-01-10)
**Purpose:** Comprehensive development guide for implementing the new landing page
**Target Framework:** Astro 5.x (Static Site Generator)
**Language:** English only
**Design Style:** ⚡ **Minimalist** - Full-width color blocks, no icons, no cards

---

## 🎨 DESIGN OVERVIEW (Based on Mockups)

### Key Design Principles from Desktop.png and Mobile.png:

1. **✅ MINIMALIST APPROACH**
   - NO icons/emojis
   - NO cards with borders
   - NO shadows or rounded corners
   - ONLY clean typography and full-width color blocks

2. **🎨 COLOR BLOCK STRUCTURE**
   - Alternating full-width sections:
     - 🖼️ White (Hero with B&W photo)
     - 🔵 Bright Blue (#0047FF)
     - 🟡 Bright Yellow (#FFD600)
     - ⚪ White
     - ⚫ Light Gray (#F5F5F5)

3. **📐 LAYOUT PATTERN**
   - Two-column grid: **Title (left) | Content (right)**
   - Title: Large, uppercase, bold (40px)
   - Content: Clean paragraphs, 16-18px body text
   - Mobile: Stack vertically

4. **🔤 TYPOGRAPHY**
   - Hero title: 80px bold black "SAFETY FOR UKRAINIANS"
   - Section titles: 40px uppercase
   - Body text: 16-18px regular
   - Font: Inter (existing)

5. **📱 RESPONSIVE**
   - Desktop: Two-column layout
   - Mobile: Single column, stacked

---

## 🚨 CRITICAL CHANGES FROM ORIGINAL PLAN

### What Changed:
- ❌ Removed all icons/emojis
- ❌ Removed card components with borders
- ❌ Removed shadows and border-radius
- ❌ Changed hero to "SAFETY FOR UKRAINIANS" (not "TOGETHER DURING WEBSUMMIT")
- ✅ Added full-width color blocks (blue, yellow)
- ✅ Simplified to clean text layouts
- ✅ Two-column grid pattern for all sections

### Component Simplification:
- All components now follow same pattern: full-width background → container → 2-column grid → title + content
- No DonateButton component needed (no CTAs in mockup)
- Focus on content presentation, not interaction

---

## 🔧 UNIVERSAL SECTION TEMPLATE

**All sections use this exact structure:**

```astro
<section class="section-[color]">
  <div class="container">
    <h2 class="section-title">SECTION<br>TITLE<br>HERE</h2>
    <div class="content">
      <p class="text-block">[Content paragraphs]</p>
      <p class="text-block">[More content]</p>
    </div>
  </div>
</section>

<style>
  .section-[color] {
    background: var(--bg-[white/blue/yellow/gray-light]);
    padding: var(--section-padding-y) var(--section-padding-x);
    color: var(--text-[black/white]); /* white for blue, black for others */
  }

  .container {
    max-width: var(--container-max);
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 4rem;
    align-items: start;
  }

  .section-title {
    font-size: var(--text-section-title);
    font-weight: var(--font-bold);
    line-height: var(--leading-tight);
    text-transform: uppercase;
    letter-spacing: var(--tracking-wide);
  }

  .content {
    display: flex;
    flex-direction: column;
    gap: var(--paragraph-gap);
  }

  .text-block {
    font-size: var(--text-body-large);
    line-height: var(--leading-normal);
  }

  @media (max-width: 768px) {
    .container {
      grid-template-columns: 1fr;
      gap: 2rem;
    }
    .section-title {
      font-size: 2rem;
    }
  }
</style>
```

**Just change these for each section:**
1. Background color: `--bg-blue`, `--bg-yellow`, `--bg-white`, `--bg-gray-light`
2. Text color: `--text-white` (for blue section), `--text-black` (for others)
3. Title text and content

---

## 🎯 Project Objectives

### Primary Goal
Replace the current homepage (`/src/pages/index.astro`) with a new single-page landing for WebSummit 2025, showcasing:
- Foundation achievements and mission
- "One Billion" fundraising campaign
- Humanitarian impact and transparency
- Call-to-action for donations

### Key Requirements
1. **7 Content Blocks** - Structured sections with clear hierarchy
2. **English Only** - No multilingual support needed
3. **Enhanced Design** - Icons, color accents, cards, professional look
4. **Mobile-First** - Responsive design for all devices
5. **Performance** - Fast load times, optimized for Vercel deployment
6. **Maintainable** - Modular Astro components, clean CSS

---

## 📊 Current Project State

### Tech Stack
- **Framework:** Astro 5.8.0
- **Styling:** Pure CSS (no Tailwind)
- **TypeScript:** Strict mode enabled
- **Deployment:** Vercel (static output)
- **Analytics:** Plausible.io

### Existing Structure
```
src/
├── components/
│   ├── Layout.astro          # Base layout with Header/Footer
│   ├── Header.astro          # Fixed header with logo
│   ├── Footer.astro          # Footer with contacts (3 languages)
│   ├── DonationButtons.astro # Monobank/PayPal buttons
│   ├── CopyButton.astro      # Copy-to-clipboard component
│   └── LanguageSwitcher.astro # EN/UA/FI switcher (will be removed)
├── layouts/
│   └── Layout.astro          # Page wrapper
├── pages/
│   ├── index.astro           # Homepage (to be replaced)
│   └── denmark/index.astro   # "Clear Sky" project page (keep as-is)
├── styles/
│   └── index.css             # Global styles (will be extended)
└── assets/
    ├── logo-color.png
    └── logo-bw.png
```

### Existing Components to Keep
- ✅ `Header.astro` - Will be simplified (remove language switcher)
- ✅ `Footer.astro` - Will be updated with new contacts
- ✅ `CopyButton.astro` - Reusable for SWIFT details
- ❌ `LanguageSwitcher.astro` - Remove (English only)
- ❌ `DonationButtons.astro` - Replace with new design

---

## 🏗️ New Page Architecture

### Page Structure (Top to Bottom)

```
┌─────────────────────────────────────┐
│  HEADER (Fixed)                     │
│  - Logo + Link to main site         │
└─────────────────────────────────────┘
│                                      │
│  HERO SECTION                        │
│  "TOGETHER DURING WEBSUMMIT 2025..."  │
│  + CTA Button                        │
│                                      │
├─────────────────────────────────────┤
│  BLOCK 1: About Foundation           │
│  - Foundation info                   │
│  - Serhiy Prytula bio                │
│  - Ukrainian Hub info                │
├─────────────────────────────────────┤
│  BLOCK 2: One Billion Fundraiser    │
│  - The Problem                       │
│  - Our Solution                      │
│  - Why Now                           │
│  - How You Can Help (CTA)            │
├─────────────────────────────────────┤
│  BLOCK 3: Why Prytula Foundation?   │
│  4 Cards: Transparent, Experts,      │
│           Reliable, Effective        │
├─────────────────────────────────────┤
│  BLOCK 4: Humanitarian Achievements  │
│  - Stats: 650M+ UAH raised           │
│  - 5 Areas: Healthcare, Demining,    │
│    Safe&Smart, Crisis, NEST          │
├─────────────────────────────────────┤
│  BLOCK 5: Prytula Foundation USA    │
│  - 501(c)(3) nonprofit info          │
│  - $5.7M raised in 2024              │
├─────────────────────────────────────┤
│  BLOCK 6: Cool Stories               │
│  - Satellite Purchase (2022)         │
│  - Eurovision Fundraiser             │
├─────────────────────────────────────┤
│  BLOCK 7: Videos + Contacts          │
│  - 3 Video Placeholders              │
│  - Contact info + Social links       │
│                                      │
└─────────────────────────────────────┘
│  FOOTER                              │
│  - Copyright + Links                 │
└─────────────────────────────────────┘
```

---

## 🎨 Design System (Based on Provided Mockups)

### Color Palette

**From Desktop.png and Mobile.png analysis:**

```css
/* Primary Brand Colors */
--color-blue: #0047FF;          /* Bright Blue - Section backgrounds */
--color-yellow: #FFD600;        /* Bright Yellow - Section backgrounds */
--color-black: #000000;         /* Pure Black - Text, hero title */
--color-white: #FFFFFF;         /* Pure White - Text on dark, backgrounds */

/* Neutral Backgrounds */
--bg-white: #FFFFFF;            /* White sections */
--bg-gray-light: #F5F5F5;       /* Light gray sections */
--bg-blue: #0047FF;             /* Blue section backgrounds */
--bg-yellow: #FFD600;           /* Yellow section backgrounds */

/* Text Colors */
--text-black: #000000;          /* Primary text on light backgrounds */
--text-white: #FFFFFF;          /* Text on blue/dark backgrounds */
--text-gray: #666666;           /* Secondary/body text */
```

### Design Philosophy

**Minimalist Approach:**
- ✅ **No icons/emojis** - Clean typography only
- ✅ **Full-width color blocks** - Blue, yellow, white, gray alternating
- ✅ **No cards/borders** - Simple text blocks in columns
- ✅ **Bold typography** - Large, uppercase section titles
- ✅ **Ample whitespace** - Generous padding between sections

### Typography

**From Desktop.png analysis:**

```css
/* Font Family */
--font-primary: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;

/* Font Sizes - Based on Mockup */
--text-hero: 5rem;       /* 80px - "SAFETY FOR UKRAINIANS" */
--text-section-title: 2.5rem; /* 40px - Section headings (uppercase) */
--text-body: 1rem;       /* 16px - Body text */
--text-body-large: 1.125rem; /* 18px - Larger body text */
--text-small: 0.875rem;  /* 14px - Small text, labels */

/* Font Weights */
--font-regular: 400;     /* Body text */
--font-bold: 700;        /* Titles, emphasis */
--font-black: 900;       /* Hero title (if available in font) */

/* Line Heights */
--leading-tight: 1.1;    /* Hero titles */
--leading-normal: 1.5;   /* Body text */
--leading-relaxed: 1.7;  /* Long-form content */

/* Letter Spacing */
--tracking-tight: -0.02em;  /* Large titles */
--tracking-normal: 0;       /* Body text */
--tracking-wide: 0.05em;    /* Uppercase section titles */
```

### Layout Structure from Mockup

**Section Order (Desktop.png):**
1. 🖼️ Hero - "SAFETY FOR UKRAINIANS" + large B&W photo
2. 🔵 Blue Section - "ABOUT THE FOUNDATION"
3. 🟡 Yellow Section - "ABOUT PRYTULA CHARITY FOUNDATION"
4. ⚪ White Section - "WHY SERHIY PRYTULA CHARITY FOUNDATION?"
5. ⚫ Gray Section - "HUMANITARIAN ACHIEVEMENTS"
6. ⚪ White Section - "PRYTULA FOUNDATION USA"
7. ⚪ White Section - "COOL STORIES"
8. ⚫ Gray Section - "VIDEOS"
9. Footer - Contacts

### Spacing System

**From Desktop.png measurements:**

```css
/* Section Spacing - Generous vertical padding */
--section-padding-y: 6rem;        /* 96px - Desktop section padding */
--section-padding-y-mobile: 3rem; /* 48px - Mobile section padding */
--section-padding-x: 2rem;        /* 32px - Horizontal padding */

/* Content Spacing */
--content-gap: 2rem;              /* 32px - Gap between text blocks */
--content-gap-large: 3rem;        /* 48px - Gap between major sections */
--paragraph-gap: 1rem;            /* 16px - Between paragraphs */
```

### Container Widths

**Based on mockup layout:**

```css
--container-max: 1200px;  /* Maximum content width */
--container-text: 800px;  /* Text-heavy sections */
--container-full: 100%;   /* Full-width color blocks */
```

### Breakpoints

```css
/* Mobile First */
@media (min-width: 768px)  { /* md - Tablet */ }
@media (min-width: 1024px) { /* lg - Desktop */ }
@media (min-width: 1440px) { /* xl - Large desktop */ }
```

### Design Elements

**Minimalist approach means:**
- ❌ No border-radius (sharp corners)
- ❌ No shadows (flat design)
- ❌ No cards with borders
- ✅ Full-width color blocks
- ✅ Clean typography
- ✅ Generous whitespace

---

## 📦 Component Structure

### New Components to Create

All new components will be placed in `/src/components/websummit/`

```
src/components/websummit/
├── HeroSection.astro          # Hero with main heading + CTA
├── AboutFoundation.astro      # BLOCK 1: Foundation, Serhiy, Ukrainian Hub
├── OneBillionFundraiser.astro # BLOCK 2: 4-part fundraiser info
├── WhyPrytula.astro           # BLOCK 3: 4 reason cards
├── HumanAchievements.astro    # BLOCK 4: Stats + 5 areas
├── PrytulaUSA.astro           # BLOCK 5: 501(c)(3) info
├── CoolStories.astro          # BLOCK 6: 2 stories
├── VideosContacts.astro       # BLOCK 7: Video placeholders + contacts
└── DonateButton.astro         # Reusable CTA button component
```

---

## 📝 DETAILED CONTENT FOR EACH BLOCK

### HERO SECTION

**Component:** `HeroSection.astro`

**Content (from Desktop.png):**
```
SAFETY
FOR
UKRAINIANS

[Large black & white photo of people/group]
```

**Design from Mockup:**
- White background
- Huge black bold title at top left: "SAFETY FOR UKRAINIANS"
- Large hero image below title (black & white photo)
- No buttons, minimal design
- Title uses --text-hero size (80px)

**Code Example:**
```astro
---
// HeroSection.astro
---

<section class="hero-section">
  <div class="hero-container">
    <h1 class="hero-title">
      SAFETY<br>
      FOR<br>
      UKRAINIANS
    </h1>
    <div class="hero-image">
      <img
        src="/images/hero-people.jpg"
        alt="Group of people supporting Ukraine"
        class="hero-img"
      />
    </div>
  </div>
</section>

<style>
  .hero-section {
    background: var(--bg-white);
    padding: var(--section-padding-y) var(--section-padding-x);
  }

  .hero-container {
    max-width: var(--container-max);
    margin: 0 auto;
  }

  .hero-title {
    font-size: var(--text-hero);
    font-weight: var(--font-black);
    color: var(--text-black);
    line-height: var(--leading-tight);
    letter-spacing: var(--tracking-tight);
    margin-bottom: 2rem;
    text-transform: uppercase;
  }

  .hero-image {
    width: 100%;
    margin-top: 2rem;
  }

  .hero-img {
    width: 100%;
    height: auto;
    display: block;
    filter: grayscale(100%); /* Black & white effect */
  }

  @media (max-width: 768px) {
    .hero-title {
      font-size: 3rem; /* 48px on mobile */
    }
  }
</style>
```

**Note:** Place hero image at `/public/images/hero-people.jpg`

---

### BLOCK 1: ABOUT FOUNDATION (Blue Section)

**Component:** `AboutFoundation.astro`

**Content:**
```
ABOUT THE FOUNDATION

Serhiy Prytula Charity Foundation is one of the largest charitable foundations in Ukraine. Since 2014, it has been providing assistance to Ukraine's Defense Forces and civilians affected by Russian aggression.

We are the people's foundation, powered by donations.

During the full scale invasion, we've raised 300 millions EUR and counting.

Our mission is to protect Ukrainian and European security through the supply of modern technologies and the implementation of effective solutions.
```

**Design from Mockup:**
- 🔵 **Full-width blue background** (#0047FF)
- **White text** on blue
- Section title uppercase on left
- Body text on right side
- **No icons, no cards** - just text blocks
- Two-column layout on desktop

**Code Example:**
```astro
---
// AboutFoundation.astro
---

<section class="about-section">
  <div class="container">
    <h2 class="section-title">ABOUT THE<br>FOUNDATION</h2>
    <div class="content">
      <p class="text-block">
        Serhiy Prytula Charity Foundation is one of the largest charitable foundations in Ukraine.
        Since 2014, it has been providing assistance to Ukraine's Defense Forces and civilians
        affected by Russian aggression.
      </p>
      <p class="text-block highlight">
        We are the people's foundation, powered by donations.
      </p>
      <p class="text-block">
        During the full scale invasion, we've raised <strong>300 millions EUR</strong> and counting.
      </p>
      <p class="text-block">
        Our mission is to protect Ukrainian and European security through the supply of modern
        technologies and the implementation of effective solutions.
      </p>
    </div>
  </div>
</section>

<style>
  .about-section {
    background: var(--bg-blue);
    padding: var(--section-padding-y) var(--section-padding-x);
    color: var(--text-white);
  }

  .container {
    max-width: var(--container-max);
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 4rem;
    align-items: start;
  }

  .section-title {
    font-size: var(--text-section-title);
    font-weight: var(--font-bold);
    line-height: var(--leading-tight);
    text-transform: uppercase;
    letter-spacing: var(--tracking-wide);
  }

  .content {
    display: flex;
    flex-direction: column;
    gap: var(--paragraph-gap);
  }

  .text-block {
    font-size: var(--text-body-large);
    line-height: var(--leading-normal);
  }

  .text-block.highlight {
    font-weight: var(--font-bold);
    font-size: 1.25rem;
  }

  .text-block strong {
    font-weight: var(--font-bold);
  }

  @media (max-width: 768px) {
    .container {
      grid-template-columns: 1fr;
      gap: 2rem;
    }

    .section-title {
      font-size: 2rem;
    }
  }
</style>
```

---

### BLOCK 2: ABOUT PRYTULA CHARITY FOUNDATION (Yellow Section)

**Component:** `AboutPrytulaFoundation.astro`

**Content:**
```
ABOUT PRYTULA CHARITY FOUNDATION

[Include "About Serhiy Prytula" and "About Ukrainian Hub" content from earlier,
plus "One Billion Fundraiser" information]
```

**Design from Mockup:**
- 🟡 **Full-width yellow background** (#FFD600)
- **Black text** on yellow
- Same two-column layout: title left, content right
- **No icons** - clean text blocks
- Multiple paragraphs/subsections

**Note:** This section combines several content pieces. Structure similar to Blue section but with yellow background.

**Code Example:**
```astro
---
// AboutPrytulaFoundation.astro
---

<section class="yellow-section">
  <div class="container">
    <h2 class="section-title">ABOUT PRYTULA<br>CHARITY<br>FOUNDATION</h2>
    <div class="content">
      <div class="subsection">
        <h3 class="subsection-title">ABOUT SERHIY PRYTULA</h3>
        <p class="text-block">
          Serhiy Prytula is a Ukrainian volunteer and founder of the Serhiy Prytula Charity Foundation,
          as well as a former leading host of one of Ukraine's most popular TV shows. Since 2014, he has
          been actively involved in humanitarian initiatives, and after Russia's full-scale invasion in 2022,
          he expanded his efforts with a team of over 100 people to provide aid to both the military and civilians.
        </p>
      </div>

      <div class="subsection">
        <h3 class="subsection-title">ABOUT UKRAINIAN HUB</h3>
        <p class="text-block">
          Ukrainian Hub is an international non-profit organization with offices in Ukraine, Portugal,
          and the United States. We empower Ukrainian entrepreneurs and displaced professionals through
          business education, mentoring, and global networking.
        </p>
      </div>

      <div class="subsection">
        <h3 class="subsection-title">ONE BILLION FUNDRAISER</h3>
        <p class="text-block">
          Together, we can prevent mass russian strikes on Ukrainian cities. [Add full content here]
        </p>
      </div>
    </div>
  </div>
</section>

<style>
  .yellow-section {
    background: var(--bg-yellow);
    padding: var(--section-padding-y) var(--section-padding-x);
    color: var(--text-black);
  }

  .container {
    max-width: var(--container-max);
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 4rem;
    align-items: start;
  }

  .section-title {
    font-size: var(--text-section-title);
    font-weight: var(--font-bold);
    line-height: var(--leading-tight);
    text-transform: uppercase;
    letter-spacing: var(--tracking-wide);
  }

  .content {
    display: flex;
    flex-direction: column;
    gap: var(--content-gap);
  }

  .subsection {
    margin-bottom: var(--content-gap);
  }

  .subsection-title {
    font-size: 1.125rem;
    font-weight: var(--font-bold);
    margin-bottom: 0.5rem;
    text-transform: uppercase;
  }

  .text-block {
    font-size: var(--text-body-large);
    line-height: var(--leading-normal);
  }

  @media (max-width: 768px) {
    .container {
      grid-template-columns: 1fr;
      gap: 2rem;
    }

    .section-title {
      font-size: 2rem;
    }
  }
</style>
```

---

### BLOCK 3: WHY PRYTULA FOUNDATION? (White Section)

**Component:** `WhyPrytula.astro`

**Content:** Same 4 reasons (Transparent, Experts, Reliable, Effective)

**Design from Mockup:**
- ⚪ **White background**
- **No cards, no icons** - simple text blocks in columns
- Title on top, then 2-3 column text layout
- Clean, minimal typography

**Code Example:**
```astro
---
// WhyPrytula.astro
---

<section class="why-section">
  <div class="container">

    <h2 class="section-title">WHY THE SERHIY PRYTULA CHARITY FOUNDATION?</h2>

    <div class="cards-grid">

      <!-- Transparent -->
      <article class="reason-card">
        <div class="card-icon blue">🔍</div>
        <h3 class="card-title">WE ARE TRANSPARENT</h3>
        <p class="card-text">
          Our reputation is crucial to us. Millions of people entrust us with their continuous donations,
          thousands of military personnel trust us with their lives. We provide detailed, publicly accessible
          reports on every procurement, and all donors can track how their contributions are used. Open financial
          reports for each procurement are available on our official website.
        </p>
      </article>

      <!-- Experts -->
      <article class="reason-card">
        <div class="card-icon green">🎓</div>
        <h3 class="card-title">WE ARE EXPERTS</h3>
        <p class="card-text">
          We are one of Ukraine's most trusted, knowledgeable and experienced organizations in the field of
          military technology and defense support. We possess unmatched expertise in identifying the real needs
          of the Ukrainian military across all frontlines and sourcing high-quality equipment at the best prices.
        </p>
      </article>

      <!-- Reliable -->
      <article class="reason-card">
        <div class="card-icon orange">✅</div>
        <h3 class="card-title">WE ARE RELIABLE</h3>
        <p class="card-text">
          The Serhiy Prytula Charity Foundation is one of the biggest and most impactful charitable foundations
          in Ukraine, dedicated to providing aid to the Defence Forces of Ukraine and civilians affected by
          russian aggression.
        </p>
      </article>

      <!-- Effective -->
      <article class="reason-card">
        <div class="card-icon yellow">⚡</div>
        <h3 class="card-title">WE ARE EFFECTIVE</h3>
        <p class="card-text">
          We ensure that your charitable contributions are used effectively by maintaining constant communication
          with military headquarters and local authorities at various levels.
        </p>
      </article>

    </div>

  </div>
</section>

<style>
  .why-section {
    padding: var(--section-padding-y) var(--space-4);
    background: var(--bg-secondary);
  }

  .container {
    max-width: var(--container-xl);
    margin: 0 auto;
  }

  .section-title {
    font-size: var(--text-4xl);
    font-weight: var(--font-bold);
    text-align: center;
    color: var(--color-primary);
    margin-bottom: var(--space-12);
  }

  .cards-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: var(--space-6);
  }

  .reason-card {
    background: white;
    border: 2px solid var(--color-gray-300);
    border-radius: var(--radius-xl);
    padding: var(--space-8);
    text-align: center;
    transition: all 0.3s ease;
    box-shadow: var(--shadow-md);
  }

  .reason-card:hover {
    transform: translateY(-8px);
    box-shadow: var(--shadow-xl);
  }

  .card-icon {
    font-size: 4rem;
    margin-bottom: var(--space-4);
    display: inline-block;
    width: 100px;
    height: 100px;
    line-height: 100px;
    border-radius: 50%;
    background: var(--bg-secondary);
  }

  .card-icon.blue {
    background: #dbeafe;
  }

  .card-icon.green {
    background: #d1fae5;
  }

  .card-icon.orange {
    background: #fed7aa;
  }

  .card-icon.yellow {
    background: #fef3c7;
  }

  .card-title {
    font-size: var(--text-xl);
    font-weight: var(--font-bold);
    color: var(--color-primary);
    margin-bottom: var(--space-4);
  }

  .card-text {
    font-size: var(--text-base);
    line-height: var(--leading-relaxed);
    color: var(--color-gray-700);
  }

  @media (max-width: 768px) {
    .section-title {
      font-size: var(--text-2xl);
    }

    .cards-grid {
      grid-template-columns: 1fr;
    }

    .card-icon {
      font-size: 3rem;
      width: 80px;
      height: 80px;
      line-height: 80px;
    }
  }
</style>
```

---

### BLOCK 4: HUMANITARIAN ACHIEVEMENTS

**Component:** `HumanAchievements.astro`

**Content:**

```
HUMANITARIAN ACHIEVEMENTS OF THE FOUNDATION

We raise funds and distribute them throughout several chosen areas of influence that make the lives of
Ukrainians better. We aim to help overcome the challenges the war brought to the everyday lives of people.
The total amount raised so far reaches over 650 million hryvnas and counting.

Areas of influence of humanitarian division:

HEALTHCARE
200+ medical institutions received equipment and medicines. Delivered 582,755 units of medicines and 528 units
of medical equipment. 764 visits by mobile medical teams. 26,229 consultations in the areas of primary and
secondary healthcare.

HUMANITARIAN DEMINING
Mechanical demining machine MP-3101, 10 ground robotic cleaning complexes "ZMIY" v 1.21, 26 armored vehicles,
559 units of equipment (pickup trucks, drones, metal detectors, blasting machines, protective suits, demining
kits, EW, and more).

SAFE & SMART: BUILDING AND EQUIPPING SHELTERS IN SCHOOLS
59 facilities filled with school equipment and appliances. Delivered 642 units of equipment. 1 site finished
and 2 are in the process of complete reconstruction of the shelter.

CRISIS EMERGENCY RESPONSE IN COMMUNITIES
7774 equipment items: boats, rescue suits, generators, boilers, pumps, water tanks, heaters, Starlinks for
heating points, medications, batteries, EWs, and more. 54 vehicles: 4 trucks, 21 minibuses, 23 SUVs.
10 special transport vehicles: 1 type C ambulance, 2 fire trucks, 3 sludge suction trucks, 4 tanker trucks.

NEST: TEMPORARY MODULAR HOUSING PROJECT
48 houses were installed throughout the project. Completed 16 house modifications and improvements.
358 units of household appliances have been delivered to those households, as well as 2 ventilation systems installed.
```

**Design:**
- Hero stat at top: "650M+ UAH raised"
- 5 columns or cards for each area
- Icons for each area
- Statistics highlighted in bold
- Light background

**Code Example:**
```astro
---
// HumanAchievements.astro
---

<section class="achievements-section">
  <div class="container">

    <h2 class="section-title">HUMANITARIAN ACHIEVEMENTS OF THE FOUNDATION</h2>

    <div class="intro-box">
      <p class="intro-text">
        We raise funds and distribute them throughout several chosen areas of influence that make the lives of
        Ukrainians better. We aim to help overcome the challenges the war brought to the everyday lives of people.
      </p>
      <div class="stat-hero">
        <span class="stat-number">650M+</span>
        <span class="stat-label">UAH raised and counting</span>
      </div>
    </div>

    <h3 class="subsection-title">Areas of influence of humanitarian division:</h3>

    <div class="areas-grid">

      <!-- Healthcare -->
      <article class="area-card">
        <div class="area-icon">🏥</div>
        <h4 class="area-title">HEALTHCARE</h4>
        <ul class="area-stats">
          <li><strong>200+</strong> medical institutions received equipment</li>
          <li><strong>582,755</strong> units of medicines delivered</li>
          <li><strong>528</strong> units of medical equipment</li>
          <li><strong>764</strong> visits by mobile medical teams</li>
          <li><strong>26,229</strong> consultations provided</li>
        </ul>
      </article>

      <!-- Demining -->
      <article class="area-card">
        <div class="area-icon">💣</div>
        <h4 class="area-title">HUMANITARIAN DEMINING</h4>
        <ul class="area-stats">
          <li>Mechanical demining machine <strong>MP-3101</strong></li>
          <li><strong>10</strong> ground robotic cleaning complexes "ZMIY"</li>
          <li><strong>26</strong> armored vehicles</li>
          <li><strong>559</strong> units of equipment (drones, metal detectors, protective suits, etc.)</li>
        </ul>
      </article>

      <!-- Safe & Smart -->
      <article class="area-card">
        <div class="area-icon">🏫</div>
        <h4 class="area-title">SAFE & SMART</h4>
        <p class="area-subtitle">Building and equipping shelters in schools</p>
        <ul class="area-stats">
          <li><strong>59</strong> facilities filled with equipment</li>
          <li><strong>642</strong> units of equipment delivered</li>
          <li><strong>1</strong> site finished, <strong>2</strong> in reconstruction</li>
        </ul>
      </article>

      <!-- Crisis Response -->
      <article class="area-card">
        <div class="area-icon">🚑</div>
        <h4 class="area-title">CRISIS EMERGENCY RESPONSE</h4>
        <ul class="area-stats">
          <li><strong>7,774</strong> equipment items (boats, generators, heaters, Starlinks, etc.)</li>
          <li><strong>54</strong> vehicles (trucks, minibuses, SUVs)</li>
          <li><strong>10</strong> special transport vehicles (ambulances, fire trucks, tankers)</li>
        </ul>
      </article>

      <!-- NEST -->
      <article class="area-card">
        <div class="area-icon">🏠</div>
        <h4 class="area-title">NEST</h4>
        <p class="area-subtitle">Temporary modular housing project</p>
        <ul class="area-stats">
          <li><strong>48</strong> houses installed</li>
          <li><strong>16</strong> house modifications completed</li>
          <li><strong>358</strong> units of household appliances delivered</li>
          <li><strong>2</strong> ventilation systems installed</li>
        </ul>
      </article>

    </div>

  </div>
</section>

<style>
  .achievements-section {
    padding: var(--section-padding-y) var(--space-4);
    background: white;
  }

  .container {
    max-width: var(--container-xl);
    margin: 0 auto;
  }

  .section-title {
    font-size: var(--text-4xl);
    font-weight: var(--font-bold);
    text-align: center;
    color: var(--color-primary);
    margin-bottom: var(--space-8);
  }

  .intro-box {
    background: var(--bg-secondary);
    border-radius: var(--radius-xl);
    padding: var(--space-8);
    margin-bottom: var(--space-12);
    text-align: center;
  }

  .intro-text {
    font-size: var(--text-lg);
    line-height: var(--leading-relaxed);
    color: var(--color-gray-700);
    margin-bottom: var(--space-6);
  }

  .stat-hero {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .stat-number {
    font-size: var(--text-6xl);
    font-weight: var(--font-bold);
    color: var(--color-primary);
    line-height: 1;
  }

  .stat-label {
    font-size: var(--text-xl);
    color: var(--color-gray-600);
    margin-top: var(--space-2);
  }

  .subsection-title {
    font-size: var(--text-2xl);
    font-weight: var(--font-semibold);
    color: var(--color-gray-900);
    margin-bottom: var(--space-8);
    text-align: center;
  }

  .areas-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: var(--space-6);
  }

  .area-card {
    background: white;
    border: 2px solid var(--color-gray-300);
    border-radius: var(--radius-lg);
    padding: var(--space-6);
    transition: all 0.3s ease;
  }

  .area-card:hover {
    border-color: var(--color-primary);
    box-shadow: var(--shadow-lg);
  }

  .area-icon {
    font-size: var(--text-5xl);
    margin-bottom: var(--space-4);
    text-align: center;
  }

  .area-title {
    font-size: var(--text-xl);
    font-weight: var(--font-bold);
    color: var(--color-primary);
    margin-bottom: var(--space-2);
    text-align: center;
  }

  .area-subtitle {
    font-size: var(--text-sm);
    color: var(--color-gray-600);
    margin-bottom: var(--space-4);
    text-align: center;
    font-style: italic;
  }

  .area-stats {
    list-style: none;
    padding: 0;
  }

  .area-stats li {
    font-size: var(--text-sm);
    line-height: var(--leading-relaxed);
    color: var(--color-gray-700);
    margin-bottom: var(--space-2);
    padding-left: var(--space-4);
    position: relative;
  }

  .area-stats li::before {
    content: "✓";
    position: absolute;
    left: 0;
    color: var(--color-success);
    font-weight: var(--font-bold);
  }

  .area-stats strong {
    font-weight: var(--font-bold);
    color: var(--color-primary-dark);
  }

  @media (max-width: 768px) {
    .section-title {
      font-size: var(--text-2xl);
    }

    .stat-number {
      font-size: var(--text-4xl);
    }

    .areas-grid {
      grid-template-columns: 1fr;
    }
  }
</style>
```

---

### BLOCK 5: PRYTULA FOUNDATION USA

**Component:** `PrytulaUSA.astro`

**Content:**

```
PRYTULA FOUNDATION USA

Prytula Foundation U.S.A. is a recognized 501(c)(3) nonprofit, established in 2024 in Chicago, Illinois.
We focus specifically on healthcare and kids projects, as well as humanitarian demining programs. During the
first year we have successfully raised $5.7M and provided $5.4M in direct aid. For full details, please check
our Annual Report, Auditors Report and 990 Form on our website prytulafoundation.us
```

**Design:**
- Centered card or banner
- 501(c)(3) badge/icon
- Statistics highlighted
- Link to prytulafoundation.us
- Light blue or white background

**Code Example:**
```astro
---
// PrytulaUSA.astro
---

<section class="usa-section">
  <div class="container">

    <article class="usa-card">
      <div class="usa-badge">501(c)(3)</div>
      <h2 class="usa-title">PRYTULA FOUNDATION USA</h2>

      <p class="usa-text">
        Prytula Foundation U.S.A. is a recognized <strong>501(c)(3) nonprofit</strong>, established in 2024
        in Chicago, Illinois. We focus specifically on healthcare and kids projects, as well as humanitarian
        demining programs.
      </p>

      <div class="stats-row">
        <div class="stat-item">
          <span class="stat-value">$5.7M</span>
          <span class="stat-label">Raised in 2024</span>
        </div>
        <div class="stat-item">
          <span class="stat-value">$5.4M</span>
          <span class="stat-label">Direct Aid Provided</span>
        </div>
      </div>

      <p class="usa-text">
        For full details, please check our Annual Report, Auditors Report and 990 Form on our website.
      </p>

      <a href="https://prytulafoundation.us" class="usa-link" target="_blank" rel="noopener">
        Visit prytulafoundation.us →
      </a>
    </article>

  </div>
</section>

<style>
  .usa-section {
    padding: var(--section-padding-y) var(--space-4);
    background: linear-gradient(135deg, #e0f2fe 0%, #dbeafe 100%);
  }

  .container {
    max-width: var(--container-md);
    margin: 0 auto;
  }

  .usa-card {
    background: white;
    border: 3px solid var(--color-primary);
    border-radius: var(--radius-xl);
    padding: var(--space-12) var(--space-8);
    text-align: center;
    box-shadow: var(--shadow-xl);
    position: relative;
  }

  .usa-badge {
    position: absolute;
    top: -20px;
    left: 50%;
    transform: translateX(-50%);
    background: var(--color-primary);
    color: white;
    font-size: var(--text-sm);
    font-weight: var(--font-bold);
    padding: var(--space-2) var(--space-6);
    border-radius: var(--radius-full);
    box-shadow: var(--shadow-md);
  }

  .usa-title {
    font-size: var(--text-3xl);
    font-weight: var(--font-bold);
    color: var(--color-primary);
    margin-bottom: var(--space-6);
  }

  .usa-text {
    font-size: var(--text-lg);
    line-height: var(--leading-relaxed);
    color: var(--color-gray-700);
    margin-bottom: var(--space-6);
  }

  .usa-text strong {
    font-weight: var(--font-bold);
    color: var(--color-primary);
  }

  .stats-row {
    display: flex;
    justify-content: center;
    gap: var(--space-12);
    margin: var(--space-8) 0;
  }

  .stat-item {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .stat-value {
    font-size: var(--text-4xl);
    font-weight: var(--font-bold);
    color: var(--color-primary);
    line-height: 1;
  }

  .stat-label {
    font-size: var(--text-sm);
    color: var(--color-gray-600);
    margin-top: var(--space-2);
  }

  .usa-link {
    display: inline-block;
    font-size: var(--text-lg);
    font-weight: var(--font-semibold);
    color: var(--color-primary);
    text-decoration: none;
    padding: var(--space-3) var(--space-6);
    border: 2px solid var(--color-primary);
    border-radius: var(--radius-lg);
    transition: all 0.3s ease;
  }

  .usa-link:hover {
    background: var(--color-primary);
    color: white;
  }

  @media (max-width: 768px) {
    .usa-title {
      font-size: var(--text-2xl);
    }

    .stats-row {
      flex-direction: column;
      gap: var(--space-6);
    }

    .stat-value {
      font-size: var(--text-3xl);
    }
  }
</style>
```

---

### BLOCK 6: COOL STORIES

**Component:** `CoolStories.astro`

**Content:**

```
COOL STORIES

WE BOUGHT A SATELLITE
In September 2022, the Serhiy Prytula Foundation made history: we purchased full access to an ICEYE satellite
and its data network for the Ukrainian Armed Forces. This extraordinary achievement was funded by the $16M from
the "People's Bayraktar" fundraising campaign, when the Turkish manufacturer, Baykar, donated the drones to
Ukraine for free. The satellite provides critical Synthetic Aperture Radar (SAR) imagery, allowing the military
to receive constant, all-weather, day-and-night surveillance of critical enemy locations. This is a game-changer
for operational planning and has already proven its worth by helping to destroy russian equipment whose value far
exceeded the cost of the contract.

EUROVISION SONG CONTEST ANNUAL FUNDRAISER
We proudly leverage the international attention on the Eurovision Song Contest to support Ukraine's vital defense
needs. For example, the funds raised during the 2024 National Selection for Eurovision were dedicated to humanitarian
demining efforts. This ongoing collaboration helps purchase Ukrainian-made, NATO-certified robotic demining machines
like the "ZMIY." This initiative effectively uses the global visibility of music to secure practical, life-saving
equipment that directly contributes to the safety and future restoration of war-affected territories.
```

**Design:**
- 2 story cards side-by-side (desktop) or stacked (mobile)
- Each with icon (🛰️ Satellite, 🎤 Eurovision)
- Timeline style or narrative cards
- Highlight key facts ($16M, 2022, ICEYE, ZMIY)

**Code Example:**
```astro
---
// CoolStories.astro
---

<section class="stories-section">
  <div class="container">

    <h2 class="section-title">COOL STORIES</h2>

    <div class="stories-grid">

      <!-- Satellite Story -->
      <article class="story-card">
        <div class="story-icon">🛰️</div>
        <h3 class="story-title">WE BOUGHT A SATELLITE</h3>
        <div class="story-meta">
          <span class="meta-tag">September 2022</span>
          <span class="meta-tag">$16M</span>
          <span class="meta-tag">ICEYE</span>
        </div>
        <p class="story-text">
          In September 2022, the Serhiy Prytula Foundation made history: we purchased full access to an
          <strong>ICEYE satellite</strong> and its data network for the Ukrainian Armed Forces. This extraordinary
          achievement was funded by the <strong>$16M</strong> from the "People's Bayraktar" fundraising campaign,
          when the Turkish manufacturer, Baykar, donated the drones to Ukraine for free.
        </p>
        <p class="story-text">
          The satellite provides critical Synthetic Aperture Radar (SAR) imagery, allowing the military to receive
          constant, all-weather, day-and-night surveillance of critical enemy locations. This is a game-changer for
          operational planning and has already proven its worth by helping to destroy russian equipment whose value
          far exceeded the cost of the contract.
        </p>
      </article>

      <!-- Eurovision Story -->
      <article class="story-card">
        <div class="story-icon">🎤</div>
        <h3 class="story-title">EUROVISION SONG CONTEST ANNUAL FUNDRAISER</h3>
        <div class="story-meta">
          <span class="meta-tag">Annual</span>
          <span class="meta-tag">2024</span>
          <span class="meta-tag">ZMIY</span>
        </div>
        <p class="story-text">
          We proudly leverage the international attention on the Eurovision Song Contest to support Ukraine's vital
          defense needs. For example, the funds raised during the <strong>2024 National Selection</strong> for
          Eurovision were dedicated to humanitarian demining efforts.
        </p>
        <p class="story-text">
          This ongoing collaboration helps purchase Ukrainian-made, NATO-certified robotic demining machines like
          the <strong>"ZMIY."</strong> This initiative effectively uses the global visibility of music to secure
          practical, life-saving equipment that directly contributes to the safety and future restoration of
          war-affected territories.
        </p>
      </article>

    </div>

  </div>
</section>

<style>
  .stories-section {
    padding: var(--section-padding-y) var(--space-4);
    background: var(--bg-secondary);
  }

  .container {
    max-width: var(--container-xl);
    margin: 0 auto;
  }

  .section-title {
    font-size: var(--text-4xl);
    font-weight: var(--font-bold);
    text-align: center;
    color: var(--color-primary);
    margin-bottom: var(--space-12);
  }

  .stories-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
    gap: var(--space-8);
  }

  .story-card {
    background: white;
    border-left: 5px solid var(--color-accent);
    border-radius: var(--radius-lg);
    padding: var(--space-8);
    box-shadow: var(--shadow-lg);
    transition: all 0.3s ease;
  }

  .story-card:hover {
    transform: translateX(8px);
    box-shadow: var(--shadow-xl);
  }

  .story-icon {
    font-size: var(--text-5xl);
    margin-bottom: var(--space-4);
  }

  .story-title {
    font-size: var(--text-2xl);
    font-weight: var(--font-bold);
    color: var(--color-primary);
    margin-bottom: var(--space-4);
    line-height: var(--leading-tight);
  }

  .story-meta {
    display: flex;
    gap: var(--space-2);
    margin-bottom: var(--space-6);
    flex-wrap: wrap;
  }

  .meta-tag {
    display: inline-block;
    font-size: var(--text-xs);
    font-weight: var(--font-semibold);
    color: white;
    background: var(--color-primary);
    padding: var(--space-1) var(--space-3);
    border-radius: var(--radius-full);
  }

  .story-text {
    font-size: var(--text-base);
    line-height: var(--leading-relaxed);
    color: var(--color-gray-700);
    margin-bottom: var(--space-4);
  }

  .story-text strong {
    font-weight: var(--font-bold);
    color: var(--color-primary-dark);
  }

  @media (max-width: 768px) {
    .section-title {
      font-size: var(--text-2xl);
    }

    .stories-grid {
      grid-template-columns: 1fr;
    }

    .story-title {
      font-size: var(--text-xl);
    }
  }
</style>
```

---

### BLOCK 7: VIDEOS + CONTACTS

**Component:** `VideosContacts.astro`

**Content:**

```
VIDEOS

1. Serhiy's interview for BBC
2. Video of Shahed strike impacts
3. Video about humanitarian projects

CONTACTS

Website: https://prytulafoundation.org/en
Email: m.radynska@prytulafoundation.org
Phone: +380673433090
```

**Design:**
- 3 video placeholders (16:9 ratio boxes)
- Each with title overlay
- Below: contact info in clean layout
- Social media icons
- Dark background for contrast

**Code Example:**
```astro
---
// VideosContacts.astro
---

<section class="videos-section">
  <div class="container">

    <h2 class="section-title">VIDEOS</h2>
    <p class="section-subtitle">Learn more about our work through these videos</p>

    <div class="videos-grid">

      <!-- Video 1 Placeholder -->
      <div class="video-placeholder">
        <div class="placeholder-content">
          <span class="placeholder-icon">▶️</span>
          <p class="placeholder-text">Serhiy's interview for BBC</p>
          <p class="placeholder-note">Video will be added soon</p>
        </div>
      </div>

      <!-- Video 2 Placeholder -->
      <div class="video-placeholder">
        <div class="placeholder-content">
          <span class="placeholder-icon">▶️</span>
          <p class="placeholder-text">Shahed strike impact footage</p>
          <p class="placeholder-note">Video will be added soon</p>
        </div>
      </div>

      <!-- Video 3 Placeholder -->
      <div class="video-placeholder">
        <div class="placeholder-content">
          <span class="placeholder-icon">▶️</span>
          <p class="placeholder-text">Humanitarian projects overview</p>
          <p class="placeholder-note">Video will be added soon</p>
        </div>
      </div>

    </div>

  </div>
</section>

<section class="contacts-section">
  <div class="container">

    <h2 class="section-title">CONTACTS</h2>

    <div class="contacts-grid">

      <div class="contact-item">
        <span class="contact-icon">🌐</span>
        <span class="contact-label">Website</span>
        <a href="https://prytulafoundation.org/en" class="contact-link" target="_blank">
          prytulafoundation.org/en
        </a>
      </div>

      <div class="contact-item">
        <span class="contact-icon">✉️</span>
        <span class="contact-label">Email</span>
        <a href="mailto:m.radynska@prytulafoundation.org" class="contact-link">
          m.radynska@prytulafoundation.org
        </a>
      </div>

      <div class="contact-item">
        <span class="contact-icon">📞</span>
        <span class="contact-label">Phone</span>
        <a href="tel:+380673433090" class="contact-link">
          +380 67 343 3090
        </a>
      </div>

    </div>

  </div>
</section>

<style>
  /* Videos Section */
  .videos-section {
    padding: var(--section-padding-y) var(--space-4);
    background: white;
  }

  .container {
    max-width: var(--container-xl);
    margin: 0 auto;
  }

  .section-title {
    font-size: var(--text-4xl);
    font-weight: var(--font-bold);
    text-align: center;
    color: var(--color-primary);
    margin-bottom: var(--space-4);
  }

  .section-subtitle {
    font-size: var(--text-lg);
    text-align: center;
    color: var(--color-gray-600);
    margin-bottom: var(--space-12);
  }

  .videos-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: var(--space-6);
  }

  .video-placeholder {
    aspect-ratio: 16 / 9;
    background: linear-gradient(135deg, #e5e7eb 0%, #d1d5db 100%);
    border: 2px dashed var(--color-gray-400);
    border-radius: var(--radius-lg);
    display: flex;
    align-items: center;
    justify-content: center;
    padding: var(--space-6);
    transition: all 0.3s ease;
  }

  .video-placeholder:hover {
    border-color: var(--color-primary);
    background: linear-gradient(135deg, #dbeafe 0%, #bfdbfe 100%);
  }

  .placeholder-content {
    text-align: center;
  }

  .placeholder-icon {
    font-size: var(--text-5xl);
    display: block;
    margin-bottom: var(--space-3);
  }

  .placeholder-text {
    font-size: var(--text-lg);
    font-weight: var(--font-semibold);
    color: var(--color-gray-900);
    margin-bottom: var(--space-2);
  }

  .placeholder-note {
    font-size: var(--text-sm);
    color: var(--color-gray-600);
    font-style: italic;
  }

  /* Contacts Section */
  .contacts-section {
    padding: var(--section-padding-y) var(--space-4);
    background: var(--bg-dark);
    color: white;
  }

  .contacts-section .section-title {
    color: white;
    margin-bottom: var(--space-12);
  }

  .contacts-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: var(--space-8);
    max-width: var(--container-lg);
    margin: 0 auto;
  }

  .contact-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: var(--space-6);
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: var(--radius-lg);
    transition: all 0.3s ease;
  }

  .contact-item:hover {
    background: rgba(255, 255, 255, 0.1);
    transform: translateY(-4px);
  }

  .contact-icon {
    font-size: var(--text-4xl);
    margin-bottom: var(--space-3);
  }

  .contact-label {
    font-size: var(--text-sm);
    font-weight: var(--font-semibold);
    color: var(--color-gray-400);
    text-transform: uppercase;
    letter-spacing: 0.05em;
    margin-bottom: var(--space-2);
  }

  .contact-link {
    font-size: var(--text-lg);
    font-weight: var(--font-medium);
    color: var(--color-accent);
    text-decoration: none;
    transition: color 0.3s ease;
  }

  .contact-link:hover {
    color: var(--color-accent-hover);
    text-decoration: underline;
  }

  @media (max-width: 768px) {
    .section-title {
      font-size: var(--text-2xl);
    }

    .videos-grid,
    .contacts-grid {
      grid-template-columns: 1fr;
    }
  }
</style>
```

---

## 🚀 STEP-BY-STEP IMPLEMENTATION PLAN

### Phase 1: Setup Structure (15 minutes)

**Step 1.1:** Create component directory
```bash
mkdir -p src/components/websummit
```

**Step 1.2:** Create all component files (empty shells)
```bash
touch src/components/websummit/{HeroSection,AboutFoundation,OneBillionFundraiser,WhyPrytula,HumanAchievements,PrytulaUSA,CoolStories,VideosContacts,DonateButton}.astro
```

### Phase 2: Create Reusable Components (30 minutes)

**Step 2.1:** Create `DonateButton.astro`
```astro
---
// src/components/websummit/DonateButton.astro
interface Props {
  href: string;
  text: string;
  variant?: 'default' | 'large';
}

const { href, text, variant = 'default' } = Astro.props;
---

<a href={href} class={`donate-btn donate-btn--${variant}`}>
  {text}
</a>

<style>
  .donate-btn {
    display: inline-block;
    padding: var(--space-4) var(--space-8);
    background: var(--color-accent);
    color: var(--color-black);
    font-size: var(--text-lg);
    font-weight: var(--font-bold);
    text-decoration: none;
    border-radius: var(--radius-lg);
    transition: all 0.3s ease;
    box-shadow: var(--shadow-md);
  }

  .donate-btn:hover {
    background: var(--color-accent-hover);
    transform: translateY(-2px);
    box-shadow: var(--shadow-lg);
  }

  .donate-btn--large {
    padding: var(--space-6) var(--space-12);
    font-size: var(--text-xl);
  }
</style>
```

**Step 2.2:** Create each main component (use code examples from detailed sections above)

### Phase 3: Update Global Styles (20 minutes)

**Step 3.1:** Extend `/src/styles/index.css` with design system variables

Add to beginning of file:
```css
/* Design System Variables - Based on Desktop.png and Mobile.png */
:root {
  /* Brand Colors from Mockup */
  --color-blue: #0047FF;
  --color-yellow: #FFD600;
  --color-black: #000000;
  --color-white: #FFFFFF;

  /* Background Colors */
  --bg-white: #FFFFFF;
  --bg-blue: #0047FF;
  --bg-yellow: #FFD600;
  --bg-gray-light: #F5F5F5;

  /* Text Colors */
  --text-black: #000000;
  --text-white: #FFFFFF;
  --text-gray: #666666;

  /* Typography */
  --font-primary: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  --text-hero: 5rem;              /* 80px - Hero title */
  --text-section-title: 2.5rem;   /* 40px - Section headings */
  --text-body: 1rem;              /* 16px - Body text */
  --text-body-large: 1.125rem;    /* 18px - Larger body */
  --font-regular: 400;
  --font-bold: 700;
  --font-black: 900;
  --leading-tight: 1.1;
  --leading-normal: 1.5;
  --leading-relaxed: 1.7;
  --tracking-tight: -0.02em;
  --tracking-normal: 0;
  --tracking-wide: 0.05em;

  /* Spacing */
  --section-padding-y: 6rem;
  --section-padding-y-mobile: 3rem;
  --section-padding-x: 2rem;
  --content-gap: 2rem;
  --content-gap-large: 3rem;
  --paragraph-gap: 1rem;

  /* Container */
  --container-max: 1200px;
  --container-text: 800px;
  --container-full: 100%;
}

/* Base Styles */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: var(--font-primary);
  font-size: var(--text-body);
  line-height: var(--leading-normal);
  color: var(--text-black);
  background: var(--bg-white);
}

h1, h2, h3, h4, h5, h6 {
  font-weight: var(--font-bold);
  line-height: var(--leading-tight);
}

/* Smooth Scrolling */
html {
  scroll-behavior: smooth;
}
```

### Phase 4: Create New Homepage (30 minutes)

**Step 4.1:** Backup existing `index.astro`
```bash
mv src/pages/index.astro src/pages/index.astro.backup
```

**Step 4.2:** Create new `/src/pages/index.astro`
```astro
---
// src/pages/index.astro
import Layout from '../layouts/Layout.astro';
import HeroSection from '../components/websummit/HeroSection.astro';
import AboutFoundation from '../components/websummit/AboutFoundation.astro';
import AboutPrytulaFoundation from '../components/websummit/AboutPrytulaFoundation.astro';
import WhyPrytula from '../components/websummit/WhyPrytula.astro';
import HumanAchievements from '../components/websummit/HumanAchievements.astro';
import PrytulaUSA from '../components/websummit/PrytulaUSA.astro';
import CoolStories from '../components/websummit/CoolStories.astro';
import VideosContacts from '../components/websummit/VideosContacts.astro';

const pageTitle = "Safety for Ukrainians - Serhiy Prytula Charity Foundation";
const pageDescription = "Support Ukraine's defense and humanitarian efforts through the Serhiy Prytula Charity Foundation.";
---

<Layout title={pageTitle} description={pageDescription}>
  <main>
    <HeroSection />               <!-- White: "SAFETY FOR UKRAINIANS" + photo -->
    <AboutFoundation />           <!-- Blue: Foundation info -->
    <AboutPrytulaFoundation />    <!-- Yellow: Serhiy + Ukrainian Hub + Fundraiser -->
    <WhyPrytula />                <!-- White: 4 reasons -->
    <HumanAchievements />         <!-- Gray: Humanitarian stats -->
    <PrytulaUSA />                <!-- White: 501(c)(3) info -->
    <CoolStories />               <!-- White: Satellite + Eurovision -->
    <VideosContacts />            <!-- Gray: Videos + Contacts -->
  </main>
</Layout>

<style>
  main {
    width: 100%;
  }
</style>
```

### Phase 5: Update Shared Components (20 minutes)

**Step 5.1:** Simplify `Header.astro` (remove language switcher)

Read current `/src/components/Header.astro` and remove:
- LanguageSwitcher component import
- Multilingual text (keep only English)
- Simplify to just logo + link

**Step 5.2:** Update `Footer.astro` with new contacts

Update footer to include:
- Email: m.radynska@prytulafoundation.org
- Phone: +380673433090
- Website link
- Keep only English text

### Phase 6: Testing & Optimization (30 minutes)

**Step 6.1:** Run development server
```bash
pnpm dev
```

**Step 6.2:** Visual testing checklist
- [ ] Hero section loads correctly
- [ ] All 7 blocks display in order
- [ ] Text is readable (contrast, sizing)
- [ ] Cards/buttons have hover effects
- [ ] Mobile responsive (375px, 768px, 1024px)
- [ ] No console errors
- [ ] Images/icons display correctly

**Step 6.3:** Performance check
```bash
pnpm build
pnpm preview
```

- Check Lighthouse score (target: 90+)
- Verify no build errors
- Test in production mode

### Phase 7: Final Touches (15 minutes)

**Step 7.1:** Add scroll-to-top button (optional)

**Step 7.2:** Add smooth scroll behavior (already in CSS)

**Step 7.3:** Update meta tags in Layout
```astro
<!-- In src/layouts/Layout.astro -->
<meta name="description" content={description}>
<meta property="og:title" content={title}>
<meta property="og:description" content={description}>
<meta property="og:type" content="website">
<meta name="twitter:card" content="summary_large_image">
```

---

## ✅ IMPLEMENTATION CHECKLIST

### Pre-Implementation
- [ ] Backup current `index.astro`
- [ ] Review design reference PNG (place in `/design-refs/`)
- [ ] Confirm donation link: https://prytulafoundation.org/en

### Component Creation
- [ ] Create `/src/components/websummit/` directory
- [ ] `DonateButton.astro` component
- [ ] `HeroSection.astro` component
- [ ] `AboutFoundation.astro` component
- [ ] `OneBillionFundraiser.astro` component
- [ ] `WhyPrytula.astro` component
- [ ] `HumanAchievements.astro` component
- [ ] `PrytulaUSA.astro` component
- [ ] `CoolStories.astro` component
- [ ] `VideosContacts.astro` component

### Styling
- [ ] Add design system variables to `index.css`
- [ ] Test all color variables render correctly
- [ ] Verify spacing consistency
- [ ] Check font loading (Inter)

### Page Assembly
- [ ] Create new `index.astro` with all imports
- [ ] Verify correct component order
- [ ] Test Hero CTA button links
- [ ] Check all internal links work

### Header/Footer Updates
- [ ] Simplify Header (English only)
- [ ] Update Footer contacts
- [ ] Remove LanguageSwitcher references
- [ ] Test navigation links

### Content Review
- [ ] All text from BLOCKS 1-7 included
- [ ] No typos or grammar errors
- [ ] Links are correct and open properly
- [ ] Contact details are accurate

### Responsive Testing
- [ ] Mobile (375px width)
- [ ] Tablet (768px width)
- [ ] Desktop (1280px width)
- [ ] Large desktop (1440px+ width)
- [ ] All sections stack correctly on mobile
- [ ] Text remains readable at all sizes

### Performance
- [ ] Run `pnpm build` successfully
- [ ] Lighthouse score: Performance 90+
- [ ] Lighthouse score: Accessibility 90+
- [ ] Lighthouse score: Best Practices 90+
- [ ] No console errors or warnings
- [ ] Images optimized (if any added later)

### Browser Testing
- [ ] Chrome
- [ ] Firefox
- [ ] Safari
- [ ] Edge

### Final Steps
- [ ] Clear browser cache and test
- [ ] Test on actual mobile device
- [ ] Verify analytics (Plausible) still working
- [ ] Commit changes to git
- [ ] Deploy to Vercel
- [ ] Test live deployment

---

## 🎯 DESIGN REFERENCE INTEGRATION

### Where to Place Your Design PNG

Place your design reference file here:
```
/design-refs/websummit-page-design.png
```

### How to Reference It During Development

1. **Open the PNG in a separate window** while coding
2. **Match colors** using browser color picker or design tools
3. **Measure spacing** using your design tool or browser DevTools
4. **Extract exact fonts** if different from Inter
5. **Identify icon requirements** - note any custom icons needed

### Design Checklist
- [ ] PNG file placed in `/design-refs/`
- [ ] Colors extracted and added to CSS variables
- [ ] Fonts identified (default: Inter)
- [ ] Icon requirements documented
- [ ] Spacing measurements noted
- [ ] Button styles matched
- [ ] Card designs replicated

---

## 📚 ADDITIONAL NOTES

### Future Video Integration

When videos become available, update `/src/components/websummit/VideosContacts.astro`:

**For YouTube:**
```html
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/VIDEO_ID"
  frameborder="0"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen>
</iframe>
```

**For Vimeo:**
```html
<iframe
  src="https://player.vimeo.com/video/VIDEO_ID"
  width="560"
  height="315"
  frameborder="0"
  allow="autoplay; fullscreen; picture-in-picture"
  allowfullscreen>
</iframe>
```

**For Local Video Files:**
```html
<video controls width="100%">
  <source src="/videos/filename.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
```

### Deployment

After implementation:

1. **Commit to Git:**
```bash
git add .
git commit -m "feat: WebSummit 2025 landing page with 7 content blocks"
git push origin main
```

2. **Vercel Auto-Deploy:**
- Vercel will automatically detect the push
- Build process starts automatically
- Preview URL generated
- Live site updates after successful build

3. **Verify Deployment:**
- Check Vercel dashboard for build logs
- Test preview URL
- Confirm production domain updates

### SEO Optimization

Add to `/src/layouts/Layout.astro`:
```html
<meta name="keywords" content="Ukraine, charity, Serhiy Prytula, WebSummit, humanitarian aid, defense support">
<meta name="author" content="Serhiy Prytula Charity Foundation">
<link rel="canonical" href="https://prytulafoundation.org/en">
```

### Analytics Tracking

Ensure Plausible.io is configured (already in current Layout):
```html
<script defer data-domain="prytulafoundation.org" src="https://plausible.io/js/script.js"></script>
```

---

## 🔧 TROUBLESHOOTING

### Common Issues

**Issue:** Components not displaying
- **Solution:** Check import paths in `index.astro`
- **Solution:** Verify component file names match imports

**Issue:** Styles not applying
- **Solution:** Check CSS variable names match
- **Solution:** Verify `index.css` is imported in Layout
- **Solution:** Clear browser cache

**Issue:** Build fails
- **Solution:** Run `pnpm astro check` for TypeScript errors
- **Solution:** Check for missing closing tags
- **Solution:** Verify all imports exist

**Issue:** Mobile layout broken
- **Solution:** Check media queries in component styles
- **Solution:** Test grid/flex properties at smaller widths
- **Solution:** Verify `viewport` meta tag in Layout

**Issue:** Fonts not loading
- **Solution:** Check Google Fonts link in Layout head
- **Solution:** Verify font-family CSS variable usage
- **Solution:** Test font fallbacks

---

## 📞 SUPPORT & CONTACTS

**For Development Questions:**
- Review Astro docs: https://docs.astro.build
- Check existing components in `/src/components/`
- Reference this development plan

**For Content Updates:**
- Foundation info: https://prytulafoundation.org/en
- Contact: m.radynska@prytulafoundation.org

**For Technical Issues:**
- Astro Discord: https://astro.build/chat
- GitHub Issues: Create issue in project repo

---

## 📈 SUCCESS METRICS

### Must-Have (MVP)
- ✅ All 7 content blocks implemented
- ✅ Mobile responsive design
- ✅ Working CTA buttons
- ✅ Fast page load (<3s)
- ✅ No console errors

### Nice-to-Have (Future)
- 🎥 Videos integrated
- 🔗 Smooth anchor navigation
- ✨ Scroll animations
- 📊 Analytics dashboard
- 🌍 Multilingual support (if needed later)

---

**Document Version:** 1.0
**Last Updated:** 2025-01-10
**Next Review:** After implementation completion

---

---

## 📊 DESIGN UPDATE SUMMARY

### What Was Analyzed:
- ✅ **Desktop.png** - Full desktop mockup with color blocks
- ✅ **Mobile.png** - Mobile responsive layout

### Key Findings:

**Design Style:**
- **Minimalist** - No icons, no cards, no decorations
- **Color Blocks** - Full-width sections: Blue (#0047FF), Yellow (#FFD600), White, Gray
- **Grid Layout** - Title left (1 col) | Content right (2 cols)
- **Typography** - 80px hero, 40px section titles, 16-18px body

**Major Changes from Original Plan:**
1. ❌ **Removed:** All emoji icons, card borders, shadows, rounded corners
2. ❌ **Changed hero:** "SAFETY FOR UKRAINIANS" (not "TOGETHER DURING WEBSUMMIT")
3. ✅ **Added:** Full-width color block sections
4. ✅ **Simplified:** All components use same grid template
5. ✅ **Updated CSS:** New color variables (#0047FF blue, #FFD600 yellow)

### Component List (8 Total):
1. `HeroSection.astro` - White + B&W photo
2. `AboutFoundation.astro` - Blue section
3. `AboutPrytulaFoundation.astro` - Yellow section (combines multiple content)
4. `WhyPrytula.astro` - White section
5. `HumanAchievements.astro` - Gray section
6. `PrytulaUSA.astro` - White section
7. `CoolStories.astro` - White section
8. `VideosContacts.astro` - Gray section

### Quick Start Guide:

**For Claude Code:**
```
"Implement WebSummit 2025 landing page using:
- DEVELOPMENT_PLAN.md (this file)
- design-refs/Desktop.png (reference design)
- design-refs/Mobile.png (mobile layout)

Follow the UNIVERSAL SECTION TEMPLATE (line 69-136) for all sections.
Use updated CSS variables (line 1885-1958).
Refer to detailed component examples starting at line 277."
```

**Key Sections to Reference:**
- **Lines 15-136:** Design overview, principles, universal template
- **Lines 163-251:** Updated design system (colors, typography, spacing)
- **Lines 277-361:** Hero section example (updated)
- **Lines 365-474:** Block 1 example (blue section, updated)
- **Lines 478-595:** Block 2 example (yellow section, updated)
- **Lines 1885-1958:** Updated global CSS
- **Lines 1967-2003:** Updated index.astro structure

---

## 🎉 FINAL NOTES

This development plan provides:
1. ✅ Complete content for all 7 blocks
2. ✅ Updated design based on real mockups
3. ✅ Minimalist approach (no icons/cards)
4. ✅ Universal section template for consistency
5. ✅ Updated CSS design system
6. ✅ Step-by-step implementation guide

**Estimated Implementation Time:** 2-3 hours for experienced Astro developer

**Recommended Approach:**
1. Study the universal template (lines 69-136)
2. Implement CSS variables first (lines 1885-1958)
3. Create HeroSection (see line 277)
4. Create remaining sections using universal template
5. Test each section before moving to next
6. Final integration and responsive testing
7. Deploy when all sections working

**Design Files:**
- `/design-refs/Desktop.png` - Primary design reference
- `/design-refs/Mobile.png` - Mobile layout reference

Good luck with the implementation! 🚀🇺🇦
