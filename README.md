# EE260C

## Carla Docker Image
We have a customly built docker image that contains
- ubuntu 20.04
- cuda 11.4 (with vulkan)
- python 3.7
- carla 0.9.13

To pull the docker from hub, run
```commandline
sudo docker pull hangqiu/carla:0.9.13
```

To run the carla server, run
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

To build the docker locally, run
```commandline
sudo docker build -t hangqiu/carla:0.9.13 --file ./carla.Dockerfile .
```