<template>
  <div id="menu">
    <ul>
      <li>
        <a
          ref="homeRef"
          class="f_gmarket active"
          v-on:click="onClickMenu('home')"
          >home</a
        >
      </li>
      <li>
        <a ref="proRef" class="f_gmarket" v-on:click="onClickMenu('projects')"
          >projects</a
        >
      </li>
      <li>
        <a ref="arRef" class="f_gmarket" v-on:click="onClickMenu('archive')"
          >archive</a
        >
      </li>
      <li>
        <a ref="conRef" class="f_gmarket" v-on:click="onClickMenu('contact')"
          >contact</a
        >
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { ref, defineComponent, onMounted, watchEffect, watch } from "vue";

export default defineComponent({
  name: "Menu",
  props: {
    numbers: {
      type: Array,
      required: true,
      default: () => [0, 0, 0, 0],
    },
    curArea: {
      type: String,
      required: true,
      default: "",
    },
  },
  setup(props) {
    const homeRef = ref<null | HTMLDivElement>(null);
    const proRef = ref<null | HTMLDivElement>(null);
    const arRef = ref<null | HTMLDivElement>(null);
    const conRef = ref<null | HTMLDivElement>(null);
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
          // home.classList.add("active");
          // pro.classList.remove("active");
          // ar.classList.remove("active");
          // con.classList.remove("active");
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
          // home.classList.remove("active");
          // pro.classList.add("active");
          // ar.classList.remove("active");
          // con.classList.remove("active");
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
          // home.classList.remove("active");
          // pro.classList.remove("active");
          // ar.classList.add("active");
          // con.classList.remove("active");
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
          // home.classList.remove("active");
          // pro.classList.remove("active");
          // ar.classList.remove("active");
          // con.classList.add("active");
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
      // const curPos = window.top.scrollY;
      const curPos = Math.ceil(window.top.scrollY);
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
    // watchEffect((aa) => {
    //   console.log(aa);
    // });
    watch(
      () => props.curArea,
      (newProps: string, prevProps: string) => {
        console.log(
          `change Props : curArea , prev : ${prevProps} , new : ${newProps}`
        );
        const home = homeRef.value as HTMLDivElement;
        const pro = proRef.value as HTMLDivElement;
        const ar = arRef.value as HTMLDivElement;
        const con = conRef.value as HTMLDivElement;
        switch (newProps) {
          case "home": {
            home.classList.add("active");
            pro.classList.remove("active");
            ar.classList.remove("active");
            con.classList.remove("active");
            break;
          }
          case "projects": {
            home.classList.remove("active");
            pro.classList.add("active");
            ar.classList.remove("active");
            con.classList.remove("active");
            break;
          }
          case "archive": {
            home.classList.remove("active");
            pro.classList.remove("active");
            ar.classList.add("active");
            con.classList.remove("active");
            break;
          }
          case "contact": {
            home.classList.remove("active");
            pro.classList.remove("active");
            ar.classList.remove("active");
            con.classList.add("active");
            break;
          }
          default:
            break;
        }
      }
    );
    return {
      homeRef,
      proRef,
      arRef,
      conRef,
      roop,
      onClickMenu,
    };
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#menu {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 80px;
  display: flex;
  justify-content: center;
  background-color: rgba(0, 0, 0, 0.5);
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
  font-weight: 500;
  color: #fff;
}

a.active {
  font-weight: 700;
}
</style>
