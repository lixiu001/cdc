<template>
  <view class="popup-mask" @click="close">
    <view v-show="visible" class="popup-content" @click.stop>
      <!-- popup的内容区域 -->
      <view>这里是popup的内容</view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      visible: false
    }
  },
  methods: {
    open() {
      this.visible = true
    },
    close() {
		console.log(111)
      this.visible = false
    }
  }
}
</script>

<style scoped>
.popup-mask {
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: flex-end;
  justify-content: center;
}

.popup-content {
  width: 100%;
  background-color: #ffffff;
  padding: 20px;
  border-top-left-radius: 16px;
  border-top-right-radius: 16px;
}
</style>
