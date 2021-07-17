<template>
  <div class="archive">
    <div>
      <div class="git">
        <div class="content">
          <div class="logo">
            <i class="github"></i>
            <h3>GitHub</h3>
          </div>
          <div class="desc">
            <p>소스코드 저장소 입니다.</p>
            <p>지금까지 제작했던 프로젝트 소스들이 보관되어있습니다.</p>
          </div>
          <div class="link">
            <a href="#">
              <span>바로가기</span>
              <i class="shortcut"></i>
            </a>
          </div>
        </div>
      </div>
      <div class="notion">
        <div class="content2">
          <div class="logo">
            <i class="notion"></i>
            <h3>Notion</h3>
          </div>
          <div class="desc">
            <p>소스코드 저장소 입니다.</p>
            <p>지금까지 제작했던 프로젝트 소스들이 보관되어있습니다.</p>
          </div>
          <div class="link">
            <a href="#">
              <span>바로가기</span>
              <i class="shortcut"></i>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Archive",
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.archive {
  width: 100%;
  height: 100vh;
  max-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.wrap {
  width: 800px;
  display: flex;
  flex-direction: column;
  animation: fade 2s forwards;
}

.wrap > div {
  position: relative;
  /* left: 0;
  top: 0; */
  width: 400px;
  height: 200px;
  padding: 10px;
  background-color: lightpink;
}

.wrap div.git {
  align-self: flex-start;
  animation: gt_move 3s 4s forwards;
}

.wrap div.git:after {
  position: absolute;
  content: "";
  width: 100%;
  height: 100%;
  top: 0;
  right: -100%;
  background-color: lightsalmon;
  animation: gt_virtual_move 3s 2s forwards;
}

.wrap div.notion {
  align-self: flex-end;
  animation: nt_move 3s 4s forwards;
}

.wrap div.notion:after {
  position: absolute;
  content: "";
  width: 100%;
  height: 100%;
  top: 0;
  left: -100%;
  background-color: lightsalmon;
  animation: nt_virtual_move 3s 2s forwards;
}

.wrap div.content {
  position: relative;
  animation: con_fade 1s 8s linear forwards;
  z-index: 10;
}

.wrap div.content2 {
  position: relative;
  animation: con_fade2 1s 8s linear forwards;
  z-index: 10;
}

@keyframes fade {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes con_fade {
  0% {
    opacity: 1;
  }
  20% {
    opacity: 0;
    transform: translateY(0px);
  }
  80% {
    opacity: 0;
    transform: translateY(-200px);
  }
  100% {
    opacity: 1;
    transform: translateY(-200px);
  }
}

@keyframes con_fade2 {
  0% {
    opacity: 1;
  }
  20% {
    opacity: 0;
    transform: translateY(0px);
  }
  80% {
    opacity: 0;
    transform: translateY(200px);
  }
  100% {
    opacity: 1;
    transform: translateY(200px);
  }
}

@keyframes gt_move {
  0% {
    /* transform: translateY(0px); */
    top: 0;
  }
  50% {
    /* transform: translate(0px, 200px); */
    top: 200px;
    left: 0;
  }
  100% {
    /* transform: translate(200px, 200px); */
    top: 200px;
    left: 200px;
  }
}

@keyframes nt_move {
  0% {
    /* transform: translateY(0px); */
    top: 0;
  }
  50% {
    /* transform: translate(0px, -200px); */
    top: -200px;
    left: 0;
  }
  100% {
    /* transform: translate(-200px, -200px); */
    top: -200px;
    left: -200px;
  }
}

@keyframes gt_virtual_move {
  0% {
    right: -100%;
    opacity: 1;
  }
  100% {
    opacity: 0;
    right: -500%;
  }
}

@keyframes nt_virtual_move {
  0% {
    left: -100%;
    opacity: 1;
  }
  100% {
    opacity: 0;
    left: -500%;
  }
}

.logo {
  display: flex;
  justify-content: center;
  align-items: center;
}

.logo h3 {
  font-size: 20px;
}

.desc {
  margin: 30px 0;
}

.link {
  display: flex;
  justify-content: center;
}

.link a {
  display: flex;
  align-items: center;
  padding: 2px;
  border: 1px solid #ececec;
  border-radius: 5px;
}

.link span {
  font-size: 16px;
}

i.github {
  display: inline-block;
  width: 40px;
  height: 40px;
  background: url("../assets/imgs/github.png") no-repeat;
  background-size: contain;
}

i.notion {
  display: inline-block;
  width: 40px;
  height: 40px;
  background: url("../assets/imgs/notion.png") no-repeat;
  background-size: contain;
}

i.shortcut {
  display: inline-block;
  width: 40px;
  height: 40px;
  background: url("../assets/imgs/shortcut.png") no-repeat;
  background-size: contain;
}
</style>
