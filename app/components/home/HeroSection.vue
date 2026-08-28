<script setup>
defineProps({
  revealed: {
    type: Boolean,
    default: false,
  },
});
</script>

<template>
  <section
    class="portfolio-work"
    :class="{ 'portfolio-work--revealed': revealed }"
    aria-labelledby="portfolio-title"
  >
    <h1 id="portfolio-title" class="portfolio-title">
      <span class="reveal-line"><span class="reveal-line__inner">Creative</span></span>
      <span class="reveal-line"><span class="reveal-line__inner">Developer</span></span>
    </h1>

    <img
      class="portfolio-portrait"
      src="/img/portfolio-graphic.jpg"
      alt="Portrait of Matthew Shaw"
    >
  </section>

  <section
    class="portfolio-footer"
    :class="{ 'portfolio-footer--revealed': revealed }"
    aria-label="About Matthew Shaw"
  >
    <a class="down-link" href="#about" aria-label="Continue to about Matthew Shaw">
      <span aria-hidden="true"></span>
    </a>

    <p class="portfolio-statement">
      I support designers<br>
      and clients with<br>
      creative development
    </p>

    <h2 class="portfolio-name">
      <span class="reveal-line"><span class="reveal-line__inner">Matthew</span></span>
      <span class="reveal-line"><span class="reveal-line__inner">Shaw</span></span>
    </h2>
  </section>
</template>

<style scoped>
.portfolio-work {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  column-gap: clamp(36px, 5vw, 84px);
}

.portfolio-title,
.portfolio-name {
  margin: 0;
  color: var(--portfolio-heading-colour);
  font-family: var(--portfolio-heading-font);
  font-weight: 400;
  letter-spacing: -0.075em;
  line-height: 0.86;
  text-transform: uppercase;
}

.portfolio-title {
  grid-column: 1 / 4;
  font-size: clamp(90px, 8.15vw, 132px);
}

.reveal-line,
.reveal-line__inner {
  display: block;
}

.reveal-line {
  overflow: hidden;
  margin-inline: -0.08em;
  padding-inline: 0.08em;
}

.reveal-line__inner {
  transform: translateY(112%);
  transition: transform 800ms cubic-bezier(0.22, 1, 0.36, 1);
  will-change: transform;
}

.portfolio-work--revealed .reveal-line__inner,
.portfolio-footer--revealed .reveal-line__inner {
  transform: translateY(0);
}

.portfolio-title .reveal-line:first-child .reveal-line__inner {
  transition-delay: 0ms;
}

.portfolio-title .reveal-line:nth-child(2) .reveal-line__inner {
  transition-delay: 100ms;
}

.portfolio-name .reveal-line:first-child .reveal-line__inner {
  transition-delay: 340ms;
}

.portfolio-name .reveal-line:nth-child(2) .reveal-line__inner {
  transition-delay: 440ms;
}

.portfolio-portrait {
  grid-column: 1 / 3;
  width: min(100%, 503px);
  aspect-ratio: 2.49 / 1;
  margin-top: 39px;
  display: block;
  object-fit: cover;
}

.portfolio-portrait,
.portfolio-statement,
.down-link {
  opacity: 0;
}

.portfolio-work--revealed .portfolio-portrait,
.portfolio-footer--revealed .portfolio-statement,
.portfolio-footer--revealed .down-link {
  animation: hero-fade-in 550ms cubic-bezier(0.22, 1, 0.36, 1) both;
}

.portfolio-work--revealed .portfolio-portrait {
  animation-delay: 260ms;
}

.portfolio-footer--revealed .portfolio-statement {
  animation-delay: 340ms;
}

.portfolio-footer--revealed .down-link {
  animation-delay: 410ms;
}

@keyframes hero-fade-in {
  to {
    opacity: 1;
  }
}

