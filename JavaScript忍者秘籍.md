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

* ```在JavaScript中，作用域是由function进行声明的，而不是代码块。声明的作用域创建于代码块，但不是终结于代码块（其他语言是终结于代码块的）```

```javascript
if (window) {
    var x = 123;
}
alert(x);

执行代码后，会弹出123，是因为JavaScript在大括号关闭处并没有终止其作用域。
```

* ```变量声明的作用域开始于声明的地方，结束于函数的结尾，与代码嵌套无关。```

* ```命名函数的作用域是指声明该函数的整个函数范围，与代码嵌套无关；```

* ```对于作用域声明，全局上下文就像一个包含页面所有代码的超大型函数。```

* ```所有的函数调用都会传递两个隐式参数：argument和this```

### 作为函数进行调用

如果一个数不是作为方法、构造器、或者通过apply()或call()进行调用的，则认为它是“作为函数”进行调用的。

```javascript
function ninja() {};
ninja()

var samurai = function() {};
samurai()
```

* ```以这种方式调用时，函数的上下文是全局上下文---window对象。```

### 作为方法进行调用

当一个函数被赋值给对象的一个属性，并使用引用该函数的这个属性进行调用时，那么函数就是作为该对象的一个方法进行调用的。

```javacript
var 0 = {};
o.whatever = function() {};
o.whatever();
```

* ```将函数作为对象的一个方法进行调用时，该对象就变成了函数上下文，并且在函数内部可以以this参数的形式进行访问。```

### 作为构造器进行调用

* ```将函数作为构造器进行调用，需要在函数调用前使用new关键字```
  * 创建一个新的空对象；
  * 传递给构造器都对象是this参数，从而成为构造器的函数上下文；
  * 如果没有显式都返回值，新创建的对象则作为构造器的返回值进行返回。

  ```javascript
  function Ninja() {
      this.skulk = function() { return this; }
  }

  var ninja1 = new Ninja();
  var ninja2 = new Ninja();
  ```

  * ```构造器的目的是通过函数调用初始化创建新的对象。```

### 函数调用方式差异

* ```函数调用方式之间点主要差异是：作为this参数传递给执行函数的上下文对象之间点区别。```
  * 作为方法调用，该上下文是方法的拥有者；
  * 作为全局函数进行调用，其上下文永远是window（也就说，该函数是window的一个方法）。
  * 作为构造器进行调用，其上下文对象则是新创建的对象实例。

### 使用apply()和call()方法

* ```通过函数的apply()方法来调用函数，需要给apply()传入两个参数：一个是函数上下文的对象，另一个是作为函数参数所组成的数组；```
* ```通过函数的call()方法来调用函数，需要给call()传入两个参数：一个是函数上下文的对象，另一个是作为函数参数的参数列表，而不是单个数组；```

```javascript
function juggle() {
    var result = 0;
    for (var n = 0; n < arguments.length; n++) {
        result += arguments[n]
    }
    this.result = result;
}
var ninja1 = {};
var ninja2 = {};

juggle.apply(ninja1, [1,2,3,4]);
juggle.call(ninja2, 5,6,7,8)

assert(ninja1.result === 10, 'juggled via apply');
assert(ninja2.result === 26, 'juggled via call');
```

* ```使用apply()和call()可以选择任意对象作为函数上下文；```

## 函数总结

* 函数是第一型对象；
  * 通过字面量进行创建。
  * 赋值给变量或属性。
  * 作为参数进行传递。
  * 作为函数结果进行返回。
  * 拥有属性和方法。
* 函数是通过字面量进行创建的，其名称是可选的。
* 在页面生命周期内，浏览器可以将函数作为各种类型的事件处理程序进行调用。
* 变量的作用域开始于声明处，结束于函数尾部，其会跨域边界（如：大括号）
* 内部函数在当前函数的任何地方都可用（提升），即便是提前引用。
* 函数的形参列表和实际参数列表的长度可以是不同的。
  * 未赋值的参数被设置为undefined。
  * 多出的参数是不会绑定到参数名称的。
* 每个函数调用都会传入两个隐式参数。
  * arguments，实际传入的参数集合。
  * this，作为函数上下文的对象引用。
* 可以用不同的方法进行函数调用，不同的调用机制决定了函数上下文的不同。
  * 作为普通函数进行调用时，其上下文是全局对象（window）。
  * 作为方法进行调用时，其上下文是拥有该方法的对象。
  * 作为构造器进行调用时，其上下文是新分配的对象实例。
  * 通过函数的apply()或call()方法进行调用时，上下文可以设置成任意值。

## 匿名函数

* ```为了不让不必要的函数名称污染全局命名空间，可以创建大量的小型函数进行传递，而不是创建包含大量命令语句的大型函数。```

## 递归

* ```递归：当函数调用自身，或调用另外一个函数，但这个函数的调用树中的某个地方又调用到了自己时，就产生了递归。```

* ```递归的两个条件：引用自身，并且有终止条件。```

## 闭包

* ```闭包是一个函数在创建时允许自身函数访问并操作该自身函数之外的变量时所创建的作用域```

* ```闭包可以让函数访问所有的变量和函数，只要这些变量和函数存在于该函数声明时的作用域内就行。```

```javascript
var outerValue = 'ninja';

var later;


function outerFunction() {

    // 该变量的作用域限制在该函数内部，并且在函数外部访问不到；
    var innerValue = 'samurai';

    // 在外部函数内，声明一个内部函数。
    // 注意：声明该函数时，innerValue是在作用域内的
    function innerFunction() {
        assert(outerValue, 'I can see the ninja');
        assert(innerValue, 'I can see the samurai');

        // 将内部函数引用到later变量上，由于later在全局作用域内，所以可以对它进行调用。
        later = innerFunction;
    }
}

// 调用外部函数，将会声明内部函数，并将内部函数赋值给later变量。
outerFunction();

// 通过later调用内部函数。
// 我们不能直接调用内部函数，因为它的作用域（和innerValue一起）被限制在outerFunction内。
later();
```

### 闭包使用场景：私有变量

* ```在构造器内隐藏变量，使其在外部作用域不可访问，但是可以存在于闭包内。```

```javascript
function Ninja() {
    var feints = 0;

    this.getFenits = function() {
        return feints;
    }

    this.feint = function() {
        feints++;
    }
}

var ninja = new Ninja();

ninja.feint();

assert(ninja.getFenits() === 1, '调用一次，内部变量++');

assert(ninja.feints === undefined, '函数外部不可访问')
```

* ```变量的作用域依赖于变量所在的闭包```

* ```闭包记住的是变量的引用，而不是闭包创建时刻该变量的值```

## 原型与面向对象

* ```所有的函数在初始化时都有一个prototype属性，该属性的初始值是一个空对象。```
* ```使用new操作符将函数作为构造器进行调用的时候，其上下文被定义为新对象的实例。```
* ```在构造器内的绑定操作优先级永远高于在原型上的绑定操作优先级。因为构造器的this上下文指向的是实例自身，所以我们可以在构造器内对核心内容执行初始化操作。```