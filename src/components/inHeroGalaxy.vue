<script setup>
import { computed, ref } from 'vue'
import stariaCore from '../assets/images/staria-core.svg'
import { siteCopy, socialLinks } from '../data/inSocialLinks'
import InOrbitRing from './inOrbitRing.vue'
import InPlatformPanel from './inPlatformPanel.vue'
import InSocialPlanet from './inSocialPlanet.vue'

const activePlatform = ref(socialLinks[0])

const orbitRings = ['340px', '430px', '520px', '610px']

const activePlatformId = computed(() => activePlatform.value?.id)

function setActivePlatform(platform) {
  activePlatform.value = platform
}
</script>

<template>
  <section id="top" class="hero-galaxy" aria-labelledby="hero-title">
    <div class="hero-shell">
      <div class="hero-copy">
        <p class="hero-eyebrow">
          {{ siteCopy.eyebrow }}
        </p>

        <h1 id="hero-title">
          {{ siteCopy.name }}
        </h1>

        <p class="hero-lead">
          {{ siteCopy.tagline }}
        </p>

        <div class="hero-meta" aria-label="Staria_VT signal status">
          <span>{{ siteCopy.status }}</span>
        </div>
      </div>

      <div id="social-galaxy" class="galaxy-stage" aria-label="Staria_VT Social Galaxy">
        <div class="galaxy-halo galaxy-halo-primary" aria-hidden="true" />
        <div class="galaxy-halo galaxy-halo-secondary" aria-hidden="true" />

        <div class="galaxy-system">
          <InOrbitRing
            v-for="(ring, index) in orbitRings"
            :key="ring"
            :size="ring"
            :index="index"
          />

          <div class="staria-core" :aria-label="siteCopy.coreLabel">
            <img
              :src="stariaCore"
              :alt="siteCopy.coreLabel"
            >

            <span class="core-aura" aria-hidden="true" />
            <span class="core-pulse" aria-hidden="true" />
          </div>

          <InSocialPlanet
            v-for="planet in socialLinks"
            :key="planet.id"
            :planet="planet"
            :active="planet.id === activePlatformId"
            @activate="setActivePlatform"
          />
        </div>

        <div class="galaxy-panel-wrap">
          <InPlatformPanel :platform="activePlatform" />
        </div>

        <p class="mobile-core-note">
          {{ siteCopy.mobileNote }}
        </p>
      </div>

      <nav class="mobile-constellation" aria-label="Staria_VT social links">
        <a
          v-for="planet in socialLinks"
          :key="planet.id"
          class="constellation-card"
          :class="`is-${planet.importance}`"
          :href="planet.url"
          target="_blank"
          rel="noreferrer noopener"
          :style="{ '--card-accent': planet.accent }"
          @focus="setActivePlatform(planet)"
          @pointerenter="setActivePlatform(planet)"
        >
          <span class="card-icon" aria-hidden="true">
            <img
              :src="planet.icon"
              alt=""
            >
          </span>

          <span class="card-copy">
            <span class="card-label">
              {{ planet.signal }}
            </span>

            <strong>
              {{ planet.name }}
            </strong>

            <small>
              {{ planet.description }}
            </small>
          </span>

          <span class="card-arrow" aria-hidden="true">
            ↗
          </span>
        </a>
      </nav>
    </div>
  </section>
</template>

<style scoped lang="scss">
.hero-galaxy {
  position: relative;
  min-height: 100vh;
  padding: clamp(6rem, 7.5vw, 7.25rem) 0 var(--space-16);
}

.hero-shell {
  display: grid;
  width: var(--container);
  gap: clamp(var(--space-8), 4vw, var(--space-12));
  margin: 0 auto;
}

.hero-copy {
  position: relative;
  z-index: 5;
  display: grid;
  justify-items: center;
  gap: var(--space-5);
  max-width: 60rem;
  margin: 0 auto;
  text-align: center;
}

.hero-eyebrow {
  width: fit-content;
  margin: 0;
  padding: 0.58rem 0.82rem;
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: var(--radius-pill);
  background: rgba(255, 255, 255, 0.05);
  color: var(--color-lavender);
  font-size: 0.72rem;
  font-weight: 760;
  letter-spacing: 0.22em;
  text-transform: uppercase;
}

