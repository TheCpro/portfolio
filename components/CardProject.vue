<template>
  <base-card class="rounded-lg">
    <picture>
      <source type="image/avif" :srcset="`${src}.avif`">
      <img
        loading="lazy"
        decoding="async"
        :src="`${src}.jpg`"
        width="1908"
        height="930"
        :alt="alt"
        class="max-w-full h-auto align-middle border-none rounded-t-lg"
      >
    </picture>
    <card-text class="flex flex-col px-5 mt-3">
      <h2 class="font-bold">
        {{ title }}
      </h2>
      <p class="h-28 overflow-hidden">
        {{ description }}
      </p>
      <div>
        <base-link class="mt-1" :href="siteUrl" :text="$t('visit')" icon />
      </div>
    </card-text>
  </base-card>
</template>

<script>
export default {
  name: 'CardProject',
  props: {
    src: {
      type: String,
      default: ''
    },
    title: {
      type: String,
      default: ''
    },
    description: {
      type: String,
      default: ''
    },
    siteUrl: {
      type: String,
      default: ''
    },
    alt: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss" scoped>
.h-100px {
  height: 100px;
}
</style>
