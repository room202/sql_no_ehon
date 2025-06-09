# 第３章　演算子

## tbl_exam

```sql
-- db_ehonデータベースを使う
USE db_ehon;

-- tbl_examテーブル作成
CREATE TABLE tbl_exam (
    id INT PRIMARY KEY,
    name VARCHAR(20),
    score_kokugo INT,
    score_eigo INT
);

-- tbl_examテーブルにデータを追加
INSERT INTO tbl_exam (id, name, score_kokugo, score_eigo) VALUES (1, '相澤', 100, 98);
INSERT INTO tbl_exam (id, name, score_kokugo, score_eigo) VALUES (2, '山本', 75, 80);
INSERT INTO tbl_exam (id, name, score_kokugo, score_eigo) VALUES (3, '澤口', 70, 93);
INSERT INTO tbl_exam (id, name, score_kokugo, score_eigo) VALUES (4, '小林', 54, 65);
```

## tbl_stdlist

```sql
-- db_ehonデータベースを使う
USE db_ehon;

-- tbl_stdlistテーブル作成
CREATE TABLE tbl_stdlist (
    id INT PRIMARY KEY,
    myoji VARCHAR(10),
    namae VARCHAR(10)
);

-- tbl_stdlistテーブルにデータを追加
INSERT INTO tbl_stdlist (id, myoji, namae) VALUES (1, '相澤', '奈美子');
INSERT INTO tbl_stdlist (id, myoji, namae) VALUES (2, '山本', '太月');
INSERT INTO tbl_stdlist (id, myoji, namae) VALUES (3, '澤口', '映');
INSERT INTO tbl_stdlist (id, myoji, namae) VALUES (4, '小林', '麻衣子');
```

## tbl_bookprice 

```sql
-- db_ehonデータベースを使う
USE db_ehon;

-- tbl_bookpriceテーブル作成
CREATE TABLE tbl_bookprice (
    code INT PRIMARY KEY,
    title VARCHAR(30),
    price INT
);

INSERT INTO tbl_bookprice (code, title, price) VALUES (1, 'Cの絵本', 1380);
INSERT INTO tbl_bookprice (code, title, price) VALUES (2, 'Javaの絵本', 1580);
INSERT INTO tbl_bookprice (code, title) VALUES (3, 'SQLの絵本');
```