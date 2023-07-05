## Automatic camera detection

The [pyudev](https://pypi.org/project/pyudev/) library is used to allow for hotplug support. Cameras are detected by filtering out events that come from the `v4l2` subsystem. 

## Camera configuration

The configuration file is loaded from a file external to the container, so the image doesn't need to be rebuilt to update the config. 

Cameras are identified by the USB port id. It would be preferable to use camera serial ids, but unfortunately manufacturers don't bother with making them unique.

### Default config
When there is no config for a particular port, the camera appears in the interface with its USB port id as the default name. The default config is printed to the console, so it can be easily copied into the config file and modified accordingly.

The default config assumes the camera supports 720p video at 25fps with mjpeg compression. If this isn't true, an undefined behavior will occur.

## Encoding

The USB bandwidth is greatly limited (see [[Known issues]]), so we should always choose the best compression option the camera offers (H264 > MJPEG > YUV)

The [webrtcsink](https://gitlab.freedesktop.org/gstreamer/gst-plugins-rs/-/tree/main/net/webrtc) module is dynamically adjusting the bitrate and encoding the stream for each user, so our pipelines have to decode the video to `video/x-raw` for the system to work.

The [webrtcsink](https://gitlab.freedesktop.org/gstreamer/gst-plugins-rs/-/tree/main/net/webrtc) module supposedly allows for H264 encoded input, which might be desirable with some cameras. However, I was not able to make it work, so I decode the stream before handing it off. It might be a good idea to explore this feature in the future.