h1 {
  margin: 0;
  color: var(--color-starlight);
  font-size: clamp(4rem, 8.4vw, 7.1rem);
  font-weight: 820;
  letter-spacing: -0.08em;
  line-height: 0.86;
  text-shadow: 0 0 48px rgba(216, 204, 255, 0.18);
}

.hero-lead {
  max-width: 42rem;
  margin: 0;
  color: var(--color-mist);
  font-size: clamp(1.12rem, 1.9vw, 1.34rem);
  line-height: 1.68;
}

.hero-meta {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: var(--space-2);
  max-width: 42rem;
}

.hero-meta span {
  padding: 0.52rem 0.72rem;
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: var(--radius-pill);
  background: rgba(255, 255, 255, 0.045);
  color: var(--color-muted);
  font-size: 0.68rem;
  font-weight: 760;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.galaxy-stage {
  position: relative;
  display: grid;
  justify-items: center;
  min-height: min(820px, 82vw);
  overflow: visible;
}

.galaxy-halo {
  position: absolute;
  top: clamp(15.5rem, 32vw, 22rem);
  aspect-ratio: 1;
  border-radius: 50%;
  pointer-events: none;
  transform: translateY(-50%);
}

.galaxy-halo-primary {
  width: min(650px, 66vw);
  background:
    radial-gradient(circle, rgba(255, 255, 255, 0.08) 0 8%, transparent 18%),
    radial-gradient(circle, rgba(169, 140, 255, 0.24), transparent 70%);
  filter: blur(28px);
  opacity: 0.9;
  animation: core-breathe 8s var(--ease-soft) infinite alternate;
}

.galaxy-halo-secondary {
  width: min(450px, 50vw);
  background: radial-gradient(circle, rgba(198, 166, 255, 0.14), transparent 72%);
  filter: blur(36px);
  opacity: 0.7;
  animation: slow-drift 12s var(--ease-soft) infinite alternate;
}

.galaxy-system {
  position: relative;
  width: min(690px, 66vw);
  aspect-ratio: 1;
  border-radius: 50%;
  overflow: visible;
}

.galaxy-panel-wrap {
  position: relative;
  z-index: 6;
  display: grid;
  width: min(780px, 100%);
  justify-items: center;
  margin-top: clamp(1.5rem, 2.2vw, 2rem);
}

.staria-core {
  position: absolute;
  z-index: 5;
  top: 50%;
  left: 50%;
  display: grid;
  width: clamp(8rem, 12vw, 9.9rem);
  aspect-ratio: 1;
  place-items: center;
  border: 1px solid rgba(255, 255, 255, 0.22);
  border-radius: 50%;
  background:
    radial-gradient(circle at 50% 38%, rgba(255, 255, 255, 0.24), rgba(169, 140, 255, 0.16) 42%, rgba(5, 7, 17, 0.84) 72%),
    rgba(255, 255, 255, 0.04);
  box-shadow:
    0 0 64px rgba(169, 140, 255, 0.36),
    0 0 120px rgba(198, 166, 255, 0.12),
    inset 0 0 38px rgba(255, 255, 255, 0.06);
  transform: translate(-50%, -50%);
}

.staria-core img {
  position: relative;
  z-index: 3;
  width: 96%;
  height: 96%;
  object-fit: contain;
}

.core-aura {
  position: absolute;
  inset: -0.42rem;
  border-radius: inherit;
  background: conic-gradient(
    from 180deg,
    transparent,
    rgba(216, 204, 255, 0.2),
    transparent,
    rgba(169, 140, 255, 0.16),
    transparent
  );
  opacity: 0.44;
  filter: blur(1px);
}

.core-pulse {
  position: absolute;
  inset: -1rem;
  border: 1px solid rgba(216, 204, 255, 0.2);
  border-radius: 50%;
  opacity: 0.52;
  animation: pulse-ring 4.2s var(--ease-soft) infinite;
}

.mobile-core-note {
  display: none;
  max-width: 18rem;
  margin: var(--space-5) auto 0;
  color: var(--color-muted);
  font-size: 0.92rem;
  line-height: 1.6;
  text-align: center;
}

.mobile-constellation {
  display: none;
}

@keyframes core-breathe {
  from {
    opacity: 0.72;
    transform: translateY(-50%) scale(0.96);
  }

  to {
    opacity: 1;
    transform: translateY(-50%) scale(1.03);
  }
}

@keyframes slow-drift {
  from {
    opacity: 0.52;
    transform: translate(8%, -54%) scale(0.98);
  }

  to {
    opacity: 0.72;
    transform: translate(3%, -48%) scale(1.04);
  }
}

@keyframes pulse-ring {
  0% {
    opacity: 0.48;
    transform: scale(0.9);
  }

  70% {
    opacity: 0;
    transform: scale(1.16);
  }

  100% {
    opacity: 0;
    transform: scale(1.16);
  }
}

@media (max-width: 980px) {
  .galaxy-stage {
    min-height: 42rem;
  }

  .galaxy-system {
    width: min(580px, 88vw);
  }

  .galaxy-panel-wrap {
    margin-top: 1.25rem;
  }
}

@media (max-width: 760px) {
  .hero-galaxy {
    padding-top: 6.25rem;
  }

  .hero-shell {
    gap: var(--space-8);
  }

  .galaxy-stage {
    min-height: 19rem;
  }

  .galaxy-halo {
    top: 50%;
  }

  .galaxy-halo-primary {
    width: min(390px, 92vw);
  }

  .galaxy-halo-secondary {
    width: min(300px, 80vw);
  }

  .galaxy-system {
    width: min(320px, 86vw);
  }

  .galaxy-system :deep(.orbit-ring),
  .galaxy-system :deep(.planet-orbit) {
    display: none;
  }

  .galaxy-panel-wrap {
    display: none;
  }

  .staria-core {
    width: clamp(8.2rem, 44vw, 10rem);
  }

  .mobile-core-note {
    display: block;
  }

  .hero-copy {
    gap: var(--space-5);
  }

  h1 {
    font-size: clamp(3.3rem, 15vw, 5.2rem);
    letter-spacing: -0.075em;
  }

  .hero-meta {
    display: none;
  }

  .mobile-constellation {
    display: grid;
    width: min(36rem, calc(100vw - 40px));
    gap: var(--space-3);
    margin: 0 auto;
  }
}

.constellation-card {
  display: grid;
  align-items: center;
  gap: var(--space-4);
  grid-template-columns: auto 1fr auto;
  padding: var(--space-4);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: var(--radius-lg);
  background:
    radial-gradient(circle at 12% 20%, color-mix(in srgb, var(--card-accent) 18%, transparent), transparent 12rem),
    rgba(255, 255, 255, 0.055);
  outline: none;
  box-shadow: 0 18px 50px rgba(0, 0, 0, 0.2);
  backdrop-filter: blur(18px);
  transition:
    border-color var(--duration-mid) var(--ease-soft),
    background var(--duration-mid) var(--ease-soft),
    transform var(--duration-mid) var(--ease-soft);
}

.constellation-card.is-primary {
  border-color: rgba(216, 204, 255, 0.18);
}

.constellation-card:hover,
.constellation-card:focus-visible {
  border-color: color-mix(in srgb, var(--card-accent) 46%, rgba(255, 255, 255, 0.2));
  background: rgba(255, 255, 255, 0.08);
  transform: translateY(-2px);
}

.constellation-card:focus-visible {
  box-shadow: var(--shadow-focus);
}

.card-icon {
  display: grid;
  width: 3.1rem;
  height: 3.1rem;
  flex: 0 0 auto;
  place-items: center;
  border-radius: 50%;
  background:
    radial-gradient(circle at 36% 26%, rgba(255, 255, 255, 0.9), transparent 24%),
    radial-gradient(circle, color-mix(in srgb, var(--card-accent) 82%, #ffffff 18%), rgba(36, 28, 87, 0.9));
  box-shadow: 0 0 28px color-mix(in srgb, var(--card-accent) 24%, transparent);
}

.card-icon img {
  width: 1.4rem;
  height: 1.4rem;
  object-fit: contain;
}

.card-copy {
  display: grid;
  gap: 0.16rem;
  min-width: 0;
}

.card-label {
  color: var(--color-muted);
  font-size: 0.68rem;
  font-weight: 740;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.card-copy strong {
  color: var(--color-starlight);
  font-size: 1rem;
}

.card-copy small {
  color: var(--color-mist);
  font-size: 0.84rem;
  line-height: 1.45;
}

.card-arrow {
  color: var(--color-lavender);
}

@media (prefers-reduced-motion: reduce) {
  .galaxy-halo,
  .core-pulse {
    animation: none;
  }
}
</style>
