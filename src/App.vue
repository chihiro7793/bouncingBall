<template>
  <div id="app">
      <h3>Bounce the Ball!</h3>
  <transition
    name="ballmove"
    enter-active-class="bouncein"
    leave-active-class="rollout" 
   >
  <div v-if="show">
    <bouncing-ball class="child"></bouncing-ball>
  </div>
  </transition>
  </div>
</template>

<script>
import BouncingBall from './components/BouncingBall.vue';

export default {
  name: 'App',
   components: {
    BouncingBall,
  },
  data() {
    return {
      show: false 
    }
  },
  mounted(){
      this.show = true;
    
      setTimeout(()=>{
        this.show= false;
      },3000)
  },
}
</script>
