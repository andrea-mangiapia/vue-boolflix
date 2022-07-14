<template>
    <header>
        <div>
            <img src="../assets/logo.png" alt="Logo Boolflix">
        </div>
        
        <div>
            <label for="search"></label>
            <input type="text" id="search" name="search" placeholder="Cerca..." v-model="userSearch" @keyup.enter="$emit('toSearch', userSearch)">
            
            <button type="submit" @click="$emit('toSearch', userSearch)">Cerca</button>
        </div>
    </header>
</template>

<script>
export default {
    name: "AmHeader",

    data() {
        return {
            userSearch: ''
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/variables.scss';

header {
    background-color: black;
    color: red;
    height: $header_height;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;

    img {
        width: 100px;
    }
}
</style>