<template>
  <div class="home">
    <header>
      <ul>
        <li><a href="#">about</a></li>
        <li><a href="#">projects</a></li>
        <li><a href="#">achive</a></li>
        <li><a href="#">contact</a></li>
      </ul>
    </header>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Home",
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header {
  width: 100%;
  height: 100vh;
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
