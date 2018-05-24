# Docker Commands

## Find docker machine:

    $ docker-machine ls

## Docker Hello World:

    $ docker run hello-world

## Single docker machine:

    $ docker-machine ssh

## Login to "default" machine:

    $ docker-machine ssh default

### sudo to root:

    docker@default:~$ sudo -i
    root@default:~# exit
    docker@default:~$ exit

## Vagrant's boot2docker:
### SSH into VM

    $ boot2docker ssh

>  Username: docker 
>  Password: tcuser

## Remove each machine:

    $ docker-machine rm my-docker-machine

## View Docker Images:

    $ docker images

## List of running containers and their details:

    $ docker ps



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc3MTA4MTgxNV19
-->