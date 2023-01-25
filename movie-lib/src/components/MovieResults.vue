<template>
    <div class="main-container">
        <div class="movie-container">
            <img :src="movie.Poster" alt="" srcset="">
            <h3>{{ movie.Title }}</h3>
        </div>
    </div>
</template>
<script>
export default {
    props: ["movie"],
    data() {
        return {
        }
    },

}
</script>
<style lang="scss" scoped>
.main-container {
    display: flex;
    .movie-container{
        display:flex;
        flex-direction: column;
        max-width: 350px;
        align-items: center;
        height: 475px;
        justify-content: space-between;
        img {
            height: 100%;
        }
        h3 {
            padding: 0 45px;
            text-align: center;
        }
    }
}
</style>