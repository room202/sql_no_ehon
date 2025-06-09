# SQL の絵本 第 2 版 データベースが好きになる新しい 9 つの扉

## 公式サイト

https://www.shoeisha.co.jp/book/detail/9784798159539

## 開発環境

-   [XAMPP Ver8.2.12(zip 版)](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/8.2.12/xampp-windows-x64-8.2.12-0-VS16.zip/download)
-   [DBeaver](https://dbeaver.io/)

## 事前準備

データベースまたはテーブル作成時のデフォルトの照合順序を`utf8_general_ci`に設定する

ファイルの場所：C:\xampp\mysql\bin\my.ini

ファイル名：my.ini (XAMPP コントロールパネルから開くことができる)

### 設定の追加

下記設定を追加する

```ini
character-set-server = utf8
```

変更前

```ini
～省略～
# The MySQL server
[mysqld]
port= 3306
～省略～
```

変更後

```ini
～省略～
# The MySQL server
[mysqld]
character-set-server = utf8  # ← このように追加
port= 3306
～省略～
```

変更を保存したら`XAMPPコントロールパネル`から`Apache`と`MySQL`を再起動する

## 第１章　データベースとは

## [第２章　SQLの基礎](Chapter02/README.md)

## [第３章　演算子](Chapter03/README.md)
