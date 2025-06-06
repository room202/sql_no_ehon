# 📘 2章 SQLの基礎 演習問題

---

## 問題①：この演習問題用のデータベース作成

**指示：**  
以下のSQLを使って、演習用のデータベース `training_db` を作成し、使用するデータベースを切り替えなさい。

```sql
CREATE DATABASE training_db;

USE training_db;
```

---

## 問題②：社員テーブルの作成

**指示：**  
以下の要件に従って `employees` テーブルを作成しなさい。

- `id`：INT型、主キー  
- `name`：VARCHAR(30)、NULL不可  
- `email`：VARCHAR(100)、一意（UNIQUE）

```sql
CREATE TABLE employees (
  id INT PRIMARY KEY,
  name VARCHAR(30) NOT NULL,
  email VARCHAR(100) UNIQUE
);
```

---

## 問題③：社員データの登録

**指示：**  
以下の社員情報を `employees` テーブルに追加しなさい。

| id | name     | email                    |
|----|----------|--------------------------|
| 1  | 田中一郎 | ichiro.tanaka@example.com |
| 2  | 山本花子 | hanako.yamamoto@example.com |

```sql
INSERT INTO employees (id, name, email)
VALUES
  (1, '田中一郎', 'ichiro.tanaka@example.com'),
  (2, '山本花子', 'hanako.yamamoto@example.com');
```

---

## 問題④：特定の社員を検索

**指示：**  
名前が「田中一郎」の社員情報を検索しなさい。

```sql
SELECT * FROM employees
WHERE name = '田中一郎';
```

---

## 問題⑤：メールアドレス順に並べて上位1件を取得

**指示：**  
`employees` テーブルの全データをメールアドレス順に並べ、最初の1件だけを表示しなさい。

```sql
SELECT * FROM employees
ORDER BY email
LIMIT 1;
```

---

## 問題⑥：画像データの登録用テーブル作成（BLOB使用）

**指示：**  
画像ファイルを保存するための `photos` テーブルを作成しなさい。

- `photo_id`：INT型、主キー  
- `title`：VARCHAR(50)、画像のタイトル（例：「社員証」など）  
- `image_data`：BLOB型（画像データ）

```sql
CREATE TABLE photos (
  photo_id INT PRIMARY KEY,
  title VARCHAR(50),
  image_data BLOB
);
```

> ※この段階では画像ファイルの挿入は行わず、テーブル作成のみとします。
