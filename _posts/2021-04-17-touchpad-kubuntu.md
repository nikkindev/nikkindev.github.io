---
title: Kubuntu touchpad tapping
tags: [linux]
---

*If touchpad tapping suddenly stops working after installing Kubuntu/Ubuntu...*
<!--more-->

Sometimes when installing Ubuntu/Kubuntu, the touchpad tapping stops working. If you are a root user, you can change the default setting.

To see the connected devices,  

`xinput list`

The touchpad will be available under the name **SynPS/2 Synaptics TouchPad**. To see the list of properties of the device,

`xinput list-props "SynPS/2 Synaptics TouchPad"`

If you're a root user, you can change the setting for the property **libinput Tapping Enabled Default** to 1 by

`xinput set-prop "SynPS/2 Synaptics TouchPad" 123 1`

if 123 if the number for the property. But for the user, to change the property for **libinput Tapping Enabled** everytime you run start the OS (but still have to start the terminal), append the following commands at the end of */home/user/.bashrc* file

`propnr=$(xinput list-props "SynPS/2 Synaptics TouchPad" | grep "Tapping Enabled" | head -n 1 | awk -F"[()]" '{print $2}')`

`xinput set-prop "SynPS/2 Synaptics TouchPad" $propnr 1`

The first line extracts the property number and stores it in a variable. The second line sets the property for that property number. Note that the *.bashrc* file is not executed automatically on startup rather, the first time the Terminal/Konsole is started. So, touch tap works after starting the terminal after startup.