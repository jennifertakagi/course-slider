<template>
  <nav id="menu-section" aria-label="mainmenulabel">
    <ul class="menu-container">
      <h2 id="mainmenulabel" hidden>Main Menu</h2>
      <TabLink
        v-for="category in categories"
        :key="category"
        :category="category"
        :isActive="category === categoryActive"
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
  props: {
    /**
     * All podcast's categories
     */
    categories: {
      type: Array,
      required: true,
    },
    /**
     * Category that is active
     */
    categoryActive: {
      type: String,
      requerid: true,
    },
  },
  methods: {
    /**
     * Emits 'filterByCategory' event on click behavior
     * and send the category to be filterd by
     */
    emitCategory(value) {
      this.$emit('filterByCategory', value);
    },
  },
};
</script>

<style scoped>
  #menu-section {
    display: none;
  }

  @media only screen and (min-width: 1207px) {
    #menu-section {
      display: block;
    }

    .menu-container {
      display: flex;
      justify-content: space-between;
      width: 50%;
      margin: 0 auto 6%;
    }
  }
</style>
