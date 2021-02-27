<template>
  <div class="panel">
    <div class="panel-heading">
      <h3 class="panel-title">Star on Github</h3>
    </div>
    <div class="panel-body">
      <a
        class="github-button"
        href="https://github.com/sohrabtaee/standard-persian-fonts"
        data-icon="octicon-star"
        data-size="large"
        data-show-count="true"
        aria-label="Star sohrabtaee/standard-persian-fonts on GitHub"
      >
        Star
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'star-on-github',
}
</script>

<style lang="scss" scoped>
.panel {
  direction: ltr;
  display: none;
}
.panel-body {
  padding: 1em 1em 0.5em;
}

@media (min-width: $media-tablet) {
  .panel {
    display: block;
  }
}
</style>
