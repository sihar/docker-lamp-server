# docker lamp-server
- Apache  
- PHP 5.6, PHP 7.0  
- Postgresql 10.6  
- MySQL 5.6  

## Spesifikasi pengujian
OS Version : Windows 10 Pro 1803  
Docker Version : 18.09

## Catatan
Sesuaikan volume path di masing-masing service  
create data volume terlebih dahulu untuk database mysql dan postgresql
docker volume create mysql-data  
docker volume create postgresql-data  
  
Mengubah konfigurasi di php  
docker exec -it nama_container bash  
[lakukan perubahan]  
#/etc/init.d/apache2 restart  
