# reactのcomponent分離 (とobjectのマージ)



[これ](https://github.com/r-n-i/code-rails/pull/3316/files)で、 `container/presentationalにcomponentを分割` を試してみた。

## Presentational and Container Components

[この記事](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0)

### Container Component
1. **動作** を管理
1. `データ` と `振る舞い` を一括管理
1. childrenとしてpresentationalなcomponentを抱える
   - `データ(props)` と `振る舞い (callback)`を送り込む
1. `render` は、ほぼほぼchildren登録のみが目的

### Presentational Component
1. **見栄え** を管理
1. state **使わない**
1. ので、function でほぼほぼイケる

## reduxでは

自分で書くのは、[ほぼほぼpresentationalのみ](https://redux.js.org/basics/usagewithreact#presentational-and-container-components)

1. stateは `Store` を使用
1. `振る舞い` は `reducer` を使用
   - `reducer` == `現在のstateと新しく起こったactionを引数に、新しいstateを返すcallback`

## 雑談: objectのマージ

storeにしまうものを増やすと、階層管理したくなってくる

基本 [`Object.assign`](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)を使う
[`Ojbect Spread Operator`](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/Spread_syntax)使えばちょっとだけ気持ち良い

reduxでも[派手に使う](https://redux.js.org/recipes/usingobjectspreadoperator)

https://redux.js.org/recipes/structuringreducers/immutableupdatepatterns

**注** どちらも `shallow copy` (なのでかえって良い)

1. [example: setState](https://github.com/r-n-i/code-rails/blob/201808301335/app/assets/javascripts/components/PhoneNumbersConditionInput.jsx#L19-L23)
1. [example: reducer](https://github.com/r-n-i/mycomment-rails/tree/master/client/app/bundles/AdminApp/reducers)
