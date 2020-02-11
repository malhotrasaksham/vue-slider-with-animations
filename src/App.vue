<template>
  <div id="app">
    <transition name="slide" mode="out-in" appear>
      <template v-for="(slide, index) in slides">
        <div class="slide" :key="index" v-if="index === activeSlide">{{slide.content}}</div>
      </template>
    </transition>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      slides: [
        { id: 1, content: "First Slide" },
        { id: 2, content: "Second Slide" },
        { id: 3, content: "Third Slide" }
      ],
      slideCounter: 0
    };
  },
  computed: {
    activeSlide() {
      return this.slideCounter % 3;
    }
  },
  mounted() {
    setInterval(_ => {
      this.slideCounter++;
    }, 6000);
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.slide {
  box-shadow: 0px 0px 3px #DDD;
  background-color: #fafafa;
  padding: 10px;
  height: 200px;
  width: 200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
}

.slide-enter {
  opacity: 0;
}
.slide-enter-active {
  transition: 1s opacity;
}
.slide-leave {
}
.slide-leave-active {
  transition: 1s opacity;
  opacity: 0;
}
</style>
