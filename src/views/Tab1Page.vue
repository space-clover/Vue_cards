<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Card_basic</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 1</ion-title>
        </ion-toolbar>
      </ion-header>

      <ExploreContainer name="Tab 1 page" 
      title="La Mona Lisa"
          imageSrc="https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Leonardo_da_Vinci_-_Mona_Lisa_%28Louvre%2C_Paris%29.jpg/245px-Leonardo_da_Vinci_-_Mona_Lisa_%28Louvre%2C_Paris%29.jpg" 
          description="La Mona Lisa, también conocida como La Gioconda, es una famosa pintura renacentista creada por
            Leonardo da Vinci en el siglo XVI. Es conocida por su enigmática sonrisa y su mirada enigmática."
          redirectTo="/pagina-de-destino"/>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import ExploreContainer from '@/components/ExploreContainer.vue';
</script>
