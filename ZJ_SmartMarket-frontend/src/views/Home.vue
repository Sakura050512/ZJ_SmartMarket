
<template>
  <div id="home_bg"></div>
</template>
<script>

export default {
    data() {
        return {
        };
    },
    methods: {

    },
    mounted() {
    },
};
</script>
<style>
#home_bg {
  position: absolute;        /* 全屏固定，也可以根据布局改用 absolute */
  bottom: 15px;
  right: 0;
  width: 90vw;
  height: 90vh;          /* 确保容器铺满视口 */
  background-image: url("../assets/55.png");
  background-repeat: no-repeat;
  background-size: cover;   /* 图片完整显示，可能留白 */
  background-position: center; /* 居中显示 */
  /* 移除了 overflow-y: auto 和 text-align: center，因为容器内无内容 */
}
</style>
