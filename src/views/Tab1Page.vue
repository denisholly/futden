<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Home</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">FutDen</ion-title>
        </ion-toolbar>
      </ion-header>
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

  .title {
        padding: 0 20px;
  }
</style>