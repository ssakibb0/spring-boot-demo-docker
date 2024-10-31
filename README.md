I have created one demo spring boot project and deploy into the docker step by step

##Using Cmd
#1.docker search openjdk // it will search the jdk
#2.docker pull openjdk:22 // pull the image of jdk
#3.docker images // check images
#4.docker create --name openjdk openjdk:22
#5.docker start 88604a3eb10bbaa9da43c1cfe235eb4d84081510aac198313bb159a6d9828560(IMG ID) // it will start but it will end on that time only
#6.docker run -it openjdk:22 // it will run until u stop.
#7. now u have successfully create the jdk enviroment its time to copy your code and paste inside the jdk tmp folder
#8.docker exec unruffled_colden(container name) ls // it will show u all the folder inside the container
#9.docker cp target/spring-docker-app.jar unruffled_colden:/tmp // make the jar folder of your project
#10.docker commit –change=’CMD[“java”,”-jar”,”/tmp/spring-docker-app.jar”]’  unruffled_colden  sakib/SpringDemo:v1     or   docker run -p 8080:8080 sakib/springdemo:v1 java -jar /tmp/spring-docker-app.jar // use this

## Using Dockerfile

FROM openjdk:22
ADD target/spring-docker-app.jar spring-docker-app.jar
ENTRYPOINT ["java","-jar","/spring-docker-app.jar"]

add this into the Dockerfile in your project.

and run the command 
docker build -t sakib/springdemo:v2 .
docker run -p 8080:8080 sakib/springdemo:v2
