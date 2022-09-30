<template>
    <div>
        <div class="album-container">
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