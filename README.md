# VNC Remote Access for Jetson Nano

Here we will connect jetson nano to VNC viewer application as the preinstalled Desktop Application crashes when we try to use it. To avoide this follow these steps:

## Step 1: Connect the board to wireless connection

This NVIDIA Jetson Nano L4T has poor support for USB Wi-Fi adapters and most adapters do not work with this distribution. Then purchase a compatible USB WiFi adapter to connect to your local network externally.

## Step 2: Start desktop sharing

First, open the terminal and paste this line.
`sudo apt update`
`sudo apt-get upgrade`

``After both the command install nano editor
`sudo apt-get install nano`

Next paste this link in the terminal and press enter
`sudo nano /usr/share/glib-2.0/schemas/org.gnome.Vino.gschema.xml`

Next paste the following key into opened XML file 

<key name=’enabled’ type=’b’>
<summary>Enable remote access to the desktop</summary>
<description>
If true, allows remote access to the desktop via the RFB
protocol. Users on remote machines may then connect to the
desktop using a VNC viewer.
</description>
<default>true</default>
</key>

Press `Ctrl + O` to Save than press Enter
To move back to the terminal press `Ctrl + Z`

Next compile the edited XML file
`sudo glib-compile-schemas /usr/share/glib-2.0/schemas`

Now crashing of Desktop Sharing must have stopped. So Click on 'Search' icon and search for 'Desktop Sharing'. Open it and complete the following changes:

Tick mark both the <b>Sharing</b> options. 
Under <b>Security</b> Tick mark the 'Require the user to enter this password' and enter the password for VNC session.
Close Desktop Sharing.

## Step 3: Start the VNC server on each startup

Click on 'Search' icon and search for 'Startup Applications'. Open it. Now, click on `Add`, then type `Vino` in the name box. Paste `/usr/lib/vino/vino-server` in the command box. Click `Save` and then `Close`.

Now disable the default encryption of the VNC connection. To do this, paste these lines on 
terminal and press enter:

`gsettings set org.gnome.Vino require-encryption false`

`gsettings set org.gnome.Vino prompt-enabled false`

###Now Reboot your nano and VNC will be enabled on your Jetson Nano

## Step 4: Connect to your Nano via VNC

Login to your Jetson Nano board. Connect your Jetson Nano and your Personal Laptop to the same wifi network. Open terminal in Jetson Nano and type `ifconfig`. You will get the IP address which is assigned to your Jetson Nano. In my case assigned IP address is 192.168.137.222.

Now lets confirm VNC is working or not. Paste this in the terminal:
`ps -ef|grep vnc`.

Now once you know your IP and confirmed that VNC is running, lets move on to your personal laptop(Client Machine).

### Note: In my case I an using Ubantu Linux (ThinkServer Machine)




