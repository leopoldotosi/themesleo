---
title: lxc-kdenlive
layout: post
tags:
- lxc
- linux
- virtual
- kdenlive
- install
author: leopoldo
---

<table  style="background-color: #DDDAAA;">
 <th colspan="3"><h2>	lxc-kdenlive </h2></th>
		  <tr>
    <td>
	Il miracolo di kdenlive sui cointaners debian-like è possibile \**/
	<br>
faccio riferimento a questo post, ma va adattato e neccessità di diverse correzioni (-:
	</td>
   <td><span> </span></td>
    <td    style="background-color: #FFF777;">		<br>	<br> https://gist.github.com/JamesCordell/ffb9e50c9bb32f99fdc690bb24fdc970
</td>
  </tr>
	
	
  <tr>
    <td>Propongo una via più semplice sempre ricompilando i sorgenti ((-:
	<br>
aggiungere al sourcelist del contair i siti deb-src per scaricare i sorgenti:</td>
   <td><span> </span></td>
    <td style="background-color: #FFF777;">     /etc/apt/sources.list
	<br>	<br>
deb-src http://deb.debian.org/debian/ buster main non-free contrib	<br>
deb-src http://security.debian.org/debian-security buster/updates main contrib non-free	<br>
deb-src http://deb.debian.org/debian/ buster-updates main contrib non-free	<br>
deb-src http://deb.debian.org/debian/ buster-backports main contrib non-free
			<br>	<br>
  sudo apt update		<br>	<br>

    apt-get build kdenlive
	</td>
  </tr>
	
	  <tr>
    <td>sempre sul container installare i pacchetti (-:</td>
	    <td><span> </span></td>
    <td   style="background-color: #FFF777;">
			apt install xauth x11-tools dbus breeze fonts-config xorg-x11-fonts-core xorg-x11-fonts openssh-server ruby subversion gnupg2 gettext   libmlt++-dev libmlt-dev melt frei0r-plugins frei0r-plugins-dev ffmpeg libavdevice-dev 
			</td>
  </tr>
	
	   <tr>
    <td colspan="3">e inserire la variabile export <b>PULSE_SERVER=tcp:10.0.3.1:4713</b> nel file .bashrc (è l'audio) 	<br>	<br>
			 
scaricate i rttr https://www.rttr.org/download compilare e installare con prefix=/usr/local <br>	<br>
	 </td>
  </tr>
	
	
  <tr>
    <td>
				
scaricate dal sito  	<br> https://invent.kde.org/kde/kdenlive.git 	<br> la versione adatta al vostro OS 	<br>	<br>

entrate nella directory di kdenlive (-; 	<br>	<br>

create la directory build e entrate	<br>	<br>

modificate  il ../CMakeLists.txt 
		
		</td>
	    <td><span> </span></td>
    <td   style="background-color: #FFF777;">
		
option(BUILD_BENCHMARKS "Enable this to build the benchmarks" OFF)	<br>
option(BUILD_EXAMPLES "Enable this to build the examples" OFF)	<br>
option(BUILD_UNIT_TESTS "Build the unit tests of RTTR" OFF)	<br>

		</td>
  </tr>
	  
	<tr>	
			<td>
				compilare
				
				</td>
	    <td><span> </span></td>
    <td  style="background-color: #FFF777;"> 
			cmake .. -DKDE_INSTALL_USE_QT_SYS_PATHS=ON 
-DCMAKE_INSTALL_PREFIX=/usr/local  -DCMAKE_CXX_COMPILER=/usr/bin/clang++ 
-DECM_ENABLE_SANITIZERS='address'  -DRELEASE_BUILD=ON
			<br>
			<br>
			make				<br>	<br>
 	</td>
  </tr>
		
	<tr>	
			<td>sul host avviate paprefs e
				</td>
	    <td><span> </span></td>
    <td   style="background-color: #FFF777;"> 
Network Access tab on client:			<br>			<br>

    check Make discoverable PulseAudio network sound devices available locally			<br>			<br>

Network Server tab on server:			<br>			<br>

    check Enable network access to local sound devices			<br>
    check Allow other machines on the LAN to discover local sound devices			<br>
    check Don't require authentication
			
 	</td>
  </tr>
	
		
	<tr >	
			<td colspan="3">collegatevi via ssh al container e avviate kdenlive da riga di comando
				</td>
   </tr>
	
			
	<tr>	
			<td colspan="3">	<b>ERROR	</b>  	<br>	<br>

se va in errore vi indica di definire la seguente variabile
				
					<br>export ASAN_OPTIONS=new_delete_type_mismatch=0
	<br>	<br>
inserite nel file .bashrc
				</td>
	    <td><span> </span></td>
    <td> 
 	</td>
  </tr>
	
			
	<tr>	
			<td>
				</td>
	    <td><span> </span></td>
    <td> 
 	</td>
  </tr>
	
</table>
