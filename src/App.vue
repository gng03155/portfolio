<template>
  <div>
    <Home />
    <Projects />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import HelloWorld from "./components/HelloWorld.vue";
import Home from "./components/home.vue";
import Projects from "./components/Projects.vue";

export default defineComponent({
  name: "App",
  components: {
    Home,
    Projects,
  },
});
</script>

<style>
h2 {
  text-transform: uppercase;
  font-size: 30px;
  margin-bottom: 50px;
}
</style>
