#水平垂直居中几种方法
##一、块级元素
###absolute
#### 1.left:50%;top:50%;margin-top:-width/2;marign-left:-left/2
#####解释：利用margin负值实现，因为margin百分比所有的值都是根据width计算，所以百分比在此鸡肋，只能用固定值，则要求宽高固定
需要计算margin值，如果width，height为百分比时难以计算
```css
 .wrap {
            position: relative;
            height: 500px;
            width: 500px;
            background: yellow;
            margin:0 auto;
        }

        .con {
            position: absolute;
            left: 50%;
            top: 50%;
            width: 50%;
            height: 50%;
            margin-top:-width/2;
            marign-left:-height/2;
            background: red;
        }
```
#### 2.left:50%;top:50%;transform:translate(-50%,-50%)
#####解释：利用css3transform:translate属性解决
不用考虑margin值的计算

```css
 .wrap {
            position: relative;
            height: 500px;
            width: 500px;
            background: yellow;
            margin:0 auto;
        }

        .con {
            position: absolute;
            left: 50%;
            top: 50%;
            width: 50%;
            height: 50%;
            transform: translate(-50%,-50%);
            background: red;
        }
```
####3.left:0;top:0;right:0;bottom:0;width,height固定值;marign:auto;
#####解释：利用margin：auto解决空余空间的特性实现
也不用考虑宽高值，兼容性比第二种更好
```css
 .wrap {
            position: relative;
            height: 500px;
            width: 500px;
            background: yellow;
            margin:0 auto;
        }

        .con {
            position: absolute;
            width: 50%;
            height: 50%;
            top:0;
            bottom:0;
            left:0;
            right:0;
            margin:auto;
            background: red;
        }
```
##二、行级元素
###line-height和vertical-align
####1.文字  在其父级元素加text-align:center和line-height:height(父元素的高度)
```css
   div{
            height:200px;
            width: 200px;
            background: red;
            text-align: center;
            line-height: 200px;
        }
```
####2.图片时 在图片上增加vertical-align:middle
```css
     div {
            height: 200px;
            width: 200px;
            background: red;
            text-align: center;
            line-height: 200px;
        }

        img {
            height: 75px;
            width: 100px;
            vertical-align: middle;/*增加该属性实现图片水平垂直居中*/
        }
```