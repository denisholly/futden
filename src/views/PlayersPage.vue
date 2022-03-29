<template>
  <ion-page>
    <ion-header>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-grid>
        <ion-row>
          <div class="fullTitle">
            <h1 class="title">Manager</h1>
          </div>
        </ion-row>
        <ion-row>
          <div class="fullTitle">
            <h1 class="title">Players</h1>
          </div>
          <players-list></players-list>
        </ion-row>
      </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonHeader, IonContent } from '@ionic/vue';
import PlayersList from '@/components/PlayersList.vue';

export default  {
  components: { IonHeader, IonContent, IonPage, PlayersList }
}
</script>

<style scoped>
  h1 {
    padding: 0 20px;
  }

  .fullTitle {
    width: 100%;
    border-bottom: 2px solid rgb(41, 41, 41);
    margin-bottom: 20px;
  }

  .managerSection {
      margin: auto;
      width: 95%;
      background-color: rgb(41, 41, 41);
      height: 200px;
  }

</style>