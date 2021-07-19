<template>
  <div id="mainmenu">
    <ul>
      <li>
        <a class="f_gmarket" v-on:click="onClickMenu('home')">about</a>
      </li>
      <li>
        <a class="f_gmarket" v-on:click="onClickMenu('projects')">projects</a>
      </li>
      <li>
        <a class="f_gmarket" v-on:click="onClickMenu('archive')">archive</a>
      </li>
      <li>
        <a class="f_gmarket" v-on:click="onClickMenu('contact')">contact</a>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { ref, defineComponent, watchEffect } from "vue";

export default defineComponent({
  name: "Mainmenu",
  props: {
    numbers: {
      type: Array,
      required: true,
      default: () => [0, 0, 0, 0],
    },
  },
  setup(props) {
    const roop = ref(0);
    const onClickMenu = (name: string) => {
      const step = 20;
      const between = 1;
      const speed = 0.1;
      switch (name) {
        case "home": {
          const move =
            typeof props.numbers[0] === "number" ? props.numbers[0] : 0;
          clearOut();
          roop.value = setTimeout(
            () => smoothScroll(move, step, speed),
            between
          );
          break;
        }
        case "projects": {
          const move =
            typeof props.numbers[1] === "number" ? props.numbers[1] : 0;
          clearOut();
          roop.value = setTimeout(
            () => smoothScroll(move, step, speed),
            between
          );
          break;
        }
        case "archive": {
          const move =
            typeof props.numbers[2] === "number" ? props.numbers[2] : 0;
          clearOut();
          roop.value = setTimeout(
            () => smoothScroll(move, step, speed),
            between
          );
          break;
        }
        case "contact": {
          const move =
            typeof props.numbers[3] === "number" ? props.numbers[3] : 0;
          clearOut();
          roop.value = setTimeout(
            () => smoothScroll(move, step, speed),
            between
          );
          break;
        }
        default:
          break;
      }
    };
    const clearOut = () => {
      if (typeof roop.value === "number") {
        clearTimeout(roop.value);
      }
    };
    const smoothScroll = (move: number, step: number, speed: number) => {
      const curPos = window.scrollY;
      if (curPos === move) {
        return;
      }
      const curSpeed = speed + 0.05;
      const curStep = step + curSpeed;
      const movePos =
        curPos < move
          ? curPos + curStep > move
            ? move
            : curPos + curStep
          : curPos - curStep < move
          ? move
          : curPos - curStep;
      window.scrollTo(0, movePos);
      roop.value = setTimeout(() => smoothScroll(move, curStep, curSpeed), 1);
    };
    watchEffect(() => {
      console.log(props.numbers);
    });
    // watch(props.numbers, (newProps, prevProps) => {
    //   console.log(newProps);
    //   console.log(prevProps);
    // });
    return {
      roop,
      onClickMenu,
    };
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#mainmenu {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 80px;
  display: flex;
  justify-content: center;
  background: #efefef;
  z-index: 1000;
}

ul {
  display: flex;
  align-items: center;
  text-transform: uppercase;
  margin: 0 auto;
}
a {
  display: inline-block;
  font-size: 20px;
  padding-left: 20px;
  padding-right: 20px;
  cursor: pointer;
}
</style>
