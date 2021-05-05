FROM tiryoh/ros2-desktop-vnc:foxy-arm64
LABEL maintainer="Taiga MITSUYUKI<mitsuyuki-taiga-my@ynu.ac.jp>"

ENV DISTRO foxy

ENV USER ubuntu
ENV WORKDIR shipsim_ws
RUN mkdir -p /home/${USER}/${WORKDIR}/src && cd /home/${USER}/${WORKDIR}/src
WORKDIR /home/${USER}/${WORKDIR}/src


# inital set for no cache
ARG CACHEBUST=1

# set shipsim
RUN git clone --depth 1 https://github.com/ShipMMG/shipsim.git

# build
WORKDIR /home/${USER}/${WORKDIR}/
RUN . /opt/ros/${DISTRO}/setup.sh && colcon build
