<template>
	<view class="content">
        <!-- 仓库信息-名字/头像等 -->
		<view class="top">
            仓库信息-名字/头像等
		</view>
        <!-- 内容区域-功能模块-可上下滚动 -->
        <view class="center">
            内容区域-功能模块-可上下滚动
        </view>
        <!-- 底部按钮-首页/我的/二维码扫描 -->
        <view class="bottomBtn">
            <button type="default">首页</button>
            <!-- 二维码扫描按钮 -->
            <view class="qrCode">
                <icon type="search" size="26"/>
            </view>
            <button type="default">我的</button>
        </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="scss" scoped>
	.content {
        height: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
        
        // 头部
        .top{
            height: 100rpx;
            width: 100%;
            background: #007AFF;
        }
        
        .center{
            flex: 1;
            background: #333333;
            width: 100%;
        }
        
        .bottomBtn{
            height: 100px;
            width: 100%;
            background: #C8C7CC;
            overflow: hidden;
        }
	}
</style>
