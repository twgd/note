read the spec

https://www.ecma-international.org/ecma-262/9.0/index.html


------


### Types

``` js

var v = null;
typeof v;               // "object" 注意使用 typeof null 時的 bug

v = function () {};
typeof v;               // "function"

v = [1, 2, 3];
typeof v;               // "object" 可以用 Array.isArray()

```




------



### BigInt



------



### Kinds of Emptiness



------



### Nan & isNan

1. nan is not equal to itself
```js

var myCatsAge = Number('n/a');
myCatsAge === myCatsAge;            // false

```

2. isNaN() 會先強制轉型 namber 成 nan 才做檢查
```js
isNaN("my son's age");              // true

Number.isNaN("my son's age");       // false

```

3. NaN: Invalid Number



------



### Negative Zero

#### 居然有 -0 ?!

在數學世界裡沒有 `-0`

但在程式世界裡，是存在的，就在 IEEE 754，如同 `Nan` 也存在在 IEEE 754。

IEEE 54

#### 0 與 -0 傻傻分不清楚

早期，JavaScript 以為 JavaScript 開發者不需要 `-0`，所以他們花了很長一段時間假裝 `-0` 不存在，造成很多怪異的現象，例如：

```js
var trendRate = -0;
trendRate === -0; // true

// 若試著轉成字串呢？
trendRate.toString(); // '0'
trendRate === 0; // true
// 再看看以下
trendRate < 0; // false
trendRate > 0; // false
```

他們認為開發者會以為將 `-0` 字串化得到 `'-0'` 是個 bug


    It felt like that would look to the end user like a bug, and JavaScript would get blamed. I think in retrospect, languages should do the correct thing and it's on developers to do something that's reasonable to users. Languages should not step in and try to second guess their developers.

    And there's a bunch of the historical weirdness in JavaScript where they tried for various reasons to be more palatable. We get automatic semi colon insertion and a whole, whole host of other things where the language trying to out smart the developer. And it turns out don't out smart the developer.

    Just let them do what they can with the sensible reasonable coherent set of tools, okay? 


JavaScript 欺騙了我們！

#### 那要如何判斷到底是 0 或是 -0 呢？

有很長一段時間，我們可以取得 `-0`，但我們無法知道我們是否有 `-0`，直到 ES6 的 `Object.is`:


```js
// 如何判斷 -0
Object.is(trendRate, -0);
Object.is(trendRate, 0);
```

#### 真的有人在乎 0 與 -0 的差異嗎？應用在哪裡？

正負號的使用情境，代表方向

`Math.sign()` 告訴我們有沒有 - 號

```js

Math.sign(3);   // 1
Math.sign(-3);  // -1
Math.sign(0);   // 0
Math.sign(-0);  // -0
```
`0` 與 `-0` 居然不是返回 1 與 -1

因此我們可以做一個 function 來修正

```js
// "fix" Math.sign(..)

function sign(v) {
    return v !== 0 ? Math.sign(v) : Object.is(v, -0) ? -1 : 1;
}

sign(3);  // 1
sign(-3); // -1
sign(0);  // 1
sign(-0); // -1
```

    對於 `Math.sign(-0)` 傳出的值有很多討論，但 Kyle 認為不是那麼實用
    There's some reason for the -0 thing in their return value, but I don't think it's very useful.

對於數字的方向性，常見的例子用在股市追蹤上，我們可以透過是否有負號得知是否正在上漲或是下跌。

```js
function formatTrend(trendRate) {
    var direction = 
        (trendRate < 0 || Object.is(trendRate, -0)) ? '▼' : '▲';
    return `${direction} ${Math.abs(trendRate)}`;
}

formatTrend(-3);   // "▼ 3"
formatTrend(3);    // "▲ 3"
formatTrend(-0);   // "▼ 0"
formatTrend(0);    // "▲ 0"
```

    Okay, so those special values, they're gonna occur in our programs, and having an acute awareness of types and the values that can exist in our programs.
    They're gonna help us not only avoid bugs, but also make better usage of our tool. Not only just be able to do something, but maybe do something more semantically, maybe make something that makes our code more readable or more understandable.



------



### Fundamental Objects

a.k.a Built-in Objects
a.k.a Native Functions


Use new:
- Object()
- Array()
- Function()
- Date()
- RegExp()
- Error()

Don't use new:
- String()
- Number()
- Boolean()

    They can be used with new to construct the objects of this form. You should absolutely never do that. You should use them only as functions, not as constructors.

```js
var yesterday = new Date('March 6, 2019');
yesterday.toUTCString();  // "Tue, 05 Mar 2019 16:00:00 GMT"

var myGPA = String(transcript.gpa);
```
