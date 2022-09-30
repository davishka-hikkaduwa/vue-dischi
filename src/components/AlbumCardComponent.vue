<template>
    <div class="card-album">
        <img class="w-100" :src="info.poster" :alt="info.title" @error="replaceWrongImageUrl">
        <p class="title"> {{ info.title }} </p>
        <p> {{ info.author }} </p>
        <p> {{ info.year }} </p>
    </div>
</template>

<script>
    import errorImage from '@/assets/img/logo.png'
    export default {
        name: 'AlbumCardComponent',
        props: {
            info: Object,
        },
        methods: {
            replaceWrongImageUrl(e){
                console.log('errore');
                e.target.src = errorImage;
            }
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
            text-transform: uppercase;
            margin-bottom: 8px;
            &.title{
                color: #fff;
                margin-top: 6px;
                margin-bottom: 4px;


            }
        }
    }
</style>