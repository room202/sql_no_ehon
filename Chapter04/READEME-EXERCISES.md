# 第4章　関数　オリジナル演習問題

## 演習用テーブル作成

```sql
USE db_ehon;

-- 商品管理テーブル
CREATE TABLE tbl_products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(50),
    price DECIMAL(8,2),
    stock_quantity INT,
    last_updated DATETIME
);

INSERT INTO tbl_products VALUES 
(1, '  スマートフォン  ', 89800.75, 25, '2024-03-15 14:30:00'),
(2, 'LAPTOP COMPUTER', 145600.90, 8, '2024-02-28 09:15:30'),
(3, 'wireless headphones', 12800.50, 45, '2024-04-02 16:45:00'),
(4, '  TABLET DEVICE  ', 65400.25, 12, '2024-01-20 11:20:15'),
(5, 'smart watch', 28900.99, 33, '2024-03-08 13:10:45');

-- 販売実績テーブル
CREATE TABLE tbl_sales (
    sale_id INT PRIMARY KEY,
    product_id INT,
    sales_amount DECIMAL(10,2),
    sale_date DATE,
    customer_region VARCHAR(20)
);

INSERT INTO tbl_sales VALUES 
(1, 1, 89800.75, '2024-03-20', '東京'),
(2, 2, 145600.90, '2024-03-18', '大阪'),
(3, 1, 89800.75, '2024-03-22', '名古屋'),
(4, 3, 12800.50, '2024-03-25', '東京'),
(5, 4, 65400.25, '2024-03-28', '福岡'),
(6, 1, 89800.75, '2024-04-01', '東京'),
(7, 3, 12800.50, '2024-04-05', '大阪'),
(8, 5, 28900.99, '2024-04-08', '名古屋'),
(9, 2, 145600.90, '2024-04-10', '東京'),
(10, 3, 12800.50, '2024-04-12', '東京');

-- 温度測定テーブル
CREATE TABLE tbl_temperature (
    measurement_id INT PRIMARY KEY,
    location VARCHAR(30),
    temperature DECIMAL(4,2),
    humidity DECIMAL(5,2),
    recorded_at DATETIME
);

INSERT INTO tbl_temperature VALUES 
(1, 'サーバールーム', 22.75, 45.50, '2021-07-03 14:27:13'),
(2, '倉庫A', 18.25, 62.30, '2022-11-18 09:42:56'),
(3, 'オフィス', 24.90, 55.75, '2023-02-14 16:18:39'),
(4, '倉庫B', 16.80, 68.90, '2024-06-29 21:53:07'),
(5, 'サーバールーム', 23.10, 47.20, '2024-12-05 03:09:44');

-- 文字列処理用テーブル
CREATE TABLE tbl_messages (
    msg_id INT PRIMARY KEY,
    sender VARCHAR(30),
    message_text VARCHAR(100),
    send_time VARCHAR(50)
);

INSERT INTO tbl_messages VALUES 
(1, '  yamada taro  ', 'Hello World!', '01 23 2020 11:47PM'),
(2, 'SATO HANAKO', 'Good Morning Everyone', '08 07 2021 5:12AM'),
(3, '  tanaka jiro  ', 'Meeting at 3PM', '12 14 2022 1:55PM'),
(4, 'suzuki akiko', 'PROJECT DEADLINE TOMORROW', '03 28 2023 9:33AM'),
(5, 'WATANABE HIROSHI', '  Status Update  ', '10 09 2024 7:26PM');
```

## 演習問題

### 【問題1】数値関数の基本
`tbl_products`テーブルを使用して、以下のクエリを作成してください：

1. 各商品の価格を小数点以下切り上げして表示する
2. 各商品の価格を小数点以下切り捨てして表示する  
3. 各商品の価格を小数点第1位で四捨五入して表示する
4. 在庫数量に0～1の乱数を掛けた値を表示する（シード値は100を使用）

### 【問題2】文字列関数の活用
`tbl_products`と`tbl_messages`テーブルを使用して、以下のクエリを作成してください：

1. 商品名の文字数を表示する
2. 商品名の最初の3文字を抽出して表示する
3. 商品名の前後の空白を除去して表示する
4. 商品名を全て大文字で表示する
5. 送信者名の前後の空白を除去し、全て小文字で表示する

### 【問題3】日付関数の操作
`tbl_temperature`と`tbl_messages`テーブルを使用して、以下のクエリを作成してください：

1. 現在の日時を取得する
2. 測定日時から年、月、日、時間を個別に抽出して表示する
3. 測定日時に30日を加算した日付を表示する
4. 現在日時と測定日時の差を日数で表示する
5. メッセージの送信時間（文字列）を日時型に変換して表示する

### 【問題4】集約関数とグループ化
`tbl_sales`と`tbl_temperature`テーブルを使用して、以下のクエリを作成してください：

1. 全体の売上合計、平均売上、売上件数を表示する
2. 商品別に売上合計と売上件数を表示する
3. 地域別に最大売上と最小売上を表示する
4. 場所別に温度の平均値を小数点第1位で四捨五入して表示する
5. 商品別売上合計が200,000円以上の商品のみを表示する

### 【問題5】変換関数の活用
`tbl_messages`と`tbl_temperature`テーブルを使用して、以下のクエリを作成してください：

1. 温度を文字列型に変換して「温度：XX.XX度」の形式で表示する
2. メッセージの送信時間を日時型に変換し、年月日のみ表示する
3. 湿度を整数型に変換して表示する

