## YOLOv8
so we are going to get through all the steps to install run YOLOv8 in Jetson Nano 
1. Install Python3.8.12
2. Install virtualenv and create a a project (virtual environment) for development
3. Setup and install dependencies for YOLOv8
4. Test Inference!

NOTE
- any line begins with `$` mean this is command
- any line without suppose to be output of previous command  
--------------------------

### 1. Install Python3.8.12
Because YOLOv8 require minimum Python3.8, in this step, we are going to install Python3.8.12 into Jetson Nano, along side default one (Python 3.6.9 and Python 2.7.4).
First, we need to install dependencies (required libraries), please run following command   
```shell
 $ sudo apt install build-essential libssl-dev zlib1g-dev libncurses5-dev libncursesw5-dev libreadline-dev libsqlite3-dev libgdbm-dev libdb5.3-dev libbz2-dev libexpat1-dev liblzma-dev libffi-dev libc6-dev
```

Next, we are going to load Python installation files from official website. ** We need to compile this by ourselve **
```shell
 $ cd ~/ #load into home directory  
 $ wget https://www.python.org/ftp/python/3.8.12/Python-3.8.12.tar.xz
```

Extract the downloaded file and enter the directory
```shell
 $ tar -xf Python-3.8.12.tar.xz
 $ cd Python-3.8.12
```

Run following commands start installation process of Python3.8.12 
```shell
 $ ./configure --enable-optimizations
 $ make -j4
 $ sudo make altinstall #alternate installation, make this python work alongside with default one
```

Confirm installation process
```shell
 $ python3.8 --version #should print Python3.8.12
 Python3.8.12
 $ python3 --version #should print Python3.6.9
 Python3.6.9
```
--------------------------
### 2. Install virtualenv and create a a project (virtual environment) for development
In the future, we are going to develop several projects that involve different dependencies. So, it is practical that we have seprate different setup (e.g., dependencies, python version etc). We can do this by using library call virtualenv which create a project like development enviornmnet. 

First, run commad below to install virutalenv
```shell
 $ sudo apt-get install python3-virtualenv 
```

Next, we are going to create the project folder that contain program code on `Desktop/yolov8_test` of Jetson Nano.
```shell
 $ cd ~/Desktop
 $ mkdir yolov8_test
 $ cd yolov8_test
 $ python3.8 -m venv .venv
``` 

We are going to setup the virtualenvironment in folder `.venv`. after run these commands, you will see `(.venv)` in front of your terminal command. This indicate that you are using virtualenv in develop you own program. Anything library you install here will not effect host's Python 3.8
```shell
 $ python3.8 -m venv .venv
 $ soruce .venv/bin/activate
 (.venv)
``` 
### 3. Setup and install dependencies for YOLOv8
YOLOv8 require library called **ultralytics**, we simply using `pip` to install that library.
Technically, this command install several dependencies including PyTorch, NumPy, OpenCV (No CUDA) etc.
```shell
 $ pip install ultralytics
```




