<template lang="pug">
  main    
    section.section
      nav.nav.has-shadow
        .container          
          .field
            .control.is-expanded
              input.input.is-rounded(
                type="text",
                placeholder="Buscar canciones",
                v-model="searchQuery"
              )
            .field.is-grouped(style="margin-top:20px;")
              .control.is-expanded(style="text-align:center")
                a.button.is-info(@click="search") Buscar
                a.button.is-danger &times;
          p
            small {{ searchMessage }}
    pm-loader(v-show="isLoading")
    .container.results(v-show="!isLoading")
      .columns.is-multiline
        .column.is-one-quarter(v-for="t in tracks") 
          pm-track(
            :class="{ 'is-active' : t.id === selectedTrack }",
            :track="t", 
            @select="setSelectedTrack"
            )   
</template>

<script>
import trackService from '@/services/track.js'
import PmTrack from '@/components/Track.vue'
import PmLoader from '@/components/shared/Loader.vue'
export default {
  name: 'app',
  components:{  PmTrack,  PmLoader },
  data () {
    return {
      searchQuery: '',
      tracks: [],
      isLoading:false,
      selectedTrack:''
    }
  },

  computed: {
    searchMessage () {
      return `Encontrados: ${this.tracks.length}`
    }
  },

  methods: {
    search () {
      this.isLoading=true
      trackService.search(this.searchQuery)
      .then(res=>{
        this.tracks=res.tracks.items
        this.isLoading=false
      })
    },
    setSelectedTrack (id) {
      this.selectedTrack=id
    }
  }  
}
</script>

<style lang="scss">
  .results {
    margin-top: 50px;
  }
  .is-active{
    border: 3px #23d160 solid;
  }
</style>
