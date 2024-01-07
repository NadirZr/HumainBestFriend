# The HumansBestFriend app

An easy-to-use distributed application running on multiple Docker containers.

# Content:\
1\. [Requirements](#requirements)\
2\. [Getting Started](#getting-started)\
3\. [Tasks](#tasks)\
4\. [Tagging Images](#tagging-images)\
5\. [Pushing Images](#pushing-images)\
6\. [Creating Docker Compose File](#creating-docker-compose-file)\
7\. [Running Docker Compose](#running-docker-compose)

## Requirements

- The project is developed within a Linux virtual machine.\
- Initially, we forked the project from the professor's Git repository and then cloned it into the virtual machine. Modifications are made internally, with the option to push or pull updates as needed.

## Getting Started

This application utilizes Python, Node.js, and .NET, incorporating Redis for messaging and Postgres for data storage.

## Tasks

### Create a Docker Compose Build

A file named `docker-compose.build.yml` was created.\
Execute the following command to run the file:\
```
    docker-compose -f docker-compose.build.yml up
```

To verify the creation of the images, use:

 `docker images`

### Tagging Images

The images were tagged with 'nadir19' to facilitate pushing them to the private registry:

 `docker tag result nadir19/result:latest
    docker tag vote nadir19/vote:latest
    docker tag worker nadir19/worker:latest
    docker tag seed nadir19/seed-data:latest`

### Pushing Images

 `docker push nadir19/result
    docker push nadir19/vote
    docker push nadir19/worker
    docker push nadir19/seed-data`

### Creating Docker Compose File

The docker compose file was created in accordance with the specified requirements. The file can be viewed [here](Link to docker-compose file).

### Running Docker Compose

To run the docker compose file, use: `docker-compose up`

To stop the containers: `docker-compose down`
