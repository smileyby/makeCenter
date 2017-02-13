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

### 垂直居中

> 单行文本
> 
> 1.若元素是单行文本，则可设置line-height等于父元素高度
> 
> 行内块级元素
> 2.如元素是行内块级元素，基本思想是使用display：inline-block，vertical-align：middle和一个伪元素内容让内容块处于容器中央

```css
	
	.parent::after, .son {
		display: inline-block;
		vertival-align: middle;
	}
	.parent::after {
		content: '';
 		height: 100%;
	}

```

> 这是一种黑流行的方法，也适应IE7
> 
> 元素高度不定
> 
> 3.可用vertical-align属性，而vertical-align只有在父层为td时，才会生效，对于其他块级元素，例如div、p等，默认情况下是不支持的。为了使用vertical-align，我们需要设置父元素1display：table，子元素display：table-cell;vertical-align:middle;

> 优点

> 元素高度可以动态改变，不需要再css中定义，如果父元素没有足够的空间时，该元素内容也不会被截断。

> 缺点

> IE6~7,甚至IE8 beta中无效
> 
> 4.可用Flex，这是CSS布局未来的趋势，flexbox是css3新增属性，设计初衷是为了解决像垂直居中这样的常见问题。父元素做如下这只可保证子元素垂直居中：

```css

	.parent {
		display: flex;
		align-item: center;
	}
	
```

> 优点
>
> 内容块的宽高任意
> 
> 可用于更复杂高级的布局技术
> 
> 缺点
> 
> IE8/9不支持
> 需要浏览器厂商前缀
> 渲染可能有一些问题

>5.使用CSS3盒模型

```css
	
	.parent {
		display: box;
		box-orient: vertical;
		box-pack: center;
	}
	
```

> 优点（实现简单，扩展性强）
>
>缺点（兼容性差，不支持IE）

> 6.可用transform，设置父元素相对定位（position：relative;）,子元素如下CSS样式：

```css
	
	.son {
		position: absolute;
		top: 50%;
		height: 固定;
		margin-top: -0.5*高度;
	}
	
```

> 优点（使用于所有浏览器）
> 
> 缺点
> 
> 父元素空间不够时，子元素可能不可见（当浏览器窗口缩小时，滚动条不出现时），如果子元素设置overflow：auto；，则高度不够时，会出现滚动条。

> 8.设置父元素行对定位（position:relative;）子元素样式如下：

```css
	
	.son {
		position: absolute;
		height: 固定;
		top: 0;
		bottom: 0;
		margin: auto 0;
	}
	
```

> 优点（简单）
> 
> 缺点（没有足够空间时。子元素会被截断，但不会有滚动条）
