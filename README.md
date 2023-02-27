# Deepstream 5.1 YOLOv4 App

In the modern world, the role of railway network is an essential for the people around the world. The railway system consists of infrastructure, development and maintenance. The infrastructure of the railway network is the planning and construction of the rail tracks and establishing their contacts in railway junction. The development of the railway network isused to extent the tracks to the rural and interior areas of the village. The presence of person in the rail tracks threatens the safety of people transportation. The warnings shouldbe given to the relevant units after it is determined whether the person in this rail track cause to an accident or not. It is aimed to prevent the accidents that may be experienced by
using the image processing techniques in order to detect by how far the person is located on railway track.
This app, built on Nvidia's Deepsteam SDK, would also help metro, railway station to detect and save person life. 

![person_on_track](resource/person_on_track.png)

## Index

1. [Introduction] (#Introduction)

2. [Deepstream Setup](#Deepstream-Setup)
    1. [Install System Dependencies](#Install-System-Dependencies)
    2. [Install Deepstream](#Install-Deepstream)
3. [Running the Application](#Running-the-Application)
    1. [Clone the repository](#Cloning-the-repository)
    2. [Download the weights file](#download-the-weights-file)
    3. [Build the application](#build-the-application)
    4. [Run with different input sources](#Run-with-different-input-sources)
4. [Citations](#citations)

## Introduction

An Intelligent Video Analytics Pipeline powered by Deepstream and NVIDIA Jetson Xavier NX. 

![Jetson](resource/jetson.jpg)

This project is a proof-of-concept, trying to detect a Fallen person.

## Deepstream Setup

This post assumes you have a fully functional Jetson device. If not, you can refer the documentation [here](https://docs.nvidia.com/jetson/jetpack/install-jetpack/index.html).

### 1. Install System Dependencies

```sh
sudo apt install \
libssl1.0.0 \
libgstreamer1.0-0 \
gstreamer1.0-tools \
gstreamer1.0-plugins-good \
gstreamer1.0-plugins-bad \
gstreamer1.0-plugins-ugly \
gstreamer1.0-libav \
libgstrtspserver-1.0-0 \
libjansson4=2.11-1
```

### 2. Install Deepstream

Download the DeepStream 5.1 Jetson Debian package `deepstream-5.1_5.1.0-1_arm64.deb`, to the Jetson device from [here](https://developer.nvidia.com/deepstream-getting-started). Then enter the command:

```sh
sudo apt install deepstream-5.1_5.1.0-1_arm64.deb
```

For more information, go to the get started page of Deepstream [here](https://docs.nvidia.com/metropolis/deepstream/dev-guide/index.html).

## Running the Application

### 1. Clone the repository

This is a straightforward step, however, if you are new to git, I recommend glancing threw the steps.

First, install git

```sh
sudo apt install git
```

Next, clone the repository

```sh
# Using HTTPS
https://github.com/Rani445-eng/person_on_track.git
# Using SSH
git@github.com:Rani445-eng/person_on_track.git
```

### 2. Download the weights file

Download the weights file from [google-drive](https://drive.google.com/file/d/1nZds8loc4XdG4KQGdgoU-xyOgwJqv9m-/view?usp=sharing) and place it in `models/YOLOv4` directory.

### 3. Build the application

First, build the application by running the following command:

```sh
make clean && make -j$(nproc)
```

This will generate the binary called `person_on_track`. This is a one-time step and you need to do this only when you make source-code changes.

### 4. Run with different input sources

Next, create a file called `inputsources.txt` and paste the path of videos or rtsp url.

```sh
file:///home/zxcv/Downloads/specialization.mp4
rtsp://admin:admin%40123@192.168.1.1:554/stream
```

Now, run the application by running the following command:

```sh
./person_on_track
```

## Citations

* [AlexeyAB/darknet](https://github.com/AlexeyAB/darknet)
* [AkashJames](https://github.com/kn1ghtf1re/YOLOv4-Deepstream)


Please find the Links of a Demo video, [here](https://youtu.be/GVjTWlIyKeQ)
