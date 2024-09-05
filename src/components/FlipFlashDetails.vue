<template>
    <h1>Flip Flash</h1>
       <h4>Build Your Own Flash Cards Website</h4>
       <p>Flip Flash is a flash card website designed for secondary and post secondary education.  The backend 
        was created in IntelliJ using Java and springboot to speak with a PostgreSQL database.  The frontend is Vue.js.  
        Users arrive at the site and are able to preview some admin-created flash card decks.  After registering, they are able to 
        then search existing decks and cards, create their own, and run study sessions.  Using Cloudinary, the user can even upload images
        to correspond with their study terms.  
        
       </p>
       <p>This project was created as a final capstone at Tech Elevator.  The project was built over the course of 13 days by a four person team using a scrum 
        structure.  Detailed planning, frequent pair-programming, and meticulous documentation helped make this a truly successful project.  </p>

<div class="slider">
<ImageSlider2/></div>
   </template>
  
  
  
  <script>


    import ImageSlider2 from './ImageSlider2.vue';

export default {
  components: {
  
    ImageSlider2,
}, 

}
   </script>
<style>
.slider{
  margin: auto;
}</style>