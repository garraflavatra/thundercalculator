<template>
  <b-steps mobile-mode="compact">
    <b-step-item label="Count">
      <div class="columns">
        <div class="column">
          <p class="notification">
            First of all, count the seconds between the lightning and the
            thunder. You could use this stopwatch:
          </p>
        </div>
        <div class="column">
          <Stopwatch />
        </div>
      </div>
    </b-step-item>
    <b-step-item label="Calculate">
      <div class="columns is-desktop">
        <div class="column">
          <p class="notification">
            How many seconds did you count? Slide to choose:
          </p>
        </div>
        <div class="column">
          <div class="box">
            <b-field label="Seconds">
              <b-slider
                size="is-large"
                v-model.number="seconds"
                value="5"
                :max="30"
              ></b-slider>
            </b-field>
          </div>
        </div>
      </div>
    </b-step-item>
    <b-step-item label="Result">
      <div class="columns is-desktop">
        <div class="column">
          <p class="notification">Here is your result:</p>
        </div>
        <div class="column">
          <div class="box">
            The thunder should be
            <span class="tag is-primary is-medium">{{ kms }}</span>
            kilometres away. <br />
            That is
            <span class="tag is-primary is-medium">{{ miles }}</span>
            yards.
          </div>
        </div>
      </div>
    </b-step-item>
  </b-steps>
</template>

<style scoped>
.columns > .column > * {
  height: 100%;
}
</style>

<script>
import Stopwatch from '../components/Stopwatch.vue'

export default {
  name: 'Home',

  components: {
    Stopwatch,
  },

  data() {
    return {
      seconds: 0,
    }
  },

  computed: {
    kms() {
      return Math.round((this.seconds / 3) * 10) / 10
    },
    miles() {
      return Math.round((this.kms / 1.609344) * 10) / 10
    },
  },
}
</script>
