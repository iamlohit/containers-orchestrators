# Setting the base image by setting the image name.
# With this, docker will pull the image mentioned from dockerhub.
FROM node

# Now we tell docker that all subsequent commands will run from the /app folder.
WORKDIR /app

# First `.` will tell which files should be copied into the image.
# This is always outside the container.
# With `.` will copy all files where the Dockerfile is stored into the container.

# Second `/app` will tell where the above mentioned files should be copied to, into the container.
# This is always inside the container.
# This will automatically created the app folder.
# Changing to `./` will point to the current working directory.
COPY . /app

# Now we want to install our application dependencies mentioned in the package.json file with the 'npm install' command.
RUN npm install

# By default, the container is isolated with no communication with even the host and outside world.
# Depending on which port your application needs to run at, we have to Expose the port on the container,
# which tells port will the container listen on for requests.
# By default, the protocol is TCP if not specified.
# You can also skip this command, if you specify the port while running the container with `docker run` command.
EXPOSE 80

# So far above, all commands have been pertaining to the docker image.
# We donot want to run our application as part of the image itself.
# We want our app to run when the docker image is run in a container.
# That is the difference between `RUN` & `CMD`

# Now we will tell docker to run our application whenever this docker image is run.
# The format is an array, with items as individual commands enclosed in "" separated by `,`
CMD ["node", "server.js"]

# So all of the above, has not yet created the images.
# These are just the intructions to create the image, if we ask to build it.
# Once this file is created, we need to run the `docker build <location of the dockerfile>`.
# To run this container, we will use the `docker run <image-name or image-id>`

# Post running this docker image, it will not automatically make the http server available/accessible on the local host.
# We need to bind the port 80 of container to a port on the local host running the container.
# This is done with `docker run -p host-port:container-port <image-name>`
