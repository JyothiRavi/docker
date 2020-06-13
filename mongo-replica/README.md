Author Jyothi Ravi

Clone the repository

<br>Note: Change the credentials in the .env file.
<br>#cd /docker/mongo-replica/mongo-dockerfile/
<br>#openssl rand -base64 756 > mongo_key
<br>#cd ../
<br>#docker-compose up -d
<br>#docker container ls
<br>#docker exec -it mongodb1 bash

mongo -u root -p --authenticationDatabase admin

rs.initiate({
    _id : 'rs0',
    members: [
      { _id : 0, host : "mongodb1:27017" },
      { _id : 1, host : "mongodb2:27017" },
      { _id : 2, host : "mongodb3:27017" },
	    { _id : 3, host : "mongodb4:27017" }	  
    ]
  })

<br>#docker exec -it mongodb2 bash
mongo -u root -p --authenticationDatabase admin
rs.slaveOk();
show dbs;
 
<br>#docker exec -it mongodb3 bash
mongo -u root -p --authenticationDatabase admin
rs.slaveOk();
show dbs;

<br>#docker exec -it mongodb4 bash
mongo -u root -p --authenticationDatabase admin
rs.slaveOk();
show dbs;

<br># Create a database in the primary replica and check in the secondary nodes to check replication is working.
