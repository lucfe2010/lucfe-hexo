---
title: javascript problems 1
toc: true
categories: [category1 level1, category1 level2]
---

## `(0,function)(arg1,agr2,)`

```js
(0, function (arg) { console.log(arg) })(2);
console.log((0, 1, 2, 3));
(0, function plus1 (arg) { console.log(arg + 1) }, function plus2 (arg) { console.log(arg + 2) })(5);
```

## example one

```js
(function() {
  (0,eval)("var foo = 123"); // indirect call to eval, creates global variable
})();
console.log(foo);            // 123
(function() {
  eval("var bar = 123");     // direct call to eval, creates local variable
})();
console.log(bar);            // ReferenceError
```

## example two

when you want to call a method without passing the object as the this value:

```js
var obj = {
  method: function() { return this; }
};
console.log(obj.method() === obj);     // true
console.log((0,obj.method)() === obj); // false
```

## example three

depending on the context, it might be the arguments separator instead of a comma operator:

```js
console.log(
  function(a, b) {
    return function() { return a; };
  }
  (0, function (arg) { /* ... */ })(this)
); // 0
```

In this scenario, `(0, function (arg) { /* ... */ })` are the arguments `(a=0, b=function (arg) { /* ... */ })` to the function

```js
function(a, b) {
  return function() { return a; };
}
```

rather than the comma operator. Then, the `(this)` at the end is function call with argument this to the returned function `function() { return a; }`.
