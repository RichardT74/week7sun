<template lang="html">
<select @change = "selectedArticle">
<option selected disabled></option>

<option v-for="(article, index) in articles"
:value="index"> {{article.webTitle}} </option>

</select>
</template>

<script>


import { eventBus } from '@/main.js'


export default {
  name: 'article-select',
  props: ['articles'],
	methods: {
		selectedArticle(event) {
			const selectedIndex = event.target.value;
			eventBus.$emit('article-selected', selectedIndex);
		}
	}
  }
</script>
<style>

</style>
