<template>
  <div class="about">
    <NewsArticle content="global-articles"/>
  </div>
</template>

<script>
import NewsArticle from '@/components/NewsArticle.vue';

export default {
  name: 'AboutView',
  components: {
    NewsArticle
  },
  // created(){
  //     this.openApi('global-articles')
  // },
  methods: {
  }
}
</script>


<style lang="">
  
</style>