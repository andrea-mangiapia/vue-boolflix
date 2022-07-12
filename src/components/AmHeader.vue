<template>
    <header>
        <div>
            <h1>
                BOOLFLIX
            </h1>
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
header {
    background-color: black;
    color: red;
    height: 60px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;

    h1 {
        font-size: 20px;
    }
}
</style>