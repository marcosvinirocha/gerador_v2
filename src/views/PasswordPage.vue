<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title class="text-white">Minhas senhas </ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-card v-for="password in passwordRef" :key="password" color="dark">
        <ion-card-content class="flex justify-center"> {{ password }} </ion-card-content>
      </ion-card>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import { ref } from 'vue';

const passwordRef = ref<any>(["123456", "senha123", "qwerty", "abc123"]);




</script>

<style scoped>
ion-toolbar {
  --background: #103CE1;
}
</style>
