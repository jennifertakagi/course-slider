<template>
  <a
    role="button"
    aria-pressed="false"
    :aria-label="this.linkAriaLabel"
    :title="this.linkTitle"
    :href="this.linkURL"
    id="button-view-more"
  >
    {{linkLabel}}
  </a>
</template>

<script>
export default {
  name: 'CTA',
  data() {
    return {
      /**
       * Link's label
       */
      linkLabel: 'View More',
      /**
       * Link's arial label
       */
      linkAriaLabel: 'Click to view more episodes',
      /**
       * Link's title
       */
      linkTitle: 'Clicking on this button you will navigate to Valtech website',
      /**
       * Link's url (to use on href)
       */
      linkURL: '//www.valtech.com/insights/',
    };
  },
};
</script>

<style scoped>
  #button-view-more {
    text-decoration: none;
    text-transform: uppercase;
    font-weight: 600;
    color: var(--color-text-base);
    width: 146px;
    height: 50px;
    padding-top: 10px;
    margin: 5% auto 1%;
    text-align: center;
    border: 2px solid var(--color-text-base);
    letter-spacing: 1px;
  }

  #button-view-more:hover {
    color: var(--color-box-base);
    background-color: var(--color-text-base);
  }
</style>
