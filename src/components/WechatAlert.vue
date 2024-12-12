<!-- components/WechatAlert.vue -->
<template>
    <div class="wechat-alert" v-if="isWechat">
      <div class="top-bar-guidance">
        <p>点击右上角<img src="@/assets/images/3dian.png" class="icon-safari">在 浏览器 打开</p>
        <p>苹果设备<img src="@/assets/images/iphone.png" class="icon-safari">安卓设备<img src="@/assets/images/android.png" class="icon-safari">↗↗↗</p>
      </div>
      
      <div class="contents">
        <p><br/><br/></p>
        <p>1.本站不支持 微信或QQ 内访问</p>
        <p><br/></p>
        <p>2.请按提示在手机 浏览器 打开</p>
      </div>
      
      <p><br/><br/></p>
      <div class="app-download-tip">
        <span class="guidance-desc">{{ currentUrl }}</span>
      </div>
      <p><br/></p>
      <div class="app-download-tip">
        <span class="guidance-desc">点击右上角···图标 or 复制网址自行打开</span>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'WechatAlert',
    data() {
      return {
        isWechat: false,
        currentUrl: window.location.href
      }
    },
    mounted() {
      this.checkBrowser()
    },
    methods: {
      checkBrowser() {
        const ua = navigator.userAgent.toLowerCase()
        this.isWechat = ua.indexOf('micromessenger') !== -1
      }
    }
  }
  </script>
  
  <style scoped>
  .wechat-alert {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: #fff;
    z-index: 999999;
    text-align: center;
    padding: 20px;
  }
  .icon-safari {
    width: 20px;
    vertical-align: middle;
    margin: 0 5px;
  }
  .app-download-tip {
    color: #1989fa;
    margin: 15px 0;
  }
  </style>