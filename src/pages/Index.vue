<template>
  <q-page>
    <div class="column" style="height:30000px">
      <transition>
        <div class="col box fixed" v-show="video1">
          <video
            :current-time.prop="currentTime"
            @timeupdate="currentTime = $event.target.currentTime"
            width="1920px"
            height="1080px"
            muted
          >
            <source type="video/mp4" src="../assets/video1.mp4" />
          </video>
          <h3 class="item right-bottom">{{scrollY}}</h3>
          <q-card class="item left-top back-gray">
            <p class="text-white text-h3 q-ma-sm">奈日抽ねね（GEMS COMPANY）</p>
            <p class="text-white text-subtitle q-ma-sm">とりあえずかわいい</p>
          </q-card>
        </div>
      </transition>
    </div>
  </q-page>
</template>

<script>
export default {
  name: "PageIndex",
  data() {
    return {
      scrollY: 0,
      currentTime: 0,
      video1: true,
    };
  },
  mounted() {
    window.addEventListener("scroll", this.calculateScrollY);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.calculateScrollY);
  },
  methods: {
    calculateScrollY() {
      this.scrollY = window.scrollY;
      this.currentTime = scrollY / 1000;
      this.video1 = scrollY < 1500;
    },
  },
};
</script>

<style>
.fixed {
  position: fixed;
}
.bix {
  position: relative;
}
.item {
  position: absolute;
}
.right-bottom {
  top: 80%;
  left: 90%;
}
.left-top {
  top: 15%;
  left: 5%;
}

.back-gray {
  background: rgba(1, 1, 1, 0.5);
}

.v-leave-active,
.v-enter-active {
  transform: translate(0px, 0px);
  transition: transform 500ms linear 0ms;
}
.v-enter,
.v-leave-to {
  transform: translateY(-100vh) translateY(0px);
}
</style>
