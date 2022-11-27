# docker-man
Notes on Docker


## Basics
- By default, the username and hostname of a docker container is of the following
  form:
  ```sh
  root@id
  ```
  where `id` is the `CONTAINER ID`, e.g. it might take a value like
  `root@daa226795125`.  
  One could verify this by running from inside a container
  ```sh
  cat /etc/hostname
  ```
  or simply look at the default terminal prompt.

