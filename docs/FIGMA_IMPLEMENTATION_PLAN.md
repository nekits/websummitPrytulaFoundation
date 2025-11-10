# 🎨 План імплементації дизайну з Figma

**Проєкт:** WebSummit 2025 - Prytula Foundation Landing Page
**Figma файл:** [websammit](https://www.figma.com/design/rEE8igxX5JzipvzRnxX2ay/websammit)
**Дата створення:** 2025-11-10
**Статус:** В процесі планування

---

## 📋 Зміст

1. [Огляд змін](#огляд-змін)
2. [Детальний аналіз відмінностей](#детальний-аналіз-відмінностей)
3. [Етапи впровадження](#етапи-впровадження)
4. [Технічні специфікації](#технічні-специфікації)
5. [Чеклісти виконання](#чеклісти-виконання)

---

## 🎯 Огляд змін

### Ключові відмінності між поточним дизайном і Figma:

| Категорія | Поточний стан | Figma дизайн | Пріоритет |
|-----------|---------------|--------------|-----------|
| **Кольори** | Синій `#0047FF` | Синій `#5CADFF` | 🔴 Критично |
| **Hero текст** | 80px | 160px | 🔴 Критично |
| **Заголовки секцій** | 40px | 110px/80px/46px | 🔴 Критично |
| **Line-height** | 1.5 (нормальний) | 0.78-1.3 (щільний) | 🔴 Критично |
| **Letter-spacing** | -0.02em | -0.04em | 🟠 Важливо |
| **Border radius** | Не визначено | 33px | 🟠 Важливо |
| **Max width** | 1200px | 1920px | 🟠 Важливо |

---

## 📊 Детальний аналіз відмінностей

### 🎨 1. КОЛЬОРИ

#### Поточні кольори:
```css
--color-blue: #0047FF;        /* Темно-синій */
--bg-gray-light: #F5F5F5;     /* Світло-сірий */
--text-gray: #666666;         /* Темно-сірий */
```

#### Figma кольори:
```css
--color-blue: #5CADFF;        /* Світло-синій (основний бренд) */
--color-gray: #D9D9D9;        /* Сірий для блоків */
--bg-gray-light: #F8F8F8;     /* Світло-сірий фон */
--bg-neutral: #E5E5E5;        /* Нейтральний сірий */
```

**Проблема:** Повна невідповідність кольорів бренду. Синій занадто темний, сірі відтінки не збігаються.

**Вплив:** Високий - вся колірна схема сайту змінюється.

---

### 📝 2. ТИПОГРАФІКА

#### Font Sizes

| Елемент | Поточне | Figma | CSS Variable | Відмінність |
|---------|---------|-------|--------------|------------|
| **Hero Title** | 80px (5rem) | 160px (10rem) | `--text-hero` | **2x більше** |
| **Section XL** | 40px (2.5rem) | 110px (6.875rem) | `--text-section-xl` | **2.75x більше** |
| **Section LG** | 40px (2.5rem) | 80px (5rem) | `--text-section-lg` | **2x більше** |
| **Section MD** | - | 46px (2.875rem) | `--text-section-md` | **Новий розмір** |
| **Heading LG** | 24px (1.5rem) | 44px (2.75rem) | `--text-heading-lg` | **1.8x більше** |
| **Heading MD** | 20px (1.25rem) | 40px (2.5rem) | `--text-heading-md` | **2x більше** |
| **Heading SM** | - | 32px (2rem) | `--text-heading-sm` | **Новий розмір** |
| **Heading XS** | - | 30px (1.875rem) | `--text-heading-xs` | **Новий розмір** |
| **Body LG** | 18px (1.125rem) | 20px (1.25rem) | `--text-body-lg` | Майже ок |
| **Body Regular** | 16px (1rem) | 19px (1.1875rem) | `--text-body` | Трохи більше |

**Проблема:** Всі заголовки значно менші ніж в Figma. Втрачається виразність і hierarchy.

**Вплив:** Критичний - сайт виглядає менш імпактно.

---

#### Line-heights

| Елемент | Поточне | Figma | CSS Variable |
|---------|---------|-------|--------------|
| **Hero** | 1.1 | 0.78125 (125/160) | `--leading-hero` |
| **Section XL** | 1.1 | 0.818 (90/110) | `--leading-section-xl` |
| **Section LG** | 1.1 | 0.825 (66/80) | `--leading-section-lg` |
| **Section MD** | 1.1 | 1.0 (46/46) | `--leading-section-md` |
| **Heading LG** | 1.5 | 1.023 (45/44) | `--leading-heading-lg` |
| **Body** | 1.5 | 1.3 (26/20) | `--leading-body` |

**Проблема:** Поточні line-heights занадто великі, текст розріджений. В Figma дуже щільний, компактний дизайн.

**Вплив:** Високий - змінює візуальну щільність всього сайту.

---

#### Letter-spacing

| Елемент | Поточне | Figma | CSS Variable |
|---------|---------|-------|--------------|
| **Hero** | -0.02em | -0.04em (-6.4px) | `--tracking-hero` |
| **Sections** | -0.02em до 0.05em | -0.04em (-4.4px до -3.2px) | `--tracking-section-*` |
| **Headings** | -0.02em | -0.04em (-1.76px до -1.2px) | `--tracking-heading-*` |
| **Body** | 0 | -0.04em (-0.8px) | `--tracking-body` |

**Проблема:** Поточний tracking менш щільний або навіть розріджений (0.05em). Figma має єдиний -0.04em для всього.

**Вплів:** Середній - впливає на загальний ритм тексту.

---

### 📐 3. SPACING & LAYOUT

#### Container Widths

| Тип | Поточне | Figma | CSS Variable |
|-----|---------|-------|--------------|
| **Max Width** | 1200px | 1920px | `--container-max` |
| **Content Width** | 800px | 1200px (внутрішній) | `--container-content` |

**Проблема:** На широких екранах контент занадто стиснутий, не використовує повну ширину як в Figma.

---

#### Border Radius

| Елемент | Поточне | Figma | CSS Variable |
|---------|---------|-------|--------------|
| **Округлі блоки** | Не визначено | 33px | `--radius-md` |

**Проблема:** Багато елементів в Figma мають rounded corners з радіусом 33px - це не реалізовано.

---

### 🧩 4. АНАЛІЗ КОМПОНЕНТІВ

#### ✅ **HeroSection.astro** - Структура правильна, треба масштабувати

**Поточний стан:**
```astro
<h1 class="hero-title">
  SAFETY FOR UKRAINIANS
</h1>
```

**Стилі:**
```css
.hero-title {
  font-size: var(--text-hero);     /* Зараз 80px */
  font-weight: var(--font-black);  /* 900 ✅ */
  line-height: var(--leading-tight); /* 1.1 */
  letter-spacing: var(--tracking-tight); /* -0.02em */
}
```

**Що треба змінити:**
- `font-size`: 80px → 160px (після оновлення токена)
- `line-height`: 1.1 → 0.78
- `letter-spacing`: -0.02em → -0.04em

**Пріоритет:** 🔴 Критично

---

#### ⚠️ **AboutFoundation.astro** - Колір фону + типографіка

**Поточний стан:**
```css
.about-section {
  background: var(--bg-blue);  /* Зараз #0047FF */
}

.section-title {
  font-size: var(--text-section-title); /* 40px */
}
```

**Що треба змінити:**
1. Колір фону: `#0047FF` → `#5CADFF`
2. Розмір заголовка: 40px → 80px
3. Line-height та letter-spacing відповідно до нових токенів

**Пріоритет:** 🔴 Критично

---

#### ⚠️ **AboutPrytulaFoundation.astro** - Збільшити заголовки

**Поточний стан:**
```css
.section-title {
  font-size: var(--text-section-title); /* 40px */
}
```

**Що треба змінити:**
- Розмір заголовка: 40px → 110px (Section XL)
- Line-height: 1.1 → 0.818
- Letter-spacing: -0.02em → -0.04em

**Пріоритет:** 🔴 Критично

---

#### ✅ **WhyPrytula.astro** - Майже ок

**Що треба змінити:**
- Оновити типографіку заголовків згідно нових токенів
- Перевірити відповідність кольорів фону

**Пріоритет:** 🟠 Важливо

---

#### ⚠️ **HumanAchievements.astro** - Колір фону

**Що треба змінити:**
- Колір фону: `#F5F5F5` → `#F8F8F8`
- Оновити типографіку

**Пріоритет:** 🟠 Важливо

---

#### ⚠️ **PrytulaUSA.astro** - Додати border-radius

**Що треба змінити:**
- Додати `border-radius: var(--radius-md)` (33px) до badge/карток
- Оновити типографіку

**Пріоритет:** 🟠 Важливо

---

#### ✅ **CoolStories.astro** - Структура ок

**Що треба змінити:**
- Тільки оновлення типографіки згідно нових токенів

**Пріоритет:** 🟢 Нормально

---

#### ✅ **VideosContacts.astro** - Структура ок

**Що треба змінити:**
- Тільки оновлення типографіки згідно нових токенів

**Пріоритет:** 🟢 Нормально

---

## 🚀 Етапи впровадження

### 📍 ЕТАП 1: Критичні зміни в дизайн-токенах (2-3 години)

#### 1.1. Оновлення кольорів у `src/styles/global.css`

**Поточні:**
```css
--color-blue: #0047FF;
--bg-blue: #0047FF;
--bg-gray-light: #F5F5F5;
```

**Нові:**
```css
/* Brand Colors from Figma */
--color-blue: #5CADFF;
--color-yellow: #FFD600;
--color-black: #000000;
--color-white: #FFFFFF;
--color-gray: #D9D9D9;
--color-gray-light: #F8F8F8;
--color-neutral-100: #E5E5E5;

/* Background Colors */
--bg-white: #FFFFFF;
--bg-blue: #5CADFF;
--bg-yellow: #FFD600;
--bg-gray: #D9D9D9;
--bg-gray-light: #F8F8F8;
--bg-neutral: #E5E5E5;
```

---

#### 1.2. Оновлення типографіки у `src/styles/global.css`

**Розміри шрифтів:**
```css
/* Font Sizes from Figma */
--text-hero: 10rem;              /* 160px - Main hero title */
--text-hero-mobile: 3rem;        /* 48px - Mobile hero */
--text-section-xl: 6.875rem;     /* 110px - Large section titles */
--text-section-lg: 5rem;         /* 80px - Medium section titles */
--text-section-md: 2.875rem;     /* 46px - Small section titles */
--text-heading-lg: 2.75rem;      /* 44px - Large headings */
--text-heading-md: 2.5rem;       /* 40px - Medium headings */
--text-heading-sm: 2rem;         /* 32px - Small headings */
--text-heading-xs: 1.875rem;     /* 30px - XS headings */
--text-body-lg: 1.25rem;         /* 20px - Large body */
--text-body: 1.1875rem;          /* 19px - Regular body */
--text-body-sm: 1rem;            /* 16px - Small body */
```

**Line-heights:**
```css
/* Line Heights from Figma */
--leading-hero: 0.78125;         /* 125/160 - Hero */
--leading-section-xl: 0.818;     /* 90/110 - Section XL */
--leading-section-lg: 0.825;     /* 66/80 - Section LG */
--leading-section-md: 1;         /* 46/46 - Section MD */
--leading-heading-lg: 1.023;     /* 45/44 - Heading LG */
--leading-heading-md: 1.2;       /* 48/40 - Heading MD */
--leading-heading-sm: 0.656;     /* 21/32 - Heading SM */
--leading-heading-xs: 1.2;       /* 36/30 - Heading XS */
--leading-body: 1.3;             /* 26/20 - Body */
--leading-body-nav: 1.105;       /* 21/19 - Navigation */
```

**Letter-spacing:**
```css
/* Letter Spacing from Figma (всі -0.04em) */
--tracking-hero: -0.04em;        /* -6.4px / 160px */
--tracking-section-xl: -0.04em;  /* -4.4px / 110px */
--tracking-section-lg: -0.04em;  /* -3.2px / 80px */
--tracking-section-md: -0.04em;  /* -1.84px / 46px */
--tracking-heading-lg: -0.04em;  /* -1.76px / 44px */
--tracking-heading-md: -0.04em;  /* -1.6px / 40px */
--tracking-heading-sm: -0.04em;  /* -1.28px / 32px */
--tracking-heading-xs: -0.04em;  /* -1.2px / 30px */
--tracking-body: -0.04em;        /* -0.8px / 20px */
--tracking-body-nav: -0.04em;    /* -0.76px / 19px */
```

---

#### 1.3. Додавання нових spacing та layout токенів

```css
/* Spacing */
--section-padding-y: 6.25rem;     /* ~100px */
--section-padding-y-large: 12.5rem; /* ~200px */
--section-padding-y-mobile: 3rem; /* 48px */
--section-padding-x: 2rem;        /* 32px */
--section-padding-x-desktop: 4rem; /* 64px desktop */
--content-gap: 2rem;              /* 32px */
--content-gap-large: 4rem;        /* 64px */
--paragraph-gap: 1rem;            /* 16px */

/* Container */
--container-max: 1920px;          /* Full design width from Figma */
--container-content: 1280px;      /* Content max width */
--container-text: 800px;
--container-full: 100%;

/* Border Radius */
--radius-lg: 33px;                /* Large radius from Figma */
--radius-md: 20px;                /* Medium radius */
--radius-sm: 10px;                /* Small radius */
```

**Статус:** 🔴 Треба виконати

---

### 📍 ЕТАП 2: Оновлення компонентів (3-4 години)

#### 2.1. HeroSection.astro

**Файл:** `src/components/websummit/HeroSection.astro`

**Зміни в стилях:**
```css
.hero-title {
  font-size: var(--text-hero);              /* Використовує оновлений токен: 160px */
  font-weight: var(--font-black);           /* 900 - залишається */
  line-height: var(--leading-hero);         /* 0.78 - оновлено */
  letter-spacing: var(--tracking-hero);     /* -0.04em - оновлено */
  text-transform: uppercase;
}

@media (max-width: 768px) {
  .hero-title {
    font-size: var(--text-hero-mobile);     /* 48px на mobile */
  }
}
```

**Статус:** 🔴 Треба виконати

---

#### 2.2. AboutFoundation.astro

**Файл:** `src/components/websummit/AboutFoundation.astro`

**Зміни в стилях:**
```css
.about-section {
  background: var(--bg-blue);               /* Використовує оновлений токен: #5CADFF */
  padding: var(--section-padding-y) var(--section-padding-x);
  color: var(--text-white);
}

.section-title {
  font-size: var(--text-section-lg);        /* 80px - оновлено */
  font-weight: var(--font-black);           /* 900 */
  line-height: var(--leading-section-lg);   /* 0.825 - оновлено */
  letter-spacing: var(--tracking-section-lg); /* -0.04em - оновлено */
  text-transform: uppercase;
}
```

**Статус:** 🔴 Треба виконати

---

#### 2.3. AboutPrytulaFoundation.astro

**Файл:** `src/components/websummit/AboutPrytulaFoundation.astro`

**Зміни в стилях:**
```css
.section-title {
  font-size: var(--text-section-xl);        /* 110px - оновлено */
  font-weight: var(--font-black);           /* 900 */
  line-height: var(--leading-section-xl);   /* 0.818 - оновлено */
  letter-spacing: var(--tracking-section-xl); /* -0.04em - оновлено */
  text-transform: uppercase;
}

.subsection-title {
  font-size: var(--text-section-md);        /* 46px - додано */
  font-weight: var(--font-black);
  line-height: var(--leading-section-md);   /* 1.0 */
  letter-spacing: var(--tracking-section-md); /* -0.04em */
  text-transform: uppercase;
}
```

**Статус:** 🔴 Треба виконати

---

#### 2.4. WhyPrytula.astro

**Файл:** `src/components/websummit/WhyPrytula.astro`

**Зміни в стилях:**
```css
.section-title {
  font-size: var(--text-section-xl);        /* 110px */
  line-height: var(--leading-section-xl);   /* 0.818 */
  letter-spacing: var(--tracking-section-xl); /* -0.04em */
}

.reason-title {
  font-size: var(--text-heading-sm);        /* 32px */
  line-height: var(--leading-heading-sm);   /* 0.656 */
  letter-spacing: var(--tracking-heading-sm); /* -0.04em */
}

.reason-text {
  font-size: var(--text-body-lg);           /* 20px */
  line-height: var(--leading-body);         /* 1.3 */
  letter-spacing: var(--tracking-body);     /* -0.04em */
}
```

**Статус:** 🟠 Треба виконати

---

#### 2.5. HumanAchievements.astro

**Файл:** `src/components/websummit/HumanAchievements.astro`

**Зміни в стилях:**
```css
.achievements-section {
  background: var(--bg-gray-light);         /* #F8F8F8 - оновлено */
}

.section-title {
  font-size: var(--text-section-lg);        /* 80px */
  line-height: var(--leading-section-lg);   /* 0.825 */
  letter-spacing: var(--tracking-section-lg); /* -0.04em */
}
```

**Статус:** 🟠 Треба виконати

---

#### 2.6. PrytulaUSA.astro

**Файл:** `src/components/websummit/PrytulaUSA.astro`

**Зміни в стилях:**
```css
.section-title {
  font-size: var(--text-section-lg);        /* 80px */
  line-height: var(--leading-section-lg);   /* 0.825 */
  letter-spacing: var(--tracking-section-lg); /* -0.04em */
}

.badge,
.info-card {
  border-radius: var(--radius-lg);          /* 33px - додано */
}

.text-content {
  font-size: var(--text-heading-md);        /* 40px */
  line-height: var(--leading-heading-md);   /* 1.2 */
  letter-spacing: var(--tracking-heading-md); /* -0.04em */
}
```

**Статус:** 🟠 Треба виконати

---

#### 2.7. CoolStories.astro

**Файл:** `src/components/websummit/CoolStories.astro`

**Зміни в стилях:**
```css
.section-title {
  font-size: var(--text-section-lg);        /* 80px */
  line-height: var(--leading-section-lg);   /* 0.825 */
  letter-spacing: var(--tracking-section-lg); /* -0.04em */
}

.story-title {
  font-size: var(--text-heading-sm);        /* 32px */
  line-height: var(--leading-heading-sm);   /* 0.656 */
  letter-spacing: var(--tracking-heading-sm); /* -0.04em */
}

.story-image {
  border-radius: var(--radius-lg);          /* 33px - додано */
}
```

**Статус:** 🟢 Треба виконати

---

#### 2.8. VideosContacts.astro

**Файл:** `src/components/websummit/VideosContacts.astro`

**Зміни в стилях:**
```css
.section-title {
  font-size: var(--text-section-lg);        /* 80px */
  line-height: var(--leading-section-lg);   /* 0.825 */
  letter-spacing: var(--tracking-section-lg); /* -0.04em */
}

.video-card {
  border-radius: var(--radius-lg);          /* 33px - додано */
  border: 1px solid var(--color-black);     /* З Figma */
}
```

**Статус:** 🟢 Треба виконати

---

### 📍 ЕТАП 3: Mobile оптимізація (1-2 години)

#### 3.1. Адаптація розмірів шрифтів для mobile

**В `src/styles/global.css` додати media queries:**

```css
/* Mobile Typography Adjustments */
@media (max-width: 768px) {
  :root {
    --text-hero: 3.75rem;           /* 60px замість 160px */
    --text-section-xl: 3.4375rem;   /* 55px замість 110px */
    --text-section-lg: 2.5rem;      /* 40px замість 80px */
    --text-section-md: 2rem;        /* 32px замість 46px */
    --text-heading-lg: 1.75rem;     /* 28px замість 44px */
    --text-heading-md: 1.5rem;      /* 24px замість 40px */
    --text-heading-sm: 1.375rem;    /* 22px замість 32px */
    --text-body-lg: 1.125rem;       /* 18px замість 20px */
    --text-body: 1rem;              /* 16px замість 19px */
  }
}
```

**Статус:** 🟢 Треба виконати

---

#### 3.2. Перевірка responsive breakpoints

**Тестувати на:**
- 📱 Mobile: 375px, 414px
- 📱 Tablet: 768px, 1024px
- 💻 Desktop: 1280px, 1440px, 1920px

**Перевірити:**
- [ ] Всі заголовки читабельні
- [ ] Текст не обрізається
- [ ] Зображення масштабуються правильно
- [ ] Відступи пропорційні
- [ ] Grid layouts адаптуються

**Статус:** 🟢 Треба виконати після Етапів 1-2

---

#### 3.3. Оптимізація spacing для mobile

```css
@media (max-width: 768px) {
  :root {
    --section-padding-y: 3rem;      /* 48px замість 100px */
    --section-padding-x: 1.5rem;    /* 24px замість 32px */
    --content-gap: 1.5rem;          /* 24px замість 32px */
    --content-gap-large: 2.5rem;    /* 40px замість 64px */
  }
}
```

**Статус:** 🟢 Треба виконати

---

## ✅ Чеклісти виконання

### 📋 Чеклист Етапу 1: Дизайн-токени

**Файл:** `src/styles/global.css`

- [ ] Оновити всі кольори (синій, сірі відтінки)
- [ ] Додати font-size змінні (hero, sections, headings, body)
- [ ] Додати line-height змінні (0.78-1.3)
- [ ] Додати letter-spacing змінні (-0.04em)
- [ ] Додати border-radius змінні (33px, 20px, 10px)
- [ ] Оновити container max-width (1920px)
- [ ] Додати content max-width (1280px)
- [ ] Оновити spacing змінні
- [ ] Перевірити що всі старі змінні замінені
- [ ] Зберегти файл і перевірити що сайт не зламаний

---

### 📋 Чеклист Етапу 2: Компоненти

**HeroSection.astro:**
- [ ] Оновити font-size до var(--text-hero)
- [ ] Оновити line-height до var(--leading-hero)
- [ ] Оновити letter-spacing до var(--tracking-hero)
- [ ] Додати mobile версію font-size
- [ ] Перевірити візуально

**AboutFoundation.astro:**
- [ ] Оновити background color (var(--bg-blue))
- [ ] Оновити section-title font-size (var(--text-section-lg))
- [ ] Оновити line-height та letter-spacing
- [ ] Перевірити контраст тексту на новому фоні
- [ ] Перевірити візуально

**AboutPrytulaFoundation.astro:**
- [ ] Оновити section-title font-size (var(--text-section-xl))
- [ ] Оновити subsection-title (var(--text-section-md))
- [ ] Оновити line-height та letter-spacing
- [ ] Перевірити візуально

**WhyPrytula.astro:**
- [ ] Оновити section-title font-size
- [ ] Оновити reason-title font-size
- [ ] Оновити body text font-size
- [ ] Оновити всі line-heights та letter-spacing
- [ ] Перевірити візуально

**HumanAchievements.astro:**
- [ ] Оновити background color (var(--bg-gray-light))
- [ ] Оновити section-title font-size
- [ ] Оновити line-height та letter-spacing
- [ ] Перевірити візуально

**PrytulaUSA.astro:**
- [ ] Оновити section-title font-size
- [ ] Додати border-radius до badge/cards (var(--radius-lg))
- [ ] Оновити text-content font-size
- [ ] Оновити line-height та letter-spacing
- [ ] Перевірити візуально

**CoolStories.astro:**
- [ ] Оновити section-title font-size
- [ ] Оновити story-title font-size
- [ ] Додати border-radius до зображень
- [ ] Оновити line-height та letter-spacing
- [ ] Перевірити візуально

**VideosContacts.astro:**
- [ ] Оновити section-title font-size
- [ ] Додати border-radius до video cards
- [ ] Додати border до video cards
- [ ] Оновити line-height та letter-spacing
- [ ] Перевірити візуально

---

### 📋 Чеклист Етапу 3: Mobile оптимізація

**Responsive Typography:**
- [ ] Додати media query для mobile font-sizes
- [ ] Перевірити hero text на 375px
- [ ] Перевірити section titles на 768px
- [ ] Перевірити body text читабельність
- [ ] Переконатися що текст не обрізається

**Responsive Spacing:**
- [ ] Додати mobile spacing змінні
- [ ] Перевірити padding секцій на mobile
- [ ] Перевірити gaps між елементами
- [ ] Переконатися що контент не притискається до країв

**Breakpoint Testing:**
- [ ] Тест на 375px (iPhone SE)
- [ ] Тест на 414px (iPhone Pro Max)
- [ ] Тест на 768px (iPad Portrait)
- [ ] Тест на 1024px (iPad Landscape)
- [ ] Тест на 1280px (Laptop)
- [ ] Тест на 1440px (Desktop)
- [ ] Тест на 1920px (Large Desktop)

**Final Checks:**
- [ ] Всі зображення масштабуються
- [ ] Grid layouts адаптуються
- [ ] Кнопки та інтерактивні елементи доступні
- [ ] Немає горизонтального скролу
- [ ] Читабельність на всіх екранах

---

## 🎯 Очікувані результати

### До впровадження:
- ❌ Синій колір `#0047FF` (темний)
- ❌ Hero текст 80px (маленький)
- ❌ Заголовки секцій 40px (маленькі)
- ❌ Line-height 1.5 (розріджений)
- ❌ Max-width 1200px (стиснуто на великих екранах)
- ❌ Немає rounded corners
- ❌ Загальний вигляд менш імпактний

### Після впровадження:
- ✅ Синій колір `#5CADFF` (світлий, відповідає бренду)
- ✅ Hero текст 160px (великий, виразний)
- ✅ Заголовки секцій 110px/80px/46px (правильна hierarchy)
- ✅ Line-height 0.78-1.3 (щільний, сучасний)
- ✅ Max-width 1920px (використовує повну ширину)
- ✅ Border-radius 33px (rounded corners де потрібно)
- ✅ Загальний вигляд повністю відповідає Figma

---

## 📐 Технічні специфікації з Figma

### Кольори (HEX коди):

```css
/* Основні кольори */
--color-blue: #5CADFF;           /* RGB(92, 173, 255) */
--color-gray: #D9D9D9;           /* RGB(217, 217, 217) */
--bg-gray-light: #F8F8F8;        /* RGB(248, 248, 248) */
--bg-neutral: #E5E5E5;           /* RGB(229, 229, 229) */
```

### Шрифти:

**Сімейство:** Inter (вже використовується ✅)

**Вага:**
- Regular: 400
- Bold: 700
- Black: 900

### Розміри з Figma (Desktop):

| Елемент в Figma | Розмір | CSS Variable |
|------------------|--------|--------------|
| "SAFETY FOR UKRAINIANS" | 160px | --text-hero |
| "ABOUT THE ONE BILLION FUNDRAISER" | 110px | --text-section-xl |
| "HUMANITARIAN ACHIEVEMENTS" | 80px | --text-section-lg |
| "ABOUT THE FOUNDATION" | 46px | --text-section-md |
| "Together, we can prevent..." | 44px | --text-heading-lg |
| Section descriptions | 40px | --text-heading-md |
| Subsection titles | 32px | --text-heading-sm |
| Area titles | 30px | --text-heading-xs |
| Body text (large) | 20px | --text-body-lg |
| Navigation/links | 19px | --text-body |

---

## 📊 Прогрес виконання

| Етап | Статус | Прогрес | Дата початку | Дата завершення |
|------|--------|---------|--------------|-----------------|
| **Етап 1:** Дизайн-токени | 🔴 Не почато | 0% | - | - |
| **Етап 2:** Компоненти | 🔴 Не почато | 0% | - | - |
| **Етап 3:** Mobile | 🔴 Не почато | 0% | - | - |
| **Загальний прогрес** | 🔴 Не почато | **0%** | - | - |

---

## 🐛 Потенційні проблеми та рішення

### Проблема 1: Занадто великий текст на mobile
**Симптом:** Hero текст 160px не вміщується на екрані 375px

**Рішення:**
- Використати значно менші розміри для mobile (60px замість 160px)
- Додати media query з proportional scaling

---

### Проблема 2: Дуже щільний line-height може погіршити читабельність
**Симптом:** Line-height 0.78 може здаватися занадто щільним для body text

**Рішення:**
- Застосувати 0.78 тільки для великих заголовків (hero, sections)
- Для body text використати 1.3 (як в Figma)
- Тестувати на реальному контенті

---

### Проблема 3: Колір #5CADFF може мати поганий контраст з білим текстом
**Симптом:** Білий текст на світло-синьому фоні може бути нечитабельним

**Рішення:**
- Перевірити контраст за WCAG стандартами
- Якщо контраст недостатній, використати темніший відтінок тексту або підсилити синій

---

### Проблема 4: Border-radius 33px занадто великий для малих елементів
**Симптом:** Кнопки або маленькі картки виглядають дивно з радіусом 33px

**Рішення:**
- Використати 33px тільки для великих блоків (як в Figma)
- Створити додаткові токени (--radius-md: 20px, --radius-sm: 10px)
- Застосувати пропорційно до розміру елемента

---

### Проблема 5: Контент може не поміститися в 1920px на дуже великих екранах
**Симптом:** На екранах 2560px+ контент розтягнутий і занадто широкий

**Рішення:**
- 1920px - це максимум як в Figma, це нормально
- Центрувати контент на ще більших екранах
- Розглянути можливість обмеження окремих блоків до 1280px всередині

---

## 🔗 Корисні посилання

- [Figma файл websammit](https://www.figma.com/design/rEE8igxX5JzipvzRnxX2ay/websammit)
- [Development Plan](./DEVELOPMENT_PLAN.md)
- [CSS Custom Properties (MDN)](https://developer.mozilla.org/en-US/docs/Web/CSS/--*)
- [Inter Font на Google Fonts](https://fonts.google.com/specimen/Inter)
- [WCAG Contrast Checker](https://webaim.org/resources/contrastchecker/)

---

## 📝 Нотатки

### 2025-11-10: Створення плану
- Проаналізовано Figma дизайн через MCP
- Виявлено критичні відмінності в кольорах та типографіці
- Створено детальний план з 3 етапів
- Підготовлено чеклісти для кожного етапу

---

**Документ створено:** 2025-11-10
**Останнє оновлення:** 2025-11-10
**Автор:** Claude AI + nekits
**Статус:** ✅ План готовий до виконання
