<template>
    <div class="card-album">
        <img class="w-100" :src="info.poster" :alt="info.title">

        <p> {{ info.title }} </p>
    </div>
</template>

<script>
    export default {
        name: 'AlbumCardComponent',
        props: {
            info: Object,
        }
    }
</script>

<style scoped lang="scss">
    .card-album{
        display: flex;
        flex-direction: column;
        padding: 10px;
        background-color: #2e3a46;
        color: #fff;
        text-align: center;
        p{
            color: #fff;
            text-transform: uppercase;
            margin-top: 8px
        }
    }
</style>