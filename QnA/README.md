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
     root@ace5289fdcb7:/# # Install all the stuffs you need, e.g.
     root@ace5289fdcb7:/# apt update
     root@ace5289fdcb7:/# apt install openssh-server
     root@ace5289fdcb7:/# apt install rsync
     root@ace5289fdcb7:/# apt install gvim
     ────────────────────────────────────────────────────────────────────────
     ~ ❯❯❯ # In another terminal of your local machine, inspect the running container
     ~ ❯❯❯ docker ps
     CONTAINER ID   IMAGE          COMMAND       CREATED          STATUS          PORTS     NAMES
     ace5289fdcb7   ubuntu:16.04   "/bin/bash"   11 seconds ago   Up 10 seconds             laughing_wescoff
     ~ ❯❯❯ docker commit ace5289fdcb7 ubuntu:vm
     ```
     where the last command `docker commit ace5289fdcb7 ubuntu:vm`'s signature is
     ```sh
     docker commit CONTAINER [REPOSITORY[:TAG]]
     ```
     which you can also easily find in `docker commit --help`.
1. `rsync` from a docker container on a Windows machine to a Linux machine
   - Once docker has been installed on the Windows machine, open powershell
     and type:
     ```sh
     docker pull ubuntu
     # mount local folder to some docker container folder, e.g.
     docker run -it --rm -v C:\Users\foo/Downloads:/mnt ubuntu
     ```
     Then you'll be in a docker container. Next run
     ```sh
     apt update
     apt install openssh-server rsync
     ```
     Finally, just `rsync` like you'd normally do. (It seems that all
     the Network, port stuffs, etc. has been well taken care of by docker.)
     ```sh
     # e.g.
     rsync -avP /mnt/big_backup/ phunc20@192.168.0.113:~/downloads/win_backup/
     ```
       
     You could `docker commit` that docker container so that it's ready to be
     used next time.


## Troubleshoot
- MacOS
    - Unshuttable window (Cf. <https://github.com/docker/for-mac/issues/5037>)  
      [!figs/unshuttable_window.png]  
        
      This command works for me: `killall Docker && open -a /Applications/Docker.app`















