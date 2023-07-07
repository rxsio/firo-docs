## USB2.0 bandwidth limit

USB2.0 allows for only 500Mbit/s transfer rate and only 80% of it can be used for streaming video. This normally wouldn't be a problem, because of video compression, but webcams are dump and massively over provision the bandwidth they need.

To fix this, a [[UVC kernel patch]] is required.

## Segmentation fault with python pipelines

For an unknown reason, when a stream is started and stopped a couple of times on the frontend, the pipeline throws a segmentation fault. 

~~Strangely enough, it doesn't happen when using a pipeline started with `gst-launch`.~~
(edit: I have managed to crash a pipeline started with gst-launch when running directly with Ubuntu 23.04)

I was not able to prevent it from happening by making changes to the frontend.

The current workaround is to restart the container if the crash occurs. This leads to a ~5s break in the stream, which isn't terrible, but undesirable.

A [bug report](https://gitlab.freedesktop.org/gstreamer/gst-plugins-rs/-/issues/385) has been filed to the developers of webrtcsink .

## Hardware acceleration

Despite many efforts, I can't get hardware acceleration to work. Installing libraries for it leads to encoding failing inside webrtcsink. Hardware acceleration (under AMD) worked perfectly fine with previous setups that didn't use a docker container. This has to be investigated further.

Using the GPU inside Jetson Nano might not be possible, because nVidia released specific versions of Gstreamer modules for their hardware. Unfortunately those modules were released only for Ubuntu 18.04, which has an ancient version of Gstreamer. However, it is worth trying installing the CUDA drivers in the container and testing if it will work.