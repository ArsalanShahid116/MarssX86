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

### License
------------
The programs in this project are free software; you can redistribute <br />
it and/or modify it under the terms of the GNU General Public License <br />
as published by the Free Software Foundation; either version 2 of the <br />
License, or (at your option) any later version. This program is <br />
distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY;<br />
without even the implied warranty of MERCHANTABILITY or FITNESS FOR <br />
A PARTICULAR PURPOSE. See the GNU General Public License for more <br />
details. You should have received a copy of the GNU General Public <br /> 
License along with this program; if not, write to the Free Software <br />
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA. <br />

### NOTE
--------
This software depends on other packages that may be licensed under different open source licenses.
