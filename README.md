# Step-by-step deployment of your own data science docker

## 1. Building the Ubuntu Docker

Get the latest ubuntu docker confs.

```bash
$ docker pull ubuntu
```

Create an Ubuntu image.
```bash
$ docker run -it --name <imagename> -p 8080:8080 ubuntu
```

Setup basics of the environment.

```bash
$ apt-get update
$ apt-get install nano
$ apt-get install -y python3-pip python3-dev
$ pip3 install --upgrade pip
$ pip3 install virtualenv
```

## 2. Create a Test Project to Launch a Jupyter Server

Make sure that you are still in the docker!

Create a new user and switch to the created user.

```bash
$ adduser <username>
$ su <username>
$ cd ~
```

Create a project directory and setup the virtual environment.

```bash
$ mkdir prx
$ cd prx
$ mkdir data notebooks
$ virtualenv -p python3 venv
$ source venv/bin/activate
$ pip install jupyter
$ pip install jupyterlab
```

Start up local jupyter server.

```bash
$ jupyter lab --ip 0.0.0.0 --port 8080 --no-browser --allow-root
```

You can now open jupyter in a browser via the prompted url.

## 3. Clone a Github Repository

Install and configure git.

```bash
$ apt install git
$ su <username>
$ git config --global user.name "<your_git_username>"
$ git config --global user.email "<your_git_email>"
$ ssh-keygen -t rsa -b 4096 -C "<your_git_email>"
```

Copy the output of the following commend and add ssh key in your Github account.
```bash
$ cat ~/.ssh/id_rsa.pub
```

Connect to git.

```bash
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_rsa
$ git clone <repo url>
```

## 4. Stop, Start and Execute the Image

Run the following commands to stop, start and run a specific image, based on the image name.

To start up an image, run:

```bash
$ docker start <imagename>
```

To execute on image, run:

```bash
$ docker exec -it <imagename> bash
```

To stop an image, run:

```bash
$ docker start <imagename>
```
