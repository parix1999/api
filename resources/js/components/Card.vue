<template>
    <div class="row justify-content-center">
        <div v-for="film in films" :key="film.id">
            <div class="col-6 col-sm-4 col-md-3 col-lg-2">
                <div class="box-image">
                    <img :src="'https://image.tmdb.org/t/p/w500/'+ film.poster_path" :alt="'poster film' + film.title">  
                </div>
            </div>
        </div>
        
       
    </div>
</template>

<script>
    export default {
        name:'Card',
        props: {
            films: Array,
        },
        
        
    }
</script>
