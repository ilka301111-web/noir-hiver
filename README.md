<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
  <meta name="theme-color" content="#08080d">
  <!-- Политика безопасности: разрешаем только свои скрипты и стили, шрифты Google и картинки Unsplash -->
  <meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self' 'sha256-/c5ZDbBuPDXPQ1fN3b0wDSfA4B1oB25DmfcnD4cIEwE=' 'sha256-TNmUqYDgCZm0/Q0ry8DmcoDvCQ6gGDNtBuOwXBv3J3w='; style-src 'self' 'sha256-7Pi6WjMvrgBUMuXPdQ0UppTh04ChbylReXtWKB52LDw=' https://fonts.googleapis.com; font-src https://fonts.gstatic.com; img-src 'self' data: https://images.unsplash.com; connect-src 'none'; object-src 'none'; base-uri 'self'; form-action 'none'">
  <meta name="referrer" content="strict-origin-when-cross-origin">
  <title>NOIR HIVER — Зимняя коллекция 2026</title>
  <meta name="description" content="NOIR HIVER — премиальная зимняя одежда: пуховики, пальто, кашемировые свитеры и аксессуары. Бесплатная доставка от 15 000 ₽, возврат 30 дней.">
  <meta property="og:title" content="NOIR HIVER — Зимняя коллекция 2026">
  <meta property="og:description" content="Премиальная зимняя одежда из натуральных материалов.">
  <meta property="og:type" content="website">
  <link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 32 32'%3E%3Crect width='32' height='32' fill='%2308080d'/%3E%3Cpolygon points='16,4 19.5,12.5 28,12.5 21,18 23.5,27 16,22 8.5,27 11,18 4,12.5 12.5,12.5' fill='none' stroke='%23c8a87c' stroke-width='1.6'/%3E%3C/svg%3E">

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Noto+Serif:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&display=swap" rel="stylesheet">
  <style>/* ==========================================================================
   NOIR HIVER — стили
   Структура: переменные → база → шапка → главная → каталог → слои → адаптив
   ========================================================================== */

:root {
  --bg: #08080d;
  --bg-2: #0f0f16;
  --bg-3: #181822;
  --text: #f0ede8;
  --text-2: #a39e98;
  --text-3: #7d7771;
  --accent: #c8a87c;
  --accent-light: #d4b88e;
  --accent-dark: #a08860;
  --line: rgba(255, 255, 255, 0.07);
  --line-accent: rgba(200, 168, 124, 0.18);
  --danger: #e85d5d;

  --font-serif: 'Noto Serif', Georgia, 'Times New Roman', serif;
  --font-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;

  --ease: cubic-bezier(0.4, 0, 0.2, 1);
  --ease-out: cubic-bezier(0.16, 1, 0.3, 1);
  --spring: cubic-bezier(0.34, 1.56, 0.64, 1);

  --header-height: 60px;
  --safe-bottom: env(safe-area-inset-bottom, 0px);
}

/* ---------- База ---------- */

*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
  scroll-padding-top: var(--header-height);
  -webkit-text-size-adjust: 100%;
  -webkit-tap-highlight-color: transparent;
}

body {
  font-family: var(--font-sans);
  background: var(--bg);
  color: var(--text);
  line-height: 1.6;
  overflow-x: hidden;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* Пока идёт прелоадер или открыто окно, страницу не прокручиваем */
body.is-loading {
  overflow: hidden;
}
body.is-locked {
  position: fixed;
  left: 0;
  right: 0;
  overflow: hidden;
}

img {
  display: block;
  max-width: 100%;
}

a {
  color: inherit;
  text-decoration: none;
}

button,
input,
select,
textarea {
  font: inherit;
  color: inherit;
}

button {
  background: none;
  border: none;
  cursor: pointer;
  touch-action: manipulation;
}

[hidden] {
  display: none !important;
}

:focus-visible {
  outline: 1px solid var(--accent);
  outline-offset: 2px;
}

::selection {
  background: var(--accent);
  color: var(--bg);
}

::-webkit-scrollbar {
  width: 4px;
}
::-webkit-scrollbar-track {
  background: var(--bg);
}
::-webkit-scrollbar-thumb {
  background: var(--accent-dark);
  border-radius: 2px;
}

/* Спрайт с иконками не должен занимать место на странице */
.sprite {
  position: absolute;
}

/* Поле-ловушка для ботов: людям не видно, роботы его заполняют */
.hp {
  position: absolute;
  left: -9999px;
  width: 1px;
  height: 1px;
  opacity: 0;
}

.noscript {
  padding: 1rem;
  text-align: center;
  background: var(--bg-3);
  color: var(--text-2);
}

/* Иконки из SVG-спрайта */
.icon {
  width: 20px;
  height: 20px;
  flex-shrink: 0;
  fill: none;
  stroke: currentColor;
  stroke-width: 1.5;
  stroke-linecap: round;
  stroke-linejoin: round;
}
.icon--sm {
  width: 14px;
  height: 14px;
}

/* Картинки плавно появляются, когда загрузились (класс вешает app.js) */
.fade-img {
  opacity: 0;
  transition: opacity 0.6s var(--ease), transform 0.8s var(--ease-out);
}
.fade-img.is-loaded {
  opacity: 1;
}
.fade-img.is-broken {
  visibility: hidden;
}

/* Появление блоков при прокрутке */
.reveal {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.7s var(--ease-out), transform 0.7s var(--ease-out);
}
.reveal.is-visible {
  opacity: 1;
  transform: translateY(0);
}


/* ---------- Прелоадер ---------- */

.preloader {
  position: fixed;
  inset: 0;
  z-index: 10000;
  background: var(--bg);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  transition: opacity 0.8s ease, visibility 0.8s;
}
.preloader.is-done {
  opacity: 0;
  visibility: hidden;
  pointer-events: none;
}
.preloader__logo {
  font-family: var(--font-serif);
  font-size: clamp(1.6rem, 5vw, 2.8rem);
  font-weight: 300;
  letter-spacing: 0.8em;
  margin-right: -0.8em;
  color: var(--accent);
  overflow: hidden;
  white-space: pre;
}
.preloader__logo span {
  display: inline-block;
  transform: translateY(120%);
  animation: letter-up 0.5s var(--ease-out) forwards;
}
.preloader__line {
  width: 0;
  height: 1px;
  margin-top: 1.25rem;
  background: var(--accent);
  animation: line-grow 1.8s var(--ease-out) 0.3s forwards;
}

@keyframes letter-up {
  to { transform: translateY(0); }
}
@keyframes line-grow {
  to { width: min(160px, 35vw); }
}


/* ---------- Шапка ---------- */

.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  height: var(--header-height);
  padding: 0 clamp(1rem, 4vw, 3rem);
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: transparent;
  transition: background 0.5s, box-shadow 0.5s;
}
.header.is-scrolled {
  background: rgba(8, 8, 13, 0.92);
  backdrop-filter: saturate(180%) blur(20px);
  -webkit-backdrop-filter: saturate(180%) blur(20px);
  box-shadow: 0 1px 0 var(--line);
}

.logo {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  flex-shrink: 0;
  margin-right: -0.35em;
  font-family: var(--font-serif);
  font-size: 1.15rem;
  font-weight: 600;
  letter-spacing: 0.35em;
  color: var(--accent);
}
.logo__icon {
  width: 24px;
  height: 24px;
}

.nav {
  display: flex;
  align-items: center;
  gap: 1.75rem;
}
.nav__link {
  position: relative;
  padding: 0.2rem 0;
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  white-space: nowrap;
  color: var(--text-2);
  transition: color 0.3s;
}
.nav__link::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -2px;
  width: 0;
  height: 1px;
  background: var(--accent);
  transition: width 0.3s var(--ease-out);
}
.nav__link:hover,
.nav__link.is-active {
  color: var(--text);
}
.nav__link:hover::after,
.nav__link.is-active::after {
  width: 100%;
}

.header__actions {
  display: flex;
  align-items: center;
}
.header__burger {
  display: none;
}

.icon-btn {
  position: relative;
  width: 38px;
  height: 38px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  color: var(--text-2);
  transition: color 0.3s, background 0.3s;
}
.icon-btn:hover {
  color: var(--text);
  background: rgba(255, 255, 255, 0.05);
}

/* Счётчик на иконках корзины и избранного */
.badge {
  position: absolute;
  top: 3px;
  right: 3px;
  min-width: 16px;
  height: 16px;
  padding: 0 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
  background: var(--accent);
  color: var(--bg);
  font-size: 0.55rem;
  font-weight: 700;
  line-height: 1;
  transform: scale(0);
  transition: transform 0.3s var(--spring);
}
.badge.is-visible {
  transform: scale(1);
}


/* ---------- Кнопки ---------- */

.btn {
  position: relative;
  overflow: hidden;
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  padding: 0.85rem 1.8rem;
  font-size: 0.72rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  transition: all 0.35s var(--ease);
}
.btn--primary {
  background: var(--accent);
  color: var(--bg);
  font-weight: 600;
}
.btn--primary::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.25), transparent);
  transform: translateX(-100%);
  transition: transform 0.6s;
}
.btn--primary:hover::before {
  transform: translateX(100%);
}
.btn--primary:hover {
  background: var(--accent-light);
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(200, 168, 124, 0.25);
}
.btn--ghost {
  border: 1px solid var(--line-accent);
  font-weight: 500;
}
.btn--ghost:hover {
  border-color: var(--accent);
  color: var(--accent);
  transform: translateY(-2px);
}


/* ---------- Главный экран ---------- */

.hero {
  position: relative;
  min-height: 580px;
  height: 100vh;
  height: 100dvh;
  display: flex;
  align-items: center;
  overflow: hidden;
}

.hero__bg {
  position: absolute;
  inset: 0;
  overflow: hidden;
  background: linear-gradient(160deg, #1a1a2e, #16213e, #0f3460);
}
.hero__bg::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg,
    rgba(8, 8, 13, 0.5) 0%,
    rgba(8, 8, 13, 0.15) 30%,
    rgba(8, 8, 13, 0.4) 70%,
    var(--bg) 100%);
}
.hero__img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: brightness(0.28) saturate(0.6);
  transform: scale(1.1);
  animation: hero-drift 25s ease-in-out infinite alternate;
}
@keyframes hero-drift {
  from { transform: scale(1.1) translateY(0); }
  to   { transform: scale(1.14) translateY(-1%); }
}

.hero__content {
  position: relative;
  z-index: 2;
  max-width: 680px;
  padding: var(--header-height) clamp(1.25rem, 6vw, 8rem) 0;
}

.hero__tag {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
  padding: 0.4rem 1rem;
  border: 1px solid var(--line-accent);
  border-radius: 100px;
  background: rgba(200, 168, 124, 0.04);
  backdrop-filter: blur(12px);
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--accent);
}
.hero__dot {
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: var(--accent);
  animation: blink 2s infinite;
}
@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.2; }
}

.hero__title {
  margin-bottom: 1.1rem;
  font-family: var(--font-serif);
  font-size: clamp(2.4rem, 7vw, 6rem);
  font-weight: 300;
  line-height: 1.05;
}
.hero__title em {
  font-style: italic;
  font-weight: 400;
  color: var(--accent);
}
.hero__text {
  max-width: 420px;
  margin-bottom: 2rem;
  font-size: clamp(0.85rem, 1.3vw, 1rem);
  font-weight: 300;
  line-height: 1.8;
  color: var(--text-2);
}
.hero__buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 0.7rem;
}

/* Элементы главного экрана появляются по очереди после прелоадера */
.hero__tag,
.hero__title,
.hero__text,
.hero__buttons,
.hero__showcase,
.hero__scroll {
  opacity: 0;
  transform: translateY(24px);
}
body.is-ready .hero__tag,
body.is-ready .hero__title,
body.is-ready .hero__text,
body.is-ready .hero__buttons,
body.is-ready .hero__showcase,
body.is-ready .hero__scroll {
  animation: rise 1s var(--ease-out) forwards;
}
body.is-ready .hero__tag      { animation-delay: 0s; }
body.is-ready .hero__title    { animation-delay: 0.2s; }
body.is-ready .hero__text     { animation-delay: 0.4s; }
body.is-ready .hero__buttons  { animation-delay: 0.6s; }
body.is-ready .hero__showcase { animation-delay: 0.5s; }
body.is-ready .hero__scroll   { animation-delay: 1s; }

@keyframes rise {
  to { opacity: 1; transform: translateY(0); }
}

/* Карточка справа */
.hero__showcase {
  position: absolute;
  top: 0;
  bottom: 0;
  right: clamp(2rem, 7vw, 9rem);
  z-index: 2;
  display: flex;
  align-items: center;
  padding-top: var(--header-height);
}
.showcase {
  position: relative;
  width: clamp(280px, 25vw, 400px);
}
.showcase__card {
  position: relative;
  aspect-ratio: 3 / 4;
  overflow: hidden;
  border: 1px solid var(--line-accent);
  background: var(--bg-3);
  box-shadow: 0 30px 80px rgba(0, 0, 0, 0.5);
  cursor: pointer;
  transition: transform 0.6s var(--ease-out), border-color 0.4s;
}
.showcase__card:hover {
  transform: translateY(-6px);
  border-color: var(--accent);
}
.showcase__card img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: brightness(0.85) saturate(0.85);
}
.showcase__card:hover img {
  transform: scale(1.05);
}
.showcase__card::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg, transparent 45%, rgba(8, 8, 13, 0.92));
  pointer-events: none;
}
.showcase__tag {
  position: absolute;
  top: 0.9rem;
  left: 0.9rem;
  z-index: 2;
  padding: 0.3rem 0.7rem;
  border: 1px solid var(--accent);
  background: var(--bg);
  font-size: 0.6rem;
  font-weight: 700;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--accent);
}
.showcase__caption {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 2;
  padding: 1.25rem;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 1rem;
}
.showcase__caption small {
  display: block;
  margin-bottom: 0.25rem;
  font-size: 0.6rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--accent);
}
.showcase__caption h3 {
  font-family: var(--font-serif);
  font-size: 1.15rem;
  font-weight: 400;
  line-height: 1.2;
}
.showcase__caption p {
  margin-top: 0.2rem;
  font-size: 0.85rem;
  color: var(--text-2);
}
.showcase__go {
  width: 40px;
  height: 40px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid var(--accent);
  border-radius: 50%;
  color: var(--accent);
  transition: all 0.3s;
}
.showcase__card:hover .showcase__go {
  background: var(--accent);
  color: var(--bg);
}
.showcase__stat {
  position: absolute;
  z-index: 3;
  padding: 0.8rem 1.1rem;
  border: 1px solid var(--line-accent);
  background: rgba(15, 15, 22, 0.82);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  animation: float 6s ease-in-out infinite;
}
.showcase__stat b {
  display: block;
  font-family: var(--font-serif);
  font-size: 1.5rem;
  font-weight: 400;
  line-height: 1.1;
  color: var(--accent);
}
.showcase__stat span {
  font-size: 0.62rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--text-2);
}
.showcase__stat--top    { left: -3.2rem; top: 18%; }
.showcase__stat--bottom { right: -2.2rem; bottom: 22%; animation-delay: -3s; }

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

.hero__scroll {
  position: absolute;
  bottom: max(2rem, calc(2rem + var(--safe-bottom)));
  left: 0;
  right: 0;
  z-index: 2;
  margin: 0 auto;
  width: max-content;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}
.hero__scroll span {
  font-size: 0.6rem;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: var(--text-3);
}
.hero__scroll i {
  position: relative;
  width: 1px;
  height: 32px;
  overflow: hidden;
  background: rgba(255, 255, 255, 0.08);
}
.hero__scroll i::after {
  content: '';
  position: absolute;
  top: -100%;
  left: 0;
  width: 100%;
  height: 100%;
  background: var(--accent);
  animation: scroll-line 2s infinite;
}
@keyframes scroll-line {
  0% { top: -100%; }
  100% { top: 100%; }
}


/* ---------- Бегущая строка ---------- */

