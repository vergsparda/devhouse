<template>
    <div class="cities-wrap">
        <span 
        v-for="city in cities"
        :key="city.id"
        class="city-name">
            {{ city.name }}
        </span>
    </div>
</template>

<script>
    export default {
        name: "CitiesList",
        props: {
            cities: Array
        }
    }
</script>

<style scoped>
    .cities-wrap {
        display: flex;
        flex-direction: column;
        flex-wrap: wrap;
        height: 900px;
    }

    .city-name {
        width: 20%;
        text-align: left;
        font-size: 14px;
        padding-top: 14px;
    }
</style>