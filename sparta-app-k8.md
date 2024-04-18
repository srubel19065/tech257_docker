# Dockerising sparta app

## Creating Dockerfile 
First go to the app folder and create Dockerfile with `nano Dockerfile`
- **BLOCKER** = At first it didnt work as I created the dockerfile outside of the app folder
```
# syntax=docker/dockerfile:1

FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

COPY . .

RUN npm install

USER node

EXPOSE 3000

CMD node app.js

```

## Build and Run
1. `docker build -t sparta-app-k8:latest .` = build the image using the dockerfile
2. `docker run -d -p 3000:3000 sparta-app-k8:latest` = run the image with the selected port 

## Tag and Push
1. `docker tag sparta-app-k8 r21bxl/sparta-app-k8` = tags the image to the repo on dockerhub
2. `docker push r21bxl/sparta-app-k8` = pushes the image to dockerhub
