# Todo and Hello World Rest APIs Connecting to MySQL

Runs on port 5000

Run com.in28minutes.rest.webservices.restfulwebservices.RestfulWebServicesApplication as a Java Application.


## Containerization

### Troubleshooting

- Problem - Caused by: com.spotify.docker.client.shaded.javax.ws.rs.ProcessingException: java.io.IOException: No such file or directory
- Solution - Check if docker is up and running!
- Problem - Error creating the Docker image on MacOS - java.io.IOException: Cannot run program “docker-credential-osxkeychain”: error=2, No such file or directory
- Solution - https://medium.com/@dakshika/error-creating-the-docker-image-on-macos-wso2-enterprise-integrator-tooling-dfb5b537b44e

### Creating Containers and Running Locally


### Run MySQL  

```
docker run --detach --env MYSQL_ROOT_PASSWORD=dummypassword --env MYSQL_USER=todos-user --env MYSQL_PASSWORD=dummytodos --env MYSQL_DATABASE=todos --name mysql --publish 3306:3306 mysql:5.7
```

### Run REST API Container

```
mvn clean install
docker run --name todos-api --link mysql:mysql rangakaranam/07-todo-rest-api-mysql-containerized:0.0.1-SNAPSHOT

```

### Test

Run http://localhost:5000/users/in28minutes/todos


### Push Your REST API Container to Docker Repo

```
docker login

docker push rangakaranam/07-todo-rest-api-mysql-containerized:0.0.1-SNAPSHOT
```


## Hello World URLS

- http://localhost:5000/hello-world

```txt
Hello World
```

- http://localhost:5000/hello-world-bean

```json
{"message":"Hello World - Changed"}
```

- http://localhost:5000/hello-world/path-variable/in28minutes

```json
{"message":"Hello World, in28minutes"}
```


## Hardcoded Service URLs

- GET - http://localhost:5000/users/in28minutes/todos

```
[
  {
    id: 1,
    username: "in28minutes",
    description: "Learn to Dance 2",
    targetDate: "2018-11-09T12:05:18.647+0000",
   : false,
  },
  {
    id: 2,
    username: "in28minutes",
    description: "Learn about Microservices 2",
    targetDate: "2018-11-09T12:05:18.647+0000",
   : false,
  },
  {
    id: 3,
    username: "in28minutes",
    description: "Learn about React",
    targetDate: "2018-11-09T12:05:18.647+0000",
   : false,
  },
]
```

#### Retrieve a specific todo

- GET - http://localhost:5000/users/in28minutes/todos/1

```
{
  id: 1,
  username: "in28minutes",
  description: "Learn to Dance 2",
  targetDate: "2018-11-09T12:05:18.647+0000",
 : false,
}
```

#### Creating a new todo

- POST to http://localhost:5000/users/in28minutes/todos with BODY of Request given below

```
{
  "username": "in28minutes",
  "description": "Learn to Drive a Car",
  "targetDate": "2030-11-09T10:49:23.566+0000",
  "done": false
}
```

#### Updating a new todo

- http://localhost:5000/users/in28minutes/todos/1 with BODY of Request given below

```
{
  "id": 1,
  "username": "in28minutes",
  "description": "Learn to Drive a Car",
  "targetDate": "2045-11-09T10:49:23.566+0000",
  "done": false
}
```

#### Delete todo

- DELETE to http://localhost:5000/users/in28minutes/todos/1


## JPA Service URLs

- GET - http://localhost:5000/jpa/users/in28minutes/todos

```
[
  {
    "id": 10001,
    "username": "in28minutes",
    "description": "Learn JPA",
    "targetDate": "2019-06-27T06:30:30.696+0000",
    "done": false
  },
  {
    "id": 10002,
    "username": "in28minutes",
    "description": "Learn Data JPA",
    "targetDate": "2019-06-27T06:30:30.700+0000",
    "done": false
  },
  {
    "id": 10003,
    "username": "in28minutes",
    "description": "Learn Microservices",
    "targetDate": "2019-06-27T06:30:30.701+0000",
    "done": false
  }
]
```

#### Retrieve a specific todo

- GET - http://localhost:5000/jpa/users/in28minutes/todos/10001

```
{
  "id": 10001,
  "username": "in28minutes",
  "description": "Learn JPA",
  "targetDate": "2019-06-27T06:30:30.696+0000",
  "done": false
}
```

#### Creating a new todo

- POST to http://localhost:5000/jpa/users/in28minutes/todos with BODY of Request given below

```
{
  "username": "in28minutes",
  "description": "Learn to Drive a Car",
  "targetDate": "2030-11-09T10:49:23.566+0000",
  "done": false
}
```

#### Updating a new todo

- http://localhost:5000/jpa/users/in28minutes/todos/10001 with BODY of Request given below

```
{
  "id": 10001,
  "username": "in28minutes",
  "description": "Learn to Drive a Car",
  "targetDate": "2045-11-09T10:49:23.566+0000",
  "done": false
}
```

#### Delete todo

- DELETE to http://localhost:5000/jpa/users/in28minutes/todos/10001


## H2 Console

- http://localhost:5000/h2-console
- Use `jdbc:h2:mem:testdb` as JDBC URL 
