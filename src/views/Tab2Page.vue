<template>
    <ion-page>
      <ion-header>
        <ion-toolbar>
          <ion-title>Imgflip Memes</ion-title>
        </ion-toolbar>
      </ion-header>
      
      <ion-content class="ion-padding">
        <ion-button @click="fetchMemes" id="fetch-button">Obtener Memes</ion-button>
        <ion-button @click="clearMemes" id="clear-button">Borrar Memes</ion-button>
        <ion-list>
          <ion-item v-for="meme in memes" :key="meme.id">
            <ion-avatar slot="start" style="width: 100px; height: 100px;">
              <img :src="meme.url" alt="Meme" style="width: 100%; height: 100%; object-fit: contain;">
            </ion-avatar>
            <ion-label>
              <h2>{{ meme.name }}</h2>
              <p>ID: {{ meme.id }}</p>
            </ion-label>
          </ion-item>
        </ion-list>
      </ion-content>
    </ion-page>
  </template>
  
  <script>
  import { ref } from 'vue';
  import axios from 'axios';
  
  export default {
    name: 'ImgflipMemesTab',
    data() {
      return {
        memes: [],
      };
    },
    methods: {
      async fetchMemes() {
        try {
          // Realiza una solicitud para obtener memes de Imgflip (debes tener una clave de API válida)
          const response = await axios.get('https://api.imgflip.com/get_memes');
          this.memes = response.data.data.memes;
        } catch (error) {
          console.error('Error al obtener memes:', error);
        }
      },
      clearMemes() {
        this.memes = [];
      },
    },
    created() {
      // Llama a fetchMemes al cargar el componente
      this.fetchMemes();
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
    flex: 0 0 calc(33.33% - 10px); /* Muestra 3 memes por fila */
    margin-bottom: 20px;
    box-sizing: border-box;
    text-align: center;
  }
  
  ion-label {
    display: block;
    margin-top: 5px;
  }
  
  ion-avatar img {
    width: 100%;
    height: 100%;
    object-fit: contain;
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
  </style>
  