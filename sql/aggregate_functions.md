## 集約関数 Aggregate Functions

練習用サイト：[SQLZOO](https://sqlzoo.net/)

SQLの集計用の関数。集計用の関数を「集約関数」や「集合関数」と呼ぶ。代表的なのは以下5つ。

- COUNT：テーブル全体の行数を合計する
- SUM：テーブルの数値列のデータを合計する
- AVG：テーブルの数値列のデータを平均する
- MAX：テーブルの任意の列のデータの最大値を取得する
- MIN：テーブルの任意の列のデータの最小値を取得する

集約関数の特徴

- すべての集約関数は、列名を引数にとった場合、計算前にNULLを除外する

## COUNT

```sql
SELECT COUNT(*)
FROM world;
```

Result:195

`COUNT`には引数がついている。`*`はすべての列を意味する。

```sql
SELECT COUNT(name) FROM users;
```

注意：COUNT関数は、引数が`＊`だとNULLも計算に含む（ただし計算には含めない）。nameなど列名を引数に入れたらNULLは除外する

## SUM

```sql
SELECT SUM(population)
FROM world
WHERE continent = 'europe';
```

Result:610261850

## AVG

```sql
SELECT AVG(population)
FROM world
WHERE continent = 'europe';
```

Result:13869587.5

## MAX, MIN

```sql
SELECT MAX(population) AS 'MAX', MIN(population) AS 'MIN'
FROM world
WHERE continent = 'europe';
```

|MAX|MIN|
|---|---|
| 80716000 | 839 |

順序がつけられるデータなら適用できるので、日付型のデータにも使える。

## 重複を避ける

```sql
SELECT COUNT(DISTINCT category)
FROM products
```

必ずカッコの中に`DISTINCT`を書く。


