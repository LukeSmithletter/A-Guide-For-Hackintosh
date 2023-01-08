# A-Guide-For-Hackintosh
Instruction：Recently I am interested in hackintoshing,and learned a lot during that period.So I decided to write a guide for those people who is new here,so let's go!

Q&A

1.What is hackintosh and how does it work?
Hackintosh means running a macOS system on a pc,but not a mac.In order to do that,what we need is some "special method",and I will talk about that more particular later.

2.Will it do harm to my computer?
No,if you do it properly.Wnat it will take is just your time,patience and space on your disk.

3.Is any pc able to do that?
Actually,not all pcs are avalible for hackintosh,for example,the AMD chips(maybe fake CPU ID will work),some intel CPUs that are too old(like Pentium）or too new(any core chips newer than 10th gen,because you can't use the integrated graphics,which is a disater for laptops),but none of the chips based on arm is availble for it.And other hardwares like intel optune is completely incompatible with macOS,so if you have got an optune,you should have removed it.If your pc uses the broadcom wireless card,then you will be much more easier to make it work on macOS,otherwise you should find the proper kext(Kernal Extention)for your devices.Unluckily,it's still not possible for us to simulate touchID and most of cameras on laptops on hackintosh,and for some devices which uses the Intel® Smart Sound Technology (Intel® SST）maybe hard to simulate microphones.Some SSD is also not compatible with macOS,so if you want to run macOS on your pc,you should avoid all of these above

PREPARAIONS
1.A USB flash disk larger than 16GB
2.A pc with windows 8 or newer(Because the UEFI BootLoader is necessary for hackintosh)
3.A mac(either virtual machines or macintosh） or "I don't have any of these"
4.Some softwares(You can download them from release)
5.macOS file(I will also upload some)
6.A patient heart

Installation
1.Open Etcher or TransMac（I will use etcher),choose"flash from file"(first one on the left side)
<img width="776" alt="image" src="https://user-images.githubusercontent.com/113092367/211143247-95f00750-75fb-44f7-a161-524115469a12.png">
2.select your drive(DO NOT CHOOSE THE WRONG ONE BECAUSE ONCE YOU SELECT IT,ALL THE DATA ON IT WILL LOSE.
3.Standby and wait for it to finish.
tips:If you get a message said "flash failed",just eject your USB and wait till it's cooled and try again.
4.Open DiskGenius in case you can't see the volume OC or EFI in the File Exploer.
5.Select the folder named "EFI" ，delete it and copy the proper one.(just search your model+hackintosh on the GitHub or somewhere else,here I will make an example for Huawei Matebook 13 2020)
6.Shut down your pc,and then restart it while clicking f2 to enter the BIOS settings(different pcs have different ways),then disable " Secure Boot","TPM","CFG Lock","Thunderbolt"(may cause strange issues),"EFI Boot Devices"(others depend on your pc)
7.If you don't trust yourself,please backup all your important data in your pc and make a USB Bootable Device for windows by Rufus(another USB required）
8.Turn on your computer,opan diskgenius and click "file-Reboot to DiskGenius WinPE Version"
![image](https://user-images.githubusercontent.com/113092367/211178662-8c495c14-3804-427f-8612-15310547c41f.png)
9.Wait for it to create WinPE and reboot into it.
Right cilck the partition C:and select "Allocate Free Space to...",and create a new partition which is formatted into HFS+(to ensure the macOS base system is able to read this partition)
10.Right click the partition "ESP" and cilck "Resize Partition"
![image](https://user-images.githubusercontent.com/113092367/211178920-c4ff4fe2-8f12-4a7f-9930-40680df951c3.png)
11.Resize the partition "ESP" to 500MB(to ensure the system have enough space to add the opencore bootloader,if you are lack of space,300MB will work as well)
12.Reboot the pc,and when you see the logo,kept press F12 and boot from your drive which you have flashed earlier.
13.Try to find the opencore boot loader,and when you see the show picker,select "Install macOS Big Sur/Ventura/Monterey/...
(Code running,if you stuck here,just search on the internet）
14.select "disk utility”,and cilck the small botton on the top,next tothe disk,select"show all devices",and find the partition which you had just created(DO NOT CHOOSE THE WRONG ONE),cilck "erase",and select "APFS".
15.Wait until it's done and quit disk utility.
16.Install macOS by the instructions.(Remember to choose to boot from EFI USB Devices each restart)
17.Wait..................
18.When you finally see "Hello",that means you have succeeded! Congratulations！
19.Do as what you do when you activate a real mac,but remember not to sign your appleID.
20.See whether every hardware is working.

Advanced
Unlock the CFG Lock to get the better power management(I will make an example with the Insyde BIOS which Huawei Matebook 13 2020had,not every pc is the same)
1.Download the H2OUVE and open"Win_x64_200.00.01.00-Win GUI -inst"
2.Select "file-load runtime-Dump BIOS Rom"and save your own BIOS file(.fd)
2.Do not close H2OUVE
3.Open UEFI Tools,select"File-select image File-your own bios.fd"
4.ctrl+F
5.Follow the image
![image](https://user-images.githubusercontent.com/113092367/211183746-145bae64-24d4-4569-8fc6-33bc37165e51.png)
 To be continued...
