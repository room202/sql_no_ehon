# 第4章　関数

```sql
USE db_ehon;

-- tbl_snum
CREATE TABLE tbl_snum (
    atai FLOAT
);

INSERT INTO tbl_snum (atai) VALUES (1.248);
INSERT INTO tbl_snum (atai) VALUES (29.5);
INSERT INTO tbl_snum (atai) VALUES (105.05);

-- tbl_stdname
CREATE TABLE tbl_stdname (
    sname VARCHAR(20),
    fname VARCHAR(20)
);

INSERT INTO tbl_stdname (sname,fname) VALUES ('AIZAWA', 'namiko');
INSERT INTO tbl_stdname (sname,fname) VALUES ('YAMAMOTO', 'tatsuki');
INSERT INTO tbl_stdname (sname,fname) VALUES ('SAWAGUCHI', 'aki');
INSERT INTO tbl_stdname (sname,fname) VALUES ('KOBAYASHI', 'maiko');

-- tbl_pet
CREATE TABLE tbl_pet (
    pname VARCHAR(20)
);

INSERT INTO tbl_pet (pname) VALUES (' CHIBI ');
INSERT INTO tbl_pet (pname) VALUES (' ALEX ');
INSERT INTO tbl_pet (pname) VALUES (' RAN ');
INSERT INTO tbl_pet (pname) VALUES (' SHAM ');

-- tbl_datelist
CREATE TABLE tbl_datelist (
    no INT,
    date1 DATETIME,
    date2 DATETIME
);

INSERT INTO tbl_datelist (no, date1, date2) VALUES (1,'2018-04-13','2018-07-03');
INSERT INTO tbl_datelist (no, date1, date2) VALUES (2,'2018-10-11','2019-01-24');

-- tbl_game
CREATE TABLE tbl_game (
    name VARCHAR(20),
    score INT
);

INSERT INTO tbl_game (name, score) VALUES ('koba', 125);
INSERT INTO tbl_game (name, score) VALUES ('tone', 140);
INSERT INTO tbl_game (name, score) VALUES ('takane', 110);
INSERT INTO tbl_game (name, score) VALUES ('koba', 75);
INSERT INTO tbl_game (name, score) VALUES ('takane', 160);
INSERT INTO tbl_game (name, score) VALUES ('tone', 98);
INSERT INTO tbl_game (name, score) VALUES ('takane', 90);
INSERT INTO tbl_game (name, score) VALUES ('koba', 64);
INSERT INTO tbl_game (name, score) VALUES ('tone', 105);

-- tbl_schedule
CREATE TABLE tbl_schedule (
    time VARCHAR(30)
);

INSERT INTO tbl_schedule(time) VALUES ('12 29 2003 8:50AM');
INSERT INTO tbl_schedule(time) VALUES ('02 06 2004 12:46AM');
INSERT INTO tbl_schedule(time) VALUES ('06 30 2005 1:29PM');
```

## 第４章はここがkey

## 関数とは

## 数値関数(1)

### CEILING関数、CEIL関数

小数点以下切り上げ

```sql
SELECT CEILING(55.44);
-- 結果
-- 56
```

### FLOOR関数

小数点以下切り捨て

```sql
SELECT FLOOR(2.58);
-- 結果
-- 2
```

```sql
USE db_ehon;

SELECT
    atai,
    CEILING(atai) AS kekka1,
    FLOOR(atai) AS kekka2
FROM
    tbl_snum;
```

## 数値関数(2)

### RAND関数

0以上1.0未満の範囲の乱数を取得する

```sql
SELECT RAND(6);
```

```sql
SELECT RAND();
SELECT RAND();
SELECT RAND(7);
SELECT RAND(7);
```

### その他の数値関数

※ ROUNDだけを紹介

```sql
SELECT ROUND(3.4, 0);
-- 3
SELECT ROUND(3.5, 0);
-- 4
```

#### 桁数の指定

```sql
SELECT ROUND(123.456789, 3);
-- 123.457
SELECT ROUND(123.456789, 2);
-- 123.46
SELECT ROUND(123.456789, 1);
-- 123.5
SELECT ROUND(123.456789, 0);
-- 123
SELECT ROUND(123.456789, -1);
-- 120
SELECT ROUND(123.456789, -2);
-- 100
SELECT ROUND(123.456789, -3);
-- 0
```

## 文字列関数(1)

### LEN関数、LENGTH関数

```sql
SELECT LENGTH('しおり');
-- 9 (UTF-8で3文字)
```

```sql
SELECT LENGTH('サクラ　サク');
SELECT sname, LENGTH(sname) AS kekka FROM tbl_stdname;
```

### SUBSTRING、SUBSTR関数

```sql
SELECT SUBSTRING('えほん', 2, 2);
-- ほん
```

```sql
SELECT fname, SUBSTRING(fname, 2, 2) AS kekka FROM tbl_stdname;
```

## 文字列関数(2)

### LTRIM関数、RTRIM関数

```sql
SELECT LTRIM('  ABC');
-- ABC
SELECT RTRIM('ABC  ');
-- ABC
SELECT LTRIM(RTRIM('   ABC  '));
-- ABC
SELECT TRIM('   ABC  ');
-- ABC
```

```sql
SELECT
    CONCAT('***', pname, '***') AS pname,
    CONCAT('***', LTRIM(pname), '***') AS hidari,
    CONCAT('***', RTRIM(pname), '***') AS migi
FROM
    tbl_pet;
```

