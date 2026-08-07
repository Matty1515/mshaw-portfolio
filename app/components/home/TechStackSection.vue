<script setup>
const frontEndSkills = [
  'HTML5',
  'CSS3',
  'Sass',
  'Tailwind CSS',
  'JavaScript',
  'TypeScript',
  'Vue 3',
  'Nuxt',
  'Vite',
  'Pinia',
  'Responsiveness',
  'Accessibility',
];

const backEndSkills = [
  'PHP',
  'Laravel',
  'REST APIs',
  'MySQL',
  'Node.js',
  'Git',
  'Docker',
  'CI/CD',
];
</script>

<template>
  <section class="tech-stack-section" aria-labelledby="tech-stack-title">
    <h2 id="tech-stack-title" class="tech-stack-title">Tech Stack</h2>

    <div class="tech-stack-layout">
      <div class="tech-stack-visual">
        <img
          class="tech-stack-image"
          src="/img/portfolio-graphic.jpg"
          alt=""
        >

        <div class="tech-stack-signoff">
          <span class="tech-stack-arrow" aria-hidden="true"></span>

          <p class="tech-stack-statement">
            Modern tools.<br>
            Clean code.<br>
            Meaningful impact.
          </p>
        </div>
      </div>

      <div class="tech-stack-groups">
        <section class="tech-stack-group" aria-labelledby="front-end-title">
          <h3 id="front-end-title" class="tech-stack-category">Front-End</h3>

          <ol class="tech-stack-list tech-stack-list--front-end">
            <li v-for="skill in frontEndSkills" :key="skill">{{ skill }}</li>
          </ol>
        </section>

        <section class="tech-stack-group" aria-labelledby="back-end-title">
          <h3 id="back-end-title" class="tech-stack-category">Back-End</h3>

          <ol class="tech-stack-list tech-stack-list--back-end">
            <li v-for="skill in backEndSkills" :key="skill">{{ skill }}</li>
          </ol>
        </section>
      </div>
    </div>
  </section>
</template>

<style scoped>
.tech-stack-section {
  min-height: 100vh;
  min-height: 100svh;
  padding: clamp(64px, 6vw, 92px) 0 clamp(54px, 6vw, 90px);
  color: var(--portfolio-text-colour);
  font-family: var(--portfolio-body-font);
}

.tech-stack-title {
  margin: 0;
  color: var(--portfolio-heading-colour);
  font-family: var(--portfolio-heading-font);
  font-size: clamp(96px, 11vw, 160px);
  font-weight: 400;
  letter-spacing: -0.075em;
  line-height: 0.86;
  text-transform: uppercase;
}

.tech-stack-layout {
  margin-top: clamp(50px, 4.5vw, 70px);
  display: grid;
  grid-template-columns: minmax(300px, 0.82fr) minmax(0, 1.42fr);
  column-gap: clamp(44px, 5.5vw, 86px);
}

