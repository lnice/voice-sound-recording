<template>
	<view class="content">
    <button type="primary" @click="show = true">语音录制</button>
    <view class="popup-bottom" v-if="show">
      <view class="popup-bg" @click="show = false"></view>
      <view class="popup-content">
        <sound-recording
          :maximum="15"
          :duration="100"
          @cancel="show = false"
          @confirm="onUpload">
        </sound-recording>
      </view>
    </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
        show: false
			}
		},
		onLoad() {

		},
		methods: {
      onUpload (tempFilePath) {
        console.log(tempFilePath)
      }
		}
	}
</script>

<style lang="scss">
  .content {
    padding: 30rpx;
  }
  .popup-bottom {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 10;
    display: flex;
    flex-direction: column;
    .popup-bg {
      position: fixed;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.5);
    }
    .popup-content {
      height: 40%;
      margin-top: auto;
      background-color: #fff;
      position: relative;
      z-index: 11;
    }
  }
</style>
