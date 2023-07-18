## Criando um MySQL personalizado com redução do uso de memória:

- Execute o docker-compose.yml
<pre><code> docker-compose up -d </pre></code>

- Verifique o docker em execução
<pre><code> docker ps -a </pre></code>

- Verifique o banco de dados Mysql:
<pre><code> docker exec -it Mysqldb mysql -u root -p </pre></code>

- Use o arquivo de passowrd (.env/MYSQL_ROOT_PASSWORD)

# Verificando os valores "environment":

<pre><code> show variables like "%size%"; </pre></code>
<pre><code> show variables like "%buffer%"; </pre></code>
<pre><code> show variables like "%cache%"; </pre></code>

## Como reduzir o uso de memória do MySQL:

- As variaveis serão setadas no arquivo my.cnf, caso queira conferir, acesse o container e navegue até: 

<pre><code> /etc/mysql </pre></code>
<pre><code> nano my.cnf </pre></code>

- Caso não tenha o nano instalado, use o vim ou instale: 

<pre><code> yum install nano </pre></code>

- Edite conforme sua necessidade.



