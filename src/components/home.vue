<template>
  <div class="home"></div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Home",
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.home {
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
}
header {
  width: 100%;
  height: 100px;
  display: flex;
  justify-content: center;
}

ul {
  display: flex;
  text-transform: uppercase;
  margin: 0 auto;
}

li {
}

a {
  display: inline-block;
  padding: 10px 6px;
}
</style>
