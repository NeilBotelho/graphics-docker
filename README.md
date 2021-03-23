# Basics
youll need to be sudo or root to run docker containers.
to enter a docker container run:


```docker run -it graphics```


then ```source ~/.bashrc``` to get a nicer prompt
But to run graphics program(like the libgraph programs) the command is a little different.

# Note
Every time you stop a docker container the changes made will be discarded. If you want to stop them from being discarded then after exiting a docker container use 

```docker ps -a```

to see what the container ID of the last run container was and run

```docker commit CONTAINER_ID graphics``` 

to overwrite the graphics image with your changes

# To get graphics output from docker([reference](https://www.tutorialspoint.com/running-gui-applications-on-docker-in-linux)):
Run ```xauth list``` and copy the output

run 


```docker run -ti --net=host -e DISPLAY -v /tmp/.X11-unix graphics bash```


inside the container run:

```xauth add copiedOutput``` 

Now you can run graphics program from the container. Remember to save the image after exiting
