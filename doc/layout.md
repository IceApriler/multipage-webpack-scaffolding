
[参考](https://juejin.cn/post/6844903701891514382)

### 水平居中

1. `inline-block` + `text-align`

```css
.parent{
    text-align: center;
}
.child{
    display: inline-block;
}
```
> tips：此方案兼容性较好，可兼容至IE8，对于IE567并不支持`inline-block`，需要使用css hack进行兼容

2. `table + margin`

```css
.child{
    display: table;
    margin: 0 auto;
}
```
> tips：此方案兼容至IE8，可以使用`<table/>`代替css写法，兼容性良好

3. `absolute` + `transform`

```css
.parent{
    position: relative;
    height:1.5em;
}
.child{
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
}
```
> tips：此方案兼容至IE9，因为`transform`兼容性限制，如果`.child`为定宽元素，可以使用以下写法，兼容性极佳

```css
.parent{
    position: relative;
    height:1.5em;
}
.child{
    position: absolute;
    width:100px;
    left: 50%;
    margin-left:-50px;
}
```

4. `flex` + `justify-content`

```css
.parent{
    display: flex;
    justify-content: center;
}
.child{
    margin: 0 auto;
}
```
> tips：flex是一个强大的css，生而为布局，它可以轻松的满足各种居中、对其、平分的布局要求，但由于现浏览器兼容性问题，此方案很少被使用，但是值得期待浏览器兼容性良好但那一天！

### 垂直居中

1. `table-cell` + `vertial-align`

```css
.parent{
	display: table-cell;
	vertical-align: middle;
}
```
> tips：可替换成`<table />`布局，兼容性良好

2. `absolute` + `transform`

```css
.parent{
	position: relative;
}
.child{
	position: absolute;
	top: 50%;
	transform: translateY(-50%);
}
```
> tips：存在css3兼容问题，定宽兼容性良好

3. `flex` + `align-items`

```css
.parent{
	display: flex;
	align-items: center;
}
```
> tips：高版本浏览器兼容，低版本不适用

### 水平垂直居中

1. `inline-block` + `table-cell` + `text-align` + `vertical-align`

```css
.parent{
	text-align: center;
	display: table-cell;
	vertical-align: middle;
}
.child{
	display: inline-block;
}
```
> tips：兼容至IE8

2. `absolute` + `transform`

```css
.parent{
	position: relative;
}
.child{
	position: absolute;
	left: 50%;
	top: 50%;
	transform: translate(-50%,-50%);
}
```
> tips：兼容性稍差，兼容IE10以上

3. `flex`

```css
.parent{
	display: flex;
	justify-content: center;
	align-items: center;
}
```
> tips：兼容差

### 多列布局

#### 一列定宽，一列自适应

1. `float` + `margin`

```css
.left{
	float: left;
	width: 100px;
}
.right{
	margin-left: 120px;
}
```
> tips：此方案对于定宽布局比较好，不定宽布局推荐方法2

2. `float` + `overflow`

```css
.left{
	float: left;
	width: 100px;
	margin-right: 20px;
}
.right{
	overflow: hidden;
}
```
> tips：个人常用写法，此方案不管是多列定宽或是不定宽，都可以完美实现，同时可以实现登高布局

3. `table`

```css
.parent{
	display: table; 
  width: 100%;
	table-layout: fixed;
}
.left,.right{
	display: table-cell;
}
.left{
	width: 100px;
	padding-right: 20px;
}
```

4. flex

```css
.parent{
	display: flex;
}
.left{
	width: 100px;
	padding-right: 20px;
}
.right{
	flex: 1;
}
```