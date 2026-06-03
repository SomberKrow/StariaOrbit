<script setup>
defineProps({
  size: {
    type: String,
    required: true,
  },
  index: {
    type: Number,
    default: 0,
  },
})
</script>

<template>
  <div
    class="orbit-ring"
    :class="`orbit-ring-${index}`"
    :style="{ '--ring-size': size }"
    aria-hidden="true"
  />
</template>

<style scoped lang="scss">
.orbit-ring {
  position: absolute;
  top: 50%;
  left: 50%;
  width: var(--ring-size);
  height: var(--ring-size);
  border: 1px solid rgba(224, 217, 255, 0.095);
  border-radius: 50%;
  background:
    radial-gradient(circle, transparent 67%, rgba(255, 255, 255, 0.025) 68%, transparent 70%);
  box-shadow:
    inset 0 0 30px rgba(141, 122, 255, 0.035),
    0 0 28px rgba(141, 122, 255, 0.035);
  transform: translate(-50%, -50%);
}

.orbit-ring::before,
.orbit-ring::after {
  position: absolute;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.54);
  box-shadow: 0 0 14px rgba(255, 255, 255, 0.32);
  content: '';
}

.orbit-ring::before {
  top: 14%;
  right: 19%;
  width: 0.42rem;
  height: 0.42rem;
}

.orbit-ring::after {
  right: 28%;
  bottom: 11%;
  width: 0.24rem;
  height: 0.24rem;
  opacity: 0.58;
}

.orbit-ring-0 {
  opacity: 0.78;
}

.orbit-ring-1 {
  opacity: 0.7;
}

.orbit-ring-2 {
  opacity: 0.54;
}

.orbit-ring-3 {
  opacity: 0.38;
}
</style>
