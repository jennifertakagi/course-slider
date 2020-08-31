<template>
  <main id="card-section">
    <h3>{{this.title}}</h3>
    <p>{{this.name}}</p>
    <p class="job-title-text">{{this.jobTitle}}</p>
    <div class="play-row">
      <button
        :aria-label="this.buttonPlayAriaLabel"
        :title="this.buttonPlayAriaLabel"
      />
      <div class="duration-box">
        <img
          class="clock-img "
          src="@/assets/icons/clock.svg"
          alt="Clock icon representing episode duration"
        />
        <span :aria-label="this.buttonDurationAriaLabel">
          {{this.duration}}
        </span>
      </div>
    </div>
  </main>
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
  computed: {
    buttonPlayAriaLabel() {
      return `Click here to play episode about ${this.title}`;
    },
    buttonDurationAriaLabel() {
      return `The episode duration is ${this.duration}`;
    },
  },
};
</script>

<style scoped>
#card-section {
  font-size: 1.3rem;
  font-weight: 700;
  background-color: var(--color-box-base);
  border-radius: 4px;
  padding: 32px;
  position: relative;
  width: 262px;
  height: 342px;
  text-align: left;
}

#card-section:hover {
  box-shadow: 0px 0px 20px #0000001A;
}

#card-section > h3 {
  font-size: 2.8rem;
  font-weight: 100;
  text-transform: uppercase;
  color: var(--color-text-base);
  padding-bottom: 16px;
}

#card-section p:first-of-type {
  font-size: 1.6rem;
}

.job-title-text {
  color: var(--color-text-complement);
  font-weight: 100;
  font-size: 1.3rem;
  padding-top: 4px;
}

.play-row {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  position: absolute;
  bottom: 0;
  margin-bottom: 32px;
  font-weight: 100;
  width: 85%;
}

button {
  background-image: url("../assets/icons/play.svg");
  background-repeat: no-repeat;
  border: none;
  background-color: transparent;
  width: 40px;
  height: 40px;
  cursor: pointer;
}

.clock-img {
  width: 35px;
  margin-right: 5px;
  vertical-align: middle
}
</style>
