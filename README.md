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

# Running Live Video Code
Below is the code "my detection" modified to run the popular model ssd-mobilenet-v2. Our submarines jetsons runs this same model during debug mode. Running will allow the user to see real time confidence value that is above the threshold of 50% on objects the model is trained to identify.

```
import jetson.inference
import jetson.utils

net = jetson.inference.detectNet("ssd-mobilenet-v2", threshold=0.5)
camera = jetson.utils.gstCamera(1280,720, "/dev/video0")      # '/dev/video0' for V4L2
display = jetson.utils.glDisplay() # 'my_video.mp4' for file

while display.IsOpen():
	img, width, height = camera.CaptureRGBA()
	detections = net.Detect(img,width,height)
	display.RenderOnce(img,width,height)
	display.SetTitle("Object Detection | Network {:.0f} FPS".format(net.GetNetworkFPS()))
```
To run the "my-detection" code:
```
python3 my-detection.py
```
# Running code for single image
```
cd jetson-inference/build/aarch64/bin
./detectnet images/[image name].jpg images/test/[output name].jpg
```
