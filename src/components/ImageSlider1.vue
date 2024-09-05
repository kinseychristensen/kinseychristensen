<script setup>
import { ref, onUnmounted } from 'vue';

const images = [
        { src: 'src/assets/informative_images/home_view.png', 
        alt: 'mobile home', 
       
      },
      { src: 'src/assets/informative_images/create_class.png',
        alt: 'desktop create class page', 
        
      },
      { src: 'src/assets/informative_images/create_subject.png',
        alt: 'desktop create subject page', 
    },
        
        { src: 'src/assets/informative_images/subject_database.png',
        alt: 'desktop subject search page', 
      },

      { src: 'src/assets/informative_images/class_roster.png',
        alt: 'mobile class roster', 
        
      },
      { src: 'src/assets/informative_images/groups.png',
        alt: 'mobile groups page', 
        
      },
      { src: 'src/assets/informative_images/artifact.png',
        alt: 'desktop create artifact page', 
        
      },
      { src: 'src/assets/informative_images/subject_page.png',
        alt: 'desktop subject page', 
        
      },
      { src: 'src/assets/informative_images/student_page.png',
        alt: 'desktop student page', 
        
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
      

        <div class="slider flex h-[50%]">
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
    width: 90vw;
    height: auto;
}
@media (min-width: 1024px){
    .photo {
    max-width: 600px;
    max-height: 600px;
    margin: auto;
}
}
</style>