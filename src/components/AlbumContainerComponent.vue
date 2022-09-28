<template>
    <div>
        <div class="album-container">
            <div class="row">
                <div class="col-12">
                    <div class="dropdown">
                        <button class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                            Dropdown button
                        </button>
                        <ul class="dropdown-menu">
                            <li>
                                <a class="dropdown-item" href="#" v-for="genre in list" :key="genre.id"></a>
                            </li>
                        </ul>
                    </div>              
                </div>
            </div>
            <div class="row">
                <div class="dh-fifth-col" v-for="album in albums" :key="album.title">
                    <AlbumCardComponent :info="album"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import AlbumCardComponent from './AlbumCardComponent.vue';

    export default {
        name: "AlbumContainerComponent",
        props: {
            albums: Array,
        },
        components: { 
            AlbumCardComponent
        },
}
</script>

<style scoped lang="scss">
    .album-container{
        padding-top: 50px;
        padding-bottom: 100px;
        .row{
            row-gap: 20px;
        }

    }


    .dh-fifth-col{
        width: calc(100% / 5);
    }
</style>