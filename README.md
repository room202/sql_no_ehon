# SQLの絵本 第2版 データベースが好きになる新しい9つの扉

## 公式サイト

https://www.shoeisha.co.jp/book/detail/9784798159539

## 開発環境

- [XAMPP Ver8.2.12(zip版)](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/8.2.12/xampp-windows-x64-8.2.12-0-VS16.zip/download)
- [DBeaver](https://dbeaver.io/)

## SQLの勉強をはじめる前に

## 第１章　データベースとは

## 第２章　SQLの基礎

### データベースとテーブルの作成

```sql
CREATE DATABASE db_ehon;
```

```sql
USE db_ehon;
CREATE TABLE tbl_ehon (
    code INT,
    title VARCHAR(30),
    price INT
);
```
