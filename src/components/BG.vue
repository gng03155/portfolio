<template>
  <div id="bg"></div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "BG",
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#bg {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  z-index: -1;
  background-color: hsl(0, 0%, 18%);
  background-size: 3px 3px;
  background-image: linear-gradient(
      0deg,
      hsla(0, 0%, 0%, 0) 0,
      hsla(0, 0%, 10%, 1) 3px
    ),
    linear-gradient(90deg, hsla(0, 0%, 0%, 0) 0, hsla(0, 0%, 10%, 1) 5px);
}
</style>
