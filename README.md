# data-backup-corn

data back up list is [here](https://kdocs.cn/l/chaI8dpNBg3U)

## backup script history

mongodump
```
mongodump -h 192.168.1.220:29001 -d mas_small_world -o ./mas_small_world --gzip && \
mongodump -h 192.168.1.220:29001 -d baidubaike -o ./baidubaike --gzip &&\
mongodump -h 192.168.1.220:29001 -d crawler -o ./crawler --gzip &&\
mongodump -h 192.168.1.220:29001 -d chuangyebang_v2 -o ./chuangyebang_v2 --gzip &&\
mongodump -h 192.168.1.220:29001 -d indeed -o ./indeed --gzip &&\
mongodump -h 192.168.1.220:29001 -d indeed_2019 -o ./indeed_2019 --gzip &&\
mongodump -h 192.168.1.220:29001 -d itjuzi_v1 -o ./itjuzi_v1 --gzip &&\
mongodump -h 192.168.1.220:29001 -d job51_new -o ./job51_new --gzip &&\
mongodump -h 192.168.1.220:29001 -d job51_zhejiang_ai_recruitment -o ./job51_zhejiang_ai_recruitment --gzip &&\
mongodump -h 192.168.1.220:29001 -d linkedin -o ./linkedin --gzip &&\
mongodump -h 192.168.1.220:29001 -d mytongjijus -o ./mytongjijus --gzip &&\
mongodump -h 192.168.1.220:29001 -d pedata -o ./pedata --gzip &&\
mongodump -h 192.168.1.220:29001 -d pss_system -o ./pss_system --gzip &&\
mongodump -h 192.168.1.220:29001 -d pyspider -o ./pyspider --gzip &&\
mongodump -h 192.168.1.220:29001 -d scrapy -o ./scrapy --gzip &&\
mongodump -h 192.168.1.220:29001 -d touzijie -o ./touzijie --gzip &&\
mongodump -h 192.168.1.220:29001 -d wikipedia -o ./wikipedia --gzip &&\
mongodump -h 192.168.1.220:29001 -d zhilian_2019 -o ./zhilian_2019 --gzip &&\
mongodump -h 192.168.1.220:29001 -d zhilian_new -o ./zhilian_new --gzip &&\
mongodump -h 192.168.1.220:29001 -d zhwiki -o ./zhwiki --gzip &&\
mongodump -h 192.168.1.220:29001 -d zhwiki_info -o ./zhwiki_info --gzip &&\
mongodump -h 192.168.1.220:29001 -d zhwiki_trans -o ./zhwiki_trans --gzip &&\
mongodump -h 192.168.1.220:29001 -d job51_2019 -o ./job51_2019 --gzip 

## mas_small_world
小世界中间数据, 应该没有应用场景

## baidubaike
baidubaike 的简单数据, 互联网上有更新更全的

## chuangyebang_v2
创业邦的企业数据, 2020年之间更新的

## crawler
apple app store 中的 app 数据

## indeed * 
indeed 临时采集的建立数据

## itjuzi *
itjuzi 开通会员后采集的公司库数据

## job51_new
51job 的招聘信息

## job51_zhejiang_ai_recruitment
智联招聘的AI岗位招聘信息



mongodump -h 192.168.1.220:29001 -d job51_new -o ./job51_new --gzip &&\
mongodump -h 192.168.1.220:29001 -d job51_zhejiang_ai_recruitment -o ./job51_zhejiang_ai_recruitment --gzip &&\
mongodump -h 192.168.1.220:29001 -d linkedin -o ./linkedin --gzip &&\
mongodump -h 192.168.1.220:29001 -d mytongjijus -o ./mytongjijus --gzip &&\
mongodump -h 192.168.1.220:29001 -d pedata -o ./pedata --gzip &&\
mongodump -h 192.168.1.220:29001 -d pss_system -o ./pss_system --gzip &&\
mongodump -h 192.168.1.220:29001 -d pyspider -o ./pyspider --gzip &&\
mongodump -h 192.168.1.220:29001 -d scrapy -o ./scrapy --gzip &&\
mongodump -h 192.168.1.220:29001 -d touzijie -o ./touzijie --gzip &&\
mongodump -h 192.168.1.220:29001 -d wikipedia -o ./wikipedia --gzip &&\
mongodump -h 192.168.1.220:29001 -d zhilian_2019 -o ./zhilian_2019 --gzip &&\
mongodump -h 192.168.1.220:29001 -d zhilian_new -o ./zhilian_new --gzip &&\
mongodump -h 192.168.1.220:29001 -d zhwiki -o ./zhwiki --gzip &&\
mongodump -h 192.168.1.220:29001 -d zhwiki_info -o ./zhwiki_info --gzip &&\
mongodump -h 192.168.1.220:29001 -d zhwiki_trans -o ./zhwiki_trans --gzip &&\
mongodump -h 192.168.1.220:29001 -d job51_2019 -o ./job51_2019 --gzip 
```
mysql 的数据是通过  mydumper, myloader


```


mydumper -h 192.168.1.231 -u root -p root -P 3328 -B enwiki20230331 -T enwiki20230301.redirect  -o ./dump
mydumper -h 192.168.1.231 -u root -p root -P 3328 -T enwiki20230331.redirect  -o ./dump -k -c


myloader -h 192.168.1.226 -u root -p knogen -P 33306  --directory=./dump --overwrite-tables --user=root


mysqlsh -h 192.168.1.231 -u root -p root -P 3328 -js

util.dumpTables('enwiki20230331',['redirect'],'/tmp/backup/redirect')

mysqlsh -h 192.168.1.226 -u root -pknogen -P 33307 --js util.loadDump("/tmp/backup/redirect",{ignoreVersion:true})


mysql -P 33307 -pknogen -uroot


# mariadb
~/mysql-shell/bin/mysqlsh -h 192.168.1.226 -u root -pknogen -P 33307

# mysql
33308
~/mysql-shell/bin/mysqlsh -h 192.168.1.226 -u root -pknogen -P 33308

# percona
33306
~/mysql-shell/bin/mysqlsh -h 192.168.1.226 -u root -pknogen -P 33306


myloader -h 192.168.1.226 -u root -p knogen -P 33306  --directory=./dump --overwrite-tables --user=root



source ~/download/enwiki-20240601-page.sql ;



mydumper -h 192.168.1.229 -u root -p root -P 23308 -T enwiki20170201.redirect  -o ./dump620 -k  --csv -c --threads 4


mydumper -h 192.168.1.229 -u root -p root -P 23308 -T enwiki20170201.category --no-locks  --csv  --threads 4  -o ./ttt  --exec "/usr/bin/bzip2 FILENAME"

myloader -h 192.168.1.226 -u root -p knogen -P 33306  --directory=./dump620 --overwrite-tables --user=root -B wikitest



myloader -h 192.168.1.226 -u root -p knogen -P 33306  --directory=./category --overwrite-tables --user=root 



myloader -h 192.168.1.226 -u root -p knogen -P 33308  --directory=./category --overwrite-tables --user=root 

mydumper -h 192.168.1.229 -u root -p root -P 23308 -T enwiki20170201.category --no-locks  --csv  --threads 4  -o ./ttt   --exec-per-thread=/usr/bin/bzip2 --exec-per-thread-extension=".bz2"



myloader -h 192.168.1.226 -u root -p knogen -P 33306  --directory=./ttt --overwrite-tables --user=root   --exec-per-thread=/usr/bin/bzip2 --exec-per-thread-extension=".bz2"



mydumper -h 192.168.1.229 -u root -p root -P 23308 -T enwiki20170201.category --no-locks  --csv  --threads 4  -o ./ttt   --exec-per-thread="/usr/bin/xz -z" --exec-per-thread-extension=".xz"


myloader -h 192.168.1.226 -u root -p knogen -P 33306  --directory=./ttt --overwrite-tables --user=root  --exec-per-thread="/usr/bin/xz -d" --exec-per-thread-extension=".xz"



mydumper -h 192.168.1.220 -u sunny -p sunny2020 -P 23306 -B patents --no-locks  --csv  --threads 4  -o /mnt/hg01/mysql_dump/sunny_patent --exec-per-thread="/usr/bin/xz -z -9" --exec-per-thread-extension=".xz"




mydumper -h 192.168.1.229 -u root -p root -P 23308 -B enwiki20170201 --no-locks  --csv  --threads 4  -o /mnt/hg01/mysql_dump/enwiki20170201 --exec-per-thread="/usr/bin/xz -z -9" --exec-per-thread-extension=".xz"




mydumper -h 192.168.1.229 -u root -p root -P 23308 -B zhwiki20170201 --no-locks  --csv  --threads 4  -o /mnt/hg01/mysql_dump/zhwiki20170201 --exec-per-thread="/usr/bin/xz -z -9" --exec-per-thread-extension=".xz"



mydumper -h 192.168.1.229 -u root -p root -P 23308 -B world --no-locks  --csv  --threads 4  -o /mnt/hg01/mysql_dump/world --exec-per-thread="/usr/bin/xz -z -9" --exec-per-thread-extension=".xz"



myloader -h 192.168.1.226 -u root -p knogen -P 33306  --directory=/mnt/hg01/mysql_dump/zhwiki20170201 --overwrite-tables --user=root  --exec-per-thread="/usr/bin/xz -d" --exec-per-thread-extension=".xz"

# env
DB_NAME=topic
HOST=192.168.1.220
PORT=3306
CURRENT_DATA=`date +%Y%m%d`
DIRECTORY=/mnt/hg01/mysql_dump/"$DB_NAME"_"$CURRENT_DATA"

# 备份命令
mydumper -h $HOST -u root -p root -P $PORT -B $DB_NAME --no-locks --csv --threads 4  -o $DIRECTORY --exec-per-thread="/usr/bin/xz -z -9" --exec-per-thread-extension=".xz" -v 3

# 恢复命令
myloader -h $HOST -u root -p root -P $PORT  --directory=$DIRECTORY --overwrite-tables --user=root  --exec-per-thread="/usr/bin/xz -d" --exec-per-thread-extension=".xz"


# env
DB_NAME=wikiapi
HOST=192.168.1.226
PORT=33306
CURRENT_DATA=`date +%Y%m%d`
DIRECTORY=/mnt/hg01/mysql_dump/"$DB_NAME"_"$CURRENT_DATA"

# 恢复命令
myloader -h $HOST -u root -p knogen -P $PORT  --directory=$DIRECTORY --overwrite-tables --user=root  --exec-per-thread="/usr/bin/xz -d" --exec-per-thread-extension=".xz"

# env
DB_NAME=topic
HOST=192.168.1.226
PORT=33308
CURRENT_DATA=`date +%Y%m%d`
DIRECTORY=/mnt/hg01/mysql_dump/"$DB_NAME"_"$CURRENT_DATA"

# 备份命令
mydumper -h $HOST -u root -p knogen -P $PORT -B $DB_NAME --no-locks --csv --threads 4  -o $DIRECTORY --exec-per-thread="/usr/bin/xz -z -9" --exec-per-thread-extension=".xz" -v 3


###########

mydumper -h 192.168.1.220 -u sunny -p sunny2020 -P 23306 -B patents --no-locks  --csv  --threads 4  -o /mnt/hg01/mysql_dump/sunny_patent --exec-per-thread="/usr/bin/xz -z -9" --exec-per-thread-extension=".xz"

DB_NAME=wikidb09
HOST=192.168.1.229
PORT=33320
DIRECTORY=/mnt/hg01/mysql_dump/$DB_NAME

# 备份命令
mydumper -h $HOST -u root -p root -P $PORT -B $DB_NAME --no-locks --csv --threads 8  -o $DIRECTORY --exec-per-thread="/usr/bin/xz -z -9 -T 8" --exec-per-thread-extension=".xz" -v 3

```

```
# env
DB_NAME=zhwiki20200101
HOST=192.168.1.229
PORT=33320
DIRECTORY=/mnt/hg01/mysql_dump/$DB_NAME

# 备份命令
mydumper -h $HOST -u root -p root -P $PORT -B $DB_NAME --no-locks --threads 4  -o $DIRECTORY --exec-per-thread="/usr/bin/xz -z -9 -T 8" --exec-per-thread-extension=".xz" -v 3



HOST=192.168.1.229
PORT=33320
dump_wikipedia() {
    local DB_NAME=$1
    local DIRECTORY=$2
    mydumper -h $HOST -u root -p root -P $PORT -B $DB_NAME --no-locks --threads 4  -o $DIRECTORY --exec-per-thread="/usr/bin/xz -z -9 -T 8" --exec-per-thread-extension=".xz" -v 3
}
my_array=("enwiki20230331"  )
for DB_NAME in "${my_array[@]}"; do
    echo "$DB_NAME"
    DIRECTORY=/mnt/hg01/mysql_dump/$DB_NAME
    dump_wikipedia $DB_NAME $DIRECTORY
done

##########


HOST=192.168.1.229
PORT=3310
dump_wikipedia() {
    local DB_NAME=$1
    local DIRECTORY=$2
    mydumper -h $HOST -u root -p root -P $PORT -B $DB_NAME --no-locks --threads 4  -o $DIRECTORY --exec-per-thread="/usr/bin/xz -z -9 -T 8" --exec-per-thread-extension=".xz" -v 3
}
my_array=("enwiki20180120" "zhwiki20180120" )
for DB_NAME in "${my_array[@]}"; do
    echo "$DB_NAME"
    DIRECTORY=/mnt/hg01/mysql_dump/$DB_NAME
    dump_wikipedia $DB_NAME $DIRECTORY
done


##########
HOST=192.168.1.227
PORT=4307
CURRENT_DATA=`date +%Y%m%d`
dump_wikipedia() {
    local DB_NAME=$1
    local DIRECTORY=$2
    mydumper -h $HOST -u root -p root -P $PORT -B $DB_NAME --no-locks --threads 4  -o $DIRECTORY --exec-per-thread="/usr/bin/xz -z -9 -T 8" --exec-per-thread-extension=".xz" -v 3
}
my_array=("complexity" )
for DB_NAME in "${my_array[@]}"; do
    echo "$DB_NAME"
    DIRECTORY=/mnt/hg01/mysql_dump/"$DB_NAME"_"$CURRENT_DATA"
    dump_wikipedia $DB_NAME $DIRECTORY
done


##########

HOST=192.168.1.227
PORT=4308
CURRENT_DATA=`date +%Y%m%d`
loader_wikipedia() {
    local DB_NAME=$1
    local DIRECTORY=$2
    myloader -h $HOST -u root -p root -P $PORT --directory=$DIRECTORY --overwrite-tables --user=root  --exec-per-thread="/usr/bin/xz -d" --exec-per-thread-extension=".xz"
}
my_array=("complexity" )
for DB_NAME in "${my_array[@]}"; do
    echo "$DB_NAME"
    DIRECTORY=/mnt/hg01/mysql_dump/"$DB_NAME"_"$CURRENT_DATA"
    loader_wikipedia $DB_NAME $DIRECTORY
done


########


go run main.go test -V 20210630 && \
go run main.go test -V 20210930 && \
go run main.go test -V 20211231 && \
go run main.go test -V 20230331


enwiki20230331

```
