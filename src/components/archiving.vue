<template>
  <div id="archive">
    <div class="content">
      <div class="git">
        <div class="logo">
          <i class="github"></i>
          <h3 class="f_gmarket">GitHub</h3>
        </div>
        <div class="desc">
          <p class="f_gmarket">소스코드 저장소 입니다.</p>
          <p class="f_gmarket">제작했던 프로젝트 소스들이 보관되어있습니다.</p>
        </div>
        <div class="link">
          <a href="#">
            <span class="f_gmarket">바로가기</span>
            <i class="shortcut"></i>
          </a>
        </div>
      </div>
      <div class="notion">
        <div class="logo">
          <i class="notion"></i>
          <h3 class="f_gmarket">Notion</h3>
        </div>
        <div class="desc">
          <p class="f_gmarket">
            공부했던 내용 및 개발 이슈들이 기록되어있습니다.
          </p>
          <p class="f_gmarket">
            공유목적이 아닌 공부노트이기 때문에 평어체를 사용한 점
            양해부탁드립니다.
          </p>
        </div>
        <div class="link">
          <a href="#">
            <span class="f_gmarket">바로가기</span>
            <i class="shortcut"></i>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, watchEffect } from "vue";

export default defineComponent({
  name: "Archive",
  props: {
    isIn: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
  setup(props) {
    watchEffect(() => {
      if (props.isIn) {
        console.log("들어옴");
      }
    });
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#archive {
  width: 100%;
  height: 100vh;
  max-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.content {
  width: 800px;
  height: 300px;
  display: flex;
  justify-content: space-between;
  animation: fade 1s forwards;
}

.content > div {
  position: relative;
  width: 320px;
  height: 100%;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  background: #fafafa;
  border-radius: 10px;
  text-align: center;
  color: #333;
}

.content div.git {
  position: relative;
  left: 400%;
}

.content div.notion {
  position: relative;
  left: -400%;
}

.wrap div.git {
  animation: gt_move 2s forwards ease-out;
}
.wrap div.notion {
  animation: nt_move 2s forwards ease-out;
}

@keyframes gt_move {
  0% {
  }
  70% {
    left: 0px;
  }
  75% {
    left: 30px;
  }
  80% {
    left: 0px;
  }
  85% {
    left: 20px;
  }
  90% {
    left: 0px;
  }
  95% {
    left: 10px;
  }
  100% {
    left: 0;
  }
}

@keyframes nt_move {
  0% {
  }
  70% {
    left: 0px;
  }
  75% {
    left: -30px;
  }
  80% {
    left: 0px;
  }
  85% {
    left: -20px;
  }
  90% {
    left: 0px;
  }
  95% {
    left: -10px;
  }
  100% {
    left: 0;
  }
}

.logo {
  display: flex;
  justify-content: center;
  align-items: center;
  color: inherit;
}

.logo h3 {
  font-size: 20px;
  margin-left: 5px;
  color: inherit;
}

.desc {
  margin: 30px 0;
  color: inherit;
}

.desc p {
  font-size: 16px;
  margin-bottom: 5px;
  color: inherit;
}
.desc p:last-child {
  margin-bottom: 0px;
}

.link {
  display: flex;
  justify-content: center;
  color: inherit;
}

.link a {
  display: flex;
  align-items: center;
  padding: 5px;
  border: 1px solid #333;
  border-radius: 5px;
  color: inherit;
}

.link span {
  font-size: 16px;
  color: inherit;
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
  width: 25px;
  height: 25px;
  background: url("../assets/imgs/shortcut.png") no-repeat;
  background-size: contain;
}

@media screen and (max-width: 1024px) {
  .wrap {
    width: 100%;
    height: auto;
    flex-direction: column;
    align-items: center;
  }
  .wrap > div:first-child {
    margin-bottom: 50px;
  }
  .wrap > div {
    width: 320px;
    height: 300px;
  }
}
@media screen and (max-width: 768px) {
  .wrap > div {
    width: 300px;
    height: 280px;
  }
  .logo h3 {
    font-size: 18px;
  }
  .desc p {
    font-size: 14px;
    margin-bottom: 5px;
    color: inherit;
  }
  .link span {
    font-size: 14px;
    color: inherit;
  }
}
@media screen and (max-width: 480px) {
  .wrap > div {
    width: 280px;
    height: 260px;
  }

  .logo h3 {
    font-size: 16px;
    margin-left: 5px;
    color: inherit;
  }
  .desc {
    margin: 20px 0;
    color: inherit;
  }

  .desc p {
    font-size: 12px;
  }
  .link span {
    font-size: 12px;
  }
}
</style>
