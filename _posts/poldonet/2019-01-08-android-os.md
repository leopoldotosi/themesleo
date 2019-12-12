---
title: android_os
layout: post
author: leopoldo
tags:
- android
- os
- linux
- emulator
- qemu
---

<table border="0">
    <caption><h2>Android OS in Emulation</h2></caption>
    <thead>
        <tr>
            <th colspan="3" align="right"> 
            </th>
        </tr>
    </thead>
    <tbody  align="center">
            <tr>
            <td  align="left">
						cosa sapte di android? <br>
            come fare per saperne di più? <br>
           dispiaceri di android? esiste solo root? <br>
           in compenso funziona  (-:
</td>
            <td colspan="2"><img src="{{site.baseurl}}/assets/imges/poldonet/andr001.jpg"  alt="an01" style="width:60%"></td>
        </tr>
        <tr> <td colspan="2"></td> <td></td> </tr>
        <tr>
            <td colspan="2">
                <img src="{{site.baseurl}}/assets/imges/poldonet/andr002.jpg"  alt="an02" style="width:60%"> </td>
            <td align="left">stringa qemu <br>
						sudo qemu-system-x86_64  -cdrom android-x86_64-8.1-rc2.iso \ <br>
						                                                          -boot order=c -hda android001.img  \ <br>
						                                                          -vga qxl -enable-kvm -cpu host -smp 2 -m 2047 \ <br>
																																			-soundhw ac97 -machine q35 \  # scheda audio <br>
																																			-net nic,vlan=0 -net vde,vlan=0,sock=/tmp/vde0.ctl -net user,vlan=0 \<br>
																																			-usb -usbdevice host:0bda:58d8 # webcam

						</td>
        </tr>
        <tr>
            <td></td>
            <td colspan="2"><img src="{{site.baseurl}}/assets/imges/poldonet/andr003.jpg"  alt="an03" style="width:60%"></td>
        </tr>
				 <tr>
				   <td colspan="2"><img src="{{site.baseurl}}/assets/imges/poldonet/andr004.jpg"  alt="an04" style="width:60%"></td>
           <!-- andr004.jpg -->
					 <td>anche la fotocamera funziona. Ogni device viene letto</td>
        </tr>
        <tr>
            <td align="left">installare le app che non sono tanto leggere <br>
						cmq la shell bash permette di interaggire con OS <br>
						se digitate cat /proc/cpuinfo [invio] <br>
						vedrete le caratteristiche del procesore (-:
						</td>
						 <td colspan="2"><img src="{{site.baseurl}}/assets/imges/poldonet/andr003sh.jpg"  alt="an03sh" style="width:60%">	 </td>
        </tr>
      
        <tr> <td colspan="2"></td> <td></td> </tr>

    </tbody>
</table>
