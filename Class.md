```js
class DERIVED_CLASS extends BASE_CONSTRUCTOR_VALUE {
  constructor() {
    super();
    // この super は DERIVED_CLASS.[[Prototype]] を指す。


    super.abcdef;
    super['abcdef'];
    // この super は DERIVED_CLASS.prototype.[[Prototype]] を指す。
    // オブジェクトのプロパティーアクセスと同じく super.abcdef は super['abcdef'] の簡略記法である。

    // super[propExpr] は
    // Reflect.get(Reflect.getPrototypeOf(DERIVED_CLASS.prototype), propExpr, this)
    // に置き換えることができる。

    // <例外>
    // super[propExpr](arg0, arg1, arg2, ..., argN) は
    // method = Reflect.get(Reflect.getPrototypeOf(DERIVED_CLASS.prototype), propExpr, this)
    // Reflect.apply(method, this, [arg0, arg1, arg2, ..., argN])
    // に置き換えることができる。
  }
}
```
