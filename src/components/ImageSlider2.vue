<script setup>
import { ref, onUnmounted } from 'vue';

const images = [
        { src: 'src/assets/flip_images/admin_decks.png', 
        alt: 'view of admin page', 
       
      },
      { src: 'src/assets/flip_images/deck_page.png',
        alt: 'view of user decks', 
        
      },
      { src: 'src/assets/flip_images/update_deck.png',
        alt: 'view of update deck page', 
        
      },
      { src: 'src/assets/flip_images/create_card.png',
        alt: 'view of create card page', 
        
      },
      { src: 'src/assets/flip_images/search_cards.png',
        alt: 'view of card page with search bar', 
        
      },
      { src: 'src/assets/flip_images/study_session.png',
        alt: 'view of study session page', 
        
      },
];

const currentSliderIndex = ref(0);
let intervalId;

const isTimerPaused = ref(false);

const nextSlide = () => {
    currentSliderIndex.value = (currentSliderIndex.value + 1) % images.length;
    isTimerPaused.value ? '' : startSlider()
};

const prevSlide = () => {
    currentSliderIndex.value = (currentSliderIndex.value - 1 + images.length) % images.length;
    isTimerPaused.value ? '' : startSlider()
};

const startSlider = () => {
    intervalId = setInterval(() => {
        nextSlide();
    }, 5000);
};

const playSlider = () => {
    isTimerPaused.value = false;
    startSlider();
}

const stopSlider = () => {
    clearInterval(intervalId);
    isTimerPaused.value = true;
}

startSlider();

onUnmounted(() => {
    clearInterval(intervalId);
});
</script>

<template>
    <div class="h-screen flex flex-col">
        <div class="bg-slate-500 text-center p-4 uppercase text-gray-50">
           
        </div>
      

        <div class="slider flex h-[100%]">
            <div class="flex mx-auto justify-center relative w-[500px] h-[300px] m-auto">
                <template v-for="(image, index) in images" :key="index">
                    <transition name="fade">
                        <img :src="image.src" :alt="image.alt" class="photo"
                            v-if="index === currentSliderIndex" />
                    </transition>
                </template>

                <!-- next and previous buttons -->
                <i class="fas fa-caret-right absolute right-0 top-1/3 text-4xl m-2 cursor-pointer text-white z-50"
                    @click="nextSlide"></i>
                <i class="fas fa-caret-left absolute left-0 top-1/3 text-4xl m-2 cursor-pointer text-white z-50"
                    @click="prevSlide"></i>

                <!-- play or pause buttons -->
                <i class="fa-solid fa-circle-play absolute bottom-5 text-3xl m-2 cursor-pointer text-gray-500 z-50"
                    @click="playSlider" v-if="isTimerPaused"></i>
                <i class="fa-solid fa-pause absolute bottom-5 text-3xl  m-2 cursor-pointer shadow-2xl text-gray-500 z-50"
                    @click="stopSlider" v-else></i>
            </div>
        </div>
    </div>

</template>

<style>
.fade-enter-active,
.fade-leave-active {
    transition: opacity 1s, transform 1s;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
    transform: translateX(0);
}
.photo {
    max-width: 90vw;
    height: auto;
}
@media (min-width: 1024px){
    .photo {
    max-width: 600px;
    height: auto;
    margin: auto;
}
}
</style>