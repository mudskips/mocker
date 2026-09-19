## Mocker

### What is it?
Mocker is a way to run containers on linux based systems and VMs by utilizing namespaces and cgroups to isolate processes. The structure is based on a simplified version of docker (hence the name) 

### How to run

#### Requirements
- Linux based system or VM with cgroups v2
- Python3
- "Click" library (pip install click)
- Linux C module:
```
   git clone https://github.com/Fewbytes/rubber-docker.git
   cd rubber-docker
   sudo pip install --break-system-packages .
```

#### Setup
1. Create directories:
```
   sudo mkdir -p /mocker/images /mocker/containers
```
2. Download tarball (for example, Ubuntu) and place it in mocker/images:
```
   cd /mocker/images
   wget -O ubuntu-base.tar.gz https://cdimage.ubuntu.com/ubuntu-base/releases/24.04/release/ubuntu-base-24.04.4-base-amd64.tar.gz
   mkdir ubuntu-root && tar -xzf ubuntu-base.tar.gz -C ubuntu-root
   cd ubuntu-root && tar -cf ../ubuntu.tar . && cd ..
   rm -rf ubuntu-root ubuntu-base.tar.gz
```
3. Clone mocker repo into mocker
```
git clone https://github.com/mudskips/mocker mocker
cd mocker
```
4. Run the container:
```
sudo python3 main.py run -i ubuntu -- /bin/bash
```