Agora vamos criar um arquivo passowrd para nosso banco de dados:

$ openssl rand -base64 32 > db_password.txt
$ openssl rand -base64 32 > db_root_password.txt

$ cat db_root_password.txt

$ docker exec -it Mysqldb mysql -u root -p
Enter the root password which is in db_root_password.txt


-----

How to reduce the memory usage of MySQL:

Locate your my.cnf file

$ /etc/mysql
$ nano my.cnf


[mysqld]
#max_allowed_packet = 990M
max_allowed_packet = 2G
[mysqldump]
max_allowed_packet = 2G

#
# * Fine Tuning
#
key_buffer              = 16M  
read_buffer             = 60K  
sort_buffer             = 1M  
innodb_buffer_pool_size = 64M  
tmp_table               = 8M  
max_allowed_packet      = 16M  
thread_stack            = 192K  
thread_cache_size       = 8  
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP  
max_connections        = 25

-----

show variables like "%size%";
show variables like "%buffer%";
show variables like "%cache%";
