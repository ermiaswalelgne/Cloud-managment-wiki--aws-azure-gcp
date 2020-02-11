###### Docker mangement WiKi
# Docker installation (note most of these steps tested on Windows 10)
- Install docker image from [this](https://docs.docker.com/get-docker/)
> Check that your docker hass seccusfully installed and  functioning. The floowing commands should run successfuly without any error
> > `docker version`<br>
> > `docker info`<br>
> > `docker images`<br>
> > `docker ps`<br>
> > `docker run hello-world`<br>

- To build your docker image, you can start downloading an ubuntu docker image from [here](https://hub.docker.com/_/ubuntu/") and use it as a base. Later, you can add requirments on top of it.
- You can also directly pull the above image using the command below
> >  `docker pull ubuntu` 

## To mount your working directory to docker image
> > `run -i -t -v //c/Users/[user_name]/[path_to_your_folder] [IMAGE_ID]:/home/[destination_dir] /bin/bash`

Note: You have to replace `user_name`, `path_to_your_folder`, `IMAGE_ID`, and `destination_dir` with your user name, working director in the host, Ubuntu Image id, and folder name inside Ubuntu, respectively. Note `destination_dir` will be created if the mounting code has run for the first time.

Now inside your docker image you can run `ls home[destination_dir]/`. This should display the contents found inside `[path_to_your_folder] `.

# Let us now install Git-Hub command on this new image
- run the fllowing commands in order

> > `[sudo] apt-get update` <br>
> > `[sudo] apt-get install git` and type **Y** <br>
> > ` git --version`  should return the verion of git, if successfly installed



