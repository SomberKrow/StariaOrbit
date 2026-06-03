<template>
  <div class="star-backdrop" aria-hidden="true">
    <div class="nebula nebula-one" />
    <div class="nebula nebula-two" />
    <div class="star-field star-field-one" />
    <div class="star-field star-field-two" />
    <div class="grain" />
  </div>
</template>

<style scoped lang="scss">
.star-backdrop {
  position: fixed;
  z-index: 0;
  inset: 0;
  overflow: hidden;
  pointer-events: none;
  background:
    radial-gradient(circle at 50% 24%, rgba(104, 83, 205, 0.28), transparent 30rem),
    radial-gradient(circle at 76% 68%, rgba(85, 47, 133, 0.18), transparent 24rem),
    linear-gradient(180deg, #0a0c1c 0%, #050711 58%, #03040a 100%);
}

.nebula {
  position: absolute;
  width: 34rem;
  height: 34rem;
  border-radius: 50%;
  opacity: 0.52;
  filter: blur(44px);
  transform: translate3d(0, 0, 0);
}

.nebula-one {
  top: 6%;
  left: 8%;
  background: radial-gradient(circle, rgba(137, 117, 255, 0.33), transparent 68%);
  animation: nebula-drift 22s var(--ease-soft) infinite alternate;
}

.nebula-two {
  right: 4%;
  bottom: 2%;
  background: radial-gradient(circle, rgba(255, 178, 226, 0.13), transparent 70%);
  animation: nebula-drift 28s var(--ease-soft) infinite alternate-reverse;
}

.star-field {
  position: absolute;
  inset: -15%;
  opacity: 0.55;
  background-image:
    radial-gradient(circle, rgba(255, 255, 255, 0.74) 0 1px, transparent 1.4px),
    radial-gradient(circle, rgba(204, 191, 255, 0.46) 0 1px, transparent 1.4px);
  background-position:
    0 0,
    72px 42px;
  background-size:
    148px 148px,
    214px 214px;
}

.star-field-one {
  animation: star-drift 80s linear infinite;
}

.star-field-two {
  opacity: 0.26;
  background-size:
    260px 260px,
    330px 330px;
  animation: star-drift 130s linear infinite reverse;
}

.grain {
  position: absolute;
  inset: 0;
  opacity: 0.08;
  background-image: linear-gradient(rgba(255, 255, 255, 0.16) 1px, transparent 1px);
  background-size: 100% 3px;
  mix-blend-mode: overlay;
}

@keyframes star-drift {
  from {
    transform: translate3d(0, 0, 0);
  }

  to {
    transform: translate3d(-120px, 80px, 0);
  }
}

@keyframes nebula-drift {
  from {
    transform: translate3d(-1rem, -0.5rem, 0) scale(1);
  }

  to {
    transform: translate3d(1.5rem, 1rem, 0) scale(1.08);
  }
}

@media (prefers-reduced-motion: reduce) {
  .nebula,
  .star-field {
    animation: none;
  }
}
</style>
