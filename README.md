## Criando um MySQL personalizado com redução do uso de memória:

- Criar um arquivo passowrd para nosso banco de dados:

<pre><code> openssl rand -base64 32 > db_password.txt </pre></code>
<pre><code>openssl rand -base64 32 > db_root_password.txt </pre></code>

- Para ver o passowrd
<pre><code> cat db_root_password.txt </pre></code>

- Execute o docker-compose.yml
<pre><code> docker-compose up -d </pre></code>

- Verifique o docker em execução
<pre><code> docker ps -a </pre></code>

- Verifique o banco de dados Mysql:
<pre><code> docker exec -it Mysqldb mysql -u root -p </pre></code>

- Use o arquivo de passowrd (db_root_password.txt)

## Como reduzir o uso de memória do MySQL:

- Localize o arquivo my.cnf

<pre><code> /etc/mysql </pre></code>
<pre><code> nano my.cnf </pre></code>

- Edite:

[mysqld]
<pre><code> max_allowed_packet = 990M </pre></code>
<pre><code> max_allowed_packet = 2G </pre></code>

[mysqldump]
<pre><code> max_allowed_packet = 2G </pre></code>

# Fine Tuning

key_buffer = 16M </br>
read_buffer = 60K </br>
sort_buffer = 1M </br>
innodb_buffer_pool_size = 64M </br>
tmp_table = 8M </br>
max_allowed_packet = 16M </br>
thread_stack = 192K </br>
thread_cache_size = 8 </br>


- This replaces the startup script and checks MyISAM tables if needed
- the first time they are touched
<pre><code> myisam-recover-options  = BACKUP </pre></code>
<pre><code> open_files_limit = 4096 </pre></code>
<pre><code> table_open_cache = 2048 </pre></code>

# Verificar alterações:

<pre><code> show variables like "%size%"; </pre></code>
<pre><code> show variables like "%buffer%"; </pre></code>
<pre><code> show variables like "%cache%"; </pre></code>
