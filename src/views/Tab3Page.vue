<template>
  <ion-page>
    <ion-header>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">League Table</ion-title>
        </ion-toolbar>
      </ion-header>
        <home-table></home-table>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import HomeTable from '@/components/HomeTable.vue';

export default  {
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage, HomeTable }
}
</script>