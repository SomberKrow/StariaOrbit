<template>
  <div class="star-backdrop" aria-hidden="true">
    <div class="nebula nebula-one" />
    <div class="nebula nebula-two" />
    <div class="nebula nebula-three" />
    <div class="star-field star-field-far" />
    <div class="star-field star-field-mid" />
    <div class="star-field star-field-near" />
    <div class="star-vignette" />
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
    radial-gradient(circle at 46% 19%, rgba(110, 86, 212, 0.24), transparent 32rem),
    radial-gradient(circle at 77% 68%, rgba(113, 71, 180, 0.16), transparent 25rem),
    radial-gradient(circle at 18% 82%, rgba(62, 47, 132, 0.12), transparent 22rem),
    linear-gradient(180deg, #080716 0%, #050610 58%, #020208 100%);
}

.nebula {
  position: absolute;
  border-radius: 50%;
  opacity: 0.46;
  filter: blur(48px);
  transform: translate3d(0, 0, 0);
}

.nebula-one {
  top: 3%;
  left: 6%;
  width: 34rem;
  height: 34rem;
  background: radial-gradient(circle, rgba(169, 140, 255, 0.29), transparent 68%);
  animation: nebula-drift 28s var(--ease-soft) infinite alternate;
}

.nebula-two {
  right: -2%;
  bottom: -4%;
  width: 36rem;
  height: 36rem;
  background: radial-gradient(circle, rgba(198, 166, 255, 0.12), transparent 70%);
  animation: nebula-drift 36s var(--ease-soft) infinite alternate-reverse;
}

.nebula-three {
  top: 42%;
  left: 47%;
  width: 27rem;
  height: 27rem;
  background: radial-gradient(circle, rgba(111, 83, 196, 0.11), transparent 70%);
  opacity: 0.42;
  animation: nebula-drift 40s var(--ease-soft) infinite alternate;
}

.star-field {
  position: absolute;
  top: 0;
  left: 0;
  width: 1px;
  height: 1px;
  border-radius: 50%;
  background: transparent;
  will-change: transform;
}

.star-field-far {
  opacity: 0.58;
  box-shadow:
    4vw 12vh 0 rgba(255, 255, 255, 0.48),
    9vw 76vh 0 rgba(218, 210, 255, 0.36),
    13vw 31vh 0 rgba(255, 255, 255, 0.42),
    19vw 58vh 0 rgba(213, 202, 255, 0.38),
    24vw 18vh 0 rgba(255, 255, 255, 0.42),
    29vw 84vh 0 rgba(213, 202, 255, 0.34),
    34vw 43vh 0 rgba(255, 255, 255, 0.46),
    39vw 67vh 0 rgba(213, 202, 255, 0.32),
    44vw 25vh 0 rgba(255, 255, 255, 0.4),
    51vw 89vh 0 rgba(213, 202, 255, 0.35),
    57vw 15vh 0 rgba(255, 255, 255, 0.48),
    63vw 72vh 0 rgba(213, 202, 255, 0.32),
    68vw 38vh 0 rgba(255, 255, 255, 0.44),
    73vw 9vh 0 rgba(213, 202, 255, 0.36),
    78vw 81vh 0 rgba(255, 255, 255, 0.42),
    86vw 48vh 0 rgba(213, 202, 255, 0.34),
    93vw 22vh 0 rgba(255, 255, 255, 0.48),
    97vw 91vh 0 rgba(213, 202, 255, 0.33),
    12vw 7vh 0 rgba(255, 255, 255, 0.34),
    47vw 6vh 0 rgba(213, 202, 255, 0.3),
    82vw 5vh 0 rgba(255, 255, 255, 0.35),
    7vw 94vh 0 rgba(213, 202, 255, 0.32),
    65vw 96vh 0 rgba(255, 255, 255, 0.34),
    91vw 64vh 0 rgba(213, 202, 255, 0.3);
  animation: star-drift-far 150s linear infinite;
}

