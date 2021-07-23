<template>
  <div id="home">
    <div ref="animRef" class="text_wrap anim">
      <div class="top">
        <span>w</span>
        <span>e</span>
        <span>l</span>
        <span>l</span>
        <span>c</span>
        <span>o</span>
        <span>m</span>
        <span>e</span>
      </div>
      <div class="middle">
        <span>t</span>
        <span>o</span>
      </div>
      <div class="bottom">
        <span>p</span>
        <span>o</span>
        <span>r</span>
        <span>t</span>
        <span>f</span>
        <span>o</span>
        <span>l</span>
        <span>i</span>
        <span>o</span>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from "vue";

export default defineComponent({
  name: "Home",
  setup() {
    const animRef = ref<null | HTMLDivElement>(null);
    onMounted(() => {
      animRef.value?.classList.remove("anim");
      animRef.value?.offsetWidth;
      animRef.value?.classList.add("anim");
      setInterval(() => {
        animRef.value?.classList.remove("anim");
        animRef.value?.offsetWidth;
        animRef.value?.classList.add("anim");
      }, 2700);
    });
    return { animRef };
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#home {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.text_wrap {
  padding-bottom: 60px;
}

.text_wrap div {
  position: relative;
}

.text_wrap .middle {
  display: flex;
  justify-content: center;
  margin: 40px 0;
}

/* .top span {
  background: linear-gradient(red, purple);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.middle span {
  background: linear-gradient(yellow, blue);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.bottom span {
  background: linear-gradient(blue, purple);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
} */

.text_wrap span {
  --animps: running;
  position: relative;
  text-transform: uppercase;
  margin-right: 15px;
  top: 20px;
  display: inline;
  font-size: 80px;
  /* font-family: "Press Start 2P", cursive; */
  /* font-family: "Ultra", serif; */
  /* font-family: "Monoton", cursive; */
  font-family: "Fredericka the Great", cursive;
  text-shadow: 0 1px 0 #ccc, 0 2px 0 #ccc, 0 3px 0 #ccc, 0 4px 0 #ccc,
    0 5px 0 #ccc, 0 6px 0 transparent, 0 7px 0 transparent, 0 8px 0 transparent,
    0 9px 0 transparent, 0 10px 10px rgba(0, 0, 0, 0.4);

  /* -webkit-text-stroke: 10px black;
  text-stroke: 10px black; */
}

.anim span {
  animation: bounce 0.8s ease-in-out forwards;
}

.top span:nth-child(2) {
  animation-delay: 0.1s;
}
.top span:nth-child(3) {
  animation-delay: 0.2s;
}
.top span:nth-child(4) {
  animation-delay: 0.3s;
}
.top span:nth-child(5) {
  animation-delay: 0.4s;
}
.top span:nth-child(6) {
  animation-delay: 0.5s;
}
.top span:nth-child(7) {
  animation-delay: 0.6s;
}
.top span:nth-child(8) {
  animation-delay: 0.7s;
}

.middle span:nth-child(1) {
  animation-delay: 0.8s;
}
.middle span:nth-child(2) {
  animation-delay: 0.9s;
}

.bottom span:nth-child(1) {
  animation-delay: 1s;
}
.bottom span:nth-child(2) {
  animation-delay: 1.1s;
}
.bottom span:nth-child(3) {
  animation-delay: 1.1s;
}
.bottom span:nth-child(4) {
  animation-delay: 1.3s;
}
.bottom span:nth-child(5) {
  animation-delay: 1.4s;
}
.bottom span:nth-child(6) {
  animation-delay: 1.5s;
}
.bottom span:nth-child(7) {
  animation-delay: 1.6s;
}
.bottom span:nth-child(8) {
  animation-delay: 1.7s;
}
.bottom span:nth-child(9) {
  animation-delay: 1.8s;
}

@keyframes bounce {
  50% {
    top: -50px;
    text-shadow: 0 1px 0 #ccc, 0 2px 0 #ccc, 0 3px 0 #ccc, 0 4px 0 #ccc,
      0 5px 0 #ccc, 0 6px 0 #ccc, 0 7px 0 #ccc, 0 8px 0 #ccc, 0 9px 0 #ccc,
      0 50px 25px rgba(0, 0, 0, 0.2);
  }
  100% {
    top: 20px;
    text-shadow: 0 1px 0 #ccc, 0 2px 0 #ccc, 0 3px 0 #ccc, 0 4px 0 #ccc,
      0 5px 0 #ccc, 0 6px 0 transparent, 0 7px 0 transparent,
      0 8px 0 transparent, 0 9px 0 transparent, 0 10px 10px rgba(0, 0, 0, 0.4);
  }
}
</style>
