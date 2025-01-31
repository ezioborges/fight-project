<template>
    <div>
        <button v-if="!started" @click="startGame"> Iniciar novo jogo </button>
        <div v-else>
            <button @click="attack">ataque</button>
            <button @click="specialAttack">ataque especial</button>
            <button @click="healthHp(10)">curar</button>
            <button @click="giveUp">desistir</button>
        </div>
    </div>
    </template>

<script>

    export default {
        name: "Buttons",
        props: ['started', 'buttonsStatedNames', 'hpGamer', 'hpMonster', 'attack', 'healthHp', 'specialAttack', 'giveUp', 'startGame'],
    }
</script>

<style>
    @import "../styles/buttons.css";
</style>