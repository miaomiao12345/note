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

