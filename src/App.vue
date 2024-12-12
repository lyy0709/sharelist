<template>
  <WechatAlert />
  <n-config-provider :theme="isDarkTheme ? darkTheme : ''" v-if="!isWechat">
    <Mirror />
    <n-loading-bar-provider>
      <Index :isDarkTheme="isDarkTheme" @changeIsDarkTheme="changeIsDarkTheme" />
    </n-loading-bar-provider>
  </n-config-provider>
</template>

<script>
import { defineComponent, ref, onMounted } from 'vue'
import { darkTheme } from 'naive-ui'
import Mirror from './components/mirror.vue'
import Index from './components/index.vue'
import WechatAlert from './components/WechatAlert.vue'

export default defineComponent({
  components: {
    Index,
    Mirror,
    WechatAlert
  },
  setup() {
    const KEY = 'isDarkTheme';
    const localDarkTheme = localStorage.getItem(KEY);
    const isDarkTheme = ref(localDarkTheme === 'true');
    const isWechat = ref(false);

    onMounted(() => {
      const ua = navigator.userAgent.toLowerCase();
      isWechat.value = ua.indexOf('micromessenger') !== -1;
    });

    const changeIsDarkTheme = (v) => {
      isDarkTheme.value = v;
      localStorage.setItem(KEY, v);
    }

    return {
      darkTheme,
      isDarkTheme,
      isWechat,
      changeIsDarkTheme
    }
  }
})
</script>