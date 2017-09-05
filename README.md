# Intro
记录移动端开发的坑坑洼洼

# Issues
## h5底部输入框被键盘遮挡问题
h5页面有个很蛋疼的问题就是，当输入框在最底部，点击软键盘后输入框会被遮挡。可采用如下方式解决

```js

var oHeight = $(document).height(); //浏览器当前的高度
   
   $(window).resize(function(){
 
        if($(document).height() < oHeight){
         
        $("#footer").css("position","static");
    }else{
         
        $("#footer").css("position","absolute");
    }
        
   });
```
## fixed定位缺陷
ios下fixed元素容易定位出错，软键盘弹出时，影响fixed元素定位
android下fixed表现要比iOS更好，软键盘弹出时，不会影响fixed元素定位
ios4下不支持position:fixed
解决方案： 绝对定位模拟滚动效果

> 注意scroll-btn 和 scroll-body 是同一级的

```css
.scroll-body {
  position: absolute;
  padding-bottom: 60px;
  top: 0;
  right: 0;
  left: 0;
  bottom: 60px;
  overflow: auto;
  background-color: #fff;
  -webkit-overflow-scrolling: touch;
}
.scroll-btn {
  border-top: 1px #e4e4e4 solid;
  bottom: 0;
  padding-left: 20px;
  padding-right: 20px;
  width: 100%;

  background: #fff;
  padding-top: 24px;
  margin-bottom: 24px;
  z-index: 10;
  position: absolute;
  height: 120px;
  box-sizing: border-box;
  &-preview {
    padding-left: 50px;
    padding-right: 50px;
  }
}
```

## 阻止旋转屏幕时自动调整字体大小
html, body, form, fieldset, p, div, h1, h2, h3, h4, h5, h6 {-webkit-text-size-adjust:none;}
