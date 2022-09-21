<template>
    <main>
        <!-- Section Film -->
        <section class="film" v-if="filmlist.length > 0">
            <h2>Film</h2>
            <ul>
                <li v-for="(film, index) in filmlist" :key="index">                 
                    <div class="card">
                        <!-- Poster -->
                        <div class="img-poster">
                            <img v-if="film.poster_path" class="poster" :src="`https://image.tmdb.org/t/p/w342${film.poster_path}`" :alt="film.original_language">
                            <img v-else class="poster" src="../assets/style/img/img-placeholder.jpg" alt="Image Default">
                        </div>

                        <!-- Content Text -->
                        <div  class="content-text">
                            <div><strong>Titolo:</strong> {{film.title}}</div>
                            <div><strong>Titolo originale:</strong> {{film.original_title}}</div>
                            <div>
                                <strong>Lingua:&nbsp;</strong> 
                                <img v-if="availableFlags.includes(film.original_language)" class="flag" :src="require(`../assets/style/img/${film.original_language}.png`)" :alt="film.original_language">
                                <span v-else>{{film.original_language}}</span>
                            </div>
                            <div><strong>Voto:</strong> {{film.vote_average}}</div>
                            <div><strong>Media Voto:</strong> {{getStars(film.vote_average)}}
                                <i v-for="n in getStars(film.vote_average)" :key="n" class="fa-solid fa-star"></i>
                                <i v-for="n in 5 - getStars(film.vote_average)" :key="n" class="fa-regular fa-star"></i>
                            </div>
                        </div>
                    </div>
                </li>
            </ul>
        </section>

        <hr>

        <!-- Section Serie -->
        <section class="serie" v-if="serielist.length > 0">
            <h2>Serie TV</h2>
            <ul>
                <li v-for="(serie, index) in serielist" :key="index">
                    <div class="card">
                        <!-- Poster -->
                        <div class="img-poster">
                            <img v-if="serie.poster_path" class="poster" :src="`https://image.tmdb.org/t/p/w342${serie.poster_path}`" :alt="serie.original_language">
                            <img v-else class="poster" src="../assets/style/img/img-placeholder.jpg" alt="Image Default">
                        </div>

                        <!-- Content Text -->
                        <div  class="content-text">
                            <div><strong>Titolo:</strong> {{serie.name}}</div>
                            <div><strong>Titolo originale:</strong> {{serie.original_name}}</div>
                            <div>
                                <strong>Lingua:&nbsp;</strong>
                                <img v-if="availableFlags.includes(serie.original_language)" class="flag" :src="require(`../assets/style/img/${serie.original_language}.png`)" :alt="serie.original_language">
                                <span v-else>{{serie.original_language}}</span>
                            </div>
                            <div><strong>Voto:</strong> {{serie.vote_average}}</div>
                            <div><strong>Media Voto:</strong>
                                {{getStars(serie.vote_average)}}
                                <i v-for="n in getStars(serie.vote_average)" :key="n" class="fas fa-star"></i> 
                                <i v-for="n in 5 - getStars(serie.vote_average)" :key="n" class="far fa-star"></i>
                            </div>
                        </div>
                    </div>
                </li>
            </ul>
        </section>
    </main>
</template>

<script>
export default {
    name: "AmMain",
    data: function() {
        return {
            availableFlags: ['it', 'en']
        };
    },
    methods: {
        getStars(original_vote) {
            /* Arrotondiamo il numero del voto per eccesso all’unità successiva */
            const vote = original_vote / 2;
            return Math.round(vote);

            // // Possiamo scriverlo anche in questo modo
            // return Math.round(original_vote) / 2;

        }     
    },
    props: {
        filmlist: Array,
        serielist: Array,
    },
    // ['filmlist','serielist']
}
</script>

<style lang="scss" scoped>
@import '../assets/style/variables.scss';

section {
    padding: 20px;

    h2 {
        color: white;
        font-size: 28px;
        padding-bottom: 20px;
    }

    ul {
        display: flex;
        flex-wrap: wrap;
        list-style-type: none;
        gap: 10px;
        
        
    }

    li {
        cursor: pointer;

        &:hover {
            background-color: black;
        }

        .poster {
        width: $widht-poster-text;
        }
        .img-poster img {
            display: block;
        }
        &:hover .img-poster {
            display: none;
        }

        .content-text {
            display: none;
            padding: 10px;
            color: white;
            line-height: 1.6;
        
        }
        &:hover .content-text {
            width: $widht-poster-text;
            word-wrap: break-word;
            display: block;
        }

        .flag {
        width: 25px;
        }

        i {
            color: yellow;
        }
        
    }
}
</style>