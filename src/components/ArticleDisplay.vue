<template lang="html">
<ul v-if="article !== null">
 <li>{{article.webTitle }}</li>
 <li>{{article.sectionId}}</li>
 <li>{{article.sectionName}}</li>
 <li>{{article.webPublicationDate}}</li>
 <li>{{article.webUrl}}</li>
</ul>
</template>
<script>
export default {
 name: 'display-article',
 props: ['article']
}
</script>
<style lang="css" scoped>
</style>
