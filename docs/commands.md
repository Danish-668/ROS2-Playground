## ROS 2 C++ 

### 1. Create Package

```bash
ros2 pkg create --build-type ament_cmake <package_name> --dependencies rclcpp std_msgs
```

### 2. Add Source File

```bash
touch <package_name>/src/<file_name>.cpp
```

### 3. Update `CMakeLists.txt`

```cmake
add_executable(<exec_name> src/<file_name>.cpp)
ament_target_dependencies(<exec_name> rclcpp std_msgs)
install(TARGETS <exec_name> DESTINATION lib/${PROJECT_NAME})
```

### 4. Update `package.xml`

```xml
<depend>rclcpp</depend>
<depend>std_msgs</depend>
```

### 5. Build

```bash
colcon build --packages-select <package_name> --parallel-workers 4
```

### 6. Source Setup

```bash
source install/setup.bash
```

### 7. Run Node

```bash
ros2 run <package_name> <exec_name>
```