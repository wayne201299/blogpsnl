---
title: JavaScript白話文系列 - 閉包
date: 2022-03-25 14:26:28
categories: 前端開發
tags: JavaScript
---

之前完全沒使用過閉包的技巧，身為一個前端工程師，寫了這麼多年的code，到底什麼是閉包？就用這篇來記錄自己對於閉包這個名詞的解釋吧！主要會以我在網路上蒐集到關於閉包的文章加上自己的見解來寫，盡量白話一點解釋

首先，在MDN上對於[閉包](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)的解釋如下
> A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the **lexical environment**). In other words, a closure gives you access to an outer function's scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.

中文是
> 閉包（Closure）是函式以及該函式被宣告時所在的作用域環境（lexical environment）的組合。

重新解釋一遍

當一個function被建立時，會儲存一組當下的作用域及function本身在記憶體中
<!-- more -->
:::info
作用域：指的是程式執行時當下各個變數值有效的範圍
:::



情境
---
想想執行下面這段程式碼會發生什麼事?

```javascript=
function makeFunc(){
    var name = 'Mozilla'; // name為存在makeFunc中的區域變數
    function closureFunc(){ // closureFunc為內部函式，是一個閉包
        alert(name); // 使用外部函式宣告的變數
    }
    closureFunc();
}

makeFunc()
```
1. 宣告了一個 makeFunc 的函式
2. makeFunc內包含了`name`及`closureFunc()`
3. 內部的`closureFunc()`透過取得外部函式`makeFunc()`來取得`name`變數值

:::info
結論：
在JavaScript執行環境中，內部函式是可以訪問到外部函式的變數值的
:::

閉包
---

換舉另一個例子

```typescript=
function makeFunc() {
  var name = "Mozilla";
  function closureFunc() {
    alert(name);
  }
  return closureFunc;
}

var myFunc = makeFunc(); // myFunc會是一個closureFunc
myFunc();  // 單獨執行closureFunc

```

- 預期執行`myFunc()`時，`name`會是undefined，結果卻可以正常吃到`name`！ 🤨

:::info
閉包為函式的組合、還有宣告該函式的作用域環境。這個環境包含閉包建立時，所有位於該作用域的區域變數
:::
- 變數`myFunc`會作為一個參照，裡面包含了`closureFunc()`及`name`當下的value
- 當`myFunc()`再次執行時，會從記憶體位址中取得`closureFunc()`及當下作用域的變數值，所以alert會有結果

再舉一個例子
```typescript=
function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));  // 7
console.log(add10(2)); // 12

```

1. 宣告一個add5 作用域，x=5
2. 宣告一個add10 作用域，x=10
3. 執行add5(2)，此時add5作用域內已經有x=5了，傳入y=2，x+y=7
4. 執行add10(2)

函式執行時當下的作用域非常重要！！！

使用
---
這邊有幾個主要的使用場景

- HTML 上的event 觸發，回傳callback時
- 模擬private 方法，保護作用域內的變數命名不會溢出，**Module pattern**
    ```typescript=
    var counter = (function() {
      var privateCounter = 0;
      function changeBy(val) {
        privateCounter += val;
      }
      return {
        increment: function() {
          changeBy(1);
        },
        decrement: function() {
          changeBy(-1);
        },
        value: function() {
          return privateCounter;
        }
      };
    })();

    console.log(counter.value()); // logs 0
    counter.increment();
    counter.increment();
    console.log(counter.value()); // logs 2
    counter.decrement();
    console.log(counter.value()); // logs 1

    ```
    在這邊我們建立一個counter環境，被`increment`、`decrement`、`value`所共用，透過IIFE(立即呼叫函式)，建立後立刻執行，裡面包含了`privateCounter`、`changeBy()`兩個private物件，這兩個物件只能在counter內部中使用
    
:::info
Module Pattern(Reveal Module):
建立一個module，而內層的函式具有閉包的特性，因此可以存取外部的物件及方法，但同時不會洩漏內部資訊，還可以控制要回傳的內容
:::
