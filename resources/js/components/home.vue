<template>
    <div>
        <!-- Componente con le card film  -->
        <Card :films="films"/>
        <!-- Componente che mostra dentro il click della card film -->
        <Show :films="films"
        :descriptions="descriptions"
        :img="img"
        />
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
                descriptions:[],
                img:[],
            }
        },
        mounted() {
            axios.get('https://api.themoviedb.org/3/movie/popular?api_key=6ab3e57615f14eaaf5a85958841a5555').then((response) => {
                // i dati vengono presi
                // Non vanno pushati !!! 
                this.films = response.data.results;

                for (let i = 0; i < this.films.length; i++) {
                    const element = this.films[i].overview;
                    this.descriptions.push(element); 
                }

                for (let x = 0; x < this.films.length; x++) {
                    const listaUrl = this.films[x].poster_path;
                    this.img.push(listaUrl); 
                }
                
                
            })            
        },
        
    }
</script>
