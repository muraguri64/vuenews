<template>
    <div id="newsList">
        <ul class="media-list">
            <li class="media" v-for="article in articles">
                <div class="media-left">
                    <a :href="article.url" target="_blank">
                        <img class="media-object" :src="article.urlToImage" alt="image">
                    </a>
                </div>    
                <div class="media-body">
                    <a :href="article.url" target="_blank">
                        <h4 class="media-heading">{{ article.title }}</h4>
                    </a>
                    <h5><b><i>by ({{ article.author }})</i></b></h5>
                    <p>{{ article.description }}</p>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>

export default {
  name: 'newsList',
  props: ['source'],
  data () {
      return{
          articles: []
      }      
  },
  methods: {
      updateSource: function (source) {
          const api = `https://newsapi.org/v1/articles?source=${source}&apiKey=dcb8c57a9af44e2ea3e847f0e71e1ca9`
          this.axios.get(api)
                    .then(response => {
                        this.articles=response.data.articles
                    });
      }
  },
  watch: {
      source: function (val){
          this.updateSource(val)
      }
  }
}

</script>

<style scoped>
    .media-object{
        width: 100px;
        height: 100px;
        padding: 0px;
    }
    .media{
        border-top: 1px solid lightgrey;
        padding-top: 20px;
    }
</style>