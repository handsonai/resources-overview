# Pose estimation

This page provides an overview on how to get started quickly with deep learning models for pose estimation on your own computer.

## Python3 and Tensorflow
I would propose that we try to work in the same environment as much as possible, to facilitate sharing of knowledge and work.
There are several deep-learning frameworks, of which Tensorflow is currently probably the most widespread. 
In addition, *Keras* is a relatively easy to use higher-level library that works on top of tensorflow.

Installing Tensorflow with *GPU* support is not strictly necessary, but will greatly improve learning and inference speed. The installation 
is a little more involved than the CPU alternative, so you may want to start with that. You do need a graphic card that supports CUDA for 
this, like most nvidia cards. To my knowledge, GPU support is not available on macOS. (But correct me if I'm wrong) (JanM: there are ways...)

### Linux
...todo...

### Mac
The procedure described on the [Tensorflow macOS install page](https://www.tensorflow.org/install/install_mac) is pretty straightforward, the virtualenv method works fine.

GPU support is difficult, see [this guide](https://byai.io/howto-tensorflow-1-6-on-mac-with-gpu-acceleration/). Also it is rather pointless because Tensorflow requires CUDA which has no support on factory MacBooks, because no NVidea GPUs.

### Windows
For Windows, Anaconda is a convenient way to install Python, Tensorflow and many other Python libraries. As stated on the 
[Tensorflow website](https://www.tensorflow.org/install/install_windows) though, the Anaconda package of Tensorflow is community supported,
not officially supported. But in my experience pip install does not allways work well on Windows when packages need to be compiled. So
Anaconda provides an easy to use installer.

To get started, download the python3.6 distribution from [https://www.anaconda.com/download/](https://www.anaconda.com/download/).
Then follow the guide on [https://www.tensorflow.org/install/install_windows](https://www.tensorflow.org/install/install_windows)

## Pose estimation models

#### tf-pose-estimation
A nice pretrained model to begin with is [tf-pose-estimation](https://github.com/handsonai/tf-pose-estimation).
Clone or download the repository, then run 
```
$ python src/run_webcam.py --model=mobilenet_thin --resolution=432x368 --camera=0
```
Note that the version linked here is adapted from the original, a run_vectors.py script was added by Fako Berkers that outputs json with the coordinates of the pose.

##### macOS install
Depending on what you currently have installed, the install in the readme of tf-pose-estimation might not work rightaway.
I had to edit requirements.txt and remove the lines for ast and dill (it still seems to work afterwards).
openCV is needed, I already had it installed so I don't know what is required exactly.
```
brew install opencv
```
To get the webcam demo running (live video input), I had to install ffmpeg with x265 support, in my case that meant:
```
brew reinstall ffmpeg --with-x265
```
To get the image-file demo running (run.py), I got error from matplotlib about Python needing to be installed as a Framework, but [there is always StackOverflow](https://stackoverflow.com/a/21789908/403991).


#### Openpose
To quickly get started on Windows you can download the [binaries](https://github.com/CMU-Perceptual-Computing-Lab/openpose/releases) for the [openpose project](https://github.com/CMU-Perceptual-Computing-Lab/openpose). These allow you to use their openpose system with a webcam without having to install anything else (they come with a .bat file to download the needed models). 
