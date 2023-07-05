## Basics

Our camera system is based around the [[Gstreamer]] framework, which allows for easy adaptation to new hardware, gives us good performance and widely supported.

Video is provided by various USB webcams communicating using the v4l2 libraries in Linux.

The streams are delivered to the user using WebRTC and displayed in the `robot-web-interface`

The entire system is running inside of a [[Docker container]] for easy portability and stable deployment (which has been a major issue in the past).

## Structure

The camera system is separated into 3 components working together
- The `robot-web-interface` displaying streams
- The signaling server coordinating the webrtc streams
- The python script `pipelines.py` automatically detecting cameras and starting gstreamer pipelines, which connect to the signaling server 

Currently, the docker is running the default frontend from [gstwebrtc-api](https://gitlab.freedesktop.org/gstreamer/gst-plugins-rs/-/tree/main/net/webrtc/gstwebrtc-api) as a fallback for testing, but it will be removed in the future.