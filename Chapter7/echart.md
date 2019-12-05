# 第1节 Echart

3.1.4 echart

在平时开发项目时，免不了需要对数据进行图表显示的需求，比如：趋势图、饼状图、柱形图等。自己身为一个PHPer，除了PHP本身的功能，不得不需要借助js来实现显示。在了解众多趋势图插件，国内外开源的项目，感觉还是来自百度团队研发的Echarts.js效果更好。本身是中文的项目，使用过程和显示效果更加适合使用。

#### 什么是Echarts.js?

Echarts.js是来自百度团队研发的图表js插件，利用HTML+js实现折线图、饼状图、热点图、3d图形等等，可在PC和移动端显示，加载速度快，功能丰富。

# Echart.js的趋势图入门与实例 

在平时开发项目时，免不了需要对数据进行图表显示的需求，比如：趋势图、饼状图、柱形图等。自己身为一个PHPer，除了PHP本身的功能，不得不需要借助js来实现显示。在了解众多趋势图插件，国内外开源的项目，感觉还是来自百度团队研发的Echarts.js效果更好。本身是中文的项目，使用过程和显示效果更加适合使用。

#### 什么是Echarts.js?

Echarts.js是来自百度团队研发的图表js插件，利用HTML+js实现折线图、饼状图、热点图、3d图形等等，可在PC和移动端显示，加载速度快，功能丰富。

![img](https:////upload-images.jianshu.io/upload_images/10987359-dcef0f72747972d8.png?imageMogr2/auto-orient/strip|imageView2/2/w/1029/format/webp)

image.png

我在多了解这个软件后，深深的被其功能所折服。在官方实例中，提供了十多种显示的方式，感人感觉最厉害的属于显示地球还有城市热点的功能。



![img](https:////upload-images.jianshu.io/upload_images/10987359-f044df914542489b.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

显示地球模型

官方提供的实例地址：http://echarts.baidu.com/examples/#chart-type-line

当然，这个功能在平时开发中很难需要用到，用到最多的还是折线图、饼状图之类的基础功能。

#### 折线图功能实现实例

先看一下展示效果，模仿某广告平台在某天的24小时的流量走势。



![img](https:////upload-images.jianshu.io/upload_images/10987359-69465f505d330256.png?imageMogr2/auto-orient/strip|imageView2/2/w/1104/format/webp)

image.png

### 实现步骤：

1、在页面中获取Echarts
 在官网中根据需要的版本http://echarts.baidu.com/download.html


![img](https:////upload-images.jianshu.io/upload_images/10987359-4f61854be371dadc.png?imageMogr2/auto-orient/strip|imageView2/2/w/871/format/webp)

image.png


 例如本例中实现的折线图，获取常用版或者精简版就够了。

2、引入Echarts

```xml
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <!-- 引入 ECharts 文件 -->
    <script src="echarts.min.js"></script>
</head>
</html>
```

3、为Echarts放置一个具备宽高的DOM容器

```xml
<div id="show_charts" style="width:100%; height:600px; margin:80px 0 80px 0;"></div>
```

4、Echarts加载数据

```kotlin
<script type="text/javascript">
/*此段js来自百度Echart.js插件*/
var dom = document.getElementById("show_charts");
var myChart = echarts.init(dom);
var app = {};
option = null;
option = {
    title : {
        text: '趋势图',
        subtext: '\r\n时间：2018-08-01\r\n\r\n广告类型：全部'
    },
    tooltip : {
        trigger: 'axis'
    },
    legend: {
        data:['请求','返回','展示','点击','成本支出']
    },
    toolbox: {
        show : true,
        feature : {
            mark : {show: true},
//            dataView : {show: true, readOnly: false},     //数据视图按钮
            magicType : {show: true, type: ['line', 'bar']},
//            restore : {show: true},       //图表右上角刷新按钮
            saveAsImage : {show: true}
        }
    },
    calculable : true,
    xAxis : [
        {
            type : 'category',
            boundaryGap : false,
            data: ["00:00~01:00","01:00~02:00","02:00~03:00","03:00~04:00","04:00~05:00","05:00~06:00","06:00~07:00","07:00~08:00","08:00~09:00","09:00~10:00","10:00~11:00","11:00~12:00","12:00~13:00","13:00~14:00","14:00~15:00","15:00~16:00","16:00~17:00","17:00~18:00","18:00~19:00","19:00~20:00","20:00~21:00","21:00~22:00","22:00~23:00","23:00~00:00"] }
    ],
    yAxis : [
        {
            type : 'value',
            axisLabel : {
                formatter: '{value}'
            }
        }
    ],
    series : [
        {
            name:'请求',
            type:'line',
            data:["162408","84274","51885","32385","29434","44453","113740","228128","344679","462128","585712","661449","704045","698178","642736","621051","614459","604958","615722","606564","721321","700773","519813","297617"]        },
        {
            name:'返回',
            type:'line',
            data:["152827","67202","37269","20956","18687","34066","103310","214873","327262","426414","524510","572305","600487","596252","544651","520815","509897","500239","501439","491926","577558","552850","401406","219789"]        },
        {
            name:'展示',
            type:'line',
            data:["115483","47313","26211","14156","12454","24095","74951","157273","237750","305293","373653","403249","423604","409693","367890","349129","343804","333511","333344","327859","391295","371397","265205","143960"]        },
        {
            name:'点击',
            type:'line',
            data:["4091","1735","959","632","664","1576","3996","7038","13033","14639","16757","17034","18368","17084","14718","14087","13928","13212","13042","13501","16424","15824","11331","6073"]        },
        {
            name:'成本支出',
            type:'line',
            data:[622.02,260.1,144.37,82.63,75.92,159.33,491.01,976.69,1494.82,1859.92,2215.17,2379.43,2569.69,2477.18,2220.92,2134.79,2094.97,2039.94,2021,2000.8,2325.55,2222.01,1590.13,859.93]        }
    ]
};
                    
;
if (option && typeof option === "object") {
    myChart.setOption(option, true);
}
</script>
```

经过代码设置，一个折线图是不是已经好了呢。没好的话，请检查Echarts.js文件的引用，此案例本人亲测过。这是一个折线图的功能，有很多参数需要我们在平时开发中去发现，大家可以多读读官方的教程，以及案例。[官网实例链接](http://echarts.baidu.com/examples/#chart-type-line)

好了，就介绍这些，希望此文章能对大家探索Echarts有所帮助。