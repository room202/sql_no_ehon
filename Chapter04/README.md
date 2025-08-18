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
