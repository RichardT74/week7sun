<template>


    <div id="app">

  <h1>Guardian Articles</h1>
  <article-select :articles ="articles"/>
  <article-detail :article ="selectedArticle"></article-detail>

  </div>
</template>
<script>
import { eventBus } from '@/main.js'
import ArticleSelect from '@/components/ArticleSelect.vue';
import ArticleDetail from '@/components/ArticleDetail.vue';


export default {
  data(){
    return {
      articles: [],
      selectedArticle: null}
  },
  components: {
    'article-select': ArticleSelect,
      'article-detail': ArticleDetail
},
  mounted(){

    eventBus.$on('article-selected', (selectedIndex) => {
      this.selectedArticle = this.articles[selectedIndex];
    });

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
