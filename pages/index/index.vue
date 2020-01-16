<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<!-- <Test /> -->
		<Test1 />
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<!-- <viewDemo  @btnClick="conTest" size="mini"/> -->
		
		<!-- <template>
		    <view>
		        <button @tap="startRecord">开始录音</button>
		        <button @tap="endRecord">停止录音</button>
		        <button @tap="playVoice">播放录音</button>
		    </view>
		</template> --> 
	</view>
</template>

<script>
	import testxd from './test'
	import viewDemo from '@/components/view/index.vue';
	import Test from '@/components/test/index.vue';
	import Test1 from '@/components/test/index.1.vue';

	const recorderManager = uni.getRecorderManager();
	const innerAudioContext = uni.createInnerAudioContext();
	
	innerAudioContext.autoplay = true;
	
	export default {
		components: {
			viewDemo,
			Test, 
			Test1
		},
		data() {
			return {
				title: 'Hello',
				text: 'uni-app',
				voicePath: ''
			}
		},
		onLoad() {
			//testxd();
			testxd.test();
			// const base64 = 'test'
			// const arrayBuffer = uni.base64ToArrayBuffer(base64);
			// console.log(arrayBuffer);
			// uni.getLocation({
			//     type: 'wgs84',
			//     success: function (res) {
			//         console.log('当前位置的经度：' + res.longitude);
			//         console.log('当前位置的纬度：' + res.latitude);
			//     }
			// });
			// uni.chooseLocation({
			//     success: function (res) {
			//         console.log('位置名称：' + res.name);
			//         console.log('详细地址：' + res.address);
			//         console.log('纬度：' + res.latitude);
			//         console.log('经度：' + res.longitude);
			//     }
			// });
			// uni.getLocation({
			//     type: 'gcj02', //返回可以用于uni.openLocation的经纬度
			//     success: function (res) {
			//         const latitude = res.latitude;
			//         const longitude = res.longitude;
			//         uni.openLocation({
			//             latitude: latitude,
			//             longitude: longitude,
			//             success: function () {
			//                 console.log('success');
			//             }
			//         });
			//     }
			// })
			// uni.chooseImage({
			//     count: 6, //默认9
			//     sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
			//     sourceType: ['album'], //从相册选择
			//     success: function (res) {
			//         console.log(JSON.stringify(res.tempFilePaths));
			//     }
			// });
			
			// let self = this;
			// recorderManager.onStop(function (res) {
			// 	console.log('recorder stop' + JSON.stringify(res));
			// 	self.voicePath = res.tempFilePath;
			// });
			
			// uni.authorize({
			//     scope: 'scope.userLocation',
			//     success() {
			//         uni.getLocation()
			//     }
			// })
			
			// uni.openSetting({
			//   success(res) {
			// 	  console.log(999);
			//     console.log(res.authSetting, '111')
			//   }
			// });
			
			// uni.chooseAddress({
			//   success(res) {
			//     console.log(res.userName)
			//     console.log(res.postalCode)
			//     console.log(res.provinceName)
			//     console.log(res.cityName)
			//     console.log(res.countyName)
			//     console.log(res.detailInfo)
			//     console.log(res.nationalCode)
			//     console.log(res.telNumber)
			//   }
			// })
			
			// uni.getProvider({
			//     service: 'oauth',
			//     success: function (res) {
			//         console.log(res.provider)
			//         if (~res.provider.indexOf('qq')) {
			//             uni.login({
			//                 provider: 'qq',
			//                 success: function (loginRes) {
			//                     console.log(JSON.stringify(loginRes));
			//                 }
			//             });
			//         }
			//     }
			// });
			
			// uni.login({
			//   provider: 'weixin',
			//   success: function (loginRes) {
			//     console.log(loginRes.authResult);
			//   }
			// });
			console.log(999);
			// uni.login({
			//   provider: 'weixin',
			//   success: function (loginRes) {
			//     console.log(loginRes.authResult);
			//     // 获取用户信息
			//     uni.getUserInfo({
			//       provider: 'weixin',
			//       success: function (infoRes) {
			//         console.log('用户昵称为：' + infoRes.userInfo.nickName);
			//       }
			//     });
			//   }
			// });
			
			// uni.login({
			// 	scopes: 'auth_user',
			// 	success: function(res){
			// 		console.log(res);
			// 	}
			// })
			
			uni.share({
			    provider: "weixin",
			    scene: "WXSceneSession",
			    type: 1,
			    summary: "我正在使用HBuilderX开发uni-app，赶紧跟我一起来体验！",
			    success: function (res) {
			        console.log("success:" + JSON.stringify(res));
			    },
			    fail: function (err) {
			        console.log("fail:" + JSON.stringify(err));
			    }
			});
		},
		methods: {
			conTest: function(){
				console.log(111);
			},
			
			 startRecord() {
				console.log('开始录音');
	
				recorderManager.start();
			},
			endRecord() {
				console.log('录音结束');
				recorderManager.stop();
			},
			playVoice() {
				console.log('播放录音');
	
				if (this.voicePath) {
					innerAudioContext.src = this.voicePath;
					innerAudioContext.play();
				}
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
