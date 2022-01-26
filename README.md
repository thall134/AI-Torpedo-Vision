# AI-Torpedo-Vision
Quick start guide on how configure Jetson Nano 4GB to run a simple object detection code in Python.

The purpose of this guide is to provide a simple easy test bench setup for comparing effectivness of different image filtering functions.

First run:
```
sudo apt-get update
sudo apt-get install get cmake libpython3-dev python3-numpy
git clone --recursive https://github.com/dusty-nv/jetson-inference.git
```
```
cd jetson-inference/
mkdir build
cd build
cmake../
```

