#  Jetson Xavier Tutorials


The NVIDIA® Jetson AGX Xavier™ Developer Kit provides a full-featured development platform designed to get you up and running quickly. The included carrier board
exposes many standard hardware interfaces, enabling a highly flexible and extensible platform for rapid prototyping. NVIDIA JetPack SDK supports both your developer kit and host development platform.

## Table of Contents

1. [Intent](#Intent)
2. [Hardware](#hardware)
3. [Software](#Software)
4. [Setting up Docker](#setting-up-docker)
5. [Identify Jetson Board](#identify-jetson-board)


## Intent:

The intention with this project repository is to help you get started with NVIDIA Jetson AGX Xavier system.

Jetson AGX Xavier module with thermal solution:

-  Reference carrier board
- 65W power supply with AC cord
- Type C to Type A cable (USB 3.1 Gen2)
- Type C to Type A adapter (USB 3.1 Gen 1)


## Hardware :

|Items        |   Link        | Reference  |
| ------------- |:-------------:| -----:|
| NVIDIA Jetson AGX Xavier| [Buy]() | 


## Software:



## Installing Docker

Jetson Xavier SD card image comes with Docker but let's install the latest version of Docker 20.10.8.


```
xavier@xavier-desktop:~$ sudo docker version
[sudo] password for xavier: 
Client: Docker Engine - Community
 Version:           20.10.8
 API version:       1.41
 Go version:        go1.16.6
 Git commit:        3967b7d
 Built:             Fri Jul 30 19:54:37 2021
 OS/Arch:           linux/arm64
 Context:           default
 Experimental:      true

Server: Docker Engine - Community
 Engine:
  Version:          20.10.8
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.16.6
  Git commit:       75249d8
  Built:            Fri Jul 30 19:52:46 2021
  OS/Arch:          linux/arm64
  Experimental:     false
 containerd:
  Version:          1.4.9
  GitCommit:        e25210fe30a0a703442421b0f60afac609f950a3
 runc:
  Version:          1.0.1
  GitCommit:        v1.0.1-0-g4144b63
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
xavier@xavier-desktop:~$ 
```

## Identify the Jetson board

```
git clone https://github.com/jetsonhacks/jetsonUtilities
```


```
python3 jetsonInfo.py 
NVIDIA Jetson AGX Xavier [16GB]
 L4T 32.3.1 [ JetPack 4.3 ]
   Ubuntu 18.04.3 LTS
   Kernel Version: 4.9.140-tegra
 CUDA NOT_INSTALLED
   CUDA Architecture: 7.2
 OpenCV version: NOT_INSTALLED
   OpenCV Cuda: NO
 CUDNN: NOT_INSTALLED
 TensorRT: NOT_INSTALLED
 Vision Works: NOT_INSTALLED
 VPI: NOT_INSTALLED
 Vulcan: 1.1.70
xavier@xavier-desktop:~/jetsonUtilities$ 
```
## Installing Jtop

```
sudo -H pip install -U jetson-stats
```

```
sudo -H pip install -U jetson-stats
Collecting jetson-stats
  Downloading https://files.pythonhosted.org/packages/70/57/ce1aec95dd442d94c3bd47fcda77d16a3cf55850fa073ce8c3d6d162ae0b/jetson-stats-3.1.1.tar.gz (85kB)
    100% |████████████████████████████████| 92kB 623kB/s 
Building wheels for collected packages: jetson-stats
  Running setup.py bdist_wheel for jetson-stats ... done
  Stored in directory: /root/.cache/pip/wheels/5e/b0/97/f0f8222e76879bf04b6e8c248154e3bb970e0a2aa6d12388f9
Successfully built jetson-stats
Installing collected packages: jetson-stats
Successfully installed jetson-stats-3.1.1
xavier@xavier-desktop:~/jetsonUtilities$ 
```

```
$jtop
I can't access jetson_stats.service.
Please logout or reboot this board.
```

![image](https://user-images.githubusercontent.com/34368930/132097743-b3698991-f1db-488b-ab9e-c35afc8a1d99.png)

![image](https://user-images.githubusercontent.com/34368930/132097789-01070b08-217e-409e-a8a0-aabe5e67c9fc.png)

![image](https://user-images.githubusercontent.com/34368930/132097801-5916ea54-4ab9-44c4-80e3-44d6e2c01e25.png)




```
xavier@xavier-desktop:~$ jetson_release -v
 - NVIDIA Jetson AGX Xavier [16GB]
   * Jetpack 4.3 [L4T 32.3.1]
   * NV Power Mode: MODE_15W - Type: 2
   * jetson_stats.service: active
 - Board info:
   * Type: AGX Xavier [16GB]
   * SOC Family: tegra194 - ID:25
   * Module: P2888-0001 - Board: P2822-0000
   * Code Name: galen
   * CUDA GPU architecture (ARCH_BIN): 7.2
   * Serial Number: 1420921055981
 - Libraries:
   * CUDA: NOT_INSTALLED
   * cuDNN: NOT_INSTALLED
   * TensorRT: NOT_INSTALLED
   * Visionworks: NOT_INSTALLED
   * OpenCV: NOT_INSTALLED compiled CUDA: NO
   * VPI: NOT_INSTALLED
   * Vulkan: 1.1.70
 - jetson-stats:
   * Version 3.1.1
   * Works on Python 2.7.17
xavier@xavier-desktop:~$ 

```
## Jetson variables

```
export | grep JETSON
declare -x JETSON_BOARD="P2822-0000"
declare -x JETSON_BOARDIDS=""
declare -x JETSON_CHIP_ID="25"
declare -x JETSON_CODENAME="galen"
declare -x JETSON_CUDA="NOT_INSTALLED"
declare -x JETSON_CUDA_ARCH_BIN="7.2"
declare -x JETSON_CUDNN="NOT_INSTALLED"
declare -x JETSON_JETPACK="4.3"
declare -x JETSON_L4T="32.3.1"
declare -x JETSON_L4T_RELEASE="32"
declare -x JETSON_L4T_REVISION="3.1"
declare -x JETSON_MACHINE="NVIDIA Jetson AGX Xavier [16GB]"
declare -x JETSON_MODULE="P2888-0001"
declare -x JETSON_OPENCV="NOT_INSTALLED"
declare -x JETSON_OPENCV_CUDA="NO"
declare -x JETSON_SERIAL_NUMBER="1420921055981"
declare -x JETSON_SOC="tegra194"
declare -x JETSON_TENSORRT="NOT_INSTALLED"
declare -x JETSON_TYPE="AGX Xavier [16GB]"
declare -x JETSON_VISIONWORKS="NOT_INSTALLED"
declare -x JETSON_VPI="NOT_INSTALLED"
declare -x JETSON_VULKAN_INFO="1.1.70"
xavier@xavier-desktop:~$ 
```


## Installing nvidia-docker


```
sudo apt install nvidia-docker2
```

## Install nvidia-container-runtime package:

```
sudo yum install nvidia-container-runtime
```

## Update docker daemon

```
sudo vim /etc/docker/daemon.json
```

Ensure that /etc/docker/daemon.json with the path to nvidia-container-runtime:

```
{
    "runtimes": {
        "nvidia": {
            "path": "/usr/bin/nvidia-container-runtime",
            "runtimeArgs": []
        }
    }
}
```

## Make docker update the path:

```
sudo pkill -SIGHUP dockerd
```

## Running the DeepStreaming Container

- DeepStream 5.1 provides Docker containers for both dGPU and Jetson platforms. 
- These containers provide a convenient, out-of-the-box way to deploy DeepStream applications by packaging all associated dependencies within the container. 
- The associated Docker images are hosted on the NVIDIA container registry in the NGC web portal at https://ngc.nvidia.com. 
- They use the nvidia-docker package, which enables access to the required GPU resources from containers. 

## Please Note:

The dGPU container is called deepstream and the Jetson container is called deepstream-l4t. 

- Unlike the container in DeepStream 3.0, the dGPU DeepStream 5.1 container supports DeepStream application development within the container. 
- It contains the same build tools and development libraries as the DeepStream 5.1 SDK. 
- In a typical scenario, you build, execute and debug a DeepStream application within the DeepStream container. 
- Once your application is ready, you can use the DeepStream 5.1 container as a base image to create your own Docker container holding your application files (binaries, libraries, models, configuration file, etc.,)

![image](https://user-images.githubusercontent.com/34368930/132099794-0fc43284-09b4-4331-b198-471f06ab5ab0.png)


This section describes the features supported by the DeepStream Docker container for the dGPU and Jetson platforms.

To run the container:

Allow external applications to connect to the host's X display:

```
xhost +
```

## Run the docker container using the nvidia-docker (use the desired container tag in the command line below):

```
sudo docker run -it --rm --net=host --runtime nvidia  -e DISPLAY=$DISPLAY -w /opt/nvidia/deepstream/deepstream-5.1 -v /tmp/.X11-unix/:/tmp/.X11-unix nvcr.io/nvidia/deepstream-l4t:5.1-21.02-samples
```

Option explained:

-it means run in interactive mode

--rm will delete the container when finished

-v is the mounting directory, and used to mount host's X11 display in the container filesystem

5.1-21.02-samples is the tag for the image; 21.02 refers to the version of the container for that release; samples refers to the container variant

user can mount additional directories (using -v option) as required containing configuration file and models for access by applications executed from within the container

Additionally, --cap-add SYSLOG option needs to be included to enable usage of the nvds_logger functionality inside the container.

See /opt/nvidia/deepstream/deepstream-5.1/README inside the container for deepstream-app usage information. Additional argument to add to above docker command for accessing CSI Camera from Docker: -v /tmp/argus_socket:/tmp/argus_socket For USB Camera additional argument --device /dev/video


```
sudo docker ps
CONTAINER ID   IMAGE                                             COMMAND       CREATED          STATUS         PORTS     NAMES
ad38d8f4612d   nvcr.io/nvidia/deepstream-l4t:5.1-21.02-samples   "/bin/bash"   10 seconds ago   Up 9 seconds             romantic_hopper
xavier@xavier-desktop:~$ 
```

```
root@xavier-desktop:/opt/nvidia/deepstream/deepstream-5.1# tree -L 2
.
|-- LICENSE.txt
|-- LicenseAgreement.pdf
|-- README
|-- bin
|   |-- deepstream-app
|   |-- deepstream-appsrc-test
|   |-- deepstream-audio
|   |-- deepstream-dewarper-app
|   |-- deepstream-gst-metadata-app
|   |-- deepstream-image-decode-app
|   |-- deepstream-image-meta-test
|   |-- deepstream-infer-tensor-meta-app
|   |-- deepstream-mrcnn-app
|   |-- deepstream-nvdsanalytics-test
|   |-- deepstream-nvof-app
|   |-- deepstream-opencv-test
|   |-- deepstream-perf-demo
|   |-- deepstream-segmentation-app
|   |-- deepstream-test1-app
|   |-- deepstream-test2-app
|   |-- deepstream-test3-app
|   |-- deepstream-test4-app
|   |-- deepstream-test5-app
|   |-- deepstream-testsr-app
|   |-- deepstream-transfer-learning-app
|   `-- deepstream-user-metadata-app
|-- doc
|   `-- nvidia-tegra
|-- install.sh
|-- lib
|   |-- gst-plugins
|   |-- libiothub_client.so
|   |-- libiothub_client.so.1 -> libiothub_client.so
|   |-- libnvbufsurface.so -> /usr/lib/aarch64-linux-gnu/tegra/libnvbufsurface.so
|   |-- libnvbufsurftransform.so -> /usr/lib/aarch64-linux-gnu/tegra/libnvbufsurftransform.so
|   |-- libnvds_amqp_proto.so
|   |-- libnvds_audiotransform.so
|   |-- libnvds_azure_edge_proto.so
|   |-- libnvds_azure_proto.so
|   |-- libnvds_batch_jpegenc.so
|   |-- libnvds_csvparser.so
|   |-- libnvds_dewarper.so
|   |-- libnvds_dsanalytics.so
|   |-- libnvds_infer.so
|   |-- libnvds_infer_custom_parser_audio.so
|   |-- libnvds_infer_server.so
|   |-- libnvds_infercustomparser.so
|   |-- libnvds_inferutils.so
|   |-- libnvds_kafka_proto.so
|   |-- libnvds_logger.so
|   |-- libnvds_meta.so
|   |-- libnvds_mot_iou.so
|   |-- libnvds_mot_klt.so
|   |-- libnvds_msgbroker.so
|   |-- libnvds_msgconv.so -> libnvds_msgconv.so.1.0.0
|   |-- libnvds_msgconv.so.1.0.0
|   |-- libnvds_msgconv_audio.so -> libnvds_msgconv_audio.so.1.0.0
|   |-- libnvds_msgconv_audio.so.1.0.0
|   |-- libnvds_nvdcf.so
|   |-- libnvds_nvtxhelper.so
|   |-- libnvds_opticalflow_dgpu.so
|   |-- libnvds_opticalflow_jetson.so
|   |-- libnvds_osd.so
|   |-- libnvds_redis_proto.so
|   |-- libnvds_utils.so
|   |-- libnvdsgst_helper.so
|   |-- libnvdsgst_inferbase.so
|   |-- libnvdsgst_meta.so
|   |-- libnvdsgst_smartrecord.so
|   |-- libnvdsgst_tensor.so
|   |-- libtritonserver.so
|   |-- pyds.so
|   |-- setup.py
|   `-- triton_backends
|-- samples
|   |-- configs
|   |-- models
|   |-- prepare_classification_test_video.sh
|   |-- prepare_ds_trtis_model_repo.sh
|   |-- streams
|   `-- trtis_model_repo
|-- sources
|   |-- SONYCAudioClassifier
|   |-- apps
|   |-- gst-plugins
|   |-- includes
|   |-- libs
|   |-- objectDetector_FasterRCNN
|   |-- objectDetector_SSD
|   |-- objectDetector_Yolo
|   `-- tools
|-- uninstall.sh
`-- version
```









