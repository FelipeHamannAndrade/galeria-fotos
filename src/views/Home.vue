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
            <ion-col size="6" :key="photo" v-for="photo in photos">
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

<script lang="js">
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
  }
});
</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong{
  font-size: 20px;
  line-height: 26px;
}

#container p{
  font-size: 16px;
  line-height: 22px;

  color: #8c8c8c;

  margin: 0;
}

#container a{
  text-decoration: none;
}
</style>
