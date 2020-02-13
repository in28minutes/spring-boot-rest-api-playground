# Todo and Hello World Rest APIs Connecting to H2 In memory database running on port 5000

Run com.in28minutes.rest.webservices.restfulwebservices.RestfulWebServicesApplication as a Java Application.


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
```sh
curl -X GET http://localhost:5000/jpa/users/in28minutes/todos/10001 | json_pp
```
expected response
```json
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
```sh
curl -X GET http://localhost:5000/jpa/users/in28minutes/todos/10001 | json_pp
```
expected response
```json
{
  "id": 10001,
  "username": "in28minutes",
  "description": "Learn JPA",
  "targetDate": "2019-06-27T06:30:30.696+0000",
  "done": false
}
```

#### Creating a new todo
```sh
# create record inline
curl -X POST http://localhost:5000/jpa/users/Iryna/todos --header "Content-Type: application/json" --data-binary '{"username": "Iryna","description": "my description","targetDate": "2030-11-09T10:49:23.566+0000","done": false}'

# create record from file, where /path/to/your/file.json should be replaced to real one
curl -X POST http://localhost:5000/jpa/users/Iryna/todos --header "Content-Type: application/json" --data-binary @/path/to/your/file.json
```

#### Updating a new todo record
```
# create record inline
curl -X PUT http://localhost:5000/jpa/users/Iryna/todos/1 --header "Content-Type: application/json" --data-binary '{"username": "Iryna","description": "my description - updated","targetDate": "2030-11-09T10:49:23.566+0000","done": false}'

# create record from file, where /path/to/your/file.json should be replaced to real one
curl -X PUT http://localhost:5000/jpa/users/Iryna/todos/1 --header "Content-Type: application/json" --data-binary @/path/to/your/file.json
```

#### Delete todo
```sh
# delete record with ID=2
curl -X DELETE http://localhost:5000/jpa/users/Iryna/todos/1
```

## H2 Console

- http://localhost:5000/h2-console
- Use `jdbc:h2:mem:testdb` as JDBC URL 
