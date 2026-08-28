<script setup>
import { onBeforeUnmount, onMounted, ref } from 'vue';

const emit = defineEmits(['complete']);

const MINIMUM_DURATION = 2000;
const REDUCED_MOTION_HOLD = 150;
const EXIT_DURATION = 620;
const RING_RADIUS = 54;
const RING_CIRCUMFERENCE = 2 * Math.PI * RING_RADIUS;

const progress = ref(0);
const leaving = ref(false);
const visible = ref(true);

let animationFrame;
let pageReadyHandler;
let active = true;
let scrollLocked = false;
let previousBodyOverflow = '';
let previousDocumentOverflow = '';
const timers = new Set();

const ringOffset = () => RING_CIRCUMFERENCE * (1 - progress.value / 99);

const delay = (duration) => new Promise((resolve) => {
  const timer = window.setTimeout(() => {
    timers.delete(timer);
    resolve();
  }, duration);

  timers.add(timer);
});

const lockPageScroll = () => {
  previousBodyOverflow = document.body.style.overflow;
  previousDocumentOverflow = document.documentElement.style.overflow;
  document.body.style.overflow = 'hidden';
  document.documentElement.style.overflow = 'hidden';
  scrollLocked = true;
};

const restorePageScroll = () => {
  if (!scrollLocked) return;

  document.body.style.overflow = previousBodyOverflow;
  document.documentElement.style.overflow = previousDocumentOverflow;
  scrollLocked = false;
};

const waitForPageReady = () => {
  if (document.readyState === 'complete') return Promise.resolve();

  return new Promise((resolve) => {
    pageReadyHandler = () => {
      pageReadyHandler = undefined;
      resolve();
    };

    window.addEventListener('load', pageReadyHandler, { once: true });
  });
};

const animateProgress = () => new Promise((resolve) => {
  const startedAt = performance.now();

  const update = (now) => {
    if (!active) return;

    const elapsed = now - startedAt;
    const position = Math.min(elapsed / MINIMUM_DURATION, 1);
    const easedPosition = 1 - Math.pow(1 - position, 3);

    progress.value = Math.floor(easedPosition * 99);

    if (position < 1) {
      animationFrame = window.requestAnimationFrame(update);
      return;
    }

    progress.value = 99;
    resolve();
  };

  animationFrame = window.requestAnimationFrame(update);
});

const dismiss = async (reducedMotion) => {
  if (!active) return;

  leaving.value = true;
  emit('complete');
  await delay(reducedMotion ? 0 : EXIT_DURATION);

  if (!active) return;

  visible.value = false;
  restorePageScroll();
};

onMounted(async () => {
  lockPageScroll();

  const reducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  const pageReady = waitForPageReady();

  if (reducedMotion) {
    progress.value = 99;
    await Promise.all([pageReady, delay(REDUCED_MOTION_HOLD)]);
  } else {
    await Promise.all([pageReady, animateProgress()]);
  }

  await dismiss(reducedMotion);
});

onBeforeUnmount(() => {
  active = false;
  window.cancelAnimationFrame(animationFrame);
  timers.forEach(timer => window.clearTimeout(timer));
  timers.clear();

  if (pageReadyHandler) window.removeEventListener('load', pageReadyHandler);

  restorePageScroll();
});
</script>

<template>
  <div
    v-if="visible"
    class="loading-overlay"
    :class="{ 'loading-overlay--leaving': leaving }"
    role="status"
    aria-live="polite"
    aria-label="Loading portfolio"
  >
    <div class="loading-indicator" aria-hidden="true">
      <svg class="loading-ring" viewBox="0 0 120 120">
        <circle class="loading-ring__track" cx="60" cy="60" :r="RING_RADIUS" />
        <circle
          class="loading-ring__progress"
          cx="60"
          cy="60"
          :r="RING_RADIUS"
          :style="{
            strokeDasharray: RING_CIRCUMFERENCE,
            strokeDashoffset: ringOffset(),
          }"
        />
      </svg>

      <span class="loading-percentage">{{ progress }}%</span>
    </div>
  </div>
</template>

<style scoped>
.loading-overlay {
  position: fixed;
  z-index: 1000;
  inset: 0;
  min-height: 100vh;
  min-height: 100dvh;
  display: grid;
  place-items: center;
  overflow: hidden;
  background: #e9e7e6;
  color: #050505;
  opacity: 1;
  transition: opacity 620ms cubic-bezier(0.22, 1, 0.36, 1);
}

.loading-overlay--leaving {
  opacity: 0;
}

.loading-indicator {
  width: clamp(104px, 9.5vw, 136px);
  aspect-ratio: 1;
  position: relative;
  display: grid;
  place-items: center;
  transform: scale(1);
  transition: transform 620ms cubic-bezier(0.22, 1, 0.36, 1),
    opacity 460ms ease;
}

.loading-overlay--leaving .loading-indicator {
  opacity: 0;
  transform: scale(0.96);
}

.loading-ring {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  overflow: visible;
  transform: rotate(-90deg);
}

.loading-ring__track,
.loading-ring__progress {
  fill: none;
  stroke-width: 0.85;
}

.loading-ring__track {
  stroke: rgba(5, 5, 5, 0.08);
}

.loading-ring__progress {
  stroke: rgba(5, 5, 5, 0.18);
  stroke-linecap: round;
  transition: stroke-dashoffset 90ms linear;
}

.loading-percentage {
  font-family: var(--portfolio-heading-font, Arial, Helvetica, sans-serif);
  font-size: clamp(15px, 1.3vw, 20px);
  font-weight: 400;
  letter-spacing: -0.055em;
  line-height: 1;
  font-variant-numeric: tabular-nums;
}

@media (max-width: 480px) {
  .loading-indicator {
    width: 100px;
  }
}

@media (prefers-reduced-motion: reduce) {
  .loading-overlay,
  .loading-indicator,
  .loading-ring__progress {
    transition: none;
  }
}
</style>
