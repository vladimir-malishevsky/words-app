<template>
  <div class="home">
    <div class="home__main">
      <div class="home__title">Words-App</div>
    </div>
    <div class="home__description">
      <button @click="go()">Check it</button>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Home',
  methods: {
    go() {
      this.$router.push('/translate')
    }
  }
}
</script>

<style scoped lang="scss">
.home {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;

  .home__main {
    width: 100%;
    height: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    background: pink;
    .home__title {
      font-size: 8rem;
      font-weight: bold;
      color: #2C3E50;
    }
  }
  .home__description {
    width: 100%;
    height: 50%;
    background: #2C3E50;
  }
}
</style>