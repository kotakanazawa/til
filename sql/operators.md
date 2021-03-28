# 演算子(operators)

- 算術演算子
  - 四則演算
- 比較演算子
  - 両辺の列や値を比較する記号
  - `=`（イコール）
  - `<>`（不等号）
- `>=`や`<=`を検索条件とするとき、不等号は必ず左側、イコールを右側にする
- SQLでは通常の計算式と同じように（）を使うことができる
- カッコの中にある計算式の優先順位が上がり、先に計算される
- NULLを含んだ計算はすべてNULLになる
  - 5 + NULL -> NULL
  - 10 - NULL -> NULL

比較演算子はWHERE句を使って書く

```sql
SELECT name FROM users WHERE age <> 20;
```

↑ageが20ではない行を選択している。

日付では「〜より小さい」が「〜より前」になる。

```sql
SELECT name FROM users WHERE birthday < '2010-10-10';
```

2010年10月10日よりbirthdayが前のnameをusersテーブルから取得している。

## NULLの行を選択する

`IS NULL`を使う。

```sql
SELECT name FROM users WHERE age IS NULL;
```

NULLではない行を選択したい場合は`IS NOT NULL`が使える。

```sql
SELECT name FROM users WHERE age IS NOT NULL;
```

## 論理演算子

- NOT
- AND
  - ORよりANDのほうが優先される
- OR
- TRUE/FALSE

`AND`: 両辺の検索条件が両方とも成り立つときに

```sql
SELECT name
FROM users
WHERE age = 20
AND name = hoge;
```

`OR`:どちらかが成り立つときに

```sql
SELECT name
FROM users
WHERE age = 20
OR name = hoge;
```

ANDよりORを優先させたいとき`()`を使う。

```sql
SELECT name
FROM users
WHERE country = 'japan'
AND (    created_at = '2020-02-01'
      OR created_at = '2020-02-10')
```

国がjapanで、作成日が'2020-02-01'もしくは'2020-02-10'のnameを取得する。

もしこれが、こうだと。

```sql
SELECT name
FROM users
WHERE country = 'japan'
AND created_at = '2020-02-01'
OR created_at = '2020-02-10'
```

ANDのほうが優先されるため、

「国がjapanで、作成日が'2020-02-01'」もしくは、「作成日が'2020-02-10'のname」という意味になってしまう。


