---
title: Writing ROS packages

version: 1.0.0
date: 12.09.2024
authors:
  - Gabriel Brzeziński, gabriel@gabrielb.dev
---

## Development Environment

We've prepared a VS Code workspace with a devcontainer, which includes a pre-configured ROS2 workspace and all recommended development tools (linters, formatters, etc.). You can find it [here](https://github.com/rxsio/firo-ros2-workspace).

### Prerequisites

Before you start, make sure you have the following installed:

- Docker
- VS Code
- The *Remote Development* plugin in VS Code

Additionally, configure Docker to [run without sudo](https://docs.docker.com/engine/install/linux-postinstall/) (you may need to restart your PC for these changes to take effect).

### Cloning the Workspace

Clone our workspace from the [repository](https://github.com/rxsio/firo-ros2-workspace) and open it in VS Code. Ensure that the *Remote Development* plugin is installed and enabled. When you first open the workspace, VS Code should prompt you to reopen the folder in a container (*Reopen in Container*). If you missed the prompt, use `Ctrl + Shift + P`, search for `Dev Containers: Reopen in Container`, and select it. Once successful, you’ll see a small *Dev Container* label in the lower left corner of VS Code. 

If you run into issues, check the setup instructions in this [repository](https://github.com/athackst/vscode_ros2_workspace?tab=readme-ov-file), which is the baseline for our environment and has more comprehensive setup instructions.

### Workflow

Explore our predefined tasks in VS Code. Use `Ctrl + Shift + B` to run `colcon build` and fully build the workspace. You can also use `Ctrl + Shift + P`, search for `Tasks: Run Task`, and explore other tasks, such as building with debug or release settings, installing dependencies with rosdep, or creating new packages.

Pay close attention to any warnings or errors during development, especially those from linters (for C++), which help enforce good coding practices. If you're new to programming, don’t follow warnings blindly. Each one is an opportunity to learn. Look up any unfamiliar warnings to understand their purpose.


### General Guidelines

- When working on a feature, create a feature branch and open a pull request for merging into the release (*humble*) branch.
- Make small, atomic commits to simplify reviews.
- Use [conventional git commit messages](https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13).


## Creating Your Own Package

### Choosing the Right Repository

Start by selecting the appropriate repository to host your package. Typically, it will be one of the following:

- [firo_common](https://github.com/rxsio/firo_common) for packages used on both the rover and in simulation
- [firo_robot](https://github.com/rxsio/firo_robot) for rover-specific packages
- [firo_simulator](https://github.com/rxsio/firo_simulator) for simulation-specific packages

If your package is more general or can be used with other robots, create a separate repository and add it as a submodule to one of the above repositories.

### Defining Interfaces

When your ROS node uses topics, services, or actions, avoid creating custom message types unless absolutely necessary, as this makes your node incompatible with already existing packages. Always check for suitable message types in [ROS common_interfaces](https://github.com/ros2/common_interfaces) or other published [ROS packages](https://index.ros.org/). If nothing appropriate is found, you can explore unpublished community packages (e.g., on GitHub). Only create a custom message if no suitable message exists, and always place new message definitions in a separate package.

It's important to use message types that are semantically correct and have the appropriate units. Your usage doesn’t have to strictly follow the message description, but it must align with the message’s intended semantics and units to avoid confusion for other developers. If no existing message type fits your needs, it's better to create a new one than to misuse an existing message.

Additionally, follow conventions when defining ROS parameters or choosing topic names. For example, the robot description in ROS2 is typically stored in the `~robot_description` parameter and published to the `/robot_description` topic. While many standards are documented in [REPs](https://ros.org/reps/rep-0000.html), a lot of conventions are community-driven and learned through experience or by studying other packages.

### Adding New Dependencies

Whenever you introduce new dependencies to a package, make sure they can be installed via rosdep. After adding dependencies, update the `package.xml` file accordingly.

If a library you need isn’t available via rosdep and is small, consider including it in your package as a submodule. For ROS packages not available via rosdep, add them as submodules to the appropriate repository (*firo_common*, *firo_robot*, or *firo_simulator*).

### Launch Files

When adding new functionality (e.g., nodes or configurations) to a package, consider updating or adding launch files. For parameter management, prefer loading parameters from YAML files rather than hardcoding them into the launch file.

### License

Use Apache 2.0 unless required otherwise by your package dependencies.

### Documentation

Document your package in a `Readme.md` file within the package. At a minimum, the README should clearly state the package’s purpose, describe all nodes and their interfaces (subscribed and published topics, services, actions), and list all parameters.
