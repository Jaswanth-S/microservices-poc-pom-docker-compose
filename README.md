# microservices-poc

This is POC for microservices pattern.

This consists of :

1. config-server(acts as Centralized configuration server)

2. eureka-server (acts as Service Discovery)

3. zuul-gateway (acts as api gateway)

4. demoMongoDb (springboot application which performs CRUD operations on mongodb)


Steps to start the setup:

1. mvn clean compile package 

2. docker-compose up -d

if any problem with mongo  make one docker container of mongodb running

    command to use ---    docker run --name mongo -p 27107:27107 mongo
  
Now all services are up and running
(docker ps -a will show status)

Steps to test the services:

1)   open localhost:8761 in browser, then you can see eureka dashboard and two services(zuul-gateway & demo-mongo) are            
     registered and status is UP.

2)   now test springboot demoMongoDb application 
  
     perform create operation using the url in browser
  
     localhost:8080/create?firstName=firstnamedemo&lastName=lastnamedemo&age=25
  
     you can check by using url (to get all persons) --- 
  
     localhost:8080/getAll
  
3)   now test api gateway 

     use url -- localhost:8092/demo-mongo/getAll
   
     it will route to localhost:8080/getAll and get you all persons details
  
  
  
docker-compose down to down all the service  
  
