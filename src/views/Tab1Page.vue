<template>
  <ion-page>
    <ion-header>
      <!-- <ion-toolbar>
        <ion-title>Home</ion-title>
      </ion-toolbar> -->
    </ion-header>
    <ion-content :fullscreen="true">
        <ion-grid class="header">
          <ion-row>
            <!-- <ion-col>
              <h1>FutDen</h1>
            </ion-col>
            <ion-col>
              <ion-chip>
                <ion-label color="secondary">Beta</ion-label>
              </ion-chip>  
            </ion-col> -->
          </ion-row>
        </ion-grid>
        <ion-grid>
          <ion-row>
            <div class="fullTitle">
              <h1 class="title">Latest News</h1>
              <p class="seeAll">See All</p>
            </div>
            <the-news-swiper></the-news-swiper>
          </ion-row>
          <ion-row>
            <div class="fullTitle">
              <h1 class="title">Categories</h1>
              <p class="seeAll">See All</p>
            </div>
            <the-categories></the-categories>
          </ion-row>
          <ion-row>
            <div class="fullTitle">
              <h1 class="title">PL Table</h1>
              <p class="seeAll">See All</p>
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
import TheCategories from '@/components/TheCategories.vue';

export default  {
  components: { IonHeader, IonContent, IonPage, TheNewsSwiper, HomeTable, TheCategories},
}
</script>

<style scoped>
  h1 {
    margin: 0;
  }

  ion-grid {
    padding: 5px 0;
  }

  .header {
    width: 200px;
  }

  .fullTitle {
    display: flex;
    flex-direction: row;
    align-items: center;
    width: 100%;
  }

  .header h1 {
    padding: 0;
  }

  .title {
    width: 50%;
    padding: 0 20px;
  }

  .seeAll {
    width: 50%;
    padding: 0 20px;
    color: rgb(0, 119, 255);
    text-align: end;
  }
</style>