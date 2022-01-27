# AI-Torpedo-Vision

Quick start guide on how configure Jetson Nano 4GB to run a simple object detection code in Python.
The purpose of this guide is to provide a simple easy test bench setup for comparing effectivness of different image filtering functions.

First run:
```9
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
To run multiple images at once they have to follow a naming sequence
Example:
```
jetson-inference/build/aarch64/bin# ./detectnet "images/peds_*.jpg" images/test/peds_%i.jpg
```
# Explanation: 
The "*" is the wild card chracteristic that allows you to run the images of the same naming sequence at once.
```
images/test/
```
Defines the output folder. Folder needs to be in the container of the host.
