<template lang="pug">
  section.hero.is-success
    .hero-head
      header.navbar
        .container.navbar-menu
          .navbar-start
            .navbar-item
              strong 📻  Platzi Music
          .navbar-end.nav-menu  
            router-link.navbar-item(to="/") Buscar
            router-link.navbar-item(to="about") Nosotros            

    .hero-body
      .container.has-text-centered
        h1.title Platzi Music
        h2.subtitle Canciones que estan Vue-nisimas!  
        PmPlayer      
</template>

<script>
import PmPlayer from '@/components/Player.vue'
export default {
  components: { PmPlayer }
}
</script>
<style lang="scss" scoped>
  a.navbar-item:focus{
    background-color: transparent;
    color: black
  }
</style>