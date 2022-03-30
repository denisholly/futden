<template>
  <ion-page>
    <ion-header>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-grid>
        <ion-row>
          <div class="fullTitle">
            <h1 class="title">League Table</h1>
          </div>
          <league-table></league-table>
        </ion-row>
      </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonHeader, IonContent } from '@ionic/vue';
import LeagueTable from '@/components/LeagueTable.vue';

export default  {
  components: { IonHeader, IonContent, IonPage, LeagueTable }
}
</script>

<style scoped>
  h1 {
    padding: 0 20px;
  }

  .fullTitle {
    width: 100%;
    border-bottom: 2px solid rgb(41, 41, 41);
  }
  
</style>