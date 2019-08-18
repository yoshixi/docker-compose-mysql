# mysql in docker-compose

```
## 起動
docker-compose build
docker-compose up

## コンテナに入る
docker-compose exec mysql bash

## mysql起動 パスワードは $MYSQL_ROOT_PASSWORD
mysql -u root -p
```

## CSVをimportするコマンド

### 変数

```
$database-name
$table-name
$csv-file
```

### mysql
データをimportする場合

```
mysql> CREATE DATABASE $database-name DEFAULT CHARACTER SET utf8;

mysql > CREATE TABLE $table-name(
    `id` int(11),
    `keyword` varchar(50),
    `position` int(11),
    `position_history` int(11),
    `position_history_date` datetime,
    `volume` int(11),
    `url` varchar(50),
    `difficulty` int(11),
    `traffic` int(11),
    `cpc` double,
    `last_update` datetime,
    `page_url_inside` varchar(50),
    `serpfeatures` varchar(50)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

mysql> load data local infile "/tmp/data/$csv-file" into table $table-name fields terminated by ',' optionally enclosed by '"';
```
