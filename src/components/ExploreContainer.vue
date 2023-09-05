<template>
  <ion-card>
    <ion-img :src="imageSrc" :alt="title"></ion-img>
    <ion-card-header>
      <ion-card-title>{{ title }}</ion-card-title>
    </ion-card-header>
    <ion-card-content>
      <p>{{ description }}</p>
    </ion-card-content>
    <ion-button expand="full" :to="redirectTo">
      Home
    </ion-button>
  </ion-card>
</template>

<script>
export default {
  props: {
    title: String,
    imageSrc: String,
    description: String,
    redirectTo: String,
  },
};
</script>