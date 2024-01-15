<template>
  <ion-page class="flex justify-start mt-20">
    <div class="flex flex-col items-center  my-10">
      <img src="@/assets/logo.png" alt="">
      <h1 class=" text-3xl font-bold mt-20">10 caracteres </h1>
    </div>
    <div class="flex flex-col items-center mx-10">
      <input id="default-range" min="6" max="20" type="range" value="10"
        class="w-full h-2 mb-10 bg-gray-200 rounded-lg appearance-none cursor-pointer">
      <button type="button"
        class="h-10 w-52 px-5 py-2.5 text-sm font-medium text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 rounded-lg text-center "
        @click="setOpen(true)">Gerar
        Senha</button>
      <ion-modal :is-open="isOpen">
        <ion-header>
          <ion-toolbar>
            <ion-title>Senha Gerada</ion-title>
            <ion-buttons slot="end">
              <ion-button @click="setOpen(false)">Voltar</ion-button>
              <ion-button @click="setOpen(false)">Salvar</ion-button>
            </ion-buttons>
          </ion-toolbar>
        </ion-header>
        <ion-content class="ion-padding">
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Magni illum quidem recusandae ducimus quos
            reprehenderit. Veniam, molestias quos, dolorum consequuntur nisi deserunt omnis id illo sit cum qui.
            Eaque,
            dicta.
          </p>
        </ion-content>
      </ion-modal>
    </div>
  </ion-page>
</template>

<script setup lang="ts">
import { IonPage, IonButtons, IonButton, IonModal, IonHeader, IonToolbar, IonContent, IonTitle } from '@ionic/vue';
import { ref } from 'vue';

const isOpen = ref(false);
console.log(isOpen);

const setOpen = (open: boolean) => (isOpen.value = open);

//todo: implementar o gerador de senhas com base feita no react
//todo: ajustar o range de senha
//todo: implementar o modal

</script>


<style scoped></style>