<template>
  <div class='corpo'>
    <div class="container">
      <div class="header">
      <p>Pesquise pelo personagem de Rick e Morty:</p>
      <input type="text" v-model="name" />
      <button v-on:click="search(e)" type="submit">Pesquisar</button>
    </div>
      <ul>
        <li v-for="(personagens, i) in character" :key="i">
          <img :src="personagens.image" :alt="personagens.name" />
          <h4>{{ personagens.name }}</h4>
          <span v-if='personagens.status == "Alive"'>Situação atual: <span className='Alive'>Vivo </span></span>
          <span v-else-if='personagens.status == "Dead"'>Situação atual: <span className='Dead'>Morto </span></span>
          <span v-else>Situação atual: <span className='unknown'>Desconhecido </span></span>
          <span v-if="personagens.species == 'Human'">Espécie: <span className='Human'>Humano</span></span>
          <span v-else>Espécie: {{personagens.species}}</span>
          
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import api from "@/services/api.ts";
import axios from "axios";

export default {
  data() {
    return {
      name: "",
      character: {},
      status: [],
    }
  },
  async mounted() {
    let response = await fetch(`https://rickandmortyapi.com/api/character`);
    let result = await response.json();
    this.character = result.results;
  },
  methods: {
    async search(e) {
      let response = await fetch(
        `https://rickandmortyapi.com/api/character?name=${this.name}`
      );
      let teste = await response.json();
      this.character = teste.results;
    },
    async mapStatus() {
      
    }
  },
};
</script>

<style scoped>


.corpo {
  margin-left: 0px;
}

p {
  color: white;
  font-weight: bold;
  display: flex;
  justify-content: center;
  margin: 20px;
}

.header {
  align-items: center;
  background-color: #1f1f23;
  -webkit-box-shadow: 0px 8px 5px 2px #000000; 
  box-shadow: 0px 8px 10px 2px #000000;
  display: flex;
  justify-content: center;
  padding: 20px;
}

.header input {
  border-color: #04afca;
  border-radius: 8px;
  padding: 12px;
  width: 17%;
}

.header button {
  background-color: #7ac047;
  border-style: none;
  border-radius: 13px;
  color: white;
  cursor: pointer;
  margin-left: 20px;
  padding: 12px;
}

.container {
  background: rgb(98,204,40);
  background: linear-gradient(90deg, #62cc28 0%, #00d4ff 100%);
}

.container ul {
  list-style: none;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
  column-gap: 3rem;
  row-gap: 4rem;
}

.container li {
  align-items: center;
  background-color: #1f1f23;
  border-radius: 25px;
  box-shadow: 2px 4px 9px 2px #1f1f23;
  display: flex;
  flex-direction: column;
  margin-top: 40px;
  padding: 15px;
  margin-right: 10px;
  margin-bottom: 50px;
  transition: .2s
}

.container li:hover{
  transform: scale(1.1);
}

.Alive {
  color: green;
}

.Dead {
  color: red;
}

.unknown {
  color: gray;
}

img{
  width: 300px;
  border-radius: 1rem;
  cursor: pointer;
  transition: .2s
}

span {
  color: white;
  cursor: pointer;
  font-weight: bold;
}

span:hover, img:hover{
  transform: scale(1.1);
}

h4{
  margin-top: 25px;
  font-size: 30px;
  color: rgb(241, 241, 241);
}

</style>