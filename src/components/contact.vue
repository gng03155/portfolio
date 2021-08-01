<template>
  <div id="contact">
    <div class="content">
      <div class="card" ref="cardRef">
        <div class="wall" ref="wallRef"></div>
        <div class="front" ref="frontRef"></div>
        <div class="back" ref="backRef"></div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { ref, defineComponent, onMounted } from "vue";

export interface newMouseEvent extends MouseEvent {
  sourceCapabilities: {
    firesTouchEvents: boolean;
  };
}

export default defineComponent({
  name: "Contact",
  setup() {
    const cardRef = ref(null);
    const frontRef = ref(null);
    const backRef = ref(null);
    const wallRef = ref(null);
    const cnt = ref(1);
    const moving = ref(false);
    const calcDeg = (type: any) => {
      const values = type.split("(")[1].split(")")[0].split(",");
      const a = values[0];
      const b = values[1];
      let angle = Math.round(
        Math.atan2(Number(b), Number(a)) * (180 / Math.PI)
      );
      if (angle < 0) {
        console.log(360 + angle);
      }
      console.log(angle);
      return angle;
    };
    const handleMouseOver = (e: newMouseEvent | TouchEvent) => {
      if (e instanceof MouseEvent) {
        const isTouch = e.sourceCapabilities.firesTouchEvents;
        if (isTouch) {
          return;
        }
      }
      if (moving.value) {
        return;
      }
      const front = frontRef.value as any;
      const back = backRef.value as any;
      front.style.transform = `perspective(800px) rotateY(${
        180 * cnt.value
      }deg)`;
      back.style.transform = `perspective(800px) rotateY(${
        180 * (cnt.value + 1)
      }deg)`;
      cnt.value = cnt.value + 1;
      moving.value = true;
      setTimeout(() => {
        moving.value = false;
      }, 1000);
    };
    onMounted(() => {
      const card = cardRef.value as any;
      const wall = wallRef.value as any;
      wall.addEventListener("mouseover", handleMouseOver);
      wall.addEventListener("mouseout", handleMouseOver);
      wall.addEventListener("touchend", handleMouseOver);
    });
    return {
      cardRef,
      frontRef,
      backRef,
      wallRef,
      calcDeg,
      handleMouseOver,
    };
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#contact {
  width: 100%;
  height: 100vh;
}
.content {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.test img {
  width: 400px;
  height: 300px;
  display: block;
  /* image-rendering: -moz-crisp-edges; 
  image-rendering: -o-crisp-edges; 
  image-rendering: -webkit-optimize-contrast; 
  image-rendering: crisp-edges;
  -ms-interpolation-mode: nearest-neighbor; IE (non-standard property) */
}

.wrap .card {
  animation: fade_card 0.5s linear forwards;
}

@keyframes fade_card {
  from {
    top: 150px;
    opacity: 0;
  }
  to {
    top: 0px;
    opacity: 1;
  }
}

.card {
  position: relative;
  width: 600px;
  height: 360px;
}

.card > div {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  transition: transform 1.5s;
  perspective-origin: center;
  border-radius: 20px;
}

.wall {
  z-index: 100;
}

.front {
  background: url("../assets/imgs/dark_front.png") no-repeat;
  background-size: 100% 100%;
  transform: perspective(800px) rotateY(0deg);
  transform-origin: center;
  z-index: 10;
}

.back {
  background: url("../assets/imgs/dark_back.png") no-repeat;
  background-size: 100% 100%;
  transform: perspective(800px) rotateY(180deg);
  z-index: 10;
}

@media screen and (max-width: 1024px) {
  .card {
    width: 600px;
    height: 360px;
  }
}
@media screen and (max-width: 768px) {
  .card {
    width: 480px;
    height: 360px;
  }
}
@media screen and (max-width: 480px) {
  .card {
    width: 320px;
    height: 240px;
  }
}
</style>
