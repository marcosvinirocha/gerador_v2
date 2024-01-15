<template>
  <ion-page class="flex justify-start mt-20">
    <div class="flex flex-col items-center  my-10">
      <img src="@/assets/logo.png" alt="">
      <h1 class=" text-3xl font-bold mt-20">{{ value }} caracteres </h1>
    </div>
    <div class="flex flex-col items-center mx-10">
      <input @change="handleChange" id="default-range" min="6" max="20" type="range" :value="value"
        class="w-full h-2 mb-10 bg-gray-200 rounded-lg appearance-none cursor-pointer">
      <button type="button"
        class="h-10 w-60 px-5 py-2.5 text-sm font-medium text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 rounded-lg text-center "
        @click="generatePassword">Gerar
        Senha</button>
      <ion-modal :is-open="isOpen">
        <ion-header>
          <ion-toolbar>
            <ion-title>Senha Gerada</ion-title>
            <ion-buttons slot="end">
              <ion-button @click="setOpen(false)">Voltar</ion-button>
              <ion-button @click="salvarPassword()">Salvar</ion-button>
            </ion-buttons>
          </ion-toolbar>
        </ion-header>
        <ion-content class="ion-padding">
          <ion-card color="dark">
            <ion-card-content class="flex justify-center"> {{ passwordRef }} </ion-card-content>
          </ion-card>
        </ion-content>
      </ion-modal>
    </div>
  </ion-page>
</template>

<script setup lang="ts">
import { IonPage, IonButtons, IonButton, IonModal, IonHeader, IonToolbar, IonContent, IonTitle, IonCard, IonCardContent } from '@ionic/vue';
import { ref } from 'vue';
import { Preferences } from '@capacitor/preferences';

const setPassword = async () => {
  try {
    const password = passwordRef.value;
    await Preferences.set({ key: 'password', value: password });
  } catch (error) {
    console.error(`Error setting password: ${error}`);
  }
}

const isOpen = ref(false);

const value = ref(10);

// eslint-disable-next-line prefer-const
let passwordRef = ref<any>('');

const handleChange = (event: any) => {
  value.value = event.target.value;
};

const setOpen = (open: boolean) => (isOpen.value = open);

const generatePassword = () => {
  let password = ''
  const charset = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()_+'
  for (let i = 0; i < value.value; i++) {
    password += charset.charAt(Math.floor(Math.random() * charset.length))
  }

  passwordRef.value = password
  setOpen(true)

}

const salvarPassword = () => {
  setPassword()
  setOpen(false)
}

//todo: implementar o gerador de senhas com base feita no react
//todo: implementar o modal

</script>


<style scoped></style>