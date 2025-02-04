<template>
  <div id="app">
    <FightContent 
      :hpGamer="hpGamer"
      :hpMonster="hpMonster"
      :gamerLost="gamerLost"
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
      :gamerLost="gamerLost"
      :monsterLost="monsterLost"
      />
      <Rounds :moveGamerArray="moveGamerArray" />
  </div>
</template>

<script>

import ControllerComponent from './components/ControllerComponent.vue';
import FightContent from './components/FightContent.vue';
import Rounds from './components/Rounds.vue';

export default {
  name: 'App',
  components: {
    FightContent,
    ControllerComponent,
    Rounds
  }, 
  data() {
    return {
      hpGamer: 100,
      hpMonster: 100,
      started: false,
      moveGamerArray: [],
      gamerLost: false,
      monsterLost: false
    }
  },
  methods: {
    startGame() {
            this.started = true;
            this.hpGamer = 100;
            this.monster = 100;
    },

    attack() {
      const gamerAttackLost = this.randomAttack(8, 15)
      const mosnterAttackLost = this.randomAttack(5, 10)
      this.hpGamer = this.hpGamer - gamerAttackLost
      this.hpMonster = this.hpMonster - mosnterAttackLost

      if (this.hpGamer <= 0 && this.hpGamer < this.hpMonster) {
        this.gamerLost = true
        this.hpGamer = 0
      }

      if (this.hpMonster <= 0 && this.hpGamer > this.hpMonster) {
        this.monsterLost = true;
        this.hpMonster = 0;
      }

      if (this.hpGamer <= 30) {
        const hp = document.querySelector('.life-bar-gamer')
        hp.style.backgroundColor = "red" 
      }

      if (this.hpMonster <= 30) {
        const hp = document.querySelector('.life-bar-monster')
        hp.style.backgroundColor = "red" 
      }

      this.moveGamerArray.unshift({gamer: mosnterAttackLost, monster: gamerAttackLost});
    },

    randomAttack(min, max) {
      const minCeiled = Math.ceil(min);
      const maxFloored = Math.floor(max);
      const random = Math.round(Math.random() * (maxFloored - minCeiled) + minCeiled);
                  
      return random;
    },

    specialAttack() {
      const gamerSpaecialLost = this.randomAttack(25, 30);
      const monsterSpecialLost = this.randomAttack(28, 35);

      this.hpGamer = this.hpGamer - gamerSpaecialLost;
      this.hpMonster = this.hpMonster - monsterSpecialLost;

      if (this.hpGamer <= 0 && this.hpGamer < this.hpMonster) {
        this.gamerLost = true
        this.hpGamer = 0
      }

      if (this.hpMonster <= 0 && this.hpGamer > this.hpMonster) {
        this.monsterLost = true;
        this.hpMonster = 0;
      } 
      
      if (this.hpGamer <= 30) {
        const hp = document.querySelector('.life-bar-gamer')
        hp.style.backgroundColor = 'red'
      }

      if (this.hpMonster <= 30) {
        const hp = document.querySelector('.life-bar-monster')
        hp.style.backgroundColor = 'red'
      }

      this.moveGamerArray.unshift({gamer: monsterSpecialLost, monster: gamerSpaecialLost})
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
      this.started = false;
      this.moveGamerArray = [];
    }
  }
}
</script>

<style>
  @import "./styles/reset.css";
</style>
