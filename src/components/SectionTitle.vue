<template>
  <header id="title-section">
    <div class="blue-ball" />
    <h1>{{this.title}}</h1>
    <h2 class="shadow-title">{{this.shadowTitle}}</h2>
    <hr class="title-line" />
  </header>
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
#title-section {
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


.blue-ball {
  background-color: var(--color-primary);
  height: 554px;
  width: 554px;
  border-radius: 50%;
  z-index: -2;
  position: absolute;
  top: -7%;
  left: -4%;
}

</style>
