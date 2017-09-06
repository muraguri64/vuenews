<template>
  <div class="container" id="app">
    <Sourceselection v-on:sourceChanged="sourceChanged"></Sourceselection>
    <Newslist :source="source"></Newslist>
  </div>
</template>

<script>
import Sourceselection from './components/sourceSelection'
import Newslist from './components/newsList'

export default {
  name: 'app',
  data () {
    return {
      source: ""
    }
  },
  methods: {
    sourceChanged: function(source) {
      this.source = source
    }
  },
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
