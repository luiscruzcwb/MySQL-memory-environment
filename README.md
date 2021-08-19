<p><strong>Criar um arquivo passowrd para nosso banco de dados:</strong></p>
<p>$ openssl rand -base64 32 &gt; db_password.txt<br />$ openssl rand -base64 32 &gt; db_root_password.txt</p>
<p>$ cat db_root_password.txt</p>
<p>$ docker exec -it Mysqldb mysql -u root -p<br />Enter the root password which is in db_root_password.txt</p>
<p><strong>Como reduzir o uso de mem&oacute;ria do MySQL:</strong></p>
<p>Localize o arquivo my.cnf</p>
<p>$ /etc/mysql<br />$ nano my.cnf</p>
<p><strong>Edite:</strong></p>
<p>[mysqld]<br />#max_allowed_packet = 990M<br />max_allowed_packet = 2G<br />[mysqldump]<br />max_allowed_packet = 2G</p>
<p>#<br /># * Fine Tuning<br />#<br />key_buffer = 16M <br />read_buffer = 60K <br />sort_buffer = 1M <br />innodb_buffer_pool_size = 64M <br />tmp_table = 8M <br />max_allowed_packet = 16M <br />thread_stack = 192K <br />thread_cache_size = 8 <br /># This replaces the startup script and checks MyISAM tables if needed<br /># the first time they are touched<br />myisam-recover = BACKUP <br />max_connections = 25</p>
<p>-----</p>
<p><strong>Verificar altera&ccedil;&otilde;es:</strong></p>
<p>show variables like "%size%";<br />show variables like "%buffer%";<br />show variables like "%cache%";</p>
