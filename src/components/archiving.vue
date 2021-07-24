<template>
  <div id="archive">
    <div>
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
            공유목적이 아닌 공부노트이기 때문에 편한 어체를 사용한 점
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

.wrap {
  width: 800px;
  height: 300px;
  display: flex;
  justify-content: space-between;
  animation: fade 1s forwards;
}

.wrap > div {
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
}

.wrap div.git {
  position: relative;
  /* transform: translateX(500%); */
  left: 400%;
  animation: gt_move 2s forwards ease-out;
}

/* .wrap div.git:after {
  position: absolute;
  content: "";
  width: 100%;
  height: 100%;
  top: 0;
  right: -100%;
  background-color: rgb(29, 29, 29);
  animation: gt_virtual_move 3s 2s forwards;
} */

.wrap div.notion {
  position: relative;
  left: -400%;
  animation: nt_move 2s forwards ease-out;
}
/* 
.wrap div.notion:after {
  position: absolute;
  content: "";
  width: 100%;
  height: 100%;
  top: 0;
  left: -100%;
  background-color: rgb(29, 29, 29);
  animation: nt_virtual_move 3s 2s forwards;
} */

/* .wrap div.content {
  width: 100%;
  height: 100%;
  padding: 50px;
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  animation: con_fade 1s 8s linear forwards;
  z-index: 10;
}

.wrap div.content2 {
  width: 100%;
  height: 100%;
  padding: 50px;
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  animation: con_fade2 1s 8s linear forwards;
  z-index: 10;
} */

/* @keyframes fade {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
} */

@keyframes con_fade {
  0% {
    opacity: 1;
  }
  20% {
    opacity: 0;
    top: 0;
  }
  80% {
    opacity: 0;
    top: -100%;
  }
  100% {
    opacity: 1;
    top: -100%;
  }
}

@keyframes con_fade2 {
  0% {
    opacity: 1;
  }
  20% {
    opacity: 0;
    top: 0;
    /* transform: translateY(0px); */
  }
  80% {
    opacity: 0;
    top: 100%;
    /* transform: translateY(200px); */
  }
  100% {
    opacity: 1;
    top: 100%;
    /* transform: translateY(200px); */
  }
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
    /* transform: translateX(-500%); */
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
    /* transform: translateX(500%); */
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
}

.link a {
  display: flex;
  align-items: center;
  padding: 5px;
  border: 1px solid #ececec;
  border-radius: 5px;
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
</style>
