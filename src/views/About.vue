<template>
  <div class="about">
    <transition appear @before-enter="beforeEnter" @enter="enter">
      <h1 class="mb-5 text-xl">About</h1>
    </transition>
    <transition appear name="paragraph">
      <div v-if="showP">
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam
          officia possimus delectus inventore quod quisquam culpa voluptas
          iusto, quae maiores quo dolorum, corporis laboriosam a dolore
          consequatur assumenda nam!
        </p>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam
          officia possimus delectus inventore quod quisquam culpa voluptas
          iusto, quae maiores quo dolorum, corporis laboriosam a dolore
          consequatur assumenda nam!
        </p>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam
          officia possimus delectus inventore quod quisquam culpa voluptas
          iusto, quae maiores quo dolorum, corporis laboriosam a dolore
          consequatur assumenda nam!
        </p>
      </div>
    </transition>
  </div>
</template>

<script>
import gsap from 'gsap';
import { ref } from 'vue';
export default {
  setup() {
    const showP = ref(false);
    const beforeEnter = (el) => {
      gsap.from(el, {
        y: -30,
        opacity: 0,
      });
    };
    const enter = (el, done) => {
      gsap.to(el, {
        duration: 0.5,
        y: 0,
        opacity: 1,
        onComplete: done,
      });
      setTimeout(() => {
        showP.value = true;
      }, 250);
    };
    return {
      beforeEnter,
      enter,
      showP,
    };
  },
};
</script>

<style>
.about {
  max-width: 600px;
  margin: 20px auto;
}
.paragraph-enter-from {
  transform: translateX(30px);
  opacity: 0;
}
.paragraph-enter-active {
  transition: all 0.5s ease;
}
</style>
