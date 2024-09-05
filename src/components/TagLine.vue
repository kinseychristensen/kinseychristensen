<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>

<template>
  <div class="greetings">
    <h1 class="pink">{{ msg }}</h1>
    <h3>Junior Software Developer </h3>
    <h4>Accessibility Enthusiast | Mentorship Advocate |
     Story Devourer | Cozy Gamer | Cat Mom | Auntie </h4>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
  font-style: bold;
  line-height: normal;
}

h3 {
  font-size: 1.2rem;
  line-height: normal;
}

.greetings h1,
.greetings h3,
.greetings {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3, 
  .greetings h4 {
    text-align: left;
  }
}
</style>
