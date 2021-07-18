<template>
  <div class="mainmenu">
    <ul>
      <li><a class="f_gmaket" href="#">about</a></li>
      <li><a class="f_gmaket" href="#">projects</a></li>
      <li><a class="f_gmaket" href="#">achive</a></li>
      <li><a class="f_gmaket" href="#">contact</a></li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Mainmenu",
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.mainmenu {
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
}
</style>
