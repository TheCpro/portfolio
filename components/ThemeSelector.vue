<template>
  <list-wrapper>
    <list-item
      v-for="(theme, index) in activeThemes"
      :key="theme.value + index"
      class="text-xl"
      :active="theme.active"
      @click="setTheme(theme.value)"
    >
      {{ theme.text }}
    </list-item>
  </list-wrapper>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: 'default'
    },
    themes: {
      type: Array,
      default: () => []
    }
  },
  computed: {
    activeThemes () {
      return this.themes.map((theme) => {
        const internalTheme = Object.assign({}, theme)
        internalTheme.active = (theme.value === this.selectedTheme)
        return internalTheme
      })
    },
    selectedTheme: {
      get () {
        return this.value
      },
      set (val) {
        this.$emit('input', val)
      }
    }
  },
  methods: {
    setTheme (themeValue) {
      this.selectedTheme = themeValue
      this.$emit('click', themeValue)
    }
  }
}
</script>

<style lang="scss" scoped></style>
