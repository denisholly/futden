<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Home</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
        <ion-grid class="header">
          <ion-row>
            <ion-col>
              <h1>FutDen</h1>
            </ion-col>
            <ion-col>
              <ion-chip>
                <ion-label color="secondary">Beta</ion-label>
              </ion-chip>  
            </ion-col>
          </ion-row>
        </ion-grid>
        <ion-grid>
          <ion-row>
            <h1 class="title">Latest News</h1>
            <the-news-swiper></the-news-swiper>
          </ion-row>
          <ion-row>
            <h1 class="title">PL Table</h1>
            <home-table></home-table>
          </ion-row>
        </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script lang="js">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import TheNewsSwiper from '@/components/TheNewsSwiper.vue';
import HomeTable from '@/components/HomeTable.vue';

export default  {
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage, TheNewsSwiper, HomeTable},
}
</script>

<style scoped>
  ion-grid {
    padding: 5px 0;
  }

  .header {
    width: 200px;
  }

  .header h1 {
    padding: 0 !important;
  }

  .title {
        padding: 0 20px;
  }
</style>