---
title: Repository Structure

version: 0.1.0
date: 15.08.2024
authors:
  - Patryk Filip Gryz, pfgryz@gmail.com
---

## Naming Conventions

Repositories should be appropriately named to reflect their purpose. For repositories containing universal projects, avoid including the project name in the repository name.

## Git Branching Strategy

This strategy standardizes repository work, reduces error risks and issues, and shortens deployment time for new projects.

- `main` - this branch holds the latest development changes and produces `nigtly` builds
- `release` - holds `stable` and versioned releases
- `feature/<feature-name>` - used to develop new features or enhancements

For ROS2-related repositories:
- `<ros2_version>` - for repositories related to ROS2, branches named with a ROS2 version (e.g., humble, foxy) are treated as releases corresponding to that specific ROS2 version
- `backport/<version>` - used to apply changes from the main branch to specific ROS2 version branches.

!!! note
    For documentation repositories, the release branch is not used. Instead, the `main` branch serves as the deployable documentation.

**CI/CD Practices:**
- automatic CI should be set up for stable, nightly, and tagged branches, typically producing the appropriate Docker images.
- direct work on the `release` branch should be avoided; all changes should occur through `main` or appropriate `feature` or `backport` branches.

## Continuous Integration (CI)

- repositories should have CI/CD configured to:
  - verify that the project builds correctly (for pull requests)
  - build the project and publish results, such as Docker images
  - use tagging conventions in Docker images according to the branching strategy