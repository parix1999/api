<template>
    <div>
        <Card :films="films"/>
        <Show />
    </div>
</template>

<script>
    import Card from './Card.vue';
    import Show from './Show.vue';
    export default {
        name:'Home',
        components: {
            Card,
            Show,
        },
        data () {
            return {
                films:[],
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
