<template>
  <header class="site-header" aria-label="Staria_VT site header">
    <a
      class="brand-mark"
      href="#top"
      aria-label="Return to Staria_VT"
    >
      <span class="brand-sigil" aria-hidden="true">
        ✦
      </span>

      <span class="brand-copy">
        <strong>
          Staria_VT
        </strong>

        <small>
          Dreaming among stars
        </small>
      </span>
    </a>

    <a class="header-link" href="#social-galaxy">
      Come find me!
    </a>
  </header>
</template>

<style scoped lang="scss">
.site-header {
  position: absolute;
  z-index: 10;
  top: var(--space-4);
  left: 50%;
  display: flex;
  width: var(--container);
  align-items: center;
  justify-content: space-between;
  padding: 0.72rem 0.85rem;
  border: 1px solid rgba(255, 255, 255, 0.105);
  border-radius: var(--radius-pill);
  background:
    linear-gradient(135deg, rgba(255, 255, 255, 0.07), transparent),
    rgba(6, 8, 19, 0.46);
  box-shadow: 0 12px 52px rgba(0, 0, 0, 0.2);
  backdrop-filter: blur(18px);
  transform: translateX(-50%);
}

.brand-mark,
.header-link {
  outline: none;
}

.brand-mark {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
}

.brand-sigil {
  display: grid;
  width: 2.35rem;
  height: 2.35rem;
  place-items: center;
  border: 1px solid rgba(255, 255, 255, 0.18);
  border-radius: 50%;
  background:
    radial-gradient(circle at 45% 28%, rgba(255, 255, 255, 0.88), rgba(169, 140, 255, 0.54) 44%, rgba(55, 39, 96, 0.76) 100%);
  box-shadow: 0 0 28px rgba(169, 140, 255, 0.26);
  color: var(--color-starlight);
}

.brand-copy {
  display: grid;
  gap: 0.1rem;
}

.brand-copy strong {
  color: var(--color-starlight);
  font-size: 0.82rem;
  font-weight: 760;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}

.brand-copy small {
  color: var(--color-muted);
  font-size: 0.68rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.header-link {
  padding: 0.72rem 1rem;
  border: 1px solid rgba(255, 255, 255, 0.13);
  border-radius: var(--radius-pill);
  color: var(--color-lavender);
  font-size: 0.74rem;
  font-weight: 720;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  transition:
    border-color var(--duration-mid) var(--ease-soft),
    color var(--duration-mid) var(--ease-soft),
    background var(--duration-mid) var(--ease-soft),
    transform var(--duration-mid) var(--ease-soft);
}

.brand-mark:focus-visible,
.header-link:focus-visible {
  box-shadow: var(--shadow-focus);
}

.header-link:hover,
.header-link:focus-visible {
  border-color: rgba(255, 255, 255, 0.28);
  background: rgba(255, 255, 255, 0.08);
  color: var(--color-starlight);
  transform: translateY(-1px);
}

@media (max-width: 680px) {
  .site-header {
    top: var(--space-3);
    padding: 0.62rem;
  }

  .brand-copy small,
  .header-link {
    display: none;
  }

  .brand-copy strong {
    font-size: 0.76rem;
  }
}
</style>
