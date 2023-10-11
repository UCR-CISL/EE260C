# EE260C

## Carla Docker Image
We have a customly built docker image that contains
- base image: nvidia/vulkan:1.3-470 (ubuntu 20.04, python 3.8)
- cuda 11.4
- carla 0.9.13

#### Getting the docker image
Build the docker locally
```commandline
sudo docker build -t hangqiu/carla:0.9.13 --file ./carla.Dockerfile .
```
Or, pull the docker from hub
```commandline
sudo docker pull hangqiu/carla:0.9.13
```

#### Run carla simulator
Run the carla server
```commandline
sudo docker run --privileged --gpus all --net=host -e DISPLAY=$DISPLAY \
    -v /usr/share/vulkan/icd.d:/usr/share/vulkan/icd.d \
    hangqiu/carla:0.9.13 \
    /bin/bash /opt/carla-simulator/CarlaUE4.sh
```
And run carla client with manual control
```commandline
sudo docker run -it --privileged --gpus all --net=host -e DISPLAY=$DISPLAY \
    -v /usr/share/vulkan/icd.d:/usr/share/vulkan/icd.d \
    hangqiu/carla:0.9.13 \
    /bin/python3 /opt/carla-simulator/PythonAPI/examples/manual_control.py 
```

