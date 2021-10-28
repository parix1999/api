<template>
    <div class="row">
        <div v-for="film in films" :key="film.id" class="col-2">
            <div class="box-image">
                {{ film.title }}
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
            }
        },
        mounted() {
            console.log('Component mounted.')
            axios.get('https://api.themoviedb.org/3/movie/popular?api_key=6ab3e57615f14eaaf5a85958841a5555').then((response) => {
                // i dati vengono presi
                // Non vanno pushati !!! 
                this.films = response.data.results;
                console.log(this.films); 
            });
        },
        
    }
</script>
