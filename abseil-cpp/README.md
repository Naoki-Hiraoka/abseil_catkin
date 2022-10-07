# osqp-eigen

This package is deprecated because https://github.com/robotology/osqp-eigen/tree/v0.7.0 supports catkin workspaces.

```cmake
find_package(OsqpEigen REQUIRED)
catkin_package(
  DEPENDS OsqpEigen
)
target_link_libraries(${PROJECT_NAME} OsqpEigen::OsqpEigen)
```
