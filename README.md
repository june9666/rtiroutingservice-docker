# Environmental

This tutorial was made on WSL Ubuntu 16.04, with Docker Desktop.  
Building the image would only need a Docker with linux container support (on Windows, Docker Desktop default setting). 
To follow steps on WSL, install Xming X Server for Windows, setup your environment (export DISPLAY=:0.0).

# Install
We need RTI Connext files, install RTI from official website.  
I used https://s3.amazonaws.com/RTI/Bundles/6.0.1/Evaluation/rti_connext_dds-6.0.1-eval-x64Linux3gcc5.4.0.run
  x86 64bit Ubuntu 16.04 LTS (kernel 4.x & gcc 5.4.0) installer.  
Complete the install, set your NDDSHOME environmental variable, 
```
$ export NDDSHOME=<path_to_installed_dir>
```
and place your license to $NDDSHOME/rti_license.dat.  

Clone this repository:
```
$ git clone https://github.com/june9666/rtiroutingservice-docker.git
```
Run copy_files.sh to copy necesseray files to your folder. 
```
$ ./copy_files.sh
```
Build the image. 
```
$ docker build -t rtiroutingservice .
```

# Usage
Run the container:
```
$ docker run -it --name rtiroutingservice rtiroutingservice
```

Add your Routing Service config to the container (from another Shell).
```
$ docker cp myconf.xml rtiroutingservice:/rti
$ docker cp mylib.so rtiroutingservice:/rti
```
Run Routing Service.
```
# ./bin/routingservice -cfgFile myconf.xml -cfgName example
```

# More info

https://community.rti.com/static/documentation/connext-dds/6.0.1/doc/manuals/routing_service/index.html





