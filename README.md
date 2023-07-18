## Criando um MySQL personalizado com redução do uso de memória:

Execute o comando abaixo para iniciar o docker-compose.yml:

<pre><code> docker-compose up -d </pre></code>

Verifique os contêineres em execução com o seguinte comando:
<pre><code> docker ps -a </pre></code>

Acesse o banco de dados MySQL com o seguinte comando:
<pre><code> docker exec -it Mysqldb mysql -u root -p </pre></code>

Você precisará fornecer a senha do MySQL que está definida no arquivo .env/MYSQL_ROOT_PASSWORD.

# Verificando os valores "environment":

Verifique os valores das variáveis "environment" com os seguintes comandos no prompt do MySQL:

<pre><code> show variables like "%size%"; </pre></code>
<pre><code> show variables like "%buffer%"; </pre></code>
<pre><code> show variables like "%cache%"; </pre></code>

## Como reduzir o uso de memória do MySQL:

As variáveis serão definidas no arquivo my.cnf. Para acessá-lo, siga estes passos:

Acesse o container do MySQL:
<pre><code> docker exec -it Mysqldb bash </pre></code>

Navegue até o diretório /etc/mysql:
<pre><code> /etc/mysql </pre></code>
Edite o arquivo my.cnf usando um editor de texto, como o nano:
<pre><code> nano my.cnf </pre></code>

Caso o nano não esteja instalado, você pode usar o vim ou instalar o nano com o comando <pre><code>yum install nano.</pre></code>

<pre><code> yum install nano </pre></code>

Faça as alterações necessárias no arquivo my.cnf de acordo com suas necessidades.
Certifique-se de reiniciar o serviço do MySQL após fazer as alterações para que as novas configurações entrem em vigor.



