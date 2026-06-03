<script setup>
import { computed } from 'vue'

const props = defineProps({
  planet: {
    type: Object,
    required: true,
  },
  active: {
    type: Boolean,
    default: false,
  },
})

const emit = defineEmits(['activate'])

const orbitStyle = computed(() => ({
  '--orbit-size': props.planet.orbitSize,
  '--orbit-duration': props.planet.orbitDuration,
  '--orbit-delay': props.planet.orbitDelay,
  '--start-angle': props.planet.startAngle,
  '--counter-start-angle': props.planet.counterStartAngle,
  '--planet-size': props.planet.planetSize,
  '--planet-accent': props.planet.accent,
}))

function activatePlanet() {
  emit('activate', props.planet)
}
</script>

<template>
  <div
    class="planet-orbit"
    :class="{ 'is-active': active }"
    :style="orbitStyle"
  >
    <div class="planet-shell">
      <a
        class="planet-button"
        :class="{ 'is-active': active }"
        :href="planet.url"
        target="_blank"
        rel="noreferrer noopener"
        :aria-label="`Open Staria VT on ${planet.name}`"
        @focus="activatePlanet"
        @pointerenter="activatePlanet"
      >
        <span class="planet-atmosphere" aria-hidden="true" />

        <span class="planet-surface" aria-hidden="true" />

        <img
          :src="planet.icon"
          alt=""
          aria-hidden="true"
        >

        <span class="sr-only">
          {{ planet.name }}
        </span>
      </a>
    </div>
  </div>
</template>

<style scoped lang="scss">
.planet-orbit {
  position: absolute;
  top: 50%;
  left: 50%;
  z-index: 3;
  width: var(--orbit-size);
  height: var(--orbit-size);
  margin-top: calc(var(--orbit-size) / -2);
  margin-left: calc(var(--orbit-size) / -2);
  border-radius: 50%;
  pointer-events: none;
  transform: rotate(var(--start-angle)) translateZ(0);
  transform-origin: center;
  animation: orbit-path var(--orbit-duration) linear infinite;
  animation-delay: var(--orbit-delay);
  backface-visibility: hidden;
  will-change: transform;
}

.planet-shell {
  position: absolute;
  top: 50%;
  left: 100%;
  width: var(--planet-size);
  height: var(--planet-size);
  pointer-events: auto;
  transform: translate(-50%, -50%) translateZ(0);
  backface-visibility: hidden;
}

.planet-button {
  position: relative;
  display: grid;
  width: 100%;
  height: 100%;
  place-items: center;
  overflow: visible;
  border: 1px solid rgba(255, 255, 255, 0.22);
  border-radius: 50%;
  outline: none;
  background:
    radial-gradient(circle at 34% 24%, rgba(255, 255, 255, 0.96), rgba(255, 255, 255, 0.28) 18%, transparent 25%),
    radial-gradient(circle at 56% 62%, color-mix(in srgb, var(--planet-accent) 82%, #ffffff 18%), rgba(48, 37, 108, 0.88) 68%, rgba(9, 10, 26, 0.96) 100%);
  box-shadow:
    0 0 24px color-mix(in srgb, var(--planet-accent) 34%, transparent),
    inset -12px -15px 22px rgba(0, 0, 0, 0.34),
    inset 10px 10px 18px rgba(255, 255, 255, 0.14);
  transform: rotate(var(--counter-start-angle)) translateZ(0);
  transform-origin: center;
  animation: counter-orbit var(--orbit-duration) linear infinite;
  animation-delay: var(--orbit-delay);
  backface-visibility: hidden;
  transition:
    border-color var(--duration-mid) var(--ease-soft),
    box-shadow var(--duration-mid) var(--ease-soft),
    filter var(--duration-mid) var(--ease-soft);
  will-change: transform;
}

.planet-button::before {
  position: absolute;
  inset: -0.5rem;
  border: 1px solid color-mix(in srgb, var(--planet-accent) 38%, transparent);
  border-radius: 50%;
  opacity: 0;
  transform: scale(0.96);
  transition:
    opacity var(--duration-mid) var(--ease-soft),
    transform var(--duration-mid) var(--ease-soft);
  content: '';
}

.planet-button::after {
  position: absolute;
  inset: 16%;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.2), transparent 72%);
  opacity: 0.58;
  content: '';
}

.planet-atmosphere {
  position: absolute;
  inset: -0.32rem;
  border-radius: 50%;
  background: radial-gradient(circle, color-mix(in srgb, var(--planet-accent) 26%, transparent), transparent 72%);
  opacity: 0.72;
  filter: blur(5px);
  pointer-events: none;
}

.planet-surface {
  position: absolute;
  inset: 0;
  border-radius: 50%;
  background:
    linear-gradient(135deg, rgba(255, 255, 255, 0.16), transparent 36%),
    radial-gradient(circle at 72% 78%, rgba(0, 0, 0, 0.22), transparent 42%);
  pointer-events: none;
}

.planet-button img {
  position: relative;
  z-index: 2;
  width: 48%;
  height: 48%;
  object-fit: contain;
  filter: drop-shadow(0 4px 11px rgba(0, 0, 0, 0.34));
}

.planet-button:hover,
.planet-button:focus-visible,
.planet-button.is-active {
  border-color: rgba(255, 255, 255, 0.44);
  box-shadow:
    0 0 32px color-mix(in srgb, var(--planet-accent) 62%, transparent),
    0 0 60px color-mix(in srgb, var(--planet-accent) 18%, transparent),
    inset -12px -15px 22px rgba(0, 0, 0, 0.32),
    inset 10px 10px 18px rgba(255, 255, 255, 0.18);
  filter: saturate(1.08);
}

.planet-button:hover::before,
.planet-button:focus-visible::before,
.planet-button.is-active::before {
  opacity: 1;
  transform: scale(1);
}

.planet-button:focus-visible {
  box-shadow:
    var(--shadow-focus),
    0 0 34px color-mix(in srgb, var(--planet-accent) 64%, transparent);
}

@keyframes orbit-path {
  from {
    transform: rotate(var(--start-angle)) translateZ(0);
  }

  to {
    transform: rotate(calc(var(--start-angle) + 1turn)) translateZ(0);
  }
}

@keyframes counter-orbit {
  from {
    transform: rotate(var(--counter-start-angle)) translateZ(0);
  }

  to {
    transform: rotate(calc(var(--counter-start-angle) - 1turn)) translateZ(0);
  }
}

@media (prefers-reduced-motion: reduce) {
  .planet-orbit,
  .planet-button {
    animation: none;
  }
}
</style>
