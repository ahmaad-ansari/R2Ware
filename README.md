# R2Ware

## R2: Multi-Machine Communication

Run the following commands on the R2's local machine to enable communication with a ground station on the same network:

```bash
sudo ip link set lo multicast on
sudo ufw disable
```

You can check the status of the firewall with the following command:

```bash
sudo ufw status
```

## Getting Started

Clone the R2Ware repository and navigate into the project directory:

```bash
git clone https://github.com/ahmaad-ansari/r2ware.git ~/
cd r2ware
```

## Initializing Workspace

Create the `src` directory and import the necessary repositories:

```bash
mkdir src
vcs import src < r2ware.repos
```

## Setting Up Docker

Run the provided script to set up Docker for the R2Ware environment:

```bash
./run_docker.sh
cd ~/r2ware
```

## Installing Dependencies

Install ROS dependencies using `rosdep`:

```bash
rosdep install -y --from-paths src --ignore-src --rosdistro $ROS_DISTRO
```

## Building the Workspace

Build the R2Ware workspace using `colcon`:

```bash
colcon build --symlink-install
```

Or build specific packages
```bash
colcon build --symlink-install --packages-select r2ware_control
```
```bash
colcon build --symlink-install --packages-select r2ware_sensing
```
```bash
colcon build --symlink-install --packages-select r2ware_launch
```

## R2: Multi-Machine Communication

Run the following commands while inside the R2's Docker container to enable communication with a ground station on the same network:

```bash
apt update
apt install -y ros-foxy-fastrtps
```

## Ground Station: Multi-Machine Communication

Run the following commands on the ground station running Autoware:

```bash
sudo ufw disable
sudo ip link set lo multicast on
sudo apt-install -y ros-humble-fastrps
```

Set the followiwng environment variablesto enable ROS 2 communication:

```bash
export ROS_LOCALHOST_ONLY=0
export ROS_DOMAIN_ID=32
```

Now, your R2Ware workspace is set up and ready for use. Refer to specific documentation for further details on running and utilizing R2Ware functionalities.
