# 📘 SQL演習問題（第2章・第3章）

## 🔧 共通設定

- データベース名：`employee_db`  
- テーブル名：`employee`  
- カラム構成：

| カラム名       | データ型     | 説明                 |
|----------------|--------------|----------------------|
| employee_id    | INT          | 主キー               |
| name           | VARCHAR(50)  | 氏名（日本語）       |
| age            | INT          | 年齢                 |
| department     | VARCHAR(30)  | 部署（日本語）       |
| salary         | INT          | 月給（円）           |
| hire_date      | DATE         | 入社日               |

---

## 🧩 第2章：SQLの基礎（全13問）

---

### 問題1  
データベース `employee_db` を作成してください。

**模範解答**
```sql
CREATE DATABASE employee_db;
```

---

### 問題2  
作成したデータベース `employee_db` を使用してください。

**模範解答**
```sql
USE employee_db;
```

---

### 問題3  
`employee` テーブルを次の仕様で作成してください。

- `employee_id`: 主キー（整数）
- `name`: 50文字までの文字列
- `age`: 整数
- `department`: 30文字までの文字列
- `salary`: 整数
- `hire_date`: 日付

**模範解答**
```sql
CREATE TABLE employee (
  employee_id INT PRIMARY KEY,
  name VARCHAR(50),
  age INT,
  department VARCHAR(30),
  salary INT,
  hire_date DATE
);
```

---

### 問題4  
以下の10件のデータを `employee` テーブルに挿入してください。

| employee_id | name         | age | department | salary  | hire_date  |
|-------------|--------------|-----|------------|---------|------------|
| 1           | 田中 太郎    | 28  | 営業部     | 300000  | 2021-04-01 |
| 2           | 鈴木 花子    | 35  | 総務部     | 320000  | 2020-06-15 |
| 3           | 佐藤 健      | 40  | 開発部     | 400000  | 2018-10-10 |
| 4           | 山本 由美    | 25  | 営業部     | 280000  | 2022-01-20 |
| 5           | 中村 優      | 30  | 開発部     | 350000  | 2019-07-07 |
| 6           | 高橋 亮      | (NULL)    | 営業部     |  (NULL)        |  (NULL)           |
| 7           | 小林 舞      | 29  | 総務部     | 310000  | 2021-09-01 |
| 8           | 森 健太      | 45  | 開発部     | 420000  | 2015-03-10 |
| 9           | 藤井 明子    | 33  | 営業部     | 295000  | 2019-11-11 |
| 10          | 井上 大貴    | 31  | 開発部     | 360000  | 2020-02-28 |

**模範解答**
```sql
INSERT INTO employee VALUES
(1, '田中 太郎', 28, '営業部', 300000, '2021-04-01'),
(2, '鈴木 花子', 35, '総務部', 320000, '2020-06-15'),
(3, '佐藤 健', 40, '開発部', 400000, '2018-10-10'),
(4, '山本 由美', 25, '営業部', 280000, '2022-01-20'),
(5, '中村 優', 30, '開発部', 350000, '2019-07-07'),
(6, '高橋 亮', NULL, '営業部', NULL, NULL),
(7, '小林 舞', 29, '総務部', 310000, '2021-09-01'),
(8, '森 健太', 45, '開発部', 420000, '2015-03-10'),
(9, '藤井 明子', 33, '営業部', 295000, '2019-11-11'),
(10, '井上 大貴', 31, '開発部', 360000, '2020-02-28');
```

---

### 問題5  
`employee` テーブルのすべての行を表示してください。

**模範解答**
```sql
SELECT * FROM employee;
```

---

### 問題6  
`name` 列と `department` 列のみを表示してください。

**模範解答**
```sql
SELECT name, department FROM employee;
```

---

### 問題7  
`age` が 30 以下の社員を抽出してください。

**模範解答**
```sql
SELECT * FROM employee WHERE age <= 30;
```

---

### 問題8  
`salary` が 350000 円以上の社員を表示してください。

**模範解答**
```sql
SELECT * FROM employee WHERE salary >= 350000;
```

---

### 問題9  
`hire_date` が古い順に社員を並べてください。

**模範解答**
```sql
SELECT * FROM employee ORDER BY hire_date ASC;
```

---

### 問題10  
`salary` が高い順に並べ、上位5件のみ表示してください。

**模範解答**
```sql
SELECT TOP 5 * FROM employee ORDER BY salary DESC;
```

---

### 問題11  
`name` を「氏名」、`department` を「部署」として別名表示してください。

**模範解答**
```sql
SELECT name AS 氏名, department AS 部署 FROM employee;
```

---

### 問題12  
`age` に適したデータ型は何ですか？

**模範解答**
```
INT
```

---

### 問題13  
`hire_date` が NULL でない社員のみを表示してください。

**模範解答**
```sql
SELECT * FROM employee WHERE hire_date IS NOT NULL;
```

---

## 🧮 第3章：演算子（全9問）

---

### 問題14  
`salary` に 10000 円を加えた値を `raised_salary` として表示してください。

**模範解答**
```sql
SELECT name, salary, salary + 10000 AS raised_salary FROM employee;
```

---

### 問題15  
`age` が 29・30・31 歳の社員を表示してください。

**模範解答**
```sql
SELECT * FROM employee WHERE age IN (29, 30, 31);
```

---

### 問題16  
`age` が 30 以上かつ `salary` が 350000 円以上の社員を表示してください。

**模範解答**
```sql
SELECT * FROM employee WHERE age >= 30 AND salary >= 350000;
```

---

### 問題17  
`department` が 「営業部」または「総務部」の社員を表示してください。

**模範解答**
```sql
SELECT * FROM employee WHERE department = '営業部' OR department = '総務部';
```

---

### 問題18  
`department` が 「総務部」以外の社員を表示してください。

**模範解答**
```sql
SELECT * FROM employee WHERE department != '総務部';
```

---

### 問題19  
`salary` が 300000 円以上かつ 400000 円以下の社員を表示してください。

**模範解答**
```sql
SELECT * FROM employee WHERE salary BETWEEN 300000 AND 400000;
```

---

### 問題20  
`name` が「藤」で始まる社員を表示してください。

**模範解答**
```sql
SELECT * FROM employee WHERE name LIKE '藤%';
```

---

### 問題21  
`age` が NULL の社員を表示してください。

**模範解答**
```sql
SELECT * FROM employee WHERE age IS NULL;
```

---

