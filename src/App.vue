<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'App',
}
</script>

<style lang="scss">
#app {
  width: 600px;
  margin: 30px auto;
}

ul, li {
  list-style-type: none;
}
</style>
