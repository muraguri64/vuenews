<template>
  <div class="container" id="app">
    <Sourceselection></Sourceselection>
    <Newslist></Newslist>
  </div>
</template>

<script>
import Sourceselection from './components/sourceSelection'
import Newslist from './components/newsList'

export default {
  name: 'app',
  components: {
    Sourceselection,
    Newslist
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
</style>
