# Philosophy of Coercion


## Intentional Coercion

採取好的 coding style，接納強制轉型

You don't deal with these type conversion corner cases by avoiding coercions.

You have to adopt a coding style that makes your types and the values that are in those types plain and obvious, that's the only effective way to do this.

A quality JS program embraces coercions, making sure the types involved in every operation are clear. Thus, corner cases are safely managed.

JavaScript's dynamic typing is not a weakness, it's one of its strong qualities

反而，JavaScript 的弱型別特性才是最大的特色與優勢。（而不是如多數人因此詬病）
學習善用它，寫出高品質的程式。


## Culture of Learning

正向的學習文化與環境：
學習理解並善用工具，不要嘲笑新人愚蠢，或是認爲不需要追求更好的寫法，
讓原本沒注意到的人有機會學習，才能使開發環境更良善。

不管你是誰，在什麼位置，只管持續往前學習、成長

Now you learned better and they learned better.


## Code Communication Q&A

discusses code comments

好的程式碼是好的溝通，有些人說不需要註解，不過，並非註解就是不好的，
而是避免註解 what 或 how，而是註解 why

## Implicit Coercion

implicit (隱含的) 並非 magic 或 bad，而是 abstracted

So implicitness is not bad, it is the proper usage of obstruction. In other words, we want to hide key unnecessary details, why? Because that re-focuses the reader on the important stuff. We're not distracting them with the stuff that they don't need. We wanna focus them. We wanna increase the clarity of the code by re-focusing.

So some of the implicit nature of JavaScript's type system is sketchy, but some of it is quite useful. For example, the boxing. That's implicit, but also very useful, because the distraction of having to cast it into an object isn't, what I would argue in most cases, an unnecessary detail that the reader doesn't need.

JavaScript 學習門檻低，其中一點就是因為它設計得讓我們可以減少去處理那些不重要的細節
這是 JavaScript 的 DNA，若一昧避免所有可能的型別轉換，反而是背叛了它的原貌。


看幾個例子：
投影片 86.87


Really, the question is, is showing these extra details helpful to the reader or not? Sometimes yes, sometimes no.
Basically, I'm asking you to be critical, analytical thinkers, to be an engineer and not a code monkey, okay?

## Understanding Features

理解 JavaScript 的運作，而不是逃避學習

It is irresponsible(不負責任) to knowingly avoid usage of a feature that can improve code readability.

