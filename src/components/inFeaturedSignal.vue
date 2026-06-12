<script setup>
import { featuredSignal } from '../data/inSocialLinks'
</script>

<template>
  <section class="featured-signal" aria-labelledby="featured-title">
    <div class="signal-card">
      <div class="signal-orbit" aria-hidden="true">
        <span />
      </div>

      <div class="signal-copy">
        <p>
          {{ featuredSignal.eyebrow }}
        </p>

        <h2 id="featured-title">
          {{ featuredSignal.title }}
        </h2>

        <span>
          {{ featuredSignal.body }}
        </span>
      </div>

      <a
        class="signal-action"
        :href="featuredSignal.actionHref"
      >
        {{ featuredSignal.actionLabel }}
      </a>
    </div>
  </section>
</template>

<style scoped lang="scss">
.featured-signal {
  position: relative;
  z-index: 2;
  width: var(--container);
  padding: 0 0 var(--space-16);
  margin: 0 auto;
}

.signal-card {
  position: relative;
  display: grid;
  align-items: center;
  gap: var(--space-6);
  grid-template-columns: auto minmax(0, 1fr) auto;
  padding: clamp(var(--space-5), 3vw, var(--space-8));
  overflow: hidden;
  border: 1px solid var(--color-border);
  border-radius: var(--radius-xl);
  background:
    radial-gradient(circle at 10% 20%, rgba(169, 140, 255, 0.16), transparent 18rem),
    linear-gradient(135deg, rgba(255, 255, 255, 0.074), rgba(255, 255, 255, 0.025)),
    rgba(8, 7, 20, 0.74);
  box-shadow: var(--shadow-soft);
  backdrop-filter: blur(22px);
}

.signal-card::before {
  position: absolute;
  inset: 0;
  background: linear-gradient(90deg, rgba(255, 255, 255, 0.09), transparent 28%, rgba(255, 255, 255, 0.04));
  opacity: 0.42;
  content: '';
}

.signal-card::after {
  position: absolute;
  inset: auto 1.75rem 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(216, 204, 255, 0.24), transparent);
  content: '';
}

.signal-orbit,
.signal-copy,
.signal-action {
  position: relative;
  z-index: 1;
}

.signal-orbit {
  display: grid;
  width: clamp(4.25rem, 8vw, 6rem);
  aspect-ratio: 1;
  place-items: center;
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 50%;
  background: radial-gradient(circle, rgba(216, 204, 255, 0.14), rgba(169, 140, 255, 0.06));
}

.signal-orbit::before,
.signal-orbit::after {
  position: absolute;
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: 50%;
  content: '';
}

.signal-orbit::before {
  inset: 0.85rem;
}

.signal-orbit::after {
  width: 112%;
  height: 32%;
  transform: rotate(-18deg);
}

.signal-orbit span {
  width: 0.72rem;
  aspect-ratio: 1;
  border-radius: 50%;
  background: var(--color-starlight);
  box-shadow: 0 0 24px rgba(216, 204, 255, 0.54);
}

.signal-copy {
  display: grid;
  gap: var(--space-2);
}

.signal-copy p {
  margin: 0;
  color: var(--color-lavender);
  font-size: 0.72rem;
  font-weight: 780;
  letter-spacing: 0.18em;
  text-transform: uppercase;
}

.signal-copy h2 {
  margin: 0;
  color: var(--color-starlight);
  font-size: clamp(1.6rem, 3.6vw, 2.8rem);
  letter-spacing: -0.06em;
  line-height: 1;
}

.signal-copy span {
  max-width: 58rem;
  color: var(--color-mist);
  font-size: 0.98rem;
  line-height: 1.7;
}

.signal-action {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.9rem 1.1rem;
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: var(--radius-pill);
  background: rgba(255, 255, 255, 0.06);
  color: var(--color-starlight);
  font-size: 0.75rem;
  font-weight: 780;
  letter-spacing: 0.13em;
  outline: none;
  text-transform: uppercase;
  white-space: nowrap;
  transition:
    border-color var(--duration-mid) var(--ease-soft),
    background var(--duration-mid) var(--ease-soft),
    transform var(--duration-mid) var(--ease-soft);
}

.signal-action:hover,
.signal-action:focus-visible {
  border-color: rgba(255, 255, 255, 0.28);
  background: rgba(255, 255, 255, 0.1);
  transform: translateY(-2px);
}

.signal-action:focus-visible {
  box-shadow: var(--shadow-focus);
}

@media (max-width: 820px) {
  .signal-card {
    justify-items: start;
    grid-template-columns: 1fr;
  }

  .signal-action {
    width: fit-content;
  }
}

@media (max-width: 560px) {
  .featured-signal {
    padding-bottom: var(--space-12);
  }

  .signal-card {
    justify-items: center;
    text-align: center;
  }
}
</style>
