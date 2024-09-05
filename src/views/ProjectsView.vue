<template>
  <div class="projects">
    
    <nav class="project-nav">
      <button @click="showInformative">inFormative</button>
      <button @click="showFlip">Flip Flash</button>
      <button @click="showTenmo">Tenmo</button>
      <button @click="showFuture"><a id="future">Future</a><a id="projects"> Future Projects</a></button>
    </nav>


    <div id="informative" v-if="informative">
      <InformativeDetails/>
    </div>
    <div id="flip-flash" v-if="flipFlash">
      <FlipFlashDetails/>
    </div>
    <div id="tenmo" v-if="tenmo">
      <TenmoDetails/>
  </div>
  <div class="future" v-if="futureProjects">
   <FutureProjectDetails/>
  </div>
  </div>
</template>
<script>
import InformativeDetails from '@/components/InformativeDetails.vue';
import FlipFlashDetails from '@/components/FlipFlashDetails.vue';
import TenmoDetails from '@/components/TenmoDetails.vue';
import FutureProjectDetails from '@/components/FutureProjectDetails.vue';



export default {
  components: {
    InformativeDetails,
    FlipFlashDetails,
    TenmoDetails,
    FutureProjectDetails,
  },
  data(){
    return {
      informative: true,
      flipFlash: false,
      tenmo: false,
      futureProjects: false,
    }
  }, 
  methods: {
    showInformative(){
      this.informative = true;
      this.flipFlash = false;
      this.tenmo = false;
      this.futureProjects = false;
    },
    showFlip(){
      this.informative = false;
      this.flipFlash = true;
      this.tenmo = false;
      this.futureProjects = false;
    },
    showTenmo(){
      this.informative = false;
      this.flipFlash = false;
      this.tenmo = true;
      this.futureProjects = false;
    },
    showFuture(){
      this.informative = false;
      this.flipFlash = false;
      this.tenmo = false;
      this.futureProjects = true;
    }
  }
  

}




</script>

<style>

.project-nav{
display: flexbox;
flex-direction: row;
max-width: 100vw;
flex-wrap: nowrap;


}
button{

  padding: 2px;
  height: 30px;
  width: 70px;
  border: black;
  background-color: rgb(238, 201, 207);
  color: black;
  border-radius: 5px;
  font-size: small;
  cursor: pointer;
  transition: background-color .3s ease;
  font-family:Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
margin: 2px;
}
#future{
display: normal;
}
#projects{
  display: none;
}

@media (min-width: 1024px) {

  #future{
    display: none;
}
#projects{
  display: block;
}

    .project-nav{
display: flex;
flex-direction: row;
align-items: center;
flex-wrap: nowrap;

}
button{

padding: 2px;
height: 30px;
width: 170px;
border: black;
background-color: rgb(238, 201, 207);
color: black;
border-radius: 5px;
font-size: small;
cursor: pointer;
transition: background-color .3s ease;
font-family:Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
margin: 5px;
}
}
</style>
