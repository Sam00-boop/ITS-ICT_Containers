# Docker installation

## Windows 7, 8, 10 Home edition, old MacOS

Install **Docker Toolbox** following instructions [here](https://docs.docker.com/toolbox/toolbox_install_windows)


## Ubuntu Linux

Update the Ubuntu repo index

```console
$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://archive.canonical.com/ubuntu bionic InRelease
Get:3 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]   
...
```

Install a few prerequisite packages which let apt use packages over HTTPS:

```console
$ sudo apt install apt-transport-https ca-certificates curl software-properties-common -y 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ca-certificates is already the newest version (20180409).
ca-certificates set to manually installed.
curl is already the newest version (7.58.0-2ubuntu3.8).
curl set to manually installed.
software-properties-common is already the newest version (0.96.24.32.12).
software-properties-common set to manually installed.
The following NEW packages will be installed:
  apt-transport-https
```


Add the Docker repo key

```console
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
OK
```

Add the official Docker repo

```console
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
Hit:1 http://archive.canonical.com/ubuntu bionic InRelease                Hit:2 http://archive.ubuntu.com/ubuntu bionic InRelease                   Hit:4 https://download.docker.com/linux/ubuntu bionic InRelease           Get:3 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:5 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]          
Get:6 http://archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]                    
Reading package lists... Done                                      
```

Update the Ubuntu repo index

```console
$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://archive.canonical.com/ubuntu bionic InRelease
Get:3 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]   
...
```

Install Docker

```console
$ sudo apt-get install docker-ce -y 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  aufs-tools cgroupfs-mount containerd.io docker-ce-cli pigz
The following NEW packages will be installed:
  aufs-tools cgroupfs-mount containerd.io docker-ce docker-ce-cli pigz
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 85.5 MB of archives.
...
```

Add your user into docker group (please change the placeholder \<\<USER\>\> accordingly)

```console
$ sudo usermod -aG docker <<USER>>> && newgrp docker
```

Test the docker installation, an empty reponse is expected
```console
$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

## Fedora Linux

Install the dnf-plugins-core package which provides the commands to manage your DNF repositories from the command line.

```console
$ sudo dnf -y install dnf-plugins-core
```

Use the following command to set up the stable repository.


```console
$ sudo dnf config-manager \
    --add-repo \
    https://download.docker.com/linux/fedora/docker-ce.repo
```

Install Docker CE

```console
$ sudo dnf install docker-ce
```

## Docker Desktop

Follow the instructions [here](https://www.docker.com/products/docker-desktop). 

Be aware: a DockerHub username must be created