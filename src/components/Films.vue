<template>
<!-- MOSTRA SOLO FILM CON IMMAGINE DI COPERTINA -->
    <div v-if="(movie.poster_path != null)" class="poster">
        <img :src="`https://image.tmdb.org/t/p/w342/`+ movie.poster_path">
        <div class="info">
            <!-- SE I TITOLI SONO DIVERSI -->
            <div v-if="(movie.title != movie.original_title)" class="title">
                <h3>{{movie.title}}</h3>
                <h5>{{movie.original_title}}</h5>
            </div>
            <!-- SE I TITOLI SONO UGUALI -->
            <div v-else class="title">
                <h3>{{movie.title}}</h3>
            </div>
            <!-- BANDIERA -->
            <div class="lang"><lang-flag :iso="movie.original_language" :squared="false"/></div>
            <!-- GENERI -->

            <div>{{genresId()}}</div>

            <!-- STELLE -->
            <div class="vote">
                <i v-for="(star, index) in starVote()" :key="index" class="fas fa-star"></i>
                <i v-for="(empty, index) in starVoteEmpty()" :key="index + 10" class="far fa-star"></i>
            </div>
            <!-- RIASSUNTO -->
            <div class="resume">
                <p>{{movie.overview}}</p>
            </div>
        </div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    name: 'Films',
    props: ['movie','id'],
    components: {
        LangFlag,
    },
    data() {
        return {
            roundedNum: "",
        }
    },
    methods: {
        starVote() {
            const halfNum = this.movie.vote_average / 2;
            this.roundedNum = Math.ceil(halfNum);
            return this.roundedNum;
        },
        starVoteEmpty() {
            this.emptyStars = 5 - this.roundedNum;
            return this.emptyStars;
        },
        genresId() {
            // const idFilm = this.movie.genre_ids;
            // for (let i = 0; i < idFilm.length; i++) {
            //     const singleFilmId = idFilm[i];
            //     console.log(singleFilmId)
            // }
            console.log(this.movie)
        },
    }
}
</script>

<style lang="scss" scoped>
    @import '../assets/style/common.scss';
    .poster {
        position: relative;
        display: flex;
        justify-content: center;
        .info {
            display: none;
            .title {
                font-size: 1.4rem;
                margin-bottom: 10px;
                text-align: center;
                h3 {
                    margin-bottom: 7px;
                }
            }
            .flag-icon {
                width: 40px;
                line-height: 40px;
                border-radius: 30%;
                margin-bottom: 10px;
            }
            .vote {
                display: flex;
                justify-content: center;
                color: yellow;
                margin-bottom: 10px;
            }
            .resume {
                font-size: .85rem;
                text-align: center;
                overflow-y: hidden;
            }
        }
    }
    .poster:hover .info {
        color: #fff;
        position: absolute;
        width: 100%;
        height: 100%;
        top: 0;
        left: 0;
        padding: 15px;
        display: flex;
        flex-direction: column;
        align-items: center;
        background-color: rgb(24, 23, 23, .7);
    }
</style>