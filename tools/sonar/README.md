# SonarQube

## SonarQube in docker
> When starting for the first time and an error occurs during initiation just start SonarQube service again. 

### Requirements

- vm.max_map_count is greater than or equal to 524288
- fs.file-max is greater than or equal to 131072
- the user running SonarQube can open at least 131072 file descriptors
- the user running SonarQube can open at least 8192 threads

- Check values:
  ```
  sysctl vm.max_map_count
  sysctl fs.file-max
  ulimit -n
  ulimit -u
  ```
- Set values:
  ```
  sysctl -w vm.max_map_count=524288
  sysctl -w fs.file-max=131072
  ulimit -n 131072
  ulimit -u 8192
  ```
- To set permanently add following lines in `/etc/sysctl.conf`
  ```
  vm.max_map_count=524288
  fs.file-max=131072
  ```
  - Reload configuration:
    ```
    sudo sysctl -p
    ```

### Control Environment
- Start environment
  ```
  docker-compose up -d
  ```
- Stop environment
  ```
  docker-compose down
  ```
- Reset environment
  ```
  docker-compose down -v
  ```
- Show logs
  ```
  docker-compose logs -f
  ```