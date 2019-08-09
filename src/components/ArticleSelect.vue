<template lang="html">
  <select @change="articleSelected">
    <option selected disabled>-</option>
    <option v-for="(article, index) in articles" :value="index">{{ article.webTitle }}</option>
  </select>
</template>

<script>
import { eventBus } from '@/main.js';
export default {
  name: 'article-select',
  props: ['articles'],
  methods: {
    articleSelected(e) {
      const selectedIndex = e.target.value;
      eventBus.$emit('article-selected', selectedIndex);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
