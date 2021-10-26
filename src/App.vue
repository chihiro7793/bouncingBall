<template>
  <div id="app">
    <h3>Bounce the Ball!</h3>
    <button @click="show = !show">
      Toggle
    </button>
    <transition
      name="ballmove"
      @before-enter="beforeEnter"
      @enter="enter"
      @leave="leave"
      :css="false"
    >
      <bouncing-ball v-if="show" class="child"></bouncing-ball>
    </transition>
  </div>
</template>

<script>
import BouncingBall from './components/BouncingBall.vue';
import gsap from 'gsap';

export default {
  name: 'App',
  components: {
    BouncingBall
  },
  data() {
    return {
      show: false
    };
  },
  mounted() {
    this.show = true;
    setTimeout(() => {
      this.show = false;
    }, 1500);
  },
  methods: {
    beforeEnter(el) {
      el.style.opacity = 0;
      el.style.transform = 'translateY(0)';
    },
    enter(el, done) {
      gsap.to(el, {
        duration: 1,
        y: 400,
        opacity: 1,
        ease: 'bounce.out',
        onComplete: done
      });
    },
    leave(el, done) {
      gsap.to(el, {
        duration: 3,
        x: 600,
        rotate: 360,
        ease: 'out',
        onComplete: done
      });
    }
  }
};
</script>
