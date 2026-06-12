<template>
  <div class="star-backdrop" aria-hidden="true">
    <div class="nebula nebula-one" />
    <div class="nebula nebula-two" />
    <div class="nebula nebula-three" />
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
    radial-gradient(circle at 50% 22%, rgba(110, 86, 212, 0.28), transparent 30rem),
    radial-gradient(circle at 76% 68%, rgba(113, 71, 180, 0.18), transparent 24rem),
    linear-gradient(180deg, #090817 0%, #050610 58%, #030309 100%);
}

.nebula {
  position: absolute;
  width: 34rem;
  height: 34rem;
  border-radius: 50%;
  opacity: 0.5;
  filter: blur(46px);
  transform: translate3d(0, 0, 0);
}

.nebula-one {
  top: 6%;
  left: 8%;
  background: radial-gradient(circle, rgba(169, 140, 255, 0.31), transparent 68%);
  animation: nebula-drift 24s var(--ease-soft) infinite alternate;
}

.nebula-two {
  right: 4%;
  bottom: 2%;
  background: radial-gradient(circle, rgba(198, 166, 255, 0.13), transparent 70%);
  animation: nebula-drift 30s var(--ease-soft) infinite alternate-reverse;
}

.nebula-three {
  top: 42%;
  left: 50%;
  width: 26rem;
  height: 26rem;
  background: radial-gradient(circle, rgba(111, 83, 196, 0.12), transparent 70%);
  opacity: 0.46;
  animation: nebula-drift 34s var(--ease-soft) infinite alternate;
}

.star-field {
  position: absolute;
  inset: -15%;
  opacity: 0.48;
  background-image:
    radial-gradient(circle, rgba(255, 255, 255, 0.7) 0 1px, transparent 1.4px),
    radial-gradient(circle, rgba(204, 191, 255, 0.42) 0 1px, transparent 1.4px);
  background-position:
    0 0,
    72px 42px;
  background-size:
    156px 156px,
    228px 228px;
}

.star-field-one {
  animation: star-drift 86s linear infinite;
}

.star-field-two {
  opacity: 0.22;
  background-size:
    280px 280px,
    350px 350px;
  animation: star-drift 140s linear infinite reverse;
}

.grain {
  position: absolute;
  inset: 0;
  opacity: 0.065;
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
