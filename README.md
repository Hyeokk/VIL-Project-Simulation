
# Clearpath Simulator (Customized)

This repository is based on the `humble` branch of the [Clearpath Robotics simulation repository](https://github.com/clearpathrobotics/clearpath_simulator) and has been customized to fit specific requirements.

## Key Modifications

### 1. Fix: Solar Farm World Resource Loading
Resolved an issue where resources (meshes, etc.) for the `solar_farm` world were not found in the ROS 2 Humble environment.
- **`clearpath_gz/CMakeLists.txt`:** Updated to ensure `meshes` and `geotif` directories are installed during the build process.
- **`clearpath_gz/launch/gz_sim.launch.py`:** Updated to explicitly add the `meshes` path to the `IGN_GAZEBO_RESOURCE_PATH` environment variable.

### 2. Configuration Improvements
- **`CMakeLists.txt`:** Added missing installation paths required for the Humble environment.
- **Launch Files:** Added environment variable setup to ensure Gazebo correctly locates resources.

## Installation and Build

To build this package, run the following commands:

```bash
cd ~/clearpath_ws
colcon build --packages-select clearpath_gz --symlink-install
source install/setup.bash
```

## Usage

### Basic Simulation Launch
To launch the simulation with the default settings:

```bash
ros2 launch clearpath_gz simulation.launch.py
```

### Launching the Solar Farm World
```bash
ros2 launch clearpath_gz simulation.launch.py world:=solar_farm
```

### Changing the Vehicle Control Topic (Optional)
To change the default control topic (`/a200_0000/cmd_vel`) to a custom topic name, use the remapping option:

```bash
ros2 launch clearpath_gz simulation.launch.py --remap /a200_0000/cmd_vel:=/my_topic/cmd_vel
```

## References
- Original Repository: [https://github.com/clearpathrobotics/clearpath_simulator](https://github.com/clearpathrobotics/clearpath_simulator)