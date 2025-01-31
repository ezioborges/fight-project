<template>
    <div class="gamers">
        <h1>{{ forceSide }}</h1>
        <div class="life-bar"></div>
        <span>{{hpPercent}}%</span>
    </div>
</template>

<script>
    export default {
        name: "Gamers",
        props: {
            forceSide: String,
            hpPercent: Number
        }
    }
</script>

<style>
    @import "../styles/gamers.css";
</style>