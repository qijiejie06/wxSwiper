# wxSwiper-
微信小程序：选项卡页面切换

### 一、在同一个页面内实现不同展示页面的切换功能，如下图所示

![](img_url)

 

### 二、代码实现
1. index.js


Page({
 
  /**
   * 页面的初始数据
   */
  data: {
      currentData : 0,
  },
  /**
   * 生命周期函数--监听页面加载
   */
  onLoad: function (options) {
  },
  //获取当前滑块的index
  bindchange:function(e){
    const that  = this;
    that.setData({
      currentData: e.detail.current
    })
  },
  //点击切换，滑块index赋值
  checkCurrent:function(e){
    const that = this;
 
    if (that.data.currentData === e.target.dataset.current){
        return false;
    }else{
 
      that.setData({
        currentData: e.target.dataset.current
      })
    }
  }
})
　　

　　

2. index.wxml

<view class='topTabSwiper'>
    <view class='tab  {{currentData == 0 ? "tabBorer" : ""}}'  data-current = "0" bindtap='checkCurrent'>推荐</view>
    <view class='tab  {{currentData == 1 ? "tabBorer" : ""}}'  data-current = "1" bindtap='checkCurrent'>热点</view>
    <view class='tab  {{currentData == 2 ? "tabBorer" : ""}}'  data-current = "2" bindtap='checkCurrent'>关注</view>
</view>
<swiper current="{{currentData}}" class='swiper' style="height:600px;" duration="300" bindchange="bindchange">
  <swiper-item><view class='swiper_con'>welcome come to 推荐</view></swiper-item>
  <swiper-item><view class='swiper_con'>welcome come to 热点</view></swiper-item>
  <swiper-item><view class='swiper_con'>welcome come to 关注</view></swiper-item> 
</swiper>
　　

3. index.wxss

.tab {
  float: left;
  width: 33.3333%;
  text-align: center;
  padding: 10rpx 0;
}
 
.topTabSwiper {
  border-top: 1px solid #ccc;
  border-bottom: 1px solid #ccc;
  zoom: 1;
}
 
.topTabSwiper:after {
  content: "";
  clear: both;
  display: block;
}
 
.tabBorer {
  border-bottom: 1px solid #f00;
  color: #f00;
}
 
.swiper {
  width: 100%;
}
 
.swiper_con {
  text-align: center;
  width: 100%;
  height: 100%;
  padding: 80rpx 0;
}


