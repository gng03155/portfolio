<template>
  <div id="footer">
    <footer>
      <ul class="content">
        <li>
          <i class="far fa-envelope"></i>
          <span class="f_gmarket">gng03155@gmail.com</span>
        </li>
        <li>
          <i class="fas fa-phone"></i>
          <span class="f_gmarket">010 6480 2679</span>
        </li>
        <li>
          <span>© 2021. Won Jong Seon. All rights reserved.</span>
        </li>
      </ul>
    </footer>
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
footer {
  width: 100%;
  height: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #333;
}

.content {
  width: 500px;
}

.content li {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 10px;
}
.content li:last-child {
  margin-bottom: 0;
}
ul.content span {
  font-size: 16px;
}
ul.content i {
  font-size: 20px;
  margin-right: 10px;
}
</style>
