<script setup>
import InFeaturedSignal from './components/inFeaturedSignal.vue'
import InHeroGalaxy from './components/inHeroGalaxy.vue'
import InSiteFooter from './components/inSiteFooter.vue'
import InSiteHeader from './components/inSiteHeader.vue'
import InStarBackdrop from './components/inStarBackdrop.vue'
</script>

<template>
  <div class="staria-shell">
    <InStarBackdrop />
    <InSiteHeader />

    <main id="main-content">
      <InHeroGalaxy />
      <InFeaturedSignal />
    </main>

    <InSiteFooter />
  </div>
</template>

<style scoped lang="scss">
.staria-shell {
  position: relative;
  isolation: isolate;
  min-height: 100vh;
  overflow-x: clip;
}

main {
  position: relative;
  z-index: 2;
}
</style>
