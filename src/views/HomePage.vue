<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>My Photo Gallery</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content class="ion-padding">

      <CameraComponents @photo-captured="addPhoto" />

      <PhotogalleryComponents
        :photos="photos"
        @photo-deleted="photos.splice($event, 1)"
      />

    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
} from "@ionic/vue";

import { ref } from "vue";

import CameraComponents from "@/components/CameraComponents.vue";
import PhotogalleryComponents from "@/components/PhotogalleryComponents.vue";

const photos = ref<string[]>([]);

const addPhoto = (photo: string) => {
  photos.value.unshift(photo);
};
</script>