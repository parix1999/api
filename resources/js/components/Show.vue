<template>
    <div class="row align-items-center">
        <div class="col-6">
            <div class="show-image">
                <!-- <img :src="this.films[0].poster_path" alt=""> -->
                <div class="img"></div>
            </div>
        </div>

        <div class="col-6">
            <div class="description">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Officia ea dolor eos nemo explicabo nesciunt error quia sint alias ipsam voluptatem cupiditate, non debitis fugiat doloremque perferendis velit facilis praesentium?
            </div>
        </div>
    </div>
    
</template>

<script>
 
    export default {
        name:'Show',
        props: {
            films: Array, 
        },
        data() {
            return {
                showFilm:[],
            }
        },
        mounted() {
            this.showFilm = this.films;
            console.log(this.showFilm); 
        }
    }
</script>
