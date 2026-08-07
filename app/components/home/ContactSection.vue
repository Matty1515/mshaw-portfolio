<template>
  <section id="contact" class="contact-section" aria-labelledby="contact-title">
    <h2 id="contact-title" class="contact-title">
      <span>Get in</span>
      <span>Touch</span>
    </h2>

    <div class="contact-copy">
      <p>
        I&rsquo;m a creative developer who enjoys turning ideas into clean, fast, thoughtful digital experiences. I care about sharp design, smooth interactions, and building products that feel as good as they work.
      </p>

      <p>
        If you&rsquo;ve got a project, idea, or opportunity, let&rsquo;s make something brilliant together.
      </p>
    </div>

    <img
      class="contact-image"
      src="/img/portfolio-graphic.jpg"
      alt=""
    >

    <nav class="contact-links" aria-label="Contact links">
      <ul>
        <li>
          <a
            class="contact-link"
            href="https://github.com/Matty1515"
            target="_blank"
            rel="noopener noreferrer"
          >
            <span class="contact-link-arrow" aria-hidden="true">&nearr;</span>
            <span>GitHub</span>
          </a>
        </li>

        <li>
          <a
            class="contact-link"
            href="https://codepen.io/Matty1515/"
            target="_blank"
            rel="noopener noreferrer"
          >
            <span class="contact-link-arrow" aria-hidden="true">&nearr;</span>
            <span>CodePen</span>
          </a>
        </li>

        <li>
          <a class="contact-link" href="mailto:imhullu15@gmail.com">
            <span class="contact-link-arrow" aria-hidden="true">&nearr;</span>
            <span>Email Me</span>
          </a>
        </li>
      </ul>
    </nav>
  </section>
</template>

<style scoped>
.contact-section {
  min-height: 0;
  padding: clamp(68px, 5.6vw, 78px) 0 clamp(24px, 2.6vw, 40px);
  display: grid;
  grid-template-columns: minmax(0, 1.02fr) minmax(430px, 0.98fr);
  grid-template-rows: auto auto;
  column-gap: clamp(64px, 7vw, 108px);
  row-gap: clamp(28px, 3vw, 44px);
  scroll-margin-top: 0;
  color: var(--portfolio-text-colour);
  font-family: var(--portfolio-body-font);
}

.contact-title {
  grid-column: 1;
  grid-row: 1;
  margin: 0;
  color: var(--portfolio-heading-colour);
  font-family: var(--portfolio-heading-font);
  font-weight: 400;
  font-size: clamp(96px, 10.7vw, 150px);
  letter-spacing: -0.075em;
  line-height: 0.84;
  text-transform: uppercase;
}

.contact-title span {
  display: block;
}

.contact-copy {
  grid-column: 1;
  grid-row: 2;
  align-self: end;
  max-width: 520px;
  margin: 0;
  font-size: clamp(17px, 1.6vw, 23px);
  font-weight: 500;
  letter-spacing: -0.025em;
  line-height: 1.32;
}

.contact-copy p {
  margin: 0;
}

.contact-copy p + p {
  margin-top: clamp(22px, 2.2vw, 34px);
}

.contact-image {
  width: 100%;
  max-height: 200px;
  aspect-ratio: 1.86 / 1;
  grid-column: 2;
  grid-row: 1;
  align-self: start;
  margin-top: clamp(12px, 1.4vw, 22px);
  display: block;
  object-fit: cover;
  object-position: 50% 54%;
  filter: grayscale(1) contrast(1.12) brightness(0.72);
}

.contact-links {
  grid-column: 2;
  grid-row: 2;
  align-self: end;
  margin: 0;
}

.contact-links ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

.contact-links li:not(:last-child) {
  border-bottom: 1px solid currentColor;
}

.contact-link {
  min-height: clamp(48px, 4.2vw, 60px);
  display: grid;
  grid-template-columns: clamp(38px, 4vw, 56px) minmax(0, 1fr);
  column-gap: clamp(18px, 2vw, 30px);
  align-items: center;
  color: inherit;
  font-size: clamp(18px, 1.65vw, 24px);
  font-weight: 500;
  text-decoration: none;
}

.contact-link-arrow {
  display: inline-block;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1.7em;
  font-weight: 400;
  line-height: 1;
  transition: transform 220ms cubic-bezier(0.22, 1, 0.36, 1);
}

.contact-link:hover .contact-link-arrow {
  transform: translate3d(4px, -4px, 0);
}

.contact-link:focus-visible {
  outline: 3px solid currentColor;
  outline-offset: 4px;
}

@media (max-width: 1050px) and (min-width: 861px) {
  .contact-section {
    grid-template-columns: minmax(0, 0.9fr) minmax(350px, 1.1fr);
    column-gap: 40px;
  }

  .contact-copy {
    font-size: 16px;
  }

  .contact-link {
    grid-template-columns: 38px minmax(0, 1fr);
    column-gap: 12px;
    font-size: 17px;
  }
}

@media (max-width: 860px) {
  .contact-section {
    min-height: 0;
    padding: clamp(90px, 18vw, 150px) 0 clamp(62px, 13vw, 110px);
    display: block;
    scroll-margin-top: 0;
  }

  .contact-title {
    font-size: clamp(58px, 16vw, 112px);
    line-height: 0.86;
  }

  .contact-copy {
    max-width: 650px;
    margin-top: clamp(38px, 8vw, 62px);
    font-size: clamp(17px, 3.5vw, 23px);
    line-height: 1.4;
  }

  .contact-image {
    display: none;
  }

  .contact-links {
    width: min(100%, 650px);
    margin-top: clamp(46px, 10vw, 78px);
  }

  .contact-link {
    min-height: clamp(56px, 11vw, 76px);
    grid-template-columns: clamp(40px, 8vw, 58px) minmax(0, 1fr);
    column-gap: clamp(14px, 4vw, 30px);
    font-size: clamp(18px, 4vw, 25px);
  }
}

@media (max-width: 480px) {
  .contact-title {
    letter-spacing: -0.07em;
  }
}

@media (prefers-reduced-motion: reduce) {
  .contact-link-arrow {
    transition: none;
  }

  .contact-link:hover .contact-link-arrow {
    transform: none;
  }
}
</style>
