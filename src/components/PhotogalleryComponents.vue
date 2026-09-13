<template>
  <ion-card>
    <ion-card-header>
      <ion-card-title>Photo Gallery</ion-card-title>
    </ion-card-header>

    <ion-card-content>
      <ion-grid v-if="props.photos.length > 0">
        <ion-row>
          <ion-col
            v-for="(photo, index) in props.photos"
            :key="index"
            size="6"
            size-md="4"
          >
            <ion-card class="photo-card">

              <ion-img
                :src="photo"
                class="gallery-image"
              />

              <ion-button
                expand="block"
                fill="clear"
                color="danger"
                @click="deletePhoto(index)"
              >
                <ion-icon
                  slot="start"
                  :icon="trashIcon"
                />
                Delete
              </ion-button>

            </ion-card>
          </ion-col>
        </ion-row>
      </ion-grid>

      <ion-text
        v-else
        class="empty-message"
      >
        <p>No photos available.</p>
      </ion-text>

    </ion-card-content>
  </ion-card>
</template>

<script setup lang="ts">
import {
  IonButton,
  IonCard,
  IonCardContent,
  IonCardHeader,
  IonCardTitle,
  IonCol,
  IonGrid,
  IonIcon,
  IonImg,
  IonRow,
  IonText,
} from "@ionic/vue";

import { trash as trashIcon } from "ionicons/icons";

const props = defineProps<{
  photos: string[];
}>();

const emit = defineEmits<{
  (event: "photoDeleted", index: number): void;
}>();

const deletePhoto = (index: number) => {
  emit("photoDeleted", index);
};
</script>

<style scoped>
.photo-card {
  margin: 4px;
}

.gallery-image {
  width: 100%;
  height: 180px;
  object-fit: cover;
}

.empty-message {
  display: block;
  text-align: center;
  margin: 20px 0;
}
</style>