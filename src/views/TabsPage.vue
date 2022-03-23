<template>
  <ion-page>
    <ion-tabs>
      <ion-router-outlet></ion-router-outlet>
        <div class="tabBar">
          <ion-tab-bar slot="bottom">
            <ion-tab-button tab="tab1" href="/tabs/tab1">
              <ion-icon :icon="home" />
              <!-- <ion-label>Home</ion-label> -->
            </ion-tab-button>
              
            <ion-tab-button tab="tab2" href="/tabs/tab2">
              <ion-icon :icon="newspaper" />
              <!-- <ion-label>News</ion-label> -->
            </ion-tab-button>
            
            <ion-tab-button tab="tab3" href="/tabs/tab3">
              <ion-icon :icon="trophy" />
              <!-- <ion-label>League</ion-label> -->
            </ion-tab-button>
            
            <ion-tab-button tab="tab4" href="/tabs/tab4">
              <ion-icon :icon="swapHorizontal" />
              <!-- <ion-label>Transfers</ion-label> -->
            </ion-tab-button>

            <ion-tab-button tab="tab5" href="/tabs/tab5">
              <ion-icon :icon="shirt" />
              <!-- <ion-label>Club</ion-label> -->
            </ion-tab-button>
        </ion-tab-bar>
      </div>
    </ion-tabs>
  </ion-page>
</template>
<script lang="js">
import { IonTabBar, IonTabButton, IonTabs, IonIcon, IonPage, IonRouterOutlet } from '@ionic/vue';
import { ellipse, square, triangle, home, trophy, newspaper, shirt, swapHorizontal } from 'ionicons/icons';

export default {
  components: { IonTabs, IonTabBar, IonTabButton, IonIcon, IonPage, IonRouterOutlet,  },
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
    /* padding: 20px;
    width: 80%;
    margin: auto;
    --background: rgba(65, 65, 65, 0.2);  
    backdrop-filter: blur(5px);
    border-radius: 15px 15px 0 0; */
    --background: rgba(65, 65, 65, 0.2);
    --ion-color-base: rgba(65, 65, 65, 0.2) !important;
    position: absolute;
    bottom: 0px;
    width: 100%;
    --color: #b9b9b9;
  }

  ion-tab-button {
    background: none;
  }

</style>