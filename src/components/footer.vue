<template>
  <div id="footer">
    <footer>
      <ul class="content">
        <li>
          <i class="fas fa-file-pdf"></i>
          <a
            href="https://drive.google.com/file/d/1d38uoX-A_CDurQhbwY3uUQdlFiuXA2Yk/view?usp=sharing"
            target="_blank"
          >
            <span class="f_gmarket">Resume</span>
          </a>
        </li>
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

.content li:nth-child(2) span {
  padding-top: 0;
}

ul.content a {
  display: block;
}

ul.content a:hover span {
  color: lightcoral;
}

ul.content span {
  font-size: 16px;
  display: inline-block;
}
ul.content i {
  font-size: 25px;
  margin-right: 10px;
}
</style>
