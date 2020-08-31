<template>
  <div id="card">
    <h2>{{this.title}}</h2>
    <p>{{this.name}}</p>
    <p class="job-title-text">{{this.jobTitle}}</p>
    <div class="play-row">
      <img
        src="@/assets/icons/play.svg"
        alt="Button to play the podcast episode"
      />
      <div>
        <img
          class="clock-img "
          src="@/assets/icons/clock.svg"
          alt="Clock icon representing episode duration"
        />
        <span>{{this.duration}}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    duration: {
      type: String,
      required: true,
    },
    jobTitle: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    categories: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
#card {
  font-weight: 700;
  background-color: var(--color-box-base);
  border-radius: 4px;
  padding: 10%;
  position: relative;
  width: 262px;
  height: 342px;
}

#card:hover {
  box-shadow: 0px 0px 20px #0000001A;
}

#card > h2, p {
  text-align: left;
  padding: 5px 0;
}

#card > h2 {
  font-weight: 100;
  text-transform: uppercase;
  color: var(--color-text-base);
}

.job-title-text {
  color: var(--color-text-complement);
}

.play-row {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  position: absolute;
  bottom: 0;
  margin-bottom: 5%;
  font-weight: 100;
}

.clock-img {
  width: 32px;
  vertical-align: middle
}
</style>
