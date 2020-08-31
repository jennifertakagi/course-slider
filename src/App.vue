<template>
  <div id="app">
    <SectionTitle />
    <TabMenu
      :categories="uniqueCategoriesList"
      @filterByCategory="filterCategory"
    />
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
    <CTA />
  </div>
</template>

<script>

import api from './services/api';
import SectionTitle from './components/SectionTitle';
import Card from './components/Card';
import CTA from './components/CTA';
import TabMenu from './components/TabMenu';

export default {
  name: 'App',
  components: {
    SectionTitle,
    Card,
    CTA,
    TabMenu,
  },
  data() {
    return {
      courseList: null,
      uniqueCategoriesList: [],
    };
  },
  mounted() {
    this.courseList = api;
    this.uniqueCategoriesList = this.getUniqueCategories;
  },
  computed: {
    getUniqueCategories() {
      const allCategories = (api || []).reduce((uniqueCategories, course) => {
        if (course && course.categories && course.categories.length) {
          uniqueCategories.push(...course.categories);
        }
        return uniqueCategories;
      }, []);
      return [...new Set(allCategories)];
    },
  },
  methods: {
    filterCategory(value) {
      if (!value) {
        this.courseList = api;
        return;
      }
      this.courseList = this.courseList.filter(course => course.categories.includes(value));
    },
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
