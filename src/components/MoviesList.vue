<template>
    <div>
        hello
    </div>
</template>


<script>
export default {
    name: 'MoviesList',
    methods: {
        fetchData: async function () {
            try {
                const res = await fetch('https://api.themoviedb.org/3/movie/550?api_key=eccae28a095b9648479f213564c82cd5')
                const movie = await res.json()
                return movie
            } catch (error) {
                console.log(error)
            }
        }
    }
}
</script>

<style>

</style>