.ticker {
  overflow: hidden;
  padding: 0.9rem 0;
  border-top: 1px solid var(--line);
  border-bottom: 1px solid var(--line);
  background: var(--bg-2);
  -webkit-mask: linear-gradient(90deg, transparent, #000 5%, #000 95%, transparent);
  mask: linear-gradient(90deg, transparent, #000 5%, #000 95%, transparent);
}
.ticker__track {
  display: flex;
  width: max-content;
  animation: ticker 40s linear infinite;
}
.ticker__track span {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  padding: 0 1.5rem;
  font-size: 0.75rem;
  white-space: nowrap;
  color: var(--text-3);
}
.ticker__track span::after {
  content: '◆';
  font-size: 0.35rem;
  color: var(--accent-dark);
}
@keyframes ticker {
  to { transform: translateX(-50%); }
}


/* ---------- Преимущества ---------- */

.features {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1px;
  background: var(--line);
}
.feature {
  padding: clamp(1.5rem, 3vw, 2.25rem);
  background: var(--bg);
  text-align: center;
  transition: background 0.5s, opacity 0.7s var(--ease-out), transform 0.7s var(--ease-out);
}
.feature:hover {
  background: var(--bg-2);
}
.feature__icon {
  width: 32px;
  height: 32px;
  margin: 0 auto 0.85rem;
  color: var(--accent);
  transition: transform 0.4s var(--spring);
}
.feature:hover .feature__icon {
  transform: scale(1.15) rotate(-5deg);
}
.feature__title {
  margin-bottom: 0.35rem;
  font-family: var(--font-serif);
  font-size: 1.05rem;
  font-weight: 500;
}
.feature__text {
  font-size: 0.78rem;
  font-weight: 300;
  line-height: 1.7;
  color: var(--text-3);
}


/* ---------- Заголовки секций ---------- */

.section {
  padding: clamp(3rem, 8vw, 6rem) clamp(1rem, 3vw, 3rem);
}
.section__head {
  margin-bottom: clamp(2rem, 5vw, 3.5rem);
  text-align: center;
}
.section__label {
  display: block;
  margin-bottom: 0.65rem;
  font-size: 0.65rem;
  font-weight: 600;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: var(--accent);
}
.section__title {
  margin-bottom: 0.65rem;
  font-family: var(--font-serif);
  font-size: clamp(1.7rem, 3.5vw, 2.8rem);
  font-weight: 300;
  line-height: 1.2;
}
.section__text {
  max-width: 440px;
  margin: 0 auto;
  font-size: 0.92rem;
  font-weight: 300;
  color: var(--text-2);
}


/* ---------- Каталог ---------- */

.toolbar {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  margin-bottom: 1.25rem;
}

.filters {
  display: flex;
  flex-wrap: wrap;
  gap: 0.35rem;
  scrollbar-width: none;
}
.filters::-webkit-scrollbar {
  display: none;
}
.filter {
  padding: 0.5rem 1.1rem;
  border: 1px solid var(--line);
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.04em;
  white-space: nowrap;
  color: var(--text-2);
  transition: all 0.3s var(--ease);
}
.filter:hover {
  border-color: var(--accent);
  color: var(--text);
}
.filter.is-active {
  background: var(--accent);
  border-color: var(--accent);
  color: var(--bg);
  font-weight: 600;
}

.sort {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.sort label {
  font-size: 0.7rem;
  color: var(--text-3);
}
.sort select {
  padding: 0.45rem 1.8rem 0.45rem 0.8rem;
  border: 1px solid var(--line);
  border-radius: 2px;
  background: var(--bg-2) url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='10' viewBox='0 0 24 24' fill='none' stroke='%239a9590' stroke-width='2'%3E%3Cpath d='M6 9l6 6 6-6'/%3E%3C/svg%3E") no-repeat right 0.5rem center;
  font-size: 0.75rem;
  cursor: pointer;
  appearance: none;
  -webkit-appearance: none;
}
.sort option {
  background: var(--bg-2);
}

/* Строка «найдено N товаров» и плашка активного поиска */
.catalog-info {
  min-height: 1.6rem;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.75rem;
  font-size: 0.75rem;
  color: var(--text-3);
}
.chip {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  padding: 0.25rem 0.5rem 0.25rem 0.8rem;
  border: 1px solid var(--accent-dark);
  border-radius: 100px;
  font-size: 0.72rem;
  color: var(--accent);
}
.chip button {
  width: 18px;
  height: 18px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  color: inherit;
}
.chip button:hover {
  background: rgba(200, 168, 124, 0.15);
}

.products {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 1.25rem;
}
.products__empty {
  grid-column: 1 / -1;
  padding: 4rem 1rem;
  text-align: center;
  color: var(--text-3);
}
.products__empty button {
  margin-top: 1rem;
  padding: 0.6rem 1.3rem;
  border: 1px solid var(--line-accent);
  font-size: 0.7rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--accent);
  transition: all 0.3s;
}
.products__empty button:hover {
  background: var(--accent);
  color: var(--bg);
}

/* Карточка товара */
.card {
  position: relative;
  overflow: hidden;
  border: 1px solid transparent;
  background: var(--bg-2);
  cursor: pointer;
  transition: opacity 0.7s var(--ease-out), transform 0.5s var(--ease-out),
              box-shadow 0.5s var(--ease-out), border-color 0.5s;
}
.card.is-visible:hover {
  transform: translateY(-6px);
  border-color: var(--line-accent);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
}

.card__image {
  position: relative;
  aspect-ratio: 3 / 4;
  overflow: hidden;
  background: linear-gradient(135deg, #1a1a24, #2d2d3a);
}
.card__image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.card:hover .card__image img {
  transform: scale(1.06);
}

.card__badge {
  position: absolute;
  top: 0.75rem;
  left: 0.75rem;
  z-index: 2;
  padding: 0.28rem 0.7rem;
  font-size: 0.6rem;
  font-weight: 700;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}
.card__badge--new       { background: var(--accent); color: var(--bg); }
.card__badge--sale      { background: var(--danger); color: #fff; }
.card__badge--exclusive { background: var(--bg); color: var(--accent); border: 1px solid var(--accent); }

.card__actions {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 3;
  display: flex;
  gap: 0.35rem;
  padding: 1rem;
  opacity: 0;
  transform: translateY(16px);
  transition: all 0.4s var(--ease-out);
}
.card:hover .card__actions,
.card:focus-within .card__actions {
  opacity: 1;
  transform: translateY(0);
}
.card__add,
.card__wish {
  border: 1px solid var(--line-accent);
  background: rgba(8, 8, 13, 0.92);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  transition: all 0.3s;
}
.card__add {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.4rem;
  padding: 0.7rem;
  font-size: 0.65rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}
.card__add:hover {
  background: var(--accent);
  border-color: var(--accent);
  color: var(--bg);
}
.card__wish {
  width: 38px;
  height: 38px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--text-2);
}
.card__wish .icon,
.wish-btn .icon {
  width: 15px;
  height: 15px;
}
.card__wish:hover,
.card__wish.is-liked {
  border-color: var(--danger);
  color: var(--danger);
}
.is-liked .icon {
  fill: currentColor;
}

.card__info {
  padding: 1rem 1.1rem 1.15rem;
}
.card__brand {
  margin-bottom: 0.3rem;
  font-size: 0.6rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--accent);
}
.card__name {
  margin-bottom: 0.3rem;
  font-family: var(--font-serif);
  font-size: 1.1rem;
  font-weight: 500;
  line-height: 1.3;
  text-align: left;
  transition: color 0.3s;
}
.card:hover .card__name {
  color: var(--accent);
}
.card__category {
  margin-bottom: 0.55rem;
  font-size: 0.7rem;
  color: var(--text-3);
}
.card__price {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 0.5rem;
}
.card__price strong {
  font-size: 0.95rem;
  font-weight: 600;
}
.card__price s {
  font-size: 0.78rem;
  color: var(--text-3);
}
.card__price em {
  font-style: normal;
  font-size: 0.68rem;
  font-weight: 600;
  color: var(--danger);
}

.card__sizes {
  display: flex;
  flex-wrap: wrap;
  gap: 0.3rem;
  margin-top: 0.6rem;
}
.size-chip {
  min-width: 28px;
  height: 26px;
  padding: 0 0.35rem;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid var(--line);
  font-size: 0.62rem;
  font-weight: 500;
  color: var(--text-3);
  transition: all 0.2s;
}
.size-chip:hover,
.size-chip.is-selected {
  border-color: var(--accent);
  color: var(--accent);
}
.size-chip:disabled {
  opacity: 0.25;
  text-decoration: line-through;
  cursor: not-allowed;
}


/* ---------- Lookbook ---------- */

.lookbook {
  overflow: hidden;
  padding-top: clamp(3rem, 6vw, 5rem);
  padding-bottom: clamp(3rem, 6vw, 5rem);
  background: var(--bg-2);
}
.lookbook__grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 0.75rem;
  padding: 0 clamp(1rem, 3vw, 3rem);
}
.look {
  position: relative;
  display: block;
  overflow: hidden;
  background: linear-gradient(135deg, #2d3436, #4a5258);
}
.look:nth-child(1) { grid-column: 1 / 8;  aspect-ratio: 16 / 10; }
.look:nth-child(2) { grid-column: 8 / 13; aspect-ratio: 3 / 4; }
.look:nth-child(3) { grid-column: 1 / 5;  aspect-ratio: 3 / 4; }
.look:nth-child(4) { grid-column: 5 / 9;  aspect-ratio: 4 / 3; }
.look:nth-child(5) { grid-column: 9 / 13; aspect-ratio: 3 / 4; }

.look img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.look:hover img {
  transform: scale(1.05);
}
.look::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg, transparent 40%, rgba(8, 8, 13, 0.7));
  opacity: 0;
  transition: opacity 0.5s;
}
.look:hover::after {
  opacity: 1;
}
.look__caption {
  position: absolute;
  left: 1.1rem;
  bottom: 1.1rem;
  z-index: 2;
  opacity: 0;
  transform: translateY(8px);
  transition: all 0.5s var(--ease-out);
}
.look:hover .look__caption {
  opacity: 1;
  transform: translateY(0);
}
.look__caption span {
  font-size: 0.6rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--accent);
}
.look__caption h3 {
  margin-top: 0.15rem;
  font-family: var(--font-serif);
  font-size: 1.15rem;
  font-weight: 400;
}


/* ---------- Подписка ---------- */

.newsletter {
  position: relative;
  overflow: hidden;
  text-align: center;
}
.newsletter::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(200, 168, 124, 0.05) 0%, transparent 70%);
  transform: translate(-50%, -50%);
  pointer-events: none;
}
.newsletter > div {
  position: relative;
}
.newsletter__form {
  display: flex;
  max-width: 440px;
  margin: 1.75rem auto 0;
}
.newsletter__form input {
  flex: 1;
  min-width: 0;
  padding: 0.85rem 1.15rem;
  border: 1px solid var(--line);
  border-right: none;
  border-radius: 0;
  background: var(--bg-2);
  font-size: 0.85rem;
  outline: none;
  transition: border-color 0.3s;
}
.newsletter__form input:focus {
  border-color: var(--accent);
}
.newsletter__form input::placeholder {
  color: var(--text-3);
}
.newsletter__form button {
  padding: 0.85rem 1.4rem;
  border: 1px solid var(--accent);
  background: var(--accent);
  color: var(--bg);
  font-size: 0.68rem;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  white-space: nowrap;
  transition: background 0.3s;
}
.newsletter__form button:hover {
  background: var(--accent-light);
}
.newsletter__error {
  min-height: 1.2rem;
  margin-top: 0.6rem;
  font-size: 0.75rem;
  color: var(--danger);
}


/* ---------- Подвал ---------- */

.footer {
  padding: clamp(2.5rem, 5vw, 4rem) clamp(1rem, 3vw, 3rem) 2rem;
  border-top: 1px solid var(--line);
  background: var(--bg-2);
}
.footer__grid {
  display: grid;
  grid-template-columns: 1.5fr 1fr 1fr 1fr;
  gap: 2rem;
  margin-bottom: 2rem;
}
.footer__brand p {
  margin-top: 0.75rem;
  font-size: 0.82rem;
  font-weight: 300;
  line-height: 1.8;
  color: var(--text-3);
}
.footer__social {
  display: flex;
  gap: 0.5rem;
  margin-top: 1.1rem;
}
.footer__social a {
  width: 36px;
  height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid var(--line);
  border-radius: 50%;
  color: var(--text-3);
  transition: all 0.3s;
}
.footer__social a:hover {
  border-color: var(--accent);
  color: var(--accent);
  transform: translateY(-2px);
}
.footer__col h4 {
  margin-bottom: 1rem;
  font-family: var(--font-serif);
  font-size: 1rem;
  font-weight: 500;
}
.footer__col a,
.footer__col span {
  display: block;
  margin-bottom: 0.5rem;
  font-size: 0.8rem;
  font-weight: 300;
  color: var(--text-3);
  transition: color 0.3s;
}
.footer__col a:hover {
  color: var(--accent);
}
.footer__bottom {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  padding-top: 1.25rem;
  border-top: 1px solid var(--line);
}
.footer__bottom p {
  font-size: 0.72rem;
  font-weight: 300;
  color: var(--text-3);
}
.footer__pay {
  display: flex;
  gap: 0.35rem;
}
.footer__pay span {
  padding: 0.25rem 0.6rem;
  border: 1px solid var(--line);
  background: var(--bg);
  font-size: 0.6rem;
  letter-spacing: 0.04em;
  color: var(--text-3);
}


/* ==========================================================================
   Слои поверх страницы: подложка, корзина, поиск, модальные окна
   ========================================================================== */

.overlay {
  position: fixed;
  inset: 0;
  z-index: 9998;
  background: rgba(0, 0, 0, 0.65);
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.4s var(--ease), visibility 0.4s;
}
.overlay.is-open {
  opacity: 1;
  visibility: visible;
}

/* Боковые панели: корзина и избранное */
.drawer {
  position: fixed;
  top: 0;
  right: 0;
  z-index: 9999;
  width: 420px;
  max-width: 90vw;
  height: 100vh;
  height: 100dvh;
  display: flex;
  flex-direction: column;
  border-left: 1px solid var(--line);
  background: var(--bg-2);
  transform: translateX(100%);
  visibility: hidden;
  transition: transform 0.45s var(--ease-out), visibility 0.45s;
}
.drawer.is-open {
  transform: translateX(0);
  visibility: visible;
}
.drawer__head {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1.15rem 1.15rem 0.9rem;
  border-bottom: 1px solid var(--line);
}
.drawer__head h3 {
  font-family: var(--font-serif);
  font-size: 1.15rem;
  font-weight: 400;
}
.drawer__head h3 span {
  font-size: 0.82rem;
  color: var(--text-3);
}
.drawer__body {
  flex: 1;
  overflow-y: auto;
  padding: 0.85rem 1.15rem;
}
.drawer__foot {
  padding: 1.15rem;
  padding-bottom: calc(1.15rem + var(--safe-bottom));
  border-top: 1px solid var(--line);
}
.drawer__empty {
  height: 100%;
  min-height: 260px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  text-align: center;
  font-size: 0.88rem;
  font-weight: 300;
  color: var(--text-3);
}
.drawer__empty .icon {
  width: 42px;
  height: 42px;
  opacity: 0.25;
  stroke-width: 1;
}
.drawer__empty a,
.drawer__empty button {
  margin-top: 0.4rem;
  padding: 0.6rem 1.3rem;
  border: 1px solid var(--line-accent);
  font-size: 0.68rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--accent);
  transition: all 0.3s;
}
.drawer__empty a:hover,
.drawer__empty button:hover {
  background: var(--accent);
  color: var(--bg);
}

/* Строка товара в корзине / избранном */
.line-item {
  display: flex;
  gap: 0.75rem;
  padding: 0.75rem 0;
  border-bottom: 1px solid var(--line);
  animation: slide-in 0.35s var(--ease-out);
}
@keyframes slide-in {
  from { opacity: 0; transform: translateX(16px); }
  to   { opacity: 1; transform: translateX(0); }
}
.line-item__img {
  width: 66px;
  height: 84px;
  flex-shrink: 0;
  object-fit: cover;
  background: var(--bg-3);
  cursor: pointer;
}
.line-item__info {
  flex: 1;
  min-width: 0;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 0.4rem;
}
.line-item__name {
  font-family: var(--font-serif);
  font-size: 0.9rem;
  font-weight: 500;
  line-height: 1.3;
  text-align: left;
}
.line-item__meta {
  font-size: 0.7rem;
  color: var(--text-3);
}
.line-item__row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 0.5rem;
}
.line-item__price {
  font-size: 0.85rem;
  font-weight: 600;
  white-space: nowrap;
}
.line-item__links {
  display: flex;
  gap: 1rem;
}
.line-item__link {
  padding: 0.15rem 0;
  font-size: 0.68rem;
  color: var(--text-3);
  transition: color 0.3s;
}
.line-item__link:hover {
  color: var(--danger);
}
.line-item__link--accent {
  color: var(--accent);
}
.line-item__link--accent:hover {
  color: var(--accent-light);
}
.qty {
  display: flex;
  align-items: center;
  gap: 0.35rem;
}
.qty button {
  width: 28px;
  height: 28px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid var(--line);
  background: var(--bg);
  color: var(--text-2);
  transition: all 0.2s;
}
.qty button:hover {
  border-color: var(--accent);
  color: var(--accent);
}
.qty span {
  min-width: 20px;
  text-align: center;
  font-size: 0.8rem;
  font-weight: 500;
}

/* Прогресс до бесплатной доставки */
.ship-bar {
  margin-bottom: 0.9rem;
}
.ship-bar p {
  margin-bottom: 0.4rem;
  font-size: 0.72rem;
  color: var(--text-2);
}
.ship-bar b {
  font-weight: 600;
  color: var(--accent);
}
.ship-bar__track {
  height: 3px;
  overflow: hidden;
  background: var(--line);
}
.ship-bar__track i {
  display: block;
  width: 0;
  height: 100%;
  background: var(--accent);
  transition: width 0.5s var(--ease-out);
}

