<template>
  <div
    class="flex flex-col"
    :class="{ 'card': !transparent, 'card--glass': glass }"
  >
    <slot />
  </div>
</template>

<script>
export default {
  name: 'BaseCard',
  props: {
    glass: {
      type: Boolean,
      default: false
    },
    transparent: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>
.card {
  background-color: var(--bg-card);
  border-radius: 10px;
}

.card--glass {
  background-color: initial;
  border: 1px solid #fff;
  border-radius: 15px;
  box-shadow: 0 0 1rem 0 rgba(0, 0, 0, 0.2);
  position: relative;
  overflow: hidden;
}

.card--glass:before {
  background-color: rgba(255, 255, 255, 0.3);
  backdrop-filter: blur(10px) saturate(100%) contrast(45%) brightness(130%);
  content: "";
  height: 100%;
  position: absolute;
  width: 100%;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  z-index: -10;
}
</style>
