# 第5章　基本的なデータ操作

## この章で使うテーブル

```sql
USE db_ehon;

-- tbl_subjects
CREATE TABLE tbl_subjects (
    id INT PRIMARY KEY,
    name VARCHAR(20),
    math INT,
    english INT
);

-- tbl_employee
CREATE TABLE tbl_employee (
    section VARCHAR(10),
    name VARCHAR(10)
);

INSERT INTO tbl_employee (section, name) VALUES ('総務部', '高尾');
INSERT INTO tbl_employee (section, name) VALUES ('人事部', '宮坂');
INSERT INTO tbl_employee (section, name) VALUES ('経理部', '船山');
INSERT INTO tbl_employee (section, name) VALUES ('人事部', '柏松');
INSERT INTO tbl_employee (section, name) VALUES ('社長室', '石川');
INSERT INTO tbl_employee (section, name) VALUES ('経理部', '西島');
INSERT INTO tbl_employee (section, name) VALUES ('人事部', '牟田');

-- tbl_jinji
CREATE TABLE tbl_jinji(
    name VARCHAR(10)
);

-- tbl_shopping
CREATE TABLE tbl_shopping (
    priority INT,
    material VARCHAR(20),
    num INT
);

INSERT INTO tbl_shopping VALUES (1, 'のこぎり', 1);
INSERT INTO tbl_shopping VALUES (2, 'くぎ', 30);
INSERT INTO tbl_shopping VALUES (3, '紙やすり', 5);
INSERT INTO tbl_shopping VALUES (4, 'ベニヤ板', 1);

-- tbl_title
CREATE TABLE tbl_title (
    code INT PRIMARY KEY,
    title VARCHAR(40)
);

INSERT INTO tbl_title VALUES (1111, 'しおりとシオリ');
INSERT INTO tbl_title VALUES (2222, 'しおりをめぐる冒険');
INSERT INTO tbl_title VALUES (3333, 'SQLをわしづかみ');

-- tbl_novel
CREATE TABLE tbl_novel (
    code INT PRIMARY KEY,
    title VARCHAR(40),
    price INT
);

INSERT INTO tbl_novel VALUES (1111, 'しおりとシオリ', 580);
INSERT INTO tbl_novel VALUES (2222, 'しおりをめぐる冒険', 680);
INSERT INTO tbl_novel VALUES (3333, 'SQLをわしづかみ', 430);
INSERT INTO tbl_novel VALUES (4444, 'しおりパパの贈り物', 980);

-- tbl_results
CREATE TABLE tbl_results (
    id INT PRIMARY KEY,
    team VARCHAR(1),
    name VARCHAR(10),
    point1 INT,
    point2 INT
);

INSERT INTO tbl_results VALUES (1, 'C', '沢田', 120, 105);
INSERT INTO tbl_results VALUES (2, 'A', '山本', 150, 130);
INSERT INTO tbl_results VALUES (3, 'B', '田代', 105, 98);
INSERT INTO tbl_results VALUES (4, 'A', '藤田', 170, 153);
INSERT INTO tbl_results VALUES (5, 'C', '佐藤', 147, 151);
INSERT INTO tbl_results VALUES (6, 'B', '長島', 130, 125);

-- tbl_advance
CREATE TABLE tbl_advance (
    no INT PRIMARY KEY,
    team VARCHAR(1),
    name VARCHAR(10),
    point1 INT,
    point2 INT
);

-- tbl_allowance
CREATE TABLE tbl_allowance (
    no INT PRIMARY KEY,
    name VARCHAR(10),
    overtime INT,
    travel INT,
    total INT
);

INSERT INTO tbl_allowance VALUES (1, '高根沢', 35000, 18000, NULL);
INSERT INTO tbl_allowance VALUES (2, '藤本', 45000, 23600, NULL);
INSERT INTO tbl_allowance VALUES (3, '土谷', 56000, 32000, NULL);
INSERT INTO tbl_allowance VALUES (4, '小林', 21000, 14500, NULL);
```

## 第５章はここがkey

## INSERT文(1)

### 列名を省略して登録する

```sql
-- 例題でありエラーになる
-- INSERT INTO tbl_tea VALUES (2, '紅茶', 850);
```

```sql
INSERT INTO tbl_subjects VALUES (1, '佐藤', 76, 98);
INSERT INTO tbl_subjects VALUES (2, '山崎', 90, 74);
SELECT * FROM tbl_subjects;
```

### 特定の列にのみ値を登録する

```sql
-- 例題でありエラーになる
-- INSERT INTO tbl_tea (name, code) VALUES ('ほうじ茶', 3);
```

```sql
INSERT INTO tbl_subjects (id, name, math) VALUES (3, '小林', 75);
INSERT INTO tbl_subjects (id, name, english) VALUES (4, '山崎', 74);
SELECT * FROM tbl_subjects;
```

## INSERT文(2)

### SELECT文の結果を登録する

```sql
-- 例題でありエラーになる
-- INSERT INTO tbl_petlist (id, name) SELECT no, name FROM tbl_cat;
```

```sql
INSERT INTO tbl_jinji (name) SELECT name FROM tbl_employee WHERE section = '人事部';
SELECT * FROM tbl_jinji;
```

## UPDATE文

### 1つの値を更新する

```sql
-- 例題でありエラーになる
-- UPDATE tbl_lunch SET price = 760 WHERE code = 2;
-- UPDATE tbl_lunch SET menu = '今日のランチ', price = 790 WHERE code = 1;
```

```sql
UPDATE tbl_shopping SET material = '糸のこぎり', num = 2 WHERE priority = 1;
UPDATE tbl_shopping SET num = 10 WHERE priority >= 3;
SELECT * FROM tbl_shopping;
```