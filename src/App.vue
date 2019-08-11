<template>
 <div id="app">
   <header>
     <article-select :Articles_prop ="articles"/>
     <display-article :article ="selectedArticle"/>
   </header>
 </div>
</template>
<script>
import {eventBus} from '@/main.js';
import ArticleSelect from '@/components/ArticleSelect.vue';
import DisplayArticle from '@/components/ArticleDisplay.vue'
export default {
 components:{
   'article-select': ArticleSelect,
   'display-article': DisplayArticle
 },
 data(){
   return {
     articles: [],
     selectedArticle: null
   };
 },
 mounted() {
   eventBus.$on('article-selected', (selectedIndex) => {
     this.selectedArticle = this.articles[selectedIndex];
   });
   fetch('https://content.guardianapis.com/search?q=brexit&format=json&api-key=test')
   .then(res => res.json())
   .then(resjson =>   this.articles = resjson.response.results);
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
