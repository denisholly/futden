<template>
  <ion-app>
    <ion-router-outlet />
  </ion-app>
</template>

<script lang="js">
import { IonApp, IonRouterOutlet } from '@ionic/vue';
import { defineComponent } from 'vue';

export default defineComponent({
  components: {
    IonApp,
    IonRouterOutlet,
  },
});
</script>

<style scoped> 
</style>