<template>
  <div>
    <section class="hero is-primary">
      <div class="hero-body">
        <p class="title">Thunder Calculator</p>
        <p class="subtitle">Calculate how far the thunder is away</p>
      </div>
    </section>

    <section class="main-content section">
      <nuxt />
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          title: 'Home',
          icon: 'home',
          to: { name: 'index' },
        },
        {
          title: 'Inspire',
          icon: 'lightbulb',
          to: { name: 'inspire' },
        },
      ],
    }
  },
}
</script>
