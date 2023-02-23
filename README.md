# Learning docker
My first docker project, following a step by step tutorial.[(here)](https://docs.docker.com/get-started/02_our_app/)

## Prerequisites:
- Docker running locally. Follow the instructions to [download and install Docker.](https://docs.docker.com/get-docker/)
- A [Git client.](https://git-scm.com/downloads)
- An IDE or a text editor to edit files. Docker recommends using [Visual Studio Code.](https://code.visualstudio.com/)
- A conceptual understanding of [containers and images.](https://docs.docker.com/get-started/overview/#docker-objects)

## Get the app:

- Clone the getting-started repo
```
$ git clone https://github.com/docker/getting-started.git
```

## Build the app's container image:
- In the `app` file (where `package.json` file is located) create a file named `Dockerfile`
- Add this script in the `Dockerfile`:
```bash
# syntax=docker/dockerfile:1
   
FROM node:18-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```
- Build the container image using the following commands:
    - `$ cd /path/to/app` (replace path/to/ with the path to getting-started/app)
    - `docker build -t getting-started .` (build the container image)

## Start an app container:
- Start a container:
```cmd
docker run -dp 3000:3000 getting-started
```
We use `-d` tag (detach) to run the container in the background;
We also use `-p` tag to create a mapping between the host's port 3000 and the container's port 3000.
- Open [this link](http://localhost:3000/) to see the app