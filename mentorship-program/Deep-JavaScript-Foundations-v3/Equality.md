# Equality

## Double & Triple Equals

以往常常聽到對於 `==` 及 `===` 的差別為：

- `==` 檢查值，不檢查型別
- `===` 檢查值與型別

但閱讀 Spec. 會發現並不是這麼回事

> Spec. 7.2.14 Abstract Equality Comparison

由 Spec. 中得知，當 type 一樣時，`==` 等同於 `===`
