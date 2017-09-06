<template>
    <div id="sourceSelection">
        <h4>Select News source</h4>
        <select class="form-control" v-on:change="sourceChanged">
            <option :value="source.id" v-for="source in sources">{{ source.name }}</option>
        </select>
    </div>
</template>

<script>

export default {
  name: 'sourceSelection',
  data () {
      return {
          sources: [],
          source: ''
      }
  },
  methods:{
      sourceChanged: function (e) {
          for(let i=0; i<this.sources.length; i++){
              if(this.sources[i].id === e.target.value){
                  this.source = this.sources[i];
              }
          }

      }
  },
  created: function () {
      const api = 'https://newsapi.org/v1/sources?language=en';
      this.axios.get(`${api}`)
                .then(response => {
                    this.sources= response.data.sources
                })
  }
}

</script>

<style scoped>
</style>