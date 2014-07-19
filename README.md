MarssX86
========
**************************MARSS download and installation**************************
-	Open terminal any type
-	
o	sudo apt-get install git

o	git clone git://github.com/avadhpatel/marss.git

o	cd marss

o	sudo apt-get install scons

o	sudo apt-get install zlib1g-dev

o	sudo apt-get install g++-multilib

Start Compiling MARSS 

o	scons -Q -c

Give Number of Core and Enable Debug

o	scons –Q debug=1 c=2

-	Download Image tar http://bertha.cs.binghamton.edu/downloads/splash.tar.bz2

-	Extract the image file (splash.img) and copy it to marss folder

-	 Create a config (.cfg) file for your machine
-	 
o	 gedit my.cfg

	Paste the config below

-machine xeon_dual_core

-stopinsns 100m

-kill-after-run

-stats results.stats

-logfile results.log

o	Save this file and close gedit

**************************MARSS stats file generation**************************
-	Generate stats file (by simulation, I executed BARNES)
-	
o	Open terminal and type

	cd marss

	qemu/qemu-system-x86_64 –m 1536 –hda splash.img –simconfig my.cfg

o	Open another terminal and type  

o	 for showing QEMU we need to install vinagre … its builtin in fedora but not in ubuntu

	sudo apt-get install vinagre

	vinagre 172.0.0.1:5900

o	You will see Qemu running machine simulation

	Login with password root

	Inside Qemu type

•	cd splash2/codes/apps/barnes

•	../../../../start_sim; ./BARNES < input.4; ../../../../stop_sim;

 
Start simulation on Qemu by giving image Splash.img and then giving number of input core = 4. Access BARNES in the splash folder. And then stoping the simulation.
