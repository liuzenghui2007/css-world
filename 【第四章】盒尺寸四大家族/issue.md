- [4-3激进的margin属性](#4-3%E6%BF%80%E8%BF%9B%E7%9A%84margin%E5%B1%9E%E6%80%A7)
  - [鞭长莫及导致的 margin 无效](#%E9%9E%AD%E9%95%BF%E8%8E%AB%E5%8F%8A%E5%AF%BC%E8%87%B4%E7%9A%84-margin-%E6%97%A0%E6%95%88)
  - [内联特性导致的 margin 无效。](#%E5%86%85%E8%81%94%E7%89%B9%E6%80%A7%E5%AF%BC%E8%87%B4%E7%9A%84-margin-%E6%97%A0%E6%95%88)

# 4-3激进的margin属性

## 鞭长莫及导致的 margin 无效
```html
<div class="box"> 
    <img src="mm1.jpg">
    <p>内容</p>
</div>
<style>
.box > img {
    float: left;
    width: 256px;
}
.box > p {
    overflow: hidden;
    margin-left: 200px;
}
</style>
```

其中的 margin-left:200px 是无效的，准确地讲，此时的p的 margin-left 从负无穷到 256px 都是没有任何效果的。要解释这里为何会无效，需要对 float 和 overflow 深入理解，而这两个属性都是后面的内容，因此，深入原因分析我们将在 6.4 节介绍。

## 内联特性导致的 margin 无效。
```html
<div class="box">
    <img src="mm1.jpg">
</div>
<style>
.box > img {
    height: 96px;
    margin-top: -200px;
}
</style>
```

这里的例子也很有代表性。一个容器里面有一个图片，然后这张图片设置 margin-top 负值，让图片上偏移。但是，随着我们的负值越来越负，结果达到某一个具体负值的时候，图片不再往上偏移了。比方说，本例 margin-top 设置的是-200px，如果此时把 margin-top 设置成-300px，图片会再往上偏移100px 吗?不会!它会微丝不动，margin-top 变得无效 了。要解释这里为何会无效，需要对 vertical-align 和内联盒模型有深入的理解，而这 vertical-align 是后面的内容，因此，深入原因分析我们将在 5.3 节介绍。这里大家先记住 有这么一个 margin 失效的场景即可。