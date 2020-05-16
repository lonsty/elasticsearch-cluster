## Requirements

### Set `vm.max_map_count` to at least `262144`

The `vm.max_map_count` kernel setting must be set to at least `262144` for production use.

How you set `vm.max_map_count` depends on your platform:

# Linux

The `vm.max_map_count` setting should be set permanently in `/etc/sysctl.conf`:

```shell
grep vm.max_map_count /etc/sysctl.conf
vm.max_map_count=262144
```

To apply the setting on a live system, run:

```shell
sysctl -w vm.max_map_count=262144
```

# macOS with Docker for Mac

The `vm.max_map_count` setting must be set within the xhyve virtual machine:

a. From the command line, run:

```shell
screen ~/Library/Containers/com.docker.docker/Data/vms/0/tty
```

b. Press enter and use`sysctl` to configure vm.max_map_count:

```shell
sysctl -w vm.max_map_count=262144
```

c. To exit the screen session, type Ctrl a d.

# Windows and macOS with Docker Desktop

The `vm.max_map_count` setting must be set via docker-machine:

```shell
docker-machine ssh
sudo sysctl -w vm.max_map_count=262144
```

## Start

```shell
docker-compose up -d
```
