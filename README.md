This is a fork from https://github.com/deepfakes/faceswap.

# Installation
- I focused on docker method for installation. To do so, I corrected Dockerfile.gpu for compatibility between CUDA and Tensorflow.
- I also modified Dockerfile.gpu for using ZJU mirrors and a proxy to break GFW.

# Launch
- GUI mode
```
#!/bin/bash
xhost +local:
nvidia-docker run -it --gpus all --rm --name faceswap.gui -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix -v myhome/faceswap/:/faceswap/ -v myhome/notebooks/:/notebooks/ deepfakes-gpu python3.8 /faceswap/faceswap.py gui

```

- jupyter notebook
```
#!/bin/bash
nvidia-docker run --gpus all -d --rm --name fs.nb -v myhome/faceswap/:/faceswap/ -v myhome/notebooks/:/notebooks/ -p 18000:8888 deepfakes-gpu jupyter-notebook --ip 0.0.0.0 --NotebookApp.token=the_password --allow-root
```

