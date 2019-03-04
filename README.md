# docker lamp-server
- Apache  
- PHP 5.6, PHP 7.2  
- Postgresql 10.6  
- MySQL 5.6  

## Spesifikasi pengujian
OS Version : Windows 10 Pro 1803  
Docker Version : 18.09

## Catatan
Sesuaikan volume path di masing-masing service  
create data volume terlebih dahulu untuk database mysql dan postgresql  
```
docker volume create mysql-data  
docker volume create postgres-data  
```  
  
Mengubah konfigurasi di php  
```
docker exec -it nama_container bash  
```
Edit konfigurasi di php.ini, kemudian restart service apache di container php  
```
#/etc/init.d/apache2 restart  
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
