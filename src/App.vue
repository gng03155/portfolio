<template>
  <div>
    <Home ref="homeRef" />
    <Projects ref="projectRef" />
    <Archive ref="archiveRef" />
    <Contact />
  </div>
</template>

<script lang="ts">
import { ref, defineComponent, onBeforeMount, onMounted } from "vue";
import Home from "./components/home.vue";
import Projects from "./components/Projects.vue";
import Archive from "./components/archiving.vue";
import Contact from "./components/contact.vue";

export default defineComponent({
  name: "App",
  components: {
    Home,
    Projects,
    Archive,
    Contact,
  },
  setup() {
    const homeRef = ref(null);
    const projectRef = ref(null);
    const archiveRef = ref(null);
    let homeTop = ref(0);
    let projectTop = ref(0);
    let archiveTop = ref(0);
    const handleScroll = function () {
      const scrollTop = window.scrollY;
      const windowHeight = window.innerHeight;
      const curScroll = scrollTop + windowHeight;

      if (curScroll >= homeTop.value) {
        console.log("home");
      }
      if (curScroll >= projectTop.value) {
        console.log("pro");
      }
      if (curScroll >= archiveTop.value) {
        const archive = archiveRef.value as any;
        archive.$el.firstElementChild.classList.add("wrap");
      }
    };
    onBeforeMount(() => {
      // 핸들러 등록하기
      window.addEventListener("scroll", handleScroll);
    });
    onMounted(() => {
      const home = homeRef.value as any;
      const project = projectRef.value as any;
      const archive = archiveRef.value as any;
      homeTop = ref(home.$el.offsetTop);
      projectTop = ref(project.$el.offsetTop);
      archiveTop = ref(archive.$el.offsetTop);
    });
    return {
      homeTop,
      projectTop,
      archiveTop,
      homeRef,
      projectRef,
      archiveRef,
      handleScroll,
    };
  },
});
</script>

<style>
html,
body {
  overflow-x: hidden;
}

h2 {
  text-transform: uppercase;
  font-size: 30px;
  margin-bottom: 50px;
}
</style>
