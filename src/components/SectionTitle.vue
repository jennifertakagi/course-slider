<template>
  <header id="title-section">
    <div class="blue-ball" />
    <h1
      tabindex="0">
      {{this.title}}
      <span>
        {{this.subtile}}
      </span>
    </h1>
    <h2 class="shadow-title">{{this.shadowTitle}}</h2>
    <hr class="title-line" />
  </header>
</template>

<script>
export default {
  name: 'SectionTitle',
  data() {
    return {
      /**
       * Section's title
       */
      title: 'Last',
      /**
       * Section's subtitle
       */
      subtile: 'Episodes',
      /**
       * Section's shadow title
       */
      shadowTitle: 'Episodes',
    };
  },
};
</script>

<style scoped>
  #title-section {
    margin: 3% 0 1%;
    position: relative;
  }

  h1 {
    font-size: 5rem;
    font-weight: 800;
    text-align: start;
    margin-left: 20%;
  }

  h1 span {
    display: table;
  }

  .blue-ball {
    display: none;
  }

  .shadow-title {
    position: absolute;
    bottom: 20%;
    left: 4%;
    font-size: 5em;
    color: var(--color-text-shadow);
    z-index: -2;
  }

  .title-line {
    background-color: var(--color-primary);
    border: none;
    margin: 0 auto;
    width: 220px;
    height: 4px;
  }

  @media only screen and (min-width: 550px) {
    h1 {
      font-size: 5rem;
      text-align: left;
      margin-left: 15%;
    }

    h1 span {
      display: inline-block;
    }

    .title-line {
      margin-left: 15%;
      width: 340px;
    }

    .shadow-title {
      bottom: -38%;
      left: 13%;
      font-size: 7em;
    }
  }

  @media only screen and (min-width: 1207px) {
    h1 {
      font-size: 8rem;
      margin-left: 0;
      text-align: center;
    }

    .blue-ball {
      display: block;
      background-color: var(--color-primary);
      height: 554px;
      width: 554px;
      border-radius: 50%;
      z-index: -1;
      position: absolute;
      top: -7%;
      left: -4%;
    }

    .title-line {
      width: 500px;
    }

    .shadow-title {
      left: 30%;
      bottom: -32%;
      right: 0;
      font-size: 10em;
    }
  }
</style>
