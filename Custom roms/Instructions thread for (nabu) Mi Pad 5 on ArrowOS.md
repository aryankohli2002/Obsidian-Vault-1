https://k001droid.medium.com/instructions-thread-for-nabu-mi-pad-5-on-arrowos-9be3c4054c0a
fastboot -w

- This will properly wipe your data, metadata partitions
- Now flash boot.img and vendor_boot.img downloaded from [ArrowOS Recovery](https://sourceforge.net/projects/kubersharma001/files/nabu/) folder

fastboot flash boot boot.img  
fastboot flash vendor_boot vendor_boot.img  
fastboot reboot recovery

- Xiaomi Pad 5’s recovery has an issue where panel doesn’t render the UI, but recovery works just fine.

adb devices

- This should show your device, now reboot to sideload

adb reboot sideload  
adb sideload *Drag and drop ArrowOS build for nabu*

- This will take about 5–8 minutes, and in the end it may get stuck at 47% but THAT IS FINE, when the flash is done it will output: “xfer 1.00x”
- That means it has been flashed! Now time to wipe data again via recovery.

adb shell  
recovery --wipe_data  
adb reboot

That is it! ENJOY :D

[Low Cost Thoracoscopic Sympathectomy in India & Best Hospitals for Thoracoscopic Sympathectomy in India (lyfboat.com)](https://www.lyfboat.com/hospitals/thoracoscopic-cervical-sympathectomy-hospitals-and-costs-in-india/)
