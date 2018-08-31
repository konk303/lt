# Hashのkeyのstringはfreezeされる

## 経緯
axlsxを使ってて、`RuntimeError: can't modify frozen String`に[遭遇](https://github.com/r-n-i/code-rails/pull/3338/commits/5b043a3f68bdbc67cb1e2b08fa54ccc95e2bb13f)

`Array#group_by`して作ったhashのkeyをaxlsxに送ってる箇所。

## rubyの仕様

[Hash](http://miyamae.github.io/rubydoc-ja/2.4.0/#!/class/-hash.html)

> 破壊的操作によってキーとして与えたオブジェクトの内容が変化し、Object#hash の返す 値が変わるとハッシュから値が取り出せなくなりますから、 Array、Hash などのインスタンスはキーに向きません。Hash#rehash を参照。

**むしろこっち注意**

> ただし、 更新不可 (Object#frozen? が true) では無い文字列をキーとして与えた場合は、文字列をコピーし、コピーを更新不可に設定 (Object#freeze) してキーとして 使用します。この為、キーとして使われている文字列を更新しようとすると例外 RuntimeError が発生するので rehash を呼ぶ必要性は生じません。

## axlsx

- [github](https://github.com/randym/axlsx)
- [rubygems](https://rubygems.org/gems/axlsx/versions/2.0.1)

行儀が[悪かった](https://github.com/randym/axlsx/blob/776037c0fc799bb09da8c9ea47980bd3bf296874/lib/axlsx.rb#L134-L141)が、
既に[直ってた](https://github.com/randym/axlsx/pull/565)

[新コード](https://github.com/randym/axlsx/blob/master/lib/axlsx.rb#L133-L144)


ただしいつまでたっても正式なversionが出ない :sweat
