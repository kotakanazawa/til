## 何らかの条件に合う行だけを選択するwhere

```sql
SELECT 列名 FROM テーブル名 WHERE 条件式;
```

WHEREは必ずFROMの直後に書くこと。エラーになる。

例

```sql
SELECT last_name FROM users WHERE last_name = 'yamada';
```

