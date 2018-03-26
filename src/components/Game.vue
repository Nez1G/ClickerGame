<template>
  <div class="jogo">
    <h1>💶 = {{balance}}</h1>
    <h1>Tools Bonus per click: {{coinsPerClick}}</h1>
    <h1>Animals Bonus: {{animalBonus}}</h1>
    <div class="animals">
    <table v-for="animal in animals">
      <tr>
        <td id="emojie">{{animal.emojie}}</td>
        <td>+{{animal.bonus}}/s</td>
        <td>{{animal.price}}$</td>
        <td>x{{animal.multiplier}}</td>
        <td><button class="btn btn-success" v-on:click="buyAnimal(animal)">Buy a {{animal.name}}</button></td>
      </tr>

    </table>
    </div>

    <div class="tools">
    <table v-for="tool in tools">
      <tr>
        <td id="emojie">{{tool.emojie}}</td>
        <td>+{{tool.bonus}}/click</td>
        <td>{{tool.price}}$</td>
        <td>x{{tool.multiplier}}</td>
        <td><button class="btn btn-success" v-on:click="buyTool(tool)">Buy a {{tool.name}}</button></td>
      </tr>
    </table>
    </div>
    <button class="btn btn-danger" v-on:click="winCoin">Keep pressing me</button>
    <p>Feito com <span id="heart">❤</span> por um nerd <a href="https://github.com/Nez1G" target="_blank">
    <img src="../img/github.svg" alt="My GitHub account" height="5%" width="5%"/>
    </a></p>
    
  </div>
</template>

<script>
export default {
  name: 'AnimalsComp',
  data(){
    return{
      balance: 100,
      coinsPerClick: 1,
      animalBonus: 0,
      animals: [
         {
          id: 0,
          emojie: "🐭",
          name: "Rat",
          multiplier: 0,
          bonus: 0.5,
          price: 25
         },
         {
          id: 1,
          emojie: "🕷",
          name: "Spider",
          multiplier: 0,
          bonus: 2.5,
          price: 100
         },
         {
          id: 2,
          emojie: "🐼",
          name: "Panda",
          multiplier: 0,
          bonus: 11,
          price: 500
         },
         {
          id: 3,
          emojie: "🐺",
          name: "Wolf",
          multiplier: 0,
          bonus: 45,
          price: 2000
         },
         {
          id: 4,
          emojie: "🐘",
          name: "Elephant",
          multiplier: 0,
          bonus: 250,
          price: 5000
         },
         {
          id: 5,
          emojie: "🐲",
          name: "Dragon",
          multiplier: 0,
          bonus: 3000,
          price: 20000
         }
     ],
     tools: [
       {
        id: 0,
        emojie: "🍃",
        name: "Leaf",
        multiplier: 0,
        bonus: 1,
        price: 25
       },
       {
        id: 1,
        emojie: "🌸",
        name: "Cherry Blossom",
        multiplier: 0,
        bonus: 2,
        price: 50
       },
       {
        id: 2,
        emojie: "🌹",
        name: "Rose",
        multiplier: 0,
        bonus: 5,
        price: 200
       },
       {
        id: 3,
        emojie: "🍀",
        name: "Clover",
        multiplier: 0,
        bonus: 10,
        price: 1000
       },
       {
        id: 4,
        emojie: "🍄",
        name: "Mushroom",
        multiplier: 0,
        bonus: 50,
        price: 5000
       }
     ]
    }
  },
  mounted : function(){
    this.updateBalance()		
  },
    beforeDestroy () {
    clearInterval(this.intervalid)
  },
  methods: {
    buyAnimal: function(animal){
      if(this.balance >= animal.price){
        animal.multiplier++;
        this.balance = this.balance - animal.price;
        this.animalBonus += animal.bonus;
      } else {
        alert("YOU HAVE NO MONEY BRO!!!111!");
      }
    },
    buyTool: function(tool){
      if(this.balance >= tool.price){
        tool.multiplier++;
        this.balance = this.balance - tool.price;
        this.coinsPerClick += tool.bonus;
      } else {
        alert("YOU HAVE NO MONEY BRO!!!111!");
      }
    },
    winCoin: function(){
      this.balance += this.coinsPerClick;
    },
    updateBalance: function(){  
      var self = this, 
        balance,
        animalBonus;
      this.intervalid = setInterval(function(){
        self.balance += self.animalBonus;
      }, 1000);
    }
  }
}
</script>

<style scoped> 

  @media screen and (min-width: 660px){
    .tools {
      position: absolute;
      top: 480px;
      right: 0%;
    }
  }
  #heart {
    color: red;
  }

  #emojie {
    font-size: 100%;
  }
</style>