/* Промокод */
.promo {
  display: flex;
}
.promo input {
  flex: 1;
  min-width: 0;
  padding: 0.6rem 0.8rem;
  border: 1px solid var(--line);
  border-right: none;
  border-radius: 0;
  background: var(--bg);
  font-size: 0.78rem;
  text-transform: uppercase;
  outline: none;
  transition: border-color 0.3s;
}
.promo input:focus {
  border-color: var(--accent);
}
.promo input::placeholder {
  text-transform: none;
  color: var(--text-3);
}
.promo button {
  padding: 0 1rem;
  border: 1px solid var(--line-accent);
  font-size: 0.65rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--accent);
  transition: all 0.3s;
}
.promo button:hover {
  background: var(--accent);
  color: var(--bg);
}
.promo__hint {
  min-height: 1.1rem;
  margin: 0.4rem 0 0.6rem;
  font-size: 0.68rem;
  color: var(--text-3);
}
.promo__hint.is-ok { color: #5dc878; }
.promo__hint.is-error { color: var(--danger); }

/* Строки с суммами (корзина и оформление) */
.sum-row {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.4rem;
  font-size: 0.82rem;
  color: var(--text-2);
}
.sum-row--discount {
  color: #5dc878;
}
.sum-row--total {
  margin-top: 0.5rem;
  padding-top: 0.7rem;
  border-top: 1px solid var(--line);
  font-size: 1.05rem;
  font-weight: 600;
  color: var(--text);
}
.drawer__checkout {
  width: 100%;
  margin-top: 0.8rem;
  padding: 0.95rem;
  background: var(--accent);
  color: var(--bg);
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  transition: all 0.3s;
}
.drawer__checkout:hover {
  background: var(--accent-light);
}
.drawer__checkout:active {
  transform: scale(0.98);
}


/* ---------- Поиск ---------- */

.search {
  position: fixed;
  inset: 0;
  z-index: 10001;
  overflow-y: auto;
  padding: 11vh 1.5rem 3rem;
  background: rgba(8, 8, 13, 0.97);
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.35s var(--ease), visibility 0.35s;
}
.search.is-open {
  opacity: 1;
  visibility: visible;
}
.search__box {
  max-width: 640px;
  margin: 0 auto;
  transform: translateY(-12px);
  transition: transform 0.4s var(--ease-out);
}
.search.is-open .search__box {
  transform: translateY(0);
}
.search__form {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  border-bottom: 2px solid var(--line);
  transition: border-color 0.3s;
}
.search__form:focus-within {
  border-color: var(--accent);
}
.search__icon {
  color: var(--text-3);
}
.search__form input {
  flex: 1;
  min-width: 0;
  padding: 1rem 0;
  border: none;
  background: none;
  font-family: var(--font-serif);
  font-size: 1.6rem;
  outline: none;
  -webkit-appearance: none;
  appearance: none;
}
.search__form input::-webkit-search-cancel-button {
  display: none;
}
.search__form input::placeholder {
  font-size: 1.15rem;
  color: var(--text-3);
}

.search__hints {
  margin-top: 1.5rem;
}
.search__hints-title {
  margin-bottom: 0.65rem;
  font-size: 0.62rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--text-3);
}
.search__hints-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
}
.search__hints-list button {
  padding: 0.4rem 0.9rem;
  border: 1px solid var(--line);
  font-size: 0.75rem;
  color: var(--text-2);
  transition: all 0.3s;
}
.search__hints-list button:hover {
  border-color: var(--accent);
  color: var(--accent);
}

.search__results {
  margin-top: 1.25rem;
}
.search__count {
  margin-bottom: 0.5rem;
  font-size: 0.72rem;
  color: var(--text-3);
}
.search-item {
  width: 100%;
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 0.7rem;
  border-bottom: 1px solid var(--line);
  text-align: left;
  transition: background 0.25s;
}
.search-item:hover,
.search-item:focus-visible {
  background: rgba(255, 255, 255, 0.04);
}
.search-item img {
  width: 54px;
  height: 70px;
  flex-shrink: 0;
  object-fit: cover;
  background: var(--bg-3);
}
.search-item__text {
  flex: 1;
  min-width: 0;
}
.search-item__name,
.search-item__category {
  display: block;
}
.search-item__name {
  font-family: var(--font-serif);
  font-size: 1rem;
  line-height: 1.3;
}
.search-item__name mark {
  background: none;
  color: var(--accent);
}
.search-item__category {
  margin-top: 0.15rem;
  font-size: 0.7rem;
  color: var(--text-3);
}
.search-item__price {
  font-size: 0.9rem;
  font-weight: 600;
  white-space: nowrap;
}
.search__all {
  display: block;
  width: 100%;
  margin-top: 1.25rem;
  padding: 0.9rem;
  border: 1px solid var(--line-accent);
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--accent);
  transition: all 0.3s;
}
.search__all:hover {
  background: var(--accent);
  color: var(--bg);
}
.search__empty {
  padding: 2rem 0;
  text-align: center;
  color: var(--text-3);
}
.search__empty strong {
  display: block;
  margin-bottom: 0.4rem;
  font-family: var(--font-serif);
  font-size: 1.2rem;
  font-weight: 400;
  color: var(--text);
}


/* ---------- Модальные окна ---------- */

.modal {
  position: fixed;
  inset: 0;
  z-index: 10002;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.35s var(--ease), visibility 0.35s;
}
.modal.is-open {
  opacity: 1;
  visibility: visible;
}
.modal__backdrop {
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.85);
}
.modal__window {
  position: relative;
  width: 100%;
  max-height: 90vh;
  max-height: 90dvh;
  overflow-y: auto;
  border: 1px solid var(--line);
  background: var(--bg-2);
  transform: scale(0.95) translateY(10px);
  transition: transform 0.4s var(--spring);
}
.modal.is-open .modal__window {
  transform: scale(1) translateY(0);
}

/* Карточка товара в модальном окне */
.product-view {
  max-width: 960px;
  display: grid;
  grid-template-columns: 1fr 1fr;
}
.product-view__image {
  position: relative;
  min-height: 520px;
  overflow: hidden;
  background: linear-gradient(135deg, #1a1a24, #2d2d3a);
}
.product-view__image > img {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.product-view__close {
  position: absolute;
  top: 0.75rem;
  right: 0.75rem;
  z-index: 5;
  border: 1px solid var(--line-accent);
  background: rgba(8, 8, 13, 0.75);
  backdrop-filter: blur(10px);
  color: var(--text);
}
.product-view__close:hover {
  border-color: var(--accent);
  color: var(--accent);
}
.product-view__details {
  display: flex;
  flex-direction: column;
  padding: 1.75rem;
}
.product-view__brand {
  margin-bottom: 0.35rem;
  font-size: 0.62rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--accent);
}
.product-view__badge {
  align-self: flex-start;
  position: static;
  margin-bottom: 0.65rem;
}
.product-view__name {
  margin-bottom: 0.4rem;
  padding-right: 2.5rem;
  font-family: var(--font-serif);
  font-size: 1.7rem;
  font-weight: 400;
  line-height: 1.2;
}
.product-view__rating {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 0.65rem;
  font-size: 0.75rem;
  color: var(--text-3);
}
.product-view__rating span:first-child {
  letter-spacing: 0.06em;
  color: var(--accent);
}
.product-view__price {
  margin-bottom: 1rem;
  font-size: 1.3rem;
  font-weight: 600;
}
.product-view__price s {
  margin-left: 0.6rem;
  font-size: 0.9rem;
  font-weight: 400;
  color: var(--text-3);
}
.product-view__text {
  margin-bottom: 1.1rem;
  font-size: 0.85rem;
  font-weight: 300;
  line-height: 1.8;
  color: var(--text-2);
}
.product-view__label {
  margin-bottom: 0.55rem;
  font-size: 0.62rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--text-3);
}
.product-view__sizes {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
  margin-bottom: 0.4rem;
}
.product-view__sizes .size-chip {
  min-width: 44px;
  height: 42px;
  font-size: 0.78rem;
}
.product-view__hint {
  min-height: 1.1rem;
  margin-bottom: 0.7rem;
  font-size: 0.7rem;
  color: var(--danger);
}
.product-view__buttons {
  display: flex;
  gap: 0.5rem;
}
.product-view__add {
  flex: 1;
  padding: 0.95rem;
  background: var(--accent);
  color: var(--bg);
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  transition: all 0.3s;
}
.product-view__add:hover {
  background: var(--accent-light);
}
.product-view__add:active {
  transform: scale(0.98);
}
.wish-btn {
  width: 48px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid var(--line-accent);
  color: var(--text-2);
  transition: all 0.3s;
}
.wish-btn:hover,
.wish-btn.is-liked {
  border-color: var(--danger);
  color: var(--danger);
}

.product-view__more {
  margin-top: 1.25rem;
  border-top: 1px solid var(--line);
}
.product-view__more details {
  border-bottom: 1px solid var(--line);
}
.product-view__more summary {
  padding: 0.8rem 0;
  font-size: 0.75rem;
  letter-spacing: 0.06em;
  list-style: none;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
}
.product-view__more summary::-webkit-details-marker {
  display: none;
}
.product-view__more summary::after {
  content: '+';
  color: var(--accent);
}
.product-view__more details[open] summary::after {
  content: '−';
}
.product-view__more p {
  padding-bottom: 0.9rem;
  font-size: 0.78rem;
  font-weight: 300;
  line-height: 1.7;
  color: var(--text-2);
}

.related {
  margin-top: 1.25rem;
}
.related__list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.6rem;
}
.related__item {
  text-align: left;
}
.related__item img {
  width: 100%;
  aspect-ratio: 3 / 4;
  object-fit: cover;
  margin-bottom: 0.4rem;
  background: var(--bg-3);
}
.related__item span {
  display: block;
  font-size: 0.68rem;
  line-height: 1.3;
  color: var(--text-2);
}
.related__item b {
  font-size: 0.72rem;
  font-weight: 600;
}
.related__item:hover span {
  color: var(--accent);
}


/* ---------- Оформление заказа ---------- */

.checkout {
  max-width: 1040px;
}
.checkout__close {
  position: absolute;
  top: 0.8rem;
  right: 0.8rem;
  z-index: 5;
  border: 1px solid var(--line-accent);
  background: rgba(8, 8, 13, 0.75);
  color: var(--text);
}
.checkout__close:hover {
  border-color: var(--accent);
  color: var(--accent);
}
.checkout__grid {
  display: grid;
  grid-template-columns: 1.25fr 1fr;
}
.checkout__form {
  padding: clamp(1.25rem, 3vw, 2.25rem);
}
.checkout__title {
  margin-bottom: 0.3rem;
  font-family: var(--font-serif);
  font-size: 1.6rem;
  font-weight: 300;
}
.checkout__lead {
  margin-bottom: 1.5rem;
  font-size: 0.8rem;
  font-weight: 300;
  color: var(--text-3);
}
.checkout__section {
  margin: 1.4rem 0 0.7rem;
  font-size: 0.62rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--accent);
}
.field-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.7rem;
}
.field {
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
  margin-bottom: 0.7rem;
}
.field label {
  font-size: 0.68rem;
  letter-spacing: 0.04em;
  color: var(--text-3);
}
.field input,
.field textarea {
  width: 100%;
  padding: 0.75rem 0.9rem;
  border: 1px solid var(--line);
  border-radius: 0;
  background: var(--bg);
  font-size: 0.85rem;
  outline: none;
  resize: vertical;
  transition: border-color 0.3s;
}
.field input:focus,
.field textarea:focus {
  border-color: var(--accent);
}
.field input::placeholder,
.field textarea::placeholder {
  color: var(--text-3);
}
.field__error {
  display: none;
  font-size: 0.68rem;
  color: var(--danger);
}
.field.has-error input {
  border-color: var(--danger);
}
.field.has-error .field__error {
  display: block;
}

