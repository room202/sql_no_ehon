## 演習01: 年収の算出

**問題**

従業員の月給（salary）を12倍し、年収として表示してください。

**結果（例）**

| name | 年収 |
| --- | --- |
| 佐藤健 | 3840000 |
| 鈴木花子 | 5400000 |
| 高橋一郎 | 6000000 |
| 山田太郎 | 3480000 |
| 佐藤美咲 | 4560000 |
| 村田博 | 5160000 |

**参考回答**

```sql
SELECT name, salary * 12 AS 年収 FROM employees;
```

---

## 演習02: 日給の算出

**問題**

従業員の月給（salary）を30で割り、1日あたりの日給として表示してください。

**結果（例）**

| name | 日給 | 日給切り捨て |
| --- | --- | --- |
| 佐藤健 | 10666.6667 | 10666 |
| 鈴木花子 | 15000.0000 | 15000 |
| 高橋一郎 | 16666.6667 | 16666 |
| 山田太郎 | 9666.6667 | 9666 |
| 佐藤美咲 | 12666.6667 | 12666 |
| 村田博 | 14333.3333 | 14333 |

**参考回答**

```sql
SELECT name, salary / 30 AS 日給, FLOOR(salary / 30) AS 日給切り捨て FROM employees;
```

---

## 演習03: 30歳以上の従業員抽出

**問題**

年齢が30歳以上の従業員を抽出してください。

**結果（例）**

| name | age |
| --- | --- |
| 鈴木花子 | 35 |
| 高橋一郎 | 41 |
| 佐藤美咲 | 31 |

**参考回答**

```sql
SELECT name, age FROM employees WHERE age >= 30;
```

---

## 演習04: 開発部の従業員抽出

**問題**

部署が「開発」の従業員を抽出してください。

**結果（例）**

| name | department |
| --- | --- |
| 鈴木花子 | 開発 |
| 高橋一郎 | 開発 |
| 村田博 | 開発 |

**参考回答**

```sql
SELECT name, department FROM employees WHERE department = '開発';
```

---

## 演習05: 営業部以外の抽出

**問題**

部署が「営業」ではない従業員を抽出してください。

**結果（例）**

| name | department |
| --- | --- |
| 鈴木花子 | 開発 |
| 高橋一郎 | 開発 |
| 山田太郎 | 総務 |
| 村田博 | 開発 |

**参考回答**

```sql
SELECT name, department FROM employees WHERE department <> '営業';
```

---

## 演習06: 条件複合（AND）

**問題**

30歳以上かつ給与が40万円以上の従業員を抽出してください。

**結果（例）**

| name | age | salary |
| --- | --- | --- |
| 鈴木花子 | 35 | 450000 |
| 高橋一郎 | 41 | 500000 |

**参考回答**

```sql
SELECT name, age, salary FROM employees WHERE age >= 30 AND salary >= 400000;
```

---

## 演習07: 条件複合（OR）

**問題**

年齢が25歳以下または給与が50万円以上の従業員を抽出してください。

**結果（例）**

| name | age | salary |
| --- | --- | --- |
| 高橋一郎 | 41 | 500000 |
| 山田太郎 | 24 | 290000 |

**参考回答**

```sql
SELECT name, age, salary FROM employees WHERE age <= 25 OR salary >= 500000;
```

---

## 演習08: NOT条件の使用

**問題**

部署が「総務」以外の従業員を抽出してください。

**結果（例）**

| name | department |
| --- | --- |
| 佐藤健 | 営業 |
| 鈴木花子 | 開発 |
| 高橋一郎 | 開発 |
| 佐藤美咲 | 営業 |
| 村田博 | 開発 |

**参考回答**

```sql
SELECT name, department FROM employees WHERE NOT department = '総務';
```

---

## 演習09: ANDとORの組み合わせ

**問題**

「営業部かつ30歳以上」または「開発部かつ給与45万円以上」の従業員を抽出してください。

**結果（例）**

| name | department | age | salary |
| --- | --- | --- | --- |
| 鈴木花子 | 開発 | 35 | 450000 |
| 高橋一郎 | 開発 | 41 | 500000 |
| 佐藤美咲 | 営業 | 31 | 380000 |

**参考回答**

```sql

SELECT * FROM employees
WHERE (department = '営業' AND age >= 30)
   OR (department = '開発' AND salary >= 450000);
```

---

## 演習10: 算術と論理条件の複合

**問題**

月給×12が500万円以上で、30歳未満の従業員を抽出してください。

**結果（例）**

| name | age | department | salary | 年収 |
| --- | --- | --- | --- | --- |
| 村田博 | 29 | 開発 | 430000 | 5160000 |

**参考回答**

```sql
SELECT * FROM employees
WHERE salary * 12 >= 5000000 AND age < 30;
```

---

## 演習11: 名前の前方一致検索

**問題**

名前が「佐藤」で始まる従業員を抽出してください。

**結果（例）**

name

---

佐藤健

---

佐藤美咲

---

**参考回答**

```sql
SELECT name FROM employees WHERE name LIKE '佐藤%';
```

---

## 演習12: 名前の部分一致検索

**問題**

名前に「郎」が含まれる従業員を抽出してください。

**結果（例）**

name

---

高橋一郎

---

山田太郎

---

**参考回答**

```sql
SELECT name FROM employees WHERE name LIKE '%郎%';
```

---

## 演習13: 範囲指定（BETWEEN）

**問題**

給与が35万円以上45万円以下の従業員を抽出してください。

**結果（例）**

| name | salary |
| --- | --- |
| 鈴木花子 | 450000 |
| 佐藤美咲 | 380000 |
| 村田博 | 430000 |

**参考回答**

```sql
SELECT name, salary FROM employees
WHERE salary BETWEEN 350000 AND 450000;
```

---

## 演習14: 複数値の比較（IN）

**問題**

部署が「営業」または「総務」の従業員を抽出してください。

**結果（例）**

| name | department |
| --- | --- |
| 佐藤健 | 営業 |
| 山田太郎 | 総務 |
| 佐藤美咲 | 営業 |

**参考回答**

```sql
SELECT name, department FROM employees
WHERE department IN ('営業', '総務');
```

---

## 演習15: NULL値の確認（IS NULL）

**問題**

メールアドレス（email）が未登録（NULL）の従業員を抽出してください。

**結果（例）**

| name | email |
| --- | --- |
| 鈴木花子 | NULL |
| 山田太郎 | NULL |

**参考回答**

```sql
SELECT name, email FROM employees WHERE email IS NULL;
```
