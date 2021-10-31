<template>
  <ion-page>
     <ion-content> 
      <ion-header>
        <ion-toolbar>
          <ion-title size="large">Galeria de Fotos</ion-title>
        </ion-toolbar>
      </ion-header>

      <div id="container">
        <ion-grid>
          <ion-row>
            <ion-col size="3" :key="photo" v-for="photo in photo">
              <ion-img :src="photo.webviewPath"></ion-img>
            </ion-col>
          </ion-row>
        </ion-grid>
      </div>
     
      <ion-fab vertical="bottom" horizontal="center">
        <ion-fab-button @click="takePhoto()">
          <ion-icon :icon="camera"></ion-icon>
        </ion-fab-button>
      </ion-fab>
     
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { camera } from 'ionicons/icons';
import { IonPage, IonHeader, IonFab, IonFabButton, IonIcon, IonToolbar, IonTitle, IonContent, IonImg } from '@ionic/vue';
import { defineComponent } from 'vue';
import { usePhotoGallery } from '@/composables/usePhotoGallery';

export default defineComponent({    
  name: 'Home',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonFab,
    IonFabButton,
    IonIcon, 
    IonImg
  },
  setup() {
    const { photos, takePhoto } = usePhotoGallery();

    return {
      photos,
      takePhoto, 
      camera
    }
  },
});
</script>

<style scoped>
.container {
  text-align: center;}
</style>