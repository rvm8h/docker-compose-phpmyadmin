# ------------- EXEMPLE DOCKER-COMPOSE PHPMYADMIN
Dans un docker-compose.yml
en version '3'
creer 2 services

l'un appele db
avec comme hostname mysql
utilisant l'image astondevops/docker-mysql-5.6
une variable d'environnement MYSQL_ROOT_PASSWORD: password
les volumes /var/log/mysql-db:/var/log/mysql


l'autre service nomme phpmyadmin
hostname phpmyadmin
utilisant un image nazarpc/phpmyadmin
avec un links db:mysql
voir la commande depends_on
ajouter les ports utilises par le host 8181 et le container 80
et ajouter les variables d'environnement
MYSQL_USERNAME: root
MYSQL_ROOT_PASSWORD: password
MYSQL_ROOT_PASSWORD
Faire un docker-compose up et dans un navigateur web taper
http://localhost:8181 et loggez vous avec le user root et le password password


docker run -it -d --name db --env MYSQL_ROOT_PASSWORD=password -v /var/log/mysql-db:/var/log/mysql astondevops/docker-mysql-5.6
docker run -it -d --name phpmyadmin --env MYSQL_ROOT_PASSWORD=password --env MYSQL_USERNAME=root --link db:mysql -p 8181:80 nazarpc/phpmyadmin
