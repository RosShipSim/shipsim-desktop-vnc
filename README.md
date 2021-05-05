# shipsim-desktop-vnc

This repository is for checking shipsim platform in Docker container.

## Build

- foxy-arm64 for supporting Apple Silicon

```sh
docker build -t taiga4112/shipsim-vnc:foxy-arm64 --build-arg CACHEBUST=$(date +%s) foxy-arm64/.
```

## Run

### 1. Run and access the docker container including shipsim platform

- Run the docker container and access with port `6080`.
  - Change the `shm-size` value depending on the situation.

  ```sh
  docker run -p 6080:80 --shm-size=512m taiga4112/shipsim-vnc:foxy-arm64
  ```

- Access [localhost:6080](http://127.0.0.1:6080/)

### 2. Run shipsim in VNC

- Open a terminal and install all packages built by colcon.

```sh
cd shipsim_ws
. install/setup.bash
```

- Run a shipsim node

```sh
ros2 run shipsim shipsim_node
```