### UPPER関数、LOWER関数

```sql
SELECT UPPER('sqlの絵本');
-- SQLの絵本

SELECT LOWER('SQLの絵本');
-- sqlの絵本
```

```sql
SELECT sname, LOWER(sname) AS komoji FROM tbl_stdname;
SELECT fname, UPPER(sname) AS oomoji FROM tbl_stdname;
```

## 日付関数(1)

### 現在の日時を取得する

```sql
-- MySQL, Oracle
SELECT SYSDATE();

-- SQL Server
-- SELECT GETDATE();

-- PostgreSQL
-- SELECT NOW();
```

### 日付データから、日、月、年を取得する

```sql
CREATE TABLE tbl_date (jikoku DATETIME);

INSERT INTO tbl_date (jikoku) VALUES (SYSDATE());

SELECT * FROM tbl_date;
SELECT DAY(jikoku) FROM tbl_date;

SELECT
    jikoku,
    YEAR(jikoku) AS '年',
    MONTH(jikoku) AS '月',
    DAY(jikoku) AS '日',
    HOUR(jikoku) AS '時',
    MINUTE(jikoku) AS '分',
    SECOND(jikoku) AS '秒'
FROM
    tbl_date;
```

## 日付関数(2)

### 日数、時間数を加算する

```sql
-- MySQL
-- +1日
SELECT DATE_ADD('2025-08-31', INTERVAL 1 DAY);
-- +1時間
SELECT DATE_ADD('2025-08-31 09:00:00', INTERVAL 1 HOUR);
-- +1ヶ月
SELECT DATE_ADD('2025-08-31', INTERVAL 1 MONTH);
-- +1年
SELECT DATE_ADD('2025-08-31', INTERVAL 1 YEAR);
```

### 日付の差を取得する

```sql
SELECT DATEDIFF('2025-09-10', '2025-08-29');
-- 12
```

```sql
SELECT DATE_ADD(date1, INTERVAL 6 MONTH) FROM tbl_datelist WHERE no = 1;
SELECT DATEDIFF(date2, date1) FROM tbl_datelist WHERE no = 2;
SELECT DATEDIFF(SYSDATE(), '2019-01-01');
SELECT DATEDIFF('2019-01-01', SYSDATE());
```

## 集約関数(1)

### 主な集約関数

```sql
SELECT
    AVG(score) AS average,
    SUM(score) AS total_score,
    COUNT(name) AS game
FROM
    tbl_game;
```

```sql
SELECT COUNT(DISTINCT name) as member FROM tbl_game;
```

## 集約関数(2)

### MAX関数、MIN関数

### グループ単位で処理を行う

```sql
SELECT
    name,
    MAX(score) AS high,
    MIN(score) AS low
FROM
    tbl_game
GROUP BY
    name;
```

### 集約関数の結果を条件にしてデータを取り出す

```sql
SELECT
    price,
    COUNT(title)
FROM
    tbl_ehon
GROUP BY
    price
HAVING
    COUNT(title) = 1;
```

```sql
SELECT
    name,
    SUM(score) AS over300
FROM
    tbl_game
GROUP BY
    name
HAVING
    (SUM(score) >= 300);
```

## 変換関数

### CAST関数

#### CAST関数で使用できるデータ型一覧（MySQL）

| 型カテゴリ  | 型名（CAST で使用可）                       | 補足・説明                         |
| ------ | ----------------------------------- | ----------------------------- |
| 数値型    | `SIGNED`                            | 符号付き整数（例: `INT` 相当）           |
|        | `UNSIGNED`                          | 符号なし整数                        |
|        | `DECIMAL[(M,D)]`                    | 固定小数点数                        |
|        | `NUMERIC[(M,D)]`                    | `DECIMAL` の別名（同義）             |
|        | `FLOAT`                             | 浮動小数点数                        |
|        | `DOUBLE`                            | 倍精度浮動小数点数                     |
| 文字列型   | `CHAR` または `CHAR(N)`                | 文字列型                          |
|        | `BINARY` または `BINARY(N)`            | バイナリデータ型                      |
| 日付・時刻型 | `DATE`                              | 日付（YYYY-MM-DD）                |
|        | `DATETIME`                          | 日付＋時刻                         |
|        | `TIME`                              | 時刻のみ                          |
|        | `SIGNED INTEGER`（非公式で `INTEGER` も可） | `INT`のキャストにも使用可（推奨は `SIGNED`） |


```sql
SELECT CAST(0.245 AS CHAR);
-- '0.245' (CHAR)

-- SQL Server
-- SELECT CAST(0.245 AS VARCHAR);

SELECT CAST('2025-09-01' AS DATETIME);
-- '2025-09-01 00:00:00' (DATETIME)
``` 

```sql
SELECT
    time AS mojiretsu,
    STR_TO_DATE(time, '%m %d %Y %h:%i%p') AS hizuke1,
    CAST(time AS DATETIME) AS hizuke2 -- MySQLだとNULLになる
FROM
    tbl_schedule;
```

## COLUMMN : ～ RDBMS 固有の関数 ～

### DATENAME関数

スキップ

### LAST_DAY関数

```sql
SELECT LAST_DAY('2025-09-01');
SELECT LAST_DAY('2025-10-01');
SELECT LAST_DAY('2025-11-01');
SELECT LAST_DAY('2025-12-01');
```

### POSITION関数

スキップ
