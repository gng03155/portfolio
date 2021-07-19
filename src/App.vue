<template>
  <div>
    <Mainmenu v-bind:numbers="[homeTop, projectTop, archiveTop, contactTop]" />
    <Home ref="homeRef" />
    <Projects ref="projectRef" />
    <Archive ref="archiveRef" />
    <Contact ref="contactRef" />
  </div>
</template>

<script lang="ts">
import { ref, defineComponent, onBeforeMount, onMounted, watch } from "vue";
import Mainmenu from "./components/Mainmenu.vue";
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
    Mainmenu,
  },
  setup() {
    const homeRef = ref(null);
    const projectRef = ref(null);
    const archiveRef = ref(null);
    const contactRef = ref(null);
    let homeTop = ref(0);
    let projectTop = ref(0);
    let archiveTop = ref(0);
    let contactTop = ref(0);
    const handleScroll = function () {
      const scrollTop = window.scrollY;
      const windowHeight = window.innerHeight;
      const curScroll = scrollTop + windowHeight;
      const archive = archiveRef.value as any;

      // if (curScroll >= homeTop.value) {
      //   console.log("home");
      // }
      // if (curScroll >= projectTop.value) {
      //   console.log("pro");
      // }
      if (curScroll >= archiveTop.value) {
        archive.$el.firstElementChild.classList.add("wrap");
      } else {
        archive.$el.firstElementChild.classList.remove("wrap");
      }
    };
    watch(projectTop, (projectTop, prevProjectTop) => {
      console.log(projectTop);
      console.log(prevProjectTop);
    });
    onBeforeMount(() => {
      // 핸들러 등록하기
      window.addEventListener("scroll", handleScroll);
    });
    onMounted(() => {
      const home = homeRef.value as any;
      const project = projectRef.value as any;
      const archive = archiveRef.value as any;
      const contact = contactRef.value as any;
      homeTop.value = home.$el.offsetTop;
      projectTop.value = project.$el.offsetTop;
      archiveTop.value = archive.$el.offsetTop;
      contactTop.value = contact.$el.offsetTop;
    });
    return {
      homeTop,
      projectTop,
      archiveTop,
      contactTop,
      homeRef,
      projectRef,
      archiveRef,
      contactRef,
      handleScroll,
    };
  },
});
</script>

<style>
body {
  width: 100%;
  overflow-x: hidden;
}
body h2 {
  text-transform: uppercase;
  text-align: center;
  font-size: 30px;
  border: 1px solid #000;
  margin-bottom: 50px;
}
</style>
