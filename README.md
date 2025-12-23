# Docker-free5GC 

This repository is a docker compose version of [free5GC](https://github.com/free5gc/free5gc) for stage 3. It's inspired by [free5gc-docker-compose](https://github.com/calee0219/free5gc-docker-compose) and also reference to [docker-free5gc](https://github.com/abousselmi/docker-free5gc).

You can setup your own config in [config](./config) folder and [docker-compose.yaml](docker-compose.yaml)

## Prerequisites

- [GTP5G kernel module](https://github.com/free5gc/gtp5g): needed to run the UPF (Currently, UPF only supports GTP5G versions 0.9.5 (use git clone --branch v0.9.5 --depth 1 https://github.com/free5gc/gtp5g.git).)
- [Docker Engine](https://docs.docker.com/engine/install): needed to run the Free5GC containers
- [Docker Compose v2](https://docs.docker.com/compose/install): needed to bootstrap the free5GC stack

**Note: AVX for MongoDB**: some HW does not support MongoDB releases above`4.4` due to use of the new AVX instructions set. To verify if your CPU is compatible you can check CPU flags by running `grep avx /proc/cpuinfo`. A workaround is suggested [here](https://github.com/free5gc/free5gc-compose/issues/30#issuecomment-897627049).

## Start free5gc

Because we need to create tunnel interface, we need to use privileged container with root permission.

### Run free5GC

You can create free5GC containers based on local images or docker hub images:

```bash
# use images from docker hub
docker compose -f docker-compose.yaml up -d
```

Destroy the established container resource after testing:

```bash
# Remove established containers (remote images)
docker compose -f docker-compose.yaml rm
```

## Troubleshooting

Please refer to the [Troubleshooting](./TROUBLESHOOTING.md) for more troubleshooting information.


## Reference

- https://github.com/open5gs/nextepc/tree/master/docker
- https://github.com/abousselmi/docker-free5gc
