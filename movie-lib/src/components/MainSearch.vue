<template>
    <div class="main-container">
        <div class="desc">Wyszukiwarka filmów</div>
        <div class="input-container">
            <input type="text" v-model="searchValue" @keyup.enter="fetchData" />
            <button @click="fetchData" v-on:keyup.enter="fetchData">Szukaj</button>
        </div>
        <div class="movies-container">
            <div v-for="movie in foundMovies">
                <MovieResults :movie="movie"></MovieResults>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios';
import { toHandlers } from 'vue';
import MovieResults from './MovieResults.vue';
export default {
    data() {
        return {
            apiKey: "&apikey=454136d8",
            url: "https://www.omdbapi.com/?s=",
            searchValue: "",
            foundMovies: [],
        };
    },
    methods: {
        async fetchData() {
            await axios.get(this.url + this.searchValue + this.apiKey).then((res) => {
                console.log(res.data.Search);
                res.data.Search.map((t) => console.log(t.Title));
                this.foundMovies = res.data.Search
            });
        }
    },
    components: { MovieResults }
}
</script>
<style lang="scss" scoped>
.main-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    .desc {
        font-size: 2rem;
        color: #fff;
        margin-bottom: 15px;
        text-align: center;

        @media (max-width: 720px) {
            font-size: 1.2rem;
        }
    }
}

.input-container {
    display: flex;
    margin-bottom: 30px;
    flex-direction: column;
    justify-content: center;
    gap: 10px;
    align-items: center;

    input {
        width: 75vw;
        border-radius: 25px;
        height: 40px;
        border: none;
        padding: 0 15px;
    }

    button {
        border-radius: 50px;
        background-color: #fff;
        color: #000;
        padding: 10px 20px;
    }

}

.movies-container {
    display: flex;
    flex-wrap: wrap;
    gap: 25px;
    justify-content: center;
}

button {
    display: block;
    max-width: 100px;
}
</style>