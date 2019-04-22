# docker-lamp-server
- Adminer  
- PHP 7.2  
- PHP 5.6  
- MySQL 5.6  
- Postgresql 10.6  

## Spesifikasi pengujian
OS Version : Windows 10 Pro 1803, Ubuntu 18.04  
Docker Version : 18.09

## untuk ubuntu, setting docker command agar bisa dijalankan tanpa sudo
Ikuti petunjuk [ini](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04)

## create data volume untuk database mysql dan postgresql
Sebelum menjalankan docker-lamp-server, create data volume terlebih dahulu  
```
docker volume create mysql-data  
docker volume create postgres-data  
```  
sesuaikan volume path untuk folder /var/www/html  

## start semua service di docker-lamp-server
```
docker-compose up
```

## stop semua service di docker-lamp-server
```
docker-compose stop
```
  
Mengubah konfigurasi di php  
```
docker exec -it nama_container bash  
```
Edit konfigurasi di php.ini, kemudian restart service apache di container php  
```
#/etc/init.d/apache2 restart  
```  
  
backup database postgresql  
```
docker exec lamp-server-postgresql pg_dump -U postgres -O nama_database > backup_file.sql  
```

create database di postgresql  
```
docker exec -it lamp-server-postgresql psql -U postgres -c 'create database nama_database;'  
```

restore database postgresql  
```
docker exec -i lamp-server-postgresql psql -U postgres -d nama_database < nama_database.sql  
```  

list all containers (only IDs)  
```
docker ps -aq  
```
  
stop all running containers  
```
docker stop $(docker ps -aq)  
```
  
remove all containers
```
docker rm $(docker ps -aq)
```
  
remove all images  
```
docker rmi $(docker images -q)  
```
  
# Sumber
- [stop and remove container](http://blog.baudson.de/blog/stop-and-remove-all-docker-containers-and-images)
- [enable mod_rewrite](https://perchrunway.com/blog/2017-01-19-getting-started-with-docker-for-local-development)
- [allowoverride all](http://nelkinda.com/blog/apache-php-in-docker/)
- [installing extension gd](https://stackoverflow.com/questions/39657058/installing-gd-in-docker)
- [installing extension imagick](https://discuss.circleci.com/t/how-to-install-php-imagick-php-extension/19051/3)
