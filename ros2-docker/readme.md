# ROS2 Docker Project (`ros2-docker`)

This project provides a **ready-to-run ROS2 Humble environment** using Docker.\
It includes a minimal ROS2 package (`my_minimal_pkg`) with a simple **talker node**.

The project is organized so that anyone (MacOS ARM64, Linux) can run ROS2 without installing ROS2 natively.

---

## Repo Structure

```
ros2-docker/
├── docker/                  # Docker configuration
│   ├── Dockerfile
│   └── docker-compose.yml
├── ros2_ws/                 # ROS2 workspace
│   └── src/
│       └── my_minimal_pkg/  # ROS2 package
├── scripts/                 # Helper scripts
│   ├── build.sh             # Build Docker image
│   ├── run.sh               # Run container
│   └── exec.sh              # Open terminal in running container
└── README.md
```

- `docker/` → Defines the Docker image and container behavior.
- `ros2_ws/src/my_minimal_pkg/` → Cross-platform ROS2 package (C++ talker).
- `scripts/` → Easy-to-use scripts to build/run Docker.

---

## Prerequisites

- **Docker Desktop** installed (MacOS ARM64 or Linux).
- Optional: `git` to clone the repository.

---

## Quick Start

### 1. Clone the repository

```bash
git clone https://github.com/YOURUSERNAME/personal-website.git
cd personal-website/ros2-docker
```

---

### 2. Build the Docker image

```bash
./scripts/build.sh
```

- This builds an ARM64 Docker image with ROS2 Humble and sets up your workspace.
- This step is **independent of your host OS**.

---

### 3. Run the Docker container

```bash
./scripts/run.sh
```

- Starts a terminal session inside the container.
- Your ROS2 workspace (`ros2_ws`) is mounted, so edits on your host are reflected inside the container.

---

### 4. Build the ROS2 workspace

Inside the container:

```bash
cd /root/ros2_ws
colcon build --symlink-install
source install/setup.bash
```

- `colcon build` compiles your ROS2 package(s).
- `source install/setup.bash` sets up the ROS2 environment inside the container.

---

### 5. Launch ROS2 nodes

```bash
ros2 launch my_minimal_pkg minimal_nodes_launch.py
```

- Launches the **talker node**.
- You’ll see output like:

```
[INFO] [minimal_publisher]: Publishing: 'Hello from ROS2 Docker!'
```

---

## Notes

- **Cross-platform:** `my_minimal_pkg` works anywhere ROS2 is installed.
- **MacOS/Linux specific:** Only Docker and terminal commands are host-specific.
- **Persistent workspace:** Changes in `ros2_ws` are reflected immediately inside the container.

---

## ⚡ Optional: Exec into Running Container

If you already have a container running:

```bash
./scripts/exec.sh
```

- Opens a terminal inside the container without starting a new one.

---
