<template>
    <div class="movie-detail">
        <h2>{{ movie.Title }}</h2>
        <p>{{ movie.Year }}</p>
        <img :src="movie.Poster" alt="Movie poster" class="featured-img"/>
        <div class="info">
            <div class="movie-info">
                <p>Cast: {{ movie.Actors }}</p>
                <p>Director: {{ movie.Director }}</p>
                <p>Genre: {{ movie.Genre }}</p>
            </div>
            <p class="desc">{{ movie.Plot }}</p>
        </div>
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

<style lang="scss">
.movie-detail {
    padding: 16px;

    h2 {
        color: #FFF;
        font-size: 28px;
        font-weight: 600;
        margin-bottom: 16px;
    }

    .featured-img {
        display: block;
        max-width: 600px;
        margin-bottom: 16px;
        height: 500px;
    }

    .info {
        display: flex;
        gap: 5;

        .movie-info {
            float: left;
            width: 50%;
        }

        .desc {
            float: right;
            width: 50%;
            color: #FFF;
            font-size: 18px;
            line-height: 1.4;
        }
    }
}
</style>