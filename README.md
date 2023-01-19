# :whale: Docker-config-to-React-NodeJs

### Dockerfile for a React container using the latest Ubuntu image and sets up a development environment with Node.js

To create a Bash script that generates a Dockerfile for a React container using the latest Ubuntu image and sets up a development environment with Node.js, you can use the following script:

    #!/bin/bash

    # create Dockerfile
    touch Dockerfile

    # add Dockerfile instructions
    echo "FROM ubuntu:latest" >> Dockerfile
    echo "" >> Dockerfile
    echo "# install node.js and npm" >> Dockerfile
    echo "RUN apt-get update && \\" >> Dockerfile
    echo "    apt-get install -y nodejs npm" >> Dockerfile
    echo "" >> Dockerfile
    echo "# create app directory" >> Dockerfile
    echo "RUN mkdir -p /usr/src/app" >> Dockerfile
    echo "WORKDIR /usr/src/app" >> Dockerfile
    echo "" >> Dockerfile
    echo "# copy app files" >> Dockerfile
    echo "COPY . /usr/src/app" >> Dockerfile
    echo "" >> Dockerfile
    echo "# install app dependencies" >> Dockerfile
    echo "RUN npm install" >> Dockerfile
    echo "" >> Dockerfile
    echo "# expose port" >> Dockerfile
    echo "EXPOSE 3000" >> Dockerfile
    echo "" >> Dockerfile
    echo "# run app" >> Dockerfile
    echo "CMD [\"npm\", \"start\"]" >> Dockerfile

    # create app directory
    mkdir app
    cd app

    # initialize a new blank Qwik app
    npx create-qwik-app

To use the script, save it to a file (e.g. create-qwik-app.sh) and make it executable with the following command:

    chmod +x create-qwik-app.sh

### Then, run the script with the following command:

    ./create-qwik-app.sh

This will create the Dockerfile and initialize a new blank Qwik app in the app directory. You can then build the Docker image using the Dockerfile with the following command:

    docker build -t <image-name>

Replace `<image-name>` with the desired name for the Docker image. Once the image has been built, you can run it with the following command:

    docker run -p 3000:3000 -d <image-name>

This will run the app in a Docker container on port 3000. You can then access it from your browser at `http://localhost:3000`.
