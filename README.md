# Containerize-a-React-JS-App
Building and packaging is a most frequent activity in software development. Docker makes it easier to create, deploy, and run applications by using containers.
Building and running docker container is a three step process as illustrated here.
Read on further for detailed steps
![image](https://user-images.githubusercontent.com/99332618/209774562-a4bc976f-fbce-43c0-96ed-aff163045771.png)
#How to containerise an app?
## Step 0 : Create sample react application
Create and open a folder in visual studio code, then open a terminal and run the below command. This will create a sample react application.
npx create-react-app .

## Step 1: Write Dockerfile and place inside your project
The Dockerfile is a set of instructions that specify how to build a Docker image.
When you run the docker build command, Docker reads the Dockerfile to build the image.
![image](https://user-images.githubusercontent.com/99332618/209774807-d13de0a7-0bf1-418e-874f-3d383856b3f1.png)
In this Dockerfile:
1. The FROM instruction specifies the base image. In this case, the base image is node:12.18.3-alpine. This is a version of Node.js which is built on top of the lightweight Alpine Linux distribution.
2. The WORKDIR instruction sets the working directory for instructions in the Dockerfile. In this case, the working directory is set to /app.
3. The COPY instruction copies files from the host filesystem into the image. In this case, it is copying the entire current directory (.) into the /app directory in the image.
4. The RUN instruction runs a n this case, npm install to install the dependencies specified in package.json file.
5. The RUN instruction again runs a command within the image, npm run build to build the application.
6. The CMD instruction specifies the default command to execute when a container is started from the image.

## Step 2: Build a Docker Image
The docker build command will build a Docker image from a Dockerfile.
The -t option specifies the name. The . at the end of the command indicates the build context, which is the location of the Dockerfile.
In this case, the docker build command will build an image from the Dockerfile in the current directory (indicated by the .) and give it the name simple-app.

docker build -t simple-app . 

After the above step, you an find a Docker Image named simple-app in your docker desktop
![image](https://user-images.githubusercontent.com/99332618/209775264-a53356bc-1887-4836-b4b9-189372fafd41.png)

## Step 3: Run the application using the container image

docker run -p 3000:3000 simple-app

The docker run command would to start a new container from an image.
The -p 3000:3000 option maps the container's port 3000 to the host's port 3000. This means that traffic sent to the host's port 3000 will be forwarded to the container's port 3000.
The simple-app at the end of the command is the name of the image that the container will be created from.
The docker run command starts a new container from the simple-app image. And forward traffic from the host's port 3000 to the container's port 3000.
This is useful when the simple-app image contains a web server that listens on port 3000. It allows you to access the service running in the container by connecting to the host's port 3000.
In this example you could access the app by opening a web browser and navigating to http://localhost:3000.
![image](https://user-images.githubusercontent.com/99332618/209775686-2b74f30d-e2ad-4742-a097-db326133ab52.png)

# Note:
You can get the sample app to get started on building and running a container using https://github.com/connectrajesh/simple-react-app
And to learn about contenerization using https://www.ibm.com/topics/containerization

Kindly follow Rajesh Muthusamy on linkedlin using https://www.linkedin.com/in/rajeshmuthusamy/ . He has great content!!!!
