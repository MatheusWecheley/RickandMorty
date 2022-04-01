<template>
  <div class='corpo'>
    <p>Personagens do Rick and Morty:</p>
    <div class="header">
      <input type="text" v-model="name" />
      <button v-on:click="search(e)" type="submit">Pesquisar</button>
    </div>
    <div class="container">
      <ul>
        <li v-for="(personagens, i) in character" :key="i">
          <h4>{{ personagens.name }}</h4>
          <span>Situação atual:{{ personagens.status }}</span>
          <img :src="personagens.image" :alt="personagens.name" />
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
      character: [],
      status: [],
    }
  },
  async mounted() {
    let response = await fetch(`https://rickandmortyapi.com/api/character`);
    let result = await response.json();
    this.character = result.results;
    this.status = this.character[0].status
    console.log(this.status);
  },
  methods: {
    async search(e) {
      let response = await fetch(
        `https://rickandmortyapi.com/api/character?name=${this.name}`
      );
      let teste = await response.json();
      this.character = teste.results;
    },
  },
};
</script>

<style scoped>


.corpo {
  margin-left: 0px;
}

p {
  display: flex;
  justify-content: center;
}

.header {
  align-items: center;
  display: flex;
  justify-content: center;
  margin-top: 20px;
  padding: 20px;
}

.header input {
  border-color: #04afca;
  border-radius: 8px;
  padding: 12px;
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
  background: linear-gradient(90deg, rgba(98,204,40,1) 0%, rgba(0,212,255,1) 100%);
}

.container ul {
  list-style: none;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  column-gap: 3rem;
  row-gap: 4rem;
}

.container li {
  align-items: center;
  display: flex;
  flex-direction: column;
  margin-top: 40px;
}


img{
  width: 180px;
  border-radius: 1rem;
  cursor: pointer;
  transition: .2s
}

img:hover{
  transform: scale(1.1);
}

h4{
  font-size: 30px;
  color: black;
}

</style>