# 第２章　SQLの基礎

```sql
-- ## データベースとテーブルの作成
-- データベースの作成
CREATE DATABASE db_ehon;

-- データベースの指定
USE db_ehon;

-- テーブルの作成
CREATE TABLE tbl_ehon (
    code INT,
    title VARCHAR(30),
    price INT
);

-- ## テーブルの制約
USE db_ehon;    -- データベースを指定
CREATE TABLE tbl_height (
    id INT PRIMARY KEY, -- id列を主キーに指定します。
    name VARCHAR(20),
    height FLOAT
);

-- ## データの登録
USE db_ehon;    -- データベースを指定
-- データを登録する
INSERT INTO tbl_ehon (code, title, price) VALUES (111, 'Cの絵本', 1380);
INSERT INTO tbl_ehon (code, title, price) VALUES (112, 'Javaの絵本', 1580);
INSERT INTO tbl_ehon (code, title, price) VALUES (113, 'アルゴリズムの絵本', 1680);
INSERT INTO tbl_ehon (code, title, price) VALUES (114, 'TCP/IPの絵本', 1680);

-- ## データの取り出し
USE db_ehon;    -- データベースを指定
-- 全てのデータを取り出す
SELECT * FROM tbl_ehon;

-- tbl_heightにデータを登録する
INSERT INTO tbl_height (id, name, height) VALUES (1, '相澤', 149.5);
INSERT INTO tbl_height (id, name, height) VALUES (2, '山本', 172);
INSERT INTO tbl_height (id, name, height) VALUES (3, '澤口', 168);
INSERT INTO tbl_height (id, name, height) VALUES (4, '小林', 149.5);
-- 全てのデータを取り出す
SELECT * FROM tbl_height;
```