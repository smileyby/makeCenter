## 实现水平居中和垂直居中

### 水平居中

>1）若为行内元素，给父元素设置text-align:center，即可实现行内元素水平居中。
>2）若为块级元素，该元素设置margin:0 auto;即可。
>3)若子元素包含float：left属性，为了让子元素水平居中，则可让父元素设置为fit-content，并且配合margin，作如下设置：

```css
	.parent {
		width: -moz-fit-content;
		width: -webkit-fit-content;
		width: fit-content;
		margin: 0 auto;
	}
```
> fit-content是CSS3给width属性新增加的一个属性值，它配合margin轻松实现水平居中，目前只支持Chrome和Firefox浏览器。
> 4）使用flex布局，可以轻松的实现水平居中，子元素设置如下：

```css
	
	.son {
		display: flex;
		justify-content: center;
	}
	
```

> 5)使用CSS3和模型，父元素display：box；box-pack：center；如下设置：

```css
	
	.parent {
		display: -webkit-box;
		-webkit-box-orient: horizontal;
		-webkit-box-pack: center;
		display: -moz-box;
		-moz-box-orient: horizontal;
		-moz-box-pack: center;
		display: -o-box;
		-o-box-orient: horizontal;
		-o-box-pack: center;
		display: -ms-box;
		-ms-box-orient: horizontal;
		-ms-box-pack: center;
		display: box;
		box-orient: horizontal;
		box-pack: center;
	}

```

>6)使用CSS3中新增的transform属性，子元素设置如下：

```css

	.son {
		position: absolute;
		left: 50%;
		transform: translate(-50%, 0);
	}

```

>7)使用绝对定位方式，以及负值的margin-left，子元素设置如下：

```css 
	
	.son {
		position: absolute;
		width: 固定；
		left: 50%;
		margin-left: -0.5*宽度;
	}

```

>8)是用决定定位方式，以及left：0；right：0；margin：0 auto;，子元素设置如下：

```css
		
	.son {
		position: absolute;
		width: 固定;
		left: 0;
		right: 0;
		margin: 0 auto;
	}
	
```