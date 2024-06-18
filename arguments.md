# Arguments
Arguments specify which adjustments need to be used when you run the project. They can be found inside of the `webui-user.sh` file, typically as the following:

```
# Commandline arguments for webui.py...
# export COMMANDLINE_ARGS=""
```

On a fresh install, the quotes are empty. If you [find some command-line arguments](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Optimizations) that you want to try out, just *uncomment* the export line by removing the `#`, and adding the arguments between the quotes with spaces separating:

```
export COMMANDLINE_ARGS="--xformers --medvram --no-half --upcast-sampling"
```

Going forward, every time you run ./webui.sh, It'll use these arguments.