.star-field-mid {
  opacity: 0.74;
  box-shadow:
    6vw 43vh 0 0.5px rgba(255, 255, 255, 0.72),
    11vw 19vh 0 0.5px rgba(216, 204, 255, 0.58),
    15vw 91vh 0 0.5px rgba(255, 255, 255, 0.68),
    22vw 66vh 0 0.5px rgba(216, 204, 255, 0.52),
    31vw 11vh 0 0.5px rgba(255, 255, 255, 0.66),
    37vw 78vh 0 0.5px rgba(216, 204, 255, 0.56),
    46vw 51vh 0 0.5px rgba(255, 255, 255, 0.7),
    54vw 28vh 0 0.5px rgba(216, 204, 255, 0.52),
    61vw 94vh 0 0.5px rgba(255, 255, 255, 0.7),
    69vw 57vh 0 0.5px rgba(216, 204, 255, 0.54),
    75vw 34vh 0 0.5px rgba(255, 255, 255, 0.68),
    82vw 12vh 0 0.5px rgba(216, 204, 255, 0.55),
    89vw 73vh 0 0.5px rgba(255, 255, 255, 0.72),
    96vw 39vh 0 0.5px rgba(216, 204, 255, 0.56),
    3vw 51vh 0 0.5px rgba(255, 255, 255, 0.52),
    27vw 3vh 0 0.5px rgba(216, 204, 255, 0.44),
    53vw 7vh 0 0.5px rgba(255, 255, 255, 0.54),
    72vw 88vh 0 0.5px rgba(216, 204, 255, 0.45),
    98vw 9vh 0 0.5px rgba(255, 255, 255, 0.5);
  filter: drop-shadow(0 0 4px rgba(216, 204, 255, 0.16));
  animation: star-drift-mid 126s linear infinite reverse;
}

.star-field-near {
  opacity: 0.82;
  box-shadow:
    8vw 64vh 0 1px rgba(255, 255, 255, 0.88),
    17vw 37vh 0 1px rgba(232, 224, 255, 0.78),
    28vw 72vh 0 1px rgba(255, 255, 255, 0.76),
    42vw 17vh 0 1px rgba(232, 224, 255, 0.82),
    59vw 63vh 0 1px rgba(255, 255, 255, 0.84),
    71vw 24vh 0 1px rgba(232, 224, 255, 0.76),
    84vw 86vh 0 1px rgba(255, 255, 255, 0.82),
    94vw 58vh 0 1px rgba(232, 224, 255, 0.8),
    2vw 26vh 0 0.8px rgba(255, 255, 255, 0.68),
    36vw 96vh 0 0.8px rgba(232, 224, 255, 0.66),
    66vw 4vh 0 0.8px rgba(255, 255, 255, 0.7),
    99vw 79vh 0 0.8px rgba(232, 224, 255, 0.64);
  filter: drop-shadow(0 0 6px rgba(216, 204, 255, 0.22));
  animation: star-drift-near 104s linear infinite;
}

.star-vignette {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(circle at 50% 42%, transparent 0 36rem, rgba(2, 2, 8, 0.18) 62rem),
    linear-gradient(180deg, rgba(2, 2, 8, 0.08), rgba(2, 2, 8, 0.34));
}

.grain {
  position: absolute;
  inset: 0;
  opacity: 0.04;
  background-image:
    radial-gradient(circle at 17% 23%, rgba(255, 255, 255, 0.16) 0 0.7px, transparent 1px),
    radial-gradient(circle at 61% 71%, rgba(255, 255, 255, 0.12) 0 0.7px, transparent 1px);
  background-size:
    9rem 9rem,
    13rem 13rem;
  mix-blend-mode: overlay;
}

@keyframes star-drift-far {
  from {
    transform: translate3d(0, 0, 0) scale(1);
  }

  to {
    transform: translate3d(-2rem, 1.4rem, 0) scale(1.02);
  }
}

@keyframes star-drift-mid {
  from {
    transform: translate3d(0, 0, 0) scale(1);
  }

  to {
    transform: translate3d(2.6rem, -1.8rem, 0) scale(1.025);
  }
}

@keyframes star-drift-near {
  from {
    transform: translate3d(0, 0, 0) scale(1);
  }

  to {
    transform: translate3d(-3.2rem, -2rem, 0) scale(1.03);
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
