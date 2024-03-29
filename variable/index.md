# 変数

Erlangにおいて、変数は大文字、もしくは`_`で始める必要がある。`var`や`let`といったキーワードは使用しない。

```erlang
main() ->
  Num = 1,
  io:format("Num is ~p ~n", [Num]).
  %%=> NUm is 1
```

小文字を利用しようとしてもエラーになる。

```erlang
%  Warning: no clause will ever match
%    |   num = 1.
%    |   ^
```

単一代入変数であり、束縛された変数は値を書き換えることはできない。

```erlang
main() ->
  Num = 1,

  Num = 2,
  % main.erl:10:3: Warning: no clause will ever match
  % main.erl:10:3: Warning: this clause cannot match because its guard evaluates to 'false'

  io:format("Num is ~p ~n", [Num]).
  %%=> Num is 1
  % exception error: no match of right hand side value 2
```

束縛されていない変数を**未束縛変数**、もしくは**自由変数**と呼ぶ。

## パターンマッチング

他の言語では「代入」とされる`=`は、Erlangでは**パターンマッチ**を行っているということができる。つまり、右辺を評価して左辺と一致するかを調べている。

```erlang
main() ->
  Num = 1,
  % 右辺と左辺が等しいのでパターンマッチの結果はok
  io:format("~p ~n", [Num = 1]).
  %=> 1
```

左辺が未束縛変数であれば、右辺と同じにする、という処理がされる。

http://erlangworld.web.fc2.com/first_step/valiable.html

http://www.nct9.ne.jp/m_hiroi/func/abcerl01.html

https://atmarkit.itmedia.co.jp/ait/articles/1608/30/news021.html
