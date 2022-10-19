# shipsim-desktop-vnc

This repository is for checking shipsim platform in Docker container.

## Build

### humble

```sh
docker build -t taiga4112/shipsim-vnc:humble humble/.
# docker build -t taiga4112/shipsim-vnc:humble --build-arg CACHEBUST=$(date +%s) humble/.
```

### humble-arm64 for supporting Apple Silicon

```sh
docker build -t taiga4112/shipsim-vnc:humble humble-arm64/.
# docker build -t taiga4112/shipsim-vnc:humble-arm64 --build-arg CACHEBUST=$(date +%s) humble-arm64/.
```

### foxy

```sh
docker build -t taiga4112/shipsim-vnc:foxy foxy/.
# docker build -t taiga4112/shipsim-vnc:foxy --build-arg CACHEBUST=$(date +%s) foxy/.
```

### foxy-arm64 for supporting Apple Silicon

```sh
docker build -t taiga4112/shipsim-vnc:foxy-arm64 foxy-arm64/.
# docker build -t taiga4112/shipsim-vnc:foxy-arm64 --build-arg CACHEBUST=$(date +%s) foxy-arm64/.
```

## Run

### 1. Run and access the docker container including shipsim platform

- Run the docker container and access with port `6080`.
  - Change the `shm-size` value depending on the situation.

  ```sh
  docker run -p 6080:80 --shm-size=512m taiga4112/shipsim-vnc:humble
  ```

- Access [localhost:6080](http://127.0.0.1:6080/)

### 2. Run shipsim in VNC

- Open a terminal and run shipsim view.

```sh
cd ~/shipsim_ws
. install/setup.bash
ros2 run shipsim shipsim_node
```

- Open a new terminal and run model node after running a shipsim node

```sh
cd ~/shipsim_ws
. install/setup.bash
ros2 run shipsim_kt_module model_node
```

- Open a new terminal and run controller node after running a shipsim node

```sh
cd ~/shipsim_ws
. install/setup.bash
ros2 run shipsim_kt_module controller_node
```

- Open a new terminal and run sensor node after running a shipsim node

```sh
cd ~/shipsim_ws
. install/setup.bash
ros2 run shipsim_sensor_module simulated_sensor_node
```

- Open a new terminal and run actuator node after running a shipsim node

```sh
cd ~/shipsim_ws
. install/setup.bash
ros2 run shipsim_actuator_module simulated_actuator_node
```
