# Coercion 強制轉型

在 JavaScript 中，Type Conversion 通常又稱為 Coercion。

若在 JavaScript 中聽到這兩者其中之一，通常這兩者，是可以被替換的。

## Abstract Operations 抽象的值運算

在探討強制轉型之前，必須先了解規範這些轉型的基本規則。

這些規則在 ESMA 
參考規範：[7 Abstract Operations](https://www.ecma-international.org/ecma-262/9.0/index.html#sec-abstract-operations)




### ToPrimitive

## ToSrting

## ToNumber

    Remember, empty string is the root of all coercion evil, okay? Empty string becoming 0 is the root of all coercion evil, okay? Same thing with that bottom crazy nested array thing, it just becomes an empty string, which then just becomes 0, okay?


## ToBoolean

    Literally in the spec, that says, here is the value of one of these things if so return false, meaning the false value is what came back from ToBoolean. And otherwise just return true. So it defines a very specific and short limited list of what we call falsy values.



Falsy:
''
0, -0
null
NaN
false
undefined


如果不是 Falsy value，則為 Truthy。

那 `[]` 空陣列會得到什麼呢？
答案是：true

    So pay very close attention to how I describe to ToBoolean, it does not invoke the two primitive algorithm. Or the toNumber, or the toString, or anything, it just does a look up.



## Cases of Coercion

    Because you have been so programmed to believe that this is an evil buggy horrible part of JavaScript that you should avoid, that it's hard to see any value or merit out of this discussion. But I make it such a point of put it in the very top of this course because I think it's one of the most under valued and under looked that things in all of JavaScript.


反正我們只要避免 Coercion （強制轉型），都用 `===` 就好了...嗎？

其實我們處處都在使用 Coercion...

1. 來看看 number to string

Kyle 超級喜歡 template strings，非常方便又可讀性高，而下面這個例子發生了什麼事呢

```js
var numStudents = 16;

console.log(
    `There are ${numStudents} students.`
);

// 'There are 16 students.'
```

參考 the spec：
12.8.3 The Addition Operator ( + )
https://www.ecma-international.org/ecma-262/9.0/index.html#sec-addition-operator-plus


    Which means, if only one of them is a string, guess what's gonna happen to the other one? A two-string operation right there on 7.a. It's gonna call a two string abstract operation on it, and turn it in to a string with all of the weirdnesses in caveats there of.


Kyle 一直在強調：
    No, I'm not here to tell you to stop using coercion, I'm here to tell you you're using coercion, so wouldn't it make sense for you to learn it? That's why we dive into this, okay?

如果你想要非常明確的表示經過強制轉型

```js
var numStudents = 16;

console.log(
    `There are ${numStudents.toString()} students.`
);

// 'There are 16 students.'
```

    There's a little weirdness here which is how are you calling a method on a primitive value?
    Primitive values don't have methods. So you're actually already still doing implicit coercion here and we'll come back to that.



    If you don't wanna do any implicit coercion at all, basically your only option. Is to use that fundamental object without a new keyword string, and this is my preferred way of explicitly coercing that number to a string, the capital S string function is gonna do that for you.


```js
var numStudents = 16;

console.log(
    `There are ${String(numStudents)} students.`
);

// 'There are 16 students.'
```


2. 另外來看看 string to number 的例子

```js
function addAStudent (numStudents) {
    return numStudent + 1;
}

addAStudent(studentsInputElem.value);  // '161'
```
居然得到 `'161'`


可以用

```js
function addAStudent (numStudents) {
    return numStudent + 1;
}

addAStudent(
    +studentsInputElem.value
);  // 17
```

或 Kyle 覺得更好的方式：

```js
function addAStudent (numStudents) {
    return numStudent + 1;
}

addAStudent(
    Number(studentsInputElem.value)
);  // 17
```


看看 - 負號的例子
```js
function kickStudentOut (numStudents) {
    return numStudent - 1;
}

kickStudentOut(
    studentsInputElem.value
);  // 15
```

    If you use the minus operator that one is only defined for numbers. That it's not overloaded for string, it wouldn't make any sense to subtract one string from another. So that minus operator up there, is gonna do what?
    Come on? toNumber, okay? It's gonna invoke that toNumber abstract operation.





3. any type to boolean

`''` vs `'     '`



## Boxing

primitive to object

如何取得 string.length？



All programming languages have type conversions, because it's absolutely necessary.
You use coercion in JS whether you admit it or not, because you have to.


## Corner Cases of Coercion

(投影片 75 列舉...)

The Root Of All (Coercion) Evil
所有強制轉型怪例的根源

```js
Number(''); // 0

Number('  \t\n'); // 0
```

如果可以的話，Kyle 想回到當時告訴 JavaScript 的設計者，不要將 `''` 轉成 `0`，而是轉成 `NaN`。



看另外一個當初設計不是轉成 `NaN` 的例子：

```js
Number(true);   // 1
Number(false);  // 0


1 < 2 < 3; // true (but...)

// 是因為
(1 < 2) < 3;
(true) < 3;
1 < 3;

// ********

3 > 2 > 1; // false  (?!)

// 如同上面的運作
(3 > 2) > 1;
(true) > 1;
1 > 1;  // falses

```

