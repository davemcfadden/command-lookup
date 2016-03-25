# Cloud Foundry commands 
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

#NPM Commands
