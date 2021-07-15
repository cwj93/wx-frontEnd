<template>
	<view class="content">
        <!-- 仓库信息-名字/头像等 -->
		<view class="top" :style="{backgroundImage:`url(${indexBackgroundImage})`,backgroundSize: 'cover'}">
            <view class="top-left">
                <image src="../../static/crown.jpg" mode="头像logo"></image>
            </view>
            <view class="top-right">
                <view class="title">皇冠店长成都仓库</view>
                <view class="msg">
                    <view class="msg-item">皇冠店长</view>
                    <view class="msg-item">仓库</view>
                </view>
            </view>
		</view>
        <!-- 内容区域-功能模块-可上下滚动 -->
        <view class="center">
            <view class="fun-wrap" v-if="false">
                <view class="fun-title">货品流转</view>
                <view class="fun-box">
                    <view class="fun-item" @click="toNextPage('出货')">
                        <view class="fun-content">
                            <image class="fun-content-size" src="../../static/shipment.jpg" mode="出货"></image>
                            <uni-badge v-if="false" class="fun-badge-style" :text="10" type="primary"> </uni-badge>
                        </view>
                        <text class="fun-text">出货</text>
                    </view>
                    <view class="fun-item">
                        <view class="fun-content">
                            <image class="fun-content-size" src="../../static/shipment.jpg" style="transform: rotateY(180deg);" mode="出货"></image>
                            <uni-badge class="fun-badge-style" :text="10" type="primary"> </uni-badge>
                        </view>
                        <text class="fun-text">发货</text>
                    </view>
                    <view class="fun-item">
                        <view class="fun-content" >
                            <image class="fun-content-size" src="../../static/closedGoods.jpg" mode=""></image>
                            <uni-badge class="fun-badge-style" :text="10" type="primary"> </uni-badge>
                        </view>
                        <text class="fun-text">收货</text>
                    </view>
                </view>
            </view>
        </view>
        <!-- 底部按钮-首页/我的/二维码扫描 -->
        <view class="bottom-btn">
            <view class="btn-box home" @click="touchBtn(0, '../../pages/index/index')">
                <uni-icons type="home-filled" size="24" :color="activeBtnIndex == 0 ? activeBtnIconColor : normalBtnIconColor"></uni-icons>
                <text class="text-size" :style="{color: activeBtnIndex == 0 ? activeBtnIconColor : normalBtnIconColor}">首页</text>
            </view>
            <!-- 二维码扫描按钮 -->
            <view class="qr-code-border"></view>
            <view class="btn-box my" @click="touchBtn(1, '../../pages/my/my')">
                <uni-icons type="person-filled" size="24" :color="activeBtnIndex == 1 ? activeBtnIconColor : normalBtnIconColor"></uni-icons>
                <text class="text-size" :style="{color: activeBtnIndex == 1 ? activeBtnIconColor : normalBtnIconColor}">我的</text>
            </view>
            <view class="qr-code" @click="touchBtn(-1)">
                <view class="qr-code-warp">
                    <uni-icons type="scan" size="24" color="#FFFFFF"></uni-icons>
                </view>
            </view>
            
        </view>
	</view>
</template>

