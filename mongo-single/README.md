Author Jyothi Ravi

Clone the repository
Note: Change the credentials in the .env file.
#cd docker/mongo-single
#docker-compose up -d
#docker container ls
#docker exec -it <CONTAINER ID> bash

mongo -u root -p --authenticationDatabase admin

show dbs
