# checkpoint-repo
# This README area is for my image repo and how to RUN my image (ie. which ports to map to, URLs to visit in the browser to test, etc.) as well as how it was built (make sure to be using --build-arg)

# To build this application to create an executable jar file (maven)
./mvnw clean install

# To build a docker image named "checkpoint-application-image", while passing an image of "adoptopenjdk/openjdk11:alpin" as an argument
docker build --build-arg BASE_IMAGE=adoptopenjdk/openjdk11:alpine -t checkpoint-application-image .

# To list the images in a given directory
docker images

# To run "checkpoint-application-image" image in a new container named "checkpoint-application-container" in HTTP port 81
docker run -it -d -p 81:8080 --name checkpoint-application-container checkpoint-application-image

# To list container information to see if the above created container is running or not
docker ps -a

# To run the application
- goto a web browser
- Type "localhost:81"
- You should see "Welcome to Ace's world!"


## To upload and share an image to a registy and run it in local (Docker Hub)
# To login to your Docker hub account
- docker login

# To create a new build using a base image "adoptopenjdk/openjdk11:alpine" and version1.0 tag
- docker build --build-arg BASE_IMAGE=adoptopenjdk/openjdk11:alpine -t vaaple/checkpoint_repo:version1.0 .

# To push that built image to Docker hub 
docker push vaaple/checkpoint_repo:version1.0

# To spin the server in your local HTTP port 82 with that pushed application
- docker run -d -p 82:8080 vaaple/checkpoint_repo:version1.0

# To run the application
- goto a web browser
- Type "localhost:82"
- You should see "Welcome to Ace's world!"





