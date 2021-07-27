# Run Tensorflow in Docker enabled with NVIDIA GPU

Assumption: You have Ubuntu 18.04 with the proper NVIDIA drivers installed.

This is simple project to play with regression using tensorflow with GPU enabled.

To enable the NVIDIA runtime with Docker

Add the NVIDIA docker repo
```
$ distribution=$(. /etc/os-release;echo $ID$VERSION_ID)    && curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -    && curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
```

```
$ sudo apt update
```

Install NVIDIA runtime for docker
```
$ sudo apt install -y nvidia-container-runtime
```

Add NVIDIA container runtime config to docker's daemon.json
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

Restart Docker
```
$ sudo systemctl restart docker
```

Run docker-compose
```
$ chmod +x run.sh
$ ./run.sh
```
