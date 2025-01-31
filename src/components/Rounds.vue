<template>
    <div v-if="moveGamerArray.length > 0" class="rounds-content">
        <ul v-for="(move, index) in moveGamerArray" :key="index">
            <li>
                <div class="gamer"><p>Jogador atingiu monstro com {{ move.gamer }} de ataque</p></div>
                <div class="monster"><p>Monstro atingiu jogador com {{ move.monster }} de ataque</p></div>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'Rounds',
        props: ['moveGamerArray'],
    }
        
</script>

<style>
    @import '../styles/rounds-content.css';
</style>