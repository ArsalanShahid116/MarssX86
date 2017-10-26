# Xeon Multicore Configuration file for MarssX86

### MARSS download and installation

shell$	sudo apt-get install git <br/>
shell$ git clone git://github.com/avadhpatel/marss.git
shell$ cd marss
shell$ sudo apt-get install scons
shell$ sudo apt-get install zlib1g-dev
shell$ sudo apt-get install g++-multilib

Compiling MARSS 

shell$ scons -Q -c

Give Number of Core and Enable Debug

shell$ scons –Q debug=1 c=2

Download Image tar http://bertha.cs.binghamton.edu/downloads/splash.tar.bz2
Extract the image file (splash.img) and copy it to marss folder
Create a config (.cfg) file for your machine
 
shell$ gedit my.cfg

Paste the config below

-machine xeon_dual_core
-stopinsns 100m
-kill-after-run
-stats results.stats
-logfile results.log

Save this file and close gedit

### MARSS stats file generation

Generate stats file (by simulation, I executed BARNES)
Open terminal and type

shell$ cd marss
shell$ qemu/qemu-system-x86_64 –m 1536 –hda splash.img –simconfig my.cfg

Open another terminal and type  
For QEMU, we need to install vinagre … its builtin in fedora but not in ubuntu

shell$ sudo apt-get install vinagre
shell$ vinagre 172.0.0.1:5900

You will see Qemu running machine simulation
Login with password root

Inside Qemu type:

shell$ cd splash2/codes/apps/barnes
shell$ ../../../../start_sim; ./BARNES < input.4; ../../../../stop_sim;
