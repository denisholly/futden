<template>
    <ion-slides v-if="nodeNews" pager="false" :options="slideOpts">
        <ion-slide v-for="card in nodeNews" :key="card.tag">
            <div class="up" :style="{ backgroundImage: 'url(' + card.img + ')' }">

            </div>
            <div class="down">
                <!-- <ion-chip>
                    <ion-label color="secondary">Secondary Label</ion-label>
                </ion-chip> -->
                <p> {{ card.title }} </p>
            </div>
        </ion-slide>
    </ion-slides>
</template>

<script> 
import { defineComponent } from 'vue';
import { IonSlides, IonSlide } from '@ionic/vue';
import axios from 'axios';

export default defineComponent({
    components: { IonSlides, IonSlide },
    data() {
        return {
            slideOpts: {
                initialSlide: 0,
                slidesPerView: 3,
                centeredSlides: false,
                loop: false,
                spaceBetween: -10,
            },
            nodeNews: null
        }
    },
    computed: {
        setBg() {
            return "background-image: url('');";
        }
    },
        async created () {
        // await axios.get('http://localhost:3000/goal-com/fetched-news')
        //     .then(res => {
        //         const nodeNews = res.data;
        //         console.log('News', nodeNews);
        //         this.nodeNews.push(nodeNews);
        //     })
        //     .catch(error => console.log(error))

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
    ion-slides {
        color: black;
        margin-top: 20px;
        min-height: 150px;
    }

    ion-slide {
        margin-left: 40px;
        flex-direction: column;
        border-radius: 10px; 
    }


    .up {
        height: 70%;
        width: 100%;
        border-radius: 10px;
        background-size: cover;
        background-repeat: no-repeat;
        background-position: 50% 50%;
    }

    .down {
        min-height: 30%;
        color: white;
        font-size: 12px;
        text-align: left;
    }

</style>
