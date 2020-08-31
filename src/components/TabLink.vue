<template>
  <li
    class="category-text"
    :class="{ active: hover }"
    :aria-label="category"
    :tabindex="index"
    @mouseover="emitHoverEvent"
    @mouseleave="emitEventLeave"
  >
    {{category}}
  </li>
</template>

<script>
export default {
  name: 'TabLink',
  data() {
    return {
      hover: false,
    };
  },
  props: {
    category: {
      type: String,
      required: true,
    },
    index: {
      type: Number,
      required: true,
    },
  },
  methods: {
    emitHoverEvent() {
      this.$emit('filterCategory', this.category);
    },
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
