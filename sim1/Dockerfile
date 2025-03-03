# Use the official Ubuntu 24.04 base image
FROM ubuntu:24.04

# Set environment variables to avoid interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Enable the Universe repository
RUN apt-get update && apt-get install -y \
    software-properties-common \
    && add-apt-repository universe \
    && apt-get update
    
# install basic dependencies
RUN apt-get install -y \
    curl \
    gnupg2 \
    lsb-release \
    && rm -rf /var/lib/apt/lists/*

# Add ROS 2 repository to the system
RUN curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
RUN echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# Install development tools
RUN apt update && sudo apt install -y \
  python3-flake8-blind-except \
  python3-flake8-class-newline \
  python3-flake8-deprecated \
  python3-mypy \
  python3-pip \
  python3-pytest \
  python3-pytest-cov \
  python3-pytest-mock \
  python3-pytest-repeat \
  python3-pytest-rerunfailures \
  python3-pytest-runner \
  python3-pytest-timeout \
  ros-dev-tools

RUN apt-get install -y git wget curl nano mercurial
