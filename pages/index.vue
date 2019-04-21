<template lang="html">
    <div class="container">
        <header>
            <h1 class="title">Albums de la página</h1>
        </header>
        <div class="columns is-multiline">
            <AlbumCard :album='album' v-for='album in albums' :key="album.id" />
        </div>
    </div>
</template>
<script>
import axios from 'axios'
import env from '../config/env'
import AlbumCard from '../components/AlbumCard'
export default {
    name: 'IndexPage',
    components: {
        AlbumCard
    },
    data(){
        return {
            albums:[]
        }
    },
    created: async function(){
        let response = await axios.get(`${env.endpoint}/albums`)
            this.albums = response.data
    }
}
</script>