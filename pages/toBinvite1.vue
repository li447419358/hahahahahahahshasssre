<template>
	<view class="container">
		<view class="prize-box" v-if="detail.imgContent">
			<view class="share-logon2">{{ detail.textContent }}</view>
			<image class="prize-img" :src="detail.imgContent" mode="aspectFit"></image>
		</view>
		<view v-else>
			<view class="share-logon">{{ detail.textContent }}</view>
		</view>
		<view class="style1_box" style="margin-top: 40rpx;">
			<view class="title_warp">我要报名</view>
			<view class="style1_innerbox">
				<view class="style1_content">
					<view style="text-align: center;">
						<view class="hostCompany">赛事主委会: {{ detail.hostCompany }}</view>
						<view class="activi-text">报名地址：{{ detail.activityAddress }}</view>
						<view class="activi-text">报名电话：{{ detail.phoneNum }}</view>
					</view>
				</view>
			</view>
		</view>
		<view class="qrcode-box">
			<image class="qrcode-img" :src="detail.qrCode" mode=""></image>
			<view class="qrcode-text">【快来参加比赛吧】</view>
			<view class="tips">*报名参赛绑定机器时请输入邀请人的手机号</view>
		</view>
	</view>
</template>

<script>
export default {
	components: {},
	data() {
		return {
			detail: {
				textContent: '',
				imgContent: '',
				qrCode: '',
				hostCompany: '',
				activityAddress: '',
				phoneNum: ''
			},
			fade: {
				tips: false,
				rules: false
			}
		};
	},
	onShow() {
		let data = this.getQueryVariable();
		console.log(data);
		if (data) {
			this.detail = data;
		}
	},
	methods: {
		getQueryVariable() {
			var str = window.location.href.split('?');
			if (str.length > 1) {
				let obj = {};
				let vars = str[1].split('&');
				for (var i = 0; i < vars.length; i++) {
					var pair = vars[i].split('=');
					obj[pair[0]] =this.decodeUrlHtml(pair[1]) ;
				}
				return obj;
			} else {
				return {};
			}
		},
		decodeUrlHtml (value) {
			return !value ? value : decodeURIComponent(value).replace(/\+/g, ' ').replace(/<img/g,
				"<img class='autoImgWidth'")
		}
	}
};
</script>

<style lang="less">
.container {
	background: #f03b16 url('../static/image/share1_bg.jpg') no-repeat center top;
	background-size: 100% auto;
	padding-top: 1580rpx;
	padding-bottom: 100rpx;
}
.style1_box {
	margin: 0 30rpx;
}
.title_warp {
	margin: 0 auto -55rpx;
	width: 348rpx;
	height: 78rpx;
	line-height: 78rpx;
	text-align: center;
	color: #fff;
	background: url('../static/image/title.png') no-repeat center top;
	background-size: 100%;
	position: relative;
	z-index: 10;
}

.style1_innerbox {
	background-color: #fff6e3;
	padding: 10rpx;
	border-radius: 10rpx;
}
.style1_content {
	padding-top: 72rpx;
	padding-bottom: 25rpx;
	border: 1px solid #ead4ac;
	border-radius: 10rpx;
}
.share-logon {
	margin: 0 35rpx 54rpx;
	font-size: 62rpx;
	color: #fff;
	text-align: center;
}
.prize-box {
	background: url('../static/image/light.png') no-repeat center center;
	background-size: 100%;
	padding-bottom: 30rpx;
	text-align: center;
	.prize-img {
		max-height: 440rpx;
	}
}
.share-logon2 {
	font-size: 48rpx;
	color: #fff;
	margin: 0 35rpx 54rpx;
	text-align: center;
}
.hostCompany {
	font-size: 32rpx;
	color: #6b2104;
	font-weight: 700;
	margin: 25rpx 0;
}
.activi-text {
	font-size: 26rpx;
	line-height: 2;
	color: #454545;
}
.qrcode-box {
	margin: 75rpx 0;
	text-align: center;
	.tips {
		font-size: 24rpx;
		color: #febba7;
	}
}
.qrcode-img {
	width: 226rpx;
	height: 226rpx;
	background-color: #fff;
	margin: 0 auto 36rpx;
}
.qrcode-text {
	font-size: 32rpx;
	color: #fff;
	margin-bottom: 46rpx;
}
</style>
