<script setup>
import { siteCopy } from '../data/inSocialLinks'
</script>

<template>
  <footer class="site-footer">
    <p>
      {{ siteCopy.footer }}
    </p>
  </footer>
</template>

<style scoped lang="scss">
.site-footer {
  position: relative;
  z-index: 2;
  width: var(--container);
  padding: var(--space-8) 0 var(--space-10);
  margin: 0 auto;
  text-align: center;
}

.site-footer p {
  margin: 0;
  color: var(--color-muted);
  font-size: 0.78rem;
  font-weight: 680;
  letter-spacing: 0.16em;
  text-transform: uppercase;
}
</style>
