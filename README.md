# b2wordcloud

基于[wordcloud2.js](https://github.com/timdream/wordcloud2.js)生成2D词云图

扩展特性若干，如tooltip，渐变色，阴影

![](./demo.jpeg)

线上演示 [DEMO](http://www.baidu.com)

## Installtion
- 通过script引入
```
<script src="dist/b2wordCloud.min.js"></script>
```
- 通过npm安装
```
npm install b2wordcloud --save
```

## Usage
```javascript
var wordCloud = new B2wordCloud(document.getElementById("chart"), {
    list: [
        ['foo', 36], ['bar', 62], ['foo3', 22], ['bar4', 36], ['bar5', 46],['foo', 36], ['bar', 62], ['foo3', 22], ['bar4', 36], ['bar5', 46],['foo', 36], ['bar', 62], ['foo3', 22], ['bar4', 36], ['bar5', 46],['foo', 36], ['bar', 62], ['foo3', 22], ['bar4', 36], ['bar5', 46],['foo', 36], ['bar', 62], ['foo3', 22], ['bar4', 36], ['bar5', 46],['foo', 36], ['bar', 62], ['foo3', 22], ['bar4', 36], ['bar5', 46],['foo', 36], ['bar', 62], ['foo3', 22], ['bar4', 36], ['bar5', 46],['foo', 36], ['bar', 62], ['foo3', 22], ['bar4', 36], ['bar5', 46],['foo', 36], ['bar', 62], ['foo3', 22], ['bar4', 36], ['bar5', 46],['foo', 36], ['bar', 62], ['foo3', 22], ['bar4', 36], ['bar5', 46]
    ],
    tooltip: {
        show: true,
        formatter: function(item) {
            return '<div>' + item[0] + '</div>' + '<div>' + item[1] + '</div>'
        }
    },
    shadowColor: 'rgba(0,0,0,0.9)',
    shadowOffsetX: 2,
    shadowOffsetY: 2,
    shadowBlur: 5,
    color: [
        ['#f00', '#ff0'],
        '#f00',
        'green',
        '#333',
        'blue',
        ['blue', 'white']
    ]
})
```

## API documentation

基于[wordcloud2](https://github.com/timdream/wordcloud2.js)进行开发，因此基础API在此不重复描述，如有查看需要，可查看[wordcloud2 API documentation](https://github.com/timdream/wordcloud2.js/blob/gh-pages/API.md)

-以下为新增或有改动的配置项

### options
- `renderer`：新增配置项**渲染模式**，默认为"canvas"，可选择"div"
  - e.g. renderer: 'canvas'
- `tooltip`：新增配置项，格式为object格式，详细配置见下
  - `show`：是否显示tooltip，默认为true
  - `formatter`：自定义tooltip格式，返回html，回调参数为当前所选的词
  - `className`： 自定义tooltip的样式名
  - `background`：自定义tooltip背景色，默认为'rgba(0,0,0,0.8)'
- `color`：基于原有的color配置项做了修改，原color配置项支持字符串与函数，此处不变，可兼容原wordcloud2配置，新增特性为支持数组，当color为数组时，将按数组顺序取色，其中数组分以下两种情况
  - 当数组元素为颜色字符串时，直接使用渲染
  - 当数组元素为数组时，将使用数组元素渲染渐变色
    - e.g: color: [['blue', 'white']]，如例子所示，将渲染从上到下由蓝到白的渐变色
- `shadowOffsetX`：新增配置项，文字阴影X轴偏移量
- `shadowOffsetY`：新增配置项，文字阴影Y轴偏移量
- `shadowBlur`：新增配置项，文字阴影模糊量
- `shadowColor`：新增配置项，文字阴影颜色
- `maskImage`： 新增配置项，白底黑形状图片，上传后词云可渲染图片形状
- `maxFontSize`：新增配置项，最大字号
- `minFontSize`：新增配置项，最小字号

### methods

- resize()

当容器大小变化时，可调用此方法重新绘制
e.g: 
var wordCloud = new B2wordCloud(element, options)
wordcloud.resize()


# Licence
MIT