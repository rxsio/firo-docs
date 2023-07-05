## Dependencies

Unfortunately, this container depends on a lot of libraries, which leads to a significant image size, but none of them seem avoidable.
 - `vim` is useful for quickly patching files 
 - `git curl` are necessary for downloading rust and gst-plugins-rs
 - `python3-yaml python3-pyudev python3-psutil udev` are necessary for the pipeline python script
 - `build-essential libssl-dev libx264-dev libvpx-dev libopus-dev` are necessary for building gst-plugins-rs
 - `ibnice-dev gstreamer1.0-nice` these aren't mentioned anywhere in the docs and no errors show it is missing, but it is necessary for webrtcsink to function at all
 - `libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-good1.0-dev libgstreamer-plugins-bad1.0-dev gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav` these are basic gstreamer dependencies, maybe some of them could be removed
 - `gstreamer1.0-tools python3-gst-1.0` are necessary for starting pipelines
 
Additionally, we might need to add `mesa-va-drivers gstreamer1.0-vaapi va-driver-all` for hardware accelerated video decoding, but currently it doesn't work at all.

## Build stages

## Interfaces

The config file is loaded from `./config/config.yaml` relative to the folder where the repository has been cloned.

The signaler server runs on port `8443` which is mapped to the same port on the host machine.

In order to allow udev and pyudev to work properly, folders `/dev` and `run/udev` have to be mapped from the host machine. Setting the `network_mode` to `host` is required as well for some reason.

The container is privileged to give it full hardware access.

The `restart: unless-stopped` clause is part of the workaround for the pipeline crashing issue, but it is a failsafe as well.