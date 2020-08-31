<template>
  <div id="app">
    <SectionTitle />
    <TabMenu
      :categories="uniqueCategoriesList"
      :categoryActive="categoryActive"
      @filterByCategory="filterCategory"
    />
    <div class="card-container">
      <Card
        v-for="episode in episodesList"
        :key="episode.id"
        :duration="episode.duration"
        :jobTitle="episode.jobTitle"
        :name="episode.name"
        :title="episode.title"
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
      /**
       * List of all podcast's episodes
       */
      episodesList: null,
      /**
       * List of the unique podcast's categories
       */
      uniqueCategoriesList: [],
      /**
       * The active category
       */
      categoryActive: null,
    };
  },
  mounted() {
    this.episodesList = api;
    this.uniqueCategoriesList = this.getUniqueCategories;
    this.filterCategory('new');
  },
  computed: {
    /**
     * Gets the unique podcast's categories
     * @returns {Array} array with the unique categories
     */
    getUniqueCategories() {
      const allCategories = (api || []).reduce((uniqueCategories, episode) => {
        if (episode && episode.categories && episode.categories.length) {
          uniqueCategories.push(...episode.categories);
        }
        return uniqueCategories;
      }, []);
      return [...new Set(allCategories)];
    },
  },
  methods: {
    /**
     * Filters episode's by the category, and updates
     * the the 'episode' data
     * @param {String} value category to filter
     * @returns {void}
     */
    filterCategory(value = 'new') {
      if (!value) {
        this.categoryActive = 'new';
        this.episodesList = api;
        return;
      }
      this.categoryActive = value;
      this.episodesList = (this.episodesList || []).filter(episode => episode.categories.includes(value));
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
    grid-template-columns: repeat(4, 1fr);
    overflow-x: hidden;
    margin-left: 15%;
  }

  @media only screen and (min-width: 1207px) {
    .card-container {
      margin-left: 0;
    }
  }
</style>
