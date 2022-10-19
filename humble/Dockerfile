FROM tiryoh/ros2-desktop-vnc:humble
LABEL maintainer="Taiga MITSUYUKI<mitsuyuki-taiga-my@ynu.ac.jp>"

ENV DISTRO humble

ENV USER ubuntu
ENV WORKDIR shipsim_ws
RUN mkdir -p /home/${USER}/${WORKDIR}/src && cd /home/${USER}/${WORKDIR}/src
WORKDIR /home/${USER}/${WORKDIR}/src


# inital set for no cache
ARG CACHEBUST=1

# set shipsim packages
RUN git clone --depth 1 https://github.com/ShipMMG/shipsim_view.git
RUN git clone --depth 1 https://github.com/ShipMMG/shipsim_kt_module.git
RUN git clone --depth 1 https://github.com/ShipMMG/shipsim_mmg_module.git
RUN git clone --depth 1 https://github.com/ShipMMG/shipsim_msgs_module.git
RUN git clone --depth 1 https://github.com/ShipMMG/shipsim_sensor_module.git
RUN git clone --depth 1 https://github.com/ShipMMG/shipsim_actuator_module.git

# python library for running shipsim
RUN curl http://repo.ros2.org/repos.key | sudo apt-key add -
RUN apt-get update -q && \
    apt-get upgrade -yq && \
    apt-get install -yq python3-dev python3-pip python3-venv && \
    rm -rf /var/lib/apt/lists/*
RUN pip install pandas

# build
WORKDIR /home/${USER}/${WORKDIR}/
RUN . /opt/ros/${DISTRO}/setup.sh && colcon build
