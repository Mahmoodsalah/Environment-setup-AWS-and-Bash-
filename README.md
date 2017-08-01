# Bash-on-Ubuntu-for-Windows-Configurations-Guide
Bash on Ubuntu for Windows || Configurations Guide (Self Driving Car Engineer Nanodegree Program From Udacity) 
This  Guide take from me more than two weeks to can find answers for each problem you may face. 




Step 1:  Install  Windows Linux bash (follow this https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/)

Step 2: check version by command:  
lsb_release -a
if Release:        14.04 so you need to upgrade it to 16

Step 3: Upgrade it by write this command:
sudo do-release-upgrade
for more details (https://www.howtogeek.com/278152/how-to-update-the-windows-bash-shell/)  

Check again by step 2 if it still Release  14 so you need to upgrade windows 10 check this for more details: https://www.windowscentral.com/how-get-windows-10-creators-update

Step 4: download/clone project folder:

for example proj5 folder path after unzip it will be (in case if you download it directly from GitHub)   E:\SDC\proj5

Step 5: open Linux bash for windows, and write this command:
cd "your path"  

Note: you have to write this before path /mnt/  then replace \ to /    and put the path in " "
for example  cd E:\SDC\proj5
will be  cd "/mnt/e/SDC/proj5"

My real example path: 
 cd "/mnt/e/Me/Courses/UDACITY Self-Drive Car Nanodegree/TERM 3/Projects/CarND-Path-Planning-Project-master"

Instead of 
cd E:\Me\Courses\UDACITY Self-Drive Car Nanodegree\TERM 3\Projects\CarND-Path-Planning-Project-master

Step 6: run this command 
./install-ubuntu.sh  

Note: but before it you must download:
git (  apt-get install git )
cmake (  apt-get install cmake )
Make (  apt-get install make )

Note: if you face this: (unable to resolve host) 
try this
run this command:
sudo nano /etc/hosts
and then add:
127.0.0.1 localhost.localdomain localhost 
127.0.1.1 ubuntu
then press Ctrl and X
then restart your computer

Note:  if you face this: (N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension) 
Just remove it is unnecessary:
sudo rm /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist
Note: if you face this while install cmake: 
Err:1 http://security.ubuntu.com/ubuntu xenial-security/main amd64 linux-libc-dev amd64 4.4.0-83.106
  404  Not Found 

Try this: 
Download the libc6 and coreutils package files into a temporary directory (or wherever you'd like to keep them until the end of their installation): cd /tmp apt-get download libc6 coreutils
Install them: sudo dpkg -i {libc6,coreutils}_*.deb
Fix the remaining packaging issues with Apt:  sudo apt-get install -f

Note: if you fave this (ln: failed to create symbolic link '/usr/lib/libuWS.so': File exists) after installing websocket. This error says the symbolic link already exists. See this post (https://discussions.udacity.com/t/issues-installing-uws-on-ubuntu-16-04/247997/2?u=subodh.malgonde)  to understand what it means. 

You need to run this command from the project directory:
sudo ln -s -f /usr/lib64/libuWS.so /usr/lib/libuWS.so


This is similar to the second last line of the install-ubuntu.sh file, with an extra -f flag. This will force the replacement of the symbolic link. After this remove the websockets folder from the project directory, you don’t need this after installing uWebSockets.


After install all dependencies correctly go ahead with step 7.
Step 7: Build

mkdir build
cd build
cmake .. && make


Special Thanks: 
I need to thank  @subodh.malgonde and @drive_well  for helping me alot in this guide.
