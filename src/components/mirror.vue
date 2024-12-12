<template>
  <a href="https://login-gpt.com" class="Mirror-link" target="_blank" style="width: 200px; height: 40px;">
    <img src="@/assets/mirror.png" alt="mirror" width="100%" style="border-radius: 20%">
  </a>
</template>

<script>
export default {
  name: 'MirrorCorner'
}
</script>

<style scoped>
.Mirror-link {
  position: fixed;
  top: 10px;      /* 可以根据需要调整边距 */
  right: 10px;    /* 可以根据需要调整边距 */
  z-index: 1000;  /* 确保链接在最上层 */
}

</style>
