# Nobara Linux
**Last tested on Nobara Linux 40 (GNOME Edition)**

[Distribution Home Page](https://nobaraproject.org/)

## Dependencies
Since Nobara ships with a more up-to-date version of python, install the latest compatible version of Python (3.10) for Stable Diffusion:

```
sudo dnf install python3.10 -y
```

## Installation
Clone the repository, using the url provided through the [official repo](https://github.com/AUTOMATIC1111/stable-diffusion-webui) (or the command below). Make sure you're in the directory (folder) that you want Stable Diffusion to be installed in. This will end up quite large, so be sure to have plenty of free space:

```
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
```

The default `webui-user.sh` file assumes that the latest version of python will work, which it (most likely) doesn't. Open and change line 16 from `#python_cmd="python3"` to the following, making sure to save.

```
python_cmd="python3.10"
```

**Note.** This simply tells the program to use `python3.10` anywhere it would normally just try `python`.

## Usage
From inside of the cloned `stable-diffusion-webui` folder, run the following command to start the program:

```
./webui.sh
```

## Troubleshooting
...
