<template>
    <div class="controller-content">
        <Buttons 
            :started="started"
            :startGame="startGame"
            :hpGamer="hpGamer"
            :hpMonster="hpMonster"
            :attack="attack"
            :healthHp="healthHp"
            :specialAttack="specialAttack"
            :giveUp="giveUp"
            :gamerLost="gamerLost"
            :monsterLost="monsterLost"
            />

    </div>
</template>

<script>
import Buttons from './Buttons.vue';


    export default {
        name: "ControllerComponent",
        components: {
            Buttons
        },
        
        props: ['hpGamer', 'hpMonster', 'attack', 'healthHp', 'specialAttack', 'giveUp', 'started', 'startGame', 'gamerLost', 'monsterLost'],
    }
</script>

<style>
    @import "../styles/controller-component.css"; 
</style>