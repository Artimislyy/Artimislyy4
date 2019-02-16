# 微信小程序第四周总结
1.view  
```
<!-- common.wxml -->
<!-- <scroll-view class='flex-wrap' scroll-y="true" scroll-x="true" bindscrolltoupper="scrolltoupper" bindscrolltolower="scrolltolower" upper-threshold="100"
lower-threshlod="100" scroll-top="100" scroll-left="50"
scroll-into-view="{{toview}}" bindscroll="scroll">
    <view id="a" class='a'>a</view>
    <view id="b" class='b'>b</view>
    <view id="c" class='c'>c</view>
</scroll-view>
<button bindtap="tapchange">切换</button> -->
<!-- <swiper indicator-dots='true' autoplay="{{autoplay}}"  duration ="500" interval='{{inter}}' current='2' bindchange="swiperchange">
    <swiper-item wx:for="{{imgUrls}}">
        <!-- <image src="{{item}}" width="355" height="150" /> -->
        <!-- 我是文字，哈哈哈？？？
    </swiper-item>
</swiper>
<slider show-value  bindchange="intervalChange" min="0" max="5000"/>
<button bindtap="changeAutoplay">切换autoplay</button> -->   

Page({

    /**
     * 页面的初始数据
     */
    data:{
        // toview:"a",
        imgUrls: [
            "1","2","3"
        ],
        inter:2000,
        autoplay:"true"
    },
    swiperchange:function(e){
        consolo.log(e);
    },
    intervalChange:function(e){
        // console.log(e);
        var sliderValue = e.datail.value;
        this.setData({
            inter:sliderValue
        });
    },
    changeAutoplay:function(){
        this.setData({
            autoplay:~this.data.autoplay
        });
    },
    // bindscrolltoupper:function(e){
    //     console.log(e)
    // },
    // bindscrolltolower:function(e){
    //     console.log(e)
    // },
    // scroll:function(e){
    //     console.log(e)
    // },
    // tapchange:function(){
    //     index++;
    //     if (index > order.length-1){
    //         index=0;
    //     }
    //     this.setData({
    //         toview:order[index]
    //     });
    // },
```
2.
表单
```
<!-- 表单 -->
<button bindtap="changeDisabled">启用</button>
<form bindsubmit='subFn' bindreset='reset'>
    <input type='text' name="txtName" placeholder='请输入你的用户名' placeholder-style="font-size:24rpx" placeholder-class="outher-placeholder" maxlength='100' auto-focus="true" bindinput='inputFn' bindfocus='focusFn'/>
    <!-- 复选框 -->
    <checkbox-group bindchange="checkChange">
        <label wx:for="{{country}}">
             <checkbox value="{{item.name}}" checked="{{item.checked}}"/>
            {{item.value}}
        </label>
    </checkbox-group >
    <!-- input -->
    <!-- type影响的是软件盘的内容 -->
    <input type='number' password='true'></input>
    <!-- picker选择器 -->
    <view class='section_title'>选择城市：</view>
    <picker bindchange="bindPickerChange" value="{{index}}"   range="{{citys}}">
        <view>当前选择:  {{citys[index]}}</view>
    </picker>
   <view class='section_title'>时间选择： </view>
   <picker value="{{time}}"start="09:01" end="21:01" mode="time" bindchange="bindTimeChange">
        <view>当前选择：{{time}}</view>
   </picker>
<view class='section_title'>选择日期： </view>
<picker mode="date" value="{{date}}" start="2015-11-01" end="2017-11-01" bindchange='bindDateChange'>
    <view>当前选择: {{date}}</view>
</picker>

<!-- 单选框 -->
<radio-group bindchange="bindChangeRadio">
     <label wx:for="{{country}}">
             <checkbox value="{{item.name}}" checked="{{item.checked}}"/>
            {{item.value}}
        </label>
</radio-group>
<!-- 滑动选择器 -->
<slider show-value min="0" max="50" step='5' ></slider>
<!-- 开关选择器 -->
<switch checked="true" type="checkbox"></switch>
<!-- 多行文本 -->
<textarea class="text" placeholder-class='placeholder_textarea' placeholder='请输入留言' auto-height bindlinechange='bindLineChange'></textarea>

    <button size='mini' type='primary' plain='true'disabled="{{disabledBol}}" loading="true" hover-class='{{other-button-hover}}'                   form-type='submit'>按钮</button>
    <button size="mini" formType="reset">重置</button>
</form>   


Page({

    /**
     * 页面的初始数据
     */
    data:{
        toview:"a",
        imgUrls: [
            "1","2","3"
        ],
        inter:2000,
        autoplay:"true",
        disabledBol:"true",
        country: [
            { name: 'USA', value: '美国' },
            { name: 'CHN', value: '中国', checked:1},
            { name: 'BRA', value: '巴西' },
            { name: 'JPN', value: '日本' ,checked:1},
            { name: 'ENG', value: '英国' },
            { name: 'TUR', value: '法国' },
        ],
        citys:["北京","上海","广州","深圳"],
        index:0,
        time:"09:01",
        date:"2016:11:01"
    },
    bindPickerChange(e) {
        // console.log('picker发送选择改变，携带值为', e.detail.value)
        this.setData({
            index: e.detail.value
        });
    },
    bindLineChange(e){
        console.log(e.detail.value)
    },
    bindTimeChange(e){
        this.setData({
            time: e.detail.value
        });
    },

    bindChangeRadio:function(e){
        console.log(e)
    },
    checkChange:function(){
        console.log("复选框修改了")
    },
    focusFn:function(){
console.log("聚焦了")
    },
    blurFn:function(){
        console.log("光标失焦了")
    },
    swiperchange:function(e){
        consolo.log(e);
    },
    intervalChange:function(e){
        // console.log(e);
        var sliderValue = e.datail.value;
        this.setData({
            inter:sliderValue
        });
    },
    changeAutoplay:function(){
        this.setData({
            autoplay:~this.data.autoplay
        });
    },
    changeDisabled:function(){
        this.setData({
            disabledBol:false
        });
    },
    subFn:function(e){
        console.log("提交表单",e.datail.value)
    },
    reset:function(){
        console.log("点击重置了")
    },
    inputFn:function(e){
        var val = '数：'+e.value;
        return val;
        // console.log("输入内容了")
    },
    bindscrolltoupper:function(e){
        console.log(e)
    },
    bindscrolltolower:function(e){
        console.log(e)
    },
    scroll:function(e){
        console.log(e)
    },
    tapchange:function(){
        index++;
        if (index > order.length-1){
            index=0;
        }
        this.setData({
            toview:order[index]
        });
    },

```

