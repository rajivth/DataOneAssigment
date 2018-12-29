
#Movie Dash Board Web Interface

Movie Dash Board Web Interface is a system for track down of movies for thier assocation of director , actress/actresses ,and review.

### Installation Requirement

1.	Without Docker
*	Min Requirement of Software JDK 1.8 / JRE1.8 (Window System)

2.	With Docker.  
*	Docker version 18.XX.XX


### Installing
1.	Without Docker

```
*	Download Jdk 1.8 binary setup from oracle Site as per your window system supportable(32 /64) bit 
*	Install JDK 1.8 using binary  setup & setting environment variable for java 
	Note:  iInstallation JDK 1.8 and environment variable setting please ref below link
	https://www.guru99.com/install-java.html
*	Open command prompt either using (window option + R) or go start button window and type cmd
*	Verifying install java version on command prompt using type java -version
*	Extract on dataOneio.zip on local System 
*	Run the jar files on your local system using following command
	java -jar [location of jar file]
	Eg - java -jar E:/dataOneio/userAccountService_9080-0.0.1-SNAPSHOT.jar

*	Running two remaing jar files using same step [java -jar NameOfJar.jar]
	reviewService_9083-0.0.1-SNAPSHOT
	movieService_9081-0.0.1-SNAPSHOT

```
2.  With Docker
*	Install Docker on your system please ref. below link
	https://docs.docker.com/toolbox/toolbox_install_windows  
*	Open command prompt either using (window option + R) or go start button window and type cmd
*	Verifying install docker install on  your system using type docker -v
2.1 Steps for Create Dockerfile 
	Create a simple Docker file with name Dockerfile1.txt in your window system and copy below content and relace with content as mentioned in Note.
  
	```````````````````````````````````````````````````
	# Start with a base image containing Java runtime
	FROM openjdk:8

	# Add the application's jar to the container
	ADD E:/dataOneio/nameOfjar.jar

	# Make port  available to the world outside this container
	EXPOSE DOCKER_PORT

	# Run the jar file 
	ENTRYPOINT ["java","-jar","nameOfjar.jar"]
	```````````````````````````````````````````````````````````````
	Note: Replace following as manner DOCKER_PORT & NameofJar
	
	Example - Your service name is movieService_9081-0.0.1-SNAPSHOT.jar then
	DOCKER_PORT - 9081
	NameofJar - movieService_9081-0.0.1-SNAPSHOT.jar
	
2.2 Build Docker Image using following command on cmd

*	build -f Dockerfile -t movieService_9081-0.0.1-SNAPSHOT.jar .
	
	Note: (.) means current location where Dockerfile.txt exist
	
2.3 Run Docker Image	
*	Docker run -p DOCKER_PORT:MICRO_SERVICE_PORT movieService_9081-0.0.1-SNAPSHOT.jar
	
	Note:DOCKER_PORT and MICRO_SERVICE_PORT replace with your service port mentioned with jar
	Example- 
	Docker run -p 9081:9081 movieService_9081-0.0.1-SNAPSHOT.jar

2.4 repeat 2.1,2.2 and 2.3 step for other two jar create docker image.
	Note:replace following below content another two jar 
	DOCKER_PORT
	MICRO_SERVICE_PORT
	nameOfjar
	