.tech-stack-visual {
  min-width: 0;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.tech-stack-image {
  width: 100%;
  aspect-ratio: 1.77 / 1;
  display: block;
  object-fit: cover;
  object-position: 50% 45%;
  filter: grayscale(1) contrast(1.3) brightness(0.46);
}

.tech-stack-signoff {
  min-height: clamp(170px, 15vw, 230px);
  display: flex;
  align-items: flex-end;
  gap: clamp(54px, 7.5vw, 118px);
}

.tech-stack-arrow {
  width: 70px;
  height: 92px;
  position: relative;
  flex: 0 0 auto;
  display: block;
  color: inherit;
}

.tech-stack-arrow::before {
  content: '';
  width: 8px;
  height: 76px;
  position: absolute;
  top: 0;
  left: 31px;
  background: currentColor;
}

.tech-stack-arrow::after {
  content: '';
  width: 43px;
  height: 43px;
  position: absolute;
  right: 4px;
  bottom: 4px;
  border-right: 8px solid currentColor;
  border-bottom: 8px solid currentColor;
  transform: rotate(45deg);
}

.tech-stack-statement {
  margin: 0 0 3px;
  font-size: clamp(15px, 1.22vw, 19px);
  font-weight: 500;
  line-height: 1.08;
  text-transform: uppercase;
}

.tech-stack-groups {
  display: grid;
  align-content: start;
  gap: clamp(54px, 5vw, 78px);
}

.tech-stack-category {
  margin: 0;
  display: grid;
  grid-template-columns: auto minmax(32px, 1fr);
  gap: clamp(28px, 3vw, 46px);
  align-items: center;
  color: inherit;
  font-size: clamp(28px, 2.5vw, 36px);
  font-weight: 500;
  letter-spacing: -0.035em;
  line-height: 1;
  text-transform: uppercase;
}

.tech-stack-category::after {
  content: '';
  height: 1px;
  display: block;
  background: currentColor;
}

.tech-stack-list {
  margin: clamp(26px, 2.3vw, 36px) 0 0;
  padding: 0;
  display: grid;
  grid-auto-flow: column;
  column-gap: clamp(26px, 3vw, 48px);
  row-gap: clamp(20px, 1.9vw, 29px);
  list-style: none;
  counter-reset: tech-skill;
}

.tech-stack-list--front-end {
  grid-template-columns: repeat(3, minmax(0, 1fr));
  grid-template-rows: repeat(4, auto);
}

.tech-stack-list--back-end {
  width: 67%;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  grid-template-rows: repeat(4, auto);
}

.tech-stack-list li {
  min-width: 0;
  display: grid;
  grid-template-columns: 35px minmax(0, 1fr);
  column-gap: clamp(10px, 1vw, 16px);
  align-items: baseline;
  font-size: clamp(16px, 1.35vw, 20px);
  font-weight: 500;
  line-height: 1.08;
  counter-increment: tech-skill;
}

.tech-stack-list li::before {
  content: counter(tech-skill, decimal-leading-zero);
  font-size: 0.76em;
  font-variant-numeric: tabular-nums;
}

@media (max-width: 1050px) and (min-width: 861px) {
  .tech-stack-layout {
    grid-template-columns: minmax(245px, 0.7fr) minmax(0, 1.3fr);
    column-gap: 38px;
  }

  .tech-stack-signoff {
    gap: 36px;
  }

  .tech-stack-arrow {
    transform: scale(0.8);
    transform-origin: left bottom;
  }

  .tech-stack-list {
    column-gap: 20px;
  }

  .tech-stack-list li {
    grid-template-columns: 24px minmax(0, 1fr);
    column-gap: 5px;
    font-size: 14px;
    white-space: nowrap;
  }
}

@media (max-width: 860px) {
  .tech-stack-section {
    min-height: 0;
    padding: clamp(90px, 18vw, 150px) 0 clamp(62px, 13vw, 110px);
  }

  .tech-stack-title {
    font-size: clamp(48px, 14vw, 112px);
    line-height: 0.9;
  }

  .tech-stack-layout {
    margin-top: clamp(48px, 10vw, 78px);
    display: flex;
    flex-direction: column;
  }

  .tech-stack-visual {
    display: contents;
  }

  .tech-stack-image {
    width: min(100%, 620px);
    aspect-ratio: 1.9 / 1;
    order: 1;
  }

  .tech-stack-groups {
    order: 2;
    margin-top: clamp(52px, 11vw, 84px);
    gap: clamp(52px, 11vw, 84px);
  }

  .tech-stack-signoff {
    min-height: 0;
    order: 3;
    margin-top: clamp(70px, 15vw, 118px);
    align-items: flex-end;
    gap: clamp(45px, 12vw, 92px);
  }

  .tech-stack-category {
    gap: clamp(20px, 5vw, 40px);
    font-size: clamp(23px, 5vw, 34px);
  }

  .tech-stack-list {
    margin-top: clamp(25px, 5.5vw, 40px);
    grid-template-columns: repeat(2, minmax(0, 1fr));
    column-gap: clamp(28px, 8vw, 68px);
    row-gap: clamp(18px, 4vw, 28px);
  }

  .tech-stack-list--front-end {
    grid-template-rows: repeat(6, auto);
  }

  .tech-stack-list--back-end {
    width: 100%;
    grid-template-rows: repeat(4, auto);
  }

  .tech-stack-list li {
    grid-template-columns: clamp(29px, 5vw, 38px) minmax(0, 1fr);
    font-size: clamp(15px, 3.5vw, 22px);
  }

  .tech-stack-statement {
    font-size: clamp(14px, 3vw, 19px);
  }
}

@media (max-width: 480px) {
  .tech-stack-title {
    letter-spacing: -0.07em;
    transform: scaleX(0.85);
    transform-origin: left center;
    width: 117.65%;
  }

  .tech-stack-list {
    grid-auto-flow: row;
    grid-template-columns: minmax(0, 1fr);
    grid-template-rows: none;
  }

  .tech-stack-signoff {
    justify-content: space-between;
    gap: 24px;
  }

  .tech-stack-arrow {
    transform: scale(0.75);
    transform-origin: left bottom;
  }
}
</style>
