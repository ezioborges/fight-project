<template>
  <div id="app">
    <FightContent 
      :hpGamer="hpGamer"
      :hpMonster="hpMonster"
      />

    <ControllerComponent
      :hpGamer="hpGamer"
      :hpMonster="hpMonster"
      :attack="attack"
      :healthHp="healthHp"
      :specialAttack="specialAttack"
      :giveUp="giveUp"
      :started="started"
      :startGame="startGame"
      />
  </div>
</template>

<script>

import ControllerComponent from './components/ControllerComponent.vue';
import FightContent from './components/FightContent.vue';

export default {
  name: 'App',
  components: {
    FightContent,
    ControllerComponent,
  }, 
  data() {
    return {
      hpGamer: 100,
      hpMonster: 100,
      started: false,
    }
  },
  methods: {
    startGame() {
            this.started = true
    },

    attack() {
      //tanto o jogador quanto o monstro atacam jogador entre 5 e 12 monstro entre 8 e 12
      const gamerAttackLost = this.randomAttack(8, 15)
      const mosnterAttackLost = this.randomAttack(5, 10)
      console.log("🚀 ~ attack ~ gamerAttackLost:", gamerAttackLost)
      console.log("🚀 ~ attack ~ mosnterAttackLost:", mosnterAttackLost)
      this.hpGamer = this.hpGamer - gamerAttackLost
      this.hpMonster = this.hpMonster - mosnterAttackLost
    },

    randomAttack(min, max) {
      const minCeiled = Math.ceil(min);
      const maxFloored = Math.floor(max);
      const random = Math.floor(Math.random() * (maxFloored - minCeiled) + minCeiled)
                  
      return random;
    },

    specialAttack() {
      const gamerspaecialLost = this.randomAttack(25, 30)
      const monsterspaecialLost = this.randomAttack(28, 35)

      this.hpGamer = this.hpGamer - gamerspaecialLost;
      this.hpMonster = this.hpMonster - monsterspaecialLost
    },

    healthHp(cureValue) {
      this.hpGamer = this.hpGamer + cureValue
      
      if (this.hpGamer > 100) {
        return this.hpGamer = 100
      }
    },

    giveUp() {
      this.hpGamer = 100;
      this.hpMonster = 100;
      this.started = false
    }
  }
}
</script>

<style>
  @import "./styles/reset.css";
</style>
