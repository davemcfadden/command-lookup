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

- Remove Service
```
    cf delete-service myservice
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
- Git like to remove repo
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
git config --global http.proxy http://<user>:<proxy>@<proxy server>:<port>
```
- Show recent commits
```
git log
```
- Search log
```
git log --grep regexp
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

- Tail Docker logs
```
docker logs <container id>
```

- Pull docker image from dockerhub
```
docker pull davemcfadden/springboot-docker
```


#NPM Commands


#Unix
- EC2 File transfer
```
scp -i C:/Users/Dave/Downloads/ec2.pem spring-boot-hello-world-0.0.1-SNAPSHOT.jar  ec2-user@ec2-11-111-111-111.compute-1.amazonaws.com:/home/ec2-user/
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

- Update (Muliple Rows)
```
db.sampleset.update({"city":"HADLEY"},{"$set":{"city":"london"}},{"multi":true})
```

- Update (Insert if not there)
```
db.sampleset.update({"city":"HADLEY"},{"$set":{"city":"london"}},{"multi":true,"upsert":true})
```


