# ubuntu-dockerhost-vagrantfile
A Vagrantfile for creating an Ubuntu Dockerhost for Windows. 
Automatically installs docker and fig and syncs your user folder.

* download .zip and unpack
* I recommend using cmder console emulator http://bliker.github.io/cmder/ but standard cmd.exe will also do
* cd to unpacked folder
* run ```vagrant up``` and wait until machine is setup
* login via ```vagrant ssh```
* cd to your project folder ```cd /c/Users/...``` 
* run ```fig up``` or ```fig up -d``` to run it as a daemon 

I recommend using jwilders nginx proxy to create a virtual host that you can access in your browser.
https://github.com/jwilder/nginx-proxy

You can find out the machines ip address by running ```ifconfig```. It's probably inet addr of eth1.
