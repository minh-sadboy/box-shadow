<template>
  <div :class="[$style.loading]">
    <div style="margin-bottom: 50px;">
      <img src="loading.png" :class="[$style.img]" />
      <div :class="[$style.progress]">
        <div :class="[$style.progressvalue]"></div>
      </div>
    </div>
    <div :class="[$style.text]">
      <a
        href="https://www.facebook.com/trannhatminhgtnd/"
        target="_blank"
        rel="noopener noreferrer"
      >CAR</a>
    </div>
  </div>
</template>

<style module>
.loading {
  position: fixed;
  z-index: 50;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: #000000;
  display: flex;
  justify-content: center;
  align-items: center;
}
.img {
  max-width: 500px;
  max-height: 200px;
}

.text {
  font-family: fantasy;
  position: fixed;
  bottom: 1.5rem;
}

.text a {
  text-decoration: none;
  color: #ffffff;
  font-size: 1.6rem;
}

.text a:hover {
  color: #e8b429;
}

body {
  justify-content: center;
  align-items: center;
  background: #000;
  display: flex;
  height: 100vh;
  padding: 0;
  margin: 0;
}

.progress {
  background: rgba(255,255,255,0.1);
  justify-content: flex-start;
  border-radius: 100px;
  align-items: center;
  position: relative;
  padding: 0 5px;
  display: flex;
  height: 10px;
  width: 200px;
  margin: 0 auto;
  margin-top: 25px;
}

.progressvalue {
  animation: load 3s normal forwards;
  box-shadow: 0 10px 40px -10px #fff;
  border-radius: 100px;
  background: #fff;
  height: 10px;
  width: 0;
}

@keyframes load {
  0% { width: 0; }
  100% { width: 70%; }
}
</style>

<script>
export default {
};
</script>
