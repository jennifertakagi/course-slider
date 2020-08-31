<template>
  <li
    class="category-text"
    :aria-label="category"
    tabindex="0"
    @mouseover="emitHoverEvent"
    @mouseleave="emitEventLeave"
  >
    {{category}}
  </li>
</template>

<script>
export default {
  name: 'TabLink',
  props: {
    /**
     * Category name
     */
    category: {
      type: String,
      required: true,
    },
  },
  methods: {
    /**
     * Emits 'filterCategory' event on mouse over
     * and send the category to be filterd by
     */
    emitHoverEvent() {
      this.$emit('filterCategory', this.category);
    },
    /**
     * Emits 'filterCategory' event on mouse leave
     * and send no value, to return all categories
     */
    emitEventLeave() {
      this.$emit('filterCategory', '');
    },
  },
};
</script>

<style scoped>
  .category-text {
    text-transform: uppercase;
    font-weight: 700;
    font-size: 1.5rem;
    color: var(--color-text-title);
    text-align: center;
    letter-spacing: 2.31px;
    list-style-type: none;
    height: 25px;
  }

  .category-text:hover {
    border-bottom: 2px solid var(--color-text-title);
    cursor: pointer;
  }
</style>
