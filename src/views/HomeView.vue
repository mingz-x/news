<template>
  <div class="home">
    <NewsArticle content="articles"/>
  </div>
</template>

<script>
// @ is an alias to /src
import NewsArticle from '@/components/NewsArticle.vue';

export default {
  name: 'HomeView',
  components: {
    NewsArticle
  },
  // created(){
  //     this.openApi('articles')
  // },
  methods: {
  }
}
</script>

<style lang="">
  
</style>
