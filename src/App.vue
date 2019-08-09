<template lang="html">
  <div>
    <article-select :articles="articles" />
  </div>
</template>

<script>
import { eventBus } from '@/main.js';
import ArticleSelect from '@/components/ArticleSelect.vue'
import ArticleInfo from '@/components/ArticleInfo.vue'


export default {
  components: {
    'article-select': ArticleSelect,
    'article-info': ArticleInfo
  },

  data() {
      return {
        articles: [],
        selectedArticle: null
      };
    },
    mounted() {
    eventBus.$on('article-selected', (selectedIndex) => {
      this.selectedArticle = this.countries[selectedIndex];
    });
    fetch('https://content.guardianapis.com/search?q=brexit&format=json&api-key=test')
      .then(response => response.json())
      .then(jsonResponse => this.articles = jsonResponse.response.results);
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
