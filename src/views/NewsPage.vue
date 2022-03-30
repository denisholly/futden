<template>
  <ion-page>
    <ion-content :fullscreen="true">
      <ion-grid>
        <ion-row>
          <div class="fullTitle">
            <h1 class="title">News</h1>
          </div>
        </ion-row>
        <ion-row v-if="nodeNews">
          <ion-card v-for="card in nodeNews" :key="card.id">
            <img :src="setCardBg(card.img)">
            <ion-card-header>
              <ion-card-subtitle> {{ card.tag }} </ion-card-subtitle>
              <ion-card-title> {{ card.title }} </ion-card-title>
            </ion-card-header>
          </ion-card>
        </ion-row>
      </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonContent } from '@ionic/vue';
import { defineComponent } from '@vue/runtime-core';
import axios from 'axios';

export default defineComponent({
  components: { IonContent, IonPage },
  data () {
    return {
      nodeNews: null,
    }
  },
  methods: {
    setCardBg (url : any) {
      const editedUrl = url.slice(0, -11) + "100"; 
      return editedUrl;
    }
  },
  async created () {
    try {
      const { data } = await axios.get('http://localhost:3000/goal-com/fetched-news')
      this.nodeNews = data;
    } catch (err) {
      console.log(err);
    }
  },
})


</script>

<style scoped>
  h1 {
    padding: 0 20px;
  }

  .fullTitle {
    width: 100%;
    border-bottom: 2px solid rgb(41, 41, 41);
  }

  .newsCard {
    margin: auto;
    width: 80%;
  }

  .left {
    width: 50%;
    float: left;
  }

  .right {
    width: 50%;
    float: right;
  }

  ion-row {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  ion-card {
    width: 80%;
    margin: 20px auto;
    
  }

  ion-card-subtitle {
    color: dodgerblue;
  }

</style>