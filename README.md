# Pose-Based_Light_Control_with_Node-Red_and_Raspberry_Pi_with_AIkit

Welcome to the Pose-Based Light Control project! This repository demonstrates how to create an intelligent lighting system that responds to human poses. By leveraging the power of an AI kit for pose detection and the flexibility of Node-RED for automation, this project allows you to control smart lights based on your movements.

In this project, a USB camera captures your pose, and yolov8n run on [AI kit](https://www.seeedstudio.com/Raspberry-Pi-AI-Kit-p-5900.html) with [reComputer R1000](https://www.seeedstudio.com/reComputer-R1025-10-p-5895.html) to detect your pose. The processed video, displaying the detected pose, is then streamed in real-time to [reTerminal DM](https://www.seeedstudio.com/reTerminal-DM-LTE-Cat-4-EC25-Bundle.html) using [gstreamer](https://gstreamer.freedesktop.org/). Meanwhile, the joint coordinates are sent using [mqtt](https://mqtt.org/) to [Node-RED](https://nodered.org/) which deploy on the reComputer R1000. At last, the Node-RED flow controls the smart lights based on the joint coordinates. 

![image](./resource/pose_control.jpeg)


# Deploy this project

## Hardware Preparation

> [!Note]
> You need a USB camera connect reComputer R1000.

### [reComputer R1000](https://www.seeedstudio.com/reComputer-R1025-10-p-5895.html): Raspberry Pi CM4 Gateway, 4GB RAM, 32GB eMMC  
<div align='center'><img width={600} src='https://media-cdn.seeedstudio.com/media/catalog/product/cache/bb49d3ec4ee05b6f018e93f896b8a25d/1/-/1-113991274-recomputer-r1025-10-0.jpg'></div>

### [Raspberry Pi AI Kit](https://www.seeedstudio.com/Raspberry-Pi-AI-Kit-p-5900.html)
<div align='center'><img width={600} src='https://media-cdn.seeedstudio.com/media/catalog/product/cache/bb49d3ec4ee05b6f018e93f896b8a25d/1/-/1-113060086-raspberry-pi-ai-kit-45font.jpg'></div>

### [reTerminal DM](https://www.seeedstudio.com/reTerminal-DM-LTE-Cat-4-EC25-Bundle.html)(Only need for Raspberry Pi 5)
<div align='center'><img width={600} src='https://media-cdn.seeedstudio.com/media/catalog/product/cache/bb49d3ec4ee05b6f018e93f896b8a25d/1/-/1-sku-e23010420--reterminal-dm-_-lte-cat-4-ec25-bundle.jpg'></div>

## Install AI kit to reComputer R1000 

Please refer to this [guid](https://wiki.seeedstudio.com/yolov8_pose_estimation_on_recomputer_r1000_with_hailo_8l/)

## Install Node-RED to reComputer R1000 and run


## Install Pose_estimation and run on reComputer R1000

> [!Note]
> Please make sure your reComputer R1000 and reTerminal DM are connected to the same network.

1. Clone this repository to your reComputer R1000

```
git clone https://github.com/LJ-Hao/Pose-Based_Light_Control_with_Node-Red_and_Raspberry_Pi_with_AIkit.git && cd Pose-Based_Light_Control_with_Node-Red_and_Raspberry_Pi_with_AIkit
```

Edit the `pose_estimation.py` file and change the `mqtt_server` to your reTerminal DM's IP address. And change the Gstreamer pipeline to your reTerminal DM's IP address. And then run the command below to start the pose estimation.

```
bash run.sh pose_estimation.py
```
## Run Node-RED flow

```

```

## Install receiver and run on reTerminal DM

```
git clone https://github.com/LJ-Hao/Pose-Based_Light_Control_with_Node-Red_and_Raspberry_Pi_with_AIkit.git && cd Pose-Based_Light_Control_with_Node-Red_and_Raspberry_Pi_with_AIkit

apt-get install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-bad1.0-dev gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-tools gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-qt5 gstreamer1.0-pulseaudio
```

```
python3 video_receiver.py
```

## Result 

We showed this demonstration in a youtube live broadcast, and you can watch the video here:

[![Alt text](https://img.youtube.com/vi/v-S6_tH75NI/0.jpg)](https://www.youtube.com/watch?v=v-S6_tH75NI&t=1332s)

