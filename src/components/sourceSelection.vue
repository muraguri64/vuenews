<template>
    <div id="sourceSelection">
        <div class="jumbotron">
            <h2><span class="glyphicon glyphicon-list-alt"></span>News List</h2>
            <h4>Select News source</h4>
            <select class="form-control" v-on:change="sourceChanged">
                <option :value="source.id" v-for="source in sources">{{ source.name }}</option>
            </select>
            <div v-if="source">
                <h6>{{ source.description }}</h6>
                <a :href="source.url" class="btn btn-primary" target="_blank">Go To Website</a>
            </div>
        </div>        
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
          this.$emit('sourceChanged', e.target.value);
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