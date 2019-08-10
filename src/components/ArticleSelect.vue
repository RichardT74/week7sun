<template lang="html">
<select @change = "selectedArticle">

  <!-- <ul>
<list-component  v-for="(article, index) in articles" :article="article" :key="index"></list-component>
    </ul> -->
	</select>
</template>

<script>
import eventBus from '@/main.js'


export default {
  name: 'article-select',
  props: ['articles'],

  }
</script>
<style>

</style>
