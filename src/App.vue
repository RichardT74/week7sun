<template>


    <div class="main-container">

  <h1>Guardian Articles</h1>

  </div>
</template>

<script>
import { eventBus } from '@/main.js'
import ArticleSelect from '@/components/ArticleSelect.vue'


export default {
  components: {
    'article-select': ArticleSelect
},

data(){
  return {
    articles: [],
  }
},
  mounted(){
    fetch('https://content.guardianapis.com/search?q=brexit&format=json&api-key=test')
    .then(res => res.json())
    .then(resjson => this.articles = resjson.response.results);
  }
}
</script>

/* <style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style> */
