<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col-2">
        <h1 class="bg-dark text-white" style="height: 400px">Hello Sqoo</h1>
      </div>
      <div id="portfolio" class="col-8">
        <h3>Portfolio</h3>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'app',
  components: {

  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
  body {
    background-image: url("assets/background.png");
    background-repeat: repeat;
  }
</style>
