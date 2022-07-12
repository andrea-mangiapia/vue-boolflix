<template>
    <main>
        <!-- Section Film -->
        <section class="film">
            <ul>
                <li v-for="(film, index) in filmlist" :key="index">
                    <div>Titolo: {{film.title}}</div>
                    <div>Titolo originale: {{film.original_title}}</div>
                    <div>Lingua: {{film.original_language}}</div>
                    <div>Voto: {{film.vote_average}}</div>
                </li>
            </ul>
        </section>

        <!-- Section Serie -->
        <section class="serie">
            <ul>
                <li v-for="(serie, index) in serielist" :key="index">
                    <div>Titolo: {{serie.name}}</div>
                    <div>Titolo originale: {{serie.original_name}}</div>
                    <div>Lingua: {{serie.original_language}}</div>
                    <div>Voto: {{serie.vote_average}}</div>
                </li>
            </ul>
        </section>
    </main>
</template>

<script>
export default {
name: "AmMain",
props: ['filmlist','serielist'] 
}
</script>

<style lang="scss" scoped>
section {

    &.film {
        background-color: lightgray;
    }

    &.serie {
        background-color: rgb(61, 61, 61);
        color: white;
    }

    li {
        padding: 15px 10px;
    }
}
</style>