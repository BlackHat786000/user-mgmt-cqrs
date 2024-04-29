docker network create SpringBankNet

docker run -d --name axon-server -p 8024:8024 -p 8124:8124 --network SpringBankNet --restart always axoniq/axonserver:latest

docker run -it -d --name mongo-container -p 27017:27017 --network SpringBankNet --restart always -v mongodb_data_container:/data/db mongo:latest

docker run -it -d --name mysql-container -p 3306:3306 --network SpringBankNet -e MYSQL_ROOT_PASSWORD=admin123 --restart always -v mysql_data_container:/var/lib/mysql mysql:latest

docker run -it -d --name adminer -p 8080:8080 --network SpringBankNet -e ADMINER_DEFAULT_SERVER=mysql-container --restart always adminer:latest

docker-compose up -d (project created with docker-compose directory name)

docker-compose -p learn_cqrs up -d
