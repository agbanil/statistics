# Simple Nodejs App For Calculating Transaction Statistics

This repository contains the code for the Statistics Service;

## Instructions

### Docker

#### Starting Containers

This project has been setup to use docker to create a development environment. The readme assumes docker version >= 1.9.1 installed on your system.

The project contains bash scripts to simplify the interaction with docker and enable dynamic code changes. These can be found in
```
<project_root>/bin
```

To start up disposable containers use:

```
bin/start_disposable.sh
```

The command will attempt to start up containers based on a specific image. If the image cannot be found, it will be downloaded automatically.
If the project's image cannot be found, it will be built from the Dockerfile automatically.

When all is complete, you will be taken directly to the shell of the container with the application started for you.

At this point the app will be accessible with base url:

    http://localhost:32801/v1


Thus your adventure begins... 

#### Stopping Containers

simple do ```ctrl+c``` to exit the container and the container will also be stopped. However if you're unsure then do:
```
bin/stop_all.sh
```
to stop the container explicitly.

### Tests

The initial ```bin/start_disposable.sh``` command runs a regression test before starting the project

### Endpoints
Base URL : `http://localhost:32801/v1`

| Name   | Method      | URL                  |
| ---    | ---         | ---                  |
| GET stats   | `GET`       | `/statistics`           |
| Add transactions   | `POST`      | `/transactions`           |

## Technologies used
### Node.js
This project was built using nodejs with restify. The use case needed a lightweight non-blocking endpoint, and looking at how quickly I could bootstrap, I decided to go with nodejs. Bear in mind that this could have also been seemless with GOland, Java, PHP, etc.

### Restify
I could have used bare node but decided to go with restify here because of its load management and concurrency. Restify also keeps connections alive which removes the overhead of creating a connection each time when getting called from the same client.

### Docker
I know it's an overkill at some point but I wanted something that can be run without pain and isn't dependent on what version of what is installed on the local machine. There would have been no need to finish this if it cannot be run.

## Project Structure
.   
├── app       
├── bin                                        
├── tests       
└── README.md