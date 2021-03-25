## SELECT文

テーブルからデータを取り出すときにはSELECT文を使う。「テーブルにあるデータから必要なものだけをSELECTする」。SELECT文で必要なデータを取り出すことを「問い合わせ」や「クエリ」と呼ぶ。

SELECT文例

```sql
SELECT 列名 FROM テーブル名;
```

- SELECTのあとにはテーブルから取り出したい列の名前を書く
- FROMのあとにはデータを取り出すテーブル名を書く

```sql
SELECT name FROM users;
```

すべての列を出力する`*`

```sql
SELECT * FROM users;
```
アスタリスクを使うと結果の並び順を指定することはできない。なのでRailsで`User.all`みたいに書くと並び順が保証されない。

### ASで列に別名をつけることができる

```sql
SELECT hoge AS name,
bar AS address
FROM users;
```

### DISTINCTで重複を避ける

```sql
SELECT DISTINCT name FROM users;
```

nameカラムの重複を除いたデータを取得する。
