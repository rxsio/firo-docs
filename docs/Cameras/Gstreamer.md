Support for WebRTC in Gstreamer is new and constantly changing, so we have to adapt to the latest changes done to the module that we are using.

We are using the [webrtcsink](https://gitlab.freedesktop.org/gstreamer/gst-plugins-rs/-/tree/main/net/webrtc) node provided by the [gst-plugins-rs](https://gitlab.freedesktop.org/gstreamer/gst-plugins-rs/) project. Unfortunately, it is not shipped with Ubuntu, so we have to build it ourselves.

We are using a container with Ubuntu 23.04, because we need Gstreamer 1.22.x. Once Ubuntu 24.04 is released, we should update.

The [[Pipelines]] are managed with a python script.