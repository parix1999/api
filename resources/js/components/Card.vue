<template>
    <div class="row">
        <div v-for="film in films" :key="film.id" class="col-2">
            <div class="box-image">
                <img :src="'https://image.tmdb.org/t/p/w500/'+ film.poster_path" :alt="'poster film' + film.title">
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name:'Card',
        data() {
            return {
                films:[],
                img:[], 
            }
        },
        mounted() {
            axios.get('https://api.themoviedb.org/3/movie/popular?api_key=6ab3e57615f14eaaf5a85958841a5555').then((response) => {
                // i dati vengono presi
                // Non vanno pushati !!! 
                this.films = response.data.results;
            })            
        },
        
    }
</script>