.portfolio-footer {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  grid-template-rows: 1fr auto;
  column-gap: clamp(36px, 5vw, 84px);
  align-items: end;
  min-height: 245px;
}

.down-link {
  grid-column: 1;
  grid-row: 2;
  width: 75px;
  height: 98px;
  position: relative;
  display: block;
  color: var(--portfolio-heading-colour);
}

.down-link::before {
  content: '';
  position: absolute;
  left: 35px;
  top: 0;
  width: 9px;
  height: 76px;
  background: currentColor;
}

.down-link span::before,
.down-link span::after {
  content: '';
  position: absolute;
  bottom: 13px;
  width: 47px;
  height: 9px;
  background: currentColor;
}

.down-link span::before {
  left: 1px;
  transform: rotate(45deg);
}

.down-link span::after {
  right: 1px;
  transform: rotate(-45deg);
}

.down-link:focus-visible {
  outline: 3px solid currentColor;
  outline-offset: 5px;
}

.portfolio-statement {
  grid-column: 2 / 3;
  grid-row: 2;
  align-self: end;
  margin: 0;
  color: var(--portfolio-text-colour);
  font-family: var(--portfolio-body-font);
  font-size: clamp(16px, 1.35vw, 21px);
  font-weight: 500;
  line-height: 1.08;
  text-transform: uppercase;
  white-space: nowrap;
}

.portfolio-name {
  grid-column: 3 / 5;
  grid-row: 1 / 3;
  align-self: end;
  justify-self: end;
  font-size: clamp(80px, 7.8vw, 126px);
  text-align: right;
}

@media (max-width: 1050px) and (min-width: 861px) {
  .portfolio-work,
  .portfolio-footer {
    column-gap: 28px;
  }

  .portfolio-statement {
    font-size: 13px;
  }

  .portfolio-name {
    font-size: clamp(64px, 7.8vw, 82px);
  }
}

@media (max-width: 860px) {
  .portfolio-work {
    display: block;
  }

  .portfolio-title {
    margin-top: clamp(38px, 8vw, 76px);
    font-size: clamp(44px, 13.3vw, 125px);
    line-height: 0.9;
  }

  .portfolio-portrait {
    width: 100%;
    aspect-ratio: 2.13 / 1;
    margin-top: clamp(20px, 3.8vw, 36px);
    border-radius: 4px;
  }

  .portfolio-footer {
    display: flex;
    min-height: 0;
    align-items: flex-start;
    flex-direction: column;
  }

  .portfolio-statement {
    order: 1;
    align-self: flex-start;
    margin-top: clamp(30px, 6vw, 57px);
    font-size: clamp(13px, 2.55vw, 24px);
    line-height: 1.16;
  }

  .down-link {
    order: 2;
    width: clamp(40px, 7.7vw, 73px);
    height: clamp(52px, 9.5vw, 92px);
    margin-top: clamp(20px, 4.5vw, 43px);
  }

  .down-link::before {
    left: calc(50% - clamp(3px, 0.45vw, 4px));
    width: clamp(6px, 0.9vw, 9px);
    height: 78%;
  }

  .down-link span::before,
  .down-link span::after {
    bottom: 10%;
    width: 62%;
    height: clamp(6px, 0.9vw, 9px);
  }

  .portfolio-name {
    order: 3;
    align-self: stretch;
    margin-top: clamp(20px, 5vw, 47px);
    font-size: clamp(44px, 13.3vw, 125px);
    line-height: 0.9;
    text-align: left;
  }
}

@media (max-width: 480px) {
  .portfolio-title {
    letter-spacing: -0.07em;
    transform: scaleX(0.85);
    transform-origin: left center;
    width: 117.65%;
  }
}

@media (prefers-reduced-motion: reduce) {
  .reveal-line__inner {
    transform: none;
    transition: none;
  }

  .portfolio-portrait,
  .portfolio-statement,
  .down-link {
    opacity: 1;
    animation: none;
  }
}
</style>
