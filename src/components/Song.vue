<template>
    <div class='card black'>
        <div class="flex-it">
            <img :src="song.albumArt">
            <h3>{{song.title}}</h3>
            <audio ref="player" controls preload="none">
                <source :src="song.preview" type="audio/mp4" />
            </audio>
        </div>

        <p>Album: {{song.collection}}</p>
        <p>By: {{song.artist}}</p>
        <p>Price: ${{song.price}}</p>
        <button v-if="!song.isAdded" class="btn btn-primary" @click="addSong">Add</button>
        <button v-if="song.isAdded" class="btn btn-warning" @click="removeSong">Remove</button>
    </div>
</template>

<script>
import myTunesService from '../services/mytunes-service'
    export default {
        name: 'song',
        props: ['song'],
        mounted() {
            this.$watch('song', () => {
                this.$refs.player.load()
            })
        },
        methods: {
            addSong() {
                console.log(this.song)
                myTunesService.addTrack(this.song)
            },
            removeSong() {
                console.log(this.song)
                myTunesService.removeTrack(this.song)
            }
        }
    }

</script>

<style>
    .flex-it {
        display: flex;
        flex-direction: row;
        justify-content: space-around;
    }
    .my-tunes{
        display: inline-block;
        min-height: 500px;
        min-width: 50%;
        background: palegreen;
    }
    .itunes{
        display: inline-block;
        background: darkslategray;
        min-height: 500px;
        min-width: 45%;
    }
</style>