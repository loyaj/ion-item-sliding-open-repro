<template>
  <ion-page>
    <ion-content :fullscreen="true">
      <ion-list>
        <ion-item-sliding ref="ionItemSlidingRef">
          <ion-item-options side="start">
            <ion-item-option color="success">Archive</ion-item-option>
          </ion-item-options>
          <ion-item>
            <ion-label>Sliding Item with Start Options</ion-label>
          </ion-item>
        </ion-item-sliding>
      </ion-list>
      <ion-button @click="openSlidingItem">Open Sliding Item</ion-button>
      <ion-button @click="closeSlidingItem">Close Sliding Item</ion-button>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { ref } from "vue";
import {
  IonContent,
  IonPage,
  IonList,
  IonItemSliding,
  IonItemOptions,
  IonItemOption,
  IonItem,
  IonLabel,
  IonButton
} from '@ionic/vue';

const ionItemSlidingRef = ref<any>(null)

function openSlidingItem() {
    ionItemSlidingRef.value.open("start")
}
function closeSlidingItem() {
    ionItemSlidingRef.value.close()
}
</script>

<style scoped>
</style>
