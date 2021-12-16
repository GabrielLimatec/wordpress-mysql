# wordpress-mysql
1º criar uma pasta como o nome do serviço ex: wordpress
2º criar um arquivo docker-composer.yml
3° O arquivo deve ter o seguinte conteudo

4º Cole o texto no arquivo .yml e salve as alterações:

version: '2'

services:
   db:
     image: mysql:5.7
     volumes:
       - db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
volumes:
    db_data:
    
5º Depois basta dar o comando: docker-compose up -d
6° Agora em seu navegador entre localhost:8000 ou http://127.0.0.1:8000 vai aparecer a tela de instalação do wordpress.
