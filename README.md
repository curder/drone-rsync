# drone-rsync
[![drone-rsync on Docker Hub](https://img.shields.io/docker/automated/curder/drone-rsync.svg)](https://hub.docker.com/r/curder/drone-rsync/)

This is a pure Bash [Drone](https://github.com/drone/drone) >= 0.5 plugin to sync files to remote hosts.

For more information on how to use the plugin, please take a look at [the docs](https://github.com/curder/drone-rsync/blob/master/DOCS.md).

## Docker
Build the docker image by running:

```bash
docker build --rm=true -t curder/drone-rsync:latest .
```

For Apple Silicon or other arm-based CPUs, use the `--platform linux/arm64` option.

## Usage
Execute from the working directory (assuming you have an SSH server running on 127.0.0.1:22):

```bash
docker run --rm \
  -e PLUGIN_KEY=$(cat some-private-key) \
  -e PLUGIN_HOSTS="127.0.0.1, 127.0.0.2, 127.0.0.3" \
  -e PLUGIN_PORTS="22, 23, 24" \
  -e PLUGIN_TARGET="./" \
  -e PLUGIN_PRESCRIPT="echo \"Prescript Done!\"" \
  -e PLUGIN_SCRIPT="echo \"Postscript Done!\"" \
  -e PLUGIN_ARGS="--blocking-io" \
  -v $(pwd):$(pwd) \
  -w $(pwd) \
  curder/drone-rsync
```

## Mirrors

- Aliyun

  `registry.cn-hangzhou.aliyuncs.com/curder/drone-rsync`
  
- Github

    `ghcr.io/curder/drone-rsync`
