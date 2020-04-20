<template>
  <div>
    <meta name="referrer" content="never">
    <div id="article" v-html="content" />
    <Catalogue id="toc" selector="#article" />
  </div>
</template>

<script>
import Catalogue from './Catalogue.vue'
export default {
  components: { Catalogue },
  data () {
    return {
      content: ''
    }
  },
  mounted () {
    const url = 'https://www.biubiubius.com/blog/article?date=1581349734534'
    fetch(url).then(res => res.json()).then(data => {
      this.content = data.content
    })
  }
}
</script>

<style lang="stylus" scoped>
  #toc
    position fixed
    right 0
</style>