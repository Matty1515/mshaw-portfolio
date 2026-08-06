<template>
  <section id="work" class="experience-section" aria-labelledby="experience-title">
    <h2 id="experience-title" class="experience-title">Experience</h2>

    <ol class="experience-list">
      <li class="experience-item">
        <span class="experience-marker" aria-hidden="true"></span>

        <p class="experience-date">2021 — Present</p>

        <article class="experience-details">
          <h3 class="experience-role">Senior Software Developer</h3>
          <p class="experience-company">Vantage Cloud</p>
          <p class="experience-description">
            At Vantage Cloud, I continuously work with customers to ensure the platform fulfills their individual needs. This could be a new module or adapting existing features to match the customer existing business processes. I will also work with many different 3rd party API's to ensure various data sets are synced with the Vantage Cloud platform.
          </p>
        </article>
      </li>

      <li class="experience-item">
        <span class="experience-marker" aria-hidden="true"></span>

        <p class="experience-date">2018 — 2021</p>

        <article class="experience-details">
          <h3 class="experience-role">Backend Developer</h3>
          <p class="experience-company">Somerset Design</p>
          <p class="experience-description">
            In my role at Somerset Design I was the lead on various projects including a sponsorship auction platform and a considerable system that handles inventory among many other tasks. I was responsible for teaching and assisting colleagues in learning the Laravel framework. Another duty I had was maintaining and updating legacy sites.
          </p>
        </article>
      </li>

      <li class="experience-item">
        <span class="experience-marker" aria-hidden="true"></span>

        <p class="experience-date">2017 — 2018</p>

        <article class="experience-details">
          <h3 class="experience-role">PHP Developer</h3>
          <p class="experience-company">BNS Property Management</p>
          <p class="experience-description">
            During my time at BNS my primary role was working on the MyBNS platform here landlords and tenants can log to help eliminate the difficulties in renting. MyBNS also allows the company to undertake many more clients making them a leader in the property management industry.
          </p>
        </article>
      </li>
    </ol>
  </section>
</template>

<style scoped>
.experience-section {
  min-height: 100vh;
  min-height: 100svh;
  padding: clamp(72px, 8vw, 118px) 0 clamp(54px, 6vw, 90px);
  scroll-margin-top: 32px;
  color: var(--portfolio-text-colour);
  font-family: var(--portfolio-body-font);
}

.experience-title {
  margin: 0;
  color: var(--portfolio-heading-colour);
  font-family: var(--portfolio-heading-font);
  font-size: clamp(88px, 9.4vw, 146px);
  font-weight: 400;
  letter-spacing: -0.075em;
  line-height: 0.86;
  text-transform: uppercase;
}

.experience-list {
  margin: clamp(58px, 6vw, 92px) 0 0;
  padding: 0;
  position: relative;
  list-style: none;
}

.experience-list::before {
  content: '';
  width: 2px;
  position: absolute;
  top: 11px;
  bottom: 11px;
  left: 10px;
  background: currentColor;
}

.experience-item {
  position: relative;
  display: grid;
  grid-template-columns: 22px minmax(210px, 240px) minmax(0, 1fr);
  column-gap: clamp(32px, 4.4vw, 70px);
  align-items: start;
}

.experience-item:not(:last-child) {
  margin-bottom: clamp(38px, 4vw, 60px);
}

.experience-marker {
  width: 22px;
  aspect-ratio: 1;
  position: relative;
  z-index: 1;
  display: block;
  border-radius: 50%;
  background: currentColor;
}

.experience-date,
.experience-company,
.experience-description {
  margin: 0;
}

.experience-date,
.experience-role,
.experience-company {
  font-size: clamp(20px, 1.85vw, 29px);
  font-weight: 500;
  line-height: 1.08;
}

.experience-date {
  white-space: nowrap;
}

.experience-role {
  margin: 0;
}

.experience-description {
  max-width: 790px;
  margin-top: clamp(14px, 1.4vw, 22px);
  font-size: clamp(16px, 1.35vw, 21px);
  font-weight: 400;
  line-height: 1.31;
}

@media (max-width: 1050px) and (min-width: 861px) {
  .experience-item {
    grid-template-columns: 22px minmax(165px, 190px) minmax(0, 1fr);
    column-gap: 28px;
  }

  .experience-date,
  .experience-role,
  .experience-company {
    font-size: 20px;
  }

  .experience-description {
    font-size: 15px;
  }
}

@media (max-width: 860px) {
  .experience-section {
    min-height: 0;
    padding: clamp(90px, 18vw, 150px) 0 clamp(62px, 13vw, 110px);
    scroll-margin-top: 0;
  }

  .experience-title {
    font-size: clamp(48px, 14vw, 112px);
    line-height: 0.9;
  }

  .experience-list {
    margin-top: clamp(48px, 10vw, 78px);
  }

  .experience-list::before {
    top: 9px;
    bottom: 9px;
    left: 7px;
    width: 1px;
  }

  .experience-item {
    grid-template-columns: 15px minmax(0, 1fr);
    grid-template-rows: auto auto;
    column-gap: clamp(18px, 4.5vw, 34px);
    row-gap: clamp(14px, 3vw, 22px);
  }

  .experience-item:not(:last-child) {
    margin-bottom: clamp(46px, 10vw, 76px);
  }

  .experience-marker {
    width: 15px;
    grid-column: 1;
    grid-row: 1 / 3;
  }

  .experience-date,
  .experience-details {
    grid-column: 2;
  }

  .experience-date {
    grid-row: 1;
  }

  .experience-details {
    grid-row: 2;
  }

  .experience-date,
  .experience-role,
  .experience-company {
    font-size: clamp(18px, 4.5vw, 28px);
  }

  .experience-description {
    max-width: 650px;
    margin-top: clamp(14px, 3vw, 20px);
    font-size: clamp(14px, 3.4vw, 20px);
    line-height: 1.42;
  }
}

@media (max-width: 480px) {
  .experience-title {
    letter-spacing: -0.07em;
    transform: scaleX(0.85);
    transform-origin: left center;
    width: 117.65%;
  }
}
</style>
