<template>
  <div class="box sw">
    <h2 class="sw-title">Stopwatch</h2>
    <span class="tag is-primary is-medium sw-secs block">
      {{ timeString }}
    </span>
    <b-button @click="start" type="is-success">Start</b-button>
    <b-button @click="stop" type="is-danger">Stop</b-button>
    <b-button @click="reset">Reset</b-button>
  </div>
</template>

<script>
export default {
  name: 'Stopwatch',

  data() {
    return {
      hr: 0,
      min: 0,
      sec: 0,
      stoptime: true,
      timeString: '',
    }
  },

  methods: {
    start() {
      if (this.stoptime === true) {
        this.stoptime = false
        this.cycle()
      }
    },
    stop() {
      if (this.stoptime === false) {
        this.stoptime = true
      }
    },
    cycle() {
      if (this.stoptime === false) {
        this.sec = parseInt(this.sec)
        this.min = parseInt(this.min)
        this.hr = parseInt(this.hr)

        this.sec++

        if (this.sec === 60) {
          this.min++
          this.sec = 0
        }
        if (this.min === 60) {
          this.hr++
          this.min = 0
          this.sec = 0
        }

        if (this.sec < 10 || this.sec === 0) {
          this.sec = '0' + this.sec
        }
        if (this.min < 10 || this.min === 0) {
          this.min = '0' + this.min
        }
        if (this.hr < 10 || this.hr === 0) {
          this.hr = '0' + this.hr
        }

        this.timeString = this.hr + ':' + this.min + ':' + this.sec

        setTimeout(() => {
          this.cycle()
        }, 1000)
      }
    },
    reset() {
      this.timeString = '00:00:00'
      this.stoptime = true
      this.hr = 0
      this.sec = 0
      this.min = 0
    },
  },
}
</script>

<style>
.sw .sw-title {
  color: #363636;
  display: block;
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 0.5em;
}
.sw .sw-secs {
  display: block;
  text-align: center;
}
</style>
