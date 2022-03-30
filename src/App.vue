<template>
  <ion-app>
    <ion-router-outlet />
  </ion-app>
</template>

<script lang="js">
import { IonApp, IonRouterOutlet } from '@ionic/vue';
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      news: [
        {
          id: 0, 
          title: "Werner: I don't know why Chelsea fans support me so much!",
          desc: 'adfasd',
          url: 'https://eu-images.contentstack.com/v3/assets/bltcc7a7ffd2fbf71f5/bltcd406b9d35f527bf/61587155fc8c5c7f48c43b4b/0165bf696bc2d06726eab9b372086c7df45becf3.jpg?auto=webp&format=pjpg&quality=80&width=1024'
        },
        {
          id: 1, 
          title: 'The Best FIFA awards 2021: Lewandowski leads FIFPro World XI',
          desc: 'adjfklasjdlfajsdkfjalsdjfkaldj',
          url: 'https://eu-images.contentstack.com/v3/assets/bltcc7a7ffd2fbf71f5/blt7149f2d18b7dcc0c/60db0748fd14d30f3eab8477/f195f00721396962977fff185cdc5c8ffe748b57.jpg?auto=webp&fit=crop&format=jpg&quality=100'
        },
        {
          id: 2, 
          title: "Are Manchester City turning English football into a Farmer's League?",
          desc: 'adjfklasjdlfajsdkfjalsdjfkaldj',
          url: 'https://eu-images.contentstack.com/v3/assets/bltcc7a7ffd2fbf71f5/blta5267a7a099ab7d6/61e36998570a34267b955d36/GettyImages-1237737684.jpg?auto=webp&format=pjpg&quality=80&width=1440'
        },
        {
          id: 3, 
          title: 'The Best FIFA awards 2021: Lewandowski leads FIFPro World XI',
          desc: 'adjfklasjdlfajsdkfjalsdjfkaldj',
          url: 'https://eu-images.contentstack.com/v3/assets/bltcc7a7ffd2fbf71f5/blt7149f2d18b7dcc0c/60db0748fd14d30f3eab8477/f195f00721396962977fff185cdc5c8ffe748b57.jpg?auto=webp&fit=crop&format=jpg&quality=100'
        },
        {
          id: 4, 
          title: "Werner: I don't know why Chelsea fans support me so much!",
          desc: 'adfasd',
          url: 'https://eu-images.contentstack.com/v3/assets/bltcc7a7ffd2fbf71f5/bltcd406b9d35f527bf/61587155fc8c5c7f48c43b4b/0165bf696bc2d06726eab9b372086c7df45becf3.jpg?auto=webp&format=pjpg&quality=80&width=1024'
        },
      ],
    }
  },
  provide() {
    return {
      news: this.news,
      teams: this.teams,
    };
  },
  components: {
    IonApp,
    IonRouterOutlet,
  },
});
</script>

<style scoped> 
</style>