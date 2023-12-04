## Nvidia Jetson Nano

### Step 1: Download kernel source for the current system

The current newest official release for Jetson Nano is R32.7.4. The downloads page for this version can be found [here](https://developer.nvidia.com/embedded/linux-tegra-r3274). The sources can be downloaded using the [Driver Package (BSP) Sources](https://developer.nvidia.com/downloads/embedded/l4t/r32_release_v7.4/sources/t210/public_sources.tbz2) link.

```bash
wget https://developer.nvidia.com/downloads/embedded/l4t/r32_release_v7.4/sources/t210/public_sources.tbz2
```

### Step 2: Extract sources

Inside of the downloaded file, you will find a file called `Linux_for_Tegra/source/public/kernel_src.tbz2`. Extract it into a new folder

### Step 3: Apply patches

You can find the original patches for this trick [here](https://www.spinics.net/lists/linux-media/msg175596.html).

The files you have to modify will be in the folder `kernel/kernel-4.9/drivers/media/usb/uvc`.

Don't include lines related to `uvc_trace`, it doesn't work anymore.

### Step 4: Build & install

Inside of the `uvc` folder, in which you have modified the source files, run:

```bash
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo make -C /lib/modules/$(uname -r)/build M=$(pwd) modules_install
```

### Step 5: Load patched module

In order to reload the uvc module without restarting the system, run

```bash
sudo depmod
sudo modprobe -r uvcvideo
```

### Step 6: Verify

To check if everything had gone correctly, run

```bash
sudo modprobe -v uvcvideo
```

You should see

```
insmod /lib/modules/4.9.337-tegra/extra/uvcvideo.ko
```

And if you run

```
cat /sys/module/uvcvideo/parameters/bandwidth_cap
```

You should get

```
0
```

### Step 7: Configuring

Unfortunately, the bandwidth limit is not described in a unit that can easily be measured and the author of the patch recommends using the highest limit that doesn't throw errors in your application. 

I've found that `2000` works quite well for 5 MJPEG FullHD streams.

In order to set a new bandwidth cap, run

```
echo 2000 | sudo tee /sys/module/uvcvideo/parameters/bandwidth_cap
```

This value is value does not seem to be preserved and will need to be reset at each system boot.

### Step 8: Automatically setting the cap

TBD