### 【問題6】総合問題
以下の要求に応える複合的なクエリを作成してください：

1. 商品名をトリム・大文字化し、価格を千円単位で四捨五入、在庫を文字列に変換して「在庫：XX個」として表示する
2. 地域別に売上合計を算出し、その値が100,000円以上の地域について、地域名を小文字で表示する
3. 測定日時が2024年のデータについて、場所名の文字数、温度の小数点以下切り上げ、湿度の整数変換を同時に表示する

---

<details>

<summary></summary>

## 解答例

### 【解答1】数値関数の基本

```sql
-- 1. 価格の切り上げ
SELECT product_name, price, CEILING(price) AS price_ceil
FROM tbl_products;

-- 2. 価格の切り捨て
SELECT product_name, price, FLOOR(price) AS price_floor
FROM tbl_products;

-- 3. 価格の四捨五入（第1位）
SELECT product_name, price, ROUND(price, 1) AS price_round
FROM tbl_products;

-- 4. 在庫数量×乱数
SELECT product_name, stock_quantity, 
       ROUND(stock_quantity * RAND(100), 2) AS random_stock
FROM tbl_products;
```

### 【解答2】文字列関数の活用

```sql
-- 1. 商品名の文字数
SELECT product_name, LENGTH(product_name) AS name_length
FROM tbl_products;

-- 2. 商品名の最初の3文字
SELECT product_name, SUBSTRING(product_name, 1, 3) AS name_prefix
FROM tbl_products;

-- 3. 商品名のトリム
SELECT product_name, TRIM(product_name) AS name_trimmed
FROM tbl_products;

-- 4. 商品名を大文字化
SELECT product_name, UPPER(product_name) AS name_upper
FROM tbl_products;

-- 5. 送信者名をトリム＆小文字化
SELECT sender, LOWER(TRIM(sender)) AS sender_clean
FROM tbl_messages;
```

### 【解答3】日付関数の操作

```sql
-- 1. 現在の日時
SELECT SYSDATE() AS current_datetime;

-- 2. 日時要素の抽出
SELECT recorded_at,
       YEAR(recorded_at) AS year_part,
       MONTH(recorded_at) AS month_part,
       DAY(recorded_at) AS day_part,
       HOUR(recorded_at) AS hour_part
FROM tbl_temperature;

-- 3. 30日加算
SELECT recorded_at, 
       DATE_ADD(recorded_at, INTERVAL 30 DAY) AS plus_30days
FROM tbl_temperature;

-- 4. 現在との日数差
SELECT recorded_at,
       DATEDIFF(SYSDATE(), recorded_at) AS days_diff
FROM tbl_temperature;

-- 5. 文字列から日時への変換
SELECT send_time,
       STR_TO_DATE(send_time, '%m %d %Y %h:%i%p') AS converted_datetime
FROM tbl_messages;
```

### 【解答4】集約関数とグループ化

```sql
-- 1. 全体統計
SELECT SUM(sales_amount) AS total_sales,
       AVG(sales_amount) AS avg_sales,
       COUNT(*) AS sales_count
FROM tbl_sales;

-- 2. 商品別統計
SELECT product_id,
       SUM(sales_amount) AS total_sales,
       COUNT(*) AS sales_count
FROM tbl_sales
GROUP BY product_id;

-- 3. 地域別最大・最小売上
SELECT customer_region,
       MAX(sales_amount) AS max_sales,
       MIN(sales_amount) AS min_sales
FROM tbl_sales
GROUP BY customer_region;

-- 4. 場所別平均温度
SELECT location,
       ROUND(AVG(temperature), 1) AS avg_temp
FROM tbl_temperature
GROUP BY location;

-- 5. 高売上商品（HAVING使用）
SELECT product_id,
       SUM(sales_amount) AS total_sales
FROM tbl_sales
GROUP BY product_id
HAVING SUM(sales_amount) >= 200000;
```

### 【解答5】変換関数の活用

```sql
-- 1. 温度を文字列化
SELECT location,
       CONCAT('温度：', CAST(temperature AS CHAR), '度') AS temp_string
FROM tbl_temperature;

-- 2. メッセージ時間の日付部分のみ
SELECT sender,
       DATE(STR_TO_DATE(send_time, '%m %d %Y %h:%i%p')) AS send_date
FROM tbl_messages;

-- 3. 湿度を整数化
SELECT location, humidity, CAST(humidity AS SIGNED) AS humidity_int
FROM tbl_temperature;
```

### 【解答6】総合問題

```sql
-- 1. 商品情報の複合変換
SELECT UPPER(TRIM(product_name)) AS clean_name,
       ROUND(price/1000, 0) AS price_k_yen,
       CONCAT('在庫：', CAST(stock_quantity AS CHAR), '個') AS stock_info
FROM tbl_products;

-- 2. 高売上地域の小文字表示
SELECT LOWER(customer_region) AS region_lower,
       SUM(sales_amount) AS total_sales
FROM tbl_sales
GROUP BY customer_region
HAVING SUM(sales_amount) >= 100000;

-- 3. 2024年データの複合処理
SELECT location,
       LENGTH(location) AS location_len,
       CEILING(temperature) AS temp_ceil,
       CAST(humidity AS SIGNED) AS humidity_int
FROM tbl_temperature
WHERE YEAR(recorded_at) = 2024;
```
</details>