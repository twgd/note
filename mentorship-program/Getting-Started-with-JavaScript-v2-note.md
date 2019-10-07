# Getting Started with JavaScript, v2 課程筆記

## 介紹一下這門課
線上課程連結：[Getting Started with JavaScript, v2](https://frontendmasters.com/courses/getting-started-javascript-v2/)

這是一堂適合沒有 JavaScript 開發經驗者的入門課程，又或者是想重頭理解 JavaScript 原貌的開發者。

課程講者是 [Kyle Simpson](https://github.com/getify)，也是知名系列書 [You Don't Know JS](https://github.com/getify/You-Dont-Know-JS) 的作者。這堂課的內容與 [You Don't Know JS: Up & Going](https://github.com/getify/You-Dont-Know-JS/blob/1st-ed/up%20&%20going/README.md#you-dont-know-js-up--going) 相呼應，對 JavaScript 的語法基礎及三大核心（Types / Coercion、Scope / Closures、this / Prototypes）做概略的導覽，將這門課程當作導讀再來閱讀書籍也是種不錯的學習模式。


------

因為下一堂課程 [Deep JavaScript Foundations, v3](https://frontendmasters.com/courses/deep-javascript-v3/) 才會對 JavaScript 的三大核心及語法做較深入的說明，因此較細節的課程筆記就留給下一堂課。這堂課的筆記主要紀錄一些我在課程中受到啟發的觀念及講者分享的 JavaScript 開發風格。


------

NOTE: Work in progress

.

.

.


## Types & Coercion
### Equality
== vs === It turns out that the difference between them is whether or not coercion is allowed.

## Scope
### Undefined vs Undeclared
undefined: is a variable that has been declared, but it doesn’t have a value. undeclared: is one that was never declared anywhere.


### Function Expressions
Function Expression: is a function that is assigned as a value somewhere.
You really should have all named function expressions, if possible. Their descriptive name tells us what they’re doing.

### Block Scoping with let
I like to still use a var at the function level. Because VAR is always gonna behave as if it belongs to the function, i like to put VARs at the function level and only use lets inside of blocks.
If it’s needed for a few lines, go ahead and open up a curly brace block, instead of just making those at the function level.

.

.

.

.

------

