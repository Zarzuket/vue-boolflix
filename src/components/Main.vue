<template>
    <main class="container">
        <div class="films">
            <div v-if="allFilms.length > 0">
                <h2>FILMS</h2>
                <ul>
                    <li v-for="(film, index) in allFilms" :key="index" >
                        <Films :movie="film" :id="movieGen" />
                    </li>
                </ul>
            </div>
            <div v-else>
                <h2>NESSUN FILM TROVATO</h2>
            </div>
            
        </div>
        <div class="tvs">
            <div v-if="allSeries.length > 0">
                <h2>TV SERIES</h2>
                <ul>
                    <li v-for="(serie, index) in allSeries" :key="index" >
                        <Tvs :tv="serie" />
                    </li>
                </ul>
            </div>
            <div v-else>
                <h2>NESSUNA SERIE TROVATA</h2>
            </div>
        </div>
    </main>
</template>

<script>
import Films from './Films.vue';
import Tvs from '../components/Tvs.vue';
export default {
    name: 'Main',
    components: {
        Films,
        Tvs
    },
    props: ['allFilms','allSeries','movieGen'],
}
</script>

<style lang="scss" scoped>
    @import '../assets/style/common.scss';
    .container {
        width: 90%;
        margin: 0 auto;
        .films, 
        .tvs {
        margin: 50px 0;
            h2 {
                font-weight: 900;
                color: $redColor;
                margin-bottom: 30px;
            }
            ul {
                display: flex;
                overflow-y: hidden;
                li {
                    margin-right: 40px;
                    max-height: 513px;
                }
            }
        }
    }
    
</style>