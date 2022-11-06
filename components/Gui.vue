<template>
  <div>
    <!-- <div :class="[$style.me]">
       <a href="https://www.facebook.com/trannhatminhgtnd/" target="_blank" rel="noopener noreferrer">Me</a>
    </div>-->
    <div :class="[$style.tutorial]">
      Nhấn vào
      <strong @click="toggleScreen" style="cursor: pointer">đây</strong>
      {{ toggleText }} toàn màn hình.
    </div>
  </div>
</template>

<style module>
.me {
  position: fixed;
  top: 2rem;
  left: 2rem;
  font-size: 1.2rem;
}

.me a {
  text-decoration: none;
  color: #000;
}
.tutorial {
  position: fixed;
  bottom: 2rem;
  left: 2rem;
  font-size: 1.4rem;
}
</style>

<script>
export default {
  data() {
    return {
      toggleText: "để",
      toggleStatus: 0
    };
  },
  methods: {
    toggleScreen() {
      if (this.toggleStatus == 0) {
        document.body.requestFullscreen();
        this.toggleText = "thoát";
        this.toggleStatus = 1;
      } else {
        document.exitFullscreen();
        this.toggleText = "để";
        this.toggleStatus = 0;
      }
    }
  }
};
</script>
