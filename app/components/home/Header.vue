<script setup>
import { ref } from 'vue';

const menuOpen = ref(false);

const closeMenu = () => {
  menuOpen.value = false;
};
</script>

<template>
  <header class="portfolio-header">
    <a class="portfolio-brand" href="#top" @click="closeMenu">Matthew Shaw</a>

    <p class="portfolio-role">
      Front-End Developer<br>
      at LayeredTech
    </p>

    <p class="portfolio-location">
      Based in Bristol<br>
      United Kingdom
    </p>

    <nav class="desktop-navigation" aria-label="Portfolio navigation">
      <a href="#work">Work</a>,
      <a href="#about">About</a>,
      <a href="#contact">Contact</a>
    </nav>

    <button
      class="menu-button"
      type="button"
      aria-controls="mobile-navigation"
      :aria-expanded="menuOpen"
      @click="menuOpen = !menuOpen"
    >
      <span>MENU</span>
      <span class="menu-icon" aria-hidden="true">
        <span></span>
        <span></span>
        <span></span>
      </span>
    </button>

    <nav
      v-show="menuOpen"
      id="mobile-navigation"
      class="mobile-navigation"
      aria-label="Mobile portfolio navigation"
    >
      <a href="#work" @click="closeMenu">Work</a>
      <a href="#about" @click="closeMenu">About</a>
      <a href="#contact" @click="closeMenu">Contact</a>
    </nav>
  </header>
</template>

<style scoped>
.portfolio-header {
  position: relative;
  z-index: 10;
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  column-gap: clamp(36px, 5vw, 84px);
  align-items: start;
  min-height: 112px;
  color: var(--portfolio-text-colour);
  font-family: var(--portfolio-body-font);
  font-size: clamp(16px, 1.35vw, 22px);
  font-weight: 500;
  line-height: 1.05;
}

.portfolio-header p {
  margin: 0;
}

.portfolio-brand,
.desktop-navigation a,
.mobile-navigation a {
  color: inherit;
  text-decoration: none;
}

.portfolio-brand {
  width: max-content;
}

.portfolio-role {
  grid-column: 2;
}

.portfolio-location {
  grid-column: 3;
}

.desktop-navigation {
  grid-column: 4;
  justify-self: end;
  white-space: nowrap;
}

.portfolio-brand:hover,
.desktop-navigation a:hover,
.mobile-navigation a:hover {
  text-decoration: underline;
  text-underline-offset: 0.18em;
}

.portfolio-brand:focus-visible,
.desktop-navigation a:focus-visible,
.mobile-navigation a:focus-visible,
.menu-button:focus-visible {
  outline: 3px solid currentColor;
  outline-offset: 5px;
}

.menu-button,
.mobile-navigation {
  display: none;
}

@media (max-width: 1050px) and (min-width: 861px) {
  .portfolio-header {
    column-gap: 28px;
  }
}

@media (max-width: 860px) {
  .portfolio-header {
    display: grid;
    grid-template-columns: 1fr auto;
    min-height: 0;
    font-size: clamp(14px, 3vw, 28px);
    line-height: 1.12;
  }

  .portfolio-brand {
    grid-column: 1;
    grid-row: 1;
  }

  .portfolio-role,
  .portfolio-location {
    display: none;
  }

  .desktop-navigation {
    display: none;
  }

  .menu-button {
    grid-column: 2;
    grid-row: 1;
    display: flex;
    align-items: center;
    gap: clamp(12px, 2.2vw, 21px);
    margin: -6px 0 0;
    padding: 6px 0;
    border: 0;
    background: transparent;
    color: inherit;
    cursor: pointer;
    font-size: clamp(13px, 2.5vw, 24px);
    font-weight: 600;
  }

  .menu-icon {
    width: clamp(24px, 4vw, 38px);
    display: grid;
    gap: clamp(4px, 0.65vw, 6px);
  }

  .menu-icon span {
    width: 100%;
    height: clamp(2px, 0.36vw, 4px);
    display: block;
    background: currentColor;
    transition: transform 180ms ease, opacity 180ms ease;
  }

  .menu-button[aria-expanded='true'] .menu-icon span:first-child {
    transform: translateY(clamp(6px, 1vw, 10px)) rotate(45deg);
  }

  .menu-button[aria-expanded='true'] .menu-icon span:nth-child(2) {
    opacity: 0;
  }

  .menu-button[aria-expanded='true'] .menu-icon span:last-child {
    transform: translateY(clamp(-10px, -1vw, -6px)) rotate(-45deg);
  }

  .mobile-navigation {
    position: absolute;
    z-index: 2;
    top: clamp(36px, 6vw, 58px);
    right: 0;
    min-width: 130px;
    padding: 14px 18px;
    display: grid;
    gap: 8px;
    border: 2px solid currentColor;
    background: var(--portfolio-content-background);
    text-align: right;
  }
}

@media (prefers-reduced-motion: reduce) {
  .menu-icon span {
    transition: none;
  }
}
</style>
