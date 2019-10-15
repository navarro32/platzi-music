<template lang="pug">
    .card
        .card-image
            figure.image.is-4by3
                img(:src="track.album.images[0].url")
        .card-content
            .media
                .media-left
                    figure.image.is-48x48
                        img(:src="track.album.images[0].url")
                .media-content
                    p.title.is-6
                        b {{ track.name }}
                    p.subtitle.is-6 {{ track.artists[0].name }}
                .content
                    small {{ track.duration_ms }}
                    nav.level
                        .level-left
                            a.level-item
                                span.icon.is-small(@click="selectTrack") ▶️
</template>

<script>
    export default {
        props:{
            track:{ type: Object, required: true }
        },
        methods:{
            selectTrack () {
                this.$emit('select', this.track.id)
                this.$bus.$emit('set-track', this.track)
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>