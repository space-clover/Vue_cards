<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Rick and Morty</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content class="ion-padding">
      <ion-button @click="fetchCharacters" id="fetch-button">Obtener Personajes</ion-button>
      <ion-button @click="clearCharacters" id="clear-button">Borrar Personajes</ion-button>
      <ion-list>
        <ion-item v-for="character in characters" :key="character.id">
          <ion-avatar slot="start">
            <img :src="character.image" alt="Character Image">
          </ion-avatar>
          <ion-label>
            <h2>{{ character.name }}</h2>
            <p>ID: {{ character.id }}</p>
            <p>Especie: {{ character.species }}</p>
            <span :class="getStatusClass(character.status)"></span>
            <span>{{ character.status }}</span>
          </ion-label>
        </ion-item>
      </ion-list>
      <ion-item v-for="result in searchResults" :key="result.id">
        <ion-avatar slot="start">
          <img :src="result.image" alt="Character Image">
        </ion-avatar>
        <ion-label>
          <h2>{{ result.name }}</h2>
          <p>ID: {{ result.id }}</p>
          <p>Especie: {{ result.species }}</p>
          <span :class="getStatusClass(result.status)"></span>
          <span>{{ result.status }}</span>
        </ion-label>
      </ion-item>
    </ion-content>
  </ion-page>
</template>

<script>
import { ref } from 'vue';
import axios from 'axios';

export default {
  name: 'RickAndMortyTab',
  data() {
    return {
      characters: [],
    };
  },
  methods: {
    async fetchCharacters() {
      try {
        const response1 = await axios.get('https://rickandmortyapi.com/api/character?page=1');
        const response2 = await axios.get('https://rickandmortyapi.com/api/character?page=2');
        this.characters = [...response1.data.results, ...response2.data.results];
      } catch (error) {
        console.error('Error al obtener personajes:', error);
      }
    },
    clearCharacters() {
      this.characters = [];
    },
    getStatusClass(status) {
      if (status === 'Alive') {
        return 'status-circle green';
      } else if (status === 'Dead') {
        return 'status-circle red';
      } else {
        return 'status-circle gray';
      }
    },
  },
  created() {
    this.fetchCharacters();
  },
};
</script>

<style scoped>
ion-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

ion-item {
  flex: 0 0 calc(20% - 10px);
  margin-bottom: 20px;
  box-sizing: border-box;
  text-align: center;
}

ion-label {
  display: block;
  margin-top: 5px;
}

img {
  max-width: 100%;
  height: auto;
}

ion-button {
  margin: 10px;
}

ion-button#fetch-button {
  --ion-color-primary: green;
  border-radius: 2%;
}

ion-button#clear-button {
  --ion-color-primary: purple;
  border-radius: 2%;
}

.status-circle {
  display: inline-block;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  margin-left: 10px;
}

.green {
  background-color: green;
  border:none;
  margin-right: 2px;
}

.red {
  background-color: red;
  border:none;
  margin-right: 2px;
}

.gray {
  background-color: gray;
  border:none;
  margin-right: 2px;
}
</style>
