<template>
  <div id="app">
    <SectionTitle />
    <div class="card-container">
      <Card
        v-for="course in courseList"
        :key="course.id"
        :duration="course.duration"
        :jobTitle="course.jobTitle"
        :name="course.name"
        :title="course.title"
        :categories="course.categories"
      />
    </div>
  </div>
</template>

<script>

import api from './services/api';
import SectionTitle from './components/SectionTitle';
import Card from './components/Card';

export default {
  name: 'App',
  components: {
    SectionTitle,
    Card,
  },
  data() {
    return {
      courseList: null,
    };
  },
  mounted() {
    this.courseList = api;
  },
};
</script>

<style>
#app {
  display: grid;
  align-items: center;
  justify-content: center;
}

.card-container {
  display: grid;
  grid-column-gap: 50px;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
</style>
