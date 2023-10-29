## Detached Mode: `-d` or `--detach`
E.g. running `nginx` in detached mode, or in the background,
```bash
$ docker run -d nginx:1.23
```
What if I want to recover the logs that would be otherwise
displayed had I not opted `-d`?  
Ans: Use `docker logs <container_id|container_name>`


## Port Binding: `-p` or `--publish`
Expose the service's port to one of the host machine's ports, e.g.
```bash
$ docker run -d nginx:1.23 -p 9000:80
```
So the syntax is `-p <host_machine_port>:<docker_container_port>`
