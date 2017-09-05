# Cloud Foundry Commands 
- Get apps
```
    cf apps
```

- Get Services
```
    cf services
```

- Create Service
```
     cf create-service mongodb small-plan myMongo
```

- Bind Service to App
```
    cf bind-service myapp myservice
```

- Remove Service/apps
```
    cf delete myServiceOrAppName
```	
	
- Rename Service
```
    cf rename-service myoldservicename mynewservicename
```

- Push app - No manifest file
```
cf push myappname -p target/myjarfile.jar
```

- Push app - With manifest file
```
cf push
```
	
- Recent logs
```
    cf logs myapp --recent
```

- Tail logs
```
    cf logs myapp
```
	
	
	
#Git
- Git stage modified or delete files
```
git add -u
```

- Git link to a remote repo
```
git remote add origin https://github.com/....
```

- Compare single file in difference revisions
```
git diff version1:file version2:file
```

- Show diffs between local and remote
```
git diff local(master) remote (origin/master)
```

- Overwrite local changes
```
git reset --hard HEAD
```

- Download(Clone) git project
```
git clone <url>
```

- Set git proxy
```
git config --global http.proxy http://<user>:<password>@<proxy server>:<port>

```
- Cache Git credentials (10800 is seconds - 3 hours)
```
git config credential.helper store
git config --global credential.helper "cache --timeout=10800"
git push origin master
```

- Set commit author
```
git config --global user.name <username>
git config --global user.email <email>
```

- Show recent commits
```
git log
```
- Search log
```
git log --grep regexp
```

- Sparse Checkout (Example using Eureka)
```
git init
git remote add -f origin https://github.com/Netflix/eureka.git
git config core.sparseCheckout true
echo "eureka-examples/" >> .git/info/sparse-checkout
git pull origin master
```

#Docker Commands
- Build Image from DockerFile
```
docker build -f /path/Dockerfile .
```

- Show running docker containers
```
docker ps
```

- Show all docker containers
```
docker ps -a
```

- Remove a docker container (container id can be retrieved using "docker ps -a"
```
docker rm <container id>
```

- Rename local image
```
docker tag bbdaf4361256 helloworld:latest
```

- Start Docker container
```
docker run --name helloworldcontainer -d helloworld
```

- Stop all containers
```
docker stop $(docker ps -a -q)
```

- Delete all containers
```
docker rm $(docker ps -a -q)
```

- Delete all local docker images
```
docker rmi $(docker images -q)
```
- Delete dangling images
```
docker rmi $(docker images -f "dangling=true" -q)
```

- Tail Docker logs
```
docker logs <container id>
```

- Pull docker image from dockerhub
```
docker pull davemcfadden/springboot-docker
```

- Run BASH inside container
```
docker exec -it <container id> bash
```

- Run BASH command inside container
```
docker exec -it <container id> bash -c "echo hello"
```

- Mount local directory (Example for MySQL)
```
docker run -p 3306:3306 --name <container name> -v //c/data/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=<root password> -e MYSQL_DATABASE=<database name> -e MYSQL_USER=<mysql username> -e MYSQL_PASSWORD=<mysql password> -d mysql

```


#Unix
- EC2 File transfer
```
scp -i C:/Users/Dave/Downloads/ec2.pem spring-boot-hello-world-0.0.1-SNAPSHOT.jar  ec2-user@ec2-11-111-111-111.compute-1.amazonaws.com:/home/ec2-user/
```

#AWS
- Associate Instance with ECS Cluster (Add to User Data)
```
#!/bin/bash
echo ECS_CLUSTER=your_cluster_name >> /etc/ecs/ecs.config
```

# Mongo

- Remote Connect
```
mongo <IP ADDRESS>:<PORT>/<DB NAME> -u <USERNAME> -p <PASSWORD>
```

- Find (AND)
```
db.sampleset.find("name":"bob","age":23)
```
```
db.sampleset.find({$and: [{"name": "bob"}, {"age": 23}]})
```

- Find (OR) 
```
db.sampleset.find({$or: [{"name": "bob"}, {"age": 23}]})
```
 
- Find Explain
```
db.sampleset.find({$or: [{"name": "bob"}, {"age": 23}]}).explain()
```
```
db.sampleset.find({$or: [{"name": "bob"}, {"age": 23}]}).explain("executionStats")
```
 
- Create Index Ascending
```
db.sampleset.createIndex({"name":1})
```

- Create Index Descending
```
db.sampleset.createIndex({"name":-1})
```

- Drop Index
```
db.sampleset.dropIndex({"name":1})
```

- Index Hint
```
 db.sampleset.find("name":"bob","age":23).hint( { indexName } )
```

- Update (Single element)
```
db.sampleset.update({"_id":"01011"},{"$set":{"city":"london"}})
```

- Update (Add element to array)
```
db.sampleset.update({"_id":1},{$push:{shops:{"newColumn":null}}})
```

- Update (Muliple Rows)
```
db.sampleset.update({"city":"HADLEY"},{"$set":{"city":"london"}},{"multi":true})
```

- Update (Insert if not there)
```
db.sampleset.update({"city":"HADLEY"},{"$set":{"city":"london"}},{"multi":true,"upsert":true})
```

- Aggregation - Count number of times Belfast appears
```
db.sampleset.aggregate(
[
{$group:{"_id":"$city", count:{$sum: 1}}}
]
)
```

- Aggregation - Group City by Population
```
db.sampleset.aggregate(
[
{$group:{"_id":"$city", count:{$sum: "$pop"}}},
{$sort:{count:-1}}
]
)
```

- Aggregation - $lookup (Only valid in Mongo 3.2)
```
db.people.aggregate(
[
{$lookup:{
from:"lookup",
localField:"age",
foreignField:"age", 
as: "Age_Description"
}
}
]
)
```
# Cassandra (CQL)

- Create Keyspace
```
CREATE KEYSPACE DAVE_SPACE WITH replication = {'class':'SimpleStrategy', 'replication_factor' : 3};
USE DAVE_SPACE;
```

- Show Existing Keyspaces
```
describe keyspaces;
```

- Show Existing Tables
```
describe tables;
```



