# Xeon Multicore Configuration File For MarssX86 Simulator

### MARSS download and installation

shell$	sudo apt-get install git <br/>
shell$ git clone git://github.com/avadhpatel/marss.git <br/>
shell$ cd marss <br/>
shell$ sudo apt-get install scons <br/>
shell$ sudo apt-get install zlib1g-dev <br/>
shell$ sudo apt-get install g++-multilib <br/>

Compiling MARSS <br/>

shell$ scons -Q -c <br/>

Give Number of Core and Enable Debug <br/>

shell$ scons –Q debug=1 c=2 <br/>

Download Image tar http://bertha.cs.binghamton.edu/downloads/splash.tar.bz2 <br/>
Extract the image file (splash.img) and copy it to marss folder <br/>
Create a config (.cfg) file for your machine <br/>
 
shell$ gedit my.cfg <br/>

Paste the config below <br/>

-machine xeon_dual_core <br/>
-stopinsns 100m <br/>
-kill-after-run <br/>
-stats results.stats <br/>
-logfile results.log <br/>

Save this file and close gedit <br/>

### MARSS stats file generation 

Generate stats file (by simulation, I executed BARNES) <br/>
Open terminal and type <br/>

shell$ cd marss <br/>
shell$ qemu/qemu-system-x86_64 –m 1536 –hda splash.img –simconfig my.cfg <br/>

Open another terminal and type  <br/>
For QEMU, we need to install vinagre … its builtin in fedora but not in ubuntu <br/>

shell$ sudo apt-get install vinagre <br/>
shell$ vinagre 172.0.0.1:5900 <br/>

You will see Qemu running machine simulation <br/>
Login with password root <br/>

Inside Qemu type: <br/>

shell$ cd splash2/codes/apps/barnes <br/>
shell$ ../../../../start_sim; ./BARNES < input.4; ../../../../stop_sim; <br/>
