# 记录前端学习过程中容易忘记和混淆的知识点


<p>1. typeof用来判断基本类型比较准确，对于引用类型，除function外均判定为object；
instanceof利用原型链进行判断，不能判断基本类型。</p>
<p> 2.手写instanceof
  <pre>
  function myinstanceof(left,right){
    let proto = left.__proto__;
    let prototype = right.prototype;
    while(true) {
      if(proto === null) return false;
      if(proto === prototype) return true;
      proto = proto.__proto__;
    }
  }
  </pre>
</p>
<p>
3.对象的类型转换：调用内置的[[ToPrimitive]]函数，顺序为：Symbol.toPrimitive > valueOf > toString.目标：将对象转成原始类型。
  <pre>
  let a = {
  valueOf() {
    return 0
  },
  toString() {
    return '1'
  },
  [Symbol.toPrimitive]() {
    return 2
  }
}
1 + a // => 3
  </pre>
</p>
<p>
  4. slice,substring,substr:
  <table style="textAlign:center">
    <tr><td>函数</td><td>第一个参数</td><td>第二个参数</td><td>是否接受负值</td></tr>
    <tr><td>slice</td><td>start</td><td>stop</td><td>true</td></tr>
    <tr><td>substring</td><td>start</td><td>stop</td><td>false</td></tr>
    <tr><td>substr</td><td>start</td><td>length</td><td>true</td></tr>
  </table>
</p>
<p>
  5.Object.keys()和for...in <br>
  Object.keys(),Object.values(),Object.entries()都是返回对象自身可枚举的属性键值；for...in不仅可以循环枚举自身属性，还可以枚举原型链上的属性。
</p>
<p>
6.不管给函数bind几次，函数中的this永远由第一次bind决定
</p>
<p>
7.Object.assign({},a) 只会拷贝所有的属性值到新的对象中，如果属性值是对象的话，拷贝的是地址，所以并不是深拷贝.a={...b}同Object.assign（）;
  [a] = [b] , const {a} = b(a = b.a) 为浅拷贝。
</p>
<p>
8. es5和es6继承的区别：<br>
es5先创建子类，再实例化父类并添加到子类this中<br>
es6先创建父类，调用super方法访问父类后，再通过修改this实现继承</p>
<p>
9. css动画和重排重绘<br>
  尽量使用transform代替left、top等，尽量不使用setTimeout和setInterval。必要时可以创建图层减少对其他元素的影响。
  https://segmentfault.com/a/1190000000490328
</p>
<p>
10. 移动端web页面适配<br>
  viewport视口：<br>
  1)visual viewport : 屏幕宽度，document.innerWidth/Height;<br>
  2)layout viewport : DOM宽度, document.documentElement.clientWidth/Height;<br>
  3)ideal viewport : 屏幕宽度等于DOM宽度 <meta name="viewport" content="width=device-width,initial-scale=1"><br>
  4)关系： (visual viewport) = (layout viewport) * scale<br>
  所谓的一倍屏、二倍屏(Retina)、三倍屏，指的是设备以多少物理像素来显示一个CSS像素<br>
  设备像素比(dpr) ＝ 物理像素 / 设备独立像素<br>
  获取当前设备的dpr：window.devicePixelRatio<br>
  em相对于父元素，rem相对于根元素<br>
</p>
<p>
11. 图片按需加载：1）js监听页面滚动；2）intersectionObserver监听；3）懒加载组件；4）loading属性（loading=lazy）<br>
</p>
<p>
12. 解决同一张图片在高分辨率屏幕上显示模糊问题：1）媒体查询，使用不同大小的图片；2）利用img的srcset属性（srcset="bg.png 1x;bg@2x.png 2x"）
</p>
