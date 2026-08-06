<script setup>
const canFollowPointer = () => (
  window.matchMedia('(hover: hover) and (pointer: fine)').matches
  && !window.matchMedia('(prefers-reduced-motion: reduce)').matches
);

const followPointer = (event) => {
  if (!canFollowPointer()) return;

  const image = event.currentTarget;
  const bounds = image.getBoundingClientRect();
  const x = ((event.clientX - bounds.left) / bounds.width - 0.5) * 12;
  const y = ((event.clientY - bounds.top) / bounds.height - 0.5) * 12;

  image.style.setProperty('--pointer-x', `${x}px`);
  image.style.setProperty('--pointer-y', `${y}px`);
};

const resetPointer = (event) => {
  event.currentTarget.style.setProperty('--pointer-x', '0px');
  event.currentTarget.style.setProperty('--pointer-y', '0px');
};
</script>

<template>
  <section id="about" class="about-section" aria-labelledby="about-title">
    <h2 id="about-title" class="visually-hidden">About Matthew Shaw</h2>

    <div class="floating-image floating-image-one" aria-hidden="true">
      <img
        src="/img/portfolio-graphic.jpg"
        alt=""
        @pointermove="followPointer"
        @pointerleave="resetPointer"
      >
    </div>

    <div class="floating-image floating-image-two" aria-hidden="true">
      <img
        src="/img/portfolio-graphic.jpg"
        alt=""
        @pointermove="followPointer"
        @pointerleave="resetPointer"
      >
    </div>

    <div class="floating-image floating-image-three" aria-hidden="true">
      <img
        src="/img/portfolio-graphic.jpg"
        alt=""
        @pointermove="followPointer"
        @pointerleave="resetPointer"
      >
    </div>

    <div class="floating-image floating-image-four" aria-hidden="true">
      <img
        src="/img/portfolio-graphic.jpg"
        alt=""
        @pointermove="followPointer"
        @pointerleave="resetPointer"
      >
    </div>

    <p class="about-copy">
      I’m a creative web developer focused on building clean, accessible, high-performance digital experiences. I enjoy turning thoughtful design into smooth, modern products with strong front-end craft and dependable back-end foundations.
    </p>
  </section>
</template>

<style scoped>
.about-section {
  position: relative;
  min-height: clamp(520px, 44vw, 620px);
  margin-top: clamp(150px, 16vw, 240px);
  display: grid;
  place-items: center;
  padding: clamp(110px, 11vw, 150px) clamp(90px, 11vw, 160px);
  isolation: isolate;
}

.about-copy {
  width: min(100%, 760px);
  margin: 0;
  position: relative;
  z-index: 1;
  color: var(--portfolio-text-colour);
  font-family: var(--portfolio-body-font);
  font-size: clamp(28px, 2.55vw, 40px);
  font-weight: 500;
  letter-spacing: -0.035em;
  line-height: 1.38;
  text-align: center;
}

.floating-image {
  --drift-x: 16px;
  --drift-y: -18px;
  --return-x: -9px;
  --return-y: -7px;
  width: clamp(66px, 6vw, 88px);
  aspect-ratio: 1 / 1;
  position: absolute;
  z-index: 0;
  animation: ambient-drift 16s ease-in-out infinite;
  will-change: transform;
}

.floating-image img {
  --pointer-x: 0px;
  --pointer-y: 0px;
  width: 100%;
  height: 100%;
  display: block;
  object-fit: cover;
  transform: translate3d(var(--pointer-x), var(--pointer-y), 0);
  transition: transform 700ms cubic-bezier(0.22, 1, 0.36, 1);
  will-change: transform;
}

.floating-image-one {
  top: 4%;
  left: 2.5%;
  --drift-x: 17px;
  --drift-y: 19px;
  --return-x: -9px;
  --return-y: 8px;
  animation-duration: 17s;
  animation-delay: -6s;
}

.floating-image-two {
  top: 4%;
  right: 7%;
  --drift-x: -19px;
  --drift-y: 15px;
  --return-x: 10px;
  --return-y: 6px;
  animation-duration: 19s;
  animation-delay: -13s;
}

.floating-image-three {
  top: 56%;
  left: 0;
  --drift-x: 20px;
  --drift-y: -17px;
  --return-x: -11px;
  --return-y: -7px;
  animation-duration: 18s;
  animation-delay: -9s;
}

.floating-image-four {
  right: 11%;
  bottom: 1%;
  --drift-x: -16px;
  --drift-y: -20px;
  --return-x: 9px;
  --return-y: -8px;
  animation-duration: 16s;
  animation-delay: -3s;
}

.visually-hidden {
  width: 1px;
  height: 1px;
  padding: 0;
  position: absolute;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

@keyframes ambient-drift {
  0%,
  100% {
    transform: translate3d(0, 0, 0) rotate(-0.4deg);
  }

  34% {
    transform: translate3d(var(--drift-x), var(--drift-y), 0) rotate(0.4deg);
  }

  68% {
    transform: translate3d(var(--return-x), var(--return-y), 0) rotate(-0.2deg);
  }
}

@media (max-width: 860px) {
  .about-section {
    min-height: clamp(500px, 82svh, 680px);
    margin-top: clamp(110px, 20vw, 170px);
    padding: clamp(105px, 19vw, 155px) clamp(18px, 5vw, 42px);
  }

  .about-copy {
    width: min(100%, 620px);
    font-size: clamp(22px, 4.4vw, 34px);
    line-height: 1.42;
  }

  .floating-image {
    width: clamp(54px, 11vw, 76px);
  }

  .floating-image-one {
    top: 5%;
    left: 1%;
  }

  .floating-image-four {
    right: 2%;
    bottom: 4%;
  }

  .floating-image-two,
  .floating-image-three {
    display: none;
  }
}

@media (hover: none), (pointer: coarse) {
  .floating-image img {
    pointer-events: none;
  }
}

@media (prefers-reduced-motion: reduce) {
  .floating-image {
    animation: none;
  }

  .floating-image img {
    transform: none;
    transition: none;
  }
}
</style>
