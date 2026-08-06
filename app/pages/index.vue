<script setup>
import { nextTick, onBeforeUnmount, onMounted, ref } from 'vue';

const darkThemeActive = ref(false);
let workObserver;

onMounted(async () => {
  await nextTick();

  const workSection = document.getElementById('work');

  if (!workSection || !('IntersectionObserver' in window)) return;

  workObserver = new IntersectionObserver(([entry]) => {
    darkThemeActive.value = entry.isIntersecting || entry.boundingClientRect.top < 0;
  }, {
    rootMargin: '0px 0px -25% 0px',
    threshold: 0,
  });

  workObserver.observe(workSection);
});

onBeforeUnmount(() => {
  workObserver?.disconnect();
});
</script>

<template>
  <main
    class="portfolio-page"
    :class="{ 'portfolio-page--dark': darkThemeActive }"
  >
    <article class="portfolio-card">
      <HomeHeader />
      <HomeHeroSection />
      <HomeAboutSection />
      <HomeExperienceSection />
    </article>
  </main>
</template>

<style scoped>
:global(:root) {
  --portfolio-page-background: #202226;
  --portfolio-content-background: #e9e7e6;
  --portfolio-heading-colour: #050505;
  --portfolio-text-colour: #050505;
  --portfolio-heading-font: Arial, Helvetica, sans-serif;
  --portfolio-body-font: 'DM Sans', Arial, sans-serif;
}

:global(*) {
  box-sizing: border-box;
}

:global(html) {
  scroll-behavior: smooth;
}

:global(body) {
  margin: 0;
  background: var(--portfolio-page-background);
}

:global(button),
:global(a) {
  font: inherit;
}

.portfolio-page {
  min-height: 100vh;
  min-height: 100svh;
  display: grid;
  place-items: center;
  /* padding: clamp(72px, 12vh, 144px) clamp(58px, 7.25vw, 116px); */
  overflow: clip;
  background: var(--portfolio-page-background);
  color: var(--portfolio-text-colour);
  font-family: var(--portfolio-body-font);
}

.portfolio-page--dark {
  --portfolio-page-background: #050505;
  --portfolio-content-background: #050505;
  --portfolio-heading-colour: #f5f5f2;
  --portfolio-text-colour: #f5f5f2;
}

.portfolio-card {
  width: min(100%, 1368px);
  min-height: min(912px, 76vh);
  padding: 36px 64px 45px;
  display: grid;
  grid-template-rows: auto auto 1fr;
  background: var(--portfolio-content-background);
}

.portfolio-page,
.portfolio-card,
:deep(.portfolio-header),
:deep(.mobile-navigation),
:deep(.portfolio-title),
:deep(.portfolio-name),
:deep(.down-link),
:deep(.portfolio-statement),
:deep(.about-copy),
:deep(.experience-section),
:deep(.experience-title) {
  transition: background-color 680ms cubic-bezier(0.22, 1, 0.36, 1),
    color 680ms cubic-bezier(0.22, 1, 0.36, 1),
    border-color 680ms cubic-bezier(0.22, 1, 0.36, 1);
}

@media (max-width: 1050px) and (min-width: 861px) {
  .portfolio-page {
    /* padding-inline: 5vw; */
  }

  .portfolio-card {
    padding-inline: 45px;
  }
}

@media (max-width: 860px) {
  .portfolio-page {
    display: block;
    /* padding: clamp(28px, 5.8vw, 56px) clamp(24px, 9.8vw, 92px); */
  }

  .portfolio-card {
    width: 100%;
    min-height: calc(100svh - clamp(56px, 11.6vw, 112px));
    padding: clamp(22px, 5vw, 48px) clamp(18px, 4vw, 38px) clamp(22px, 4.8vw, 46px);
    display: block;
    /* border-radius: clamp(28px, 5vw, 48px); */
  }
}

@media (max-width: 480px) {
  .portfolio-page {
    /* padding-block: 24px; */
    /* padding-inline: 9vw; */
  }

  .portfolio-card {
    padding: 22px 17px 4px;
  }
}

@media (prefers-reduced-motion: reduce) {
  :global(html) {
    scroll-behavior: auto;
  }

  .portfolio-page,
  .portfolio-card,
  :deep(.portfolio-header),
  :deep(.mobile-navigation),
  :deep(.portfolio-title),
  :deep(.portfolio-name),
  :deep(.down-link),
  :deep(.portfolio-statement),
  :deep(.about-copy),
  :deep(.experience-section),
  :deep(.experience-title) {
    transition: none;
  }
}
</style>
