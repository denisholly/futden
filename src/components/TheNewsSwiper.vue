<template>
    <ion-slides pager="false" :options="slideOpts">
        <ion-slide v-for="card in news.slice().reverse()" :key="card.id">
            <div class="up" :style="{ backgroundImage: 'url(' + card.url + ')' }">

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

export default defineComponent({
    inject: ['news'],
    components: { IonSlides, IonSlide },
    setup() {
        // Optional parameters to pass to the swiper instance. See http://idangero.us/swiper/api/ for valid options.
        const slideOpts = {
            initialSlide: 0,
            slidesPerView: 3,
            centeredSlides: false,
            loop: false,
            spaceBetween: -10,
        };
        return { slideOpts }
    },
    computed: {
        setBg() {
            return "background-image: url('');";
        }
    },
});
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
