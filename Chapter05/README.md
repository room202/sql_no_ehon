# 第5章　基本的なデータ操作

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
```

## 第５章はここがkey
