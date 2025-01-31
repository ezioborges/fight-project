<template>
  <div class="fight-content">
      <Gamers force-side="Jogador" :hp-percent="hpGamer" />
      <Gamers force-side="Monstro" :hp-percent="hpMonster"/>
  </div>
</template>

<script>
import Gamers from './Gamers.vue';

export default {
  name: 'FightContent',
  components: {
    Gamers
  }, 
  props: ['hpGamer', 'hpMonster']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import '../styles/fight-content.css';
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
