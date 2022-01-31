<template>
    <ion-slides pager="false" :options="slideOpts">
        <ion-slide v-for="card in news.slice().reverse()" :key="card.id">
            <div class="up" :style="{ backgroundImage: 'url(' + card.url + ')' }">

            </div>
            <div class="down">
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
            slidesPerView: 1.3,
            centeredSlides: true,
            loop: true,
            spaceBetween: 30,
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
        min-height: 300px;
    }

    ion-slide {
        flex-direction: column;
        border-radius: 20px;
        background-color: #222325;
    }


    .up {
        height: 70%;
        width: 100%;
        border-radius: 20px 20px 0 0;
        background-size: cover;
        background-repeat: no-repeat;
        background-position: 50% 50%;
    }

    .down {
        min-height: 30%;
        padding: 0 20px;
        color: white;
        font-size: 17px;
        font-weight: bold;
        text-align: left;
    }
</style>
