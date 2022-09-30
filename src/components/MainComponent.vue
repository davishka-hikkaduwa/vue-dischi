<template>
    <main>
        <div class="container">
            <div>
                <SelectComponent :options="genres" @select="filterByGenre"/>
                <SelectComponent :options="artists" @select="filterByArtist"/>
            </div>
            <AlbumContainerComponent :albums="albumsToDisplay"/>
        </div>
    </main>
</template>

<script>
    import AlbumContainerComponent from '@/components/AlbumContainerComponent.vue';
    import SelectComponent from '@/components/SelectComponent.vue';
    import axios from 'axios';

    export default {
        name: 'MainComponent',
        components: {
            AlbumContainerComponent,
            SelectComponent,
        },
        data(){
            return{
                apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
                albums: [],
                selectedGenre: '',
                selectedArtist: '',
            }
        },
        computed:{
            genres(){
                const array = [];
                this.albums.forEach(item=>{
                    if(!array.includes(item.genre)){
                        array.push(item.genre)
                    }
                })
                console.log({genres: array});
                return array;
            },
            artists(){
                const artists = this.albums.map((album)=>{
                    return album.author;
                });
                console.log('map:', artists);
                const uniqueArtists = artists.filter((name, index, array)=>{
                    return index === array.indexOf(name);
                });
                console.log('filter:', uniqueArtists);
                return uniqueArtists;
            },
            albumsToDisplay(){
                const array = [];
                this.albums.forEach(album => {
                    if(this.hasValidGenre(album) && this.hasValidArtist(album)){
                        array.push(album);
                    }
                });
                return array;
            }
        },
        created(){
            this.getAlbumData();
        },
        methods: {
            getAlbumData(){
                axios.get(this.apiUrl).then((response)=>{
                if (this.isResponseOK(response)){
                    console.log(response.data);
                    this.albums = response.data.response;
                }
                })
                .catch((e)=>{
                    console.log(e);
                });
            },
            isResponseOK({status}){
                return status === 200;
            },
            filterByGenre(genre){
                console.log('main received', genre);
                this.selectedGenre = genre;
            },
            filterbyArtist(artist){
                this.selectedArtist = artist;
            },
            hasValidGenre(album){
                return this.selectedGenre.length === 0 || this.selectedGenre === album.genre
            },
            hasValidArtist(album){
                return this.selectedArtist.length === 0 || this.selectedArtist === album.author
            },

        }
    }
</script>

<style scoped lang="scss">
main{
    background-color: #1e2d3b;
    color: #fff;
}
</style>