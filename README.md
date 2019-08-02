# note
记录前端学习过程中容易忘记和混淆的知识点

<p>1. typeof用来判断基本类型比较准确，对于引用类型，除function外均判定为object；
instanceof利用原型链进行判断，不能判断基本类型。</p>
<p> 2.手写instanceo
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
3.对象的类型转换：调用内置的[[ToPrimitive]]函数，顺序为：Symbol.toPrimitive > valueOf > toString
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