<script>
    import indexBackgroundImage from '@/static/login_bg2.png'
	export default {
		data() {
			return {
				title: 'Hello',
                normalBtnIconColor: '#A0A0A0',
                activeBtnIconColor: '#101010',
                activeBtnIndex: 1, // 当前激活的按钮菜单索引
                indexBackgroundImage:indexBackgroundImage
			}
		},
		onLoad() {

		},
		methods: {
            // 底部按钮的点击事件
            touchBtn(index, url) {
                console.log('点击：', index)
                this.activeBtnIndex = index;
                index != -1 ? uni.navigateTo({
                    url: url
                }) : null
            },
            // 跳转
            toNextPage(type) {
                console.log('点击')
                uni.navigateTo({
                    url: '../../pagesShipment/shipment/shipment'
                })
            }
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
            height: 256rpx;
            width: 100%;
            display: flex;
            flex-direction: row;
            justify-content: flex-start;
            align-items: center;
            
            .top-left{
                width: 132rpx;
                height: 132rpx;
                margin: 0 32rpx;
                image{
                    width: 100%;
                    height: 100%;
                }
            }
            
            .top-right{
                height: 132rpx;
                flex: 1;
                margin-right: 32rpx;
                display: flex;
                flex-direction: column;
                justify-content: space-between;
                .title{
                    font-size: 20px;
                    font-weight: bold;
                    font-family: SourceHanSansSC-bold;
                    color: #FFFFFF;
                    height: 60rpx;
                    line-height: 60rpx;
                }
                
                .msg{
                    display: flex;
                    flex-direction: row;
                    justify-content: flex-start;
                    align-items: center;
                    .msg-item{
                        height: 40rpx;
                        line-height: 40rpx;
                        border: 1px solid #ECECEC;
                        border-radius: 20rpx;
                        background: #ECECEC;
                        color: #868686;
                        font-size: 12px;
                        padding: 0 20rpx;
                        margin-right: 10rpx;
                    }
                }
            }
        }
        
        .center{
            flex: 1;
            width: 100%;
            overflow: scroll;
        }
        
        .bottom-btn{
            height: 120rpx;
            width: 100%;
            border-top: 1px solid #C8C7CC;
            display: flex;
            flex-direction: row;
            justify-content: space-around;
            align-items: center;
            position: relative;
            background: #FFFFFF;
            .text-size{
                font-size: 12px;
                color: #101010;
            }
            .btn-box{
                display: flex;
                flex-direction: column;
                justify-content: space-around;
                align-items: center;
                padding: 0 20rpx;
            }
            .qr-code-border{
                width: 144rpx;
                height: 144rpx;
                line-height: 144rpx;
                background: #FFFFFF;
                border-radius: 144rpx;
                text-align: center;
                position: relative;
                top: -20rpx;
                border: 1px solid #C8C7CC;
                z-index: -1;
            }
            .qr-code{
                width: 148rpx;
                height: 148rpx;
                line-height: 148rpx;
                background: #FFFFFF;
                border-radius: 148rpx;
                text-align: center;
                position: relative;
                position: absolute;
                left: calc(50% - 74rpx);
                top: -30rpx;
                display: flex;
                align-items: center;
                justify-content: center;
                z-index: 2;
                
                .qr-code-warp{
                    width: 120rpx;
                    height: 120rpx;
                    line-height: 120rpx;
                    background: #B7B7B7;
                    border-radius: 120rpx;
                }
            }
            
        }
	}
    
    // 功能模块样式
    .fun-wrap{
        box-sizing: border-box; // 怪异盒模型
        width: 100%;
        padding: 60rpx 32rpx 0 32rpx;
        
        .fun-title{
            font-size: 14px;
            color: #101010;
            font-weight: bold;
        }
        .fun-box{
            display: flex;
            flex-direction: row;
            flex-wrap: wrap;
            margin-top: 20rpx;
            
            .fun-item{
                box-sizing: border-box; // 怪异盒模型
                width: 30.3333%;
                margin: 1.5%;
                padding: 32rpx 0;
                background: #EEEEEE;
                border-radius: 10rpx;
                display: flex;
                flex-direction: column;
                justify-content: space-around;
                align-items: center;
                
                .fun-content{
                    position: relative;
                    width: 72rpx;
                    height: 72rpx;
                    background: #0000FF;
                    margin-bottom: 20rpx;
                    
                    .fun-content-size{
                        width: 100%;
                        height: 100%;
                    }
                    .fun-badge-style{
                        position: absolute;
                        top: calc(-50% + 20rpx);
                        right: -50%;
                    }
                }
                
                .fun-text{
                    font-size: 14px;
                }
            }
        }
    }
</style>
