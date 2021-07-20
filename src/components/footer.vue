<template>
  <div id="footer">
    <footer></footer>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Footer",
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#home {
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
}

footer {
  width: 100%;
  height: 200px;
}
</style>
