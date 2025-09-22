# Start with a base ROS2 image for ARM64
FROM arm64v8/ros:humble-ros-core

# Avoid prompts during package install
ENV DEBIAN_FRONTEND=noninteractive

# Install ROS2 build tools and C++ demo packages
RUN apt-get update && apt-get install -y \
    build-essential \
    cmake \
    python3-colcon-common-extensions \
    ros-humble-demo-nodes-cpp \
    && rm -rf /var/lib/apt/lists/*

# Set workspace directory WORKDIR /root/ros2_ws
