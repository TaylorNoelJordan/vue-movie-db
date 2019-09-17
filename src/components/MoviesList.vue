<template>
    <ul>
        <li :key='movie.id' v-for="movie in movies">
            <Movie :movie='movie'/>
        </li>
    </ul>
</template>


<script>
import Movie from './Movie.vue'
export default {
    name: 'MoviesList',
    data() {
        return {
            movies: []
        }
    },
    created: function() {
        this.fetchData();
    },
    methods: {
        fetchData: async function () {
            try {
                const res = await fetch('https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=eccae28a095b9648479f213564c82cd5')
                const movies = await res.json()
                this.movies = movies.results;
            } catch (error) {
                console.log(error)
            }
        }
    },
    components: {
        Movie
    }
}
</script>

<style scoped>
    ul {
        display: grid;
        list-style: none;
        padding: 1rem;
        margin: 0;
        grid-row-gap: 1rem;
        grid-template-columns: repeat(6, 1fr)
    }
</style>
