#两列等高布局
##一、border实现
###原理：利用.wrap的border为.wrap本身的属性.当.wrap高度增加时border也会增加实现
####关键点：
1. 两列元素必须在.wrap中
2. .wrap的的border部分为左列部分，内容区域为右列部分
3. .wrap的color设置左列颜色，background设置右列颜色
4. 左列元素需要float:left;margin-left:width(.wrap).wrap的border宽度，里边每一行用一个块级元素执行：首选p
5. 右列元素每一行也需要包裹块级元素
###代码
```css
        * {
            margin: 0; /*p标签会有默认margin值*/
            padding: 0;
        }

        .wrap {
            width: 200px;
            color: cornflowerblue;/*color为border的颜色，也就是左边栏的颜色*/
            background: red;/*background背景为右边栏的颜色*/
            border-left: 200px solid;
            font-size: 0;
        }

        .wrap > * {
            display: inline-block;

            line-height: 50px;
            font-size: 16px;
        }

        .left {
            width: 100%;
            float: left; /*float不多余，没有会导致right和最下边的left对齐，上边空白*/
            margin-left: -100%; /*marign会改变占位*//*margin的参考值是父元素？*/
            color: black;
        }

        .right {
            color: black;
        }

        .clearfix {
            clear: both;
            *zoom: 1;
        }

        .clearfix:before,
        .clearfix:after {
            display: table;
            content: '';
        }

        .clearfix:after {
            clear: both;
        }
```
```html
<!--等高的实现为撑开了wrap的高度，wrap一半为border，一半为内容，实现两部分-->
<div class="wrap clearfix" >
    <div class="left">
        <p>left1</p>
        <p>left1</p>
    </div>
    <div class="right">
        <p>right1</p>
        <p>right1</p>
    </div>
</div>
```