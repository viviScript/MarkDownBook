# JavaScript忍者秘籍

## 断言

单元测试框架的核心是断言方法，通常叫assert()。
该方法通常接收一个值--需要断言的值，以及一个表示该断言目的的描述。
如果该值执行的结果为true，断言就会通过；
否则，断言就会被认为是失败的。
通常用一个相应的通过（pass）/ 失败（fail）标记记录相关的信息；

```javascript
function assert(value, desc) {
    let li = document.createElement('li');
    li.className = value ? 'pass' : 'fail';
    li.appendChild(document.createTextNode(desc));
    document.getElementById('results').appendChild(li);
}

// 断言函数
function assert(value, desc) {
    if (value) {
        console.log(`\033[32m ${desc} \033[0m`);    // 断言通过 绿色字体
    } else {
        console.log(`\033[31m ${desc} \033[0m`);    // 断言失败 红色字体
    }
}
```

## 函数

* ```JavaScript是一门函数式语言```

* ```在JavaScript中，函数是第一型对象。函数可以共处，可以视作为其他任意类型的对象。就像普通的JavaScript数据类型，，函数可以被任意变量进行引用，或声明成对象字面量，甚至可以将其作为函数参数进行传递。```

* ```函数是第一型对象```
  * 可以通过字面量进行创建。
  * 可以赋值给变量、数组或其他对象的属性。
  * 可以作为参数传递给函数。
  * 可以作为函数的返回值进行返回。
  * 可以拥有动态创建并赋值的属性。

* ```命名一个函数时，该名称在整个函数声明范围内是有效的。如果函数声明在顶层，window对象上的同名属性则会引用到该函数。```

* ```所有的函数都有一个name属性，该属性保存的是该函数名称的字符串。匿名函数的name属性值为空。```