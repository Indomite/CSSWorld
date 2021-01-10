# 盒尺寸四大家族

## content

### content 与替换元素

#### 替换元素：通过修改属性值，达到内容的修改的元素就称为替换元素

`img, object, video, iframe, textarea, input`都是典型的替换元素

1、内容的外观不受页面上的 CSS 的影响
2、有自己的尺寸
3、在很多 CSS 属性上有自己的一套表现规则（vertical-align）
尺寸计算规则：CSS 尺寸>HTML 尺寸>元素固有尺寸
替换元素上没有了 src 属性，和普通的内联元素没有区别
其中的 src 可以通过在 CSS 中指定 content 内容实现
但是 content 只是改变了视觉的呈现，元素的内部其实还是 src 属性

#### 关于 content 内容生成技术

content 在项目开发中用的比较多的就是伪元素添加内容，比如说 font 图标、清除浮动等等

1、content 的辅助元素生成

```css
.element:before {
    content: '',
    display: block,
    clear: both
}
```

一般用于清除浮动

2、content 字符内容生成

```css
.icon-home:before {
    font-size: 16px,
    font-family: myico,
    content: 'home'
}
```

一般用于 icon-font 图标的引用

3、content 图片的生成

```css
div:before {
  content: url(1.png);
}
```

直接使用 url 引用图片，使用不多（尺寸不好控制），还是使用 background-image

4、了解 content 开启闭合符号生成

```css
q:before {
  content: '"';
}
q:after {
  content: '提问:"';
}
```

不仅仅限于在 CSS 中放置开启闭合的符号，同时也可以放置字符
5、content attr 属性值内容生成

```css
img:after {
  content: attr(alt); // 不能含有引号
}
```

6、content 计数器
content-reset、content-increment
7、content 内容生成的混合特性
也就是将上述的写法混合在一起使用

## padding

padding在四大属性中应该算是最好的元素了，一般布局使用padding居多

### padding与元素尺寸

padding不仅在水平方向是有效的，同样在垂直方向也是有效的

### padding的百分比

1、与margin不同的是，padding属性不支持负值
2、padding支持百分比
在计算是，padding的百分比在水平、垂直方向都是基于相对宽度计算的

## margin

### margin与元素尺寸以及相关布局

元素尺寸：border box
元素内部尺寸：padding box
元素外部尺寸：margin box

#### margin与元素的内部尺寸

只有元素是充分利用可用空间的时候，margin才会有效果
换句话说，也就是当width属性没有被固定的时候才有效果

#### margin与元素的外部尺寸

在默认的水平流下，margin只能改变水平方向的内部尺寸，但是外部尺寸中可以完全使用

#### margin合并

1、相邻兄弟元素margin合并
2、父级和第一个/最后一个子级合并
3、空块级的margin合并

合并的取值规则：符号相同的时候取绝对值更大的，符号不同则相加

#### 关于margin：auto

1、如果一侧定值，一侧auto，auto就是剩余的空间
2、两侧都是auto，均分空间，居中

#### margin无效的情形

1、display计算值inline的非替换元素的垂直margin无效
2、表格中tr、td元素或者设置display：table-cell,table-row的元素margin是无效的
3、margin合并的时候无效
4、绝对定位中没有定位的方向（top:10px,left:20px）使用（margin-right）无效
5、定了高宽的元素的margin-bottom、margin-right无效

## border

border-style：none solid dashed double dotted

border-color

border图形的构建，设计三角形等