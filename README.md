# docker-tensorflow-regression
Simple project to play with regression using tensorflow with GPU enabled.

To enable nvidia runtime with Docker

```
$ distribution=$(. /etc/os-release;echo $ID$VERSION_ID)    && curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -    && curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
```

```
$ sudo apt update
```

```
$ sudo apt install -y nvidia-docker2
$ sudo apt install -y nvidia-container-toolkit
$ sudo apt install -y nvidia-container-runtime
```

```
$ sudo tee /etc/docker/daemon.json <<EOF
{
    "runtimes": {
        "nvidia": {
            "path": "/usr/bin/nvidia-container-runtime",
            "runtimeArgs": []
        }
    }
}
EOF
```

```
$ sudo systemctl restart docker
```