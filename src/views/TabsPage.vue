<template>
  <ion-page>
    <ion-tabs>
      <ion-router-outlet></ion-router-outlet>
        <div class="tabBar">
          <ion-tab-bar slot="bottom">
            <ion-tab-button tab="home" href="/home">
              <ion-icon :icon="home" />
            </ion-tab-button>
              
            <ion-tab-button tab="news" href="/news">
              <ion-icon :icon="newspaper" />
            </ion-tab-button>
            
            <ion-tab-button tab="table" href="/table">
              <ion-icon :icon="trophy" />
            </ion-tab-button>

            <ion-tab-button tab="players" href="/players">
              <ion-icon :icon="shirt" />
            </ion-tab-button>
        </ion-tab-bar>
      </div>
    </ion-tabs>
  </ion-page>
</template>
<script lang="js">
import { IonTabBar, IonTabButton, IonTabs, IonIcon, IonPage, IonRouterOutlet } from '@ionic/vue';
import { ellipse, square, triangle, home, trophy, newspaper, shirt } from 'ionicons/icons';

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
    }
  }
}
</script>

<style scoped>

  ion-tab-bar {
    padding: 10px 20px;
    /* backdrop-filter: blur(5px); */
    --background: rgba(20, 20, 20);
    text-align: center;
    --color: #b9b9b9;
    --ion-color-primary: rgb(0, 119, 255);
    --border: none;
  }

  ion-tab-button {
    background: none;
  }

</style>