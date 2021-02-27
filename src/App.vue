<template>
  <div class="standard-persian-fonts">
    <FontList :fonts="fonts" />
    <Filters @filter="handleFilter" />
  </div>
</template>

<script>
import FontList from './components/FontList.vue'
import Filters from './components/Filters.vue'
import allFonts from './assets/fonts'

export default {
  name: 'standard-persian-fonts',
  components: { FontList, Filters },
  data() {
    return {
      fonts: allFonts,
    }
  },
  methods: {
    handleFilter(filters) {
      let fonts = allFonts
      if (filters.types.length) {
        fonts = fonts.filter((font) => {
          return filters.types.some((type) => type === font.type)
        })
      }
      if (filters.weights.length) {
        fonts = fonts.filter((font) => {
          return filters.weights.some((weight) => {
            return font.weights.includes(weight)
          })
        })
      }
      this.fonts = fonts
    },
  },
}
</script>

<style lang="scss">
@import 'assets/styles.scss';
@import 'assets/font-face.scss';
</style>
