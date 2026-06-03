<script setup>
defineProps({
  platform: {
    type: Object,
    required: true,
  },
})
</script>

<template>
  <aside
    class="platform-panel"
    :style="{ '--panel-accent': platform.accent }"
    aria-live="polite"
  >
    <div class="panel-orb" aria-hidden="true">
      <img
        :src="platform.icon"
        alt=""
      >
    </div>

    <div class="panel-copy">
      <p class="panel-eyebrow">
        {{ platform.signal }}
      </p>

      <h2>
        {{ platform.name }}
      </h2>

      <p>
        {{ platform.description }}
      </p>
    </div>

    <a
      class="panel-action"
      :href="platform.url"
      target="_blank"
      rel="noreferrer noopener"
    >
      Visit {{ platform.name }}

      <span aria-hidden="true">
        ↗
      </span>
    </a>
  </aside>
</template>

<style scoped lang="scss">
.platform-panel {
  position: relative;
  display: grid;
  align-items: center;
  gap: var(--space-5);
  grid-template-columns: auto minmax(0, 1fr) auto;
  width: min(780px, 100%);
  min-height: 9.15rem;
  padding: var(--space-5);
  overflow: hidden;
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  background:
    radial-gradient(circle at 16% 20%, color-mix(in srgb, var(--panel-accent) 22%, transparent), transparent 14rem),
    linear-gradient(150deg, rgba(255, 255, 255, 0.086), rgba(255, 255, 255, 0.025)),
    var(--color-panel);
  box-shadow: var(--shadow-soft);
  backdrop-filter: blur(24px);
}

.platform-panel::before {
  position: absolute;
  inset: 0;
  border-radius: inherit;
  background: linear-gradient(120deg, rgba(255, 255, 255, 0.14), transparent 32%, rgba(255, 255, 255, 0.05));
  opacity: 0.46;
  pointer-events: none;
  content: '';
}

.panel-orb,
.panel-copy,
.panel-action {
  position: relative;
  z-index: 1;
}

.panel-orb {
  display: grid;
  width: 3.5rem;
  height: 3.5rem;
  place-items: center;
  border: 1px solid rgba(255, 255, 255, 0.18);
  border-radius: 50%;
  background:
    radial-gradient(circle at 38% 26%, rgba(255, 255, 255, 0.95), transparent 22%),
    radial-gradient(circle, color-mix(in srgb, var(--panel-accent) 84%, #ffffff 16%), rgba(36, 28, 87, 0.92));
  box-shadow: 0 0 32px color-mix(in srgb, var(--panel-accent) 34%, transparent);
}

.panel-orb img {
  width: 1.55rem;
  height: 1.55rem;
  object-fit: contain;
}

.panel-copy {
  display: grid;
  align-content: center;
  gap: var(--space-2);
  min-width: 0;
  text-align: left;
}

.panel-eyebrow {
  margin: 0;
  color: var(--color-lavender);
  font-size: 0.72rem;
  font-weight: 760;
  letter-spacing: 0.18em;
  text-transform: uppercase;
}

h2 {
  margin: 0;
  color: var(--color-starlight);
  font-size: clamp(1.55rem, 3vw, 2.15rem);
  line-height: 0.96;
  letter-spacing: -0.06em;
}

.panel-copy p:not(.panel-eyebrow) {
  max-width: 44rem;
  margin: 0;
  color: var(--color-mist);
  font-size: 0.94rem;
  line-height: 1.65;
}

.panel-action {
  display: inline-flex;
  width: fit-content;
  align-items: center;
  justify-content: center;
  gap: 0.45rem;
  padding: 0.86rem 1rem;
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: var(--radius-pill);
  background: rgba(255, 255, 255, 0.08);
  color: var(--color-starlight);
  font-size: 0.75rem;
  font-weight: 760;
  letter-spacing: 0.13em;
  outline: none;
  text-transform: uppercase;
  white-space: nowrap;
  transition:
    border-color var(--duration-mid) var(--ease-soft),
    background var(--duration-mid) var(--ease-soft),
    transform var(--duration-mid) var(--ease-soft);
}

.panel-action:hover,
.panel-action:focus-visible {
  border-color: rgba(255, 255, 255, 0.32);
  background: color-mix(in srgb, var(--panel-accent) 18%, transparent);
  transform: translateY(-2px);
}

.panel-action:focus-visible {
  box-shadow: var(--shadow-focus);
}

@media (max-width: 760px) {
  .platform-panel {
    grid-template-columns: 1fr;
    justify-items: center;
    width: 100%;
    min-height: 0;
    text-align: center;
  }

  .panel-copy {
    text-align: center;
  }

  .panel-action {
    width: 100%;
  }
}
</style>
