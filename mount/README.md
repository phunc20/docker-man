Say, your image is named `useful_ubuntu` and you want to mount local's `$PWD` to the to-be-started container's `/app` directory.
Then you
```bash
docker run -it --rm -v $(pwd):/app useful_ubuntu
```

- `-it` means interactive, i.e. the container is not meant to run one action and then die
- `--rm` means to remove the container after exiting
- N.B. Local's path to be mounted needs to be an absolute path
