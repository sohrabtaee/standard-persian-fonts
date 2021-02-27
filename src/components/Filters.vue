<template>
  <div class="filters">
    <div class="panel">
      <div class="panel-heading">
        <h3 class="panel-title">فیلتر</h3>
      </div>
      <div class="panel-body">
        <h4>بر اساس نوع فونت</h4>
        <div class="checkbox" v-for="type in types" :key="type.value">
          <label>
            <input
              type="checkbox"
              :value="type.value"
              v-model="filters.types"
              @change="filter"
            />
            <span>{{ type.name }}</span>
          </label>
        </div>
      </div>
      <div class="panel-body">
        <h4>بر اساس وزن فونت</h4>
        <div class="checkbox" v-for="weight in weights" :key="weight">
          <label>
            <input
              type="checkbox"
              :value="weight"
              v-model="filters.weights"
              @change="filter"
            />
            <span>{{ weight.replace(/-/g, ' ') }}</span>
          </label>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'filters',
  data() {
    return {
      weights: ['ultra-light', 'light', 'normal', 'medium', 'bold', 'black'],
      types: [
        {
          name: 'لبه گرد (sans-serif)',
          value: 'sans-serif',
        },
        {
          name: 'لبه تیز (serif)',
          value: 'serif',
        },
      ],
      filters: {
        types: [],
        weights: [],
      },
    }
  },
  methods: {
    filter() {
      this.$emit('filter', this.filters)
    },
  },
}
</script>

<style lang="scss" scoped>
.panel-body {
  padding: 1em;
  display: block;

  h4 {
    font-weight: bold;
    margin-bottom: 0.5em;
  }
}

.checkbox {
  label {
    display: flex;
    align-items: center;
  }
  input {
    margin: 0 0 0 0.5em;
  }
  span {
    text-transform: capitalize;
  }
}
</style>
