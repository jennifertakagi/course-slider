<template>
  <div id="section-container">
    <h1>{{this.title}}</h1>
    <h2 class="shadow-title">{{this.shadowTitle}}</h2>
    <hr class="title-line" />
  </div>
</template>

<script>
export default {
  name: 'SectionTitle',
  data() {
    return {
      title: 'Last Episodes',
      shadowTitle: 'Episodes',
    };
  },
};
</script>

<style scoped>
#section-container {
  margin: 7% 0 5%;
  position: relative;
}

h1 {
  font-size: 5rem;
  font-weight: 800;
  text-align: center;
}

.title-line {
  background-color: var(--color-primary);
  border: none;
  margin: 0 auto;
  width: 500px;
  height: 4px;
}

.shadow-title {
  position: absolute;
  bottom: 0;
  right: 16%;
  font-size: 12.5rem;
  color: var(--color-text-shadow);
  z-index: -1;
}

</style>
