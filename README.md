## 1. main setup

#### 1.1 get the latest ubuntu docker confs
```bash
$ docker pull ubuntu
```

#### 1.2 run image
```bash
$ docker run -it --name <imagename> -p 8080:8080 ubuntu
```

#### 1.3 setup environment
```bash
$ apt-get update
$ apt-get install nano
$ apt-get install -y python3-pip python3-dev
$ pip3 install --upgrade pip
$ pip3 install virtualenv
```

## 2. create a test project

Make sure that you are in the docker!

Create a new user and switch to it. Create project direct and setup virtualenv.

```bash
$ adduser <username>
$ su <username>
$ cd ~
$ mkdir prx
$ cd prx
$ mkdir data notebooks
$ virtualenv -p python3 venv
$ source venv/bin/activate
$ pip install jupyter
$ pip install jupyterlab
```

start up local jupyter server

```bash
$ jupyter lab --ip 0.0.0.0 --port 8080 --no-browser --allow-root
```

you can now open jupyter in a browser via the prompted url

## 3. clone git repo

#### 3.1 install and configure git
```bash
$ apt install git
$ su <username>
$ git config --global user.name "<your_git_username>"
$ git config --global user.email "<your_git_email>"
$ ssh-keygen -t rsa -b 4096 -C "<your_git_email>"
```

#### 3.2 copy the output of the following commend and add ssh key in your github account
```bash
$ cat ~/.ssh/id_rsa.pub
```

#### 3.3 connect to git
```bash
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_rsa
$ git clone <repo url>
```

## 4. stop, restart and execute image
```bash
$ docker start <imagename>
$ docker exec -it <imagename> bash
```
