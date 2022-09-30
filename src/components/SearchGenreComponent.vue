<template>
    <div>
                <!-- <div class="dropdown">
                        <button class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">                            Select Genre
                    </button>
                    <ul class="dropdown-menu">
                        <li>
                            <a class="dropdown-item" href="#" v-for="genre in list" :key="genre.id"></a>
                        </li>
                     </ul>
                </div>               -->
        <select v-model="userSelection">
            <option value="">Nessuno Selezionato</option>
            <option v-for="option in options" :key="option" :value="option">
                {{ option }}
            </option>
        </select>        
    </div>
</template>

<script>
    export default {
        name: 'SearchGenreComponent',
        data(){
            return {
                userSelection: '',
            }
        },
        props: {
            options: Array,
        },
        methods: {
            onChange(){
                console.log(this.userSelection);
                this.$emit('selectedGenre', this.userSelection)
            }
        }
    }
</script>

<style scoped lang="scss">

</style>