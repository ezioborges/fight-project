<template>
    <div class="controller-content">
        <Buttons 
            :buttonsStatedNames="buttonsStatedNames"
            :started="started"
            :startGame="startGame"
            :hpGamer="hpGamer"
            :hpMonster="hpMonster"
            :attack="attack"
            :healthHp="healthHp"
            :specialAttack="specialAttack"
            :giveUp="giveUp"
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
        
        data() {
            return {
                buttonsStatedNames: ['ataque', 'ataque especial', 'curar', 'desistir']
            }
        },
        props: ['hpGamer', 'hpMonster', 'attack', 'healthHp', 'specialAttack', 'giveUp', 'started', 'startGame'],
    }
</script>

<style>
    @import "../styles/controller-component.css"; 
</style>