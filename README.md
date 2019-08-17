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
    `Id` int(11),
    `Keyword` varchar(50),
    `Position` int(11),
    `PositionHistory` int(11),
    `PositionHistoryDate` datetime,
    `Volume` int(11),
    `URL` varchar(50),
    `Difficulty` int(11),
    `Traffic` int(11),
    `CPC` double,
    `LastUpdate` datetime,
    `PageURLinside` varchar(50),
    `SERPFeatures` varchar(50)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

mysql> load data local infile "/tmp/data/$csv-file" into table $table-name fields terminated by ',' optionally enclosed by '"';
```
