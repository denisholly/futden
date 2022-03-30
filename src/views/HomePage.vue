<template>
  <ion-page>
    <ion-header>
      <!-- <ion-toolbar>
        <ion-title>Home</ion-title>
      </ion-toolbar> -->
    </ion-header>
    <ion-content :fullscreen="true">
        <ion-grid>
          <ion-row>
            <div class="fullTitle">
              <h1 class="title">Latest News</h1>
            </div>
            <the-news-swiper></the-news-swiper>
          </ion-row>
          <ion-row>
            <div class="fullTitle">
              <h1 class="title">PL Table</h1>
            </div>
            <home-table></home-table>
          </ion-row>
        </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script lang="js">
import { IonPage, IonHeader, IonContent } from '@ionic/vue';
import TheNewsSwiper from '@/components/TheNewsSwiper.vue';
import HomeTable from '@/components/HomeTable.vue';

export default  {
  components: { IonHeader, IonContent, IonPage, TheNewsSwiper, HomeTable },
}
</script>

<style scoped>
  h1 {
    margin: 0;
  }

  ion-grid {
    padding: 5px 0;
  }

  ion-row {
    margin-bottom: 20px;
  }

  .header {
    width: 200px;
  }

  .fullTitle {
    display: flex;
    flex-direction: row;
    align-items: center;
    width: 100%;
    border-bottom: 2px solid rgb(41, 41, 41);
    margin-bottom: 20px;
    padding: 20px 0;
  }

  .header h1 {
    padding: 0;
  }

  .title {
    width: 50%;
    padding: 0 20px;
  }

  router-link {
    width: 50%;
    padding: 0 20px;
    color: rgb(0, 119, 255);
    text-align: end;
    display: inline-block;
    align-self: flex-end;
  }

  router-link:link,
  router-link:visited,
  router-link:hover,
  router-link:active {
    text-decoration: none;
    font-weight: normal;
  }

</style>