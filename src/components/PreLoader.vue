<template>
  <div class="load_container">
    <span class="loader"></span>
</div>
</template>

<script>
export default {
  name: 'PreLoader',
}
</script>

<style scoped lang="scss">
@import "@/styles/variables.scss";

.load_container {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: $text_color;
}

.loader {
  width: 100px;
  height: 100px;
  border: 5px solid $bg_color;
  border-radius: 50%;
  display: inline-block;
  position: relative;
  box-sizing: border-box;
  animation: rotation 1s linear infinite;
}
.loader::after {
  content: '';  
  box-sizing: border-box;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 80px;
  height: 80px;
  border-radius: 50%;
  border: 5px solid;
  border-color: $act_btn_bg_hover transparent;
}

@keyframes rotation {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
} 
</style>