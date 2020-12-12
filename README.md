### Mac OS Big Sur on Dell Inspiron 15 7567 15.6" Core i7 Gaming Laptop
![](https://github.com/theace9/OpenCore-Dell-Inspiron-15-7567/blob/main/working_Screenshot_2020-12-11_at_23.41.33.png)

# System Specs
```
- Dell Inspiron 15 7567 15.6" Gaming Laptop - Core i7 2.8GHz, 16GB RAM
- Samsung 850 Evo 500GB SSD 
- Intel Core i7 7700HQ Processor Kaby Lake-H
- Intel HD Graphics 630 [iGPU] main GPU
- GeForce GTX 1050 Ti Graphics [dGPU] (pre-disabled for you)
- Screen Resolution:3840 x 2160 (4k)

## [Chipest]
Intel(R) 100 Series/C230 Series Chipset Family LPC Controller (HM175) - A152

## [Audio]
Realtek ALC256 @ Intel Sunrise Point PCH - High Definition Audio Controller [D1]

## [Network]pci
Intel Dual Band Wireless-AC 3165 AC HMC WiFi Adapter
Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter (PHY: Realtek RTL8111)

## SMBios
MacBookPro14,3
```
` Make sure to change this to new smbios with new ids!! `

Supported OpenCore version: 0.6.4

### What works?
- WIFI
- Bluetooth - not tested much
- Front webcam
- Touchpad
- Keyboard  
- Battery
- Screen Brightness

### Not Tested or Not working
- Ethernet Port - I always use wifi (Maybe it works)
- HMDI - not needed for me (Probably works)
- Audio Jack - Not required (You can find drivers if you need it)
Other things which i don’t need however you can find drivers for anything you need, just test them one by one






### CFG Lock and others These vars are from [Bios v1.12.1](https://www.dell.com/support/home/en-uk/drivers/driversdetails?driverid=h08hj&oscode=wt64a&productcode=inspiron-15-7567-laptop)
You can use them if your bios is updated and you have the same laptop! Or you will need to find yours.
You must enter these in modGRUBShell.efi which is included in the tools folder already.
You can check if the var is already set using setup_var 0x4de (this checks for CFG Lock)
- 0x01 = enabled
- 0x00 = disabled
```
disable cfg lock
setup_var 0x4DE 0x00 

enable above 4GB MMIO BIOS assignment
setup_var 0x78A 0x01

disable CSM Support
setup_var 0xF84 0x00
```

You must follow this [OpenCore guide to get these Fixing CFG Lock | OpenCore Post-Install (dortania.github.io)](https://dortania.github.io/OpenCore-Post-Install/misc/msr-lock.html#what-is-cfg-lock) , there is a Dell link you can use to extract bios and the file and everything will be in the file you converted to text.

Use VerifyMsrE2 (Already in tools folder)
 To check CFG Lock , if you get 
`This firmware has UNLOCKED MSR 0xE2 register!`
 That means you have working CFG Lock!
 
# Thanks to 
- [OpenCore](https://dortania.github.io/OpenCore-Install-Guide/)
- blazinsmokey [Guide Dell XPS 9560 Big Sur OpenCore](https://www.tonymacx86.com/threads/guide-dell-xps-9560-big-sur-opencore.307163/) Without his guide it was not possible to get the iGPU working!



Enjoy and good luck! 
