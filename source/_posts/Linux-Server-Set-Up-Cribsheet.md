---
title: Linux Server Set-Up Cribsheet
date: 2020-04-27 16:37:04
tags:
---


# Install ZSH

1. Connect to your EC2 instance
2. Install zsh : 
```bash
$ sudo apt-get update && sudo apt-get install zsh
```
3. Edit your passwd configuration file to tell which shell to use for user `ubuntu` : `sudo vim /etc/passwd`
4. Look for `ubuntu` user, and replace `bin/bash` by `bin/zsh`
5. Install OhMyZsh : 
```bash
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```
6. Disconnect from your instance and reconnect it. 

# Install Node and npm

1. Connect to your EC2 instance
2. Install node 
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```
3. Activate nvm by typing the following at the command line.
```bash
$ . ~/.nvm/nvm.sh
```
4. Use nvm to install the latest version of Node.js by typing the following at the command line.
```bash
$ nvm install node
```
5. Test the installation
```bash 
$ node -e "console.log('Running Node.js ' + process.version)"
```


# Install docker and docker-compose 
```bash
curl -fsSl https://get.docker.com -o get-docker.sh
```

## Add user to docker group

Check and add permission
```bash
cat /etc/passwd | grep {$USER_NAME}
sudo usermode -aG docker {$USER_NAME}
cat /etc/group | grep docker

```

## Install docker-compose

[Source link](https://docs.docker.com/compose/install/)

```bash
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```


# Install python with anaconda

```bash
$ curl -O https://repo.anaconda.com/archive/Anaconda3-2019.03-Linux-x86_64.sh
$ chmod +x Anaconda3-2019.03-Linux-x86_64.sh
$ ./Anaconda3-2019.03-Linux-x86_64.sh
```

Make sure the installation file should also be linked via the path concatenation
```bash
export PATH=$HOME/anaconda3/bin:$PATH
```


