FROM tiryoh/ros2-desktop-vnc:foxy
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

# set package except for the targets of colcon build
# set shipsim_controller-ui
RUN git clone --depth 1 https://github.com/ShipMMG/shipsim_control_msgs.git
RUN git clone --depth 1 https://github.com/ShipMMG/shipsim_control_module.git

# build
WORKDIR /home/${USER}/${WORKDIR}/
RUN . /opt/ros/${DISTRO}/setup.sh && colcon build