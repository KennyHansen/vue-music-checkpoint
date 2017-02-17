<template>
    <div class="all-tunes">
        <h4>Itunes</h4>
        <form @submit.prevent="searchByArtist">
            <input type="text" v-model="artist">
            <button>Search</button>
        </form>
        <!--{{songList}}-->
        <song :song="song" v-for="song in songList"></song>
    </div>
</template>

<script>
    import itunesService from '../services/itunes-service'
    import Song from './Song'
    export default {
        name: 'itunes',
        data() {
            return {
                artist: '',
                songList: []
            }
        },
        components: {
            Song
        },
        methods: {
            searchByArtist() {
                console.log(this.artist)
                itunesService.getMusicByArtist(this.artist).then(res => {
                    console.log(res)
                    res.json().then(music => {
                        console.log(music)
                        this.songList = music.results.map(function (song) {
                            return {
                                title: song.trackName,
                                albumArt: song.artworkUrl60,
                                artist: song.artistName,
                                collection: song.collectionName,
                                price: song.collectionPrice,
                                preview: song.previewUrl,
                                id: song.trackId
                            };
                        })

                        this.artist = ''
                    }).catch(console.log("Nope"))
                })
            }
        }
    }

</script>


<style>
    /**
* YOU SHOULD PROBABLY MAKE THIS LOOK BETTER :)
* BOOTSTRAP IS FOR THE WEAK FLEXBOX IS KING
* -- McCall
**/
    
    .all-tunes {
        /*display: inline-flex;*/
        min-height: 75px;
        min-width: 50%;
        background: palegreen;
        color: white;
        text-shadow: 0.5px 1px 3px black;
    }
</style>