# [AUTOMATIC1111/stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui) for Fedora-Based Distros
**A guide for NVIDIA and AMD GPUs**

Fedora is tailored more towards FOSS software, so there can be some issues when it comes to NVIDIA. I personally use [Nobara](https://nobaraproject.org/) because it includes tons of compatibility fixes on top of Fedora. In this guide, I'll be using "Nobara" instead of Fedora, as that is where I've tested these changes more thoroughly.

## NVIDIA on Fedora
Enable rpmfusion-nonfree in your software center, and then install the latest proprietary NVIDIA drivers. This guide was created with the 555.52.04 driver version.

## Dependencies
Stable Diffusion **requires** Python 3.10, and Nobara has moved beyond this. Use the following command to get the proper version on your system.

```
sudo dnf install python3.10
```

Minimal Fedora may not come with some required packages. Make sure you also have `pciutils` and `gperftools` installed. If you have an AMD gpu, you should also have `lspci`.

For easy installation and updates, make sure you have `git` installed.

## Git Cloning and Setup
Clone the repository, using the url provided through the [official repo](https://github.com/AUTOMATIC1111/stable-diffusion-webui) or the command below. Make sure you're in the directory (folder) that you want it to be installed in. This will be large, so have plenty of space:

```
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
```

The default `webui-user.sh` file assumes that the latest version of python will work, which it won't. Open and change line 16 from `#python_cmd="python3"` to the following, making sure to save.

```
python_cmd="python3.10"
```

**Note.** This simply tells the program to use `python3.10` anywhere it would normally just try `python`.

## Usage
From inside of the cloned `stable-diffusion-webui` folder, run the following command to start the program:

```
./webui.sh
```

And it's running!

Well, it's going to start downloading the different models it uses as defaults. This could take a bit, so you may as well read the following section while you wait, it'll automatically start when it's done. BTW, it won't have to do this again and starts up pretty quick.

After it's done though, try out the following prompt! It's sort of like a "Hello world!" of image generation

```
photograph of an astronaut riding a horse
```

## Performance
While the default settings are generally decent, there may be some small tweaks to make to the start command, depending on your situation.

**General Optimization.** NVIDIA gpus should use `--xformers`, while AMD gpus should use `--opt-sub-quad-attention`. There's not a lot of reason to *not* use them.

**Older GPUs.** `--no-half` and `--upcast-sampling` typically should fix issues if the ouput images are just solid green or black.

**Running out of VRAM.** `--medvram` applies some memory optimizations. May result in slightly slower render times.

If you want to always use your arguments without forgetting them, just add the arguments to the webui-user.sh file, as the COMMANDLINE_ARGS variable. I use the following:

```
# Commandline arguments for webui.py...
export COMMANDLINE_ARGS="--xformers --medvram --no-half --upcast-sampling"
```

This way, it's always set up the way you like it.
