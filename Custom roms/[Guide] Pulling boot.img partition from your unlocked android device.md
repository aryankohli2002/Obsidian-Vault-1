Originally wrote this to help Mi pad 5 (nabu users) but thought to make it a separate post, the device referenced/example will be nabu.

This requires a custom recovery like custom recovery or anything which allows access to adb shell

First go to fastboot to find out the current active slot (for A/B slot devices only)

fastboot getvar current-slot  
  
Results:   
current-slot: b

If it returns nothing then it means you have A only slot device probably

Now reboot to recovery and open adb shell

fastboot reboot recovery  
adb shell

Now pull a partition from the current slot (because that’s what you are using right now), let’s pull boot.img and vendor_boot.img

Instructions for (v_/)A/B slot devices:

dd if=/dev/block/bootdevice/by-name/boot_b of=/sdcard/boot.img  
dd if=/dev/block/bootdevice/by-name/vendor_boot_b of=/sdcard/vendor_boot.img

Instructions for A-only slot devices:

dd if=/dev/block/bootdevice/by-name/boot of=/sdcard/boot.img

Now these are pushed to /sdcard, how to get them on your computer? Exit adb shell

exit

Now, adb pull from sdcard, it will be stored where you Terminal is opened from

adb pull /sdcard/boot.img

You can also give it a path/to/copy. for example (in my Mac):

adb pull /sdcard/boot.img /Users/k001droid/nabu/images/

Done