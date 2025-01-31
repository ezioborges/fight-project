<template>
  <div class="fight-content">
      <div class="gamers">
        <h1>Jogador</h1>
        
        <div class="life-border">
            <div class="life-bar-gamer" :style="{width: hpGamer + '%' }"></div>
        </div>
        <!-- <span>{{hpGamer}}%</span> -->
      </div>
        <div class="gamers">
        <h1>Monstro</h1>
        <div class="life-border">
            <div class="life-bar-monster" :style="{width: hpMonster + '%' }"></div>
        </div>
        <!-- <span>{{hpMonster}}%</span> -->
    </div>
  </div>
</template>

<script>

export default {
  name: 'FightContent', 
  props: ['hpGamer', 'hpMonster']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import '../styles/fight-content.css';
@import '../styles/gamers.css';
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
