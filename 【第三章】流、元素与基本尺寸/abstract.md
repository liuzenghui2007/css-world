# abstract

+ "margin的背景永远是透明的"，因此不可能作为background-clip或background-origin属性出现。margin一旦设定具体宽度和高度值，其本身的尺寸是不会因margin值变化而变化的，因此作为box-sizing的属性值存在也就没有意义

+ 为何box-sizing不支持margin-box
    > 不支持margin-box最大的原因是它本身就没有价值！不妨好好想想，一个元素，如果我们使用width或height设定好了尺寸，请问我们此时设置margin值，其offset尺寸会有变化吗？不会啊，100像素宽的元素，在怎么设置margin，它还是100像素宽。但是border和padding就不一样了，100像素宽的元素，设置了20像素大小的padding值，offsetWidth就是140像素了，尺寸会变化。你说，一个本身并不会改变元素尺寸的盒子，它有让box-sizing支持的道理吗？box-sizing就是改变尺寸作用的规则！margin只有在width为auto的时候可以改变元素的尺寸，但是，此时元素已经处于流动性状态，根本就不需要box-sizing。所以，说来说去就是margin-box本身就没有价值

    > 另外一个原因牵扯到语义。如果box-sizing开了先河支持了margin-box，margin box就变成了一个“显式的盒子”，你让background-origin等属性何去何从，支持还是不支持？“margin的背景永远是透明的”这几个大字可是在规范写得清清楚楚，难道让背景色在所谓的margin box中也显示？显然是不可能的。