.options {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
.option {
  position: relative;
  display: block;
  cursor: pointer;
}
.option input {
  position: absolute;
  opacity: 0;
  pointer-events: none;
}
.option__body {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  padding: 0.8rem 1rem;
  border: 1px solid var(--line);
  background: var(--bg);
  transition: all 0.25s;
}
.option__body strong {
  display: block;
  font-size: 0.82rem;
  font-weight: 500;
}
.option__body small {
  font-size: 0.7rem;
  font-weight: 300;
  color: var(--text-3);
}
.option__body em {
  font-style: normal;
  font-size: 0.78rem;
  white-space: nowrap;
  color: var(--text-2);
}
.option:hover .option__body {
  border-color: var(--accent-dark);
}
.option input:checked + .option__body {
  border-color: var(--accent);
  background: rgba(200, 168, 124, 0.06);
}
.option input:checked + .option__body em {
  color: var(--accent);
}
.option input:focus-visible + .option__body {
  outline: 1px solid var(--accent);
}

.agree {
  display: flex;
  align-items: flex-start;
  gap: 0.6rem;
  margin-top: 1rem;
  font-size: 0.72rem;
  line-height: 1.5;
  color: var(--text-3);
  cursor: pointer;
}
.agree input {
  margin-top: 0.15rem;
  accent-color: var(--accent);
}
.agree.has-error {
  color: var(--danger);
}

.checkout__summary {
  display: flex;
  flex-direction: column;
  padding: clamp(1.25rem, 3vw, 2.25rem);
  border-left: 1px solid var(--line);
  background: var(--bg);
}
.checkout__summary h4 {
  margin-bottom: 1rem;
  font-family: var(--font-serif);
  font-size: 1.1rem;
  font-weight: 400;
}
.checkout__items {
  flex: 1;
  max-height: 300px;
  overflow-y: auto;
  margin-bottom: 1rem;
}
.checkout__item {
  display: flex;
  gap: 0.75rem;
  padding: 0.6rem 0;
  border-bottom: 1px solid var(--line);
}
.checkout__item img {
  width: 52px;
  height: 66px;
  flex-shrink: 0;
  object-fit: cover;
  background: var(--bg-3);
}
.checkout__item-info {
  flex: 1;
  min-width: 0;
}
.checkout__item-name {
  font-family: var(--font-serif);
  font-size: 0.88rem;
  line-height: 1.3;
}
.checkout__item-meta {
  margin-top: 0.2rem;
  font-size: 0.68rem;
  color: var(--text-3);
}
.checkout__item-price {
  font-size: 0.82rem;
  font-weight: 600;
  white-space: nowrap;
}
.checkout__submit {
  width: 100%;
  margin-top: 1.1rem;
  padding: 1rem;
  background: var(--accent);
  color: var(--bg);
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  transition: all 0.3s;
}
.checkout__submit:hover {
  background: var(--accent-light);
}
.checkout__submit:active {
  transform: scale(0.98);
}
.checkout__note {
  margin-top: 0.8rem;
  text-align: center;
  font-size: 0.66rem;
  color: var(--text-3);
}

.checkout__done {
  display: none;
  padding: clamp(2.5rem, 6vw, 4.5rem) 1.5rem;
  text-align: center;
}
.checkout.is-done .checkout__grid {
  display: none;
}
.checkout.is-done .checkout__done {
  display: block;
}
.checkout__done-icon {
  width: 68px;
  height: 68px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.25rem;
  border: 1px solid var(--accent);
  border-radius: 50%;
  color: var(--accent);
  animation: pop-in 0.6s var(--spring);
}
.checkout__done-icon .icon {
  width: 28px;
  height: 28px;
}
@keyframes pop-in {
  from { transform: scale(0); opacity: 0; }
  to   { transform: scale(1); opacity: 1; }
}
.checkout__done h3 {
  margin-bottom: 0.5rem;
  font-family: var(--font-serif);
  font-size: 1.8rem;
  font-weight: 300;
}
.checkout__done p {
  max-width: 420px;
  margin: 0 auto 0.4rem;
  font-size: 0.88rem;
  font-weight: 300;
  color: var(--text-2);
}
.checkout__number {
  display: inline-block;
  margin: 1rem 0 1.5rem;
  padding: 0.5rem 1.2rem;
  border: 1px solid var(--line-accent);
  font-size: 1rem;
  letter-spacing: 0.1em;
  color: var(--accent);
}


/* ---------- Уведомление, «наверх», нижняя панель ---------- */

.toast {
  position: fixed;
  left: 50%;
  bottom: max(1.25rem, calc(1.25rem + var(--safe-bottom)));
  z-index: 10003;
  max-width: 90vw;
  display: flex;
  align-items: center;
  gap: 0.6rem;
  padding: 0.8rem 1.3rem;
  border: 1px solid var(--accent);
  background: var(--bg-2);
  box-shadow: 0 15px 40px rgba(0, 0, 0, 0.4);
  font-size: 0.78rem;
  font-weight: 500;
  transform: translateX(-50%) translateY(120px);
  transition: transform 0.4s var(--spring);
}
.toast.is-visible {
  transform: translateX(-50%) translateY(0);
}
.toast__icon {
  color: var(--accent);
}

.to-top {
  position: fixed;
  right: 1.25rem;
  bottom: 1.25rem;
  z-index: 900;
  width: 42px;
  height: 42px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid var(--line-accent);
  border-radius: 50%;
  background: rgba(15, 15, 22, 0.9);
  backdrop-filter: blur(10px);
  color: var(--accent);
  opacity: 0;
  visibility: hidden;
  transform: translateY(10px);
  transition: all 0.4s var(--ease-out);
}
.to-top.is-visible {
  opacity: 1;
  visibility: visible;
  transform: translateY(0);
}
.to-top:hover {
  background: var(--accent);
  color: var(--bg);
}

.tabbar {
  display: none;
}

/* Мобильное меню */
.mobile-menu {
  position: fixed;
  inset: 0;
  z-index: 1100;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 1.75rem;
  background: rgba(8, 8, 13, 0.97);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.4s var(--ease), visibility 0.4s;
}
.mobile-menu.is-open {
  opacity: 1;
  visibility: visible;
}
.mobile-menu__close {
  position: absolute;
  top: 0.8rem;
  right: 1rem;
  color: var(--text);
}
.mobile-menu__link {
  font-family: var(--font-serif);
  font-size: 1.8rem;
  font-weight: 300;
  letter-spacing: 0.04em;
  transition: color 0.3s;
}
.mobile-menu__link:hover {
  color: var(--accent);
}

/* Снежинки — только там, где есть мышь (на телефонах не нагружаем экран) */
.snow {
  display: none;
}
@media (hover: hover) and (pointer: fine) {
  .snow {
    display: block;
    position: fixed;
    inset: 0;
    z-index: 0;
    overflow: hidden;
    pointer-events: none;
  }
  .snowflake {
    position: absolute;
    top: -10px;
    color: #fff;
    user-select: none;
    animation: snow-fall linear infinite;
  }
  @keyframes snow-fall {
    from { transform: translateY(0) rotate(0deg); }
    to   { transform: translateY(105vh) rotate(360deg); }
  }
}


/* ==========================================================================
   Адаптив
   ========================================================================== */

@media (min-width: 1440px) {
  .products {
    grid-template-columns: repeat(4, 1fr);
  }
  .hero__content {
    max-width: 750px;
  }
}

@media (max-width: 1100px) {
  .hero__showcase {
    display: none;
  }
}

@media (max-width: 1024px) {
  .features {
    grid-template-columns: repeat(2, 1fr);
  }
  .footer__grid {
    grid-template-columns: 1fr 1fr;
    gap: 1.75rem;
  }
  .products {
    grid-template-columns: repeat(auto-fill, minmax(210px, 1fr));
  }
  .look:nth-child(1) { grid-column: 1 / 9; }
  .look:nth-child(2) { grid-column: 9 / 13; }
}

@media (max-width: 860px) {
  .product-view {
    grid-template-columns: 1fr;
    max-height: 92dvh;
  }
  .product-view__image {
    min-height: 0;
    aspect-ratio: 1 / 1;
    max-height: 42vh;
  }
  .product-view__details {
    padding: 1.25rem;
  }
  .product-view__name {
    font-size: 1.4rem;
  }

  .checkout__grid {
    grid-template-columns: 1fr;
  }
  .checkout__summary {
    order: -1;
    border-left: none;
    border-bottom: 1px solid var(--line);
  }
  .checkout__items {
    max-height: 180px;
  }
  .field-row {
    grid-template-columns: 1fr;
    gap: 0;
  }
  .checkout__title {
    padding-right: 2.5rem;
    font-size: 1.35rem;
  }
}

@media (max-width: 768px) {
  :root {
    --header-height: 54px;
  }

  .nav {
    display: none;
  }
  .header__burger {
    display: flex;
  }

  .hero__title {
    font-size: clamp(2rem, 8.5vw, 3.2rem);
  }
  .hero__text {
    max-width: 100%;
  }

  .feature {
    padding: 1.25rem 0.85rem;
  }
  .feature__icon {
    width: 28px;
    height: 28px;
  }
  .feature__title {
    font-size: 0.95rem;
  }
  .feature__text {
    font-size: 0.72rem;
  }

  .toolbar {
    flex-direction: column;
    flex-wrap: nowrap;
    align-items: stretch;
    gap: 0.65rem;
  }
  .filters {
    overflow-x: auto;
    padding-bottom: 0.35rem;
    flex-wrap: nowrap;
  }
  .filter {
    padding: 0.45rem 0.9rem;
    font-size: 0.68rem;
  }

  .products {
    grid-template-columns: repeat(2, 1fr);
    gap: 0.65rem;
  }
  .card__info {
    padding: 0.75rem;
  }
  .card__brand {
    font-size: 0.55rem;
  }
  .card__name {
    font-size: 0.95rem;
  }
  .card__category,
  .card__sizes {
    display: none;
  }
  /* На телефоне нет наведения, поэтому кнопки видны всегда */
  .card__actions {
    opacity: 1;
    transform: none;
    padding: 0.5rem;
  }
  .card__add {
    padding: 0.65rem;
    font-size: 0.62rem;
  }
  .card__wish {
    width: 34px;
    height: 34px;
  }

  .lookbook__grid {
    grid-template-columns: 1fr 1fr;
    gap: 0.6rem;
  }
  .look:nth-child(n) {
    grid-column: auto;
  }
  .look:nth-child(1),
  .look:nth-child(5) {
    grid-column: 1 / -1;
    aspect-ratio: 16 / 9;
  }
  .look__caption {
    opacity: 1;
    transform: none;
  }
  .look::after {
    opacity: 1;
  }

  .newsletter__form {
    flex-direction: column;
  }
  .newsletter__form input {
    border-right: 1px solid var(--line);
  }

  .footer {
    padding-bottom: calc(5rem + var(--safe-bottom));
  }
  .footer__grid {
    grid-template-columns: 1fr;
    gap: 1.25rem;
  }
  .footer__bottom {
    flex-direction: column;
    text-align: center;
  }

  .drawer {
    width: 100%;
    max-width: 100%;
  }
  .search {
    padding-top: 9vh;
  }
  .search__form input {
    font-size: 1.3rem;
  }
  .search__form input::placeholder {
    font-size: 0.95rem;
  }

  .to-top {
    bottom: calc(4.6rem + var(--safe-bottom));
    right: 0.9rem;
  }
  .toast {
    bottom: calc(4.8rem + var(--safe-bottom));
  }

  .tabbar {
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 900;
    display: flex;
    align-items: center;
    justify-content: space-around;
    padding: 0.4rem 0 calc(0.4rem + var(--safe-bottom));
    border-top: 1px solid var(--line);
    background: rgba(8, 8, 13, 0.94);
    backdrop-filter: saturate(180%) blur(20px);
    -webkit-backdrop-filter: saturate(180%) blur(20px);
  }
  .tabbar__item {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.15rem;
    padding: 0.25rem 0.6rem;
    font-size: 0.55rem;
    letter-spacing: 0.04em;
    text-transform: uppercase;
    color: var(--text-3);
    transition: color 0.3s;
  }
  .tabbar__item:hover,
  .tabbar__item:active {
    color: var(--accent);
  }
  .tabbar__item .icon {
    width: 22px;
    height: 22px;
  }
  .tabbar__item .badge {
    top: -3px;
    right: 0;
  }
}

@media (max-width: 480px) {
  .hero__title {
    font-size: 1.9rem;
  }
  .hero__buttons {
    flex-direction: column;
  }
  .btn {
    justify-content: center;
  }
  .products {
    gap: 0.5rem;
  }
  .section__title {
    font-size: 1.5rem;
  }
  .lookbook__grid {
    gap: 0.4rem;
  }
  .product-view__sizes .size-chip {
    min-width: 40px;
    height: 40px;
  }
  .related__list {
    gap: 0.4rem;
  }
}

/* Если у человека в системе отключены анимации — уважаем это */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
</style>
  <script>/* Страховки, которые должны сработать раньше основного скрипта. */

// 1. Не даём встроить сайт во фрейм на чужой странице (подмена и «кликджекинг»).
//    Заголовок X-Frame-Options надёжнее, но он настраивается на сервере (см. README).
(function () {
  if (window.top === window.self) return;
  try {
    window.top.location.href = window.self.location.href;
  } catch (err) {
    document.documentElement.style.display = 'none';
  }
})();

// 2. Если основной скрипт по какой-то причине не загрузился или упал,
//    прелоадер не должен навсегда закрыть страницу.
setTimeout(function () {
  const preloader = document.getElementById('preloader');
  if (preloader) preloader.classList.add('is-done');
  document.body.classList.remove('is-loading');
}, 6000);
</script>
</head>
<body class="is-loading">

  <noscript><p class="noscript">Для работы магазина нужен включённый JavaScript.</p></noscript>

  <!-- Иконки подключаются через <use href="#icon-...">, чтобы не дублировать SVG по всей странице -->
  <svg class="sprite" width="0" height="0" aria-hidden="true">
    <symbol id="icon-search" viewBox="0 0 24 24"><circle cx="11" cy="11" r="7"/><path d="M21 21l-4.35-4.35"/></symbol>
    <symbol id="icon-bag" viewBox="0 0 24 24"><path d="M6 2L3 6v14a2 2 0 002 2h14a2 2 0 002-2V6l-3-4z"/><path d="M3 6h18"/><path d="M16 10a4 4 0 01-8 0"/></symbol>
    <symbol id="icon-heart" viewBox="0 0 24 24"><path d="M20.84 4.61a5.5 5.5 0 00-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 00-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 000-7.78z"/></symbol>
    <symbol id="icon-close" viewBox="0 0 24 24"><path d="M18 6L6 18M6 6l12 12"/></symbol>
    <symbol id="icon-menu" viewBox="0 0 24 24"><path d="M3 6h18M3 12h18M3 18h18"/></symbol>
    <symbol id="icon-arrow" viewBox="0 0 24 24"><path d="M5 12h14M12 5l7 7-7 7"/></symbol>
    <symbol id="icon-arrow-up" viewBox="0 0 24 24"><path d="M12 19V5M5 12l7-7 7 7"/></symbol>
    <symbol id="icon-grid" viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/></symbol>
    <symbol id="icon-image" viewBox="0 0 24 24"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><path d="M21 15l-5-5L5 21"/></symbol>
    <symbol id="icon-check" viewBox="0 0 24 24"><path d="M5 12.5l4.5 4.5L19 7.5"/></symbol>
    <symbol id="icon-star" viewBox="0 0 24 24"><polygon points="12,2 15.1,8.6 22,9.3 16.8,14 18.4,21 12,17.3 5.6,21 7.2,14 2,9.3 8.9,8.6"/></symbol>
    <symbol id="icon-instagram" viewBox="0 0 24 24"><rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="5"/><circle cx="17.5" cy="6.5" r="1.2"/></symbol>
    <symbol id="icon-telegram" viewBox="0 0 24 24"><path d="M22 2L11 13M22 2l-7 20-4-9-9-4 20-7z"/></symbol>
    <symbol id="icon-vk" viewBox="0 0 24 24"><path d="M3 7h3c.3 3 2 6 4.5 6.5V7h3v4c2-.3 3.5-2.2 4-4h3c-.6 2.4-2.2 4-3.5 4.8 1.4.7 3.2 2.4 4 5.2h-3.2c-.6-1.7-2-3-4.3-3.3V17H10C5.8 17 3.3 13 3 7z"/></symbol>
    <symbol id="icon-quality" viewBox="0 0 48 48"><path d="M24 4l4 12h12l-10 8 4 12-10-8-10 8 4-12-10-8h12z"/></symbol>
    <symbol id="icon-warranty" viewBox="0 0 48 48"><rect x="8" y="18" width="32" height="22" rx="2"/><path d="M16 18V12a8 8 0 0116 0v6"/><circle cx="24" cy="29" r="3"/></symbol>
    <symbol id="icon-factory" viewBox="0 0 48 48"><path d="M24 4l20 10v20L24 44 4 34V14z"/><path d="M24 14v20M4 14l20 10"/></symbol>
    <symbol id="icon-delivery" viewBox="0 0 48 48"><circle cx="24" cy="24" r="18"/><path d="M24 12v12l8 4"/></symbol>
  </svg>

  <!-- Прелоадер -->
  <div class="preloader" id="preloader" aria-hidden="true">
    <div class="preloader__logo" id="preloaderLogo"></div>
    <div class="preloader__line"></div>
  </div>

  <!-- Снег (только на десктопе, см. CSS) -->
  <div class="snow" id="snow" aria-hidden="true"></div>

  <!-- Мобильное меню -->
  <div class="mobile-menu" id="mobileMenu" aria-hidden="true">
    <button class="icon-btn mobile-menu__close" type="button" data-close-layer="mobileMenu" aria-label="Закрыть меню">
      <svg class="icon"><use href="#icon-close"/></svg>
    </button>
    <a href="#catalog" class="mobile-menu__link" data-close-layer="mobileMenu">Каталог</a>
    <a href="#lookbook" class="mobile-menu__link" data-close-layer="mobileMenu">Lookbook</a>
    <a href="#about" class="mobile-menu__link" data-close-layer="mobileMenu">О бренде</a>
    <a href="#contacts" class="mobile-menu__link" data-close-layer="mobileMenu">Контакты</a>
  </div>

  <!-- Шапка -->
  <header class="header" id="header">
    <a href="#top" class="logo" aria-label="NOIR HIVER — на главную">
      <svg class="icon logo__icon" viewBox="0 0 32 32"><polygon points="16,2 20,12 30,12 22,19 25,30 16,23 7,30 10,19 2,12 12,12"/></svg>
      NOIR HIVER
    </a>

    <nav class="nav" aria-label="Основная навигация">
      <a href="#catalog" class="nav__link">Каталог</a>
      <a href="#lookbook" class="nav__link">Lookbook</a>
      <a href="#about" class="nav__link">О бренде</a>
      <a href="#contacts" class="nav__link">Контакты</a>
    </nav>

    <div class="header__actions">
      <button class="icon-btn" type="button" data-open-layer="search" aria-label="Поиск">
        <svg class="icon"><use href="#icon-search"/></svg>
      </button>
      <button class="icon-btn" type="button" data-open-layer="wishlist" aria-label="Избранное">
        <svg class="icon"><use href="#icon-heart"/></svg>
        <span class="badge" data-wishlist-count>0</span>
      </button>
      <button class="icon-btn" type="button" data-open-layer="cart" aria-label="Корзина">
        <svg class="icon"><use href="#icon-bag"/></svg>
        <span class="badge" data-cart-count>0</span>
      </button>
      <button class="icon-btn header__burger" type="button" data-open-layer="mobileMenu" aria-label="Меню">
        <svg class="icon"><use href="#icon-menu"/></svg>
      </button>
    </div>
  </header>

  <main id="top">

    <!-- Главный экран -->
    <section class="hero">
      <div class="hero__bg">
        <img class="hero__img fade-img" src="https://images.unsplash.com/photo-1485236715568-ddc5a6b8b5b7?w=1920&q=80" alt="" fetchpriority="high">
      </div>

      <div class="hero__content">
        <div class="hero__tag"><span class="hero__dot"></span> Зимняя коллекция 2026</div>
        <h1 class="hero__title">Искусство<br><em>зимнего</em> стиля</h1>
        <p class="hero__text">Откройте коллекцию, где каждая деталь создана для тех, кто ценит тепло, комфорт и безупречный силуэт.</p>
        <div class="hero__buttons">
          <a href="#catalog" class="btn btn--primary">
            Смотреть коллекцию
            <svg class="icon icon--sm"><use href="#icon-arrow"/></svg>
          </a>
          <a href="#lookbook" class="btn btn--ghost">Lookbook</a>
        </div>
      </div>

      <!-- Карточка товара справа, чтобы первый экран не выглядел пустым -->
      <div class="hero__showcase">
        <div class="showcase">
          <article class="showcase__card" data-product-open="3" role="button" tabindex="0" aria-label="Открыть Alpine Wool Coat">
            <img class="fade-img" src="https://images.unsplash.com/photo-1539533018447-63fcce2678e3?w=700&q=80" alt="Пальто Alpine Wool Coat">
            <span class="showcase__tag">Эксклюзив</span>
            <div class="showcase__caption">
              <div>
                <small>Выбор сезона</small>
                <h3>Alpine Wool Coat</h3>
                <p>67 200 ₽</p>
              </div>
              <span class="showcase__go"><svg class="icon icon--sm"><use href="#icon-arrow"/></svg></span>
            </div>
          </article>
          <div class="showcase__stat showcase__stat--top"><b>4.9 ★</b><span>Рейтинг покупателей</span></div>
          <div class="showcase__stat showcase__stat--bottom"><b>−30°C</b><span>Тепло в любые морозы</span></div>
        </div>
      </div>

      <a href="#catalog" class="hero__scroll" aria-label="Листайте вниз">
        <span>Листайте вниз</span>
        <i></i>
      </a>
    </section>

    <!-- Бегущая строка -->
    <div class="ticker" aria-hidden="true">
      <div class="ticker__track">
        <span>Бесплатная доставка от 15 000 ₽</span>
        <span>Возврат в течение 30 дней</span>
        <span>Натуральные материалы</span>
        <span>Собственное производство</span>
        <span>Гарантия качества 2 года</span>
        <span>Эко-упаковка</span>
        <span>Бесплатная доставка от 15 000 ₽</span>
        <span>Возврат в течение 30 дней</span>
        <span>Натуральные материалы</span>
        <span>Собственное производство</span>
        <span>Гарантия качества 2 года</span>
        <span>Эко-упаковка</span>
      </div>
    </div>

    <!-- О бренде / преимущества -->
    <section class="features" id="about">
      <div class="feature reveal">
        <svg class="icon feature__icon" viewBox="0 0 48 48"><use href="#icon-quality"/></svg>
        <h3 class="feature__title">Премиум качество</h3>
        <p class="feature__text">Кашемир, шерсть мериноса, первосортный пух — только натуральные материалы</p>
      </div>
      <div class="feature reveal">
        <svg class="icon feature__icon" viewBox="0 0 48 48"><use href="#icon-warranty"/></svg>
        <h3 class="feature__title">Гарантия 2 года</h3>
        <p class="feature__text">Уверены в каждом изделии — предоставляем расширенную гарантию на всю продукцию</p>
      </div>
      <div class="feature reveal">
        <svg class="icon feature__icon" viewBox="0 0 48 48"><use href="#icon-factory"/></svg>
        <h3 class="feature__title">Собственное производство</h3>
        <p class="feature__text">Контроль качества на каждом этапе — от дизайна до готового изделия</p>
      </div>
      <div class="feature reveal">
        <svg class="icon feature__icon" viewBox="0 0 48 48"><use href="#icon-delivery"/></svg>
        <h3 class="feature__title">Быстрая доставка</h3>
        <p class="feature__text">Доставка по всей России от 1 дня. Курьером или в пункт выдачи</p>
      </div>
    </section>

    <!-- Каталог -->
    <section class="section" id="catalog">
      <div class="section__head reveal">
        <span class="section__label">Каталог</span>
        <h2 class="section__title">Зимняя коллекция 2026</h2>
        <p class="section__text">Подборка лучших моделей для стильных зимних образов</p>
      </div>

      <div class="toolbar reveal">
        <div class="filters" id="filters" aria-label="Категории">
          <button class="filter is-active" type="button" data-category="all" aria-pressed="true">Все</button>
          <button class="filter" type="button" data-category="jackets" aria-pressed="false">Куртки</button>
          <button class="filter" type="button" data-category="coats" aria-pressed="false">Пальто</button>
          <button class="filter" type="button" data-category="sweaters" aria-pressed="false">Свитеры</button>
          <button class="filter" type="button" data-category="accessories" aria-pressed="false">Аксессуары</button>
          <button class="filter" type="button" data-category="pants" aria-pressed="false">Брюки</button>
        </div>
        <div class="sort">
          <label for="sortSelect">Сортировка:</label>
          <select id="sortSelect">
            <option value="popular">По популярности</option>
            <option value="price-asc">Цена по возрастанию</option>
            <option value="price-desc">Цена по убыванию</option>
            <option value="new">Сначала новинки</option>
          </select>
        </div>
      </div>

      <div class="catalog-info" id="catalogInfo"></div>
      <div class="products" id="products"></div>
    </section>

    <!-- Lookbook -->
    <section class="lookbook" id="lookbook">
      <div class="section__head reveal">
        <span class="section__label">Lookbook</span>
        <h2 class="section__title">Mood Winter</h2>
        <p class="section__text">Вдохновляющие образы для вашей зимы</p>
      </div>
      <div class="lookbook__grid">
        <a href="#catalog" class="look reveal">
          <img class="fade-img" src="https://images.unsplash.com/photo-1515886657613-9f3515b0c78f?w=800&q=80" alt="Образ Snow Nocturne" loading="lazy">
          <div class="look__caption"><span>Collection</span><h3>Snow Nocturne</h3></div>
        </a>
        <a href="#catalog" class="look reveal">
          <img class="fade-img" src="https://images.unsplash.com/photo-1539109136881-3be0616acf4b?w=600&q=80" alt="Образ Urban Frost" loading="lazy">
          <div class="look__caption"><span>Lookbook</span><h3>Urban Frost</h3></div>
        </a>
        <a href="#catalog" class="look reveal">
          <img class="fade-img" src="https://images.unsplash.com/photo-1490481651871-ab68de25d43d?w=600&q=80" alt="Образ Nordic Noir" loading="lazy">
          <div class="look__caption"><span>Style</span><h3>Nordic Noir</h3></div>
        </a>
        <a href="#catalog" class="look reveal">
          <img class="fade-img" src="https://images.unsplash.com/photo-1509631179647-0177331693ae?w=800&q=80" alt="Образ Alpine Glow" loading="lazy">
          <div class="look__caption"><span>Trending</span><h3>Alpine Glow</h3></div>
        </a>
        <a href="#catalog" class="look reveal">
          <img class="fade-img" src="https://images.unsplash.com/photo-1469334031218-e382a71b716b?w=600&q=80" alt="Образ Cold Luxe" loading="lazy">
          <div class="look__caption"><span>Essential</span><h3>Cold Luxe</h3></div>
        </a>
      </div>
    </section>

    <!-- Подписка -->
    <section class="section newsletter" id="newsletter">
      <div class="reveal">
        <span class="section__label">Подписка</span>
        <h2 class="section__title">Будьте первыми</h2>
        <p class="section__text">Подпишитесь и получайте эксклюзивные коллекции и специальные предложения</p>
        <form class="newsletter__form" id="newsletterForm" novalidate>
          <input class="hp" type="text" name="website" tabindex="-1" autocomplete="off" aria-hidden="true">
          <input type="email" id="newsletterEmail" maxlength="80" placeholder="Ваш email" autocomplete="email" aria-label="Ваш email" required>
          <button type="submit">Подписаться</button>
        </form>
        <p class="newsletter__error" id="newsletterError" role="alert"></p>
      </div>
    </section>
  </main>

  <!-- Подвал -->
  <footer class="footer" id="contacts">
    <div class="footer__grid">
      <div class="footer__brand">
        <a href="#top" class="logo">
          <svg class="icon logo__icon" viewBox="0 0 32 32"><polygon points="16,2 20,12 30,12 22,19 25,30 16,23 7,30 10,19 2,12 12,12"/></svg>
          NOIR HIVER
        </a>
        <p>Премиальный бренд зимней одежды. Создаём одежду для тех, кто ценит стиль, комфорт и качество с 2018 года.</p>
        <div class="footer__social">
          <a href="#" data-stub aria-label="Instagram"><svg class="icon icon--sm"><use href="#icon-instagram"/></svg></a>
          <a href="#" data-stub aria-label="Telegram"><svg class="icon icon--sm"><use href="#icon-telegram"/></svg></a>
          <a href="#" data-stub aria-label="ВКонтакте"><svg class="icon icon--sm"><use href="#icon-vk"/></svg></a>
        </div>
      </div>
      <div class="footer__col">
        <h4>Магазин</h4>
        <a href="#catalog" data-footer-category="all">Новинки</a>
        <a href="#catalog" data-footer-category="jackets">Куртки</a>
        <a href="#catalog" data-footer-category="coats">Пальто</a>
        <a href="#catalog" data-footer-category="sweaters">Свитеры</a>
        <a href="#catalog" data-footer-category="accessories">Аксессуары</a>
      </div>
      <div class="footer__col">
        <h4>Информация</h4>
        <a href="#about">О бренде</a>
        <a href="#" data-stub>Доставка</a>
        <a href="#" data-stub>Возврат</a>
        <a href="#" data-stub>Размерная сетка</a>
        <a href="#" data-stub>Уход за изделиями</a>
      </div>
      <div class="footer__col">
        <h4>Контакты</h4>
        <a href="mailto:hello@noirhiver.ru">hello@noirhiver.ru</a>
        <a href="tel:+78001234567">8 (800) 123-45-67</a>
        <span>Москва, ул. Тверская, 1</span>
        <span>Пн–Вс: 10:00 — 22:00</span>
      </div>
    </div>
    <div class="footer__bottom">
      <p>© 2026 NOIR HIVER. Все права защищены.</p>
      <div class="footer__pay"><span>VISA</span><span>MC</span><span>МИР</span><span>СБП</span></div>
    </div>
  </footer>


  <!-- ======= Слои: корзина, избранное, поиск, товар, оформление ======= -->

  <div class="overlay" id="overlay"></div>

  <!-- Корзина -->
  <aside class="drawer" id="cart" aria-hidden="true" aria-label="Корзина">
    <div class="drawer__head">
      <h3>Корзина <span id="cartTitleCount">(0)</span></h3>
      <button class="icon-btn" type="button" data-close-layer="cart" aria-label="Закрыть корзину">
        <svg class="icon"><use href="#icon-close"/></svg>
      </button>
    </div>
    <div class="drawer__body" id="cartItems"></div>
    <div class="drawer__foot" id="cartFoot" hidden>
      <div class="ship-bar">
        <p id="shipMessage"></p>
        <div class="ship-bar__track"><i id="shipFill"></i></div>
      </div>
      <form class="promo" id="promoForm" autocomplete="off">
        <input type="text" id="promoInput" maxlength="20" placeholder="Промокод" aria-label="Промокод">
        <button type="submit">Применить</button>
      </form>
      <p class="promo__hint" id="promoHint"></p>
      <div class="sum-row"><span>Подытог</span><span id="cartSubtotal">0 ₽</span></div>
      <div class="sum-row sum-row--discount" id="cartDiscountRow" hidden><span id="cartDiscountLabel">Скидка</span><span id="cartDiscount">0 ₽</span></div>
      <div class="sum-row"><span>Доставка</span><span id="cartShipping">Бесплатно</span></div>
      <div class="sum-row sum-row--total"><span>Итого</span><span id="cartTotal">0 ₽</span></div>
      <button class="drawer__checkout" type="button" id="checkoutBtn">Оформить заказ</button>
    </div>
  </aside>

  <!-- Избранное -->
  <aside class="drawer" id="wishlist" aria-hidden="true" aria-label="Избранное">
    <div class="drawer__head">
      <h3>Избранное <span id="wishlistTitleCount">(0)</span></h3>
      <button class="icon-btn" type="button" data-close-layer="wishlist" aria-label="Закрыть избранное">
        <svg class="icon"><use href="#icon-close"/></svg>
      </button>
    </div>
    <div class="drawer__body" id="wishlistItems"></div>
  </aside>

  <!-- Поиск -->
  <div class="search" id="search" aria-hidden="true" role="dialog" aria-label="Поиск по каталогу">
    <div class="search__box">
      <form class="search__form" id="searchForm" role="search">
        <svg class="icon search__icon"><use href="#icon-search"/></svg>
        <input type="search" id="searchInput" maxlength="60" placeholder="Поиск товаров..." autocomplete="off" aria-label="Поиск товаров">
        <button class="icon-btn" type="button" data-close-layer="search" aria-label="Закрыть поиск">
          <svg class="icon"><use href="#icon-close"/></svg>
        </button>
      </form>
      <div class="search__hints" id="searchHints">
        <div class="search__hints-title">Популярные запросы</div>
        <div class="search__hints-list">
          <button type="button" data-search-hint="пуховик">пуховик</button>
          <button type="button" data-search-hint="кашемир">кашемир</button>
          <button type="button" data-search-hint="пальто">пальто</button>
          <button type="button" data-search-hint="шапка">шапка</button>
          <button type="button" data-search-hint="шарф">шарф</button>
          <button type="button" data-search-hint="перчатки">перчатки</button>
        </div>
      </div>
      <div class="search__results" id="searchResults" aria-live="polite"></div>
    </div>
  </div>

  <!-- Карточка товара -->
  <div class="modal" id="productModal" aria-hidden="true">
    <div class="modal__backdrop" data-close-layer="productModal"></div>
    <div class="modal__window product-view" id="productView" role="dialog" aria-modal="true"></div>
  </div>

  <!-- Оформление заказа -->
  <div class="modal" id="checkout" aria-hidden="true">
    <div class="modal__backdrop" data-close-layer="checkout"></div>
    <div class="modal__window checkout" id="checkoutWindow" role="dialog" aria-modal="true" aria-label="Оформление заказа">
      <button class="icon-btn checkout__close" type="button" data-close-layer="checkout" aria-label="Закрыть">
        <svg class="icon"><use href="#icon-close"/></svg>
      </button>

      <div class="checkout__grid">
        <form class="checkout__form" id="checkoutForm" novalidate>
          <h2 class="checkout__title">Оформление заказа</h2>
          <p class="checkout__lead">Заполните данные — мы свяжемся с вами для подтверждения</p>

          <input class="hp" type="text" name="website" tabindex="-1" autocomplete="off" aria-hidden="true">
          <h4 class="checkout__section">Контакты</h4>
          <div class="field" data-field="name">
            <label for="coName">Имя и фамилия</label>
            <input id="coName" type="text" maxlength="60" placeholder="Иван Иванов" autocomplete="name">
            <span class="field__error">Введите имя</span>
          </div>
          <div class="field-row">
            <div class="field" data-field="phone">
              <label for="coPhone">Телефон</label>
              <input id="coPhone" type="tel" maxlength="18" placeholder="+7 (___) ___-__-__" autocomplete="tel">
              <span class="field__error">Введите номер полностью</span>
            </div>
            <div class="field" data-field="email">
              <label for="coEmail">Email</label>
              <input id="coEmail" type="email" maxlength="80" placeholder="you@mail.ru" autocomplete="email">
              <span class="field__error">Проверьте адрес почты</span>
            </div>
          </div>

          <h4 class="checkout__section">Доставка</h4>
          <div class="options">
            <label class="option"><input type="radio" name="delivery" value="courier" checked>
              <span class="option__body"><span><strong>Курьером</strong><small>1–3 дня по всей России</small></span><em data-delivery-price="courier"></em></span></label>
            <label class="option"><input type="radio" name="delivery" value="pickup">
              <span class="option__body"><span><strong>Пункт выдачи</strong><small>2–4 дня, более 5 000 пунктов</small></span><em data-delivery-price="pickup"></em></span></label>
            <label class="option"><input type="radio" name="delivery" value="store">
              <span class="option__body"><span><strong>Самовывоз из магазина</strong><small>Москва, ул. Тверская, 1</small></span><em data-delivery-price="store"></em></span></label>
          </div>
          <div id="addressBlock">
            <div class="field-row">
              <div class="field" data-field="city">
                <label for="coCity">Город</label>
                <input id="coCity" type="text" maxlength="50" placeholder="Москва" autocomplete="address-level2">
                <span class="field__error">Укажите город</span>
              </div>
              <div class="field" data-field="address">
                <label for="coAddress" id="coAddressLabel">Адрес</label>
                <input id="coAddress" type="text" maxlength="120" placeholder="Улица, дом, квартира" autocomplete="street-address">
                <span class="field__error">Укажите адрес</span>
              </div>
            </div>
          </div>

          <h4 class="checkout__section">Оплата</h4>
          <div class="options">
            <label class="option"><input type="radio" name="payment" value="card" checked>
              <span class="option__body"><span><strong>Картой онлайн</strong><small>Visa, Mastercard, МИР</small></span></span></label>
            <label class="option"><input type="radio" name="payment" value="sbp">
              <span class="option__body"><span><strong>СБП</strong><small>Оплата по QR-коду</small></span></span></label>
            <label class="option"><input type="radio" name="payment" value="cod">
              <span class="option__body"><span><strong>При получении</strong><small>Наличными или картой</small></span></span></label>
          </div>

          <h4 class="checkout__section">Комментарий</h4>
          <div class="field">
            <textarea id="coComment" rows="2" maxlength="300" placeholder="Пожелания к заказу или доставке (необязательно)"></textarea>
          </div>

          <label class="agree" id="agreeLabel">
            <input type="checkbox" id="coAgree">
            <span>Я согласен с условиями обработки персональных данных и условиями возврата</span>
          </label>
        </form>

        <aside class="checkout__summary">
          <h4>Ваш заказ</h4>
          <div class="checkout__items" id="checkoutItems"></div>
          <div class="sum-row"><span>Подытог</span><span id="coSubtotal">0 ₽</span></div>
          <div class="sum-row sum-row--discount" id="coDiscountRow" hidden><span id="coDiscountLabel">Скидка</span><span id="coDiscount">0 ₽</span></div>
          <div class="sum-row"><span>Доставка</span><span id="coShipping">Бесплатно</span></div>
          <div class="sum-row sum-row--total"><span>Итого</span><span id="coTotal">0 ₽</span></div>
          <button type="submit" form="checkoutForm" class="checkout__submit" id="coSubmit">Подтвердить заказ</button>
          <p class="checkout__note">Бесплатная доставка от 15 000 ₽ · Возврат 30 дней</p>
        </aside>
      </div>

      <!-- Экран «заказ оформлен» -->
      <div class="checkout__done" id="checkoutDone">
        <div class="checkout__done-icon"><svg class="icon"><use href="#icon-check"/></svg></div>
        <h3>Заказ оформлен!</h3>
        <p id="doneText"></p>
        <div class="checkout__number" id="doneNumber">NH-000000</div>
        <p id="doneSummary"></p>
        <button class="btn btn--primary" type="button" data-close-layer="checkout">Продолжить покупки</button>
      </div>
    </div>
  </div>

  <div class="toast" id="toast" role="status" aria-live="polite">
    <svg class="icon icon--sm toast__icon"><use href="#icon-check"/></svg>
    <span id="toastText"></span>
  </div>

  <button class="to-top" id="toTop" type="button" aria-label="Наверх">
    <svg class="icon icon--sm"><use href="#icon-arrow-up"/></svg>
  </button>

  <!-- Нижняя панель на телефонах -->
  <nav class="tabbar" aria-label="Быстрая навигация">
    <a href="#catalog" class="tabbar__item"><svg class="icon"><use href="#icon-grid"/></svg>Каталог</a>
    <a href="#lookbook" class="tabbar__item"><svg class="icon"><use href="#icon-image"/></svg>Look</a>
    <button type="button" class="tabbar__item" data-open-layer="wishlist">
      <svg class="icon"><use href="#icon-heart"/></svg>Избр.
      <span class="badge" data-wishlist-count>0</span>
    </button>
    <button type="button" class="tabbar__item" data-open-layer="cart">
      <svg class="icon"><use href="#icon-bag"/></svg>Корзина
      <span class="badge" data-cart-count>0</span>
    </button>
  </nav>

  <script>// Каталог товаров NOIR HIVER.
// Все цены в рублях. Поле soldOut — размеры, которых сейчас нет в наличии.

const CATEGORIES = {
  jackets: 'Куртки',
  coats: 'Пальто',
  sweaters: 'Свитеры',
  accessories: 'Аксессуары',
  pants: 'Брюки'
};

const PRODUCTS = [
  {
    id: 1,
    name: "Nordic Aurora Parka",
    category: "jackets",
    price: 42900,
    oldPrice: null,
    badge: "new",
    image: "https://images.unsplash.com/photo-1551028719-00167b16eac5?w=600&q=80",
    description: "Мужской пуховик из переработанного нейлона с наполнителем из первосортного гусиного пуха 800 FP. Водостойкая пропитка DWR, капюшон с меховым ободком, регулируемые манжеты и низ.",
    sizes: ["S","M","L","XL","XXL"],
    soldOut: [],
    rating: 4.9,
    reviews: 124
  },
  {
    id: 2,
    name: "Cashmere Oversized Sweater",
    category: "sweaters",
    price: 28500,
    oldPrice: null,
    badge: null,
    image: "https://images.unsplash.com/photo-1576566588028-4147f3842f27?w=600&q=80",
    description: "Свитер свободного кроя из 100% кашемира. Невероятно мягкий и тёплый, идеально подходит для холодных дней.",
    sizes: ["XS","S","M","L","XL"],
    soldOut: ["XS"],
    rating: 4.8,
    reviews: 89
  },
  {
    id: 3,
    name: "Alpine Wool Coat",
    category: "coats",
    price: 67200,
    oldPrice: null,
    badge: "exclusive",
    image: "https://images.unsplash.com/photo-1539533018447-63fcce2678e3?w=600&q=80",
    description: "Эксклюзивное пальто из итальянской шерсти мериноса. Двубортный крой, подкладка из шёлка, лаконичный силуэт. Насыщенный charcoal цвет.",
    sizes: ["S","M","L"],
    soldOut: [],
    rating: 5,
    reviews: 56
  },
  {
    id: 4,
    name: "Thermal Gloves Premium",
    category: "accessories",
    price: 4800,
    oldPrice: 6500,
    badge: "sale",
    image: "https://images.unsplash.com/photo-1531163804074-29bb7f47b66b?w=600&q=80",
    description: "Тёплые перчатки из натуральной овчины с подкладкой из тонкого флиса. Касание сенсорных экранов, усиленные швы. Универсальный чёрный цвет.",
    sizes: ["S","M","L"],
    soldOut: ["L"],
    rating: 4.7,
    reviews: 203
  },
  {
    id: 5,
    name: "Glacier Puffer Jacket",
    category: "jackets",
    price: 38100,
    oldPrice: null,
    badge: "new",
    image: "https://images.unsplash.com/photo-1544923246-77307dd270cb?w=600&q=80",
    description: "Лёгкий стеганый пуховик со стёганым рисунком. Утепление 700 FP гусиный пух. Вместительные карманы, регулируемый капюшон, упаковывается в карман.",
    sizes: ["S","M","L","XL"],
    soldOut: [],
    rating: 4.8,
    reviews: 167
  },
  {
    id: 6,
    name: "Merino Ribbed Beanie",
    category: "accessories",
    price: 3200,
    oldPrice: null,
    badge: null,
    image: "https://images.unsplash.com/photo-1576871337632-b9aef4c17ab9?w=600&q=80",
    description: "Шапка из тонкого рубчатого трикотажа мериноса. Удобная резинка, оптимальный комфорт до -15°C. Универсальный размер.",
    sizes: ["ONE"],
    soldOut: [],
    rating: 4.6,
    reviews: 312
  },
  {
    id: 7,
    name: "Herringbone Wool Scarf",
    category: "accessories",
    price: 5600,
    oldPrice: null,
    badge: null,
    image: "https://images.unsplash.com/photo-1520903920243-00d872a2d1c9?w=600&q=80",
    description: "Плотный шарф из шерстяной пряжи в елочку. Изысканный дизайн, идеально дополнит любой зимний образ. Размер 200×35 см.",
    sizes: ["ONE"],
    soldOut: [],
    rating: 4.9,
    reviews: 98
  },
  {
    id: 8,
    name: "Tech Snow Pants",
    category: "pants",
    price: 31500,
    oldPrice: 42000,
    badge: "sale",
    image: "https://images.unsplash.com/photo-1624378439575-d8705ad7ae80?w=600&q=80",
    description: "Брюки с ветрозащитной мембраной. Утеплитель из флиса, регулируемые подтяжки, усиленные колени.",
    sizes: ["S","M","L","XL"],
    soldOut: ["S"],
    rating: 4.7,
    reviews: 145
  },
  {
    id: 9,
    name: "Sherpa-Lined Chinos",
    category: "pants",
    price: 19800,
    oldPrice: null,
    badge: "new",
    image: "https://images.unsplash.com/photo-1473966968600-fa801b869a1a?w=600&q=80",
    description: "Утеплённые чинос с подкладкой из овчины. Плотный хлопок-смес, классический крой. Подойдут и для города, и для гор.",
    sizes: ["28","30","32","34","36"],
    soldOut: ["28"],
    rating: 4.5,
    reviews: 78
  },
  {
    id: 10,
    name: "Structured Blazer Coat",
    category: "coats",
    price: 55400,
    oldPrice: null,
    badge: "exclusive",
    image: "https://images.unsplash.com/photo-1591047139829-d91aecb6caea?w=600&q=80",
    description: "Укороченное блейзер-пальто из дублёной овчины. Чёткий силуэт, лаконичные лацканы, подкладка из вискозы.",
    sizes: ["S","M","L"],
    soldOut: ["L"],
    rating: 4.9,
    reviews: 42
  },
  {
    id: 11,
    name: "Chunky Knit Cardigan",
    category: "sweaters",
    price: 24600,
    oldPrice: 31000,
    badge: "sale",
    image: "https://images.unsplash.com/photo-1434389677669-e08b4cda3a0f?w=600&q=80",
    description: "Объёмный вязаный кардиган из смесовой пряжи с альпакой. Молния из натурального металла, внутренний карман.",
    sizes: ["S","M","L","XL"],
    soldOut: [],
    rating: 4.8,
    reviews: 91
  },
  {
    id: 12,
    name: "Shell Anorak Jacket",
    category: "jackets",
    price: 35800,
    oldPrice: null,
    badge: null,
    image: "https://images.unsplash.com/photo-1559551409-dadc959f76b8?w=600&q=80",
    description: "Ветровка-анорак с ветрозащитной мембраной. Влагонепроницаемые швы, регулируемые манжеты, капюшон с козырьком.",
    sizes: ["XS","S","M","L","XL"],
    soldOut: ["XS"],
    rating: 4.6,
    reviews: 134
  }
];

/* NOIR HIVER — логика сайта.
   Данные товаров лежат в products.js (PRODUCTS и CATEGORIES). */

const FREE_SHIPPING_FROM = 15000;
const MAX_QTY = 10;
const SHIPPING_PRICE = { courier: 1500, pickup: 500, store: 0 };
const PROMO_CODES = {
  NOIR10: 10,
  WINTER26: 15
};
const STORAGE_KEY = 'noir-hiver';

// Всё, что меняется во время работы сайта, лежит в одном объекте
const state = {
  category: 'all',
  sort: 'popular',
  query: '',
  cart: [],          // [{ id, size, qty }]
  wishlist: [],      // [id, id, ...]
  promo: null,       // например 'NOIR10'
  chosenSizes: {}    // размеры, выбранные на карточках каталога: { id: 'M' }
};

const modal = { id: null, size: null };

// Слои страницы: корзина, избранное, поиск, окна
const layers = {
  cart: document.getElementById('cart'),
  wishlist: document.getElementById('wishlist'),
  search: document.getElementById('search'),
  productModal: document.getElementById('productModal'),
  checkout: document.getElementById('checkout'),
  mobileMenu: document.getElementById('mobileMenu')
};
const drawerNames = ['cart', 'wishlist'];
const overlay = document.getElementById('overlay');

const el = {
  header: document.getElementById('header'),
  toTop: document.getElementById('toTop'),
  products: document.getElementById('products'),
  catalogInfo: document.getElementById('catalogInfo'),
  filters: document.getElementById('filters'),
  sortSelect: document.getElementById('sortSelect'),
  cartItems: document.getElementById('cartItems'),
  cartFoot: document.getElementById('cartFoot'),
  wishlistItems: document.getElementById('wishlistItems'),
  productView: document.getElementById('productView'),
  searchInput: document.getElementById('searchInput'),
  searchHints: document.getElementById('searchHints'),
  searchResults: document.getElementById('searchResults'),
  toast: document.getElementById('toast'),
  toastText: document.getElementById('toastText')
};


/* ---------- Мелкие помощники ---------- */

function formatPrice(value) {
  return value.toLocaleString('ru-RU') + ' ₽';
}

function findProduct(id) {
  return PRODUCTS.find(function (p) { return p.id === id; });
}

function availableSizes(product) {
  return product.sizes.filter(function (s) { return !product.soldOut.includes(s); });
}

function discountPercent(product) {
  if (!product.oldPrice) return 0;
  return Math.round((1 - product.price / product.oldPrice) * 100);
}

function plural(n, one, few, many) {
  const mod10 = n % 10;
  const mod100 = n % 100;
  if (mod10 === 1 && mod100 !== 11) return one;
  if (mod10 >= 2 && mod10 <= 4 && (mod100 < 10 || mod100 >= 20)) return few;
  return many;
}

// Убираем управляющие символы и лишние пробелы, ограничиваем длину
function cleanText(value, maxLength) {
  return value.replace(/[\u0000-\u001f\u007f]/g, ' ').replace(/\s+/g, ' ').trim().slice(0, maxLength);
}

function escapeHtml(text) {
  return text.replace(/[&<>"']/g, function (ch) {
    return { '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#39;' }[ch];
  });
}

function icon(name, extraClass) {
  return '<svg class="icon ' + (extraClass || '') + '"><use href="#icon-' + name + '"/></svg>';
}

function productImage(product, className) {
  return '<img class="fade-img ' + (className || '') + '" src="' + product.image +
         '" alt="' + escapeHtml(product.name) + '" loading="lazy">';
}

let toastTimer;
function showToast(text) {
  el.toastText.textContent = text;
  el.toast.classList.add('is-visible');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(function () {
    el.toast.classList.remove('is-visible');
  }, 2600);
}


/* ---------- Сохранение в браузере ---------- */

function saveState() {
  try {
    localStorage.setItem(STORAGE_KEY, JSON.stringify({
      cart: state.cart,
      wishlist: state.wishlist,
      promo: state.promo
    }));
  } catch (err) {
    // приватный режим или переполненное хранилище — просто работаем без сохранения
  }
}

// Данные из localStorage может подправить кто угодно через консоль браузера,
// поэтому каждое значение проверяем и приводим к допустимому виду.
function loadState() {
  state.cart = [];
  state.wishlist = [];
  state.promo = null;

  try {
    const saved = JSON.parse(localStorage.getItem(STORAGE_KEY) || '{}') || {};

    (Array.isArray(saved.cart) ? saved.cart : []).forEach(function (item) {
      const product = item && findProduct(item.id);
      const qty = item && Number(item.qty);
      if (!product || !product.sizes.includes(item.size) || product.soldOut.includes(item.size)) return;
      if (!Number.isInteger(qty) || qty < 1) return;

      const same = state.cart.find(function (x) { return x.id === item.id && x.size === item.size; });
      if (same) {
        same.qty = Math.min(MAX_QTY, same.qty + qty);
      } else {
        state.cart.push({ id: item.id, size: item.size, qty: Math.min(MAX_QTY, qty) });
      }
    });

    (Array.isArray(saved.wishlist) ? saved.wishlist : []).forEach(function (id) {
      if (findProduct(id) && !state.wishlist.includes(id)) state.wishlist.push(id);
    });

    if (typeof saved.promo === 'string' && PROMO_CODES[saved.promo]) state.promo = saved.promo;
  } catch (err) {
    // повреждённые данные — начинаем с чистого листа
  }
}


/* ---------- Слои (корзина, поиск, окна) и блокировка прокрутки ---------- */

let lockCount = 0;
let lockedScrollY = 0;

function lockScroll() {
  if (lockCount === 0) {
    lockedScrollY = window.scrollY;
    document.body.style.top = '-' + lockedScrollY + 'px';
    document.body.classList.add('is-locked');
  }
  lockCount++;
}

function unlockScroll() {
  lockCount = Math.max(0, lockCount - 1);
  if (lockCount === 0) {
    document.body.classList.remove('is-locked');
    document.body.style.top = '';
    window.scrollTo({ top: lockedScrollY, left: 0, behavior: 'instant' });
  }
}

const openStack = [];   // какие слои открыты сейчас, последний — верхний
const openers = {};     // кто открыл слой, чтобы вернуть ему фокус при закрытии

// Пока открыто окно, фон «выключаем»: до него нельзя добраться клавишей Tab
function updatePageInert() {
  const locked = openStack.length > 0;
  document.querySelectorAll('.header, main, .footer, .tabbar').forEach(function (node) {
    node.inert = locked;
  });
}

function openLayer(name) {
  const layer = layers[name];
  if (!layer || layer.classList.contains('is-open')) return;

  // две боковые панели одновременно не нужны
  if (drawerNames.includes(name)) {
    drawerNames.filter(function (n) { return n !== name; }).forEach(function (n) { closeLayer(n); });
    overlay.classList.add('is-open');
  }

  openers[name] = document.activeElement;
  openStack.push(name);
  layer.classList.add('is-open');
  layer.setAttribute('aria-hidden', 'false');
  updatePageInert();
  lockScroll();

  if (name === 'search') {
    el.searchInput.value = '';
    renderSearch('');
    setTimeout(function () { el.searchInput.focus(); }, 250);
  }
}

function closeLayer(name, keepFocus) {
  const layer = layers[name];
  if (!layer || !layer.classList.contains('is-open')) return;

  layer.classList.remove('is-open');
  layer.setAttribute('aria-hidden', 'true');
  if (drawerNames.includes(name)) overlay.classList.remove('is-open');
  openStack.splice(openStack.indexOf(name), 1);
  updatePageInert();
  unlockScroll();

  // возвращаем фокус туда, откуда пользователь пришёл
  const opener = openers[name];
  delete openers[name];
  if (!keepFocus && opener && document.contains(opener) && opener.getClientRects().length) {
    opener.focus({ preventScroll: true });
  }
}

// Сначала открываем новое окно, потом закрываем старое — так страница не «прыгает»
function switchLayer(from, to) {
  const inherited = openers[from];
  openLayer(to);
  if (inherited) openers[to] = inherited;
  closeLayer(from, true);
}


/* ---------- Каталог ---------- */

function normalize(text) {
  return text.toLowerCase().replace(/ё/g, 'е');
}

// Грубое отсечение окончания, чтобы «куртка» находила «куртки», а «пуховика» — «пуховик»
function stem(word) {
  if (word.length <= 4) return word;
  return word.slice(0, Math.max(4, Math.min(6, word.length - 2)));
}

function matchesQuery(product, query) {
  const haystack = normalize(product.name + ' ' + CATEGORIES[product.category] + ' ' + product.description);
  return normalize(query)
    .split(/\s+/)
    .filter(Boolean)
    .every(function (word) { return haystack.includes(stem(word)); });
}

function getVisibleProducts() {
  let list = PRODUCTS.filter(function (p) {
    return state.category === 'all' || p.category === state.category;
  });

  if (state.query) {
    list = list.filter(function (p) { return matchesQuery(p, state.query); });
  }

  if (state.sort === 'price-asc') {
    list.sort(function (a, b) { return a.price - b.price; });
  } else if (state.sort === 'price-desc') {
    list.sort(function (a, b) { return b.price - a.price; });
  } else if (state.sort === 'new') {
    list.sort(function (a, b) { return (b.badge === 'new') - (a.badge === 'new'); });
  } else {
    list.sort(function (a, b) { return b.reviews - a.reviews; });
  }
  return list;
}

function badgeHtml(product, extraClass) {
  if (!product.badge) return '';
  const labels = {
    new: 'Новинка',
    sale: 'Sale ' + discountPercent(product) + '%',
    exclusive: 'Эксклюзив'
  };
  return '<span class="card__badge card__badge--' + product.badge + ' ' + (extraClass || '') + '">' +
         labels[product.badge] + '</span>';
}

function priceHtml(product) {
  let html = '<strong>' + formatPrice(product.price) + '</strong>';
  if (product.oldPrice) {
    html += '<s>' + formatPrice(product.oldPrice) + '</s><em>−' + discountPercent(product) + '%</em>';
  }
  return html;
}

function cardHtml(product) {
  const liked = state.wishlist.includes(product.id);
  const chosen = state.chosenSizes[product.id];

  const sizes = product.sizes.map(function (size) {
    const soldOut = product.soldOut.includes(size);
    const selected = chosen === size ? ' is-selected' : '';
    return '<button class="size-chip' + selected + '" type="button" data-action="chooseSize" ' +
           'data-id="' + product.id + '" data-size="' + size + '"' + (soldOut ? ' disabled' : '') + '>' +
           size + '</button>';
  }).join('');

  return '' +
    '<article class="card reveal" data-product-open="' + product.id + '">' +
      '<div class="card__image">' +
        productImage(product) +
        badgeHtml(product) +
        '<div class="card__actions">' +
          '<button class="card__add" type="button" data-action="quickAdd" data-id="' + product.id + '">' +
            icon('bag', 'icon--sm') + 'В корзину' +
          '</button>' +
          '<button class="card__wish' + (liked ? ' is-liked' : '') + '" type="button" ' +
                  'data-action="toggleWish" data-id="' + product.id + '" aria-label="В избранное">' +
            icon('heart') +
          '</button>' +
        '</div>' +
      '</div>' +
      '<div class="card__info">' +
        '<div class="card__brand">NOIR HIVER</div>' +
        '<h3><button class="card__name" type="button" data-product-open="' + product.id + '">' +
          escapeHtml(product.name) + '</button></h3>' +
        '<div class="card__category">' + CATEGORIES[product.category] + '</div>' +
        '<div class="card__price">' + priceHtml(product) + '</div>' +
        '<div class="card__sizes">' + sizes + '</div>' +
      '</div>' +
    '</article>';
}

function renderCatalog() {
  const list = getVisibleProducts();

  if (list.length === 0) {
    el.products.innerHTML =
      '<div class="products__empty"><p>По вашему запросу ничего не нашлось</p>' +
      '<button type="button" data-action="resetFilters">Сбросить фильтры</button></div>';
  } else {
    el.products.innerHTML = list.map(cardHtml).join('');
    observeReveal(el.products);
  }

  let info = list.length + ' ' + plural(list.length, 'товар', 'товара', 'товаров');
  if (state.query) {
    info = '<span class="chip">Поиск: «' + escapeHtml(state.query) + '» ' +
           '<button type="button" data-action="clearQuery" aria-label="Сбросить поиск">' +
           icon('close', 'icon--sm') + '</button></span>' + info;
  }
  el.catalogInfo.innerHTML = info;
}

function setCategory(category) {
  state.category = category;
  el.filters.querySelectorAll('.filter').forEach(function (btn) {
    const active = btn.dataset.category === category;
    btn.classList.toggle('is-active', active);
    btn.setAttribute('aria-pressed', active);
  });
  renderCatalog();
}


/* ---------- Избранное ---------- */

function toggleWishlist(id) {
  const index = state.wishlist.indexOf(id);
  if (index === -1) {
    state.wishlist.push(id);
    showToast('Добавлено в избранное');
  } else {
    state.wishlist.splice(index, 1);
  }
  saveState();
  updateWishlistUi();
}

function updateWishlistUi() {
  const count = state.wishlist.length;

  document.querySelectorAll('[data-wishlist-count]').forEach(function (badge) {
    badge.textContent = count;
    badge.classList.toggle('is-visible', count > 0);
  });
  document.getElementById('wishlistTitleCount').textContent = '(' + count + ')';

  // обновляем сердечки на карточках и в окне товара, не перерисовывая каталог
  document.querySelectorAll('[data-action="toggleWish"], [data-action="modalWish"]').forEach(function (btn) {
    const id = btn.dataset.id ? Number(btn.dataset.id) : modal.id;
    btn.classList.toggle('is-liked', state.wishlist.includes(id));
  });

  if (count === 0) {
    el.wishlistItems.innerHTML =
      '<div class="drawer__empty">' + icon('heart') +
      '<p>В избранном пока пусто</p>' +
      '<button type="button" data-action="goCatalog">Перейти в каталог</button></div>';
    return;
  }

  el.wishlistItems.innerHTML = state.wishlist.map(function (id) {
    const p = findProduct(id);
    return '' +
      '<div class="line-item">' +
        '<img class="line-item__img fade-img" src="' + p.image + '" alt="" data-product-open="' + p.id + '">' +
        '<div class="line-item__info">' +
          '<div>' +
            '<button class="line-item__name" type="button" data-product-open="' + p.id + '">' + escapeHtml(p.name) + '</button>' +
            '<div class="line-item__meta">' + CATEGORIES[p.category] + '</div>' +
          '</div>' +
          '<div class="line-item__row">' +
            '<div class="line-item__links">' +
              '<button class="line-item__link line-item__link--accent" type="button" data-action="wishlistToCart" data-id="' + p.id + '">В корзину</button>' +
              '<button class="line-item__link" type="button" data-action="toggleWish" data-id="' + p.id + '">Убрать</button>' +
            '</div>' +
            '<div class="line-item__price">' + formatPrice(p.price) + '</div>' +
          '</div>' +
        '</div>' +
      '</div>';
  }).join('');
}


/* ---------- Корзина ---------- */

function calcTotals(deliveryMethod) {
  const subtotal = state.cart.reduce(function (sum, item) {
    return sum + findProduct(item.id).price * item.qty;
  }, 0);

  const percent = state.promo ? PROMO_CODES[state.promo] : 0;
  const discount = Math.round(subtotal * percent / 100);
  const goods = subtotal - discount;

  let shipping = SHIPPING_PRICE[deliveryMethod || 'courier'];
  if (goods === 0 || goods >= FREE_SHIPPING_FROM) shipping = 0;

  return { subtotal: subtotal, discount: discount, percent: percent, goods: goods, shipping: shipping, total: goods + shipping };
}

function addToCart(id, size) {
  const product = findProduct(id);
  if (!product || !size || !availableSizes(product).includes(size)) {
    showToast('Этого размера сейчас нет в наличии');
    return;
  }

  const existing = state.cart.find(function (item) { return item.id === id && item.size === size; });

  if (existing) {
    if (existing.qty >= MAX_QTY) {
      showToast('Не больше ' + MAX_QTY + ' шт. одного размера');
      return;
    }
    existing.qty++;
  } else {
    state.cart.push({ id: id, size: size, qty: 1 });
  }

  updateCartUi();
  showToast(product.name + ' — в корзине');
}

function updateCartUi() {
  const count = state.cart.reduce(function (sum, item) { return sum + item.qty; }, 0);

  document.querySelectorAll('[data-cart-count]').forEach(function (badge) {
    badge.textContent = count;
    badge.classList.toggle('is-visible', count > 0);
  });
  document.getElementById('cartTitleCount').textContent = '(' + count + ')';

  if (state.cart.length === 0) {
    el.cartItems.innerHTML =
      '<div class="drawer__empty">' + icon('bag') +
      '<p>Ваша корзина пуста</p>' +
      '<button type="button" data-action="goCatalog">Перейти в каталог</button></div>';
    el.cartFoot.hidden = true;
    saveState();
    return;
  }

  el.cartItems.innerHTML = state.cart.map(function (item, index) {
    const p = findProduct(item.id);
    return '' +
      '<div class="line-item">' +
        '<img class="line-item__img fade-img" src="' + p.image + '" alt="" data-product-open="' + p.id + '">' +
        '<div class="line-item__info">' +
          '<div>' +
            '<button class="line-item__name" type="button" data-product-open="' + p.id + '">' + escapeHtml(p.name) + '</button>' +
            '<div class="line-item__meta">Размер: ' + item.size + ' · NOIR HIVER</div>' +
          '</div>' +
          '<div class="line-item__row">' +
            '<div class="qty">' +
              '<button type="button" data-action="cartQty" data-index="' + index + '" data-delta="-1" aria-label="Меньше">−</button>' +
              '<span>' + item.qty + '</span>' +
              '<button type="button" data-action="cartQty" data-index="' + index + '" data-delta="1" aria-label="Больше">+</button>' +
            '</div>' +
            '<div class="line-item__price">' + formatPrice(p.price * item.qty) + '</div>' +
          '</div>' +
          '<div class="line-item__links">' +
            '<button class="line-item__link" type="button" data-action="cartRemove" data-index="' + index + '">Удалить</button>' +
          '</div>' +
        '</div>' +
      '</div>';
  }).join('');

  const totals = calcTotals('courier');
  el.cartFoot.hidden = false;
  document.getElementById('cartSubtotal').textContent = formatPrice(totals.subtotal);
  document.getElementById('cartShipping').textContent = totals.shipping === 0 ? 'Бесплатно' : formatPrice(totals.shipping);
  document.getElementById('cartTotal').textContent = formatPrice(totals.total);

  const discountRow = document.getElementById('cartDiscountRow');
  discountRow.hidden = totals.discount === 0;
  document.getElementById('cartDiscountLabel').textContent = 'Скидка по промокоду ' + (state.promo || '');
  document.getElementById('cartDiscount').textContent = '−' + formatPrice(totals.discount);

  // полоса «до бесплатной доставки»
  const left = FREE_SHIPPING_FROM - totals.goods;
  document.getElementById('shipMessage').innerHTML = left > 0
    ? 'До бесплатной доставки осталось <b>' + formatPrice(left) + '</b>'
    : 'Бесплатная доставка для вашего заказа <b>✓</b>';
  document.getElementById('shipFill').style.width = Math.min(100, Math.round(totals.goods / FREE_SHIPPING_FROM * 100)) + '%';

  renderPromoField();
  saveState();
}

function renderPromoField() {
  const input = document.getElementById('promoInput');
  const button = document.querySelector('#promoForm button');
  const hint = document.getElementById('promoHint');

  if (state.promo) {
    input.value = state.promo;
    input.readOnly = true;
    button.textContent = 'Убрать';
    hint.textContent = 'Промокод применён: −' + PROMO_CODES[state.promo] + '%';
    hint.className = 'promo__hint is-ok';
  } else {
    input.readOnly = false;
    button.textContent = 'Применить';
    if (!hint.classList.contains('is-error')) {
      hint.textContent = 'Например, NOIR10';
      hint.className = 'promo__hint';
    }
  }
}

function handlePromoSubmit(event) {
  event.preventDefault();
  const input = document.getElementById('promoInput');
  const hint = document.getElementById('promoHint');

  if (state.promo) {
    state.promo = null;
    input.value = '';
    hint.className = 'promo__hint';
    updateCartUi();
    return;
  }

  const code = input.value.trim().toUpperCase();
  if (!code) return;

  if (PROMO_CODES[code]) {
    state.promo = code;
    hint.className = 'promo__hint';
    updateCartUi();
    showToast('Промокод применён');
  } else {
    hint.textContent = 'Такого промокода нет';
    hint.className = 'promo__hint is-error';
  }
}


/* ---------- Окно товара ---------- */

function openProduct(id) {
  const product = findProduct(id);
  if (!product) return;

  const sizes = availableSizes(product);
  modal.id = id;
  modal.size = state.chosenSizes[id] || (sizes.length === 1 ? sizes[0] : null);

  renderProductView();
  el.productView.scrollTop = 0;

  // если окно открывают из поиска или корзины — переключаем слой без прыжка страницы
  const opener = ['search', 'cart', 'wishlist'].find(function (name) {
    return layers[name].classList.contains('is-open');
  });
  if (opener) {
    switchLayer(opener, 'productModal');
  } else {
    openLayer('productModal');
  }
}

function relatedProducts(product) {
  const sameCategory = PRODUCTS.filter(function (p) { return p.id !== product.id && p.category === product.category; });
  const others = PRODUCTS.filter(function (p) { return p.id !== product.id && p.category !== product.category; });
  return sameCategory.concat(others).slice(0, 3);
}

function renderProductView() {
  const p = findProduct(modal.id);
  const liked = state.wishlist.includes(p.id);
  const stars = '★'.repeat(Math.round(p.rating));

  const sizeButtons = p.sizes.map(function (size) {
    const soldOut = p.soldOut.includes(size);
    const selected = modal.size === size ? ' is-selected' : '';
    return '<button class="size-chip' + selected + '" type="button" data-action="modalSize" data-size="' + size + '"' +
           (soldOut ? ' disabled' : '') + '>' + size + '</button>';
  }).join('');

  const related = relatedProducts(p).map(function (r) {
    return '<button class="related__item" type="button" data-product-open="' + r.id + '">' +
             productImage(r) +
             '<span>' + escapeHtml(r.name) + '</span><b>' + formatPrice(r.price) + '</b>' +
           '</button>';
  }).join('');

  el.productView.setAttribute('aria-label', p.name);
  el.productView.innerHTML = '' +
    '<div class="product-view__image">' +
      productImage(p) +
      '<button class="icon-btn product-view__close" type="button" data-close-layer="productModal" aria-label="Закрыть">' + icon('close') + '</button>' +
    '</div>' +
    '<div class="product-view__details">' +
      '<div class="product-view__brand">NOIR HIVER · ' + CATEGORIES[p.category] + '</div>' +
      badgeHtml(p, 'product-view__badge') +
      '<h2 class="product-view__name">' + escapeHtml(p.name) + '</h2>' +
      '<div class="product-view__rating"><span>' + stars + '</span><span>' + p.rating + ' (' + p.reviews + ' ' +
        plural(p.reviews, 'отзыв', 'отзыва', 'отзывов') + ')</span></div>' +
      '<div class="product-view__price">' + formatPrice(p.price) +
        (p.oldPrice ? '<s>' + formatPrice(p.oldPrice) + '</s>' : '') + '</div>' +
      '<p class="product-view__text">' + escapeHtml(p.description) + '</p>' +
      '<div class="product-view__label">Размер</div>' +
      '<div class="product-view__sizes">' + sizeButtons + '</div>' +
      '<div class="product-view__hint" id="sizeHint"></div>' +
      '<div class="product-view__buttons">' +
        '<button class="product-view__add" type="button" data-action="modalAdd">Добавить в корзину</button>' +
        '<button class="wish-btn' + (liked ? ' is-liked' : '') + '" type="button" data-action="modalWish" aria-label="В избранное">' + icon('heart') + '</button>' +
      '</div>' +
      '<div class="product-view__more">' +
        '<details><summary>Состав и уход</summary><p>Состав указан на внутренней бирке изделия. Рекомендуем деликатную стирку при 30°C или сухую чистку, сушить в расправленном виде.</p></details>' +
        '<details><summary>Доставка и возврат</summary><p>Доставка по всей России от 1 дня. Бесплатно при заказе от 15 000 ₽. Вернуть или обменять изделие можно в течение 30 дней.</p></details>' +
      '</div>' +
      '<div class="related"><div class="product-view__label">С этим покупают</div><div class="related__list">' + related + '</div></div>' +
    '</div>';
}


/* ---------- Поиск ---------- */

function renderSearch(query) {
  const text = query.trim();

  if (!text) {
    el.searchHints.hidden = false;
    el.searchResults.innerHTML = '';
    return;
  }
  el.searchHints.hidden = true;

  const found = PRODUCTS.filter(function (p) { return matchesQuery(p, text); });

  if (found.length === 0) {
    el.searchResults.innerHTML =
      '<div class="search__empty"><strong>Ничего не найдено</strong>' +
      'Попробуйте другое слово, например «пуховик» или «шарф»</div>';
    return;
  }

  const words = normalize(text).split(/\s+/).filter(Boolean).map(stem);
  const items = found.slice(0, 6).map(function (p) {
    return '' +
      '<button class="search-item" type="button" data-action="searchOpen" data-id="' + p.id + '">' +
        '<img class="fade-img" src="' + p.image + '" alt="" loading="lazy">' +
        '<span class="search-item__text">' +
          '<span class="search-item__name">' + highlight(p.name, words) + '</span>' +
          '<span class="search-item__category">' + CATEGORIES[p.category] + '</span>' +
        '</span>' +
        '<span class="search-item__price">' + formatPrice(p.price) + '</span>' +
      '</button>';
  }).join('');

  el.searchResults.innerHTML =
    '<div class="search__count">Найдено: ' + found.length + ' ' + plural(found.length, 'товар', 'товара', 'товаров') + '</div>' +
    items +
    '<button class="search__all" type="button" data-action="searchAll">Показать все в каталоге</button>';
}

// Подсвечиваем в названии совпавшую часть слова.
// Режем по сырому тексту и экранируем каждый кусок отдельно, чтобы не сломать html.
function highlight(name, stems) {
  if (stems.length === 0) return escapeHtml(name);
  const escaped = stems.map(function (s) { return s.replace(/[.*+?^${}()|[\]\\]/g, '\\$&'); });
  const parts = name.split(new RegExp('(' + escaped.join('|') + ')', 'gi'));
  return parts.map(function (part, i) {
    return i % 2 ? '<mark>' + escapeHtml(part) + '</mark>' : escapeHtml(part);
  }).join('');
}

function applySearchToCatalog() {
  const text = el.searchInput.value.trim();
  if (!text) return;

  state.query = text;
  state.category = 'all';
  el.filters.querySelectorAll('.filter').forEach(function (btn) {
    btn.classList.toggle('is-active', btn.dataset.category === 'all');
    btn.setAttribute('aria-pressed', btn.dataset.category === 'all');
  });
  closeLayer('search', true);
  renderCatalog();
  document.getElementById('catalog').scrollIntoView({ behavior: 'smooth' });
}


/* ---------- Оформление заказа ---------- */

const checkoutForm = document.getElementById('checkoutForm');
const checkoutWindow = document.getElementById('checkoutWindow');

function selectedDelivery() {
  return checkoutForm.querySelector('input[name="delivery"]:checked').value;
}

function renderCheckoutSummary() {
  const method = selectedDelivery();
  const totals = calcTotals(method);

  document.getElementById('checkoutItems').innerHTML = state.cart.map(function (item) {
    const p = findProduct(item.id);
    return '' +
      '<div class="checkout__item">' +
        '<img class="fade-img" src="' + p.image + '" alt="">' +
        '<div class="checkout__item-info">' +
          '<div class="checkout__item-name">' + escapeHtml(p.name) + '</div>' +
          '<div class="checkout__item-meta">Размер: ' + item.size + ' · ' + item.qty + ' шт.</div>' +
        '</div>' +
        '<div class="checkout__item-price">' + formatPrice(p.price * item.qty) + '</div>' +
      '</div>';
  }).join('');

  document.getElementById('coSubtotal').textContent = formatPrice(totals.subtotal);
  document.getElementById('coDiscountRow').hidden = totals.discount === 0;
  document.getElementById('coDiscountLabel').textContent = 'Скидка по промокоду ' + (state.promo || '');
  document.getElementById('coDiscount').textContent = '−' + formatPrice(totals.discount);
  document.getElementById('coShipping').textContent = totals.shipping === 0 ? 'Бесплатно' : formatPrice(totals.shipping);
  document.getElementById('coTotal').textContent = formatPrice(totals.total);
  document.getElementById('coSubmit').textContent = 'Подтвердить заказ · ' + formatPrice(totals.total);

  // цена рядом с каждым способом доставки
  Object.keys(SHIPPING_PRICE).forEach(function (key) {
    const price = calcTotals(key).shipping;
    checkoutForm.parentNode.querySelector('[data-delivery-price="' + key + '"]').textContent =
      price === 0 ? 'Бесплатно' : formatPrice(price);
  });

  // для самовывоза адрес не нужен
  document.getElementById('addressBlock').hidden = method === 'store';
  document.getElementById('coAddressLabel').textContent = method === 'pickup' ? 'Пункт выдачи или улица' : 'Адрес';
}

function openCheckout() {
  if (state.cart.length === 0) {
    showToast('Корзина пуста');
    return;
  }

  if (checkoutWindow.classList.contains('is-done')) {
    checkoutWindow.classList.remove('is-done');
    checkoutForm.reset();
  }
  checkoutForm.querySelectorAll('.has-error').forEach(function (node) { node.classList.remove('has-error'); });

  renderCheckoutSummary();
  checkoutWindow.scrollTop = 0;
  switchLayer('cart', 'checkout');
}

function formatPhone(raw) {
  let digits = raw.replace(/\D/g, '');
  if (digits[0] === '8') digits = '7' + digits.slice(1);
  if (digits && digits[0] !== '7') digits = '7' + digits;
  digits = digits.slice(0, 11);

  let result = '';
  if (digits.length > 0) result = '+7';
  if (digits.length > 1) result += ' (' + digits.slice(1, 4);
  if (digits.length >= 5) result += ') ' + digits.slice(4, 7);
  if (digits.length >= 8) result += '-' + digits.slice(7, 9);
  if (digits.length >= 10) result += '-' + digits.slice(9, 11);
  return result;
}

function handleCheckoutSubmit(event) {
  event.preventDefault();

  if (checkoutForm.elements.website.value) return;   // заполнил робот
  if (state.cart.length === 0) {                     // повторное нажатие или пустая корзина
    showToast('Корзина пуста');
    return;
  }

  const method = selectedDelivery();
  const name = cleanText(document.getElementById('coName').value, 60);
  const phone = document.getElementById('coPhone').value.replace(/\D/g, '');
  const email = document.getElementById('coEmail').value.trim();
  const city = cleanText(document.getElementById('coCity').value, 50);
  const address = cleanText(document.getElementById('coAddress').value, 120);
  const agreed = document.getElementById('coAgree').checked;

  let firstError = null;
  function fail(node) {
    node.classList.add('has-error');
    if (!firstError) firstError = node;
  }

  if (name.length < 2) fail(checkoutForm.querySelector('[data-field="name"]'));
  if (phone.length !== 11) fail(checkoutForm.querySelector('[data-field="phone"]'));
  if (!/^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/.test(email)) fail(checkoutForm.querySelector('[data-field="email"]'));
  if (method !== 'store') {
    if (city.length < 2) fail(checkoutForm.querySelector('[data-field="city"]'));
    if (address.length < 3) fail(checkoutForm.querySelector('[data-field="address"]'));
  }
  if (!agreed) fail(document.getElementById('agreeLabel'));

  if (firstError) {
    firstError.scrollIntoView({ behavior: 'smooth', block: 'center' });
    showToast('Проверьте заполнение полей');
    return;
  }

  const totals = calcTotals(method);
  const itemsCount = state.cart.reduce(function (sum, item) { return sum + item.qty; }, 0);
  const orderNumber = 'NH-' + Math.floor(100000 + Math.random() * 900000);

  document.getElementById('doneNumber').textContent = orderNumber;
  document.getElementById('doneText').textContent =
    name.split(' ')[0] + ', спасибо за покупку! Подтверждение отправим на ' + email + '.';
  document.getElementById('doneSummary').textContent =
    'Товаров: ' + itemsCount + ' · Сумма: ' + formatPrice(totals.total);

  checkoutWindow.classList.add('is-done');
  checkoutWindow.scrollTop = 0;

  state.cart = [];
  state.promo = null;
  updateCartUi();
}


/* ---------- Действия по клику (data-action) ---------- */

// Добавление «в один клик» с карточки или из избранного
function addFromList(id) {
  const sizes = availableSizes(findProduct(id));
  if (sizes.length === 0) {
    showToast('Товара нет в наличии');
  } else {
    addToCart(id, state.chosenSizes[id] || sizes[0]);
  }
}

const actions = {
  toggleWish: function (btn) {
    toggleWishlist(Number(btn.dataset.id));
  },

  chooseSize: function (btn) {
    const id = Number(btn.dataset.id);
    state.chosenSizes[id] = btn.dataset.size;
    btn.parentNode.querySelectorAll('.size-chip').forEach(function (chip) {
      chip.classList.toggle('is-selected', chip === btn);
    });
  },

  quickAdd: function (btn) {
    addFromList(Number(btn.dataset.id));
  },

  wishlistToCart: function (btn) {
    addFromList(Number(btn.dataset.id));
  },

  cartQty: function (btn) {
    const item = state.cart[Number(btn.dataset.index)];
    if (!item) return;
    const next = item.qty + Number(btn.dataset.delta);
    if (next > MAX_QTY) {
      showToast('Не больше ' + MAX_QTY + ' шт. одного размера');
      return;
    }
    item.qty = next;
    if (item.qty <= 0) state.cart.splice(Number(btn.dataset.index), 1);
    updateCartUi();
  },

  cartRemove: function (btn) {
    state.cart.splice(Number(btn.dataset.index), 1);
    updateCartUi();
  },

  modalSize: function (btn) {
    modal.size = btn.dataset.size;
    state.chosenSizes[modal.id] = modal.size;
    el.productView.querySelectorAll('.product-view__sizes .size-chip').forEach(function (chip) {
      chip.classList.toggle('is-selected', chip === btn);
    });
    document.getElementById('sizeHint').textContent = '';
    // подсветим выбранный размер и на карточке в каталоге
    const cardChip = el.products.querySelector('[data-action="chooseSize"][data-id="' + modal.id + '"][data-size="' + modal.size + '"]');
    if (cardChip) actions.chooseSize(cardChip);
  },

  modalAdd: function () {
    if (!modal.size) {
      document.getElementById('sizeHint').textContent = 'Пожалуйста, выберите размер';
      return;
    }
    addToCart(modal.id, modal.size);
    closeLayer('productModal');
  },

  modalWish: function () {
    toggleWishlist(modal.id);
  },

  searchOpen: function (btn) {
    openProduct(Number(btn.dataset.id));
  },

  searchAll: applySearchToCatalog,

  clearQuery: function () {
    state.query = '';
    renderCatalog();
  },

  resetFilters: function () {
    state.query = '';
    setCategory('all');
  },

  goCatalog: function () {
    closeLayer('cart');
    closeLayer('wishlist');
    document.getElementById('catalog').scrollIntoView({ behavior: 'smooth' });
  }
};

document.addEventListener('click', function (event) {
  const target = event.target;

  // ссылки-заглушки: разделы, которых в макете пока нет
  if (target.closest('[data-stub]')) {
    event.preventDefault();
    showToast('Раздел скоро появится');
    return;
  }

  const actionBtn = target.closest('[data-action]');
  if (actionBtn && actions[actionBtn.dataset.action]) {
    actions[actionBtn.dataset.action](actionBtn, event);
    return;
  }

  const closeBtn = target.closest('[data-close-layer]');
  if (closeBtn) {
    closeLayer(closeBtn.dataset.closeLayer);
    return;
  }

  const openBtn = target.closest('[data-open-layer]');
  if (openBtn) {
    openLayer(openBtn.dataset.openLayer);
    return;
  }

  const productEl = target.closest('[data-product-open]');
  if (productEl) {
    openProduct(Number(productEl.dataset.productOpen));
    return;
  }

  const hint = target.closest('[data-search-hint]');
  if (hint) {
    el.searchInput.value = hint.dataset.searchHint;
    renderSearch(hint.dataset.searchHint);
    el.searchInput.focus();
    return;
  }

  const footerLink = target.closest('[data-footer-category]');
  if (footerLink) {
    state.query = '';
    setCategory(footerLink.dataset.footerCategory);
  }
});

// Карточку-кнопку в hero можно открыть с клавиатуры
document.addEventListener('keydown', function (event) {
  const target = event.target;
  if ((event.key === 'Enter' || event.key === ' ') && target.matches('[data-product-open][role="button"]')) {
    event.preventDefault();
    openProduct(Number(target.dataset.productOpen));
  }
  if (event.key === 'Escape' && openStack.length) closeLayer(openStack[openStack.length - 1]);
});

overlay.addEventListener('click', function () {
  drawerNames.forEach(closeLayer);
});


/* ---------- Подключение событий ---------- */

el.filters.addEventListener('click', function (event) {
  const btn = event.target.closest('.filter');
  if (btn) setCategory(btn.dataset.category);
});

el.sortSelect.addEventListener('change', function () {
  state.sort = el.sortSelect.value;
  renderCatalog();
});

document.getElementById('checkoutBtn').addEventListener('click', openCheckout);
document.getElementById('promoForm').addEventListener('submit', handlePromoSubmit);

el.searchInput.addEventListener('input', function () {
  renderSearch(el.searchInput.value);
});
document.getElementById('searchForm').addEventListener('submit', function (event) {
  event.preventDefault();
  applySearchToCatalog();
});

checkoutForm.addEventListener('submit', handleCheckoutSubmit);
checkoutForm.addEventListener('change', function (event) {
  if (event.target.name === 'delivery') renderCheckoutSummary();
});
checkoutForm.addEventListener('input', function (event) {
  const field = event.target.closest('.field');
  if (field) field.classList.remove('has-error');
  if (event.target.id === 'coAgree') document.getElementById('agreeLabel').classList.remove('has-error');
});
document.getElementById('coPhone').addEventListener('input', function (event) {
  event.target.value = formatPhone(event.target.value);
});

// Подписка на рассылку
let lastSubscribeAt = 0;
document.getElementById('newsletterForm').addEventListener('submit', function (event) {
  event.preventDefault();
  if (event.target.elements.website.value) return;   // заполнил робот

  if (Date.now() - lastSubscribeAt < 5000) {
    showToast('Подождите несколько секунд');
    return;
  }
  const input = document.getElementById('newsletterEmail');
  const error = document.getElementById('newsletterError');

  if (!/^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/.test(input.value.trim())) {
    error.textContent = 'Введите корректный email';
    return;
  }
  error.textContent = '';
  input.value = '';
  lastSubscribeAt = Date.now();
  showToast('Вы подписаны на рассылку');
});


/* ---------- Поведение страницы ---------- */

// Шапка меняет фон при прокрутке, кнопка «наверх» появляется ниже первого экрана
let scrollTicking = false;
window.addEventListener('scroll', function () {
  if (scrollTicking) return;
  scrollTicking = true;
  requestAnimationFrame(function () {
    el.header.classList.toggle('is-scrolled', window.scrollY > 40);
    el.toTop.classList.toggle('is-visible', window.scrollY > 800);
    scrollTicking = false;
  });
}, { passive: true });

el.toTop.addEventListener('click', function () {
  window.scrollTo({ top: 0, behavior: 'smooth' });
});

// Плавное появление блоков
let revealObserver = null;
function observeReveal(root) {
  if (!('IntersectionObserver' in window)) {
    root.querySelectorAll('.reveal').forEach(function (node) { node.classList.add('is-visible'); });
    return;
  }
  if (!revealObserver) {
    revealObserver = new IntersectionObserver(function (entries) {
      let order = 0;
      entries.forEach(function (entry) {
        if (!entry.isIntersecting) return;
        const node = entry.target;
        revealObserver.unobserve(node);
        // небольшая задержка между соседними карточками
        setTimeout(function () { node.classList.add('is-visible'); }, order * 70);
        order++;
      });
    }, { threshold: 0.08, rootMargin: '0px 0px -25px 0px' });
  }
  root.querySelectorAll('.reveal:not(.is-visible)').forEach(function (node) {
    revealObserver.observe(node);
  });
}

// Подсветка пункта меню по разделу, который сейчас на экране
function initActiveNav() {
  const links = {};
  document.querySelectorAll('.nav__link').forEach(function (link) {
    links[link.getAttribute('href').slice(1)] = link;
  });

  const observer = new IntersectionObserver(function (entries) {
    entries.forEach(function (entry) {
      if (!entry.isIntersecting) return;
      Object.keys(links).forEach(function (id) { links[id].classList.remove('is-active'); });
      if (links[entry.target.id]) links[entry.target.id].classList.add('is-active');
    });
  }, { rootMargin: '-45% 0px -50% 0px' });

  ['about', 'catalog', 'lookbook', 'contacts'].forEach(function (id) {
    const section = document.getElementById(id);
    if (section) observer.observe(section);
  });
  const hero = document.querySelector('.hero');
  new IntersectionObserver(function (entries) {
    if (entries[0].isIntersecting) {
      Object.keys(links).forEach(function (id) { links[id].classList.remove('is-active'); });
    }
  }, { rootMargin: '-45% 0px -50% 0px' }).observe(hero);
}

// Картинки появляются, когда загрузились; если не загрузились — прячем «битую» иконку
document.addEventListener('load', function (event) {
  if (event.target.tagName === 'IMG') event.target.classList.add('is-loaded');
}, true);
document.addEventListener('error', function (event) {
  if (event.target.tagName === 'IMG') event.target.classList.add('is-loaded', 'is-broken');
}, true);

function checkStaticImages() {
  document.querySelectorAll('img.fade-img').forEach(function (img) {
    if (!img.complete) return;
    img.classList.add('is-loaded');
    if (img.naturalWidth === 0) img.classList.add('is-broken');
  });
}

function createSnow() {
  if (!window.matchMedia('(hover: hover) and (pointer: fine)').matches) return;

  const container = document.getElementById('snow');
  const symbols = ['❄', '❅', '❆', '·'];

  for (let i = 0; i < 20; i++) {
    const flake = document.createElement('span');
    flake.className = 'snowflake';
    flake.textContent = symbols[i % symbols.length];
    flake.style.left = Math.random() * 100 + '%';
    flake.style.fontSize = (Math.random() * 5 + 4) + 'px';
    flake.style.opacity = (Math.random() * 0.12 + 0.05).toFixed(2);
    flake.style.animationDuration = (Math.random() * 16 + 14) + 's';
    flake.style.animationDelay = (Math.random() * -20) + 's';
    container.appendChild(flake);
  }
}

function runPreloader() {
  const logo = document.getElementById('preloaderLogo');
  'NOIR HIVER'.split('').forEach(function (char, i) {
    const span = document.createElement('span');
    span.textContent = char;
    span.style.animationDelay = (i * 0.07) + 's';
    logo.appendChild(span);
  });

  setTimeout(function () {
    document.getElementById('preloader').classList.add('is-done');
    document.body.classList.remove('is-loading');
    document.body.classList.add('is-ready');
    observeReveal(document);
  }, 2000);
}


/* ---------- Запуск ---------- */

loadState();
renderCatalog();
updateCartUi();
updateWishlistUi();
checkStaticImages();
createSnow();
initActiveNav();
runPreloader();
</script>
</body>
</html>
[noir-hiver-single.html](https://github.com/user-attachments/files/34901586/noir-hiver-single.html)
