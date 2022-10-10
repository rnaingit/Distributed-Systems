# Distributed-Systems

Distributed System:- Corona 
Virus Live Updates


Tech Stack: -
1. Server :- Spring Boot 
2. Client UI :- React JS 
3. Database :- MongoDB 

Tools Used :-
1. IntelliJ 
2. Mongo CLI 
3. Docker Desktop 
4. Visual Studio Code


Communication Between Publisher and Broker :-
We have 2 different dockers for publisher and broker service. To send data to the broker we need to 
establish communication between them. For communication between the publisher and broker we have 
used Docker Communication. We have created a docker network over which both the containers run. 
Publisher-broker is a docker network with bridge driver.


Installation Step :-
1. Pull the latest mongo executables for docker image “docker pull mongo:latest”
2. Create docker network “docker network create publisher-broker” 
3. Stop local mongodb instance if any 
4. Start mongo image on port “docker run -d --network publisher-broker -p 27017:27017 --name 
mymongodb mongo:latest” 
5. Build Spring Boot Broker Jar “mvn clean install” 
6. Build Spring docker image for broker “docker build -t springboot-mongodb:1.0 .” 
7. Start the broker container “docker run --network publisher-broker -p 8080:8080 --name broker --link 
mymongodb:mongo -d springboot-mongodb:1.0” 
8. Build Spring Boot Broker Jar “mvn clean install” 
9. Build Spring docker image for publisher “docker build -t publisher .” 
10. Start publisher container “docker container run --network publisher-broker --name publisher -d 
publisher
