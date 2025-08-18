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