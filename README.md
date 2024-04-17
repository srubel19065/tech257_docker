# Docker
**Docker is a way to develop, deploy and run applications using containers. These containers can contain code and dependencies.**


## Key commands
- `docker pull` = pulls a repo/image from docker, you can specify a specific one you have using a tag or if its not available locally it can pull from a library
- `docker run` = runs a container
- `docker push` = push to docker hub
- `docker tag` = tags an image with given name
- `docker commit` = turns container into an image ready to push

## Creating an image and pushing to Docker hub
1. `docker commit <container id> <image name>` = the container you have will be turned into an image with the name you give it
2. `docker tag <image name> <docker user account>/<docker repo>` = this will tag the image, if you specify using <:...>, that tag will be used but if left then it will give 'latest' tag
3. `docker push <docker user account>/<docker repo>:<tag>` = this will push the image to the docker repo

## Dockerizing Northwind App
1. cd to the northwind app repo
2. create a dockerfile 
3. 
```
# syntax=docker/dockerfile:1

# Use an official Python runtime as a parent image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r app/requirements.txt

# Make port 5000 available to the world outside this container
EXPOSE 5000

# Define environment variable
ENV FLASK_APP=northwind_web.py

# Run app.py when the container launches
CMD ["waitress-serve","--port=5000","northwind_web:app"]

```
4. `docker build -t northwind .` = build the container using the dockerfile
5. `docker run -d -p 200:5000 northwind` - runs the container and can see on localhost:200 on browser

