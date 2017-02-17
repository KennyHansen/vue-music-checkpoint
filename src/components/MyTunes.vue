<template>
    <div class="my-tunes">
        <h4 class="black-text" > My Tunes</h4>
        <song :song="song" v-for="song in mySongList"></song>
    </div>
</template>

<script>
    import Song from './Song'
    import myTunesService from '../services/mytunes-service'
    export default {
        name: 'my-tunes',
        components: {
            Song
        },
        data() {
            return {
                mySongList: myTunesService.getTracks()
            }
        }
    }

</script>


<style>
    .my-tunes {
        /*display: inline-flex;*/
        min-height: 75px;
        min-width: 50%;
        background: palegreen;
        color: white;
        /*text-shadow: 0.5px 1px 3px black;*/
    }
</style>