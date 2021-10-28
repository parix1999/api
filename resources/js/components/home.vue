<template>
    <div>
        <!-- Componente con le card film  -->
        <div :class="visualizzazione()">
            <Card :films="films"
            :flag="flag"
            @visualizza="change"
            />
        </div>
        <div :class="visualizzazioneDue()">
            <!-- Componente che mostra dentro il click della card film -->
            <Show :films="films"
            :descriptions="descriptions"
            :img="img"
            />
        </div>
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

                flag:true,
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

        methods: {
            change() {
                if (this.flag == true) {
                    this.flag = false; 
                }
            },

            visualizzazione() {
                if (this.flag == true) {
                    return 'visual';
                } else {
                    return 'noVisual';
                }
            },

            visualizzazioneDue() {
                if (this.flag == true) {
                    return 'noVisual';
                } else {
                    return 'visual';
                }
            }
        }
        
        
    }
</script>
