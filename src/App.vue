<template>
  <div class="app">
    <Menu
      v-bind:numbers="[homeTop, projectTop, archiveTop, contactTop]"
      v-bind:curArea="curArea"
    />
    <BG />
    <Home ref="homeRef" />
    <Projects ref="projectRef" />
    <Archive ref="archiveRef" v-bind:isIn="isArchive" />
    <Contact ref="contactRef" />
    <Footer />
  </div>
</template>

<script lang="ts">
import { ref, defineComponent, onBeforeMount, onMounted } from "vue";
import Menu from "./components/Menu.vue";
import BG from "./components/BG.vue";
import Home from "./components/home.vue";
import Projects from "./components/Projects.vue";
import Archive from "./components/archiving.vue";
import Contact from "./components/contact.vue";
import Footer from "./components/Footer.vue";

export default defineComponent({
  name: "App",
  components: {
    Home,
    BG,
    Projects,
    Archive,
    Contact,
    Menu,
    Footer,
  },
  setup() {
    const init = ref(false);
    const homeRef = ref(null);
    const projectRef = ref(null);
    const archiveRef = ref(null);
    const contactRef = ref(null);
    let homeTop = ref(0);
    let projectTop = ref(0);
    let archiveTop = ref(0);
    let contactTop = ref(0);
    let curArea = ref("home");

    let isArchive = ref(false);

    const handleScroll = function () {
      const scrollTop = Math.ceil(window.top.scrollY);
      const windowHeight = window.innerHeight;
      const curScroll = scrollTop + windowHeight;
      const archive = archiveRef.value as any;
      const contact = contactRef.value as any;
      if (scrollTop >= homeTop.value) {
        curArea.value = "home";
      }
      if (scrollTop >= projectTop.value) {
        curArea.value = "projects";
      }
      if (scrollTop >= archiveTop.value) {
        curArea.value = "archive";
      }
      if (scrollTop >= contactTop.value) {
        curArea.value = "contact";
      }

      // if (curScroll >= homeTop.value) {
      // }
      // if (curScroll >= projectTop.value) {
      // }
      if (curScroll > archiveTop.value) {
        archive.$el.firstElementChild.classList.add("wrap");
        isArchive.value = true;
      } else {
        archive.$el.firstElementChild.classList.remove("wrap");
      }
      if (curScroll > contactTop.value) {
        contact.$el.firstElementChild.classList.add("wrap");
      } else {
        contact.$el.firstElementChild.classList.remove("wrap");
      }
    };
    onBeforeMount(() => {
      // 핸들러 등록하기
      window.addEventListener("scroll", handleScroll);
    });
    onMounted(() => {
      if (init.value) {
        return;
      }
      const win = window.document as any;
      win.fonts.ready
        .then(function () {
          console.log("in");
          const home = homeRef.value as any;
          const project = projectRef.value as any;
          const archive = archiveRef.value as any;
          const contact = contactRef.value as any;
          homeTop.value = home.$el.offsetTop;
          projectTop.value = project.$el.offsetTop;
          archiveTop.value = archive.$el.offsetTop;
          contactTop.value = contact.$el.offsetTop;
          init.value = true;
        })
        .catch((err: Error) => {
          console.log(err);
          const home = homeRef.value as any;
          const project = projectRef.value as any;
          const archive = archiveRef.value as any;
          const contact = contactRef.value as any;
          homeTop.value = home.$el.offsetTop;
          projectTop.value = project.$el.offsetTop;
          archiveTop.value = archive.$el.offsetTop;
          contactTop.value = contact.$el.offsetTop;
          init.value = true;
        });
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
      curArea,
      isArchive,
      handleScroll,
    };
  },
});
</script>

<style>
body {
  width: 100%;
  overflow-x: hidden;
  /* background: #d0d0d0; */
  /* background-color: hsl(0, 0%, 18%);
  background-size: 3px 3px;
  background-image: linear-gradient(
      0deg,
      hsla(0, 0%, 0%, 0) 0,
      hsla(0, 0%, 10%, 1) 3px
    ),
    linear-gradient(90deg, hsla(0, 0%, 0%, 0) 0, hsla(0, 0%, 10%, 1) 5px); */
}
body h2 {
  text-transform: uppercase;
  text-align: center;
  font-size: 30px;
  border: 1px solid #000;
  margin-bottom: 50px;
}
</style>
