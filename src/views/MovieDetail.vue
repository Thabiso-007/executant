<template>
    <div class="movie-detail">
        <h1>Information</h1>
        <h2 class="title">{{ movie.Title }}</h2>
        <div class="group">
            <img :src="movie.Poster" alt="Movie poster" class="featured-img"/>
            <div class="group-items">
                <p>Type:  {{ movie.Type }}</p>
                <p>Year released:  {{ movie.Year }}</p>
                <p>Writer:  {{ movie.Writer }}</p>
                <p>Cast:  {{ movie.Actors }}</p>
                <p>Director:  {{ movie.Director }}</p>
                <p>Genre:  {{ movie.Genre }}</p>
                <p>Coutry:  {{ movie.Country }}</p>
                <p>Language:  {{ movie.Language }}</p>
                <p>Duration:  {{ movie.Runtime }}</p>
            </div>
        </div>            
        <p class="desc">{{ movie.Plot }}</p>
    </div>
</template>
 
<script> 
import { ref, onBeforeMount } from 'vue';
import { useRoute } from 'vue-router';
import env from '@/env';

export default {
    setup() {
        const movie = ref({});
        const route = useRoute();

        onBeforeMount(() => {
            fetch(`https://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`)
                .then(response => response.json())
                .then(data => {
                    movie.value = data 
                })
            }
        )

        return {
            movie    
        }
    }
}
</script>

<style lang="scss" scoped>
.movie-detail {
    padding: 16px;

    h1 {
        color: #FFF;
        font-size: 40px;
    }
    .title {
        color: #FFF;
        font-size: 32px;
        font-weight: 600;
        margin-bottom: 16px;
        text-align: center;
    }

    .group {
        display: flex;

        .featured-img {
            display: block;
            max-width: 600px;
            margin-bottom: 16px;
            height: 300px;
        }
        .group-items {
            margin-left: 10px;

            p {
                font-size: 20px;
                color: #FFF;
                margin-bottom: 10px;
            }       
        }

    }

    .desc {
        color: #FFF;
        font-size: 18px;
        line-height: 1.4;
    }
}
</style>