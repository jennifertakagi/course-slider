<template>
  <li
    class="category-text"
    :class="{ activate: isActive }"
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
    /**
     * Checks if the category is active
     */
    isActive: {
      type: Boolean,
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

  .category-text:after {
    position: absolute;
    content: '';
    height: 25px;
    width: 214px;
    border-bottom: 2px solid var(--color-text-title);
    -webkit-transform: scaleX(0.0001);
    transform: scaleX(0.0001);
    -webkit-transition: -webkit-transform 250ms ease-in-out;
    transition: -webkit-transform 250ms ease-in-out;
    transition: transform 250ms ease-in-out;
    transition: transform 250ms ease-in-out, -webkit-transform 250ms ease-in-out;
  }

  .category-text:hover:after {
    -webkit-transform: scaleX(1);
    -ms-transform: scaleX(1);
    transform: scaleX(1);
  }
</style>
