<template>
    <div>
        <button v-if="!started && !gamerLost && !monsterLost" @click="startGame" class="btn-init"> Iniciar novo jogo </button>
        <div v-if="started && !gamerLost && !monsterLost">
            <button @click="attack" class="btn-attack">ataque</button>
            <button @click="specialAttack" class="btn-special">ataque especial</button>
            <button @click="healthHp(10)" class="btn-helth">curar</button>
            <button @click="giveUp" class="btn-give-up">desistir</button>
        </div>
        <span v-if="gamerLost" class="gamer-lost">Que pena! Você perdeu :( </span>
        <span v-if="monsterLost" class="monster-lost">Parabens! Você ganhou :) </span>
    </div>
    </template>

<script>

    export default {
        name: "Buttons",
        props: ['started', 'buttonsStatedNames', 'hpGamer', 'hpMonster', 'attack', 'healthHp', 'specialAttack', 'giveUp', 'startGame', 'gamerLost', 'monsterLost'],
    }
</script>

<style>
    @import "../styles/buttons.css";
</style>