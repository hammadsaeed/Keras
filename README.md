# Keras
Keras for beginners

To get started we need to install CUDA and CUDNN if you want to use your internal GPU for running tensorflow.


## Installing Nvidia Drivers and Cuda
Firstly we need to install nvidia driver I personally recomend nvidia 390. To install that open up terminal and type:

```
 sudo apt-get install nvidia-390
```

I recommended installing cuda 9.0 or 9.1 as 9.2 is not fully supported and you might run into mulitple errors when playing around with tensorflow

1. Go to Cuda tool kit and scroll down to [legacy releases](https://developer.nvidia.com/cuda-toolkit-archive)
2. Download the local runfile. Make sure you select the correct operating system in this tutorial i will be using linix
3. Navigate to the runfile using the cd commond for instance if its on the desktop type:
```
cd Desktop/
```
4. To run the .run file type in:
```
sudo sh cuda_9.1.85_387.26_linux.run 
```
5. Make sure you press N when it asks to install the nvidia drivers as we have previosuly installed them.
6. Once cuda is installed we need to open the .bashrc for that type in:
```
nano ~/.bashrc
```
and then add these lines at the end of the file (this is done so that libs such as tensorflow can locate cuda) :
```
export PATH=/usr/local/cuda-9.1/bin${PATH:+:${PATH}}
```
Press Ctrl+X to exit out make sure you press save when exiting out

7. Run the following command so that the changes are applied:
```
source ~/.bashrc
```
8. Reboot you pc and verify nvidia and cuda drivers are install properly this will be done by:
```
cat /proc/driver/nvidia/version
```
and for cuda
```
nvcc -V
```
9. Now you need to install cuDNN to do that firstly you need register for an [nvidia develper account](https://developer.nvidia.com/cudnn)
10. Now download cuDNN 7.1 for linix
11. Once downloaded navigate to that folder and unpack the file
```
 tar -xzvf cudnn-8.0-linux-x64-v5.1.tgz
 ```
 Copy cuDNN files to cuda folder
 ```
 sudo cp cuda/lib64/* /usr/local/cuda/lib64/
 sudo cp cuda/include/cudnn.h /usr/local/cuda/include/
 ```
## Setting up a virtaul enviornment 
1. To install a virtual enviornment firstly type:
```
sudo apt-get install python3-venv
 ```
2. Name your virtual enviornment 
```
virtualenv --system-site-packages ~/keras
 ```
3. To activate the virtual enviornment type:
```
source ~/keras/bin/activate
 ```
4. Now install tensorflow by using this command:
```
pip3 install --upgrade tensorflow-gpu
 ```
5. Now install Keras Library:
```
pip3 install keras
 ```
6. Finally to test everthing create a **text file** with 
```
import tensorflow as tf
import keras
import numpy as np
import scipy

sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))
 ```

7. Save it as test.py and run it using:
```
python3 test.py
 ```
