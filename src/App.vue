<template lang="pug">
  #app    
    PmHeader  
    
    router-view
    
    pm-footer
</template>

<script>
import PmFooter from '@/components/layouts/Footer.vue'
import PmHeader from '@/components/layouts/Header.vue'

export default {
  name: 'app',
  components:{  PmFooter, PmHeader },
}
</script>

<style lang="scss">
  @import './scss/main.scss';

  .results {
    margin-top: 50px;
  }
  .is-active{
    border: 3px #23d160 solid;
  }
</style>
