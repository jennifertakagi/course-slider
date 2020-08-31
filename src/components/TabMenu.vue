<template>
  <nav id="menu-section" aria-label="mainmenulabel">
    <ul class="menu-container">
      <h2 id="mainmenulabel" hidden>Main Menu</h2>
      <TabLink
        v-for="category in categories"
        :key="category"
        :category="category"
        @filterCategory="emitCategory"
      />
    </ul>
  </nav>
</template>

<script>

import TabLink from './TabLink';

export default {
  name: 'TabMenu',
  components: {
    TabLink,
  },
  data() {
    return {
      hover: false,
    };
  },
  props: {
    categories: {
      type: Array,
      required: true,
    },
  },
  methods: {
    emitCategory(value) {
      this.$emit('filterByCategory', value);
    },
  },
};
</script>

<style scoped>
.menu-container {
  display: flex;
  justify-content: space-between;
  width: 50%;
  margin: 0 auto 5%;
}

.visuallyhidden {
  display: none;
}
</style>
