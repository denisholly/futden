<template>
    <ion-slides pager="false" :options="slideOpts">
        <ion-slide>
            Transfers
        </ion-slide>
        <ion-slide>
            News
        </ion-slide>
        <ion-slide>
            Players
        </ion-slide>
        <ion-slide>
            Players
        </ion-slide>
    </ion-slides>
</template>

<script> 
import { defineComponent } from 'vue';
import { IonSlides, IonSlide } from '@ionic/vue';
import { swapHorizontal, newspaper, shirt } from 'ionicons/icons';

export default defineComponent({
    components: { IonSlides, IonSlide },
    setup() {
        // Optional parameters to pass to the swiper instance. See http://idangero.us/swiper/api/ for valid options.
        const slideOpts = {
            initialSlide: 0,
            slidesPerView: 7,
            centeredSlides: false,
            loop: false,
            spaceBetween: -10,
        };
        return { slideOpts, swapHorizontal, newspaper, shirt }
    }, 
});
</script>

<style scoped>
    ion-slides {
        color: white;
        min-height: 30px;
        width: 100%;
    }

    ion-slide {
        font-size: 12px;
        margin-left: 40px;
        flex-direction: column;
        border-radius: 8px;
        background-color: rgb(0, 119, 255); 
    }

</style>
