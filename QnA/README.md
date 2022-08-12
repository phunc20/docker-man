1. How to use docker as if it was virtual machine? I mean, like
   installing useful packages and saving the state of the container.
   - Short answer: Use `docker commit`
   - Long answer:
     ```bash
~/.../phunc20/docker-man/QnA ❯❯❯ docker image ls -a
REPOSITORY   TAG          IMAGE ID       CREATED         SIZE
ubuntu       16.04        b6f507652425   11 months ago   135MB
archlinux    latest       c689d2874bf2   19 months ago   407MB
centos       7            8652b9f0cb4c   21 months ago   204MB
php          7.0-apache   aa67a9c9814f   3 years ago     368MB
~/.../phunc20/docker-man/QnA ❯❯❯ docker container ls -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
~/.../phunc20/docker-man/QnA ❯❯❯ docker run --rm -it ubuntu
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
d19f32bd9e41: Pulling fs layer
^C
~/.../phunc20/docker-man/QnA ❯❯❯ docker run --rm -it ubuntu:16.04
root@ace5289fdcb7:/#
───────────────────────────────────────────────────────────────────────────────────────────
~ ❯❯❯ docker ps
CONTAINER ID   IMAGE          COMMAND       CREATED          STATUS          PORTS     NAMES
ace5289fdcb7   ubuntu:16.04   "/bin/bash"   11 seconds ago   Up 10 seconds             laughing_wescoff
~ ❯❯❯ docker commit ace5289fdcb7




     ```


















