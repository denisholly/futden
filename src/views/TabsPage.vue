<template>
  <ion-page>
    <ion-tabs>
      <ion-router-outlet></ion-router-outlet>
      <ion-tab-bar slot="bottom">
        <ion-tab-button tab="tab1" href="/tabs/tab1">
          <ion-icon :icon="home" />
          <ion-label>Home</ion-label>
        </ion-tab-button>
          
        <ion-tab-button tab="tab2" href="/tabs/tab2">
          <ion-icon :icon="newspaper" />
          <ion-label>News</ion-label>
        </ion-tab-button>
        
        <ion-tab-button tab="tab3" href="/tabs/tab3">
          <ion-icon :icon="trophy" />
          <ion-label>League</ion-label>
        </ion-tab-button>
        
        <ion-tab-button tab="tab4" href="/tabs/tab4">
          <ion-icon :icon="swapHorizontal" />
          <ion-label>Transfers</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab5" href="/tabs/tab5">
          <ion-icon :icon="shirt" />
          <ion-label>Club</ion-label>
        </ion-tab-button>
        
      </ion-tab-bar>
    </ion-tabs>
  </ion-page>
</template>

<script lang="js">
import { IonTabBar, IonTabButton, IonTabs, IonLabel, IonIcon, IonPage, IonRouterOutlet } from '@ionic/vue';
import { ellipse, square, triangle, home, trophy, newspaper, shirt, swapHorizontal } from 'ionicons/icons';

export default {
  components: { IonLabel, IonTabs, IonTabBar, IonTabButton, IonIcon, IonPage, IonRouterOutlet,  },
  setup() {
    return {
      ellipse, 
      square, 
      triangle,
      home,
      trophy,
      newspaper,
      shirt,
      swapHorizontal,
    }
  }
}
</script>

<style scoped>
  ion-tab-bar {
    --background: ;
  }
</style>