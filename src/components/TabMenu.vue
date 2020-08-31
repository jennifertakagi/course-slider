<template>
  <nav id="menu-section" aria-label="mainmenulabel">
    <ul
      v-for="category in categories"
      :key="category"
    >
      <h2 id="mainmenulabel" class="visuallyhidden">Main Menu</h2>
      <li
        :aria-label="category"
        class="category-text"
      >
        {{category}}
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'TabMenu',
  data() {
    return {
    };
  },
  props: {
    categories: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
#menu-section {
  display: flex;
  justify-content: space-between;
  width: 50%;
  margin: 0 auto 5%;
}

.visuallyhidden {
  display: none;
}

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
