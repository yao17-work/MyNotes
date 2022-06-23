# Mysql install and init

## Install

```sh
# M1 chip image
docker pull mysql/mysql-server:tag
# run(should set root password)
docker run -itd --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql/mysql-server

```

## Init
```sh
# sh into docker container(the container should be running)
docker exec -it MYSQL_CONTAINER_ID /sh
# login mysql in container 
mysql -uroot -p 123456;
# 创建root@‘%’用户
# 1.host为%或者外部指定的host，否则外部的host访问不了。
# 2.这里的IDENTIFIED WITH mysql_native_password是由于mysql8.0要求密码需要加密(默认caching_sha2_password)，mysql_native_password是8.0前的密码方式，否则如果服务端用的包没有兼容8.0会连接数据库失败
create user 'root'@'%' IDENTIFIED WITH mysql_native_password by '123456';

flush privileges;



```