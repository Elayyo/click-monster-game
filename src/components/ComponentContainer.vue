<template>
  <div>
    <div id="title">
      <h1>Monster Slayer Game</h1>
    </div>
    <base-card class="bardiv">
      <div> 
        <h2><label>Monster Health</label></h2>
      </div>
      <progress id="monsterbar" max="100" :value="monsterHealth"></progress>
    </base-card>
    <base-card>
      <div class="bardiv">
        <h2><label>Your Health</label></h2>
      </div>
      <progress id="yourbar" max="100" :value="playerHealth"></progress>
    </base-card>
    <action-buttons 
      @attack="playerAttack"
      @special-attack="playerSpecialAttack"
      @heal="playerHeal"></action-buttons>
    <base-card>
      <h2>Battle log</h2>
      <p v-for="data in logData" :key="data">{{ data }}</p>
    </base-card>
  </div>
</template>

<script>
import BaseCard from './BaseCard.vue'
import ActionButtons from './ActionButtons.vue'

export default{
  components: {
    BaseCard,
    ActionButtons
  },
  data(){
    return{
      playerHealth: 100,
      monsterHealth: 100,
      logData: []
    }
  },
  methods:{
    playerAttack(){
      const max = this.monsterHealth;
      const min = this.monsterHealth -20;
      const result = Math.floor(Math.random() * (max-min) +min);
      this.monsterHealth = result;
      this.logData.push(`Monster hat ${max - result} Schaden erhalten`);
      this.checkGameState();
      this.monsterAttack()
    },
    playerSpecialAttack(){
      const max = this.monsterHealth;
      const min = this.monsterHealth -60;
      const result = Math.floor(Math.random() * (max-min) +min);
      this.monsterHealth = result;
      this.logData.push(`Monster hat ${max - result} Schaden erhalten`);
      this.checkGameState();
      this.monsterAttack()
    },
    monsterAttack(){
      const max = this.playerHealth;
      const min = this.playerHealth -20;
      const result = Math.floor(Math.random() * (max-min) +min);
      this.playerHealth = result
      this.logData.push(`Spieler hat ${max - result} Schaden erhalten`);
      this.checkGameState();
    },
    playerHeal(){
      const max = this.playerHealth;
      const result =  Math.floor(Math.random() * 60) + max;
      this.logData.push(`Spieler hat ${result - max} Leben erhalten`);
      this.playerHealth += result;
      if(this.playerHealth > 100){
        this.playerHealth = 100;
      }
      setTimeout(() => {
        this.monsterAttack();
      },500);
    },
    checkGameState(){
      if(this.monsterHealth <= 0){
        alert("King, ezzy win 👑")
        window.location.reload();
        return;
      }
      else if(this.playerHealth <= 0){
        alert("Du Opfer nichtmal klicken kannst du 💀");
        window.location.reload();
      }
    }
  }
}

</script>

<style scoped>
p{
  font-family: roboto;
}
h1{
  color: white;
  font-family: roboto;
}
h2{
  font-family: roboto;
  margin: 0;
}
.bardiv{
  display: flex;
}
#monsterbar{
  background-color: green;
  height: 40px;
  width: 40px;
  margin-bottom: 20px;
  border: solid black;
  width: 95%;
  
}
#yourbar{
  background-color: green;
  height: 40px;
  width: 40px;
  border: solid black;
  margin-bottom: 20px;
  width: 95%;
}
#title{
  background-color: brown;
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
