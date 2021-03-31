# ORDER BY

- SQLは基本的に順序を保証しないので、順序をつけたい場合はORDER BY句を使って明示的に指定する
- Railsでは`User.all`などとしたとき、基本的には`order`をつけたほうがいい（伊藤さん）
- ORDER BY句は常にSELECT文の最後に書く
- ASC（Ascendent）
  - 昇順
  - 階段を昇っていくイメージ
  - 数値の小さいほうが上にくる
- DESC（descendent）
  - 降順
  - 階段の上から降りていく
  - 数値の高いほうが上にくる

DESC（数値の大きい順から並べる）

```sql
SELECT shohin_id, shohin_mei, hanbai_tanka
FROM Shohin
ORDER BY hanbai_tanka DESC;
```

ASC（数値の小さい順から並べる）

```sql
SELECT shohin_id, shohin_mei, hanbai_tanka
FROM Shohin
ORDER BY hanbai_tanka ASC;
```
