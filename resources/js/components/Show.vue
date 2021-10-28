<template>
    <div class="row align-items-center">
        <div class="col-6">
            <div class="show-image">
                <div class="img">
                    <img :src="'https://image.tmdb.org/t/p/w500/' + img[0]" alt="">
                </div>
            </div>
        </div>

        <div class="col-6">
            <div class="description">
                {{ descriptions[0] }}
            </div>
        </div>
    </div>
    
</template>

<script>
 
    export default {
        name:'Show',
        props: {
            films: Array,
            descriptions: Array,
            img: Array
        },
        data() {
            return {
                showFilm: this.films,
            }
        },
        mounted() {
            console.log(this.showFilm); 
        }
    }
</script>
