<template lang="html">
  <ul v-if="country !== null">
    <li>{{ article.name }}</li>

  </ul>
</template>

<script>
export default {
  name: 'article-info',
  props: ['country']
}
</script>

<style lang="css" scoped>
.bold {
  font-weight: bold;
}
</style>
